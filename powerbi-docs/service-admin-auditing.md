---
title: Usar la auditoría dentro de su organización
description: Obtenga información sobre cómo puede usar la auditoría con Power BI para supervisar e investigar las acciones realizadas. Puede usar el Centro de seguridad y cumplimiento o usar PowerShell.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 294fb3a0142908ce0ab068e075ce39f950a0b124
ms.sourcegitcommit: d20f74d5300197a0930eeb7db586c6a90403aabc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2018
ms.locfileid: "50973359"
---
# <a name="using-auditing-within-your-organization"></a>Usar la auditoría dentro de su organización

Es fundamental saber quién realiza cada acción en cada elemento del inquilino de Power BI para ayudar a la organización a satisfacer sus requisitos, como el cumplimiento normativo y la administración de registros. Use las funciones de auditoría de Power BI para auditar las acciones que realizan los usuarios, como "Ver informe" o "Ver panel". No se pueden utilizar para auditar permisos.

Trabaje con las funciones de auditoría en el Centro de seguridad y cumplimiento de Office 365 o use PowerShell. Trataremos ambas opciones en este artículo. Puede filtrar los datos de auditoría por intervalo de fechas, usuario, panel, informe, conjunto de datos y tipo de actividad. También puede descargar las actividades en un archivo .csv (valores separados por comas) para analizarlo sin conexión.

## <a name="requirements"></a>Requisitos

Debe cumplir estos requisitos para tener acceso a los registros de auditoría:

- Para acceder a la sección de auditoría del Centro de seguridad y cumplimiento de Office 365, debe tener una licencia de Exchange Online (que se incluye con las suscripciones de Office 365 Enterprise E3 y E5).

- Debe ser un administrador global o tener un rol de administrador de Exchange que proporcione acceso al registro de auditoría. Los roles de administrador de Exchange se controlan mediante el centro de administración de Exchange. Para más información, vea [Permisos en Exchange Online](/exchange/permissions-exo/permissions-exo/).

- Si tiene acceso al registro de auditoría pero no es un administrador global o un administrador del servicio Power BI, no tendrá acceso al portal de administración de Power BI. En este caso, deberá obtener un vínculo directo al [Centro de seguridad y cumplimiento de Office 365](https://sip.protection.office.com/#/unifiedauditlog).

- Para ver registros de auditoría para Power BI en su inquilino, necesita al menos una licencia de buzón de Exchange en dicho inquilino.

## <a name="accessing-your-audit-logs"></a>Obtener acceso a los registros de auditoría

Para acceder a los registros, asegúrese de que el registro está habilitado en Power BI. Para más información, vea [Registros de auditoría](service-admin-portal.md#audit-logs) en la documentación del portal de administración. Puede haber una demora de hasta 48 horas entre la habilitación de la auditoría y el momento en el que se empiecen a mostrar los datos de auditoría. Si no ve los datos de inmediato, consulte los registros de auditoría más tarde. Puede haber una demora similar entre la obtención de permisos para ver los registros de auditoría y la posibilidad de acceder a estos.

Los registros de auditoría de Power BI están disponibles directamente en el [Centro de seguridad y cumplimiento de Office 365](https://sip.protection.office.com/#/unifiedauditlog). También hay un vínculo desde el portal de administración de Power BI:

1. En Power BI, seleccione el **icono de engranaje** en la esquina superior derecha y luego seleccione **Portal de administración**.

   ![Portal de administración](media/service-admin-auditing/powerbi-admin.png)

1. Seleccione **Registros de auditoría**.

1. Seleccione **Ir al Centro de administración de O365**.

   ![Ir al Centro de administración de O365](media/service-admin-auditing/audit-log-o365-admin-center.png)

Para las cuentas que no sean de administrador con acceso al registro de auditoría, debe asignar permisos en el Centro de administración de Exchange Online. Por ejemplo, puede asignar un usuario a un grupo de roles existente, como Administración de organizaciones, o puede crear un nuevo grupo de roles con el rol Registros de auditoría. Para más información, vea [Permisos en Exchange Online](/exchange/permissions-exo/permissions-exo/).

## <a name="search-only-power-bi-activities"></a>Buscar solo actividades de Power BI

Restrinja los resultados solo a las actividades de Power BI; para ello siga estos pasos. Para obtener una lista de actividades, consulte la [lista de actividades auditadas por Power BI](#list-of-activities-audited-by-power-bi) más adelante en este artículo.

1. En la página **Búsqueda de registros de auditoría**, seleccione la lista desplegable **Actividades** en **Buscar**.

2. Seleccione **Actividades de Power BI**.

   ![Búsqueda de registros de auditoría](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Seleccione un lugar fuera del cuadro de selección para cerrarlo.

Ahora, las búsquedas se filtrarán de modo que solo aparezcan actividades de Power BI.

## <a name="search-the-audit-logs-by-date"></a>Buscar en los registros de auditoría por fecha

Puede buscar registros por intervalo de fechas mediante el campo **Fecha de inicio** y **Fecha de finalización**. De forma predeterminada, están seleccionados los últimos siete días. La fecha y hora se presentan en formato de hora universal coordinada (UTC). El intervalo de fechas máximo que se puede especificar es de 90 días. 

Si el intervalo de fechas seleccionado es superior a 90 días, se muestra un error. Si usa el intervalo de fechas máximo de 90 días, debe seleccionar la hora actual en la **fecha de inicio**. En caso contrario, recibirá un error que indica que la fecha de inicio es anterior a la fecha de finalización. Si ha activado la auditoría durante los 90 últimos días, el intervalo de fechas no puede empezar antes de la fecha de activación de la auditoría.

![](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Buscar en los registros de auditoría por usuario

Puede buscar entradas del registro de auditoría para actividades realizadas por usuarios específicos. Para ello, escriba uno o varios nombres de usuario en el campo **Usuarios**. El nombre de usuario es similar a una dirección de correo electrónico; es la cuenta con la que los usuarios inician sesión en Power BI. Si deja este cuadro en blanco, se devolverán las entradas de todos los usuarios (y las cuentas de servicio) de la organización.

![Buscar por fecha](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Ver los resultados de la búsqueda

Después de seleccionar **Buscar**, se cargarán los resultados de la búsqueda y, tras unos instantes, se mostrarán en **Resultados**. Cuando la búsqueda haya finalizado, se mostrará el número de resultados encontrados. Se muestra un máximo de 1000 eventos; si hay más de 1000 eventos que cumplen los criterios de búsqueda, se mostrarán los 1000 eventos más recientes.

### <a name="view-the-main-results"></a>Ver los resultados principales

El área **Resultados** contiene la siguiente información sobre cada evento devuelto por la búsqueda. Seleccione un encabezado de columna en **Resultados** para ordenar los resultados.

| **Columna** | **Definición** |
| --- | --- |
| Fecha |Fecha y hora (en formato UTC) en las que se produjo el evento. |
| IP address (Dirección IP) |Dirección IP del dispositivo que se ha usado al registrar la actividad. La dirección IP se muestra en el formato de dirección IPv4 o IPv6. |
| User (Usuario) |Usuario (o cuenta de servicio) que realizó la acción que desencadenó el evento. |
| Activity (Actividad) |Actividad realizada por el usuario. Este valor corresponde a las actividades que se seleccionaron en la lista desplegable **Actividades**. En el caso de un evento del registro de auditoría de administración de Exchange, el valor de esta columna es un cmdlet de Exchange. |
| Item (Elemento) |Objeto creado o modificado como resultado de la actividad correspondiente. Por ejemplo, el archivo que se ha visualizado o se ha modificado, o bien la cuenta de usuario que se ha actualizado. No todas las actividades tienen un valor en esta columna. |
| Detail (Detalle) |Detalles adicionales sobre una actividad. También en este caso, no todas las actividades tienen un valor. |

### <a name="view-the-details-for-an-event"></a>Ver los detalles de un evento

Para ver más detalles de un evento, haga clic en el registro de eventos en la lista de los resultados de la búsqueda. Se muestra una página de **detalles** que contiene las propiedades detalladas del registro de eventos. Las propiedades que se muestran dependen del servicio de Office 365 en el que se produce el evento. 

Para mostrar estos detalles, seleccione **Más información**. Todas las entradas de Power BI tienen un valor de 20 para la propiedad RecordType. Para obtener información sobre otras propiedades, vea [Propiedades detalladas del registro de auditoría de Office 365](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Detalles de auditoría](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exportar los resultados de la búsqueda

Para exportar el registro de auditoría de Power BI a un archivo .csv, siga estos pasos.

1. Seleccione **Exportar resultados**.

1. Seleccione **Save loaded results** (Guardar resultados cargados) o **Download all results** (Descargar todos los resultados).

    ![Exportar resultados](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Uso de PowerShell para buscar registros de auditoría

También puede usar PowerShell para acceder a los registros de auditoría mediante el inicio de sesión. El ejemplo siguiente muestra cómo usar el comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) para extraer las entradas de registro de auditoría de Power BI.

Para usar el comando [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession/), su cuenta debe tener una licencia de Exchange Online asignada y necesita tener acceso al registro de auditoría para el inquilino. Para más información sobre cómo conectarse a Exchange Online, vea [Conectarse a Exchange Online mediante PowerShell remoto](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Para consultar otro ejemplo del uso de PowerShell con los registros de auditoría, vea [Using Power BI audit log and PowerShell to assign Power BI Pro licenses](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) (Uso del registro de auditoría de Power BI y PowerShell para asignar licencias de Power BI Pro).

## <a name="activities-audited-by-power-bi"></a>Actividades auditadas por Power BI

A continuación, se indican las actividades auditadas por Power BI.

* AddDatasourceToGateway
* AddGroupMembers
* AnalyzedByExternalApplication
* AnalyzeInExcel
* AttachDataflowStorageAccount
* BindToGateway
* ChangeCapacityState
* ChangeGatewayAdministrators
* ChangeGatewayDatasourceUsers
* CreateApp
* CreateDashboard
* CreateDataflow
* CreateDataset
* CreateEmailSubscription
* CreateFolder
* CreateGateway
* CreateGroup
* CreateOrgApp
* CreateReport
* DeleteComment
* DeleteDashboard
* DeleteDataflow
* DeleteDataset
* DeleteEmailSubscription
* DeleteFolder
* DeleteGateway
* DeleteGroup
* DeleteGroupMembers
* DeleteOrgApp
* DeleteReport
* DownloadReport
* EditDataset
* EditReport
* ExportDataflow
* ExportReport
* ExportTile
* GenerateDataflowSasToken
* GenerateEmbedToken
* GetDatasources
* Importar
* InstallApp
* MigrateWorkspaceIntoCapacity
* OptInForProTrial
* PostComment
* PrintDashboard
* PrintReport
* PublishToWebReport
* RefreshDataset
* RemoveDatasourceFromGateway
* RemoveWorkspacesFromCapacity
* RenameDashboard
* SetAllConnections
* SetScheduledRefresh
* SetScheduledRefreshOnDataflow
* ShareDashboard
* ShareReport
* TakeOverDataset
* TakeOverDatasource
* UnpublishApp
* UpdateApp
* UpdateCapacityAdmins
* UpdateCapacityDisplayName
* UpdateCapacityResourceGovernanceSettings
* UpdateCapacityUsersAssignment
* UpdatedAdminFeatureSwitch
* UpdateDataflow
* UpdateDatasetParameters
* UpdateDatasourceCredentials
* UpdateDatasources
* UpdateEmailSubscription
* UpdateFolder
* UpdateFolderAccess
* ViewDashboard
* ViewDataflow
* ViewReport
* ViewTile
* ViewUsageMetrics

## <a name="next-steps"></a>Pasos siguientes

[¿Qué es la administración de Power BI?](service-admin-administering-power-bi-in-your-organization.md)  

[Portal de administración de Power BI](service-admin-portal.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
