---
title: Paseo por el panel de filtros de informe
description: Cómo agregar un filtro a un informe en el servicio Power BI para consumidores
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/30/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: dcf62925d8e5eef07fb6295f8d8141413947f8fb
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413127"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ver el panel Filtros del informe
En este artículo echa un vistazo en el panel de filtros de informe en el servicio Power BI. Utilice los filtros para descubrir nuevas perspectivas en los datos.

Hay muchas maneras diferentes de filtrar los datos en Power BI, por eso es recomendable leer primero el artículo [Filtros y resaltado](../power-bi-reports-filters-and-highlighting.md).

![informar en el explorador](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Trabajar con el panel Filtros de informes
Cuando algún compañero comparta un informe con usted, asegúrese de buscar el panel **Filtros**. A veces se contrae en el borde derecho del informe. Selecciónelo para expandirlo.   

![informar en el explorador](media/end-user-report-filter/power-bi-filter-pane.png)

El panel Filtros contiene filtros que el *diseñador* de informes ha agregado al informe. *Los consumidores* como usted, puede interactuar con los filtros existentes y guarde los cambios, pero no se puede agregar nuevos filtros para el informe. Por ejemplo, en la captura de pantalla anterior el diseñador agregó dos filtros de nivel de página: Segmento y el año de ejecución. Puede cambiar estos filtros e interactuar con ellos, pero no agregar un tercer filtro de nivel de página.

En el servicio Power BI, informes de conservar los cambios que realice en el panel filtros y dichos cambios se aplican a través de la versión móvil del informe. Para restablecer los valores predeterminados del diseñador en el panel Filtro, seleccione **Restablecer valores predeterminados** en la barra de menús superior.  

![Restablecer valores predeterminados](media/end-user-report-filter/power-bi-reset-to-default.png)   

## <a name="view-all-the-filters-for-a-report-page"></a>Ver todos los filtros de una página de informe
El panel filtros muestra todos los filtros que se agregan al informe mediante el *diseñador*. El panel de filtros también es el área donde puede ver información acerca de los filtros e interactuar con ellos. Puede guardar los cambios que realizan o utilizan **Restablecer valores predeterminados** para revertir a la configuración del filtro original.

Si hay cambios que le gustaría guardar, también puede crear un marcador personal.  Para obtener más información, consulte [agregar un marcador a un informe](end-user-bookmarks.md).

Hay varios tipos de filtros de informe que se muestran y administran en el panel filtros, las que se aplican a un objeto visual, a una página del informe y a todo el informe.

En este ejemplo, hemos seleccionado un objeto visual que tiene 2 filtros. La página del informe también tiene filtros, que se muestran bajo el **filtros en esta página** encabezado. Y todo el informe tiene un filtro de fecha.

![lista de filtros](media/end-user-report-filter/power-bi-all-filters2.png)

Algunos de los filtros tienen la palabra **Todo** junto a ellos, lo que indica que se incluyen como filtro todos los valores.  Por ejemplo, **Segment(All)** en la captura de pantalla anterior nos indica que esta página del informe incluye datos acerca de todos los segmentos de producto.  Por otro lado, el nivel de página de filtro de **la región Oeste es** nos indica que la página del informe solo incluye los datos de la región Oeste.

Cualquier persona que vea este informe puede interactuar con estos filtros.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Ver solo esos filtros aplicados a un objeto visual
Para obtener una visión más detallada de los filtros aplicados a un objeto visual específico, mantenga el mouse sobre el objeto visual para mostrar el icono de filtro ![icono](media/end-user-report-filter/power-bi-filter-icon.png). Seleccione ese icono de filtro para ver un elemento emergente con todas las segmentaciones, filtros y así sucesivamente, que afectan a ese objeto visual. Los filtros en la ventana emergente son los mismos filtros que se muestra en el **filtros** panel. 

![lista de filtros](media/end-user-report-filter/power-bi-hover-visual-filter.png)

 
Estos son los tipos de filtros que puede mostrar esta vista:
- Filtros básicos
- Segmentaciones
- Resaltado cruzado
- Filtrado cruzado
- Filtros avanzados
- N filtros principales
- Filtros de fecha relativa
- Segmentaciones de sincronización
- Filtros de inclusión o exclusión
- Filtros que se pasan mediante una dirección URL



En el ejemplo, a continuación:
1. Podemos ver que el gráfico de columnas ha sido un filtrado cruzado.
2. **Incluye** nos indica que es el filtro cruzado para **segmento**, y se incluyen tres. 
3. Se ha aplicado una segmentación de datos para **trimestre**.
4. **Región** es un filtro aplicado a esta página del informe, y
5. **isVanArsdel** y **año** son filtros aplicados a este objeto visual.


![lista de filtros](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Búsqueda en un filtro
A veces, un filtro puede tener una larga lista de valores. Utilice el cuadro de búsqueda para buscar y seleccionar el valor que desee. 

![Búsqueda en un filtro](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Mostrar detalles del filtro
Para entender un filtro, eche un vistazo a los valores disponibles y los recuentos.  Ver los detalles del filtro por encima de él y seleccione la flecha situada junto al nombre de filtro. 
  
![muestra Lindseys seleccionado](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Cambiar las selecciones de filtro
Es una manera de buscar información sobre los datos interactuar con los filtros. Puede cambiar las selecciones de filtro mediante la flecha desplegable situada junto al nombre de campo.  Según el filtro y el tipo de datos que se está filtrados, sus opciones estará comprendida entre selecciones simple de una lista para identificar los intervalos de fechas o números. En el filtro avanzado a continuación, hemos cambiado el filtro **Total de unidades de YTD** en el gráfico de rectángulos para estar entre 2000 y 3000. Tenga en cuenta que esto quita Prirum desde el gráfico de rectángulos. 
  
![muestra Fashions Direct seleccionado](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Para seleccionar más de un valor de filtro a la vez, mantenga presionada la tecla CTRL. Mayoría de los filtros admite la selección múltiple. 

### <a name="reset-filter-to-default"></a>Restablecer valores predeterminados de filtro
Si desea salir de todos los cambios realizados en los filtros, seleccionados **Restablecer valores predeterminados** desde la barra de menús superior.  Esto revierte los filtros a su estado original, según lo establecido por el informe *diseñador*. 

![Restablecer valores predeterminados](media/end-user-report-filter/power-bi-reset-to-default.png)
    
### <a name="clear-a-filter"></a>Borrado de un filtro
Si hay solo un filtro que le gustaría establecer **(All)** , desactívela seleccionando el icono de borrador ![ icono de borrador ](media/end-user-report-filter/power-bi-eraser-icon.png) junto al nombre del filtro.
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Pasos siguientes
[Obtener información sobre cómo y por qué cambiar el filtro cruzado y el resaltado cruzado entre los objetos visuales en una página de informe](end-user-interactions.md)