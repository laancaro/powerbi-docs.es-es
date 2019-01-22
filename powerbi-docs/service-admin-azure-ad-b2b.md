---
title: Distribución de contenido a usuarios externos invitados con Azure AD B2B
description: Power BI se integra con Azure Active Directory Business-to-business (Azure AD B2B) para permitir una distribución segura de contenido de Power BI para usuarios invitados de fuera de la organización.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 7e76f03a3795976aebd1480dc77a579c9245ed9e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282066"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir contenido de Power BI a usuarios externos invitados con Azure AD B2B

Power BI se integra con Azure Active Directory de negocio a negocio (Azure AD B2B) para permitir una distribución segura de contenido de Power BI para usuarios invitados de fuera de la organización manteniendo, aún así, el control sobre los datos internos.

## <a name="enable-access"></a>Habilitar acceso

Asegúrese de que la característica [Exportar y compartir configuración](service-admin-portal.md#export-and-sharing-settings) está habilitada en el portal de administración de Power BI antes de invitar a usuarios invitados.

## <a name="who-can-you-invite"></a>¿A quién puede invitar?

Puede invitar a usuarios invitados con cualquier dirección de correo electrónico, incluidas las cuentas personales como gmail.com, outlook.com y hotmail.com. En Azure AD B2B, estas direcciones se denominan *identidades sociales*.

## <a name="invite-guest-users"></a>Invitar a usuarios externos

Las invitaciones solo se necesitan la primera vez que se invita a un usuario externo a la organización. Hay dos maneras de invitar a los usuarios: invitaciones planeadas e invitaciones ad hoc.

### <a name="planned-invites"></a>Invitaciones planeadas

Use una invitación planeada si sabe a qué usuarios desea invitar. Puede enviar la invitación mediante Azure Portal o PowerShell. Debe ser un administrador de inquilinos para invitar a usuarios.

Siga estos pasos para enviar una invitación en Azure Portal.

1. En [Azure Portal](https://portal.azure.com), seleccione **Azure Active Directory**.

1. En **Administrar**, vaya a **Usuarios** > **Todos los usuarios** > **Nuevo usuario invitado**.

    ![Portal de Azure AD: Nuevo usuario invitado](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. Escriba una **dirección de correo electrónico** y un **mensaje personal**.

    ![Portal de Azure AD: Nuevo mensaje de invitación para usuarios invitados](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. Seleccione **Invitar**.

Para invitar a más de un usuario externo, use PowerShell. Para más información, consulte el [código de colaboración de Azure AD B2B y los ejemplos de PowerShell](/azure/active-directory/b2b/code-samples/).

El usuario invitado debe seleccionar **Empezar** en la invitación de correo electrónico que reciba. A continuación, se agregará al usuario invitado al inquilino.

![Invitación de correo electrónico para el usuario invitado](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Invitaciones ad hoc

Para enviar invitación en cualquier momento, agregue al usuario externo al panel o informe a través de la interfaz de usuario de uso compartido o a la aplicación a través de la página de acceso. A continuación se muestra un ejemplo de lo que debe hacer al invitar a un usuario externo para que use una aplicación.

![Usuario externo agregado a la lista de acceso a las aplicaciones](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

El usuario invitado recibirá un correo electrónico que indica que la aplicación se ha compartido con él.

![Correo electrónico de la aplicación compartida con el usuario invitado](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

El usuario invitado debe iniciar sesión con su dirección de correo electrónico de la organización. Se les pedirá que acepten la invitación después de iniciar sesión. Después de iniciar sesión, se redirige al usuario invitado al contenido de la aplicación. Para volver a la aplicación, debe marcar el vínculo como favorito o guardar el correo electrónico.

## <a name="licensing"></a>Licencias

El usuario invitado debe tener la licencia adecuada en vigor para ver la aplicación que se ha compartido. Existen tres opciones para realizar esta acción: usar Power BI Premium, asignar una licencia de Power BI Pro o utilizar la licencia de Power BI Pro de invitado.

### <a name="use-power-bi-premium"></a>Usar Power BI Premium

Asignar el área de trabajo de la aplicación a una [funcionalidad de Power BI Premium](service-premium.md) permite al usuario invitado usar la aplicación sin necesidad de una licencia de Power BI Pro. Power BI Premium también permite que las aplicaciones saquen partido a otras funcionalidades como una mayor frecuencia de actualización, capacidad dedicada y tamaños de modelo grandes.

![Usar Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Asignar una licencia de Power BI Pro a un usuario invitado

Asignar una licencia de Power BI Pro al usuario invitado, dentro de su inquilino, permite que ese usuario invitado vea el contenido del inquilino.

![Asignar licencia de Pro del inquilino](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>El usuario invitado aporta su propia licencia de Power BI Pro

El usuario invitado ya tiene una licencia de Power BI Pro asignada dentro del inquilino.

![El usuario invitado aporta su propia licencia](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* Los invitados B2B externos solo pueden consumir contenido. Los invitados B2B externos pueden ver aplicaciones, paneles, informes, exportar los datos y crear suscripciones de correo electrónico para los paneles e informes. No pueden acceder a áreas de trabajo ni publicar su propio contenido.

* Esta característica no está disponible actualmente en las aplicaciones móviles de Power BI. En un dispositivo móvil, puede ver el contenido de Power BI compartido mediante Azure AD B2B en un explorador.

* Esta característica no está disponible actualmente en el componente web de los informes de SharePoint Online de Power BI.

## <a name="next-steps"></a>Pasos siguientes

Para más información, incluida la referida a cómo funciona la seguridad en el nivel de fila, consulte las notas del producto: [Distribuir contenido de Power BI a usuarios externos invitados con Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Para obtener información sobre Azure AD B2B, consulte [¿Qué es la colaboración B2B de Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/)
