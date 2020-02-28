---
title: Ordenar por columnas en Power BI Desktop
description: En Power BI, puede cambiar el aspecto de un objeto visual ordenando por diferentes campos de datos.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 0cbba86bd77debda9ab2162b8f9b190e1846b99c
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464700"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Ordenar por columnas en Power BI Desktop
En Power BI Desktop y en el servicio Power BI, puede cambiar el aspecto de un objeto visual ordenando por diferentes campos de datos. Al cambiar cómo se ordena un objeto visual, puede resaltar la información que quiere transmitir y asegurarse de que el objeto visual refleja la tendencia (o énfasis).

Independientemente de si usa datos numéricos (como cifras de ventas) o datos de texto (como nombres de estado), puede ordenar las visualizaciones y conferirles el aspecto que quiera que tengan. Power BI proporciona mucha flexibilidad a la hora de ordenar, así como menús rápidos para que pueda usarlos. Para ordenar un objeto visual, seleccione el menú **Más acciones** (...), seleccione **Ordenar por** y, después, el campo por el que desea ordenar.

![Menú Más opciones](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="sorting-example"></a>Ejemplo de ordenación
Usemos un ejemplo que tiene más de profundidad, y veamos cómo funciona en Power BI Desktop.

En esta visualización se muestran los costos, las cantidades y los importes por nombre de fabricante. Este es el aspecto de la visualización antes de realizar cualquier tipo de ordenación:

![Visualización inicial](media/desktop-sort-by-column/sortbycolumn_1.png)

Actualmente, el objeto visual está ordenado por la columna **SalesQuantity**. Podemos averiguar cuál es la columna de ordenación relacionando el color de las barras ascendentes con la leyenda, pero hay una forma mejor de hacerlo: el menú **Más opciones**, al que se accede seleccionando los puntos suspensivos (...).

![Menú Más opciones](media/desktop-sort-by-column/sortbycolumn_2.png)

Las selecciones de ordenación son estas:

* El campo de ordenación actual es **SalesQuantity**, lo que se deduce porque **SalesQuantity** aparece en negrita y precedido de una barra amarilla. 

* La dirección de ordenación actual es ascendente, tal como se muestra en **Orden ascendente**, en negrita y precedido de una barra amarilla.

Abordaremos los temas de campo de ordenación y dirección de ordenación en las dos secciones siguientes.

## <a name="select-which-column-to-use-for-sorting"></a>Selección de la columna que se va a usar para la ordenación
Se habrá percatado de la barra amarilla que precede a **SalesQuantity** en el menú **Más opciones**, que indica que el objeto visual está ordenado por esa columna **SalesQuantity**. Ordenar por otra columna es fácil: seleccione los puntos suspensivos (...) para abrir el menú **Más opciones**, seleccione **Ordenar por** y, después, seleccione otra columna.

En esta imagen, hemos seleccionado **DiscountAmount** para ordenar por esta columna. Esa columna resulta ser una de las líneas en el objeto visual, en lugar de una de las barras. 

![Ordenar por DiscountAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

Observe cómo ha cambiado el objeto visual. Ahora, los valores se ordenan desde el valor más alto de **DiscountAmount** (Fabrikam Inc.) hasta el valor más bajo (Northwind Traders). 

Pero, ¿qué ocurre si queremos ordenar de forma ascendente en lugar de hacerlo de forma descendente? En la siguiente sección se muestra lo fácil que es hacer esto.

## <a name="select-the-sort-order"></a>Selección del criterio de ordenación
Cuando echamos un vistazo más de cerca al menú **Más opciones** de la imagen anterior, vemos que **Orden descendente** está en negrita, precedido de una barra amarilla.

![Ordenar de mayor a menor](media/desktop-sort-by-column/sortbycolumn_4.png)

Cuando se selecciona **Orden descendente**, significa que el objeto visual se ordena por la columna seleccionada de valor mayor a valor menor. ¿Quiere cambiar esto? Sin problemas; simplemente, seleccione **Orden ascendente** y el criterio de ordenación de la columna seleccionada cambiará de menor a mayor valor.

Este es el mismo objeto visual después de cambiar el orden de **DiscountAmount**. Observe que, ahora, Northwind Traders es el primer fabricante de la lista y Fabrikam Inc., el último (el orden opuesto al anterior).

![Ordenar de menor a mayor](media/desktop-sort-by-column/sortbycolumn_5.png)

Puede ordenar por cualquier columna incluida en el objeto visual. Podríamos haber seleccionado perfectamente **SalesQuantity** como la columna por la que ordenar, para mostrar primero los fabricantes con más ventas y seguir conservando las otras columnas en el objeto visual según corresponda a ese fabricante. Aquí se muestra el objeto visual con esa configuración:

![Ordenar por SalesQuantity](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Ordenación con el botón Ordenar por columna
Hay otra forma de ordenar los datos: con el botón **Ordenar por columna** de la cinta de opciones **Modelado**.

![Botón Ordenar por columna](media/desktop-sort-by-column/sortbycolumn_8.png)

En este método de ordenación, primero se debe seleccionar la columna (campo) por la que ordenar en el panel **Campos** y, luego, seleccionar **Modelado** > **Ordenar por columna** para ordenar el objeto visual. Si no se selecciona una columna, el botón **Ordenar por columna** está inactivo.

Veamos un ejemplo habitual. Tenemos datos de cada mes del año y queremos ordenarlos cronológicamente. En los siguientes pasos se explica cómo:

1. Fíjese en que, cuando el objeto visual está seleccionado pero no hay ninguna columna seleccionada en el panel **Campos**, el botón **Ordenar por columna** está inactivo (atenuado).
   
   ![Botón Ordenar por columna inactivo](media/desktop-sort-by-column/sortbycolumn_9.png)

2. Cuando se selecciona la columna por la que se desea ordenar, en el panel **Campos**, el botón **Ordenar por columna** se activa.
   
   ![Botón Ordenar por columna activo](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Con el objeto visual seleccionado, podemos seleccionar **MonthOfYear**, en lugar del valor predeterminado (**MonthName**), y el objeto visual se ordena en el orden que queremos: por mes del año.
   
   ![Menú Ordenar por columna](media/desktop-sort-by-column/sortbycolumn_11.png)


<!---
This functionality is no longer active. Jan 2020

## Getting back to default column for sorting
You can sort by any column you'd like, but there may be times when you want the visual to return to its default sorting column. No problem. For a visual that has a sort column selected, open the **More options** menu and select that column again, and the visualization returns to its default sort column.

For example, here's our previous chart:

![Initial visualization](media/desktop-sort-by-column/sortbycolumn_6.png)

When we go back to the menu and select **SalesQuantity** again, the visual defaults to being ordered alphabetically by **Manufacturer**, as shown in the following image.

![Default sort order](media/desktop-sort-by-column/sortbycolumn_7.png)

With so many options for sorting your visuals, creating just the chart or image you want is easy.
--->

## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Uso de la obtención de detalles de varios informes en Power BI Desktop](desktop-cross-report-drill-through.md)
* [Segmentaciones en Power BI](visuals/power-bi-visualization-slicers.md)

