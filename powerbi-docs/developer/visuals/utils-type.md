---
title: Introducción al uso de tipos de utilidad en los objetos visuales de Power BI
description: En este artículo se describe cómo usar las utilidades de SVG para ampliar los tipos básicos de los objetos visuales de Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 206fda4e64dd13782753bfd067c962b3079bb4ff
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818741"
---
# <a name="type-utils"></a>Tipos de utilidad

TypeUtils es un conjunto de funciones y clases para extender los tipos básicos de los objetos visuales de Power BI.

## <a name="installation"></a>Instalación

Para instalar el paquete, debe ejecutar el comando siguiente en el directorio con el objeto visual personalizado actual:

npm install powerbi-visuals-utils-typeutils --save Este comando instala el paquete y agrega un paquete como dependencia al archivo package.json

## <a name="double"></a>Doble

`Double` proporciona funciones para manipular la precisión de los números.

El módulo proporciona las siguientes funciones:

### <a name="pow10"></a>pow10

Esta función devuelve la potencia de 10.

```typescript
function pow10(exp: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Esta función devuelve un logaritmo en base 10 del número.

```typescript
function log10(val: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Esta función devuelve una potencia de 10 que representa la precisión del número.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Esta función comprueba si una diferencia entre dos números es menor que la precisión proporcionada.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Esta función comprueba si el primer valor es menor que el segundo.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Esta función comprueba si el primer valor es menor o igual que el segundo.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Esta función comprueba si el primer valor es mayor que el segundo.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Esta función comprueba si el primer valor es mayor o igual que el segundo.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Esta función calcula el límite inferior del número con la precisión proporcionada.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Esta función aplica `ceils` al número con la precisión proporcionada.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Esta función calcula el límite inferior del número a la precisión proporcionada.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Esta función aplica `ceils` al número a la precisión proporcionada.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Esta función redondea el número a la precisión proporcionada.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Esta función devuelve un número entre un mínimo y un máximo.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Esta función redondea el número.

```typescript
function round(x: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Esta función quita el ruido decimal.

```typescript
function removeDecimalNoise(value: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Esta función comprueba si el número es un entero.

```typescript
function isInteger(value: number): boolean;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Esta función incrementa el número por el número proporcionado y devuelve el número redondeado.

```typescript
function toIncrement(value: number, increment: number): number;
```

Ejemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototipo

`Prototype` proporciona funciones para heredar objetos.

El módulo proporciona las siguientes funciones:

## <a name="inherit"></a>inherit

Esta función devuelve un objeto nuevo con el objeto proporcionado como su prototipo.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Ejemplo:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Esta función devuelve un objeto nuevo con el objeto proporcionado como su prototipo si, y solo si, no se ha establecido el prototipo.

```typescript
function inheritSingle<T>(obj: T): T;
```

Ejemplo:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` permite convertir píxeles en puntos y puntos en píxeles.

El módulo proporciona las siguientes funciones:

## <a name="tostring"></a>toString

Esta función convierte el valor de píxel en una cadena.

```typescript
function toString(px: number): string;
```

Ejemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Esta función convierte el valor de punto proporcionado en el valor de píxel y devuelve la interpretación de la cadena.

```typescript
function fromPoint(pt: number): string;
```

Ejemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Esta función convierte el valor de punto proporcionado en el valor de píxel.

```typescript
function fromPointToPixel(pt: number): number;
```

Ejemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Esta función convierte el valor de píxel en el valor de punto.

```typescript
function toPoint(px: number): number;
```

Ejemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
