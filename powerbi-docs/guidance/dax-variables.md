---
title: 'DAX: Uso de variables para mejorar las fórmulas'
description: Instrucciones sobre el uso de variables en las expresiones DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: f352cbbd7c42aa54ae876e73c0ed821eccda59c8
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700717"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: Uso de variables para mejorar las fórmulas

Como modelador de datos, escribir y depurar algunos cálculos DAX puede ser complejo. Es habitual que los requisitos de cálculos complejos impliquen a menudo la escritura de expresiones compuestas o complejas. Las expresiones compuestas pueden implicar el uso de muchas funciones anidadas y, posiblemente, la reutilización de la lógica de expresión.

El uso de variables en las fórmulas DAX le permite escribir cálculos complejos y eficaces. Las variables pueden:

- [Mejorar el rendimiento](#improve-performance)
- [Mejorar la legibilidad](#improve-readability)
- [Simplificar la depuración](#simplify-debugging)
- [Reducir la complejidad](#reduce-complexity)

En este artículo se mostrarán las tres primeras ventajas con una medida de ejemplo para el crecimiento de ventas de año a año (YoY). La fórmula del crecimiento de ventas YoY es la siguiente: ventas por período _menos ventas para el mismo período del año pasado, _dividido por_ las ventas del mismo período del año pasado.

Comencemos con la siguiente definición de medida.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

La medida genera el resultado correcto, pero veamos cómo se puede mejorar.

## <a name="improve-performance"></a>Mejorar el rendimiento

Observe que la fórmula repite la expresión que calcula "el mismo período del año pasado". Esta fórmula es ineficaz, ya que fuerza a Power BI a evaluar la misma expresión dos veces. La definición de la medida se puede hacer más eficaz usando una variable.

La siguiente definición de medida representa una mejora. Usa una expresión para asignar el resultado "del mismo período del año pasado" a una variable denominada **SalesPriorYear**. Entonces, la variable se usa dos veces en la expresión RETURN.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

La medida sigue generando el resultado correcto y lo hace en más o menos la mitad del tiempo de consulta.

## <a name="improve-readability"></a>Mejorar la legibilidad

En la definición de medida anterior, observe cómo la elección del nombre de la variable hace que la expresión RETURN sea más fácil de entender. La expresión es breve y autodescriptiva.

## <a name="simplify-debugging"></a>Simplificar la depuración

Las variables también pueden ayudarle a depurar una fórmula. Para probar una expresión asignada a una variable, debe reescribir temporalmente la expresión RETURN para generar la variable.

La siguiente definición de medida solo devuelve la variable **SalesPriorYear**. Observe cómo quita la marca de comentario de la expresión RETURN deseada. Con esta técnica puede revertirla fácilmente una vez concluida la depuración.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Reducir la complejidad

En versiones anteriores de DAX, las variables aún no eran compatibles. Las expresiones complejas que incorporaban nuevos contextos de filtro eran necesarias para usar las funciones DAX [EARLIER](/dax/earlier-function-dax) o [EARLIEST](/dax/earliest-function-dax) para hacer referencia a contextos de filtro externos. Desafortunadamente, para los modeladores de datos estas funciones eran difíciles de comprender y de usar.

Las variables siempre se evalúan fuera de los filtros a los que se aplica la expresión RETURN. Por este motivo, a la hora de usar una variable dentro de un contexto de filtro modificado, se obtiene el mismo resultado que con la función EARLIEST. Por lo tanto, se puede evitar el uso de las funciones EARLIER o EARLIEST. Es decir, ahora puede escribir fórmulas menos complejas y más fáciles de entender.

Observe la siguiente definición de columna calculada que se ha agregado a la tabla **Subcategoría**. Evalúa un rango para cada subcategoría de producto en función de los valores de la columna **Subcategory Sales** (Ventas por subcategoría).

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

La función EARLIER sirve para hacer referencia al valor de la columna **Subcategory Sales**_en el contexto de fila actual_.

La definición de la columna calculada se puede mejorar usando una variable en lugar de la función EARLIER. La variable **CurrentSubcategorySales** almacena el valor de la columna **Subcategory Sales**_en el contexto de fila actual_ y la expresión RETURN la usa en un contexto de filtro modificado.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- Artículo DAX [VAR](/dax/var-dax)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
