---
title: Introducción a los iconos del panel para los diseñadores de Power BI
description: En este artículo se describen los iconos de panel en Power BI, que incluye los que se crean a partir de informes de SQL Server Reporting Services (SSRS).
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 801af5e9c4d5306a3e77d4e82c787cc90e9cac37
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872796"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Introducción a los iconos del panel para los diseñadores de Power BI

Un icono es una instantánea de sus datos, anclado en el panel. Un icono se puede crear desde un informe, un conjunto de datos, un panel, el cuadro de Preguntas y respuestas, Excel, informes de SQL Server Reporting Services (SSRS), etc.  Esta captura de pantalla muestra muchos iconos diferentes anclados a un panel.

![Panel de Power BI](media/service-dashboard-tiles/power-bi-dashboard.png)

Los paneles y los iconos de paneles son una característica del servicio Power BI y no de Power BI Desktop. No puede crear paneles en dispositivos móviles, pero puede [verlos y compartirlos](mobile-apps-view-dashboard.md) allí.

Además de anclar iconos, puede crear iconos independientes directamente en el panel mediante el control [Agregar icono](service-dashboard-add-widget.md). Los iconos independientes incluyen: cuadros de texto, imágenes, vídeos, datos de transmisión y contenido web.

¿Necesita ayuda para comprender los bloques de creación que conforman Power BI? Vea [Conceptos básicos para los diseñadores en el servicio Power BI](service-basic-concepts.md).

> [!NOTE]
> Si la visualización original usada para crear el icono cambia, no se produce ningún cambio en el icono.  Por ejemplo, si ancló un gráfico de líneas desde un informe y luego cambió el gráfico de líneas a un gráfico de barras, el icono del panel seguirá mostrando un gráfico de líneas. Los datos se actualizan, pero no el tipo de visualización.
> 
> 

## <a name="pin-a-tile"></a>Anclar un icono
Existen muchas maneras diferentes de agregar (anclar) un icono al panel. Puede anclar iconos desde:

* [Preguntas y respuestas de Power BI](service-dashboard-pin-tile-from-q-and-a.md)
* [Un informe](service-dashboard-pin-tile-from-report.md)
* [Otro panel](service-pin-tile-to-another-dashboard.md)
* [Un libro de Excel en OneDrive para la Empresa](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher para Excel](publisher-for-excel.md)
* [Quick Insights (Información rápida)](service-insights.md)
* [Un informe paginado local en Power BI Report Server o SQL Server Reporting Services](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Puede crear iconos independientes para imágenes, cuadros de texto, vídeos, datos de streaming y contenido web directamente en el panel mediante el control [Agregar icono](service-dashboard-add-widget.md).

  ![Icono de Agregar icono](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>Interactuar con los iconos en un panel
Después de agregar un icono a un panel, puede moverlo y cambiarlo de tamaño, o bien modificar su apariencia y comportamiento.

### <a name="move-and-resize-a-tile"></a>Mover un icono y cambiar su tamaño
Capte un icono y [muévalo por el panel](service-dashboard-edit-tile.md). Mantenga el puntero y seleccione el controlador ![controlador de icono](media/service-dashboard-tiles/resize-handle.jpg) para cambiar el tamaño del icono.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Mantener el puntero sobre un icono para cambiar la apariencia y comportamiento
1. Mantenga el puntero sobre el icono para que se muestren los puntos suspensivos.
   
    ![Puntos suspensivos de icono](media/service-dashboard-tiles/ellipses_new.png)
2. Seleccione los puntos suspensivos para abrir el menú de acciones del icono.
   
    ![Icono de puntos suspensivos](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Desde aquí, puede:
   
     * [Agregar comentarios al panel](consumer/end-user-comment.md).
     * [Abrir el informe que se ha usado para crear este icono](service-reports.md).  
     * [Ver en el modo de enfoque](service-focus-mode.md).   
     * [Exportar los datos que se usan en el icono](visuals/power-bi-visualization-export-data.md).
     * [Editar el título y el subtítulo, y agregar un hipervínculo](service-dashboard-edit-tile.md). 
     * [Ejecutar información detallada](service-insights.md). 
     * [Anclar el icono a otro panel](service-pin-tile-to-another-dashboard.md).
     * [Eliminar el icono](service-dashboard-edit-tile.md).

3. Para cerrar el menú de acciones, seleccione un área en blanco en el panel.

### <a name="select-a-tile"></a>Selección de un icono
Al seleccionar un icono, lo que sucede después depende de cómo lo ha creado. En caso contrario, al seleccionar el icono se le dirige al informe, al libro de Excel Online, al informe local de Reporting Services o a la pregunta de Preguntas y respuestas que se ha usado para crear el icono. O bien, si tiene un [vínculo personalizado](service-dashboard-edit-tile.md), al seleccionar el icono se le lleva a ese vínculo.

> [!NOTE]
> Una excepción son los iconos de vídeo creados directamente en el panel mediante **Agregar icono**. Al seleccionar un icono de vídeo (que se haya creado de este modo), el vídeo se reproduce directamente en el panel.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

* Si el informe que se ha usado para crear la visualización no se ha guardado, al seleccionar el icono no se realizará ninguna acción.
* Si el icono se ha creado desde un libro de Excel Online, debe tener al menos permisos de lectura para ese libro. De lo contrario, al seleccionar el icono no se abrirá el libro en Excel Online.
* Imagine que crea un icono directamente en el panel mediante **Agregar icono** y establece un hipervínculo personalizado para él. En ese caso, al seleccionar el título, el subtítulo o el icono, se abre esa dirección URL. De lo contrario, de forma predeterminada, al seleccionar un icono creado directamente en el panel para una imagen, un código web o un cuadro de texto, no sucede nada.
* Los iconos se pueden crear desde informes paginados locales en Power BI Report Server o SQL Server Reporting Services. Si no tiene permiso para acceder al informe local, al seleccionar el icono se le llevará a una página en la que se indica que no tiene acceso (rsAccessDenied).
* Imagine que selecciona un icono creado desde un informe paginado local en Power BI Report Server o SQL Server Reporting Services. Si no tiene acceso a la red donde se encuentra el servidor de informes, al seleccionar un icono creado desde ese informe paginado se le dirigirá a una página en la que se le indica que no se encuentra el servidor (HTTP 404). El dispositivo debe tener acceso de red al servidor de informes para ver el informe.
* Si cambia la visualización original usada para crear el icono, no se produce ningún cambio en el icono. Por ejemplo, si ancla un gráfico de líneas desde un informe y luego cambia el gráfico de líneas a un gráfico de barras, el icono del panel sigue mostrando un gráfico de líneas. Los datos se actualizan, pero no el tipo de visualización.

## <a name="next-steps"></a>Pasos siguientes
- [Creación de una tarjeta (icono grande de número) para el panel](power-bi-visualization-card.md)
- [Introducción a los paneles para los diseñadores de Power BI](service-dashboards.md)  
- [Actualizar datos en Power BI](refresh-data.md)
- [Conceptos básicos para los diseñadores en el servicio Power BI](service-basic-concepts.md)
- [Integración de iconos de Power BI en documentos de Office](https://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)
- [Anclado de elementos de Reporting Services en los paneles de Power BI](https://msdn.microsoft.com/library/mt604784.aspx)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/).

