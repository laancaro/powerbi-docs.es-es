---
title: Información en pantalla de los objetos visuales
description: Los objetos visuales de Power BI pueden mostrar información en pantalla.
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 286c5eef2c341ad77c351008b321992597bef292
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425652"
---
# <a name="power-bi-visuals-tooltips"></a>Información en pantalla de los objetos visuales de Power BI

Los objetos visuales ahora pueden aprovechar la compatibilidad con la información en pantalla de Power BI. Con la información en pantalla de Power BI se controlan las siguientes interacciones:

Mostrar una información en pantalla.
Ocultar una información en pantalla.
Mover una información en pantalla.

La información en pantalla puede mostrar un elemento de texto con un título, un valor en un color determinado y opacidad en un conjunto especificado de coordenadas. Estos datos se proporcionan a la API. Asimismo, el host de Power BI los representa de la misma manera que representa la información en pantalla para los objetos visuales nativos.

Por ejemplo, la información en pantalla en el ejemplo BarChart.

![Información en pantalla de BarChart de ejemplo](./media/tooltips-in-samplebarchart.png)

La información en pantalla anterior muestra una sola categoría de barra y su valor. Se puede ampliar para mostrar varios valores en una sola información en pantalla.

## <a name="handling-tooltips"></a>Control de la información en pantalla

La interfaz a través de la cual se administra la información en pantalla es "ITooltipService". Esta interfaz se utiliza para notificar al host que una información en pantalla debe mostrarse, quitarse o moverse.

```typescript
    interface ITooltipService {
        enabled(): boolean;
        show(options: TooltipShowOptions): void;
        move(options: TooltipMoveOptions): void;
        hide(options: TooltipHideOptions): void;
    }
```

El objeto visual tendrá que escuchar los eventos del mouse dentro del objeto visual y llamar a los delegados `show()`, `move()` y `hide()` según sea necesario con el contenido adecuado rellenado en los objetos `Tooltip****Options`.
A su vez, `TooltipShowOptions` y `TooltipHideOptions` definirían lo que se va a mostrar y cómo comportarse en estos eventos.
Dado que la llamada a estos métodos implicaría eventos de usuario tales como movimientos del mouse o eventos táctiles, una buena idea sería crear clientes de escucha para estos eventos, lo que a su vez invocaría a los miembros `TooltipService`.
En nuestro ejemplo se agrega en una clase denominada `TooltipServiceWrapper`.

### <a name="tooltipservicewrapper-class"></a>Clase TooltipServiceWrapper

La idea básica que subyace en esta clase es mantener la instancia de la clase `TooltipService`, escuchar eventos del mouse D3 sobre elementos pertinentes y, luego, realizar las llamadas a `show()` y `hide()` cuando sea necesario.
La clase contiene y administra cualquier estado pertinente y la lógica de estos eventos, principalmente orientados a la interactuación con el código D3 subyacente. La interactuación y conversión de D3 queda fuera del ámbito de este documento.

Puede encontrar el código de ejemplo completo en el [repositorio del objeto visual SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/981b021612d7b333adffe9f723ab27783c76fb14).

### <a name="creating-tooltipservicewrapper"></a>Creación de TooltipServiceWrapper

El constructor BarChart tiene ahora un miembro `tooltipServiceWrapper`, del que se crean instancias en el constructor con la instancia de `tooltipService` de host.

```typescript
        private tooltipServiceWrapper: ITooltipServiceWrapper;

        this.tooltipServiceWrapper = createTooltipServiceWrapper(this.host.tooltipService, options.element);
```

La clase `TooltipServiceWrapper` contiene la instancia de `tooltipService`, también como elemento raíz D3 de los parámetros visuales y táctiles.

```typescript
    class TooltipServiceWrapper implements ITooltipServiceWrapper {
        private handleTouchTimeoutId: number;
        private visualHostTooltipService: ITooltipService;
        private rootElement: Element;
        private handleTouchDelay: number;

        constructor(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay: number) {
            this.visualHostTooltipService = tooltipService;
            this.handleTouchDelay = handleTouchDelay;
            this.rootElement = rootElement;
        }
        .
        .
        .
    }
```

El único punto de entrada para que esta clase registre a los clientes de escucha de eventos es el método `addTooltip`.

### <a name="addtooltip-method"></a>Método addTooltip

```typescript
        public addTooltip<T>(
            selection: d3.Selection<Element>,
            getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[],
            getDataPointIdentity: (args: TooltipEventArgs<T>) => ISelectionId,
            reloadTooltipDataOnMouseMove?: boolean): void {

            if (!selection || !this.visualHostTooltipService.enabled()) {
                return;
            }
        ...
        ...
        }
```

* **selection: d3.Selection<Element>**
* Elementos D3 en los que se controla la información en pantalla.
* **getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[]**
* Delegado para rellenar el contenido de la información en pantalla (lo que se muestra) por contexto.
* **getDataPointIdentity: (args: TooltipEventArgs<T>) => ISelectionId**
* Delegado para recuperar el identificador del punto de datos (no se usa en este ejemplo). 
* **reloadTooltipDataOnMouseMove?: boolean**
* Valor booleano que indica si se deben actualizar los datos de la información en pantalla durante un evento mouseMove (no se usa en este ejemplo).

Como puede ver, `addTooltip` se cerrará sin realizar ninguna acción si la clase `tooltipService` está deshabilitada o no hay ninguna selección real.

### <a name="call-of-show-method-to-display-a-tooltip"></a>Llamada del método Show para mostrar una información en pantalla.

`addTooltip` escucha a continuación el evento `mouseover` de D3.

```typescript
        ...
        ...
        selection.on("mouseover.tooltip", () => {
            // Ignore mouseover while handling touch events
            if (!this.canDisplayTooltip(d3.event))
                return;

            let tooltipEventArgs = this.makeTooltipEventArgs<T>(rootNode, true, false);
            if (!tooltipEventArgs)
                return;

            let tooltipInfo = getTooltipInfoDelegate(tooltipEventArgs);
            if (tooltipInfo == null)
                return;

            let selectionId = getDataPointIdentity(tooltipEventArgs);

            this.visualHostTooltipService.show({
                coordinates: tooltipEventArgs.coordinates,
                isTouchEvent: false,
                dataItems: tooltipInfo,
                identities: selectionId ? [selectionId] : [],
            });
        });
```

* **makeTooltipEventArgs**
* Extrae el contexto de los elementos seleccionados de D3 en una clase tooltipEventArgs. También calculará las coordenadas.
* **getTooltipInfoDelegate**
* Luego, compila el contenido de la información en pantalla desde la clase tooltipEventArgs. Es una devolución de llamada a la clase BarChart, ya que es la lógica del objeto visual. Se trata del contenido de texto real que se va a mostrar en la información en pantalla.
* **getDataPointIdentity**
* No se usa en este ejemplo.
* **this.visualHostTooltipService.show**
* Llamada para mostrar la información en pantalla.  

Se puede encontrar control adicional en el ejemplo de los eventos `mouseout` y `mousemove`.

Para más información, consulte el [repositorio del objeto visual SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/981b021612d7b333adffe9f723ab27783c76fb14).

### <a name="populating-the-tooltip-content-by-gettooltipdata-method"></a>Rellenado del contenido de la información en pantalla con el método getTooltipData

Se ha agregado `BarChart` con un miembro `getTooltipData` que simplemente extrae la categoría, el valor y el color del punto de datos en un elemento VisualTooltipDataItem[].

```typescript
        private static getTooltipData(value: any): VisualTooltipDataItem[] {
            return [{
                displayName: value.category,
                value: value.value.toString(),
                color: value.color,
                header: 'ToolTip Title'
            }];
        }
```

En la implementación anterior, el miembro `header` es constante, pero se puede usar para implementaciones más complejas, que requieren valores dinámicos. Puede rellenar `VisualTooltipDataItem[]` con más de un elemento, lo que agregará varias líneas a la información en pantalla. Puede resultar útil en objetos visuales, como los gráficos de barras apiladas, donde la información en pantalla puede mostrar datos de más de un solo punto de datos.

### <a name="calling-addtooltip-method"></a>Llamadas al método addTooltip

El paso final es llamar a `addTooltip` cuando los datos reales puedan cambiar. Esta llamada se realizará en el método `BarChart.update()`. Por lo tanto, se realiza una llamada para supervisar la selección de todos los elementos "bar", pasando solo el elemento `BarChart.getTooltipData()` indicado anteriormente.

```typescript
        this.tooltipServiceWrapper.addTooltip(this.barContainer.selectAll('.bar'),
            (tooltipEvent: TooltipEventArgs<number>) => BarChart.getTooltipData(tooltipEvent.data),
            (tooltipEvent: TooltipEventArgs<number>) => null);
```

## <a name="adding-report-page-tooltips"></a>Adición de información en pantalla de la página de informes

Para agregar compatibilidad con la información en pantalla de la página de informes, la mayoría de los cambios se ubicarán en capabilities.json.

Un esquema de ejemplo es el siguiente:

```json
{
    "tooltips": {
        "supportedTypes": {
            "default": true,
            "canvas": true
        },
        "roles": [
            "tooltips"
        ]
    }
}
```

La definición de la información en pantalla de la página de informes se puede realizar en el panel Formato.

![Información en pantalla de la página de informes](media/report-page-tooltip.png)

`supportedTypes` es la configuración de información en pantalla que admite el objeto visual y se refleja en el conjunto de campos. `default` especifica si se admite el enlace de la información en pantalla "automática" mediante el campo de datos. El lienzo especifica si se admite la información en pantalla de la página de informes.

`roles` es opcional. Una vez definida, indica qué roles de datos se van a enlazar a la opción de información en pantalla seleccionada en el conjunto de campos.

Para obtener más información, consulte las instrucciones de uso de la información en pantalla de la página de informes que encontrará en el artículo de blog [Información en pantalla de la página de informes](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#tooltips).

Para mostrar la información en pantalla de la página de informes, al llamar a `ITooltipService.Show(options: TooltipShowOptions)` o `ITooltipService.Move(options: TooltipMoveOptions)`, el host de Power BI utilizará selectionId (propiedad `identities` del argumento `options` anterior). SelectionId debe representar los datos seleccionados (categoría, serie, etc.) del elemento sobre el que mantuvo el mouse para que la información en pantalla los recupere.

Ejemplo de envío de selectionId a llamadas de visualización de información en pantalla:

```typescript
    this.tooltipServiceWrapper.addTooltip(this.barContainer.selectAll('.bar'),
        (tooltipEvent: TooltipEventArgs<number>) => BarChart.getTooltipData(tooltipEvent.data),
        (tooltipEvent: TooltipEventArgs<number>) => tooltipEvent.data.selectionID);
```
