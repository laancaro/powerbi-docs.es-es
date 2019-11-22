---
title: Selecciones de puntos de datos de objetos visuales de Power BI
description: En el artículo se describe cómo agregar selecciones a objetos visuales de Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 5f5e4769c750406a02ead656af551133fbceb738
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061900"
---
# <a name="add-interactivity-into-visual-by-power-bi-visuals-selections"></a>Incorporación de interactividad en un objeto visual mediante las selecciones de objetos visuales de Power BI

Power BI proporciona dos maneras de interacción entre los objetos visuales: selección y filtrado. En el ejemplo siguiente se muestra cómo seleccionar los elementos de un elemento visual y cómo notificar a otros objetos visuales del informe sobre el nuevo estado de selección.

El objeto `Selection` corresponde a la interfaz:

```typescript
export interface ISelectionId {
    equals(other: ISelectionId): boolean;
    includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
    getKey(): string;
    getSelector(): Selector;
    getSelectorsByColumn(): SelectorsByColumn;
    hasIdentity(): boolean;
}
```

## <a name="how-to-use-selectionmanager-to-select-data-points"></a>Uso de SelectionManager para seleccionar puntos de datos

El objeto host del objeto visual proporciona un método para crear una instancia del administrador de selección. El administrador de selección es responsable de seleccionar, anular la selección, mostrar el menú contextual, almacenar las selecciones actuales y comprobar el estado de la selección. Además, el administrador de selección tiene los métodos correspondientes para esas acciones.

### <a name="create-instance-of-selection-manager"></a>Creación de una instancia del administrador de selección

Para usar el administrador de selección, debe crear la instancia de administrador de selección. Por lo general, los objetos visuales crean la instancia del administrador de selección en `constructor` del objeto visual.

```typescript
export class Visual implements IVisual {
    private target: HTMLElement;
    private host: IVisualHost;
    private selectionManager: ISelectionManager;
    // ...
    constructor(options: VisualConstructorOptions) {
        this.host = options.host;
        // ...
        this.selectionManager = this.host.createSelectionManager();
    }
    // ...
}
```

### <a name="create-instance-of-selection-builder"></a>Creación de una instancia del generador de selección

Cuando se crea la instancia del administrador de selección, debe crear `selections` para cada punto de datos del objeto visual. El objeto host del objeto visual proporciona el método `createSelectionIdBuilder` para generar la selección para cada punto de datos. Este método devuelve una instancia del objeto con la interfaz `powerbi.visuals.ISelectionIdBuilder`:

```typescript
export interface ISelectionIdBuilder {
    withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
    withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
    withMeasure(measureId: string): this;
    withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
    withTable(table: DataViewTable, rowIndex: number): this;
    createSelectionId(): ISelectionId;
}
```

Este objeto tiene métodos correspondientes para crear `selections` para diferentes tipos de asignaciones de vistas de datos.

> [!NOTE]
> Los métodos `withTable`, `withMatrixNode` se introdujeron en la API 2.5.0 de los objetos visuales de Power BI.
> Si necesita usar selecciones para las asignaciones de vistas de datos de tabla o matriz, debe actualizar la versión de la API a 2.5.0 o superior.

### <a name="create-selections-for-categorical-data-view-mapping"></a>Creación de selecciones para la asignación de vistas de datos de categóricos

Vamos a revisar cómo se representan las selecciones en la asignación de vistas de datos categóricos para el conjunto de datos de ejemplo:

| Fabricante | Tipo | Valor |
| - | - | - |
| Chrysler | Automóvil nacional | 28883 |
| Chrysler | Camión nacional | 117131 |
| Chrysler | Automóvil importado | 0 |
| Chrysler | Camión importado | 6362 |
| Ford | Automóvil nacional | 50032 |
| Ford | Camión nacional | 122446 |
| Ford | Automóvil importado | 0 |
| Ford | Camión importado | 0 |
| GM | Automóvil nacional | 65426 |
| GM | Camión nacional | 138122 |
| GM | Automóvil importado | 197 |
| GM | Camión importado | 0 |
| Honda | Automóvil nacional | 51450 |
| Honda | Camión nacional | 46115 |
| Honda | Automóvil importado | 2932 |
| Honda | Camión importado | 0 |
| Nissan | Automóvil nacional | 51476 |
| Nissan | Camión nacional | 47343 |
| Nissan | Automóvil importado | 5485 |
| Nissan | Camión importado | 1430 |
| Toyota | Automóvil nacional | 55643 |
| Toyota | Camión nacional | 61227 |
| Toyota | Automóvil importado | 20799 |
| Toyota | Camión importado | 23614 |

Y el objeto visual usa esta asignación de vistas de datos:

```json
{
    "dataRoles": [
        {
            "displayName": "Columns",
            "name": "columns",
            "kind": "Grouping"
        },
        {
            "displayName": "Rows",
            "name": "rows",
            "kind": "Grouping"
        },
        {
            "displayName": "Values",
            "name": "values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "categorical": {
                "categories": {
                    "for": {
                        "in": "columns"
                    }
                },
                "values": {
                    "group": {
                        "by": "rows",
                        "select": [
                            {
                                "for": {
                                    "in": "values"
                                }
                            }
                        ]
                    }
                }
            }
        }
    ]
}
```

En el ejemplo, `Manafacturer` es `columns` y `Type` es `rows`. Hay una serie creada mediante la agrupación de valores por `rows` (`Type`).

Además, el objeto visual debe poder segmentar los datos por `Manafacturer` y `Type` también.

Por ejemplo, cuando el usuario selecciona `Chrysler` por `Manafacturer`, otros objetos visuales deberían mostrar los datos siguientes:

| Fabricante | Tipo | Valor |
| - | - | - |
| **Chrysler** | Automóvil nacional | 28883 |
| **Chrysler** | Camión nacional | 117131 |
| **Chrysler** | Automóvil importado | 0 |
| **Chrysler** | Camión importado | 6362 |

Cuando el usuario selecciona `Import Car` por `Type` (selecciona datos por serie), otros objetos visuales deberían mostrar estos datos:

| Fabricante | Tipo | Valor |
| - | - | - |
| Chrysler | **Automóvil importado** | 0 |
| Ford | **Automóvil importado** | 0 |
| GM | **Automóvil importado** | 197 |
| Honda | **Automóvil importado** | 2932 |
| Nissan | **Automóvil importado** | 5485 |
| Toyota | **Automóvil importado** | 20799 |

![El objeto visual con selecciones para categorías y series](media/visual-selections-sample.png)

Debe rellenar las cestas de datos del objeto visual.

![Cestas de datos del objeto visual con selecciones](media/visual-selections-databuckets.png)

Hay `Manafacturer` como categoría (columnas), `Type` como serie (filas) y `Value` como `Values` para la serie.

> [!NOTE]
> Se requieren los `Values` para la serie, porque según la asignación de vistas de datos, el objeto visual espera que los `Values` se agrupen según los datos de `Rows`.

#### <a name="create-selections-for-categories"></a>Creación de selecciones para categorías

```typescript
// categories
const categories = dataView.categorical.categories;

// create label for 'Manafacturer' column
const p = document.createElement("p") as HTMLParagraphElement;
p.innerText = categories[0].source.displayName.toString();
this.target.appendChild(p);

// get count of category elements
const categoriesCount = categories[0].values.length;

// iterate all categories to generate selection and create button elements to use selections
for (let categoryIndex = 0; categoryIndex < categoriesCount; categoryIndex++) {
    const categoryValue: powerbi.PrimitiveValue = categories[0].values[categoryIndex];

    const categorySelectionId = this.host.createSelectionIdBuilder()
        .withCategory(categories[0], categoryIndex) // we have only one category (only one `Manafacturer` column)
        .createSelectionId();
    this.dataPoints.push({
        value: categoryValue,
        selection: categorySelectionId
    });
    console.log(categorySelectionId);

    // create button element to apply selection on click
    const button = document.createElement("button") as HTMLButtonElement;
    button.value = categoryValue.toString();
    button.innerText = categoryValue.toString();
    button.addEventListener("click", () => {
        // handle click event to apply correspond selection
        this.selectionManager.select(categorySelectionId);
    });
    this.target.appendChild(button);
}
```

En el código de ejemplo puede ver que se recorren en iteración todas las categorías. Y en cada iteración llamamos a `createSelectionIdBuilder` para crear la selección siguiente para cada categoría llamando al método `withCategory` del generador de selección. El método `createSelectionId` se utiliza como método final para devolver el objeto `selection` generado.

En el método `withCategory`, pasamos la columna de `category`, en el ejemplo es `Manafacturer` y el índice del elemento de categoría.

#### <a name="create-selections-for-series"></a>Creación de selecciones para la serie

```typescript
// get groupped values for series
const series: powerbi.DataViewValueColumnGroup[] = dataView.categorical.values.grouped();

// create label for 'Type' column
const p2 = document.createElement("p") as HTMLParagraphElement;
p2.innerText = dataView.categorical.values.source.displayName;
this.target.appendChild(p2);

// iterate all series to generate selection and create button elements to use selections
series.forEach( (ser: powerbi.DataViewValueColumnGroup) => {
    // create selection id for series
    const seriesSelectionId = this.host.createSelectionIdBuilder()
        .withSeries(dataView.categorical.values, ser)
        .createSelectionId();

    this.dataPoints.push({
        value: ser.name,
        selection: seriesSelectionId
    });

    // create button element to apply selection on click
    const button = document.createElement("button") as HTMLButtonElement;
    button.value =ser.name.toString();
    button.innerText = ser.name.toString();
    button.addEventListener("click", () => {
        // handle click event to apply correspond selection
        this.selectionManager.select(seriesSelectionId);
    });
    this.target.appendChild(button);
});
```

### <a name="create-selections-for-table-data-view-mapping"></a>Creación de selecciones para asignación de vistas de datos de tabla

Ejemplo de asignación de vistas de datos de tabla

```json
{
    "dataRoles": [
        {
            "displayName": "Values",
            "name": "values",
            "kind": "GroupingOrMeasure"
        }
    ],
    "dataViewMappings": [
        {
            "table": {
                "rows": {
                    "for": {
                        "in": "values"
                    }
                }
            }
        }
    ]
}
```

Para crear una selección para cada fila de la asignación de vistas de datos de tabla, debe llamar al método `withTable` del generador de selección.

```typescript
public update(options: VisualUpdateOptions) {
    const dataView = options.dataViews[0];
    dataView.table.rows.forEach((row: DataViewTableRow, rowIndex: number) => {
        this.target.appendChild(rowDiv);
        const selection: ISelectionId = this.host.createSelectionIdBuilder()
            .withTable(dataView.table, rowIndex)
            .createSelectionId();
    }
}
```

El código del objeto visual recorre en iteración las filas de la tabla y cada fila llama al método `withTable` de tabla. Los parámetros del método `withTable` son el objeto `table` y el índice de la fila de la tabla.

### <a name="create-selections-for-matrix-data-view-mapping"></a>Creación de selecciones para asignación de vistas de datos de matriz

```typescript
public update(options: VisualUpdateOptions) {
    const host = this.host;
    const rowLevels: powerbi.DataViewHierarchyLevel[] = dataView.matrix.rows.levels;
    const columnLevels: powerbi.DataViewHierarchyLevel[] = dataView.matrix.rows.levels;

    // iterate rows hierarchy
    nodeWalker(dataView.matrix.rows.root, rowLevels);
    // iterate columns hierarchy
    nodeWalker(dataView.matrix.columns.root, columnLevels);

    function nodeWalker(node: powerbi.DataViewMatrixNode, levels: powerbi.DataViewHierarchyLevel[]) {
        const nodeSelection = host.createSelectionIdBuilder().withMatrixNode(node, levels);

        if (node.children && node.children.length) {
            node.children.forEach(child => {
                nodeWalker(child, levels);
            });
        }
    }
}
```

En el ejemplo, `nodeWalker` llama de manera recursiva a cada nodo y a los nodos secundarios.

`nodeWalker` crea un objeto `nodeSelection` en cada llamada. Y cada `nodeSelection` representa la `selection` de los nodos correspondientes.

## <a name="select-datapoints-to-slice-other-visuals"></a>Selección de puntos de datos para segmentar otros objetos visuales

En los códigos de ejemplo de las selecciones para la asignación de vistas de datos categóricos, pudo ver que creamos un controlador de clics para los elementos de botón. El controlador llama al método `select` del administrador de selección y pasa el objeto de la selección.

```typescript
button.addEventListener("click", () => {
    // handle click event to apply correspond selection
    this.selectionManager.select(categorySelectionId);
});
```

La interfaz del método `select` es

```typescript
interface ISelectionManager {
    // ...
    select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
    // ...
}
```

Puede ver que `select` puede aceptar la matriz de selecciones. Esto significa que el objeto visual puede seleccionar varios puntos de datos. El segundo parámetro `multiSelect` es responsable de la selección múltiple. Si el valor es true, Power BI no borra el estado de selección anterior y aplica la selección actual; de lo contrario, se restablecerá la selección anterior.

Escenario típico del uso de `multiSelect` que controla el estado del botón CTRL en un evento de clic.

```typescript
button.addEventListener("click", (mouseEvent) => {
    const multiSelect = (mouseEvent as MouseEvent).ctrlKey;
    this.selectionManager.select(seriesSelectionId, multiSelect);
});
```

## <a name="next-steps"></a>Pasos siguientes

* [Lea cómo usar las selecciones para vincular las propiedades de objeto visual a los puntos de datos](objects-properties.md#objects-selector).

* [Lea cómo controlar las selecciones en el cambio de marcadores](bookmarks-support.md#visuals-with-selection).

* [Lea cómo agregar un menú contextual para los puntos de datos de objetos visuales](context-menu.md).

* [Lea cómo usar InteractivityUtils para agregar selecciones a los objetos visuales de Power BI](utils-interactivity-selections.md).
