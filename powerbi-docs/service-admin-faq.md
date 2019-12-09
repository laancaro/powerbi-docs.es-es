---
title: 'Administración de Power BI: preguntas más frecuentes (P+F)'
description: Obtenga las respuestas a las preguntas más frecuentes sobre la suscripción de Power BI, la administración de inquilinos y otras tareas administrativas.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 0c9d346017dc3b18abd6a56d0d3a62e1305e6575
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698748"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administración de Power BI: preguntas más frecuentes (P+F)

En este artículo se tratan las preguntas más frecuentes para la administración de Power BI. Para obtener información general sobre la administración de Power BI, vea [¿Qué es la administración de Power BI?](service-admin-administering-power-bi-in-your-organization.md)

## <a name="whats-in-this-article"></a>Contenido de este artículo

### <a name="sign-up-for-power-bi-section"></a>Sección Suscribirse en Power BI

* [Uso de PowerShell](#using-powershell)
* [¿Cómo se suscriben los usuarios a Power BI?](#how-do-users-sign-up-for-power-bi)
* [¿Cómo se suscriben los usuarios individuales de mi organización?](#how-do-individual-users-in-my-organization-sign-up)
* [¿Cómo puedo impedir que los usuarios se unan a mi inquilino de Office 365 existente?](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [¿Cómo puedo permitir que los usuarios se unan a mi inquilino de Office 365 existente?](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [¿Cómo puedo comprobar si tengo el bloqueo activado en el inquilino?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [¿Cómo puedo impedir que mis usuarios existentes comiencen a usar Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [¿Cómo puedo permitir a mis usuarios existentes que se suscriban a Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Sección Administración de Power BI

* [¿Cómo cambiará esto la manera de administrar identidades para usuarios de mi organización hoy?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [¿Cómo se administra Power BI?](#how-do-we-manage-power-bi)
* [¿Cuál es el proceso para administrar un inquilino creado por Microsoft para mis usuarios?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Si dispongo de varios dominios, ¿puedo controlar el inquilino de Microsoft 365 al que se agregan usuarios?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [¿Cómo quito Power BI para los usuarios que ya están suscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [¿Cómo sé cuándo nuevos usuarios se han unido a mi inquilino?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [¿Hay aspectos adicionales para los que debería prepararme?](#are-there-any-additional-things-i-should-prepare-for)
* [¿Dónde se encuentra mi inquilino de Power BI?](#where-is-my-power-bi-tenant-located)
* [¿Qué es el Acuerdo de Nivel de Servicio de Power BI?](#what-is-the-power-bi-sla)
* [¿Cómo controla Power BI la alta disponibilidad y la conmutación por error?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Sección Seguridad en Power BI

* [¿Cumple Power BI los requisitos de cumplimiento nacionales, regionales y específicos del sector?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [¿Cómo funciona la seguridad en Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Suscribirse en Power BI

### <a name="using-powershell"></a>Uso de PowerShell

Algunos de los procedimientos descritos en esta sección requieren los scripts de Windows PowerShell. Si no está familiarizado con PowerShell, se recomienda leer la [Guía de introducción de PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=286814). Para ejecutar los scripts, instale primero la última versión de 64 bits de [PowerShell de Azure Active Directory para Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>¿Cómo se suscriben los usuarios a Power BI?

Como administrador de Microsoft 365, se puede suscribir a Power BI en el [sitio web de Power BI](https://powerbi.microsoft.com) o en la página [Servicios de compra](https://admin.microsoft.com/AdminPortal/Home#/catalog) del Centro de administración de Microsoft 365. Al suscribirse un administrador de Microsoft 365 a Power BI, puede asignar licencias de usuario a los que deban tener acceso.

Además, los usuarios individuales de la organización pueden suscribirse a Power BI a través del [sitio web de Power BI](https://powerbi.microsoft.com). Cuando un usuario de la organización se suscribe a Power BI, el servicio le asigna de forma automática una licencia de Power BI. Para más información, vea [Registro en Power BI como usuario individual](service-self-service-signup-for-power-bi.md) y [Licencias de Power BI en la organización](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>¿Cómo se suscriben los usuarios individuales de mi organización?

Hay tres escenarios que se podrían aplicarse a los usuarios de su organización:

* **Escenario 1**: Su organización ya tiene un entorno de Microsoft 365 y el usuario que se suscribe a Power BI ya tiene una cuenta de Microsoft 365.
    En este escenario, si un usuario ya tiene una cuenta profesional o educativa en el inquilino (por ejemplo, contoso.com) pero todavía no tiene Power BI, Microsoft simplemente activa el plan de Power BI (gratis) para esa cuenta. Se notifica de forma automática al usuario cómo usar el servicio Power BI.

* **Escenario 2**: Su organización tiene un entorno de Microsoft 365, pero el usuario que se suscribe a Power BI no tiene cuenta de Microsoft 365.
    En este escenario, el usuario tiene una dirección de correo electrónico en el dominio de la organización (por ejemplo, contoso.com), pero todavía no tiene una cuenta de Microsoft 365. En este caso, el usuario puede suscribirse a Power BI y automáticamente se le asigna una cuenta. Esta acción permite al usuario acceder al servicio Power BI. Por ejemplo, si una empleada llamada Nancy usa su dirección de correo del trabajo (como nancy@contoso.com) para suscribirse, Microsoft la agrega de forma automática como usuario en el entorno de Microsoft 365 de Contoso y activa Power BI para esa cuenta.

* **Escenario 3**: La organización no tiene un entorno de Microsoft 365 conectado al dominio de correo electrónico.
    No hay ninguna acción administrativa obligatoria para la organización con el fin de aprovechar las ventajas de Power BI. El servicio agrega usuarios a un nuevo directorio de usuario solo en la nube. También puede optar por asumir el control como administrador global de Microsoft 365 por el inquilino y realizar la administración.

> [!IMPORTANT]
> Si su organización tiene varios dominios de correo y usted prefiere que todas las extensiones de dirección de correo estén en el mismo inquilino, agregue todos los dominios de dirección de correo a un inquilino de Azure Active Directory antes de suscribir ningún usuario. Después de haber creado a los usuarios, no hay ningún mecanismo automático para moverlos entre inquilinos. Para más información sobre este proceso, consulte [Si dispongo de varios dominios, ¿puedo controlar el inquilino de Microsoft 365 al que se agregan usuarios?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to) más adelante en este artículo y [Agregar un dominio a Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>¿Cómo puedo impedir que los usuarios se unan a mi inquilino de Microsoft 365 existente?

Hay pasos que puede realizar como administrador global de Microsoft 365 para impedir que los usuarios se unan a su inquilino de Microsoft 365 existente. Si bloquea el acceso, se producirá un error en los intentos de los usuarios para suscribirse y aparece un mensaje que les redirige para que se pongan en contacto con el administrador de su organización. No es necesario repetir este proceso si ya ha deshabilitado la distribución automática de licencias (por ejemplo, mediante Office 365 para el ámbito educativo para estudiantes, profesores y docentes).

Use el siguiente script de PowerShell para impedir que los nuevos usuarios se unan a un inquilino administrado. ([Más información sobre PowerShell][1]).

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> El bloqueo del acceso impide que los nuevos usuarios de su organización se suscriban a Power BI. Los usuarios que se suscriben a Power BI antes de deshabilitar nuevas suscripciones para su organización aún conservarán sus licencias. Para quitar un usuario, consulte [¿Cómo quito Power BI para los usuarios que ya están suscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) más adelante en este artículo.

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>¿Cómo puedo permitir que los usuarios se unan a mi inquilino de Microsoft 365 existente?

Use el siguiente script de PowerShell para permitir que los nuevos usuarios se unan a un inquilino administrado. ([Más información sobre PowerShell][1]).

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>¿Cómo puedo comprobar si tengo el bloqueo activado en el inquilino?

Use el siguiente script de PowerShell para comprobar la configuración. *AllowEmailVerifiedUsers* debe ser false. ([Más información sobre PowerShell][1]).

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>¿Cómo puedo impedir que mis usuarios existentes comiencen a utilizar Power BI?

La opción de configuración de Azure AD que controla esto es **AllowAdHocSubscriptions**. La mayoría de los inquilinos tienen esta opción establecida en *true*, lo que significa que está habilitada. Si ha adquirido Power BI a través de un asociado, podría estar establecida en *false*, lo que significa que está deshabilitada.

Use el siguiente script de PowerShell para deshabilitar las suscripciones ad hoc. ([Más información sobre PowerShell][1]).

1. Inicie sesión en Azure Active Directory con sus credenciales de Microsoft 365. La primera línea del siguiente script de PowerShell le pide las credenciales. La segunda línea se conecta a Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Captura de pantalla del inicio de sesión de Azure Active Directory a través de PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Después de iniciar sesión, ejecute el comando siguiente para ver cómo está configurado actualmente el inquilino.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Ejecute este comando para habilitar (`$true`) o deshabilitar (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Use la marca **AllowAdHocSubscriptions** para controlar varias funcionalidades de usuario en la organización, incluida la capacidad de que los usuarios se suscriban al servicio Azure Rights Management. El cambio de esta marca afecta a todas estas funcionalidades. Con un valor de configuración *false*, los usuarios siguen pudiendo registrarse para una prueba individual de Power BI Pro.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>¿Cómo puedo permitir a mis usuarios existentes que se suscriban a Power BI?

Para permitir que los usuarios existentes se suscriban a Power BI, ejecute el comando indicado para la pregunta anterior, pero pase `$true` en lugar de `$false` en el último paso.

## <a name="administration-of-power-bi"></a>Administración de Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>¿Cómo cambiará esto la manera de administrar identidades para usuarios de mi organización hoy?

Hay tres escenarios que se podrían aplicarse a los usuarios de su organización:

* **Escenario 1**: Si la organización ya tiene un entorno de Microsoft 365 y todos los usuarios tienen cuentas de Microsoft 365, no se producirá ningún cambio en la forma de administrar las identidades.

* **Escenario 2**: Si la organización ya tiene un entorno de Microsoft 365 pero no todos los usuarios tienen cuentas de Microsoft 365, se crea un usuario en el inquilino y se asignan licencias en función de la dirección de correo electrónico profesional o educativa del usuario.

    Como resultado, el número de usuarios que administra en cualquier momento determinado crecerá a medida que los usuarios de la organización se suscriben al servicio.

* **Escenario 3**: Si la organización no tiene un entorno de Microsoft 365 conectado al dominio de correo electrónico, no se producirá ningún cambio en la forma de administrar las identidades.

    El servicio agrega usuarios a un nuevo directorio de usuario solo en la nube; puede optar por asumir el control como administrador global de Microsoft 365 y realizar la administración.

### <a name="how-do-we-manage-power-bi"></a>¿Cómo se administra Power BI?

Power BI proporciona un portal de administración de Power BI para los usuarios con el rol de administrador global de Microsoft 365 y los usuarios con el rol de administrador del servicio Power BI. Para usar el portal de administración de Power BI, debe marcar la cuenta como **Administrador global** dentro de Microsoft 365 o Azure Active Directory, o bien, alguien debe asignarle el rol de administrador del servicio Power BI a la cuenta de usuario. Para más información, vea [Descripción del rol de administrador de Power BI](service-admin-role.md) y [Portal de administración de Power BI](service-admin-portal.md). El portal permite controlar la configuración de los usuarios, ver las estadísticas de uso de Power BI y proporciona un vínculo al Centro de administración de Microsoft 365 para administrar usuarios y grupos.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>¿Cuál es el proceso para administrar un inquilino creado por Microsoft para mis usuarios?

Cuando un usuario de autoservicio se suscribe a un servicio en la nube que usa Azure AD, el servicio lo agrega a un directorio de Azure AD no administrado en función de su dominio de correo electrónico. Puede reclamar y administrar un inquilino que alguien haya creado mediante un proceso conocido como *adquisición de administración*. Para más información, vea [Adquisición de un directorio no administrado como administrador en Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover). El tipo de adquisición que realice dependerá de si existe un inquilino administrado asociado al dominio:

* Power BI admite la adquisición de administración interna. Cuando realiza una adquisición de administración _interna_ de un directorio de Azure no administrado, se le agregará como administrador global del directorio no administrado. No se migra ningún usuario, dominio ni plan de servicio a ningún otro directorio que administre.

* Power BI ya no admite la adquisición de administración externa. Cuando realiza una adquisición de administración _externa_ de un directorio de Azure no administrado, agrega el nombre de dominio DNS del directorio no administrado al directorio de Azure administrado. La adquisición externa resultará en una pérdida de acceso a todo el contenido de Power BI en el inquilino original que no se administraba. Será necesario volver a publicar los informes de Power BI y volver a crear los paneles y las aplicaciones de Power BI en el nuevo inquilino.

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>Si dispongo de varios dominios, ¿puedo controlar el inquilino de Microsoft 365 al que se agregan usuarios?

Si no hace nada, el servicio crea un inquilino para cada dominio y subdominio de correo electrónico del usuario. Si desea que todos los usuarios se encuentren en el mismo inquilino independientemente de sus extensiones de dirección de correo electrónico: Cree con antelación un inquilino de destino, o bien use uno existente. Después, agregue todos los dominios y subdominios existentes que quiera que se consoliden en ese inquilino. Todos los usuarios cuyas direcciones de correo electrónico terminen en esos dominios y subdominios se unirán de forma automática al inquilino de destino al suscribirse.

> [!IMPORTANT]
> Después de haber creado a los usuarios, no se admite ningún mecanismo automático para moverlos entre inquilinos. Para información sobre cómo agregar dominios a un solo inquilino de Microsoft 365, consulte [Pasos para comprobar dominio en Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>¿Cómo quito Power BI para los usuarios que ya están suscritos?

Si un usuario se suscribió a Power BI, pero ya no desea que tenga acceso a Power BI, puede quitar la licencia de Power BI para ese usuario.

1. Vaya al [Centro de administración de Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. En el panel de navegación, seleccione **usuarios** > **Usuarios activos**.

1. Busque el usuario para el que desea quitar la licencia y seleccione su nombre.

    También puede realizar la administración masiva de licencias para los usuarios. Para ello, seleccione varios usuarios y luego **Editar licencias de productos**.

1. En la página de detalles del usuario, junto a **Licencias de productos**, seleccione **Editar**.

1. En función de la licencia que haya aplicado a la cuenta, establezca **Power BI (gratis)** o **Power BI Pro** en **Desactivado**.

1. Seleccione **Guardar**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>¿Cómo sé cuándo nuevos usuarios se han unido a mi inquilino?

A los usuarios que se han unido al inquilino mediante la suscripción autoservicio se les asigna una licencia única por la que se puede filtrar dentro el panel de usuarios activos en el panel de administración. Para crear esta vista, siga estos pasos.

1. Vaya al [Centro de administración de Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. En el panel de navegación, seleccione **usuarios** > **Usuarios activos**.

1. En el menú **Vistas**, seleccione **Agregar vista personalizada**.

1. Asigne un nombre a la nueva vista y, en **Licencia de producto asignada**, seleccione **Power BI (gratis)** o **Power BI Pro**.

    Solo puede tener una licencia seleccionada por vista. Si tiene tanto la licencia **Power BI (gratis)** como la licencia **Power BI Pro** en su organización, puede crear dos vistas.

1. Escriba cualquier otra condición que desee y después seleccione **Agregar**.

1. Después de crear la vista, estará disponible en el menú **Vistas**.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>¿Hay aspectos adicionales para los que debería prepararme?

Es posible que experimente un aumento en las solicitudes de restablecimiento de contraseña. Para obtener información sobre este proceso, vea [Restablecimiento de una contraseña de usuario](/office365/admin/add-users/reset-passwords).

Puede quitar un usuario del inquilino mediante el proceso estándar en el Centro de administración de Microsoft 365. Sin embargo, si el usuario todavía tiene una dirección de correo electrónico activa de su organización, puede volver a unirse a menos que bloquee todos los usuarios para impedirles que se unan.

### <a name="where-is-my-power-bi-tenant-located"></a>¿Dónde se encuentra mi inquilino de Power BI?

Para obtener información sobre en qué región de datos se encuentra el inquilino de Power BI, vea [¿Dónde se encuentra mi inquilino de Power BI?](service-admin-where-is-my-tenant-located.md)

### <a name="what-is-the-power-bi-sla"></a>¿Qué es el Acuerdo de Nivel de Servicio?

Para obtener información sobre el Acuerdo de Nivel de Servicio de Power BI, vea el artículo [Licensing Terms and Documentation](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) (Documentación y términos de licencia) de la sección **Licensing** (Licencias) del sitio web de licencias de Microsoft.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>¿Cómo controla Power BI la alta disponibilidad y la conmutación por error?

Para obtener información sobre alta disponibilidad y conmutación por error, vea [P+F sobre alta disponibilidad, conmutación por error y recuperación ante desastres en Power BI](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Seguridad en Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>¿Cumple Power BI los requisitos de cumplimiento nacionales, regionales y específicos del sector?

Para obtener más información acerca de la compatibilidad de Power BI, consulte el [Centro de confianza de Microsoft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>¿Cómo funciona la seguridad en Power BI?

Microsoft ha creado Power BI sobre Microsoft 365, que a su vez se basa en servicios de Azure como Azure Active Directory. Para obtener información general de la arquitectura de Power BI, vea [Seguridad de Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Pasos siguientes

[Portal de administración de Power BI](service-admin-portal.md)  
[Descripción del rol de administrador de Power BI](service-admin-role.md)  
[Registro de autoservicio para Power BI](service-self-service-signup-for-power-bi.md)  
[Adquisición de Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[¿Qué es Power BI Premium?](service-premium-what-is.md)  
[Procedimientos para comprar Power BI Premium](service-admin-premium-purchase.md)  
[Notas del producto de Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Administración del grupo en Power BI y Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Administración de cuentas de usuario de Office 365](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Administración de grupos de Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview
