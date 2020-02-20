---
title: Guía para la configuración de la administración de inquilinos
description: Guía para la configuración de inquilinos de Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: v-pemyer
ms.openlocfilehash: f9832948fdd25d1bd807e0ff5d916b08b55aea95
ms.sourcegitcommit: e27d40054949421701f829113c4a5f6d260c8d5f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2020
ms.locfileid: "77155028"
---
# <a name="tenant-admin-settings-guidance"></a>Guía para la configuración de la administración de inquilinos

Este artículo está dirigido a administradores de Power BI encargados de instalar y configurar el entorno de Power BI de su organización.

Proporciona instrucciones para la configuración específica de inquilinos que ayuda a mejorar la experiencia de Power BI, o que podrían poner en riesgo la organización. Se recomienda configurar siempre el inquilino de modo que esté alineado con las directivas y los procesos de la organización.

La [configuración de inquilinos](../service-admin-portal.md#tenant-settings) se administra en el [portal de administración](https://app.powerbi.com/admin-portal/tenantSettings) y la puede llevar a cabo [un administrador del servicio Power BI](../service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi). Muchos valores de configuración de inquilino pueden restringir las capacidades y características a un conjunto limitado de usuarios. Así pues, le recomendamos que se familiarice con la configuración para planear los grupos de seguridad que necesitará. Es posible que descubra que puede aplicar el mismo grupo de seguridad a varias configuraciones.

## <a name="improve-power-bi-experience"></a>Mejora de la experiencia de Power BI

### <a name="publish-get-help-information"></a>Publicar información "Obtener ayuda"

Le recomendamos que configure los sitios internos relacionados con Power BI mediante [Microsoft Teams](/microsoftteams) u otra plataforma de colaboración. Puede usar estos sitios para almacenar documentación de entrenamiento, hospedar debates, realizar solicitudes de licencias o responder a la ayuda.

En ese caso, se recomienda que habilite la opción **Publicar información de "Obtener ayuda"** _para toda la organización_. Se encuentra en el grupo **Configuración de la ayuda y el soporte técnico**. Puede establecer las direcciones URL de:

- documentación de entrenamiento;
- foro de debate;
- solicitudes de licencias;
- servicio de asistencia.

Estas direcciones URL estarán disponibles como vínculos en el menú de ayuda de Power BI.

> [!NOTE]
> El hecho de proporcionar la dirección URL de las **solicitudes de licencias** impedirá que los usuarios individuales se suscriban a la versión de evaluación gratuita de 60 días de Power BI Pro. En su lugar, se les dirigirá al sitio interno con información sobre cómo adquirir una licencia, ya sea gratis o Pro.

![Se muestra la opción "Publicar información de 'Obtener ayuda'".](media/admin-tenant-settings/publish-get-help-information.png)

## <a name="manage-risk"></a>Administración de los riesgos.

### <a name="receive-email-notification-service-outages-or-incidents"></a>Recepción de notificaciones por correo electrónico sobre interrupciones o incidentes en el servicio

Puede recibir una notificación por correo electrónico si el inquilino se ve afectado por un incidente o una interrupción del servicio. De este modo, puede responder a los incidentes de forma proactiva.

Le recomendamos que habilite la opción **Recepción de notificaciones por correo electrónico sobre interrupciones o incidentes en el servicio**. Se encuentra en el grupo **Configuración de la ayuda y el soporte técnico**. Asigne uno o varios grupos de seguridad _habilitados para correo_.

![Se muestra la opción "Recepción de notificaciones por correo electrónico sobre interrupciones o incidentes en el servicio".](media/admin-tenant-settings/receive-email-notifications-for-service-outages-or-incidents.png)

### <a name="information-protection"></a>Protección de la información

La protección de la información permite aplicar la configuración de protección (como el cifrado o las marcas de agua) al exportar datos desde el servicio Power BI.

Hay dos configuraciones de inquilino relacionadas con la protección de la información. De forma predeterminada, ambas opciones están deshabilitadas para toda la organización.

Se recomienda que habilite esta configuración cuando sea necesario controlar y proteger la información confidencial. Para obtener más información, consulte [Protección de datos en Power BI](../admin/service-security-data-protection-overview.md).

### <a name="create-workspaces"></a>Crear áreas de trabajo

Puede impedir que los usuarios creen áreas de trabajo. De este modo, puede controlar lo que se crea dentro de la organización.

> [!NOTE]
> Actualmente hay un período de transición entre la experiencia antigua del área de trabajo y la nueva. Esta configuración de inquilino solo se aplica a la nueva experiencia.

La opción **Crear áreas de trabajo** está habilitada de forma predeterminada para toda la organización. Se encuentra en el grupo **Configuración del área de trabajo**.

Se recomienda que asigne uno o varios grupos de seguridad. Se puede conceder _o denegar_ permiso a estos grupos para crear áreas de trabajo.

Asegúrese de incluir instrucciones en la documentación que permitan a los usuarios (que no tienen derechos de creación de áreas de trabajo) saber cómo pueden solicitar una nueva área de trabajo.

![Se muestra la opción "Crear áreas de trabajo".](media/admin-tenant-settings/create-workspaces.png)

### <a name="share-content-with-external-users"></a>Compartir contenido con usuarios externos

Los usuarios pueden compartir informes y paneles con personas ajenas a la organización.

La opción **Compartir contenido con usuarios externos** está habilitada de forma predeterminada para toda la organización. Se encuentra en el grupo **Exportar y compartir configuración**.

Se recomienda que asigne uno o varios grupos de seguridad. Se puede conceder _o denegar_ permiso a estos grupos para compartir contenido con usuarios externos.

![Se muestra la opción "Compartir contenido con usuarios externos".](media/admin-tenant-settings/share-content-with-external-users.png)

### <a name="publish-to-web"></a>Publicar en Web

La característica [Publicar en Web](../service-publish-to-web.md) permite publicar informes públicos en la Web. Si se usa incorrectamente, existe el riesgo de que la información confidencial esté disponible en la Web.

La opción **Publicar en Web** está habilitada de forma predeterminada para toda la organización, pero restringe la capacidad de los usuarios que no son administradores para crear códigos para insertar. Se encuentra en el grupo **Exportar y compartir configuración**.

Si está habilitada, se recomienda que asigne uno o varios grupos de seguridad. Se puede conceder _o denegar_ permiso a estos grupos para publicar informes.

Además, hay una opción para elegir cómo funcionan los códigos para insertar. De forma predeterminada, se establece en **Solo permitir códigos existentes**. Esto implica que se solicitará a los usuarios que se pongan en contacto con un administrador de Power BI para crear un código para insertar.

![Se muestra la opción "Publicar en Web".](media/admin-tenant-settings/publish-to-web.png)

También se recomienda que revise regularmente los [códigos para insertar de Publicar en Web](https://app.powerbi.com/admin-portal/embedCodes). Quite los códigos si provocan la publicación de información privada o confidencial.

### <a name="export-data"></a>Exportar datos

Puede impedir que los usuarios exporten datos de los iconos del panel o los objetos visuales del informe.

La opción **Exportar datos** está habilitada de forma predeterminada para toda la organización. Se encuentra en el grupo **Exportar y compartir configuración**.

Se recomienda que asigne uno o varios grupos de seguridad. Se puede conceder _o denegar_ permiso a estos grupos para publicar informes.

> [!IMPORTANT]
> Si se deshabilita esta opción, también se restringe el uso de las características [Analizar en Excel](../service-analyze-in-excel.md) y [Conexión dinámica](../desktop-report-lifecycle-datasets.md#using-a-power-bi-service-live-connection-for-report-lifecycle-management) del servicio Power BI.

![Se muestra la opción "Exportar datos".](media/admin-tenant-settings/export-data.png)

> [!NOTE]
> Si los usuarios permiten que los usuarios exporten datos, puede agregar una capa de protección aplicando la [protección de datos](../admin/service-security-data-protection-overview.md). Si está configurada, se impedirá a los usuarios no autorizados exportar contenido con etiquetas de confidencialidad.

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Permitir a los usuarios externos editar y administrar el contenido de la organización

Es posible que los usuarios invitados externos puedan editar y administrar el contenido de Power BI. Para más información, consulte [Distribuir contenido de Power BI a usuarios externos invitados con Azure AD B2B](../service-admin-azure-ad-b2b.md).

La opción **Permitir a los usuarios externos editar y administrar el contenido de la organización** está deshabilitada de forma predeterminada para toda la organización. Se encuentra en el grupo **Exportar y compartir configuración**.

Si necesita autorizar que usuarios externos editen y administren contenido, se recomienda que asigne uno o varios grupos de seguridad. Se puede conceder _o denegar_ permiso a estos grupos para publicar informes.

![Se muestra la opción "Permitir a los usuarios externos editar y administrar el contenido de la organización".](media/admin-tenant-settings/allow-external-guest-users.png)

### <a name="developer-settings"></a>Configuración de desarrollador

Hay dos configuraciones de inquilinos relacionadas con la [inserción de contenido de Power BI](../developer/embedding.md). Son las siguientes:

- Insertar contenido en aplicaciones (habilitado de forma predeterminada)
- Concesión de permisos a las entidades de servicio para utilizar las API de Power BI (deshabilitado de forma predeterminada).

Si no tiene intención de usar las API de desarrollador para insertar contenido, se recomienda que las deshabilite. O bien, al menos, configure grupos de seguridad específicos que realizarían esta función.

![Se muestra la configuración de desarrollador.](media/admin-tenant-settings/developer-settings.png)

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [¿Qué es la administración de Power BI?](../service-admin-administering-power-bi-in-your-organization.md)
- [Administración de Power BI en el portal de administración](../service-admin-portal.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com)
