---
title: 'DAX: Uso de SELECTEDVALUE en lugar de VALUES'
description: Instrucciones sobre cuándo usar las funciones SELECTEDVALUE.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 6aef2c06cc62668ea7dea9fe404e294d1a5faa93
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700487"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX: Uso de SELECTEDVALUE en lugar de VALUES

Como modelador de datos, es posible que en ocasiones tenga que escribir una expresión DAX que compruebe si una columna está filtrada por un valor específico.

En versiones anteriores de DAX, este requisito se satisfacía de forma segura con un patrón que implicaba tres funciones DAX. Las funciones son [IF](/dax/if-function-dax), [HASONEVALUE](/dax/hasonevalue-function-dax) y [VALUES](/dax/values-function-dax). La siguiente definición de medida presenta un ejemplo. Calcula el importe del impuesto de ventas, pero solo de las ventas efectuadas a los clientes de Australia.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

En el ejemplo, la función HASONEVALUE devuelve TRUE solo si un valor único filtra la columna **Country-Region**. Si es TRUE, la función VALUES se compara con el texto literal "Australia". Si la función VALUES devuelve TRUE, la medida **Sales** se multiplica por 0,10 (que representa el 10%). Si la función HASONEVALUE devuelve FALSE (ya que más de un valor filtra la columna), la primera función IF devolverá un valor en blanco.

El uso de HASONEVALUE es una técnica defensiva. Es necesario porque es posible que varios valores filtren la columna **Country-Region**. En este caso, la función VALUES devuelve una tabla de varias filas. La comparación de una tabla de varias filas con un valor escalar genera un error.

## <a name="recommendation"></a>Recomendación

Se recomienda usar la función [SELECTEDVALUE](/dax/selectedvalue-function). Logra el mismo resultado que el patrón que se describe en este artículo, pero de forma más eficaz y elegante.

Con la función SELECTEDVALUE, ahora se reescribe la definición de la medida de ejemplo.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> Es posible pasar un valor de _resultado alternativo_ a la función SELECTEDVALUE. Se devuelve el valor de resultado alternativo cuando no se aplica ningún filtro (o se aplican varios) a la columna.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Referencia de expresiones de análisis de datos (DAX)](/dax/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
