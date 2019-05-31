---
title: Incorporación de un filtro a un informe en la vista Editar
description: Adición de un filtro de página, un filtro de visualización o un filtro de informe a un informe en Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 3666335394222d32bc13ce86d8d0a4ed421b5f73
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187630"
---
# <a name="add-a-filter-to-a-report-in-editing-view"></a>Incorporación de un filtro a un informe en la vista Editar

En este artículo se explica cómo agregar un filtro de página, un filtro de visualización, un filtro de informe o un filtro de obtención de detalles a un informe en Power BI. Para los ejemplos de este artículo se usa el servicio Power BI. Los pasos son casi idénticos en Power BI Desktop.

**¿Sabía qué?** Power BI tiene una nueva experiencia de filtro, actualmente en versión preliminar. Aprenda más sobre la [nueva experiencia de filtro en los informes de Power BI](power-bi-report-filter-preview.md).

![Nueva experiencia de filtro](media/power-bi-report-add-filter/power-bi-filter-reading.png)

## <a name="filters-in-editing-view-or-reading-view"></a>Filtros en la vista de edición o en la vista de lectura
Puede interactuar con informes en dos vistas diferentes: la vista de lectura y la vista de edición. Las funcionalidades de filtrado disponibles dependen de la vista en la que se encuentre. Lea toda la [información sobre filtros y resaltado en informes de Power BI](power-bi-reports-filters-and-highlighting.md) para obtener detalles.

En este artículo se describe cómo crear filtros en la **Vista de edición** del informe.  Para más información sobre los filtros en la vista de lectura, vea [Interacción con un informe en la vista de lectura en Power BI](consumer/end-user-report-filter.md).

## <a name="filter-types-in-the-filters-pane"></a>Tipos de filtro en el panel Filtros
Tanto si usa Desktop como el servicio de Power BI, el panel Filtros se muestra en el lado derecho del lienzo del informe. Si no se muestra el panel Filtros, seleccione el icono ">" en la esquina superior derecha para expandirlo.

Hay cuatro tipos de filtros: **filtro de página**, **filtro de objeto visual**, **filtro de obtención de detalles** y **filtro de informe**.

![panel Filtros en la Vista de lectura](media/power-bi-report-add-filter/power-bi-add-filter-reading-view.png)

Dado que los filtros se *conservan*, cuando sale del informe, Power BI conserva el filtro, la segmentación y otros cambios de la vista de datos que ha realizado. De esta forma, puede retomar el informe por donde lo dejó cuando vuelva a él. Si no quiere conservar los cambios de filtro, seleccione **Restablecer valores predeterminados** en la barra de menús superior.

![botón de filtro persistente](media/power-bi-report-add-filter/power-bi-reset-to-default.png)

## <a name="add-a-filter-to-a-visual"></a>Agregar un filtro a un objeto visual
Puede agregar un filtro de nivel de objeto visual a un objeto visual específico de dos maneras diferentes. 

* Filtre un campo que ya se use en la visualización.
* Identifique un campo que ya no se utiliza en la visualización y agregue ese campo directamente al cubo **Filtros de nivel de objeto visual**.

Además, este procedimiento usa el ejemplo de Análisis de venta al por menor, por si quiere descargarlo y seguirlo como referencia. [Descargue el ejemplo de análisis de venta al por menor](sample-retail-analysis.md).

### <a name="filter-the-fields-in-the-visual"></a>Filtrar los campos en el objeto visual


1. Seleccione **Editar informe** para abrir el informe en la vista de edición.
   
   ![Botón Editar informe](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Abra el panel Visualizaciones y filtros y el panel Campos (si no están ya abiertos).
   
   ![Las visualizaciones, filtros y campos de paneles](media/power-bi-report-add-filter/power-bi-display-panes.png)
3. Seleccione un objeto visual para activarlo. Todos los campos que se usan en el objeto visual se encuentran en el panel **Campos** y también se enumeran en el panel **Filtros**, en el encabezado **Filtros de nivel de objeto visual**.
   
   ![Seleccionar filtros de nivel de objeto visual](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
4. En este punto, vamos a agregar un filtro a un campo que ya se está usando en la visualización. 
   
    Desplácese hacia abajo hasta el área **Filtros de nivel visual** y seleccione la flecha para expandir el campo que quiere filtrar. En este ejemplo, vamos a filtrar **StoreNumberName**.
     
    ![La flecha expande el filtro](media/power-bi-report-add-filter/power-bi-visual-level-filter.png) 
    
    Establezca controles de filtrado **básico**, **avanzado** o **N principales**. En este ejemplo, se busca **cha** con el filtrado básico y se seleccionan los cinco almacenes.
     
    ![Buscar en el filtrado básico](media/power-bi-report-add-filter/power-bi-search-filter.png) 
   
    El objeto visual cambia para reflejar el nuevo filtro. Si guarda el informe con el filtro, los lectores de informes verán el objeto visual filtrado para empezar a trabajar con él y podrán interactuar con el filtro en la vista de lectura y activar o desactivar valores.
     
    ![El objeto visual filtrado](media/power-bi-report-add-filter/power-bi-search-visual-filter-results.png)

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>Filtrar con un campo que no está en el objeto visual

Ahora vamos a agregar un campo nuevo a la visualización como un filtro de nivel de objeto visual.
   
1. En el panel Campos, seleccione el campo que quiere agregar como nuevo filtro de nivel visual y arrástrelo al área **Filtros de nivel de objeto visual**.  En este ejemplo se arrastra **District Manager** al cubo **Filtros de nivel de objeto visual**, se busca **an** y se seleccionan esos tres administradores. 
     
    ![Agregar un campo al panel filtros](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    Tenga en cuenta que **District Manager** *no* se agrega a la misma visualización. La visualización se todavía se compone de **StoreNumberName** como el eje y **This Year Sales** como el valor.  
     
    ![El campo no se encuentra en el objeto visual](media/power-bi-report-add-filter/power-bi-visualization.png)

    Además, la misma visualización ahora se filtra para mostrar solo las ventas de los administradores de este año en los almacenes especificados.
     
    ![El objeto visual filtrado](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    Si guarda el informe con este filtro, los lectores de informes pueden interactuar con el filtro **District Manager** en la vista de lectura y activar o desactivar valores.

## <a name="add-a-filter-to-an-entire-page"></a>Agregar un filtro a una página completa

También puede agregar un nivel de página filtro para aplicarlo a una página completa.

1. Seleccione **Editar informe** para abrir el informe en la vista de edición.
   
   ![Botón Editar informe](media/power-bi-report-add-filter/power-bi-edit-view.png)
2. Abra el panel Visualizaciones y filtros y el panel Campos (si no están ya abiertos).
3. En el panel Campos, seleccione el campo que quiere agregar como nuevo filtro de nivel de página y arrástrelo al área **Filtros de nivel de página**.  
4. Seleccione los valores que quiera filtrar y establecer mediante los controles de filtrado **básico** o **avanzado**.
   
   Todas las visualizaciones en la página se vuelve a dibujar para reflejar el cambio.
   
   ![Agregar un filtro y seleccione los valores](media/power-bi-report-add-filter/filterpage.gif)

    Si guarda el informe con el filtro, los lectores de informes pueden interactuar con el filtro en la vista de lectura y activar o desactivar valores.

## <a name="add-a-drillthrough-filter"></a>Adición de un filtro de obtención de detalles
Con la obtención de detalles en el servicio Power BI y Power BI Desktop, puede crear una página en el informe de *destino* que se centra en una entidad específica, como un proveedor, un cliente o un fabricante. Ahora, desde las otras páginas del informe, los usuarios hacer clic con el botón derecho en un punto de datos de esa entidad y obtener detalles en la página específica.

### <a name="create-a-drillthrough-filter"></a>Creación de un filtro de obtención de detalles
Para poder continuar, descargue el [ejemplo Customer Profitability](sample-customer-profitability.md). Supongamos que desea una página que se centra en áreas de negocio ejecutivas.

1. Seleccione **Editar informe** para abrir el informe en la vista de edición.
   
   ![Botón Editar informe](media/power-bi-report-add-filter/power-bi-edit-view.png)

1. Agregue una nueva página al informe y asígnele el nombre **Equipo ejecutivo**. Esta será la página de *destino* de la obtención de detalles.
2. Agregue visualizaciones que realicen el seguimiento de las métricas clave de las áreas de negocios de los equipos ejecutivos.    
3. Agregue **Ejecutivo > Nombre del ejecutivo** al área de filtros de obtención de detalles.    
   
    ![Agregar un valor a los filtros de obtención de detalles](media/power-bi-report-add-filter/power-bi-drillthrough-filter.png)
   
    Observe que Power BI agrega una flecha hacia atrás a la página del informe.  Al seleccionar la flecha atrás se devuelve a los usuarios la página del informe *original*, la página en la que estaban cuando seleccionaron la obtención de detalles. La flecha atrás solo funciona en la vista de lectura.
   
     ![La flecha Atrás](media/power-bi-report-add-filter/power-bi-back-arrow.png)

### <a name="use-the-drillthrough-filter"></a>Uso del filtro de obtención de detalles
Veamos cómo funciona el filtro de obtención de detalles.

1. Comience en la página del informe **Cuadro de mandos de equipo**.    
2. Supongamos que es Andrew Ma y desea ver la página del informe del equipo ejecutivo filtrada por sus datos únicamente.  En el gráfico del área superior izquierda, haga clic con el botón derecho en cualquier punto de datos verde para abrir la opción de menú Obtención de detalles.
   
    ![Inicia la acción de obtención de detalles](media/power-bi-report-add-filter/power-bi-drillthrough.png)
3. Seleccione **Obtención de detalles > Equipo ejecutivo** para la obtención de detalles en la página del informe llamada **Equipo ejecutivo**. La página se filtra para mostrar información acerca del punto de datos desde el que se hizo clic con el botón derecho, en este caso, Andrew Ma. Solo el campo que se encuentra en el área Filtros de obtención de detalles lleva a la página de obtención de detalles del informe.  
   
    ![Seleccione la acción de obtención de detalles](media/power-bi-report-add-filter/power-bi-drillthrough-executive.png)

## <a name="add-a-report-level-filter-to-filter-an-entire-report"></a>Agregue un nivel de informe de filtro para filtrar un informe completo

1. Seleccione **Editar informe** para abrir el informe en la vista de edición.
   
   ![Botón Editar informe](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Abra el panel visualizaciones y filtros y el panel campos, si no está ya abiertos.
3. En el panel Campos, seleccione el campo que quiere agregar como nuevo filtro de nivel de informe y arrástrelo al área **Filtros de nivel de informe**.  
4. Seleccione los valores que desea filtrar.

    Los objetos visuales de la página activa, y de todas las páginas del informe, cambian para reflejar el nuevo filtro. Si guarda el informe con el filtro, los lectores de informes pueden interactuar con el filtro en la vista de lectura y activar o desactivar valores.

1. Seleccione la flecha Atrás para volver a la página anterior del informe.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

- Hay situaciones en las que el filtro de nivel de objeto visual y el filtro de nivel de página pueden devolver resultados diferentes.  Por ejemplo, al agregar un filtro de nivel de objeto visual, Power BI filtra los resultados agregados.  La agregación predeterminada es la suma, pero puede [cambiar el tipo de agregación](service-aggregates.md).  

    Después, cuando agrega un filtro de nivel de página, Power BI filtra sin ninguna agregación.  El motivo es que una página puede tener varios objetos visuales, cada uno de los cuales puede usar diferentes tipos de agregaciones.  Por lo tanto, el filtro se aplica en cada fila de datos.

- Si no ve el panel Campos, asegúrese de que se encuentra en la [vista de edición](service-interact-with-a-report-in-editing-view.md) del informe.    
- Si ha realizado muchos cambios en los filtros y quiere volver a la configuración predeterminada del autor del informe, seleccione **Restablecer valores predeterminados** en la barra de menús superior.

## <a name="next-steps"></a>Pasos siguientes
[Ver el panel Filtros del informe](consumer/end-user-report-filter.md)

[Filtrado y resaltado en informes](power-bi-reports-filters-and-highlighting.md)

[Interacción con filtros y resaltado en la vista de lectura del informe](consumer/end-user-reading-view.md)

[Cambiar el filtro cruzado y el resaltado cruzado entre los objetos visuales de los informes](consumer/end-user-interactions.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

