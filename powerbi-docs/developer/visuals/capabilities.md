---
title: Funciones
description: Funciones y propiedades de objetos visuales de Power BI
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425468"
---
# <a name="power-bi-visual-capabilities"></a>Funciones de objetos visuales de Power BI

Las funciones proporcionan información al host sobre el objeto visual. Todas las propiedades del modelo de funciones son `optional`

Los objetos raíz de las funciones del objeto visual son `dataRoles`, `dataViewMappings`, etc.

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>Definir los campos de datos que espera el objeto visual: `dataRoles`

Para definir los campos que se pueden enlazar a los datos, usamos `dataRoles`, que obtiene una matriz de objetos de `DataViewRole` para definir todas las propiedades necesarias.

### <a name="properties"></a>Propiedades

* **name**: el nombre interno del campo de datos (tiene que ser único).
* **kind**: el tipo de campo:
    * `Grouping`: valores discretos usados para la agrupación de campos de medida.
    * `Measure`: valores de datos numéricos.
    * `GroupingOrMeasure`: puede usarse como una agrupación o como una medida.
* **displayName**: el nombre que se muestra al usuario en el panel de propiedades.
* **description**: una descripción breve del campo (opcional).
* **requiredTypes**: el tipo de datos necesario para este rol de datos. Cualquier valor que no coincida se establecerá en nulo (opcional).
* **preferredTypes**: el tipo de datos preferido para este rol de datos (opcional).

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Tipos de datos válidos en “requiredTypes” y “preferredTypes”

* **bool**: un valor booleano.
* **integer**: un valor entero (número entero).
* **numeric**: un valor numérico.
* **text**: un valor de texto.
* **geography**: un dato geográfico.

### <a name="example"></a>Ejemplo

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

Los roles de datos anteriores crearían los campos siguientes.

![Mostrar el rol de datos](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>Definir cómo quiere que se asignen los datos: `dataViewMappings`

Un elemento DataViewMapping describe cómo se relacionan los roles de datos entre sí y le permite especificar requisitos condicionales para estos.

La mayoría de los objetos visuales proporcionan una sola asignación, pero puede proporcionar varios elementos dataViewMappings. Cada asignación válida generará un elemento DataView. 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[Más información sobre DataViewMappings](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>Definir opciones del panel de propiedades: `objects`

Los objetos describen propiedades personalizables asociadas al objeto visual.
Cada objeto puede tener varias propiedades, y cada propiedad tiene un tipo asociado.
Los tipos hacen referencia a lo que será la propiedad. A continuación, encontrará más información sobre los distintos tipos.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[Más información sobre los objetos](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>Controlar el resaltado parcial: `supportsHighlight`

De forma predeterminada, este valor es falso, lo que significa que sus “Valores” se filtrarán automáticamente al seleccionar un elemento en la página; a su vez, se actualizará el objeto visual para mostrar solo el valor seleccionado. Para mostrar todos los datos, pero solo resaltar los elementos seleccionados, necesita establecer `supportsHighlight` en “true” en el archivo capabilities.json.

[Más información sobre el resaltado](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>Controlar el modo de edición avanzada: `advancedEditModeSupport`

Un objeto visual puede declarar su compatibilidad con el modo de edición avanzada.
De forma predeterminada, un objeto visual no admite el modo de edición avanzada, a menos que se indique lo contrario en el archivo JSON de funciones.

[Más información sobre advancedEditModeSupport](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>Opciones de ordenación de datos para objetos visuales: `sorting`

Un objeto visual puede definir su comportamiento de ordenación mediante sus funciones.
De forma predeterminada, un objeto visual no permite que se modifique su criterio de ordenación, a menos que se indique lo contrario en el archivo capabilities.json.

[Más información sobre la ordenación](sort-options.md)
