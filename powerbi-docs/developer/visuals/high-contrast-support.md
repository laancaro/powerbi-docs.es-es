---
title: Compatibilidad con el modo de contraste alto
description: Agregar compatibilidad con el modo de contraste alto a objetos visuales de Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cb77ea012fdfdbd5be62c58c6f9b94a0355db1a9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424939"
---
# <a name="high-contrast-mode-support"></a>Compatibilidad con el modo de contraste alto

La configuración de *contraste alto* de Windows mejora la visualización del texto y las aplicaciones al usar colores más definidos.
Obtenga más información sobre la [compatibilidad con contraste alto en Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

Para agregar la compatibilidad con contraste alto a un objeto visual, se necesita lo siguiente:

1. Al iniciar: detecte si Power BI está en el modo de contraste alto y, si es así, obtenga los colores de contraste alto actuales.
2. En cada actualización: cambie la forma en que se representa el objeto visual para que sea más fácil de ver.

El objeto visual PowerBI-visuals-sampleBarChart tiene la implementación de compatibilidad con contraste alto.

Para obtener más información, vea el [Repositorio de objetos visuales de PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6).

## <a name="on-init"></a>Al iniciar

El miembro de colorPalette de `options.host` tiene varias propiedades para el modo de contraste alto. Use estas propiedades para determinar si el modo de contraste alto está activo y, de ser así, qué colores usar.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Detectar si Power BI está en el modo de contraste alto

Si `host.colorPalette.isHighContrast` es `true`, se activará el modo de contraste alto y, en consecuencia, se dibujará el objeto visual.

### <a name="get-high-contrast-colors"></a>Obtener colores de contraste alto

En el modo de contraste alto, el objeto visual tiene que limitarse a los colores siguientes:

* El color de **primer plano** se usa para dibujar cualquier línea, icono, texto y contorno o relleno de formas.
* El color de **fondo** se usa para el fondo, y como color de relleno de las formas con contorno.
* El color de **primer plano: seleccionado** se usa para indicar un elemento seleccionado o activo.
* El color de los **hipervínculos** solo se usa para el texto de los hipervínculos.

> [!NOTE]
> Si necesita un color secundario, el color de primer plano puede usarse con cierta opacidad (los objetos visuales nativos de Power BI usan un 40 % de opacidad). Use esta opción con moderación para asegurarse de que los detalles visuales puedan verse fácilmente.

Puede guardar estos valores durante la inicialización:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

O bien puede guardar el objeto `host` durante la inicialización y acceder a las propiedades de `colorPalette` relevantes durante la actualización.

## <a name="on-update"></a>Al actualizar

Las implementaciones específicas de la compatibilidad con contraste alto varían según el objeto visual y dependen de los detalles del diseño gráfico. Normalmente, el modo de contraste alto necesita un diseño ligeramente distinto al predeterminado para asegurarse de que los detalles importantes puedan distinguirse fácilmente con los colores limitados.

Estas son algunas directrices que siguen los objetos visuales nativos de Power BI:

* Todos los puntos de datos usan el mismo color (primer plano).
* Todo el texto, los ejes, las flechas, las líneas, etc., usan el color de primer plano.
* Las formas gruesas se dibujan como contornos, con trazos gruesos (como mínimo, de dos píxeles) y relleno del color de fondo.
* Cuando corresponde, los puntos de datos se distinguen mediante varias formas de marcadores, y las líneas de datos se distinguen mediante el uso de distintas líneas discontinuas.
* Al resaltar un elemento de datos, el resto de los elementos cambian su opacidad a 40 %.
* Para las segmentaciones, los elementos de filtro activos usan el color seleccionado del primer plano.

Por ejemplo, en el gráfico de barras, todas las barras se dibujan con un contorno de primer plano de dos píxeles de grosor y con relleno de fondo. Compare el aspecto con los colores predeterminados y con un par de temas de contraste alto:

![Gráfico de barras de ejemplo con colores estándar](./media/hc-samplebarchart-standard.png)
![Gráfico de barras de ejemplo con el tema de color *Oscuro 2*](./media/hc-samplebarchart-dark2.png)
![Gráfico de barras de ejemplo con el tema de color *Blanco*](./media/hc-samplebarchart-white.png)

En la función `visualTransform`, se ha cambiado un valor para admitir el contraste alto, al que se realiza una llamada como parte de la representación durante `update`:

### <a name="before"></a>Antes

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Después

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
