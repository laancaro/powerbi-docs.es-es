---
title: 'DAX: Evitar el uso de FILTER como argumento de filtro'
description: Guía de uso de la función FILTER como argumento de filtro.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 6abcb77e3eb534e8b5d20c1d5567c117cbb97ffe
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161441"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Evitar el uso de FILTER como argumento de filtro

Como modelador de datos, es habitual que escriba expresiones DAX que se deban evaluar en un contexto de filtro modificado. Por ejemplo, puede escribir una definición de medida para calcular las ventas de "productos de margen alto". Este cálculo se describe más adelante.

> [!NOTE]
> Este artículo resulta especialmente pertinente para los cálculos de modelos que aplican filtros a las tablas de importación.

Las funciones DAX [CALCULATE](/dax/calculate-function-dax) y [CALCULATETABLE](/dax/calculatetable-function-dax) son importantes y útiles. Le permiten escribir cálculos que quitan o agregan filtros, o que modifican las rutas de acceso de las relaciones. Se realiza pasando argumentos de filtro, que son expresiones booleanas, expresiones de tabla o funciones de filtro especiales. En este artículo solo trataremos las expresiones booleanas y de tabla.

Valore la siguiente definición de medida, que calcula las ventas de productos de color rojo mediante una expresión de tabla. Reemplazará todos los filtros que se puedan aplicar a la tabla **Producto**.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

La función CALCULATE acepta una expresión de tabla devuelta por la función DAX [FILTER](/dax/filter-function-dax), que evalúa su expresión de filtro para cada fila de la tabla **Producto**. Obtiene el resultado correcto: el de ventas de los productos rojos. Sin embargo, se podría lograr de forma mucho más eficaz mediante el uso de una expresión booleana.

Esta es una definición de medida mejorada, que usa una expresión booleana en lugar de la expresión de tabla. La función DAX [KEEPFILTERS](/dax/keepfilters-function-dax) garantiza que se conservan los filtros existentes aplicados a la columna de **Color** y no se sobrescriban.

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

Se recomienda pasar argumentos de filtro como expresiones booleanas, siempre que sea posible. Se debe a que las tablas de modelo de importación son almacenes de columnas en memoria. Están optimizadas explícitamente para filtrar de forma eficaz las columnas de esta manera.

Sin embargo, hay restricciones que se aplican a expresiones booleanas cuando se usan como argumentos de filtro. Son las siguientes:

- No pueden comparar unas columnas con otras.
- No pueden hacer referencia a una medida.
- No pueden usar funciones CALCULATE anidadas.
- No pueden usar funciones que examinen o devuelvan una tabla.

Esto significa que necesitará usar expresiones de tabla para requisitos de filtro más complejos.

Tome ahora una definición de medida diferente.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

Un _producto de margen alto_ es aquel que tiene una lista de precios de venta superior al doble de su costo estándar. En este ejemplo se debe usar la función FILTER. Se debe a que la expresión de filtro es demasiado compleja para una expresión booleana.

Este es otro ejemplo. Esta vez, el requisito es calcular las ventas, pero solo para los meses en los que se haya logrado un beneficio.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

En este ejemplo también se debe usar la función FILTER. Se debe a que es necesario evaluar la medida **Beneficio** para eliminar los meses en los que no se logró un beneficio. No es posible usar una medida en una expresión booleana cuando se usa como un argumento de filtro.

## <a name="recommendations"></a>Recomendaciones

Para obtener el mejor rendimiento, se recomienda usar expresiones booleanas como argumentos de filtro, siempre que sea posible.

Por lo tanto, la función FILTER solo debe usarse cuando sea necesario. Puede utilizarla para realizar comparaciones de columnas complejas de filtro. Estas comparaciones de columnas pueden implicar:

- Medidas
- Otras columnas
- Uso de la función DAX [OR](/dax/or-function-dax) o el operador lógico OR (||)

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Referencia de expresiones de análisis de datos (DAX)](/dax/)
- [Funciones de filtro (DAX)](/dax/filter-function-dax)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
