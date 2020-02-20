---
title: Visualización de tablas en los informes y los paneles de Power BI
description: Tutorial para trabajar con visualizaciones de tablas en informes y paneles de Power BI, incluida la forma de cambiar el tamaño de los anchos de columna.
author: mihart
ms.reviewer: willt
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/10/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 014186acf6bf6b8c00686c0b7a29d0b526b0afb7
ms.sourcegitcommit: e27d40054949421701f829113c4a5f6d260c8d5f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2020
ms.locfileid: "77154320"
---
# <a name="tables-in-power-bi-reports-and-dashboards"></a>Tablas en informes y paneles de Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Una tabla es una cuadrícula que contiene datos relacionados en una serie lógica de filas y columnas. También puede contener encabezados y una fila de totales. Las tablas funcionan bien con comparaciones cuantitativas en las que está mirando muchos valores para una única categoría. Por ejemplo, en esta tabla se muestran cinco medidas distintas para **Categoría**.

![Captura de pantalla de una tabla en la que se muestran cinco medidas distintas para Categoría.](media/power-bi-visualization-tables/power-bi-table-grid3.png)

Cree tablas en los informes y resalte los elementos dentro de la tabla con otros objetos visuales en la misma página del informe. Puede seleccionar filas, columnas e incluso celdas individuales y realizar un resaltado cruzado. También puede copiar y pegar las celdas individuales y las selecciones de celdas múltiples en otras aplicaciones.

## <a name="when-to-use-a-table"></a>Cuándo usar una tabla

Las tablas son una excelente opción:

* Para ver y comparar datos detallados y valores exactos (en lugar de representaciones visuales).

* Para mostrar datos en un formato tabular.

* Para mostrar datos numéricos por categorías.

## <a name="prerequisite"></a>Requisito previo

En este tutorial se usa el [archivo PBIX del Ejemplo de análisis de minoristas](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de minoristas**.

1. Abra el **archivo PBIX del Ejemplo de análisis de minoristas** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.


## <a name="create-a-table"></a>Crear una tabla

Vamos a crear la tabla que aparece al principio del artículo para mostrar los valores de ventas por categoría de producto.


1. En el panel **Campos**, seleccione **Artículo** > **Categoría**.

    Power BI crea automáticamente una tabla que enumera todas las categorías.

    ![Resultado de agregar Categoría](media/power-bi-visualization-tables/power-bi-table1.png)

1. Seleccione **Ventas > Precio unitario medio** y **Ventas > Ventas del año anterior**

1. A continuación, seleccione **Ventas > Ventas de este año** y, a continuación, las tres opciones: **Valor**, **Objetivo** y **Estado**.

1. En el panel **Visualizaciones**, busque el área **Valores** y seleccione los valores hasta que el orden de las columnas del gráfico coincida con la primera imagen de esta página. Arrastre los valores en el área si es necesario. El área **Valores** será similar a esta:

    ![Área Valores](media/power-bi-visualization-tables/power-bi-table2.png)


## <a name="format-the-table"></a>Dar formato a la tabla

Existen muchas formas de aplicar formato a una tabla. Aquí solo se analizan algunas. Una buena manera de conocer las demás opciones de formato es abrir el panel **Formato** (icono de rodillo de pintar ![rodillo de pintar](media/power-bi-visualization-tables/power-bi-format.png)) y explorarlo.

* Pruebe a dar formato a la cuadrícula de tabla. En este caso agregará una cuadrícula vertical azul y espacio a las filas, y aumentará el esquema y el tamaño de texto.

    ![Tarjeta de cuadrícula](media/power-bi-visualization-tables/power-bi-table-gridnew.png)

    ![Tabla en la que se muestran los resultados](media/power-bi-visualization-tables/power-bi-table-grid3.png)

* Para los encabezados de columna, cambie el color de fondo, agregue un esquema y aumente el tamaño de fuente.

    ![Tarjeta de encabezados de columna](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

    ![Formato de los encabezados en la tabla](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Incluso puede aplicar formato a encabezados de columna y columnas individuales. Empiece por ampliar el **Formato de campo** y seleccione la columna a la que se va a dar formato en la lista desplegable. Dependiendo de los valores de columna, el **Formato de campo** permite configurar parámetros como mostrar unidades, el color de fuente, el número de posiciones decimales, el fondo, la alineación y más. Una vez que haya ajustado la configuración, decida si desea aplicar esta configuración también al encabezado y la fila de totales.

    ![Formato de campo para Ventas de este año](media/power-bi-visualization-tables/power-bi-field-formatting.png)

    ![Formato de campo para Ventas de este año en la tabla](media/power-bi-visualization-tables/power-bi-field-formatting-1.png)

* Después de algunos cambios de formato adicionales, esta es nuestra tabla final.

    ![Tabla con todo el formato aplicado hasta ahora](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Formato condicional

El *formato condicional* es un tipo de formato. Power BI puede aplicar formato condicional a cualquier campo que haya agregado al área **Valores** del panel **Visualizaciones**.

![El panel Visualizaciones](media/power-bi-visualization-tables/power-bi-table-values.png)

Con el formato condicional para tablas, puede especificar iconos, direcciones URL, colores de fondo de las celdas y colores de fuente según los valores de la celda, e incluso usar colores de degradado.

1. En el panel **Formato**, abra la tarjeta **Formato condicional**.

    ![Tarjeta de formato condicional](media/power-bi-visualization-tables/power-bi-conditional.png)

1. Seleccione un campo al que quiera dar formato y mueva el control deslizante **Color de fondo** a Activado. Power BI aplica un degradado en función de los valores de la columna. Para cambiar los colores predeterminados, seleccione **Controles avanzados**.

    Si selecciona la opción **Divergente**, también puede configurar un valor **Centro** opcional.

    ![Pantalla Escalas de color de fondo](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)

    Vamos a aplicar un formato personalizado a los valores de Precio unitario medio. Seleccione **Divergente**, agregue algunos colores y seleccione **Aceptar**.

    ![Tabla en la que se muestran colores divergentes](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
1. Agregue un nuevo campo a la tabla que contenga valores positivos y negativos. Seleccione **Ventas > Varianza total de ventas**.

    ![Se muestra un campo nuevo en el extremo derecho](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)

1. Agregue formato condicional de barra de datos moviendo el control deslizante **Barras de datos** a Activado.  

    ![Tarjeta de formato condicional con Barras de datos establecido en Activado](media/power-bi-visualization-tables/power-bi-data-bar-matrix.png)

1. Para personalizar las barras de datos, seleccione **Controles avanzados**. En el cuadro de diálogo que aparece, establezca los colores para **Barra positiva** y **Barra negativa**, seleccione la opción **Mostrar solo la barra** y realice cualquier otro cambio que desee.

    ![Marca de verificación para Mostrar solo la barra](media/power-bi-visualization-tables/power-bi-data-bar.png)

1. Seleccione **Aceptar**.

    Las barras de datos reemplazarán los valores numéricos en la tabla, lo cual facilitará el análisis.

    ![La misma tabla pero con barras en la última columna](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)

1. Agregue indicaciones visuales a la tabla con *iconos condicionales*.  En la tarjeta **Formato condicional**, seleccione **Ventas de este año** en la lista desplegable. Mueva el control deslizante **Iconos** a **Activado**.  Para personalizar los iconos, seleccione **Controles avanzados**.

    ![Tabla con los iconos agregados](media/power-bi-visualization-tables/power-bi-table-icons.png)


## <a name="copy-values-from-power-bi-tables-for-use-in-other-applications"></a>Copia de los valores de las tablas de Power BI para su uso en otras aplicaciones

Su tabla o matriz puede tener contenido que le gustaría utilizar en otras aplicaciones, como Dynamics CRM, Excel e incluso otros informes de Power BI. En Power BI, al hacer clic con el botón derecho dentro de una celda, puede copiar los datos en una sola celda o una selección de celdas en el portapapeles y pegarlas en las otras aplicaciones.

Para copiar el valor de una sola celda:

1. Seleccione la celda que desea copiar.

1. Haga clic con el botón derecho dentro de la celda.

1. Seleccione **Copiar** > **Copiar valor**.

    ![opciones de copia](media/power-bi-visualization-tables/power-bi-copy-value.png)

    Con el valor de la celda sin formato en el portapapeles, puede pegarlo en otra aplicación.

Para copiar más de una celda:

1. Seleccione un rango de celdas o use **Ctrl** para seleccionar una o varias celdas.

1. Haga clic con el botón derecho en una de las celdas seleccionadas.

1. Seleccione **Copiar** > **Copiar selección**.

    ![opciones de copia](media/power-bi-visualization-tables/power-bi-copy-selection.png)

## <a name="adjust-the-column-width-of-a-table"></a>Ajustar el ancho de columna de una tabla

A veces, Power BI trunca un encabezado de columna en un informe o un panel. Para mostrar el nombre de columna completo, mantenga el puntero sobre el espacio a la derecha del encabezado para mostrar las flechas dobles, selecciónelas y arrástrelas.

![Primer plano de vídeo del cambio de tamaño de la columna](media/power-bi-visualization-tables/resizetable.gif)


## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

Al aplicar el formato de las columnas, solo puede elegir una opción de alineación por cada columna: **Automática**, **Izquierda**, **Centro** y **Derecha**. Normalmente, una columna contiene todo el texto o todos los números, y no una combinación de ellos. En casos donde una columna contiene números y texto, **Automática** alineará el texto a la izquierda y los números a la derecha. Este comportamiento es compatible con idiomas en los que se lee de izquierda a derecha.

## <a name="next-steps"></a>Pasos siguientes

* [Gráficos de rectángulos en Power BI](power-bi-visualization-treemaps.md)

* [Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
