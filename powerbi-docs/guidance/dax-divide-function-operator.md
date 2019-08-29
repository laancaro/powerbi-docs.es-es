---
title: 'DAX: función DIVIDE frente al operador de división (/)'
description: Instrucciones sobre cuándo usar la función DIVIDE de DAX.
author: guyinacube
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/05/2019
ms.author: v-pemyer
ms.openlocfilehash: d22491ee314ebcebd4479c4e57dbfdf7a6a1ffdb
ms.sourcegitcommit: c2197c3ad1d747b4ad490ab75771a0d32d0ae208
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "70010446"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: función DIVIDE frente al operador de división (/)

Este artículo va dirigido a los modeladores de datos que definen expresiones DAX.

## <a name="background"></a>Fondo

Al escribir una expresión DAX para dividir un numerador mediante un denominador, puede usar la función [DIVIDE](/dax/divide-function-dax) o el operador de división (/-barra diagonal).

Cuando se usa la función DIVIDE, se deben pasar expresiones de numerador y denominador. Opcionalmente, puede pasar un valor que representa un resultado alternativo.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

La función DIVIDE se ha diseñado para controlar automáticamente los casos de división entre cero. Si no se pasa un resultado alternativo y el denominador es cero o está en blanco, la función devuelve un valor en blanco. Si se pasa un resultado alternativo, se devuelve, en lugar de ofrecer un valor en blanco.

La función DIVIDE es útil porque guarda la expresión para que no tenga que probar primero el valor del denominador. La función también está mejor optimizada para probar el valor del denominador que la función [IF](/dax/if-function-dax). El uso de DIVIDE también da lugar a una expresión más concisa y elegante.

## <a name="example"></a>Ejemplo

La siguiente expresión de medición genera una división segura, pero implica el uso de tres funciones DAX.

```dax

=IF(ISBLANK([Sales]) || [Sales] = 0, BLANK(), [Profit] / [Sales])

```

Esta expresión de medición consigue el mismo resultado, pero de forma más eficaz y elegante.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Recomendaciones

Se recomienda usar la función DIVIDE siempre que el denominador sea una expresión que _pueda_ devolver cero o un valor en blanco.

En el caso de que el denominador sea un valor constante, se recomienda el uso del operador de división. En este caso, la división tiene la garantía de que se realizará correctamente y la expresión funcionará mejor porque evitará pruebas innecesarias.

Debe considerar detenidamente si la función DIVIDE debe devolver un valor alternativo. En el caso de las medidas, normalmente se trata de un mejor diseño, ya que devuelven un valor en blanco. Esto se debe a que los objetos visuales de los informes eliminan las agrupaciones de forma predeterminada cuando los resúmenes están en blanco. Esto permite que el objeto visual se centre en los grupos en los que existen los datos. Si es necesario, puede configurar el objeto visual para mostrar todos los grupos (que devuelven valores o en blanco) dentro del contexto de filtro habilitando la opción "Mostrar elementos sin datos".
