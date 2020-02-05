---
title: Utilidades de interactividad de objetos visuales de Power BI
description: En el artículo se describe cómo agregar selecciones en objetos visuales de Power BI mediante el uso de utilidades de interactividad
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818695"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Utilidades de interactividad de objetos visuales de Microsoft Power BI

InteractivityUtils es un conjunto de funciones y clases que tienen como fin simplificar la implementación de la selección cruzada y del filtrado cruzado de objetos visuales personalizados de Power BI.

## <a name="installation"></a>Instalación

> [!NOTE]
> Si sigue usando la versión anterior de powerbi-visuals-tools (un número de versión anterior a 3.x.x), instale la versión nueva de las herramientas (3.x.x).

> [!IMPORTANT]
> Las actualizaciones nuevas de las utilidades de interactividad solo admitirán la versión más reciente de las herramientas. [Más información sobre cómo actualizar el código del objeto visual para su uso con las herramientas más recientes](migrate-to-new-tools.md)

Para instalar el paquete, debe ejecutar el comando siguiente en el directorio con el objeto visual personalizado actual:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

Desde la versión 3.0 o versiones posteriores, también tiene que instalar ```powerbi-models``` para resolver las dependencias.

```bash
npm install powerbi-models --save
```

Para usar las utilidades de interactividad, debe importar el componente necesario en el código fuente del elemento visual.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>Inclusión de artefactos de CSS en el objeto visual personalizado

Para usar el paquete con los objetos visuales personalizados, debe importar el archivo CSS siguiente al archivo `your.less`:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Como resultado, tendrá la estructura de archivos siguiente:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Debe importar el archivo .css como archivo .less, porque las herramientas de objetos visuales de Power BI encapsulan las reglas de CSS externas.

## <a name="usage"></a>Uso

### <a name="define-interface-for-data-points"></a>Definición de la interfaz para los puntos de datos

Por lo general, los puntos de datos contienen selecciones y valores. La interfaz extiende la interfaz de `SelectableDataPoint`. `SelectableDataPoint` ya contiene propiedades:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

El primer paso del uso de las utilidades de interactividad es crear una instancia de las utilidades de interactividad y guardar el objeto como propiedad del objeto visual.

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

El segundo paso es extender la clase de comportamiento base:

> [!NOTE]
> BaseBehavior se presentó en la [versión 5.6.x de las utilidades de interactividad](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Si usa la versión anterior, cree una clase de comportamiento a partir del ejemplo siguiente (la clase `BaseBehavior` es la misma):

Defina la interfaz para las opciones de clase de comportamiento:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Defina una clase para `visual behavior`. La clase es responsable de controlar los eventos de mouse `click`, `contextmenu`.
Cuando un usuario hace clic en los elementos de datos, el objeto visual llama al controlador de selección para seleccionar los puntos de datos. Si el usuario hace clic en el elemento de fondo del objeto visual, llamará al controlador Clear Selection. Y la clase tiene los métodos correspondientes: `bindClick`, `bindClearCatcher`, `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

O bien, puede extender la clase `BaseBehavior`:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Para controlar el clic en los elementos, llame al método `on` del objeto de selección D3 (para elementsSelection y clearCatcherSelection también):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Agregue un controlador similar para el evento `contextmenu` para llamar al método `showContextMenu` del administrador de selección:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

Las utilidades de interactividad llaman a los métodos `bindEvents` para asignar funciones a los controladores, agregan llamadas de `bindClick`, `bindClearCatcher` y `bindContextMenu` en el método `bindEvents`:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

El método `renderSelection` es responsable de actualizar el estado del objeto visual de los elementos del gráfico.

Método `renderSelection` de implementación de ejemplo:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

El último paso es crear una instancia de `visual behavior` y la llamada del método `bind` de la instancia de utilidades de interactividad:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` es el objeto de selección D3, que representa todos los elementos de selección en el objeto visual.

* `select(this.target)` es el objeto de selección D3, que representa los elementos DOM principales del objeto visual.

* `this.categories` son puntos de datos con elementos, donde la interfaz es `VisualDataPoint` (o `categories: VisualDataPoint[];`).

* `this.behavior` es una instancia nueva de `visual behavior`

  creada en el constructor del objeto visual:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

Ahora, el objeto visual está listo para controlar la selección.

## <a name="next-steps"></a>Pasos siguientes

* [Lea cómo controlar las selecciones en el cambio de marcadores](bookmarks-support.md#visuals-with-selection).

* [Lea cómo agregar un menú contextual para los puntos de datos de objetos visuales](context-menu.md).

* [Lea cómo usar el administrador de selección para agregar selecciones a los objetos visuales de Power BI](selection-api.md)
