---
title: Portal de administración de Power BI
description: El portal de administración permite la administración de inquilinos de Power BI en su organización. Incluye elementos como métricas de uso, acceso al Centro de administración de Microsoft 365 y configuración.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: c59f1c1653e3b1a506f342bffed6fa539dfe58b3
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76819592"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Administración de Power BI en el portal de administración

El portal de administración le permite administrar un *inquilino* de Power BI de su organización. El portal incluye elementos como métricas de uso, acceso al Centro de administración de Microsoft 365 y configuración.

El portal de administración completo es accesible para todos los usuarios que sean administradores globales de Office 365 o a los que se les haya asignado el rol de administrador del servicio Power BI. Si no está en uno de estos roles, solo verá **Configuración de la capacidad** en el portal. Para más información acerca del rol de administrador del servicio Power BI, consulte [Descripción del rol de administrador de Power BI](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Acceso al portal de administración

La cuenta debe estar marcada como **Administrador global** en Office 365 o Azure Active Directory (Azure AD) o tener asignado el rol Administrador del servicio Power BI para acceder al portal de administración de Power BI. Para más información acerca del rol de administrador del servicio Power BI, consulte [Descripción del rol de administrador de Power BI](service-admin-role.md). Para acceder al portal de administración de Power BI, haga lo siguiente.

1. Seleccione el engranaje de configuración en la parte superior derecha del servicio Power BI.

1. Seleccione **Portal de administración**.

    ![Configuración del portal de administración](media/service-admin-portal/powerbi-admin-settings.png)

Hay nueve pestañas en el portal. En el resto de este artículo se proporciona información sobre cada una de ellas.

![Navegación en el portal de administración](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Métricas de uso](#usage-metrics)
* [Usuarios](#users)
* [Registros de auditoría](#audit-logs)
* [Configuración de inquilinos](#tenant-settings)
* [Configuración de capacidad](#capacity-settings)
* [Códigos para insertar](#embed-codes)
* [Objetos visuales de la organización](#organizational-visuals)
* [Almacenamiento de flujos de datos (versión preliminar)](#dataflowStorage)
* [Áreas de trabajo](#workspaces)
* [Personalización de marca](#custom-branding)

## <a name="usage-metrics"></a>Métricas de uso

La pestaña **Métricas de uso** le permiten supervisar el uso de Power BI de su organización. También proporciona la capacidad para ver qué usuarios y grupos, son los más activos en Power BI para su organización. 

> [!NOTE]
> La primera vez que accede al panel, o después de visitarlo de nuevo tras un largo período sin verlo, probablemente verá una pantalla de carga mientras se carga el panel.

Una vez cargado el panel, verá dos secciones de iconos. La primera sección incluye datos de uso para usuarios individuales y la segunda sección muestra información similar para los grupos de su organización.

Este es un desglose de lo que puede ver en cada icono:

* Recuento definido de todos los paneles, informes y conjuntos de datos en el área de trabajo de usuario.
  
    ![Recuento diferente de paneles, informes y conjuntos de datos.](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* El panel más consumido por número de usuarios que pueden acceder a él. Por ejemplo, si tiene un panel que ha compartido con tres usuarios y también lo agrega a un paquete de contenido al que están conectados dos usuarios distintos, su recuento sería 6 (1 + 3 + 2).
  
    ![Más paneles consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* El contenido más popular al que están conectados los usuarios. Esto sería cualquier cosa que los usuarios puedan alcanzar a través del proceso de obtención de datos: paquetes SaaS, paquetes de contenido organizativo, archivos o bases de datos.
  
    ![Más paquetes consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Una vista de los usuarios principales según el número de paneles que tienen, tanto paneles que crearon ellos mismos como paneles compartidos con ellos.
  
    ![Usuarios principales: paneles](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Una vista de los usuarios principales según el número de informes que tienen.
  
    ![Usuarios principales: informes](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

La segunda sección muestra el mismo tipo de información, pero se basa en grupos. Esto le permite ver qué grupos de la organización son más activos y qué tipo de contenido consumen.

Con esta información, puede obtener información real sobre cómo las personas usan Power BI en toda la organización y puede reconocer esos usuarios y grupos que son muy activos en su organización.

## <a name="control-usage-metrics"></a>Control de métricas de uso

Los informes de métricas de uso son una característica que el administrador de Power BI u Office 365 puede activar o desactivar. Los administradores tienen control granular sobre qué usuarios tienen acceso a las métricas de uso. De forma predeterminada, todos los usuarios de la organización tienen esta opción en modo **Activado**.

Los administradores también pueden determinar si los creadores de contenido pueden ver los datos de cada usuario en las métricas de uso. 

Consulte [Supervisar las métricas de uso de paneles e informes de Power BI](service-usage-metrics.md) para obtener más información acerca de los informes.

### <a name="usage-metrics-for-content-creators"></a>Métricas de uso para creadores de contenido

1. En el portal de administración, seleccione **Configuración de inquilino** > **Métricas de uso para los creadores de contenido**.

    ![Métricas de uso de la configuración de inquilino del portal de administración](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. Habilite (o deshabilite) las métricas de uso > **Aplicar**.

    ![Métricas de uso habilitadas](media/service-usage-metrics/power-bi-tenant-settings-updated.png)


### <a name="per-user-data-in-usage-metrics"></a>Datos de cada usuario en las métricas de uso

Los datos por usuario están habilitados de forma predeterminada en las métricas de uso, mientras que el informe de métricas incluye información sobre la cuenta del consumidor de contenido. Si prefiere no incluir esta información de algunos los usuarios, incluso de ninguno de ellos, deshabilite la característica para los grupos de seguridad en cuestión o para toda la organización. En tal caso, la información de la cuenta aparece en el informe como *Sin nombre*.

![Datos de uso de cada usuario](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>Eliminación de todo el contenido existente de las métricas de uso

Al deshabilitar las métricas de uso para toda la organización, los administradores pueden utilizar una de estas opciones, o ambas:

- **Elimine todo el contenido existente de las métricas de uso** para eliminar todos los iconos de informes y paneles existentes que se compilaron mediante los informes y conjuntos de datos de las métricas de uso. Esta opción permite eliminar todos los accesos a los datos de métricas de uso de todos los usuarios de la organización que ya los puedan estar usando. 
- **Eliminar todos los datos por usuario existentes del contenido de las métricas de uso actuales** Esta opción elimina todo el acceso a los datos por usuario para todos los usuarios de la organización que ya lo estén utilizando. 

Tenga cuidado, ya que la eliminación del contenido de las métricas de uso y por usuario existentes es irreversible.

## <a name="users"></a>Usuarios

Administra usuarios, grupos y administradores de Power BI en el Centro de administración de Microsoft 365. La pestaña **Usuarios** proporciona un vínculo al centro de administración del inquilino.

![Ir al Centro de administración de Microsoft 365](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Registros de auditoría

Administrará registros de auditoría de Power BI en el Centro de seguridad y cumplimiento de Office 365. La pestaña **Registros de auditoría** proporciona un vínculo al Centro de seguridad y cumplimiento del inquilino. [Más información](service-admin-auditing.md)

Para usar los registros de auditoría, asegúrese de que la opción [**Crear registros de auditoría para el cumplimiento y la auditoría de la actividad interna**](#create-audit-logs-for-internal-activity-auditing-and-compliance) está habilitada.

## <a name="tenant-settings"></a>Configuración de inquilinos

La pestaña **Configuración de inquilinos** permite controlar de manera pormenorizada las características que están disponibles para su organización. Si le preocupa la información confidencial, algunas de nuestras características pueden no ser adecuadas para su organización, o puede que solo quiera que una determinada característica esté disponible para un grupo concreto.

En la imagen siguiente se muestran varias opciones de la pestaña **Configuración de inquilinos**.

![Configuración de inquilinos](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> La configuración puede tardar hasta 10 minutos en aplicarse para todos los usuarios del inquilino.

La configuración puede tener tres estados:

* **Deshabilitado para toda la organización**: ninguna persona de la organización puede usar esta característica.

    ![Opción de deshabilitar para todos](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Habilitado para toda la organización**: todas las personas de la organización pueden usar esta característica.

    ![Opción de habilitar para todos](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Habilitado para un subconjunto de la organización**: un subconjunto específico de usuarios o grupos de la organización puede usar esta característica.

    Puede habilitar la característica para toda la organización, menos para un grupo de usuarios específico.

    ![Opción de habilitar para un subconjunto](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    Puede habilitar también la característica solo para un grupo específico de usuarios y deshabilitarla para determinados usuarios de ese grupo. El uso de este enfoque garantiza que determinados usuarios no tengan acceso a la característica incluso aunque pertenezcan al grupo permitido.

    ![Opción de habilitar con excepciones](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

Las secciones siguientes proporcionan una visión general de los distintos tipos de configuración de inquilino.

## <a name="help-and-support-settings"></a>Configuración de ayuda y soporte técnico

### <a name="publish-get-help-information"></a>Publicar información "Obtener ayuda"

Los usuarios de la organización pueden obtener acceso a recursos de ayuda y soporte técnico internos desde el menú Ayuda de Power BI. Concretamente, estos parámetros cambian el comportamiento de los elementos de menú Saber más, Comunidad y Obtener ayuda.

Además, al especificar una dirección URL para las solicitudes de licencia, puede personalizar la dirección URL de destino del botón **Actualización de cuenta**. Los usuarios que no tengan una licencia de Power BI Pro verán este botón en el cuadro de diálogo **Actualizar a Power BI Pro**, así como en la página **Administrar almacenamiento personal**. Además, Power BI ya no ofrece el botón **Probar Pro gratis** en este cuadro de diálogo ni en la página de almacenamiento. Esto garantiza que Power BI guiará a los usuarios de forma confiable por los procesos definidos en la organización en la solución de administración de licencias.

![Opción de habilitar con excepciones](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>Recepción de notificaciones por correo electrónico sobre interrupciones o incidentes en el servicio

Los grupos de seguridad habilitados para correo recibirán notificaciones por correo electrónico si este inquilino se ve afectado por una interrupción del servicio o un incidente. Más información sobre [Notificaciones de interrupción del servicio](service-interruption-notifications.md).

## <a name="workspace-settings"></a>Configuración del área de trabajo

### <a name="create-workspaces"></a>Crear áreas de trabajo

Los administradores usan la configuración **Crear áreas de trabajo** para indicar qué usuarios de la organización pueden crear áreas de trabajo para colaborar en paneles, informes y otro contenido. Obtenga más información sobre las [áreas de trabajo](service-create-the-new-workspaces.md).

El portal de administración tiene otra sección de configuración sobre las áreas de trabajo del inquilino. En esa sección, puede ordenar y filtrar la lista de áreas de trabajo y mostrar los detalles de cada una de ellas. Consulte [Áreas de trabajo](#workspaces) para obtener detalles.

En el portal de administración, también controla qué usuarios tienen permisos para distribuir aplicaciones a la organización. Consulte [Publicación de paquetes de contenido y aplicaciones en toda la organización](#publish-content-packs-and-apps-to-the-entire-organization) en este artículo para obtener detalles.

## <a name="export-and-sharing-settings"></a>Configuración de exportación y uso compartido

### <a name="share-content-with-external-users"></a>Compartir contenido con usuarios externos

Los usuarios de la organización pueden compartir paneles, informes y aplicaciones con usuarios ajenos a la organización. Obtenga más información sobre el [uso compartido externo](service-share-dashboards.md#share-a-dashboard-or-report-outside-your-organization).

![Opción de usuarios externos](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

En la imagen siguiente se muestra el mensaje que aparece al compartir con un usuario externo.

![Compartir con usuarios externos](media/service-admin-portal/powerbi-admin-sharing-external.png)  

> [!IMPORTANT]
> Esta opción controla si los usuarios de Power BI pueden invitar a usuarios externos a convertirse en usuarios invitados de Azure Active Directory B2B (Azure AD B2B) en la organización a través de Power BI. Si se habilita, los usuarios que tienen el rol de invitador de usuarios invitados en Azure AD pueden agregar direcciones de correo electrónico externas al compartir informes, paneles y aplicaciones de Power BI. El destinatario externo es invitado a unirse a su organización como usuario invitado de Azure AD B2B. Lo importante es que, al deshabilitar esta opción, los usuarios externos que ya sean usuarios invitados de Azure AD B2B en la organización seguirán apareciendo en las interfaces de usuario del selector de personas de Power BI y se les puede conceder acceso a elementos, áreas de trabajo y aplicaciones.

### <a name="publish-to-web"></a>Publicar en Web

Los usuarios de la organización pueden publicar informes en la web. [Más información](service-publish-to-web.md). Esto hace que el informe y los datos que contiene estén disponibles para cualquier persona en la web.

> [!NOTE]
> Un administrador de Power BI debe permitir la creación de nuevos códigos para insertar de publicación en web. Las organizaciones pueden tener códigos para insertar existentes. Use la página de [códigos para insertar](service-admin-portal.md#embed-codes) para revisar los informes publicados actualmente.

En la imagen siguiente se muestra el menú **Archivo** de un informe cuando está habilitada la opción **Publicar en la web**.

![Publicación en web en el menú Archivo](media/service-admin-portal/powerbi-admin-publish-to-web.png)

La configuración **Publicar en la web** proporciona opciones para las que los usuarios pueden crear códigos para insertar.

![Opción de publicación en la web](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)


Se pide a los usuarios que se pongan en contacto con el administrador de Power BI para permitirles crear un código para insertar cuando la opción **Elegir cómo funcionan los códigos para insertar** está establecida en **Allow only existing embed codes** (Permitir solo los códigos para insertar existentes) y la opción **Publicar en la web** está **Habilitada**.

![Mensaje de Publicar en la web](media/service-publish-to-web/publish_to_web_admin_prompt.png)


Los usuarios ven diferentes opciones en la interfaz de usuario en función del valor de la opción **Publicar en la web**.

|Característica |Habilitada para toda la organización |Deshabilitada para toda la organización |Grupos de seguridad específicos   |
|---------|---------|---------|---------|
|**Publicar en la web** en el menú **Archivo**.|Habilitada para todos|No visible para todos|Solo visible para usuarios o grupos autorizados.|
|**Administrar códigos para insertar** en **Configuración**|Habilitada para todos|Habilitada para todos|Habilitada para todos<br><br>Opción * **Eliminar** solo para usuarios o grupos autorizados.<br>* **Obtener código** habilitada para todos.|
|**Códigos de inserción** en el portal de administración|El estado refleja uno de los siguientes:<br>* Activo<br>* No admitido<br>* Bloqueado|El estado muestra **Deshabilitado**.|El estado refleja uno de los siguientes:<br>* Activo<br>* No admitido<br>* Bloqueado<br><br>Si el usuario no está autorizado según la configuración del inquilino, el estado muestra **Infracción**.|
|Informes publicados existentes|Todos habilitados|Todos deshabilitados|Los informes continúan generándose para todos.|

### <a name="export-data"></a>Exportar datos

Los usuarios de la organización pueden exportar datos desde un icono o una visualización. [Más información](visuals/power-bi-visualization-export-data.md)

En la imagen siguiente se muestra la opción para exportar datos desde un icono.

![Exportación de datos desde un icono](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Si deshabilita la opción **Exportar datos** también impedirá que los usuarios usen la característica **Analizar en Excel**, así como la conexión dinámica al servicio Power BI.

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Exportación de informes como presentaciones de PowerPoint o documentos PDF

Los usuarios de la organización pueden exportar informes de Power BI como archivos de PowerPoint o documentos PDF. [Más información](consumer/end-user-powerpoint.md)

En la imagen siguiente se muestra el menú **Archivo** para un informe cuando está habilitada la opción **Exportar informes como presentaciones de PowerPoint o documentos PDF**.

![Exportar informes como presentaciones de PowerPoint](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Imprimir paneles e informes

Los usuarios de la organización pueden imprimir paneles e informes. [Más información](consumer/end-user-print.md)

En la imagen siguiente se muestra la opción para imprimir un panel.

![Imprimir panel](media/service-admin-portal/powerbi-admin-print-dashboard.png)

En la imagen siguiente se muestra el menú **Archivo** de un informe cuando está habilitada la opción **Imprimir paneles e informes**.

![Imprimir informe](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Permitir a los usuarios externos editar y administrar el contenido de la organización

Los usuarios invitados de Azure AD B2B pueden editar y administrar el contenido de la organización. [Más información](service-admin-azure-ad-b2b.md)

La imagen siguiente muestra la opción Permitir a los usuarios externos editar y administrar el contenido de la organización.

![Permitir a los usuarios externos editar y administrar el contenido de la organización](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

En el portal de administración, también se controla qué usuarios tienen permisos para invitar a usuarios externos a la organización. Consulte [Compartir contenido con usuarios externos](#export-and-sharing-settings) en este artículo para obtener más información.

### <a name="email-subscriptions"></a>Suscripciones de correo electrónico
Los usuarios de la organización pueden crear suscripciones de correo electrónico. Obtenga más información sobre las [suscripciones](service-report-subscribe.md).

![Habilitar suscripciones de correo electrónico](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

## <a name="content-pack-and-app-settings"></a>Configuración de paquetes de contenido y de aplicaciones

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Publicación de paquetes de contenido y aplicaciones en toda la organización

Los administradores usan esta configuración para decidir qué usuarios pueden publicar paquetes de contenido y aplicaciones en toda la organización, en lugar de solo en grupos específicos. Obtenga más información sobre cómo [publicar aplicaciones](service-create-distribute-apps.md).

La siguiente imagen muestra la opción **Toda mi organización** al crear un paquete de contenido.

![Publicar el paquete de contenido en la organización](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Crear paquetes de contenido organizativos y aplicaciones de plantilla

Los usuarios de la organización pueden crear paquetes de contenido organizativos y aplicaciones de plantilla que utilizan conjuntos de datos integrados en un origen de datos de Power BI Desktop. Obtenga más información sobre las [aplicaciones de plantilla](template-content-pack-authoring.md).

### <a name="push-apps-to-end-users"></a>Insertar aplicaciones para los usuarios finales

Los creadores de informes pueden compartir aplicaciones directamente con los usuarios finales sin requerir la instalación desde [AppSource](https://appsource.microsoft.com). Obtenga más información sobre cómo [instalar aplicaciones automáticamente para los usuarios finales](service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Configuración de integración

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Usar la función Analizar en Excel en los conjuntos de datos locales

Los usuarios de la organización pueden utilizar Excel para ver e interactuar con conjuntos de datos locales de Power BI. [Más información](service-analyze-in-excel.md)

> [!NOTE]
> Si deshabilita la opción **Exportar datos** también impide que los usuarios usen la característica **Analizar en Excel**.

### <a name="use-arcgis-maps-for-power-bi"></a>Usar ArcGIS Maps for Power BI

Los usuarios de la organización pueden usar la visualización de ArcGIS Maps for Power BI proporcionada por Esri. [Más información](visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Usar la búsqueda global para Power BI (versión preliminar)

Los usuarios de la organización pueden usar características de búsqueda externa que se basan en Azure Search.

## <a name="custom-visuals-settings"></a>Configuración de objetos visuales personalizados

### <a name="add-and-use-custom-visuals"></a>Incorporación y uso de objetos visuales personalizados

Los usuarios de la organización pueden interactuar con objetos visuales personalizados y compartirlos. [Más información](developer/power-bi-custom-visuals.md)

> [!NOTE]
> Esta configuración se puede aplicar en toda la organización o puede limitarse a grupos específicos.


Power BI Desktop (a partir de la versión de marzo de 2019) admite el uso de **Directiva de grupo** para deshabilitar el uso de objetos visuales personalizados en los equipos implementados de una organización.

<table>
<tr><th>Atributo</th><th>Valor</th>
</tr>
<td>key</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

Un valor de 1 (decimal) permite el uso de objetos visuales personalizados en Power BI (este es el valor predeterminado).

Un valor de 0 (decimal) no permite el uso de objetos visuales personalizados en Power BI.

### <a name="allow-only-certified-visuals"></a>Permitir solo objetos visuales certificados

Los usuarios de la organización a los que se han concedido permisos para agregar y usar objetos visuales personalizados (lo que se indica mediante la configuración "Agregar y usar objetos visuales personalizados") solo podrán usar [objetos visuales personalizados certificados](https://go.microsoft.com/fwlink/?linkid=2002010). Los objetos visuales no certificados se bloquearán y se mostrará un mensaje de error cuando se usen. 


Power BI Desktop (a partir de la versión de marzo de 2019) admite el uso de **Directiva de grupo** para deshabilitar el uso de objetos visuales personalizados sin certificar en los equipos implementados de una organización.

<table>
<tr><th>Atributo</th><th>Valor</th>
</tr>
<td>key</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

Un valor de 1 (decimal) permite el uso de objetos visuales personalizados sin certificar en Power BI (este es el valor predeterminado).

Un valor de 0 (decimal) no permite el uso de objetos visuales personalizados sin certificar en Power BI (esta opción solo permite el uso de [objetos visuales personalizados certificados](https://go.microsoft.com/fwlink/?linkid=2002010)).

## <a name="r-visuals-settings"></a>Configuración de objetos visuales de R

### <a name="interact-with-and-share-r-visuals"></a>Compartir objetos visuales de R e interactuar con ellos

Los usuarios de la organización pueden interactuar con objetos visuales creados mediante scripts de R y compartirlos. [Más información](visuals/service-r-visuals.md)

> [!NOTE]
> Esta configuración se aplica a toda la organización y no se puede limitar a grupos específicos.

## <a name="audit-and-usage-settings"></a>Configuración de auditoría y uso

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Crear registros de auditoría con fines de auditoría y cumplimiento de la actividad interna

Los usuarios de la organización pueden utilizar la auditoría para supervisar las acciones realizadas en Power BI por otros usuarios de la organización. [Más información](service-admin-auditing.md)

Se debe habilitar esta configuración para que las entradas de registro de auditoría se puedan registrar. Puede haber una demora de hasta 48 horas entre la habilitación de la auditoría y el momento en el que se empiecen a mostrar los datos de auditoría. Si no ve los datos de inmediato, consulte los registros de auditoría más tarde. Puede haber una demora similar entre la obtención de permisos para ver los registros de auditoría y la posibilidad de acceder a estos.

> [!NOTE]
> Esta configuración se aplica a toda la organización y no se puede limitar a grupos específicos.

### <a name="usage-metrics-for-content-creators"></a>Métricas de uso para creadores de contenido

Los usuarios de la organización pueden consultar las métricas de uso de los paneles y los informes que hayan creado. [Más información](service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Datos por usuario en métricas de uso de creadores de contenido

Las métricas de uso de creadores de contenido revelan los nombres para mostrar y las direcciones de correo electrónico de los usuarios que acceden al contenido. [Más información](service-usage-metrics.md)

Los datos por usuario están habilitados de forma predeterminada en las métricas de uso, mientras que el informe de métricas incluye información sobre la cuenta del creador de contenido. Si no desea recopilar esta información para todos los usuarios, puede deshabilitar la característica para los grupos de seguridad en cuestión o para toda la organización. En tal caso, la información de la cuenta de los usuarios excluidos aparecerá en el informe como *Sin nombre*.

## <a name="dashboard-settings"></a>Configuración del panel

### <a name="data-classification-for-dashboards"></a>Clasificación de datos para paneles

Los usuarios de la organización pueden etiquetar paneles con clasificaciones que indiquen los niveles de seguridad del panel. [Más información](service-data-classification.md)

> [!NOTE]
> Esta configuración se aplica a toda la organización y no se puede limitar a grupos específicos.

## <a name="developer-settings"></a>Configuración de desarrollador

### <a name="embed-content-in-apps"></a>Insertar contenido en aplicaciones

Los usuarios de la organización pueden insertar informes y paneles de Power BI en las aplicaciones de software como servicio (SaaS). Si deshabilita esta configuración, impide que los usuarios puedan usar las API REST para insertar contenido de Power BI en la aplicación. [Más información](developer/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Concesión de permisos a las entidades de servicio para utilizar las API de Power BI

Las aplicaciones web registradas en Azure Active Directory (Azure AD) usarán una entidad de servicio asignada para acceder a API de Power BI sin un usuario con sesión iniciada. Para permitir que una aplicación use la autenticación de entidad de servicio, su entidad de servicio debe estar incluida en un grupo de seguridad permitido. [Más información](developer/embed-service-principal.md)

> [!NOTE]
> Las entidades de servicio heredan de su grupo de seguridad los permisos correspondientes a todas las opciones de configuración del inquilino de Power BI. Para limitar los permisos, cree un grupo de seguridad dedicado para las entidades de servicio y agréguelo a la lista "Excepto grupos de seguridad específicos" correspondiente a la configuración habilitada y pertinente de Power BI.

## <a name="dataflow-settings"></a>Configuración de flujo de datos

### <a name="create-and-use-dataflows"></a>Creación y uso de flujos de datos

Los usuarios de la organización pueden crear y usar flujos de datos. Para obtener información general sobre flujos de datos, consulte [Preparación de datos de autoservicio en Power BI](service-dataflows-overview.md). Para habilitar flujos de datos en una capacidad Premium, vea [Configuración de las cargas de trabajo](service-admin-premium-workloads.md).

> [!NOTE]
> Esta configuración se aplica a toda la organización y no se puede limitar a grupos específicos.

## <a name="template-apps-settings"></a>Configuración de aplicaciones de plantilla

Tres valores de configuración controlan la capacidad de las aplicaciones de plantilla de publicar o instalar aplicaciones de plantilla.

![Configuración de aplicaciones de plantilla del portal de administración de Power BI](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>Publicar aplicaciones de plantilla

Los usuarios de la organización pueden crear áreas de trabajo de aplicaciones de plantilla. Controle qué usuarios pueden publicar aplicaciones de plantilla o distribuirlas a clientes fuera de la organización mediante [AppSource](https://appsource.microsoft.com) u otros métodos de distribución.

![Portal de administración de Power BI, opción Crear aplicaciones de plantilla](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>Instalar aplicaciones de plantilla que aparecen en AppSource

Los usuarios de la organización pueden descargar e instalar aplicaciones de plantilla **solo** desde [AppSource](https://appsource.microsoft.com). Controle qué usuarios o grupos de seguridad específicos pueden instalar aplicaciones de plantilla desde AppSource.

![Portal de administración de Power BI, opción Instalar aplicaciones de plantilla](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>Instalar aplicaciones de plantilla que no aparecen en AppSource

Controle qué usuarios de la organización pueden descargar e instalar aplicaciones de plantilla **que no aparecen en [AppSource](https://appsource.microsoft.com)** .

![Portal de administración de Power BI, opción Instalar aplicaciones de plantilla](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>Configuración de la capacidad

### <a name="power-bi-premium"></a>Power BI Premium

La pestaña **Power BI Premium** le permite administrar las funcionalidades de Power BI Premium (SKU EM o P) que se han adquirido para su organización. Todos los usuarios de su organización pueden ver la pestaña **Power BI Premium**, pero solo ven lo que contiene si están asignados como *administrador de funcionalidades* o como un usuario con permisos de asignación. Si un usuario no tiene ningún permiso, aparecerá el mensaje siguiente.

![No hay acceso a la configuración de Premium](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

La pestaña **Power BI Embedded** le permite ver sus funcionalidades de Power BI Embedded (SKU A) que ha adquirido para su cliente. Dado que solo puede adquirir SKU A de Azure, puede [administrar las funcionalidades insertadas en Azure](developer/azure-pbie-create-capacity.md) desde **Azure Portal**.

Para más información sobre cómo administrar la configuración de Power BI Embedded (SKU A), consulte [¿Qué es Power BI Embedded?](developer/azure-pbie-what-is-power-bi-embedded.md).

## <a name="embed-codes"></a>Códigos para insertar

Como administrador, puede ver los códigos para insertar que se generan para su inquilino para compartir informes de forma pública. También puede revocar o eliminar códigos. [Más información](service-publish-to-web.md)

![Códigos para insertar en el portal de administración de Power BI](media/service-admin-portal/embed-codes.png)

 ## <a name="organizational-visuals">Objetos visuales de la organización</a> 

La pestaña **Objetos visuales de la organización** le permite implementar y administrar los objetos visuales personalizados dentro de la organización. Con objetos visuales de la organización, puede implementar fácilmente objetos visuales propietarios en su organización, que los autores de informes pueden detectar e importar después en sus informes de Power BI Desktop. [Más información](developer/power-bi-custom-visuals-organization.md)

> [!WARNING]
> Un objeto visual personalizado podría contener código con riesgos para la seguridad o la privacidad; asegúrese de que confía en el autor y del origen del objeto visual personalizado antes de implementar en el repositorio de la organización.

En la imagen siguiente se muestran todos los objetos visuales personalizados que están implementados actualmente en un repositorio de la organización.

![Objeto visual de administrador de organización](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>Adición de un nuevo objeto visual personalizado

Para agregar un nuevo objeto visual personalizado a la lista, siga estos pasos. 

1. En el panel derecho, seleccione **Agregar objeto visual personalizado**.

    ![Formulario de objetos visuales personalizados](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. Rellene el formulario **Agregar objeto visual personalizado**:

    * **Elija un archivo .pbiviz** (obligatorio): seleccione un archivo visual personalizado para cargar. Se admiten solo objetos visuales de API con control de versiones (lea aquí lo que esto significa).

    Antes de cargar un objeto visual personalizado, debe revisar la seguridad y privacidad de dicho objeto visual para asegurarse de que se ajusta a los estándares de su organización.

    * **Asigne un nombre a los objetos visuales personalizados** (obligatorio): asigne un título corto al objeto visual para que los usuarios de Power BI Desktop sepan fácilmente para qué sirve.

    * **Icono**: El archivo de icono que se muestra en la interfaz de usuario de Power BI Desktop.

    * **Descripción**: una descripción breve del objeto visual para proporcionar más contexto e información al usuario.

1. Seleccione **Agregar** para iniciar la solicitud de carga. Si se realiza correctamente, verá el nuevo elemento en la lista. Si el proceso no se completa, recibirá el mensaje de error pertinente.

### <a name="delete-a-custom-visual-from-the-list"></a>Eliminación de un objeto visual personalizado de la lista

Para eliminar de forma permanente un objeto visual, seleccione el icono de la Papelera de reciclaje para el objeto visual en el repositorio.

> [!IMPORTANT]
> La eliminación es irreversible. Una vez eliminado, el objeto visual deja de representarse de inmediato en los informes existentes. Aunque se cargue el mismo objeto visual de nuevo, no reemplazará al anterior que se eliminó. Sin embargo, los usuarios pueden volver a importar el nuevo objeto visual y reemplazar la instancia que tienen en los informes.

### <a name="disable-a-custom-visual-in-the-list"></a>Deshabilitación de un objeto visual personalizado en la lista

Para deshabilitar el objeto visual desde la tienda de la organización, seleccione el icono de engranaje. En la sección **Acceso**, deshabilite el objeto visual personalizado.

Después de deshabilitar el objeto visual, ya no se representa en los informes existentes y se muestra el mensaje de error siguiente.

*This custom visual is no longer available (Este objeto visual personalizado ya no está disponible). Please contact your administrator for details* (Póngase en contacto con su administrador para más información).

Sin embargo, los objetos visuales guardados como marcador siguen funcionando.

Después de una actualización o un cambio por el administrador, los usuarios de Power BI Desktop deben reiniciar la aplicación o actualizar el explorador en el servicio Power BI para ver las actualizaciones.

### <a name="update-a-visual"></a>Actualización de un objeto visual

Para actualizar el objeto visual desde la tienda de la organización, seleccione el icono de engranaje. Examine y cargue una nueva versión del objeto visual.

Asegúrese de que el identificador del objeto visual no cambie. El archivo nuevo reemplaza al archivo anterior en todos los informes de la organización. Sin embargo, si la versión nueva del objeto visual puede generar errores en el uso o la estructura de datos de la versión anterior del objeto visual, no reemplace la versión anterior. En lugar de eso, debe crear una nueva lista para la versión nueva del objeto visual. Por ejemplo, agregue un número de versión nuevo (versión X.X) al título del objeto visual nuevo. De este modo, resulta claro que es el mismo objeto visual solo con un número de versión actualizado, por lo que los informes existentes no interrumpen su funcionalidad. Vuelva a asegurarse de que el identificador del objeto visual no cambie. Luego, la próxima vez que los usuarios entren en el repositorio de la organización desde Power BI Desktop, pueden importar la versión nueva, donde se les pide que reemplacen la versión actual que tienen en el informe.

Para obtener más información, visite las [preguntas más frecuentes sobre objetos visuales personalizados de organización](/power-bi/developer/power-bi-custom-visuals-faq#organizational-power-bi-visuals).

## <a name="dataflowStorage">Almacenamiento de flujos de datos (versión preliminar)</a>

De forma predeterminada, los datos usados con Power BI se almacenan en almacenamiento interno proporcionado por Power BI. Con la integración de flujos de datos y Azure Data Lake Storage Gen2 (ADLS Gen2), puede almacenar los flujos de datos en la cuenta de Azure Data Lake Storage Gen2 de su organización. Para obtener más información, vea [Integración de flujos de datos y Azure Data Lake (versión preliminar)](service-dataflows-azure-data-lake-integration.md).

## <a name="workspaces"></a>Áreas de trabajo

Como administrador, puede ver las áreas de trabajo que existen en el inquilino. Puede ordenar y filtrar la lista de áreas de trabajo y mostrar los detalles de cada una de ellas. Las columnas de la tabla se corresponden con las propiedades devueltas por la [API de REST de administración de Power BI](/rest/api/power-bi/admin) para las áreas de trabajo. Las áreas de trabajo personales son de tipo **PersonalGroup**, las clásicas son de tipo **Group** y las áreas de trabajo de la nueva experiencia de áreas de trabajo son de tipo **Workspace**. Para obtener más información, consulte [Crear nuevas áreas de trabajo en Power BI](service-create-the-new-workspaces.md).

![Lista de áreas de trabajo](media/service-admin-portal/workspaces-list.png)

En la pestaña **Áreas de trabajo**, verá el *estado* para cada área de trabajo. En la tabla siguiente se proporcionan más detalles sobre el significado de estos estados.

|Estado  |Descripción  |
|---------|---------|
| Activo | Un área de trabajo normal. No indica nada sobre el uso o lo que hay en el interior, solo que el área de trabajo es "normal". |
| Huérfana | Un área de trabajo sin usuario administrador. |
| Eliminada | Un área de trabajo eliminada. Se conservan suficientes metadatos para restaurar el área de trabajo, si se quiere. |
| Quitando | Un área de trabajo en proceso de eliminación, pero aún no ha desaparecido. Los usuarios pueden eliminar sus propias áreas de trabajo, que se sitúan en estado Quitando y, con el tiempo, en Eliminada. |

## <a name="custom-branding"></a>Personalización de marca

Como administrador, puede personalizar la apariencia de Power BI para toda la organización. Actualmente, hay tres opciones principales:

![Opciones de personalización de marca](media/service-admin-portal/power-bi-custom-branding.png)

* **Carga del logotipo**: para obtener los mejores resultados, cargue un logotipo guardado en formato .png de 10 KB o menos y de al menos 200 x 30 píxeles.

* **Carga de la imagen de portada**: para obtener los mejores resultados, cargue una imagen de portada guardada en formato .jpg o .png de 1 MB o menos y de al menos 1920 x 160 píxeles.

* **Selección del color de tema**: puede seleccionar su tema basado en un número hexadecimal, RGB, valor o desde la paleta que se proporciona.


Para más información, consulte [Personalización de marca de la organización](https://aka.ms/orgBranding).

![Lista de áreas de trabajo](media/service-admin-portal/workspaces-list.png)
## <a name="next-steps"></a>Pasos siguientes

[Administración de Power BI en su organización](service-admin-administering-power-bi-in-your-organization.md)  
[Descripción del rol de administrador de Power BI](service-admin-role.md)  
[Auditoría de Power BI en su organización](service-admin-auditing.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
