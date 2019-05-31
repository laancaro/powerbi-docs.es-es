---
title: Uso del objeto visual de matriz en Power BI
description: Conozca cómo el objeto visual de matriz permite diseños de paso y resaltado pormenorizado en Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6ad8900e5a95148b3f8333aa1953cc939d56f0e6
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375347"
---
# <a name="use-the-matrix-visual-in-power-bi"></a>Uso del objeto visual de matriz en Power BI
El **matriz** visual es similar a un **tabla**.  Una tabla admite 2 dimensiones y los datos son planos, se muestran y no agregan valores duplicados de significado. Una matriz resulta más fácil mostrar los datos de forma significativa en varias dimensiones, es compatible con un diseño escalonado. La matriz automáticamente agrega los datos y permite la obtención de abajo. 

Puede crear objetos visuales de matriz en **Power BI Desktop** y **servicio Power BI** informes y elementos de resaltado cruzado dentro de la matriz con otros objetos visuales en esa página del informe. Por ejemplo, puede seleccionar filas, columnas e incluso celdas individuales y el resaltado cruzado. Además, las celdas individuales y las selecciones de varias celdas pueden copiarse y pegarse en otras aplicaciones. 

![resaltado matriz y gráfico de anillos entre](media/desktop-matrix-visual/matrix-visual_2a.png)

Hay muchas características asociadas a la matriz que iremos revisando en las siguientes secciones de este artículo.


## <a name="understanding-how-power-bi-calculates-totals"></a>Descripción del cálculo de los totales por Power BI

Antes de pasar a analizar el uso del objeto visual **Matriz**, es importante entender cómo hace Power BI para calcular los valores totales y subtotales en tablas y matrices. Para las filas de total y subtotal, se evalúa la medida a través de todas las filas en los datos subyacentes: *no* es simplemente una suma de los valores de las filas visibles o que se muestran. Esto significa que obtendrá valores diferentes en la fila de total de lo que cabría esperar. 

Eche un vistazo a los siguientes objetos visuales de matriz. 

![Compara las tablas y matrices](media/desktop-matrix-visual/matrix-visual_3.png)

En este ejemplo, cada fila de la matriz visual situado más a la derecha muestra la *cantidad* para cada combinación de fecha y vendedor. Sin embargo, puesto que un vendedor se muestra con varias fechas, los números pueden aparecer más de una vez. Por lo tanto, el total de los datos subyacentes y una simple suma de los valores visibles no coincide. Se trata de un patrón común cuando el valor que está sumando está en el lado "uno" de una relación de uno a varios.

Cuando se examinan los totales y subtotales, recuerde que los valores se basan en los datos subyacentes, y no solo en los valores visibles. 

<!-- use Nov blog post video

## Expanding and collapsing row headers
There are two ways you can expand row headers. The first is through the right-click menu. You’ll see options to expand the specific row header you clicked on, the entire level or everything down to the very last level of the hierarchy. You have similar options for collapsing row headers as well.

![](media/desktop-matrix-visual/power-bi-expand1.png)

You can also add +/- buttons to the row headers through the formatting pane under the row headers card. By default, the icons will match the formatting of the row header, but you can customize the icons’ color and size separately if you want. 
Once the icons are turned on, they work similarly to the icons from PivotTables in Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

The expansion state of the matrix will save with your report. It can be pinned to dashboards as well, but consumers will need to open up the report to change the state. Conditional formatting will only apply to the inner most visible level of the hierarchy. Note that this expand/collapse experience is not currently supported when connecting to AS servers older than 2016 or MD servers.

![](media/desktop-matrix-visual/power-bi-expand3.png)

Watch the following video to learn more about expand/collapse in the matrix:

-->
## <a name="using-drill-down-with-the-matrix-visual"></a>Uso de exploración en profundidad hacia abajo con el objeto visual matriz
Con el objeto visual de matriz, puede hacer a todo tipo de interesante de explorar en profundidad las actividades que no estaban disponibles anteriormente. Esto incluye la capacidad de explorar en profundidad mediante filas, columnas e incluso en celdas y secciones individuales. Veamos cómo funciona cada una de ellas.

### <a name="drill-down-on-row-headers"></a>Exploración en profundidad en encabezados de fila
En el panel **Visualizaciones**, al agregar varios campos a la sección **Filas** del área **Campos**, se habilita la exploración en profundidad en las filas del objeto visual de matriz. Esto es parecido a la creación de una jerarquía que después permite explorar en profundidad (y, posteriormente, retroceder) por esa jerarquía y analizar los datos de cada nivel.

En la siguiente imagen, el **filas** sección contiene *fase de ventas* y *tamaño de oportunidad*, creación de una agrupación (o jerarquía) en las filas que se pueden explorar.

![Tarjeta de filtros que muestra las filas que se eligen](media/desktop-matrix-visual/power-bi-rows-matrix.png)

Cuando se ha creado la agrupación en el objeto visual en la sección **Filas**, el mismo objeto visual muestra los iconos *Explorar* y *Expandir* en la esquina superior izquierda del objeto visual.

![matriz con los controles de obtención de detalles que se describen](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

De forma parecida al comportamiento de exploración y expansión de otros objetos visuales, al hacer clic en esos botones se puede explorar en profundidad (o retroceder) por la jerarquía. En este caso, se puede explorar en profundidad desde *fase de ventas* a *tamaño de oportunidad*, tal y como se muestra en la imagen siguiente, donde se ha seleccionado el icono de un nivel (el Tridente) en profundidad.

![matriz con Tridente descrito](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Además de usar esos iconos, puede seleccionar cualquiera de los encabezados de fila y explorar en profundidad por en el menú que aparece.

![Opciones de menú para las filas de matriz](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Tenga en cuenta que hay algunas opciones en el menú que aparece que generan resultados diferentes:

Seleccionar **explorar en profundidad** se expande la matriz para *que* nivel de fila, *excepto* todos los demás encabezados de fila, excepto el encabezado de fila que se ha seleccionado. En la siguiente imagen, **propuesta** > **explorar en profundidad** se ha seleccionado. Tenga en cuenta que otras filas de nivel superior ya no aparecen en la matriz. Esta forma de explorar en profundidad es una característica útil, que se convierte en magnífica cuando se llega a la sección **Resaltado cruzado**.

![aumenta el detalle de un nivel de matriz](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Seleccione el **Rastrear agrupando datos** icono para volver a la vista de nivel superior anterior. Si selecciona **propuesta** > **Mostrar siguiente nivel**, obtener un listado de todos los elementos del siguiente nivel ascendente (en este caso, el *tamaño de oportunidad* campo), sin la categorización de jerarquía de nivel superior.

![matriz usando Mostrar siguiente nivel](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Seleccione el **Rastrear agrupando datos** situado en la esquina superior izquierda para que la matriz muestre todas las categorías de nivel superior, a continuación, seleccione **propuesta** > **expandir al siguiente nivel**a ver todos los valores para los dos niveles de la jerarquía - *fase de ventas* y *tamaño de oportunidad*.

![mediante el siguiente nivel de expansión de matriz](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

También puede usar el **expandir** elemento de menú para controlar aún más la presentación.  Por ejemplo, seleccione **propuesta** > **expandir** > **selección**. Power BI muestra una fila total para cada *fase de ventas* y todas las *tamaño de oportunidad* opciones para *propuesta*.

![Matriz después de expandir aplicada propuesta](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Exploración en profundidad en encabezados de columna
Al igual que la capacidad de profundizar en las filas, puede también profundizar en **columnas**. En la siguiente imagen, hay dos campos en el **columnas** conjunto de campos, la creación de una jerarquía similar a lo que hemos usado para las filas anteriormente en este artículo. En el **columnas** conjunto de campos, tenemos *región* y *segmento*. Tan pronto como el segundo campo se agregó a **columnas**, un nuevo menú desplegable aparece en el objeto visual, muestra actualmente **filas**.

![Matriz después del segundo valor de columna agregado](media/desktop-matrix-visual/power-bi-matrix-row.png)

Para profundizar en las columnas, seleccione **columnas** desde el *profundizar en* menú que puede encontrarse en la esquina superior izquierda de la matriz. Seleccione el *East* región y elija **explorar en profundidad**.

![menú para explorar en profundidad para las columnas](media/desktop-matrix-visual/power-bi-matrix-column.png)

Al seleccionar **explorar en profundidad**, el siguiente nivel de la jerarquía de columnas para *región > East* muestra, que en este caso es *recuento de oportunidades*. La otra región de muestra, pero está atenuada.

![matriz con colum explorar en profundidad un nivel](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

El resto de los elementos de menú funciona en las columnas de la misma manera que lo hacen para las filas (consulte la sección anterior, **explorar en profundidad en encabezados de fila**). También puede **Mostrar siguiente nivel** y **expandir al siguiente nivel** con columnas solo se puede hacer con las filas.

> [!NOTE]
> Los iconos Explorar en profundidad y Explorar agrupando datos situados en la esquina superior izquierda del objeto visual de matriz solo son aplicables a las filas. Para explorar en profundidad por las columnas, debe usar el menú contextual.
> 
> 

## <a name="stepped-layout-with-matrix-visuals"></a>Diseño escalonado con objetos visuales de matriz
El objeto visual **Matriz** aplica sangría automáticamente a las subcategorías de una jerarquía debajo de cada elemento primario, lo cual se denomina **Diseño escalonado**.

En la versión *original* del objeto visual de la matriz, las subcategorías se mostraban en una columna completamente diferente, lo cual ocupaba mucho más espacio en el objeto visual. En la imagen siguiente se muestra la tabla del objeto visual **Matriz** original; observe que las subcategorías se encuentran en una columna independiente.

![manera antigua de formato predeterminado para matrices](media/desktop-matrix-visual/matrix-visual_14.png)

En la siguiente imagen, puede ver un objeto visual **Matriz** con el **Diseño escalonado** en acción. Observe que la categoría *Computers* tiene sus subcategorías (Computers Accessories, Desktops, Laptops, Monitors, etc.) ligeramente con sangría. Esto ofrece un objeto visual más limpio y mucho más reducido.

![actual que forma esa matriz de formatos de datos](media/desktop-matrix-visual/matrix-visual_13.png)

Puede ajustar fácilmente la configuración del diseño escalonado. Con el objeto visual **Matriz** seleccionado, en la sección **Formato** (el icono de rodillo de pintura) del panel **Visualizaciones**, expanda la sección **Encabezados de fila**. Tiene dos opciones: la opción **Diseño escalonado** (que se puede activar o desactivar) y la opción **Sangría de diseño escalonado** (que permite especificar el tamaño de la sangría, en píxeles).

![Tarjeta de encabezados de fila muestra el control de diseño escalonado](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Si desactiva **Diseño escalonado**, las subcategorías se muestran en otra columna en lugar de con una sangría debajo de la categoría primaria.

## <a name="subtotals-with-matrix-visuals"></a>Subtotales con objetos visuales de matriz
Puede activar o desactivar subtotales en objetos visuales de matriz tanto para filas como para columnas. En la imagen siguiente, puede ver que los subtotales de fila están establecidos en **Activado**.

![subtotales y totales de matriz que muestra](media/desktop-matrix-visual/matrix-visual_20.png)

En la sección **Formato** del panel **Visualizaciones**, expanda la tarjeta **Subtotales** y mueva el control deslizante **Subtotales de fila** a **Desactivado**. Al hacerlo, no se muestran los subtotales.

![matriz con subtotales que se ha desactivado](media/desktop-matrix-visual/matrix-visual_21.png)

El mismo proceso se aplica a los subtotales de columna.

## <a name="cross-highlighting-with-matrix-visuals"></a>Resaltado cruzado con objetos visuales de matriz
Con el objeto visual **Matriz**, puede seleccionar todos los elementos de la matriz como base para el resaltado cruzado. Si selecciona una columna en una **Matriz**, esta se resaltará, al igual que sucede con los demás objetos visuales de la página de informe. Este tipo de resaltado cruzado ha sido una característica común de otros objetos visuales y selecciones de punto de datos, por lo que ahora el objeto visual **Matriz** ofrece la misma función.

Además, el uso de Ctrl+clic también funciona para el resaltado cruzado. Por ejemplo, en la siguiente imagen, se ha seleccionado una colección de subcategorías del objeto visual **Matriz**. Observe que los elementos del objeto visual que no se seleccionaron aparecen atenuados y que los demás objetos visuales de la página reflejan las selecciones realizadas en el objeto visual **Matriz**.

![informe de página entre highighted mediante una matriz](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Copia de valores de Power BI para su uso en otras aplicaciones

La matriz o tabla puede tener contenido que le gustaría utilizar en otras aplicaciones, como Dynamics CRM, Excel e incluso otros informes de Power BI. Con el botón derecho de Power BI, puede copiar una sola celda o una selección de celdas en el portapapeles y pegarlas en la otra aplicación.

![opciones de copia](media/desktop-matrix-visual/power-bi-cell-copy.png)

* Para copiar el valor de una sola celda, seleccione la celda, haga clic con el botón derecho del ratón y elija **Copiar valor**. Con el valor de la celda sin formato en el portapapeles, ahora puede pegarlo en otra aplicación.

    ![opciones de copia](media/desktop-matrix-visual/power-bi-copy.png)

* Para copiar más de una celda, seleccione un rango de celdas o utilice CTRL para seleccionar una o más celdas. La copia incluirá los encabezados de columna y de fila.

    ![pegado en Excel](media/desktop-matrix-visual/power-bi-copy-selection.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Colores de fuente y sombreado con objetos visuales de matriz
Con el objeto visual de matriz, puede aplicar **formato condicional** (colores y barras de datos y sombreado) al fondo de las celdas de la matriz y se puede aplicar formato condicional en el texto y los valores propiamente dichos.

Para aplicar formato condicional, seleccione la matriz visual y abra el **formato** panel. Expanda el **formato condicional** tarjeta y para **color de fondo**, **color de fuente**, o **barras de datos**, mueva el control deslizante a **En**. Activar una de estas opciones muestra un vínculo de *controles avanzados*, que permite personalizar los colores y los valores para el formato de color.
  
  ![Panel de formato que muestra el control de las barras de datos](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Seleccione *controles avanzados* para mostrar un cuadro de diálogo que le permite realizar ajustes. En este ejemplo se muestra el cuadro de diálogo **barras de datos**.

![Panel de las barras de datos](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>Pasos siguientes

[Gráficos de dispersión y de burbujas de Power BI](power-bi-visualization-scatter.md)

[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)