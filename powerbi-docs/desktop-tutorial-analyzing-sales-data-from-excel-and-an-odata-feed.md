---
title: 'Tutorial: Combinación de datos de Excel y una fuente de OData en Power BI Desktop'
description: 'Tutorial: Combinación de datos de Excel y una fuente de OData'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 94e40681d065591db008f8a9062d851e0bd83f61
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61368788"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: Combinación de datos de ventas de Excel y una fuente de OData

Es habitual tener los datos repartidos en varios orígenes de datos como, por ejemplo, la información de producto en una base de datos y la información de ventas en otra. Con **Power BI Desktop**, puede combinar datos de orígenes diferentes para crear interesantes y atractivos análisis de datos y visualizaciones. 

En este tutorial, aprenderá a combinar datos de dos orígenes de datos: un libro de Excel que incluye la información de producto y una fuente de OData que contiene los datos de pedidos. Después de importar cada conjunto de datos y realizar los pasos de transformación y agregación, use los datos de ambos orígenes para generar un informe de análisis de ventas con visualizaciones interactivas. Estas técnicas pueden aplicarse también a consultas de SQL Server, archivos CSV y cualquier otro origen de datos en Power BI Desktop.

>[!NOTE]
>En Power BI Desktop, a menudo hay varias maneras de realizar una tarea. Por ejemplo, muchas de las selecciones de la cinta de opciones también están disponibles mediante el uso de un menú contextual o el menú **Más opciones** en una columna o celda. En los pasos siguientes se describen varios métodos alternativos. 

## <a name="import-the-product-data-from-excel"></a>Importación de los datos de producto de Excel

En primer lugar, importe los datos de producto desde el libro de Excel Products.xlsx en Power BI Desktop.

1. [Descargue el libro de Excel Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) y guárdelo como **Products.xlsx**.
   
2. Seleccione la flecha desplegable junto a **Obtener datos** en la pestaña **Inicio** de la cinta de opciones de Power BI Desktop y luego seleccione **Excel** en el menú desplegable **Más comunes**. 
   
   ![Obtener datos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >También puede seleccionar el elemento **Obtener datos** o seleccionar **Obtener datos** en el cuadro de diálogo **Introducción** de Power BI, seleccionar después **Excel** o **Archivo** > **Excel** en el cuadro de diálogo **Obtener datos** y luego seleccionar **Conectar**.
   
3. En el cuadro de diálogo **Abrir**, vaya al archivo **Products.xlsx** y selecciónelo y luego seleccione **Abrir**.
   
4. En el panel **Navegador** , seleccione la tabla **Productos** y, a continuación, seleccione **Editar**.
   
   ![Panel Navegador para Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
Se abre una vista previa de la tabla en el **Editor de Power Query**, donde puede aplicar transformaciones para limpiar los datos. 
   
![Editor de Power Query](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>También puede abrir el **Editor de Power Query** si selecciona **Editar consultas** > **Editar consultas** en la cinta de opciones **Inicio** de Power BI Desktop; también puede hacer clic con el botón derecho o seleccionar **Más opciones** junto a cualquier consulta de **Vista de informe** y seleccionar **Editar consulta**.

## <a name="clean-up-the-products-columns"></a>Limpieza de columnas de productos

El informe combinado solo usará las columnas **ProductID**, **ProductName**, **QuantityPerUnit** y **UnitsInStock** del libro de Excel, para que pueda quitar las otras columnas. 

1. En el **Editor de Power Query**, seleccione las columnas **ProductID**, **ProductName**, **QuantityPerUnit** y **UnitsInStock** (use **Ctrl**+**Clic** para seleccionar más de una columna, o **Mayús**+**Clic** para seleccionar columnas contiguas entre sí).
   
2. Haga clic en cualquiera de los encabezados seleccionados y seleccione **Quitar otras columnas** en la lista desplegable, para quitar todo excepto las columnas seleccionadas de la tabla. 
   También puede seleccionar **Quitar columnas** > **Quitar otras columnas** desde el grupo **Administrar columnas** de la pestaña **Inicio** de la cinta de opciones. 
   
   ![Quitar otras columnas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>Importación de datos de pedidos desde una fuente de OData

A continuación, importe los datos de pedidos de la fuente de OData del sistema de ventas de Northwind de ejemplo. 

1. En el **Editor de Power Query**, seleccione **Nuevo origen** y luego seleccione **Fuente de OData** en el menú desplegable **Más comunes**. 
   
   ![Obtener OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. En el cuadro de diálogo **Fuente de OData**, pegue la dirección URL de la fuente de OData de Northwind, `http://services.odata.org/V3/Northwind/Northwind.svc/`, y seleccione **Aceptar**.
   
   ![Cuadro de diálogo Fuente de OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. En el panel **Navegador**, seleccione la tabla **Orders** y luego seleccione **Aceptar** para cargar los datos en el **Editor de Power Query**.
   
   ![Panel Navegador para OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >En **Navegador**, puede seleccionar cualquier nombre de tabla, sin marcar la casilla, para obtener una vista previa.

## <a name="expand-the-order-data"></a>Expansión de los datos del pedido

Cuando se conecta a orígenes de datos que tienen varias tablas, como bases de datos relacionales o la fuente de OData de Northwind, puede utilizar referencias entre tablas para crear las consultas. La tabla **Orders** contiene referencias a varias tablas relacionadas. Puede agregar las columnas **ProductID**, **UnitPrice**, y **Quantity** de la tabla relacionada **Order_Details** en la tabla principal (**Orders**) mediante la operación **Expandir**. 

1. Desplácese hacia la derecha en la tabla **Orders** hasta que pueda ver la columna **Order_Details**. Tenga en cuenta que, en lugar de datos, contiene referencias a otra tabla.
   
   ![Columna Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Seleccione el icono **Expandir** (![Icono expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) en el encabezado de columna **Order_Details**. 
   
3. En el menú desplegable **Expandir** :
   
   1. Seleccione **(Seleccionar todas las columnas)** para borrar todas las columnas.
      
   2. Seleccione **ProductID**, **UnitPrice** y **Quantity**, y luego seleccione **Aceptar**.
      
      ![Cuadro de diálogo Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

Después de expandir la tabla **Order_Details**, la columna **Order_Details** se reemplaza con las tres columnas nuevas de la tabla anidada, y hay filas nuevas en la tabla para los datos agregados de cada pedido. 

![Columnas expandidas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Creación de una columna calculada personalizada

El Editor de Power Query le permite crear cálculos y campos personalizados para enriquecer los datos. Se creará una columna personalizada que calcula el precio total de cada artículo de línea en un orden multiplicando el precio unitario por la cantidad de artículos.

1. En la pestaña **Agregar columna** de la cinta de opciones del Editor de Power Query, seleccione **Columna personalizada**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. En el cuadro de diálogo **Columna personalizada**, escriba **LineTotal** en el campo **Nuevo nombre de columna**.

3. En el campo **Fórmula de columna personalizada** después de **=** , escriba **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . (También puede seleccionar los nombres de campo en el cuadro de desplazamiento **Columnas disponibles** y seleccionar **<< Insertar**, en lugar de escribirlos). 
3. Seleccione **Aceptar**.
   
   ![Cuadro de diálogo Columna personalizada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

El nuevo campo **LineTotal** aparece como la última columna de la tabla **Orders**.

## <a name="set-the-data-type-for-the-new-field"></a>Definición del tipo de datos del nuevo campo

Cuando el Editor de Power Query se conecta a los datos, determina el mejor tipo de datos para cada campo y muestra los datos correspondientes. Puede ver los tipos de datos asignados a los campos mediante los iconos de los encabezados, o bien en **Tipo de datos** en el grupo **Transformar** de la pestaña **Inicio** de la cinta de opciones. 

La nueva columna **LineTotal** tiene el tipo de datos **Cualquiera**, pero los valores son de moneda. Para asignar un tipo de datos, haga clic con el botón derecho en el encabezado de columna **LineTotal**, seleccione **Cambiar tipo de datos** en el menú desplegable y luego seleccione **Número decimal fijo**. 

![Cambio del tipo de datos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>También puede seleccionar la columna **LineTotal**, luego seleccionar la flecha desplegable junto a **Tipo de datos** en la sección **Transformar** de la pestaña **Inicio** de la cinta de opciones y seleccionar **Número decimal fijo**.

## <a name="clean-up-the-orders-columns"></a>Limpieza de las columnas de pedidos

Para que sea más fácil que el modelo funcione con los informes, puede eliminar algunas columnas, cambiarles el nombre y reordenarlas.

El informe solo usará las columnas **OrderDate**, **ShipCity**, **ShipCountry**, **Order_Details.ProductID**, **Order_Details.UnitPrice** y **Order_Details.Quantity**. Puede seleccionar estas columnas y usar **Quitar otras columnas** como hizo con los datos de Excel, o bien puede seleccionar todas las columnas excepto las que aparecen, hacer clic con el botón derecho en las columnas seleccionadas y seleccionar **Quitar columnas** para quitarlas todas. 

Puede facilitar la identificación de las columnas **Order_Details.ProductID**, **Order_Details.UnitPrice** y **Order_Details.Quantity** si quita los prefijos *Order_Details* de los nombres de columna. Para cambiar el nombre de las columnas a **ProductID**, **UnitPrice** y **Quantity**, respectivamente:

1. Haga doble clic en el encabezado de columna o manténgalo presionado, o bien haga clic con el botón derecho en el encabezado de columna y seleccione **Cambiar nombre** en el menú desplegable. 
2. Elimine el prefijo *Order_Details.* de todos los nombres y luego presione **ENTRAR**.

Por último, para facilitar el acceso a la columna **LineTotal**, arrástrela y colóquela en la izquierda, justo a la derecha de la columna **ShipCountry**.

![Limpiar tabla](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>Revisión de los pasos de la consulta

A medida que dio forma a los datos y los transformó en el Editor de Power Query, cada paso se registró en el área **Pasos aplicados** del panel de **configuración de consulta** que se encuentra a la derecha del Editor de Power Query. Puede retroceder en los pasos aplicados para revisar los cambios que realizó y editarlos, eliminarlos o reorganizarlos si es necesario, a pesar de que esto podría resultar un riesgo, porque cualquier cambio que se haga en los pasos anteriores podría afectar los pasos posteriores. 

Seleccione cada una de las consultas en la lista **Consultas** en el lado izquierdo del Editor de Power Query y revise los **Pasos aplicados** en **Configuración de la consulta**. Después de aplicar las transformaciones de datos anteriores, los pasos aplicados a las dos consultas deben ser similares a los siguientes:

![Pasos aplicados a la consulta de productos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Pasos aplicados a la consulta de pedidos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>Subyacentes a los pasos aplicados se encuentran las fórmulas escritas en el **lenguaje de Power Query**, que también se conoce como el lenguaje **M**. Para ver y editar las fórmulas, seleccione **Editor avanzado** en el grupo de **consultas** de la pestaña Inicio de la cinta de opciones. 

## <a name="import-the-transformed-queries"></a>Importación de las consultas transformadas

Cuando esté satisfecho con los datos transformados, seleccione **Cerrar y aplicar** > **Cerrar y aplicar** en el grupo **Cerrar** de la pestaña **Inicio** de la cinta de opciones, para importar los datos en la vista de informe de Power BI Desktop. 

![Cerrar y aplicar](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Una vez cargados los datos, las consultas aparecen en la lista **Campos** de la vista de informe de Power BI Desktop.

![Consultas en la lista Campos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Administración de la relación entre los conjuntos de datos

Power BI Desktop no requiere combinar consultas para informar sobre estas. Sin embargo, puede usar las relaciones entre los conjuntos de datos, en función de los campos que tengan en común, para ampliar y enriquecer los informes. Power BI Desktop puede detectar automáticamente las relaciones, o puede crearlas en el cuadro de diálogo **Administrar relaciones** de Power BI Desktop. Para obtener más información sobre las relaciones en Power BI Desktop, vea [Crear y administrar relaciones](desktop-create-and-manage-relationships.md).

Los conjuntos de datos de pedidos y productos de este tutorial comparten un campo *ProductID* común, por lo que existe una relación entre ellos basada en dicha columna. 

1. En la vista de informe de Power BI Desktop, seleccione **Administrar relaciones** en el área **Relaciones** de la pestaña **Inicio** de la cinta de opciones.
   
   ![Cinta de opciones Administrar relaciones](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. En el cuadro de diálogo **Administrar relaciones**, observe que Power BI Desktop ya ha detectado y enumerado una relación activa entre las tablas de productos y pedidos. Para ver la relación, seleccione **Editar**. 
   
   ![Cuadro de diálogo Administrar relaciones](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   Se abre el cuadro de diálogo **Editar relación**, donde se muestran los detalles sobre la relación.  
   
   ![Cuadro de diálogo Editar relación](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. Power BI Desktop ha detectado automática y correctamente la relación; por tanto, puede seleccionar **Cancelar** y luego **Cerrar** para salir de los cuadros de diálogo de relaciones.

También puede ver y administrar las relaciones entre las consultas si selecciona la vista **Relación** en el lado izquierdo de la ventana de Power BI Desktop. Haga doble clic en la flecha situada en la línea que conecta las dos consultas para abrir el cuadro de diálogo **Editar relación** y ver o cambiar la relación. 

![Vista de relación](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Para volver a la vista de informe desde la vista de relaciones, seleccione el icono de **Vista de informe**. 

![Icono de la vista Informe](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Creación de visualizaciones con los datos

En la vista de informe de Power BI Desktop, puede crear una amplia gama de visualizaciones para obtener información a partir de los datos. Puede generar informes con varias páginas y cada página puede tener varios objetos visuales. Tanto usted como otros usuarios pueden interactuar con las visualizaciones para ayudar a analizar y comprender los datos. Para obtener más información sobre cómo ver y editar informes en el servicio Power BI (el sitio), consulte la información sobre la [edición de un informe](service-interact-with-a-report-in-editing-view.md).

Puede usar los dos conjuntos de datos y la relación entre ellos para facilitar la visualización y el análisis de los datos de ventas. 

En primer lugar, cree un gráfico de columnas apiladas que utilice campos de las dos consultas para mostrar la cantidad de cada producto pedido. 

1. Seleccione el campo **Quantity** de **Orders** en el panel **Campos** de la derecha, o bien arrástrelo hasta un espacio en blanco en el lienzo. De esta forma se crea un gráfico de columnas apiladas en el que se muestra la cantidad total de todos los productos pedidos. 
   
2. Seleccione **ProductName** en **Products** en el panel **Campos**, o bien arrástrelo hasta el gráfico, para mostrar la cantidad de cada producto pedido. 
   
3. Para ordenar los productos según los más pedidos o los menos pedidos, seleccione los puntos suspensivos **Más opciones** ( **...** ) en la parte superior derecha de la visualización y luego seleccione **Ordenar por cantidad**.
   
4. Use los controladores de las esquinas del gráfico para ampliarlo, para que aparezcan más nombres de productos. 
   
   ![Gráfico de barras de cantidad por nombre de producto](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

A continuación, cree un gráfico en el que aparezcan los importes en dólares de los pedidos (**LineTotal**) a lo largo del tiempo (**OrderDate**). 

1. Sin ningún elemento seleccionado en el lienzo, seleccione **LineTotal** en **Orders** en el panel **Campos**, o bien arrástrelo hasta un espacio en blanco en el lienzo. En el gráfico de columnas apiladas se muestra la cantidad total en dólares de todos los pedidos. 
   
2. Con el gráfico seleccionado, seleccione **OrderDate** en **Orders**, o bien arrástrelo hasta el gráfico. En el gráfico ahora se muestran el total de línea de cada fecha de pedido. 
   
3. Para cambiar el tamaño de la visualización y poder ver más datos, arrastre las esquinas. 
   
   ![Gráfico de líneas LineTotals por OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Si solo ve los años en el gráfico (solo tres puntos de datos), despliegue la flecha que está junto a **OrderDate** en el campo **Eje** del panel **Visualizaciones** y seleccione **OrderDate** en lugar de **Jerarquía de fechas**. 

Por último, cree una visualización de mapa en la que se muestren las cantidades de pedidos de cada país. 

1. Sin ningún elemento seleccionado en el lienzo, seleccione **ShipCountry** en **Orders** en el panel **Campos**, o bien arrástrelo hasta un espacio en blanco en el lienzo. Power BI Desktop detecta que los datos se corresponden con los nombres de país y crea automáticamente una visualización de mapa, con un punto de datos para cada país que había realizado pedidos. 
   
2. Para que los tamaños de los puntos de datos reflejen las cantidades de pedidos de cada país, arrastre el campo **LineTotal** al mapa, o bien arrástrelo hasta **Arrastrar campos de datos aquí** en **Tamaño**, en la mitad inferior del panel **Visualizaciones**. Los tamaños de los círculos en el mapa ahora reflejan las cantidades en dólares de los pedidos de cada país. 
   
   ![Visualización de mapa LineTotals por ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interactuación con los objetos visuales de informes para analizar más

Power BI Desktop permite descubrir las futuras tendencias al interactuar con objetos visuales que se filtran y resaltan entre sí. Para más información, consulte [Filtrado y resaltado en informes](power-bi-reports-filters-and-highlighting.md). 

Debido a la relación que existe entre las consultas, las interacciones con una visualización afectarán a todas las demás visualizaciones de la página. 

En la visualización de mapa, seleccione el círculo en el centro de **Canadá**. Tenga en cuenta que se filtran las otras dos visualizaciones para resaltar los totales de línea y las cantidades de pedidos solo para Canadá.

![Datos de ventas filtrados para Canadá](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Si selecciona uno de los productos en el gráfico **Cantidad por ProductName**, el mapa y el gráfico de fechas se filtra para reflejar los datos de dicho producto y, si selecciona una de las fechas en el gráfico **LineTotal por OrderDate**, el mapa y gráfico de productos se filtran para mostrar los datos de dicha fecha. 
>[!TIP]
>Para anular una selección, vuelva a realizar la selección o seleccione alguna de las otras visualizaciones. 

## <a name="complete-the-sales-analysis-report"></a>Completar el informe de análisis de ventas

El informe completo combina los datos del archivo de Excel Products.xlsx y la fuente de OData de Northwind en objetos visuales que le ayudarán a analizar la información de pedidos de distintos países, períodos de tiempo y productos. Cuando el informe esté listo, puede [cargarlo en el servicio Power BI](desktop-upload-desktop-files.md) para compartirlo con otros usuarios de Power BI.

## <a name="next-steps"></a>Pasos siguientes
* [Lea otros tutoriales de Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Vea vídeos de Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite el foro de Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Lea el blog de Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)