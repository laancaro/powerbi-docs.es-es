---
title: Cmdlets de PowerShell, API de REST y SDK de .NET para administradores
description: Obtenga información sobre las distintas formas de administrar Power BI a través de scripts y API de programación.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: da19eaffff7abfd8edd745cdb58c008ea40eee8a
ms.sourcegitcommit: 9665997274301b228f45aa7250ba557e90164a4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70751500"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Cmdlets de PowerShell, API de REST y SDK de .NET para la administración de Power BI
Con Power BI, los administradores pueden generar scripts de tareas comunes usando cmdlets de PowerShell. Power BI expone también API de REST y proporciona un SDK de .NET para desarrollar soluciones de carácter administrativo. En este tema encontrará una lista de cmdlets y el método de SDK y punto de conexión de API de REST correspondientes. Para más información, consulte:

- [Descarga](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) y [documentación](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) de PowerShell
- [Documentación](https://docs.microsoft.com/rest/api/power-bi/admin) de la API de REST
- [Descarga](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) de SDK de .NET

> Se debe llamar a los cmdlets siguientes con `-Scope Organization` para operar en el inquilino de cara a la administración.

| **Nombre del cmdlet** | **Alias** | **Método del SDK** | **Punto de conexión de la API de REST** | **Descripción** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/A | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtiene los orígenes de datos de un conjunto de datos determinado. |
| `Get-PowerBIDataset` | N/A | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Obtiene la lista completa de conjuntos de datos de un inquilino de Power BI. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Obtiene la lista completa de áreas de trabajo de un inquilino de Power BI. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Agrega un usuario como miembro a un área de trabajo determinada. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Quita un usuario de la lista de miembros de un área de trabajo determinada. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Restaura un área de trabajo eliminada. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Actualiza las propiedades de un área de trabajo determinada. |
| `Get-PowerBIDataset -WorkspaceId` | N/A | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtiene los conjuntos de datos de un área de trabajo determinada. |
| `Get-PowerBIReport` | N/A | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Obtiene la lista completa de informes de un inquilino de Power BI. |
| `Get-PowerBIDashboard` | N/A | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Obtiene la lista completa de paneles de un inquilino de Power BI. |
| `Get-PowerBIDashboard -WorkspaceId` | N/A | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtiene los paneles de un área de trabajo determinada. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtiene los iconos de un panel determinado. |
| `Get-PowerBIReport` | N/A | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtiene los informes de un área de trabajo determinada. |
| `Get-PowerBIImport` | N/A | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Obtiene la lista completa de importaciones de un inquilino de Power BI. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/A | N/A | Inicia sesión en Power BI y comienza una sesión. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/A | N/A | Cierra sesión en Power BI y cierra la sesión existente. |
| `Invoke-PowerBIRestMethod`| N/A | N/D | N/A | Envía llamadas de API de REST arbitrarias a Power BI. |
| `Get-PowerBIAccessToken`| N/A | N/D | N/A | Obtiene el token de acceso de Power BI en una sesión. |
| `Resolve-PowerBIError`| N/A | N/D | N/A | Obtiene información detallada de un error relativo a llamadas de cmdlet incorrectas. |
