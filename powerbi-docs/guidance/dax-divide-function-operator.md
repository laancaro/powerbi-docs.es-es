---
title: 'DAX: función DIVIDE frente al operador de división (/)'
description: Instrucciones sobre cuándo usar la función DIVIDE de DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c20a366ef657e851ef77a9649dbcc8b66b67dac0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74695206"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: función DIVIDE frente al operador de división (/)

Como modelador de datos, al escribir una expresión DAX para dividir un numerador por un denominador, puede usar la función [DIVIDE](/dax/divide-function-dax) o el operador de división (/: barra diagonal).

Cuando se usa la función DIVIDE, se deben pasar expresiones de numerador y denominador. Opcionalmente, puede pasar un valor que representa un _resultado alternativo_.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

La función DIVIDE se ha diseñado para controlar de forma automática los casos de división entre cero. Si no se pasa un resultado alternativo y el denominador es cero o está en blanco, la función devuelve un valor en blanco. Al pasar un resultado alternativo, se devuelve, en lugar de ofrecer un valor en blanco.

La función DIVIDE es útil porque guarda la expresión para que no tenga que probar primero el valor del denominador. La función también está mejor optimizada para probar el valor del denominador que la función [IF](/dax/if-function-dax). La mejora del rendimiento es importante, ya que la búsqueda de la división entre cero resulta costosa. El uso adicional de DIVIDE da lugar a una expresión más concisa y elegante.

## <a name="example"></a>Ejemplo

La siguiente expresión de medición genera una división segura, pero implica el uso de cuatro funciones DAX.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Esta expresión de medición consigue el mismo resultado, pero de forma más eficaz y elegante.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Recomendaciones

Se recomienda usar la función DIVIDE siempre que el denominador sea una expresión que _pueda_ devolver cero o un valor en blanco.

En el caso de que el denominador sea un valor constante, se recomienda el uso del operador de división. En este caso, la división tiene la garantía de que se realizará correctamente y la expresión funcionará mejor porque evitará pruebas innecesarias.

Considere detenidamente si la función DIVIDE debe devolver un valor alternativo. En cuanto a las medidas, suele ser un mejor diseño que devuelva BLANK si no se puede evaluar ningún resultado significativo. Para obtener más información, consulte [Impedimento de la conversión de BLANK en valores](dax-avoid-converting-blank.md).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Referencia de expresiones de análisis de datos (DAX)](/dax/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
