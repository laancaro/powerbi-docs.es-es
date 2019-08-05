---
title: API de filtros visuales
description: Filtrado de objetos visuales mediante objetos visuales de Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425054"
---
# <a name="power-bi-visual-filters-api"></a>API de filtros visuales de Power BI

Los filtros de objeto visual permiten el filtrado de datos. La principal diferencia con respecto a las selecciones es que otros objetos visuales se filtrarán de todos modos, a pesar de que otro objeto visual admita el resaltado.

Para habilitar el filtrado del objeto visual, el objeto visual debe contener el objeto `filter` en la sección `general` de contenido de capabilities.json.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

Las interfaces de Filter API están disponibles en el paquete [`powerbi-models`](https://www.npmjs.com/package/powerbi-models). El paquete también contiene clases para crear instancias de filtro.

```cmd
npm install powerbi-models --save
```

Si usa las herramientas de una versión anterior (inferior a 3.x.x), debe incluir `powerbi-models` en el paquete de objetos visuales. [Guía breve de procedimientos para incluir el paquete](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Todos los filtros extienden la interfaz `IFilter`.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target`: la columna de la tabla en el origen de datos.

## <a name="basic-filter-api"></a>Basic Filter API

La interfaz de filtro básica es la siguiente:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator`: es una enumeración con los valores "In", "NotIn", "All"

`values`: son los valores para la condición

Ejemplo de filtro básico:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

El filtro significa "enviarme todas las filas donde `col1` es igual a uno de los valores 1, 2 o 3".

El equivalente en SQL es el siguiente:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Para crear un filtro, puede usar la clase BasicFilter en `powerbi-models`.

Si usa la versión anterior de las herramientas, debe obtener una instancia de los modelos en el objeto de ventana mediante `window['powerbi-models']`:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

El objeto visual invoca el filtro mediante el método applyJsonFilter() en la interfaz de host IVisualHost proporcionada al objeto visual en el constructor.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>Advanced Filter API

[Advanced Filter API](https://github.com/Microsoft/powerbi-models) permite realizar consultas complejas de selección y filtrado de puntos de datos entre objetos visuales en función de varios criterios (como "LessThan", "Contains", "Is", "IsBlank", etc.).

El filtro se presentó en Visuals API 1.7.0.

Advanced Filter API también requiere `target` con los nombres de `table` y `column`. Pero los operadores de Advanced Filter API son `"And" | "Or"`. 

Además, el filtro usa condiciones en lugar de valores con la interfaz:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Los operadores de condición para el parámetro `operator` son `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

El equivalente en SQL es el siguiente:

```sql
SELECT * FROM table WHERE col1 < 0;
```

El código de ejemplo completo del uso de Advanced Filter API se puede encontrar en el [repositorio `Sampleslicer visual`](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>Tuple Filter API (filtro de varias columnas)

Tuple Filter API se presentó en Visuals API 2.3.0.

La API de filtro de tupla es similar a la de filtro básico, pero permite definir condiciones para varias columnas y tablas.

Y un filtro tiene la interfaz: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` es una matriz de columnas con nombres de tabla:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  El filtro puede abarcar columnas de tablas diferentes.

`$schema` es "http://powerbi.com/product/schema#tuple"

`filterType` es `FilterType.Tuple`

`operator` solo permite el uso del operador `"In"`

`values` es una matriz de tuplas de valor, donde cada tupla representa una combinación permitida de los valores de columna de destino. 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Ejemplo completo:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**El orden de los nombres y valores de columna de la condición es sensible.**

El equivalente en SQL es el siguiente:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>Restauración del filtro JSON desde DataView

A partir de la API 2.2, **los filtros JSON** se pueden restaurar desde **VisualUpdateOptions**.

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Power BI llama al método `update` del objeto visual, cuando se usan marcadores de intercambio y el objeto visual obtiene el objeto `filter` correspondiente.
[Más información sobre la compatibilidad con marcadores](bookmarks-support.md)

### <a name="sample-json-filter"></a>Filtro JSON de ejemplo

![Captura de pantalla del filtro JSON](./media/json-filter.png)

### <a name="clear-json-filter"></a>Borrado del filtro JSON

Filter API acepta el valor de filtro `null` para restablecer o borrar.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
