---
title: Objeto y propiedades
description: Propiedades personalizables de Power BI Visual
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424617"
---
# <a name="object-and-properties"></a>Objeto y propiedades

Los objetos describen propiedades personalizables asociadas al objeto visual.
Cada objeto puede tener varias propiedades, y cada propiedad tiene un tipo asociado.
Los tipos hacen referencia a lo que será la propiedad. A continuación, encontrará más información sobre los distintos tipos.

`myCustomObject` es el nombre interno usado para hacer referencia al objeto en `dataView` y `enumerateObjectInstances`.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Nombre para mostrar

`displayName` es el nombre que se mostrará en el panel de propiedades.

## <a name="properties"></a>Propiedades

`properties` es un mapa de propiedades definido por el desarrollador.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` es una propiedad especial que habilita un botón de alternancia para cambiar el valor del objeto.

Ejemplo:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Tipos de propiedad

Hay dos tipos de propiedad: `ValueTypeDescriptor` y `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Descriptor de tipo de valor

`ValueTypeDescriptor` son en su mayoría tipos primitivos y suelen usarse como un objeto estático.
Estos son algunos de los elementos comunes `ValueTypeDescriptor`

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Descriptor de tipo estructural

`StructuralTypeDescriptor` se usan principalmente para objetos enlazados a datos.
El relleno es el elemento más común `StructuralTypeDescriptor`

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Propiedad de degradado

La propiedad de degradado no se puede establecer como una propiedad estándar. En su lugar, tiene que configurar una regla para la sustitución de la propiedad del selector de colores (tipo de relleno).
Vea el ejemplo a continuación:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Preste atención a las propiedades `"fill"` y `"fillRule"`. La primera es el selector de colores, mientras que la segunda es la regla de sustitución de degradado que reemplazará a la propiedad “fill” `visually` cuando se cumplan las condiciones de la regla.

Este vínculo entre la propiedad “fill” y la regla de sustitución se establece en la sección `"rule"`->`"output"` de la propiedad `"fillRule"`.

`"Rule"`->`"InputRole"` establece el rol de datos que desencadena la regla (condición). En este ejemplo, si el rol de datos `"Gradient"` contiene datos, la regla se aplicará en la propiedad `"fill"`.

A continuación, puede ver un ejemplo del rol de datos que desencadena la regla de relleno (`the last item`).

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="enumerateobjectinstances-method"></a>Método `enumerateObjectInstances`

Para usar los objetos correctamente, necesitará una función en el objeto visual personalizado denominada `enumerateObjectInstances`. Esta función rellenará el panel de propiedades con objetos y también determinará dónde necesitan enlazarse los objetos en el elemento dataView.  

Este es el aspecto de una configuración típica:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Propiedades

Las propiedades de `enumerateObjectInstances` reflejarán las propiedades que haya definido en sus funciones. Vea el ejemplo al final de la página.

### <a name="objects-selector"></a>Selector de objetos

El selector de `enumerateObjectInstances` determina dónde se enlazará cada objeto en el elemento dataView. Hay cuatro opciones disponibles.

#### <a name="static"></a>static

Este objeto se enlazará a los metadatos `dataviews[index].metadata.objects`.

```typescript
selector: null
```

#### <a name="columns"></a>columns

Este objeto se enlazará a columnas con el objeto `QueryName` correspondiente.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Este objeto se enlazará al elemento para el que hemos creado un elemento de `selectionID`. En este ejemplo, se da por hecho que hemos creado elementos de `selectionID` para algunos elementos de puntos de datos, y que los estamos recorriendo en bucle.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Identidad del ámbito

Este objeto se enlazará a valores específicos en la intersección de grupos. Por ejemplo, si tengo categorías `["Jan", "Feb", "March", ...]` y series`["Small", "Medium", "Large"]`, puede que quiera tener un objeto en la intersección de los valores `Feb` y `Large` que coincidan. Para lograr esto, podría obtener el valor `DataViewScopeIdentity` de ambas columnas, enviarlos a la variable `identities` y, después, usar esta sintaxis con el selector.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Ejemplo

En este ejemplo, se muestra la apariencia de un elemento objectEnumeration para un objeto customColor con una propiedad `fill`. Queremos que este objeto se enlace estáticamente a `dataViews[index].metadata.objects`

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
