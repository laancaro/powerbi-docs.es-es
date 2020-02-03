---
title: Introducción al uso de utilidades de SVG en los objetos visuales de Power BI
description: En este artículo se describe cómo usar las utilidades de SVG para simplificar las manipulaciones de SVG para objetos visuales de Power BI personalizados.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 612c253e53cdaec5819387548354595c8bd94fa0
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819316"
---
# <a name="svg-utils"></a>Utilidades de SVG

SVGUtils es un conjunto de funciones y clases para simplificar las manipulaciones de SVG para objetos visuales de Power BI personalizados

## <a name="installation"></a>Instalación

Para instalar el paquete, debe ejecutar el comando siguiente en el directorio con el objeto visual actual:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

El módulo `CssConstants` proporciona la función y la interfaz especiales para trabajar con los selectores de clase.

El módulo `powerbi.extensibility.utils.svg.CssConstants` proporciona la siguiente función e interfaz:

## <a name="classandselector"></a>ClassAndSelector

Esta interfaz describe propiedades comunes del selector de clases.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Esta función crea una instancia de ClassAndSelector con el nombre de la clase especificado.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Ejemplo:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

`manipulation` proporciona algunas funciones especiales para generar cadenas para usar con la propiedad de transformación de SVG.

El módulo proporciona las siguientes funciones:

### <a name="translate"></a>translate

Esta función crea una cadena de traducción para usar con la propiedad de transformación SVG.

```typescript
function translate(x: number, y: number): string;
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Esta función crea una cadena translateX para usar con la propiedad de transformación de SVG.

```typescript
function translateXWithPixels(x: number): string;
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Esta función crea una cadena de traducción para usar con la propiedad de transformación SVG.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Esta función crea una cadena de traducción y rotación para usar con la propiedad de transformación de SVG.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

Esta función crea una cadena de escala para usar en una propiedad de transformación de CSS.

```typescript
function scale(scale: number): string;
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Esta función crea una cadena de transformación y origen para usar en una propiedad de transformación y origen de CSS.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Esta función obliga a que se completen todas las transiciones de D3.

```typescript
function flushAllD3Transitions(): void;
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Esta función analiza la cadena de transformación con el valor "translate (x,y)".

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Esta función crea una flecha.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Ejemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

El módulo `Rect` proporciona algunas funciones especiales para manipular rectángulos.

El módulo proporciona las siguientes funciones:

### <a name="getoffset"></a>getOffset

Esta función devuelve un desplazamiento del rectángulo.

```typescript
function getOffset(rect: IRect): IPoint;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Esta función devuelve el tamaño del rectángulo.

```typescript
function getSize(rect: IRect): ISize;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Esta función modifica el tamaño del rectángulo.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Esta función devuelve una posición derecha del rectángulo.

```typescript
function right(rect: IRect): number;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Esta función devuelve una posición inferior del rectángulo.

```typescript
function bottom(rect: IRect): number;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Esta función devuelve una posición superior izquierda del rectángulo.

```typescript
function topLeft(rect: IRect): IPoint;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Esta función devuelve una posición superior derecha del rectángulo.

```typescript
function topRight(rect: IRect): IPoint;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Esta función devuelve una posición inferior izquierda del rectángulo.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Esta función devuelve una posición inferior derecha del rectángulo.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Ejemplo

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clon

Esta función crea una copia del rectángulo.

```typescript
function clone(rect: IRect): IRect;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Esta función convierte el rectángulo en una cadena.

```typescript
function toString(rect: IRect): string;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Esta función aplica el desplazamiento dado al rectángulo.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Esta función agrega el primer rectángulo al segundo.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Esta función devuelve el punto más cercano del rectángulo al punto especificado.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Esta función compara los rectángulos y devuelve true si son iguales.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Esta función compara los rectángulos considerando la precisión de los valores.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Esta función comprueba si el rectángulo está vacío.

```typescript
function isEmpty(rect: IRect): boolean;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Esta función comprueba si el rectángulo contiene el punto.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Esta función comprueba si los rectángulos se cruzan.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Esta función devuelve una intersección de rectángulos.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Esta función combina rectángulos.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Esta función devuelve una punto central del rectángulo.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Ejemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>puntero

El módulo `pointer` proporciona una función especial para obtener la posición del puntero.

El módulo proporciona la función siguiente:

### <a name="getcoordinates"></a>getCoordinates

Esta función devuelve la posición del puntero.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Ejemplo:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
