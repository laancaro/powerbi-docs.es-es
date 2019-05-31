---
title: Conexión a Application Insights con Power BI
description: Application Insights para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/10/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 3f0a23c2bdb97c6fbc75981c40cb92c529550b1b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61177258"
---
# <a name="connect-to-application-insights-with-power-bi"></a>Conexión a Application Insights con Power BI
Use Power BI para crear paneles personalizados eficaces a partir de la telemetría de [Application Insights](/azure/application-insights/app-insights-overview/). Visualice la telemetría de la aplicación de nuevas maneras. Combine las métricas de varias aplicaciones o servicios de componentes en un panel. Esta primera versión del paquete de contenido de Power BI para Application Insights incluye widgets para métricas comunes relacionadas con el uso, como usuarios activos, vista de página, sesiones, explorador, versión del explorador y el sistema operativo, y distribución geográfica de los usuarios en un mapa.

Conéctese al [paquete de contenido de Application Insights para Power BI](https://app.powerbi.com/getdata/services/application-insights).

>[!NOTE]
>Este método de integración ahora está **en desuso**. Para obtener más información sobre el método preferido de conexión de Application Insights a Power BI, use la [funcionalidad de consulta de análisis de exportación](https://docs.microsoft.com/azure/application-insights/app-insights-export-power-bi#export-analytics-queries).

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.
   
    ![Botón Obtener datos](media/service-connect-to-application-insights/pbi_getdata.png)
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
    ![Botón Obtener servicios](media/service-connect-to-application-insights/pbi_getservices.png)
3. Seleccione **Application Insights** > **Obtener**.
   
    ![Paquete de contenido de Application Insights](media/service-connect-to-application-insights/appinsights.png)
4. Proporcione los detalles de la aplicación a la que desea conectarse, incluidos **Nombre de recurso**, **Grupo de recursos**e **Id. de suscripción**de Aplication Insights. Consulte [Búsqueda de parámetros de Application Insights](#FindingAppInsightsParams) a continuación para obtener más detalles.
   
    ![Cuadro de diálogo de conexión de Aplication Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. Seleccione **Iniciar sesión** y siga las pantallas para conectarse.
   
    ![Inicio de sesión de conexión de Aplication Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. El proceso de importación se inicia automáticamente. Cuando finaliza, se muestra una notificación y aparecen un panel, un informe y un conjunto de datos nuevos en el panel Navegación (marcados con un asterisco).  Seleccione el panel para ver los datos importados.
   
    ![Panel Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](consumer/end-user-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

## <a name="whats-included"></a>Qué se incluye
El paquete de contenido de Application Insights incluye las siguientes tablas y métricas:  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>Búsqueda de parámetros
Los valores Nombre de recurso, Grupo de recursos e Id. de suscripción se pueden encontrar en Azure Portal. Al seleccionar el nombre se abrirá una vista detallada y podrá usar la lista desplegable Essentials para encontrar todos los valores que necesita.

![Parámetros de Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

Copie y pegue estos elementos en los campos de Power BI:

![Parámetros de Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>Pasos siguientes
[Introducción a Power BI](service-get-started.md)

[Obtener datos en Power BI](service-get-data.md)

