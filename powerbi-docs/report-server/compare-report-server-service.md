---
title: Comparación de Power BI Report Server y el servicio Power BI
description: En este artículo se comparan las características de Power BI Report Server y del servicio Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 01/16/2020
ms.openlocfilehash: f7f163a8930d8bd90d6270f59e8afa602e89dd57
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160843"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparación de Power BI Report Server y el servicio Power BI

Power BI Report Server y el servicio Power BI tienen muchas similitudes y algunas diferencias clave. En esta tabla se explican cuáles son.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Características de Power BI Report Server y el servicio Power BI

| Características | Power BI Report Server | Servicio Power BI | Notas |
|---------|---------|---------|---------|
| Implementación | Local u hospedada en la nube | Nube | Power BI Report Server se puede implementar en máquinas virtuales de Azure (implementación hospedada en la nube) si tiene licencia de Power BI Premium. |
| Datos de origen | Nube o local | Nube o local |  |
| Licencia | Power BI Premium o SQL Server EE con Software Assurance (SA) | Power BI Pro o Power BI Premium | |  
| Ciclo de vida | Directiva de ciclo de vida moderna | Servicio totalmente administrado |  |
| Ciclo de versiones | Tres veces al año (enero, mayo, septiembre) | Una vez al mes | Las últimas características y correcciones primero se incorporan en el servicio Power BI. La mayoría de las funcionalidades se incorporan en algunas de las próximas versiones de Power BI Report Server; algunas características solo están indicadas para el servicio Power BI. |
| Crear informes de Power BI en Power BI Desktop | Sí | Sí |  |
| Crear informes de Power BI en el explorador | No | Sí |  |
| Hospedar y conectarse a conjuntos de datos compartidos de Power BI | No | Sí | [Introducción a los conjuntos de datos de áreas de trabajo](../service-datasets-across-workspaces.md) |
| Se requiere una puerta de enlace | No | Sí para orígenes de datos locales |  |
| Streaming en directo | No | Sí | [Streaming en directo en Power BI](../service-real-time-streaming.md) |
| Paneles | No | Sí | [Paneles en el servicio Power BI](../consumer/end-user-dashboards.md) |
| Distribuir grupos de informes con aplicaciones | No | Sí | [Crear y publicar aplicaciones con los paneles e informes](../service-create-distribute-apps.md) |
| Paquetes de contenido | No | Sí | [Paquetes de contenido organizativo: Introducción](../service-organizational-content-pack-introduction.md) |
| Conectarse a servicios como Salesforce | Sí | Sí | [Conéctese a los servicios que usa](../service-connect-to-services.md) con paquetes de contenido en el servicio Power BI. En Power BI Report Server, use conectores certificados para conectarse a los servicios. Vea [Orígenes de datos de los informes de Power BI en Power BI Report Server](data-sources.md) para obtener más información. |
| Preguntas y respuestas | No | Sí | [Preguntas y respuestas en el servicio Power BI y Power BI Desktop](../power-bi-tutorial-q-and-a.md) 
| Información rápida | No | Sí | [Generación automática de información sobre los datos con Power BI](../consumer/end-user-insights.md) |
| Analizar en Excel | No | Sí | [Analizar en Excel](../service-analyze-in-excel.md) 
| Informes paginados | Sí | Sí | Los [informes paginados están disponibles en el servicio Power BI](../paginated-reports-report-builder-power-bi.md), en la versión preliminar en una capacidad Premium. |
| Aplicaciones móviles de Power BI | Sí | Sí | [Información general sobre aplicaciones móviles de Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| Mapas de ArcGIS | No | Sí | [Tutorial de mapas de ArcGIS de Esri en el servicio Power BI y Power BI Desktop](../visuals/power-bi-visualization-arcgis.md) |
| Suscripciones de correo electrónico para los informes de Power BI | No | Sí | [Suscripción personal o de otros usuarios](../service-report-subscribe.md) a un informe o panel en el servicio Power BI |
| Suscripciones de correo electrónico para informes paginados | Sí | Sí | [Suscripción personal y de otros usuarios a informes paginados en el servicio Power BI](../consumer/paginated-reports-subscriptions.md)<br><br>[Entrega de correo electrónico en Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  |
| Alertas de datos | No | Sí | [Alertas de datos](../service-set-data-alerts.md) en el servicio Power BI
| Seguridad de nivel de fila (RLS) | Sí | Sí | Disponible en DirectQuery (origen de datos) y en el modo de importación <br><br>Seguridad de nivel de fila (RLS) en el [servicio Power BI](../service-admin-rls.md) <br><br>Seguridad de nivel de fila (RLS) en [Power BI Report Server](row-level-security-report-server.md) |
| Modo de pantalla completa | No | Sí | [Modo de pantalla completa](../consumer/end-user-focus.md) en el servicio Power BI |
| Colaboración avanzada de Office 365 | No | Sí | [Colaboración en un área de trabajo](../service-collaborate-power-bi-workspace.md) con Office 365 |
| Objetos visuales de R | No | Sí | [Cree objetos visuales de R](../desktop-r-visuals.md) en Power BI Desktop y publíquelos en el servicio Power BI. No se pueden guardar los informes de Power BI con objetos visuales de R en Power BI Report Server.  |
| Características en vista previa | No | Sí | [Participación en las características de versión preliminar del servicio Power BI](../consumer/end-user-preview-features.md) |
| Objetos visuales personalizados | Sí | Sí | [Elementos visuales personalizados en Power BI](../developer/power-bi-custom-visuals.md) |
| Modelos compuestos | No | Sí |
| Power BI Desktop | Versión optimizada para Report Server, disponible para su descarga con Report Server | Versión optimizada para el servicio Power BI, disponible desde Mirosoft Store | [Power BI Desktop para Report Server](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para el servicio Power BI](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Pasos siguientes

[Instalar un servidor de informes de Power BI](install-report-server.md)
