---
title: Cmdlets de PowerShell, API de REST y SDK de .NET para administradores
description: Obtenga información sobre las distintas formas de administrar Power BI a través de scripts y API de programación.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: f4455fef5a2ed0e7ee23ff8ca3a0b626cd695838
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51508000"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Cmdlets de PowerShell, API de REST y SDK de .NET para la administración de Power BI
Con Power BI, los administradores pueden generar scripts de tareas comunes usando cmdlets de PowerShell. Power BI expone también API de REST y proporciona un SDK de .NET para desarrollar soluciones de carácter administrativo. En este tema encontrará una lista de cmdlets y el método de SDK y punto de conexión de API de REST correspondientes. Para más información, consulte:

  - [Descarga](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) y [documentación](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) de PowerShell
  - [Documentación](https://docs.microsoft.com/rest/api/power-bi/admin) de la API de REST
  - [Descarga](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) de SDK de .NET 


| **Nombre del cmdlet** | **Método del SDK** | **Punto de conexión de la API de REST** | **Descripción** |
| --- | --- | --- | --- |
| **Get-PowerBIDatasource** | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtiene los orígenes de datos de un conjunto de datos determinado. |
| **Get-PowerBIDataset** | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | Obtiene la lista completa de conjuntos de datos de un inquilino de Power BI. |
| **Get-PowerBIWorkspace** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Obtiene la lista completa de áreas de trabajo de un inquilino de Power BI. |
| **Add-PowerBIWorkspaceUser** | Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Agrega un usuario como miembro a un área de trabajo determinada. |
| **Remove-PowerBIWorkspaceUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Quita un usuario de la lista de miembros de un área de trabajo determinada. |
| **Restore-PowerBIWorkspace** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Restaura un área de trabajo eliminada. |
| **Set-PowerBIWorkspace** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Actualiza las propiedades de un área de trabajo determinada. |
| **Get-PowerBIDataset -WorkspaceId** | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtiene los conjuntos de datos de un área de trabajo determinada. |
| **Export-PowerBIReport** | Reports\_ExportReportAsAdmin | N/D | Exporta un informe determinado a un archivo local. |
| **Get-PowerBIReport** | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Obtiene la lista completa de informes de un inquilino de Power BI. |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Obtiene la lista completa de paneles de un inquilino de Power BI. |
| **Get-PowerBIDashboard -WorkspaceId** | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtiene los paneles de un área de trabajo determinada. |
| **Get-PowerBITile -DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtiene los iconos de un panel determinado. |
| **Get-PowerBIReport -WorkspaceId** | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtiene los informes de un área de trabajo determinada. |
| **Get-PowerBIImport** | Imports\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Obtiene la lista completa de importaciones de un inquilino de Power BI. |
| **Connect-PowerBIServiceAccount** | N/D | N/D | Inicia sesión en Power BI y comienza una sesión. |
| **Disconnect-PowerBIServiceAccount** | N/D | N/D | Cierra sesión en Power BI y cierra la sesión existente. |
| **Invoke-PowerBIRestMethod** | N/D | N/D | Envía llamadas de API de REST arbitrarias a Power BI. |
| **Get-PowerBIAccessToken** | N/D | N/D | Obtiene el token de acceso de Power BI en una sesión. |
| **Resolve-PowerBIError** | N/D | N/D | Obtiene información detallada de un error relativo a llamadas de cmdlet incorrectas. |