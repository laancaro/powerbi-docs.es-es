---
title: Uso del objeto visual de matriz en Power BI
description: Conozca cómo el objeto visual de matriz permite diseños de paso y resaltado pormenorizado en Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/10/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 10f79c8670b42828b4219723bd8e503424e77820
ms.sourcegitcommit: e27d40054949421701f829113c4a5f6d260c8d5f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2020
ms.locfileid: "77154445"
---
# <a name="create-matrix-visualizations-in-power-bi"></a>Creación de visualizaciones de matriz en Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

El objeto visual de matriz es similar a una tabla.  Una tabla admite dos dimensiones y los datos son planos; es decir, que los valores duplicados se muestran, pero no se agregan. Una matriz hace que sea más fácil mostrar los datos de manera significativa en múltiples dimensiones, ya que admite un diseño escalonado. La matriz agrega automáticamente los datos y permite explorarlos en profundidad. 

Puede crear objetos visuales de matriz en elementos cruzados e informes de **Power BI Desktop** dentro de la matriz con otros objetos visuales en esa página de informe. Por ejemplo, puede seleccionar filas, columnas y e incluso celdas individuales y realizar un resaltado cruzado. Además, las celdas individuales y las selecciones de celdas múltiples pueden copiarse y pegarse en otras aplicaciones. 

![matriz con resaltado cruzado y gráfico de anillos](media/desktop-matrix-visual/matrix-visual_2a.png)

Hay muchas características asociadas a la matriz que iremos revisando en las siguientes secciones de este artículo.


## <a name="understanding-how-power-bi-calculates-totals"></a>Descripción del cálculo de los totales por Power BI

Antes de pasar a analizar el uso del objeto visual de matriz, es importante entender cómo hace Power BI para calcular los valores totales y subtotales en tablas y matrices. Para las filas de total y subtotal, Power BI evalúa la medida a través de todas las filas en los datos subyacentes: no es simplemente una suma de los valores de las filas visibles o que se muestran. Esto significa que obtendrá valores diferentes en la fila de total de lo que cabría esperar.

Eche un vistazo a los siguientes objetos visuales de matriz. 

![comparación de tablas y matrices](media/desktop-matrix-visual/matrix-visual_3.png)

En este ejemplo, cada fila del objeto visual de matriz situado más a la derecha muestra la *cantidad* para cada combinación de fecha y vendedor. Sin embargo, puesto que un vendedor se muestra con varias fechas, los números pueden aparecer más de una vez. Por lo tanto, el total de los datos subyacentes y una simple suma de los valores visibles no coincide. Se trata de un patrón común cuando el valor que está sumando está en el lado "uno" de una relación de uno a varios.

Al examinar los totales y subtotales, recuerde que estos valores se basan en los datos subyacentes. No se basan exclusivamente en los valores visibles.


## <a name="expanding-and-collapsing-row-headers"></a>Expansión y contracción de encabezados de fila
Hay dos maneras de expandir los encabezados de fila. La primera es mediante el menú contextual. Verá opciones para expandir el encabezado de fila específico que seleccionó, el nivel entero o todo hasta el último nivel de la jerarquía. También tiene opciones similares para contraer los encabezados de fila.

![](media/desktop-matrix-visual/power-bi-expand1.png)

Además, puede agregar botones +/-a los encabezados de fila mediante el panel de formato situado bajo la tarjeta **Encabezados de fila**. De forma predeterminada, los iconos coinciden con el formato del encabezado de fila, pero puede personalizar los colores y tamaños de los iconos por separado si así lo desea.

Una vez que los iconos están activados, funcionan de forma similar a los de la tabla dinámica de Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

El estado de expansión de la matriz se guardará con el informe. Una matriz se puede anclar a un panel expandido o contraído. Cuando se selecciona el icono del panel y se abre el informe, se puede cambiar el estado de expansión en el informe. 

![](media/desktop-matrix-visual/power-bi-expand3.png)



## <a name="using-drill-down-with-the-matrix-visual"></a>Uso de la exploración en profundidad con el objeto visual de matriz
Con el objeto visual de matriz, puede realizar todo tipo de actividades interesantes de exploración en profundidad que no estaban disponibles anteriormente. Esto incluye la capacidad de explorar en profundidad mediante filas, columnas e incluso en celdas y secciones individuales. Veamos cómo funciona cada una de ellas.

### <a name="drill-down-on-row-headers"></a>Exploración en profundidad en encabezados de fila

En el panel Visualizaciones, al agregar varios campos a la sección **Filas** del área **Campos**, se habilita la exploración en profundidad en las filas del objeto visual de matriz. Esto es parecido a la creación de una jerarquía que después permite explorar en profundidad (y, posteriormente, retroceder) por esa jerarquía y analizar los datos de cada nivel.

En la siguiente imagen, la sección **Filas** contiene *Fase de ventas* y *Tamaño de oportunidad*, lo cual permite crear una agrupación (o jerarquía) de las filas que se pueden explorar.

![Tarjeta de filtros que muestra las filas que se eligen](media/desktop-matrix-visual/power-bi-rows-matrix.png)

Cuando se ha creado la agrupación en el objeto visual en la sección **Filas**, el mismo objeto visual muestra los iconos *Explorar* y *Expandir* en la esquina superior izquierda del objeto visual.

![matriz con los controles de exploración en profundidad contorneados](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

De forma parecida al comportamiento de exploración y expansión de otros objetos visuales, al hacer clic en esos botones se puede explorar en profundidad (o retroceder) por la jerarquía. En este caso, se puede explorar en profundidad desde *Ventas* a *Tamaño de oportunidad*, como se muestra en la imagen siguiente, en la que se ha hecho clic en el icono de nivel uno de exploración en profundidad (el tridente).

![matriz con tridente contorneado](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Además de usar esos iconos, puede seleccionar cualquiera de los encabezados de fila y explorar en profundidad seleccionando la opción correspondiente en el menú que aparece.

![opciones de menú para las filas de la matriz](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Tenga en cuenta que hay algunas opciones en el menú que aparece que generan resultados diferentes:

Si selecciona **Explorar en profundidad** se expande la matriz de *ese* nivel de fila, *salvo* todos los demás encabezados de fila, a excepción del encabezado que se seleccionó. En la siguiente imagen, se seleccionó **Propuesta** > **Explorar en profundidad**. Tenga en cuenta que otras filas de nivel superior ya no aparecen en la matriz. Esta forma de explorar en profundidad es una característica útil, que se convierte en magnífica cuando se llega a la sección de resaltado cruzado.

![matriz explorada en profundidad un nivel](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Seleccione el icono de **Rastrear agrupando datos** para volver a la vista de nivel superior anterior. Si, a continuación, selecciona **Propuesta** > **Mostrar el siguiente nivel**, obtendrá un listado alfabético de todos los elementos del siguiente nivel (en este caso, el campo *Tamaño de oportunidad*), sin la categorización de jerarquía de nivel superior.

![matriz con Mostrar el siguiente nivel](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Seleccione el icono de **Rastrear agrupando datos** situado en la esquina superior izquierda para que la matriz muestre todas las categorías de nivel superior; a continuación, seleccione **Propuesta** > **Expandir al siguiente nivel** para ver todos los valores de los dos niveles de la jerarquía: *Fase de ventas* y *Tamaño de oportunidad*.

![matriz con Expandir al siguiente nivel](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

También puede usar el elemento de menú **Expandir** para controlar aún más la presentación.  Por ejemplo, seleccione **Propuesta** > **Expandir** > **Selección**. Power BI muestra una fila total para cada *fase de ventas* y todas las opciones de *Tamaño de oportunidad* de *Propuesta*.

![Matriz después de haber aplicado Expandir en Propuesta](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Exploración en profundidad en encabezados de columna
Al igual que la funcionalidad de explorar en profundidad en las filas, también se puede hacer en las columnas. En la siguiente imagen, hay dos campos en el conjunto de campos **Columnas**, lo cual permite crear una jerarquía similar a la que hemos usado para las filas anteriormente en este artículo. En el conjunto de campos **Columnas**, tenemos *Región* y *Segmento*. En cuanto el segundo campo se agregó a **Columnas**, un nuevo menú desplegable apareció en el objeto visual; actualmente muestra **Filas**.

![Matriz después del segundo valor de columna agregado](media/desktop-matrix-visual/power-bi-matrix-row.png)

Para explorar en profundidad en las columnas, seleccione **Columnas** desde el menú *Obtener detalles*, que puede encontrarse en la esquina superior izquierda de la matriz. Seleccione la región *Este* y elija **Explorar en profundidad**.

![menú para explorar en profundidad en las columnas](media/desktop-matrix-visual/power-bi-matrix-column.png)

Cuando se selecciona **Explorar en profundidad**, aparece el siguiente nivel de la jerarquía de la columna para *Región > Este* que, en este caso, es *Recuento de oportunidades*. La otra región está oculta.

![matriz con columna explorada en profundidad en un nivel](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

El resto de los elementos de menú funcionan de la misma manera que lo hacen los de las filas (vea la sección anterior, **Exploración en profundidad en encabezados de fila**). También puede seleccionar las opciones **Mostrar el siguiente nivel** y **Expandir al siguiente nivel** con columnas al igual que podía hacer con las filas.

> [!NOTE]
> Los iconos Explorar en profundidad y Explorar agrupando datos situados en la esquina superior izquierda del objeto visual de matriz solo son aplicables a las filas. Para explorar en profundidad por las columnas, debe usar el menú contextual.

## <a name="stepped-layout-with-matrix-visuals"></a>Diseño escalonado con objetos visuales de matriz

El objeto visual de matriz aplica sangría automáticamente a las subcategorías de una jerarquía debajo de cada elemento primario, que se denomina Diseño escalonado.

En la versión original del objeto visual de la matriz, las subcategorías se mostraban en una columna completamente diferente, lo cual ocupaba mucho más espacio en el objeto visual. En la imagen siguiente se muestra la tabla del objeto visual de matriz original; observe que las subcategorías se encuentran en una columna independiente.

![Captura de pantalla del objeto visual de matriz anterior que muestra las subcategorías en una columna independiente.](media/desktop-matrix-visual/matrix-visual_14.png)

En la siguiente imagen, puede ver un objeto visual de matriz con el diseño escalonado en acción. Observe que la categoría *Computers* tiene sus subcategorías (Computers Accessories, Desktops, Laptops, Monitors, etc.) ligeramente con sangría. Esto ofrece un objeto visual más limpio y mucho más reducido.

![forma actual en que esa matriz formatea los datos](media/desktop-matrix-visual/matrix-visual_13.png)

Puede ajustar fácilmente la configuración del diseño escalonado. Con el objeto visual de matriz seleccionado, en la sección **Formato** (el icono de rodillo de pintura) del panel **Visualizaciones**, expanda la sección de encabezados de fila. Tiene dos opciones: la opción de diseño escalonado (que se puede activar o desactivar) y la opción de sangría de diseño escalonado (que permite especificar el tamaño de la sangría, en píxeles).

![Tarjeta de encabezados de fila que muestra el control Diseño escalonado](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Si desactiva el diseño escalonado, Power BI muestra subcategorías en otra columna en lugar de con una sangría debajo de la categoría primaria.

## <a name="subtotals-and-grand-totals-with-matrix-visuals"></a>Subtotales y totales generales con objetos visuales de matriz

Puede activar o desactivar subtotales en objetos visuales de matriz tanto para filas como para columnas. En la imagen siguiente, puede ver que los subtotales de fila están establecidos en **Activado** y configurados para que se muestren en la parte inferior.

![matriz que muestra subtotales y totales](media/desktop-matrix-visual/power-bi-subtotals.png)

Al activar **Subtotales** y agregar una etiqueta, Power BI también agrega una fila y la misma etiqueta al valor total general. Para dar formato al total general, seleccione la opción de formato para **Total general**. 

![matriz que muestra la tarjeta de Total general](media/desktop-matrix-visual/power-bi-grand-total.png)

Si quiere desactivar los subtotales y el total general, en la sección Formato del panel Visualizaciones, expanda la tarjeta **Subtotales** y mueva el control deslizante de subtotales a **Desactivado**. Al hacerlo, no se muestran los subtotales.

![matriz con subtotales desactivados](media/desktop-matrix-visual/power-bi-no-subtotals.png)

El mismo proceso se aplica a los subtotales de columna.

## <a name="add-conditional-icons"></a>Adición de iconos condicionales
Agregue indicaciones visuales a la tabla o a la matriz con *iconos condicionales*. 

En la sección formato del panel Visualizaciones, expanda la tarjeta **Formato condicional**. Mueva el control deslizante **Iconos** a **Activado** y seleccione **Controles avanzados**.

![Matriz que muestra la pantalla Iconos](media/desktop-matrix-visual/power-bi-icons.png)

Ajuste las condiciones, los iconos y los colores de la matriz y seleccione **Aceptar**. En este ejemplo, se usa una marca roja para los valores bajos, un círculo púrpura para los valores altos y un triángulo amarillo para los valores intermedios. 

![Matriz que muestra los iconos](media/desktop-matrix-visual/power-bi-icons-applied.png)

## <a name="cross-highlighting-with-matrix-visuals"></a>Resaltado cruzado con objetos visuales de matriz

Con el objeto visual de matriz, puede seleccionar todos los elementos de la matriz como base para el resaltado cruzado. Seleccione una columna en una matriz para que Power BI resalte la columna, al igual que sucede con los demás objetos visuales de la página de informe. Este tipo de resaltado cruzado ha sido una característica común de otros objetos visuales y selecciones de punto de datos, por lo que ahora el objeto visual de matriz ofrece la misma función.

Además, el uso de Ctrl+clic también funciona para el resaltado cruzado. Por ejemplo, en la siguiente imagen, se ha seleccionado una colección de subcategorías del objeto visual de matriz. Observe que los elementos del objeto visual que no se seleccionaron aparecen atenuados y que los demás objetos visuales de la página reflejan las selecciones realizadas en el objeto visual de matriz.

![Captura de pantalla del objeto visual de matriz visual junto con dos otros objetos visuales que muestran la función de Ctrl+clic para el resaltado cruzado.](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Copia de valores de Power BI para su uso en otras aplicaciones

La matriz o tabla puede tener contenido que es posible que quiera usar en otras aplicaciones: Dynamics CRM, Excel y otros informes de Power BI. Con el menú contextual de Power BI, puede copiar una sola celda o una selección de celdas en el portapapeles y pegarlas en la otra aplicación.


* Para copiar el valor de una sola celda, seleccione la celda, haga clic con el botón derecho del ratón y elija **Copiar valor**. Con el valor de la celda sin formato en el portapapeles, ahora puede pegarlo en otra aplicación.

    ![Captura de pantalla del objeto visual de matriz con una flecha que apunta a un valor y el menú contextual expandido con el valor de la copia y las opciones de selección de copia resaltados.](media/desktop-matrix-visual/power-bi-cell-copy.png)



* Para copiar más de una celda, seleccione un rango de celdas o utilice CTRL para seleccionar una o más celdas. 

    ![Captura de pantalla del objeto visual de matriz con una flecha que apunta a los tres valores resaltados en el menú contextual expandido con el valor de la copia y las opciones de selección de copia resaltados.](media/desktop-matrix-visual/power-bi-copy.png)

* La copia incluirá los encabezados de columna y de fila.

    ![Captura de pantalla que muestra filas y columnas de Excel con los valores pegados en ellas.](media/desktop-matrix-visual/power-bi-copy-selection.png)

* Si quiere hacer una copia del objeto visual que contiene solo las celdas seleccionadas, seleccione una o varias celdas; para ello, haga clic en CTRL, haga clic con el botón derecho y seleccione **Copiar objeto visual**.

    ![Captura de pantalla que muestra la opción de copiar objeto visual](media/desktop-matrix-visual/power-bi-copy-visual.png)

* La copia será otra visualización de la matriz, pero solo contendrá los datos copiados.

    ![Captura de pantalla que muestra el ejemplo de copiar objeto visual](media/desktop-matrix-visual/power-bi-copy-visual-example.png)

## <a name="setting-a-matrix-value-as-a-custom-url"></a>Establecimiento de un valor de matriz como una dirección URL personalizada

Si tiene una columna o una medida que contiene direcciones URL de sitios web, puede usar el formato condicional para aplicar dichas direcciones URL a los campos como vínculos activos. Encontrará esta opción en la tarjeta **Formato condicional** del panel de formato.

![Tarjeta de filtros que muestra las filas que se eligen](media/desktop-matrix-visual/power-bi-web-url.png)

Active **Dirección URL web** y seleccione un campo para usarlo como dirección URL de la columna. Una vez aplicados, los valores de ese campo (columna) se convierten en vínculos activos. Mantenga el mouse para ver el vínculo y selecciónelo para saltar a esa página. 

Para más información, consulte [Formato de tabla condicional](../desktop-conditional-table-formatting.md).

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Colores de fuente y sombreado con objetos visuales de matriz
Con el objeto visual de matriz, puede aplicar formato condicional (colores, sombreado y barras de datos) al fondo de las celdas de la matriz y también al texto y a los valores propiamente dichos.

Para aplicar formato condicional, seleccione el objeto visual de matriz y abra el panel **Formato**. Expanda la tarjeta **Formato condicional**, y para **Color de fondo**, **Color de fuente** o **Barras de datos**, mueva el control deslizante a **Activar**. Al activar una de estas opciones se muestra un vínculo para *Controles avanzados*, que permite personalizar los colores y los valores del formato de color.
  
  ![Panel Formato que muestra el control Barras de datos](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Seleccione *Controles avanzados* para mostrar un cuadro de diálogo, que permite realizar ajustes. En este ejemplo se muestra el cuadro de diálogo de **Barras de datos**.

![Panel Barras de datos](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>Pasos siguientes

[Objeto visual de Power Apps para Power BI](power-bi-visualization-powerapp.md)

[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)