---
title: 'DAX: Uso de COUNTROWS en lugar de COUNT'
description: Instrucciones sobre cuándo usar las funciones COUNTROWS.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: fd3b50e9016298db8b692d6a2f3549b770f143e8
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700671"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: Uso de COUNTROWS en lugar de COUNT

Como modelador de datos, en ocasiones es posible que tenga que escribir una expresión DAX que cuente las filas de una tabla. La tabla puede ser una tabla modelo o una expresión que devuelve una tabla.

Su requisito se puede satisfacer de dos formas. Puede usar la función [COUNT](/dax/count-function-dax) para contar los valores de la columna o bien puede usar la función [COUNTROWS](/dax/countrows-function-dax) para contar las filas de la tabla. Ambas funciones lograrán el mismo resultado, siempre y cuando la columna contada no contenga ningún valor en blanco.

La siguiente definición de medida presenta un ejemplo. Calcula el número de valores de columna **OrderDate**.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Siempre que la granularidad de la tabla **Sales** sea una fila por pedido de venta y la columna **OrderDate** no contenga ningún valor en blanco, la medida devolverá un resultado correcto,

pero la siguiente definición de medida es una solución mejor.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Hay tres motivos por los que la segunda definición de medida es mejor:

- Es más eficaz y, por lo tanto, funcionará mejor.
- No tiene en cuenta los valores en blanco incluidos en las columnas de la tabla.
- La intención de la fórmula es más clara, hasta el punto de ser autodescriptiva.

## <a name="recommendation"></a>Recomendación

Si su intención es contar las filas de una tabla, le recomendamos que use siempre la función COUNTROWS.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Referencia de expresiones de análisis de datos (DAX)](/dax/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
