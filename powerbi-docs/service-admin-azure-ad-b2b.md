---
title: Distribución de contenido a usuarios externos invitados con Azure AD B2B
description: Power BI se integra con Azure Active Directory Business-to-business (Azure AD B2B) para permitir una distribución segura de contenido de Power BI para usuarios invitados de fuera de la organización.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2d1e9e32fcec67647bb75ac14ed872e6c51fef96
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101716"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir contenido de Power BI a usuarios externos invitados con Azure AD B2B

Power BI se integra con Azure Active Directory de negocio a negocio (Azure AD B2B) para permitir una distribución segura de contenido de Power BI para usuarios invitados de fuera de la organización manteniendo, aún así, el control sobre los datos internos.  

Además, puede permitir que usuarios invitados de fuera de la organización editen y administren contenido dentro de la organización.

## <a name="enable-access"></a>Habilitar acceso

Asegúrese de habilitar la [compartir contenido con usuarios externos](service-admin-portal.md#export-and-sharing-settings) característica en el portal de administración de Power BI antes de invitar a usuarios invitados.

También puede usar el [permiten a los usuarios externos invitados edición y administración de contenido de la organización](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) característica. Le permite seleccionar qué usuario invitado puede ver y crear contenido en áreas de trabajo, incluida la exploración de Power BI de su organización.

## <a name="who-can-you-invite"></a>¿A quién puede invitar?

Puede invitar a usuarios invitados con cualquier dirección de correo electrónico, incluidas las cuentas personales como hotmail.com, gmail.com y outlook.com. B2B de Azure AD llama a estas direcciones *identidades de redes sociales*.

## <a name="invite-guest-users"></a>Invitar a usuarios externos

Los usuarios invitados solo requieren las invitaciones de la primera vez que invitarlos a su organización. Hay dos maneras de invitar a los usuarios: planeado invitaciones e invitaciones ad hoc.

### <a name="planned-invites"></a>Invitaciones planeadas

Use una invitación planeada si sabe a qué usuarios desea invitar. Puede enviar la invitación mediante Azure Portal o PowerShell. Debe ser un administrador de inquilinos para invitar a usuarios.

Siga estos pasos para enviar una invitación en Azure Portal.

1. En [Azure Portal](https://portal.azure.com), seleccione **Azure Active Directory**.

1. En **administrar**, seleccione **usuarios** > **todos los usuarios** > **nuevo usuario invitado**.

    ![Captura de pantalla de Azure portal con la nueva opción de usuario invitado mencionadas.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Escriba una **dirección de correo electrónico** y un **mensaje personal**.

    ![Captura de pantalla del cuadro de diálogo de usuario invitado de Azure AD Portal nuevo.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Seleccione **Invitar**.

Para invitar a más de un usuario externo, use PowerShell. Para más información, consulte el [código de colaboración de Azure AD B2B y los ejemplos de PowerShell](/azure/active-directory/b2b/code-samples/).

El usuario invitado debe seleccionar **Empezar** en la invitación de correo electrónico que reciba. A continuación, se agregará al usuario invitado al inquilino.

![Invitación de correo electrónico del usuario de captura de pantalla de invitado.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Invitaciones ad hoc

Para invitar a un usuario externo en cualquier momento, agregue a su panel o informe a través de la interfaz de usuario de recurso compartido o a la aplicación a través de la página de acceso. A continuación se muestra un ejemplo de lo que debe hacer al invitar a un usuario externo para que use una aplicación.

![Captura de pantalla de externo usuario agregado a la lista de acceso de aplicaciones en Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

El usuario invitado recibirá un correo electrónico que indica que la aplicación ha compartido con ellos.

![Captura de pantalla de correo electrónico de la aplicación compartida con el usuario invitado](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

El usuario invitado debe iniciar sesión con su dirección de correo electrónico de la organización. Recibirá un aviso para aceptar la invitación después de iniciar sesión. Después de inicio de sesión, la aplicación se abre para el usuario invitado. Para volver a la aplicación, debe marcar el vínculo como favorito o guardar el correo electrónico.

## <a name="licensing"></a>Licencias

El usuario invitado debe tener la licencia adecuada en su lugar para ver el contenido que se ha compartido. Hay tres maneras para asegurarse de que el usuario tiene una licencia adecuada: usar Power BI Premium, asigne una licencia de Power BI Pro o usar la licencia de Power BI Pro de invitado.

Si se usa la característica [Permitir a los usuarios externos editar y administrar el contenido de la organización](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization), los usuarios invitados que aporten contenido a áreas de trabajo o compartan contenido con otros usuarios necesitan una licencia de Power BI Pro.

### <a name="use-power-bi-premium"></a>Usar Power BI Premium

Asignar el área de trabajo a [capacidad de Power BI Premium](service-premium-what-is.md) permite que el usuario invitado usar la aplicación sin necesidad de una licencia de Power BI Pro. Power BI Premium también permite a las aplicaciones aprovechar otras funcionalidades como la frecuencia de actualización mayor, capacidad dedicada y tamaños de modelo de gran tamaño.

![Diagrama de la experiencia del usuario invitado con Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Asignar una licencia de Power BI Pro a un usuario invitado

Asignar una licencia de Power BI Pro al usuario invitado, dentro de su inquilino, permite que ese contenido de la vista del usuario invitado en el inquilino.

![Diagrama de la experiencia del usuario invitado con licencia de Pro asignar desde el inquilino.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>El usuario invitado aporta su propia licencia de Power BI Pro

El usuario invitado ya tiene una licencia de Power BI Pro asignada dentro del inquilino.

![Diagrama de la experiencia del usuario invitado al que traigan su propia licencia.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Usuarios invitados que pueden editar y administrar contenido 

Cuando se usa el [permiten a los usuarios externos invitados edición y administración de contenido de la organización](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) característica, los usuarios invitados especificado obtengan acceso a Power BI de su organización. Puede ver cualquier contenido a los que tienen permiso. Pueden tener acceso a casa, examinar las áreas de trabajo, instalar aplicaciones, ver dónde se encuentran en la lista de acceso y contribuir con contenido a áreas de trabajo. Pueden crear o ser administradores de áreas de trabajo que usen la nueva experiencia de área de trabajo. Existen algunas limitaciones. La sección consideraciones y limitaciones se muestran esas restricciones.
 
Para ayudar a los usuarios iniciar sesión en Power BI, les proporciona la dirección URL del inquilino. Para buscar la dirección URL del inquilino, siga estos pasos.

1. En el servicio Power BI, en el menú superior, seleccione Ayuda ( **?** ) y, a continuación, **Acerca de Power BI**.

2. Vea el valor junto a **URL de inquilino**. El valor es la dirección URL del inquilino puede compartir con los usuarios invitados.

    ![Cuadro de diálogo de captura de pantalla de acerca de Power BI con el inquilino del usuario invitado que URL mencionadas.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* De forma predeterminada, B2B externos de AD de Azure limita los invitados al consumo de contenido solo. Pueden ver los invitados de B2B de Azure AD externos aplicaciones, paneles, informes, exportar los datos y crear suscripciones de correo electrónico para paneles e informes. No pueden acceder a áreas de trabajo ni publicar su propio contenido. Sin embargo, estas restricciones no se aplican a los usuarios invitados que obtienen acceso a través de la [permiten a los usuarios externos invitados edición y administración de contenido de la organización](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) característica.

* Para los usuarios invitados que habilita a través de la [permiten a los usuarios externos invitados edición y administración de contenido de la organización](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) característica, algunas experiencias no están disponibles para ellos. Para actualizar o publicar informes, necesitan usar la interfaz de usuario web del servicio Power BI, incluido Obtener datos para cargar archivos de Power BI Desktop.  No se admiten las siguientes experiencias:
    * Publicación directa desde Power BI Desktop en el servicio Power BI
    * Los usuarios invitados no pueden usar Power BI desktop para conectarse a conjuntos de datos de servicio en el servicio Power BI
    * Áreas de trabajo clásicas asociadas a Grupos de Office 365:
        * Usuario invitado no puede crear ni ser administradores de estas áreas de trabajo
        * Los usuarios invitados pueden ser miembros
    * Enviar invitaciones ad hoc no se admite para las listas de acceso de área de trabajo
    * Power BI Publisher para Excel no se admite para los usuarios invitados
    * Los usuarios invitados no se pueden instalar una de Power BI Gateway y conectarse a su organización
    * Los usuarios invitados no se pueden instalar la publicación de aplicaciones en toda la organización
    * Los usuarios invitados no se pueden usar, crear, actualizar o instalar paquetes de contenido organizativos
    * Los usuarios invitados no pueden usar analizar en Excel
    * Los usuarios invitados no pueden ser @mentioned en comentarios
    * Los usuarios invitados no pueden utilizar las suscripciones
    * Los usuarios invitados que usen esta funcionalidad deben tener una cuenta profesional o educativa. Usuarios invitados utilizando cuentas personales experimentará más limitaciones debido al iniciar sesión en las restricciones.

* Esta característica no está disponible con el elemento web de informes Power BI SharePoint Online.

* Hay una configuración de Active Directory que se puede limitar lo que pueden hacer los usuarios invitados externos dentro de la organización en general. Que también se aplica a su entorno de Power BI. En la siguiente documentación se tratan las opciones:
    * [Administrar la configuración de colaboración externa](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Permitir o bloquear invitaciones a los usuarios de B2B de organizaciones específicas](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Pasos siguientes

Para obtener información más detallada, incluido el nivel de fila cómo funciona la seguridad, consulte las notas del producto: [Distribuir contenido de Power BI a usuarios externos invitados con Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Para obtener información acerca de Azure AD B2B, consulte [¿qué es la colaboración B2B de Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
