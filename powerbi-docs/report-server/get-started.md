---
title: ¿Qué es Power BI Report Server?
description: Obtenga información general de Power BI Report Server para saber cómo se adapta a SQL Server Reporting Services (SSRS) y al resto de servicios de Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 11/20/2018
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: 23b78ba20666d1a1d942c7a5bd59991205991bc1
ms.sourcegitcommit: ccbe76a0a43c5c5e87354a33e617bf3cb291608e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394829"
---
# <a name="what-is-power-bi-report-server"></a>¿Qué es Power BI Report Server?

Power BI Report Server es un servidor de informes local con un portal web en el que muestra y administra informes y KPI. Junto con él, se incluyen herramientas para crear informes de Power BI, informes paginados, informes móviles y KPI. Los usuarios pueden acceder a los informes de maneras diferentes: verlos en un explorador web o en un dispositivo móvil, o como un correo electrónico en su bandeja de entrada.

![Portal web del servidor de informes de Power BI](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Comparación de Power BI Report Server 
Power BI Report Server es similar a SQL Server Reporting Services y al servicio en línea Power BI, pero con algunas diferencias. Al igual que el servicio Power BI, Power BI Report Server hospeda informes de Power BI (.PBIX) y archivos de Excel. Al igual que Reporting Services, Power BI Report Server es local y hospeda los informes paginados (.RDL). Power BI Report Server es un superconjunto de Reporting Services: todo lo que puede hacer en Reporting Services, puede hacerlo con Power BI Report Server, además de tener compatibilidad con los informes de Power BI. Vea [Comparación de Power BI Report Server y el servicio Power BI](compare-report-server-service.md) para obtener información detallada.

## <a name="licensing-power-bi-report-server"></a>Licencias de Power BI Report Server
Microsoft Power BI Report Server está disponible en dos licencias diferentes: [Power BI Premium](../service-premium.md) y [SQL Server Enterprise Edition](https://www.microsoft.com/sql-server/sql-server-2017-editions) con Software Assurance. Con una licencia de Power BI Premium, puede crear una implementación híbrida en la que se combine la nube y un entorno local.  

> [!NOTE]
> Para Power BI Premium, Power BI Report Server solo se incluye con las SKU P. No se incluye con las SKU EM.

## <a name="web-portal"></a>Portal web
El punto de entrada de Power BI Report Server es un portal web seguro que puede ver en cualquier explorador moderno. Aquí, accede a todos los informes y KPI. El contenido del portal web se organiza en una jerarquía de carpetas tradicional. En las carpetas, el contenido se agrupa por tipo: informes de Power BI, informes móviles, informes paginados, KPI y libros de Excel. Los conjuntos de datos y orígenes de datos compartidos se encuentran en sus propias carpetas, que usará como bloques de creación de informes. Etiquete favoritos para verlos en una sola carpeta y cree los KPI directamente en el portal web. 

![Portal web del servidor de informes de Power BI](media/get-started/web-portal.png)

Dependiendo de sus permisos, puede administrar el contenido en el portal web. Puede programar el procesamiento de informes, acceder a informes a petición y suscribirse a los informes publicados. Puede aplicar también su propia [marca](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal) personalizada al portal web. 

Obtenga más información sobre el [portal web de Power BI Report Server](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Informes de Power BI
Cree informes de Power BI (.PBIX) con la versión de Power BI Desktop optimizada para el servidor de informes. A continuación, publíquelos y véalos en el portal web en su propio entorno.

![Informes de Power BI en Power BI Report Server](media/get-started/powerbi-reports.png)

Un informe de Power BI es una vista de varias perspectivas de un modelo de datos, con visualizaciones que representan diferentes hallazgos e información detallada de ese modelo de datos.  Un informe puede tener una sola visualización o páginas enteras de visualizaciones. Dependiendo de su rol, puede leer y explorar los informes, o puede crearlos para otras personas.

Instale [Power BI Desktop optimizado para Power BI Report Server](quickstart-create-powerbi-report.md).

## <a name="paginated-reports"></a>Informes paginados
Los informes paginados (.RDL) son informes con estilo de documento con visualizaciones, en los que las tablas se expanden horizontalmente y verticalmente para mostrar todos sus datos, avanzando de una página a otra según sea necesario. Son excelentes para generar documentos de diseño fijo y apariencia perfecta, optimizados para la impresión, como los archivos PDF y de Word. 

![Informes paginados en Power BI Report Server](media/get-started/paginated-reports.png)

Para crear informes de aspecto moderno mediante el [Generador de informes](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) o el Diseñador de informes en [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt). 

## <a name="reporting-services-mobile-reports"></a>Informes móviles de Reporting Services
Los informes móviles se conectan a datos locales y tienen un diseño dinámico que se adapta a diferentes dispositivos y distintas maneras de contenerlos. Puede crearlos con el Publicador de informes móviles de Microsoft SQL Server.

Obtenga más información sobre los [Informes móviles de Reporting Services](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Características de programación del servidor de informes
Saque provecho de las características de programación de Power BI Report Server para que pueda extender y personalizar los informes, con API para integrar o extender el procesamiento de datos e informes en aplicaciones personalizadas.

Más [documentación para desarrolladores del servidor de informes](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Pasos siguientes
[Instalar un servidor de informes de Power BI](install-report-server.md)  
[Descarga del Generador de informes](https://www.microsoft.com/download/details.aspx?id=53613)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)


