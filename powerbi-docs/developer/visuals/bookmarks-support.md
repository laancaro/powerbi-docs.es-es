---
title: Marcadores
description: Un objeto visual de Power BI puede controlar el cambio de marcadores.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425514"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Adición de compatibilidad de los marcadores para los objetos visuales de Power BI

Los marcadores de los informes de Power BI permiten capturar la vista configurada de una página de informe, el estado de selección y el estado de filtrado del objeto visual. Sin embargo, los objetos visuales personalizados requieren una acción más para admitir los marcadores y poder aplicar los cambios correctamente.

Obtenga más información sobre los marcadores en la [documentación](https://docs.microsoft.com/power-bi/desktop-bookmarks).

## <a name="report-bookmarks-support-in-your-visual"></a>Compatibilidad de los marcadores de un informe en un objeto visual

Si el objeto visual filtra elementos del mismo tipo o interactúa con ellos, o bien si selecciona puntos de datos, hay que restaurar el estado de las propiedades.

## <a name="how-to-add-report-bookmarks-support"></a>Cómo agregar compatibilidad con los marcadores de un informe

1. Instale (o actualice) la utilidad necesaria, `powerbi-visuals-utils-interactivityutils` (https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) ), versión 3.0.0 o posterior. Contiene clases adicionales para la manipulación con selección de estado o filtro. Se necesita para los objetos visuales de filtro y cualquiera que use el módulo `InteractivityService`.

2. Actualice la API de los objetos visuales a la versión 1.11.0 para usar `registerOnSelectCallback`, en el caso de `SelectionManager`. Se necesita para los objetos visuales que no sean de filtro y usen `SelectionManager` estándar, en lugar de `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Interacción de los objetos visuales personalizados con Power BI en los marcadores de un informe

Veamos el siguiente ejemplo: Un usuario crea varios marcadores en la página del informe, con un estado de selección diferente en cada marcador.

En primer lugar, el usuario selecciona un punto de datos en el objeto visual. El objeto visual interactúa con Power BI y otros objetos visuales y pasa las selecciones al host. Luego, el usuario selecciona "Agregar" en `Bookmark panel` y Power BI guarda las selecciones actuales del nuevo marcador.

Esto ocurre cada vez que el usuario cambia la selección y agrega nuevos marcadores.
Una vez creados, el usuario puede cambiar de un marcador a otro.

Cuando los usuarios seleccionan un marcador, Power BI restaura el estado de selección o filtro guardado y lo pasa a los objetos visuales. El resto de objetos visuales quedarán resaltados o filtrarán según el estado almacenado en el marcador. El host de Power BI es responsable de las acciones. El objeto visual es responsable de reflejar correctamente el nuevo estado de selección (por ejemplo, cambiar el color de los puntos de datos representados).

El nuevo estado de selección se comunica al objeto visual a través del método `update`. El argumento `options` contendrá una propiedad especial, `options.jsonFilters`. Se trata de JSONFilter, una propiedad que puede contener `Advanced Filter` y `Tuple Filter`.

El objeto visual debe restaurar los valores de filtro para mostrar el estado correspondiente del objeto visual para el marcador seleccionado.

O bien, usar el método `registerOnSelectCallback` registrado de la función de devolución de llamada especial de ISelectionManager, si el objeto visual solo usa selecciones.

### <a name="visuals-with-selections"></a>Objetos visuales con selecciones

Si los objetos visuales interactúan con otros objetos visuales mediante [selecciones](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), tiene dos maneras de agregar marcadores.

* Puede usar el método `FilterManager.restoreSelectionIds` si **no ha usado[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** antes en el objeto visual.

* Si el objeto visual ya utiliza **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** para administrar selecciones, debe emplear el método `applySelectionFromFilter` en el caso de `InteractivityService`.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Uso de `ISelectionManager.registerOnSelectCallback`

Cuando un usuario hace clic en un marcador, Power BI llama al método `callback` del objeto visual con las selecciones correspondientes. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Supongamos que tiene un punto de datos en el objeto visual creado en el método [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

Además, `datapoints` tiene el siguiente aspecto:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Por lo tanto, tiene `visualDataPoints` como puntos de datos y una matriz `ids` que ha pasado a la función `callback`.

En este punto, el objeto visual debe comparar la matriz de `ISelectionId[]` con la selección de la matriz `visualDataPoints` y marcar como seleccionados los puntos de datos que correspondan.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Tras actualizarlos, los puntos de datos reflejarán el estado de selección actual almacenado en el objeto `filter`. Luego, cuando los puntos de datos se representen, el estado de selección del objeto visual personalizado coincidirá con el del marcador.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>Uso de `InteractivityService` para el control de selecciones en el objeto visual

Si el objeto visual usa `InteractivityService`, no hay que hacer nada más para admitir los marcadores en el objeto visual.

La utilidad controlará el estado de selección del objeto visual cuando el usuario seleccione los marcadores.

### <a name="visuals-with-filter"></a>Objetos visuales con filtro

Supongamos que el objeto visual crea un filtro de datos por intervalo de fechas. Por lo tanto, tenemos `startDate` y `endDate` como inicio y fin del intervalo.
El objeto visual crea un filtro avanzado y llama al método de host `applyJsonFilter` para filtrar los datos según las condiciones pertinentes.
`target` es la tabla del filtrado.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Cada vez que un usuario hace clic en un marcador, el objeto visual personalizado recibe una llamada de `update`.

El objeto visual personalizado debe comprobar el filtro en el objeto:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Si el objeto `filter` no es NULL, el objeto visual debe restaurar las condiciones de filtro del objeto:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Después, el objeto visual debe cambiar su estado interno, los puntos de datos y los objetos de visualización (líneas, rectángulos, etc.), para reflejar las condiciones actuales.

> [!IMPORTANT]
> En el caso de los marcadores de informe, el objeto visual no tiene que llamar a `applyJsonFilter` para filtrar otros objetos visuales, puesto que ya estarán filtrados por Power BI.

El objeto visual de segmentación de escala de tiempo cambia el selector de intervalo a los intervalos de datos correspondientes.

Para obtener más información, consulte el [repositorio de segmentación de escala de tiempo](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Estado del filtro para guardar propiedades del objeto visual en los marcadores

La propiedad `filterState` crea una propiedad de una parte del filtrado. El objeto visual puede almacenar distintos valores en marcadores.

Para guardar el valor de la propiedad como estado del filtro, la propiedad del objeto debe marcarse como `"filterState": true` en `capabilities.json`.

Ejemplo: `Timeline Slicer` almacena los valores de la propiedad `Granularity` en el filtro. También permite modificar la granularidad actual al cambiar los marcadores por usuario.

Para obtener más información, consulte el [repositorio de segmentación de escala de tiempo](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
