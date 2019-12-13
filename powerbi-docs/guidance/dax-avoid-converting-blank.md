---
title: 'DAX: Impedimento de la conversión de BLANK en valores'
description: Instrucciones sobre la conversión de BLANK en valores.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700395"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Impedimento de la conversión de BLANK en valores

Como modelador de datos, al escribir expresiones de medida es posible que se encuentre casos en los que no se puede devolver un valor significativo. En tales casos, es posible que le tiente devolver un valor (por ejemplo, cero). Le recomendamos que decida detenidamente si este diseño es eficaz y práctico.

Tenga en cuenta la siguiente definición de medida, que convierte de forma explícita los resultados en blanco en cero.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Tenga en cuenta otra definición de medida, que también convierte los resultados en blanco en cero.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

La función [DIVIDE](/dax/divide-function-dax) divide la medida **Profit** por la medida **Sales**. Si el resultado es cero o está en blanco, se devolverá el tercer argumento: el resultado alternativo (que es opcional). En este ejemplo, dado que se pasa cero como resultado alternativo, se garantiza que la medida siempre devolverá un valor.

Estos diseños de medida son ineficaces y dan lugar a diseños de informes deficientes.

Cuando se agregan a un objeto visual de informe, Power BI intenta recuperar todas las agrupaciones del contexto del filtro. La evaluación y la recuperación de resultados de consultas de gran tamaño suelen comportar una representación lenta de los informes. Cada medida de ejemplo convierte de forma eficaz un cálculo disperso en uno denso, lo que fuerza que Power BI use más memoria de la necesaria.

Además, si hay demasiadas agrupaciones, los usuarios de los informes podrían saturarse.

Veamos lo que sucede cuando se agrega la medida **Profit Margin** a un objeto visual de tabla, agrupando por cliente.

![Un objeto visual de tabla tiene tres columnas: Customer (Cliente), Sales (Ventas) y Profit Margin (Margen de beneficio). La tabla muestra aproximadamente 10 filas de datos, pero la barra de desplazamiento vertical indica que hay muchas más filas que se podrían mostrar. La columna Sales no muestra ningún valor. La columna Profit Margin muestra solo cero.](media/dax-avoid-converting-blank/table-visual-poor.png)

El objeto visual de tabla muestra un enorme número de filas (en realidad hay 18 484 clientes en el modelo, por lo que la tabla intenta mostrarlos todos). Tenga en cuenta que los clientes de la vista no han conseguido ninguna venta. Pero como la medida **Profit Margin** siempre devuelve un valor, estos se muestran.

> [!NOTE]
> Cuando hay demasiados puntos de datos para mostrarlos en un objeto visual, Power BI puede usar las estrategias de reducción de datos para quitar o resumir los resultados de consultas de gran tamaño. Para obtener más información, consulte [Límites de punto de datos y estrategias por tipo de objeto visual](../visuals/power-bi-data-points.md).

Veamos lo que sucede cuando se mejora la definición de la medida **Profit Margin**. Ahora devuelve un valor solo si la medida **Sales** no está en blanco (o cero).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

El objeto visual de tabla ahora muestra solo los clientes que han tenido ventas en el contexto de filtro actual. La medida mejorada da como resultado una experiencia más eficaz y práctica para los usuarios de los informes.

![El mismo objeto visual de tabla ahora muestra cuatro filas de datos. Cada fila es para un cliente que tiene un valor de ventas y los valores de Profit Margin no son cero.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Si es necesario, puede configurar un objeto visual para mostrar todas las agrupaciones (que devuelven valores o en blanco) dentro del contexto de filtro habilitando la opción [Mostrar elementos sin datos](../desktop-show-items-no-data.md).

## <a name="recommendation"></a>Recomendación

Se recomienda que las medidas devuelvan un valor en blanco si no se puede devolver un valor significativo.

Este enfoque de diseño es eficaz, lo que permite a Power BI representar los informes con mayor rapidez. Además, la devolución de un valor BLANK es más indicada ya que, de forma predeterminada, los objetos visuales de los informes eliminan las agrupaciones cuando los resúmenes están en blanco.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Referencia de expresiones de análisis de datos (DAX)](/dax/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
