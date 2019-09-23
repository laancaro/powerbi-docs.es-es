---
title: 'Administración de Power BI: preguntas más frecuentes (P+F)'
description: Obtenga las respuestas a las preguntas más frecuentes sobre la suscripción de Power BI, la administración de inquilinos y otras tareas administrativas.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c32f4b0a03ba751d5b8cbd6e98633275ece9222b
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877814"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administración de Power BI: preguntas más frecuentes (P+F)

En este artículo se tratan las preguntas más frecuentes para la administración de Power BI. Para obtener información general sobre la administración de Power BI, vea [¿Qué es la administración de Power BI?](service-admin-administering-power-bi-in-your-organization.md)

## <a name="whats-in-this-article"></a>Contenido de este artículo

### <a name="sign-up-for-power-bi-section"></a>Sección Suscribirse en Power BI

* [Uso de PowerShell](#using-powershell)
* [¿Cómo se suscriben los usuarios a Power BI?](#how-do-users-sign-up-for-power-bi)
* [¿Cómo se suscriben los usuarios individuales de mi organización?](#how-do-individual-users-in-my-organization-sign-up)
* [¿Cómo puedo impedir que los usuarios se unan a mi inquilino de Office 365 existente?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [¿Cómo puedo permitir que los usuarios se unan a mi inquilino de Office 365 existente?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [¿Cómo puedo comprobar si tengo el bloqueo activado en el inquilino?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [¿Cómo puedo impedir que mis usuarios existentes comiencen a usar Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [¿Cómo puedo permitir a mis usuarios existentes que se suscriban a Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Sección Administración de Power BI

* [¿Cómo cambiará esto la manera de administrar identidades para usuarios de mi organización hoy?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [¿Cómo se administra Power BI?](#how-do-we-manage-power-bi)
* [Si dispongo de varios dominios, ¿puedo controlar el inquilino de Office 365 al que se agregan usuarios?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
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

Algunos de los procedimientos descritos en esta sección requieren los scripts de Windows PowerShell. Si no está familiarizado con PowerShell, se recomienda leer la [Guía de introducción de PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814). Para ejecutar los scripts, instale primero la última versión de 64 bits de [PowerShell de Azure Active Directory para Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>¿Cómo se suscriben los usuarios a Power BI?

Como administrador, se puede suscribir a Power BI en el [sitio web de Power BI](https://powerbi.microsoft.com) o en la página [Servicios de compra](https://admin.microsoft.com/AdminPortal/Home#/catalog) del Centro de administración de Microsoft 365. Cuando un administrador se suscribe a Power BI, puede asignar licencias de usuario a usuarios que deben tener acceso.

Además, los usuarios individuales de la organización pueden suscribirse a Power BI a través del [sitio web de Power BI](https://powerbi.microsoft.com). Cuando un usuario de la organización se suscribe a Power BI, el servicio le asigna de forma automática una licencia de Power BI. Para más información, vea [Registro en Power BI como usuario individual](service-self-service-signup-for-power-bi.md) y [Licencias de Power BI en la organización](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>¿Cómo se suscriben los usuarios individuales de mi organización?

Hay tres escenarios que se podrían aplicarse a los usuarios de su organización:

* **Escenario 1**: Su organización ya tiene un entorno de Office 365 existente y el usuario que se suscribe a Power BI ya tiene una cuenta de Office 365.
    En este escenario, si un usuario ya tiene una cuenta profesional o educativa en el inquilino (por ejemplo, contoso.com) pero todavía no tiene Power BI, Microsoft simplemente activa el plan para esa cuenta. Se notifica de forma automática al usuario cómo usar el servicio Power BI.

* **Escenario 2**: Su organización tiene un entorno de Office 365 existente, pero el usuario que se suscribe a Power BI no tiene una cuenta de Office 365.
    En este escenario, el usuario tiene una dirección de correo electrónico en el dominio de la organización (por ejemplo, contoso.com), pero todavía no tiene una cuenta de Office 365. En este caso, el usuario puede suscribirse a Power BI y automáticamente se le asigna una cuenta. Esta acción permite al usuario acceder al servicio Power BI. Por ejemplo, si una empleada llamada Nancy usa su dirección de correo del trabajo (como nancy@contoso.com) para suscribirse, Microsoft la agrega de forma automática como un usuario en el entorno de Office 365 de Contoso y activa Power BI para esa cuenta.

* **Escenario 3**: La organización no tiene un entorno de Office 365 conectado al dominio de correo electrónico.
    No hay ninguna acción administrativa obligatoria para la organización con el fin de aprovechar las ventajas de Power BI. El servicio agrega usuarios a un nuevo directorio de usuario solo en la nube. También puede optar por asumir el control como administrador de inquilinos y administrarlos.

> [!IMPORTANT]
> Si su organización tiene varios dominios de correo y usted prefiere que todas las extensiones de dirección de correo estén en el mismo inquilino, agregue todos los dominios de dirección de correo a un inquilino de Azure Active Directory antes de suscribir ningún usuario. Después de haber creado a los usuarios, no hay ningún mecanismo automático para moverlos entre inquilinos. Para más información sobre este proceso, vea [Si dispongo de varios dominios, ¿puedo controlar el inquilino de Office 365 al que se agregan usuarios?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) más adelante en este artículo y [Agregar un dominio a Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>¿Cómo puedo impedir que los usuarios se unan a mi inquilino de Office 365 existente?

Hay pasos que puede realizar, como administrador, para impedir que los usuarios se unan a su inquilino de Office 365 existente. Si bloquea el acceso, se producirá un error en los intentos de los usuarios para suscribirse y aparece un mensaje que les redirige para que se pongan en contacto con el administrador de su organización. No es necesario repetir este proceso si ya ha deshabilitado la distribución automática de licencias (por ejemplo, mediante Office 365 para el ámbito educativo para estudiantes, profesores y docentes).

Use el siguiente script de PowerShell para impedir que los nuevos usuarios se unan a un inquilino administrado. ([Más información sobre PowerShell][1]).

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> El bloqueo del acceso impide que los nuevos usuarios de su organización se suscriban a Power BI. Los usuarios que se suscriben a Power BI antes de deshabilitar nuevas suscripciones para su organización aún conservarán sus licencias. Para quitar un usuario, consulte [¿Cómo quito Power BI para los usuarios que ya están suscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) más adelante en este artículo.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>¿Cómo puedo permitir que los usuarios se unan a mi inquilino de Office 365 existente?

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

1. Inicie sesión en Azure Active Directory usando sus credenciales de Office 365. La primera línea del siguiente script de PowerShell le pide las credenciales. La segunda línea se conecta a Azure Active Directory.

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
> Use la marca **AllowAdHocSubscriptions** para controlar varias funcionalidades de usuario en la organización, incluida la capacidad de que los usuarios se suscriban al servicio Azure Rights Management. El cambio de esta marca afecta a todas estas funcionalidades. Si el valor es *false*, los usuarios todavía pueden registrarse para obtener una prueba de Pro.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>¿Cómo puedo permitir a mis usuarios existentes que se suscriban a Power BI?

Para permitir que los usuarios existentes se suscriban a Power BI, ejecute el comando indicado para la pregunta anterior, pero pase `$true` en lugar de `$false` en el último paso.

## <a name="administration-of-power-bi"></a>Administración de Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>¿Cómo cambiará esto la manera de administrar identidades para usuarios de mi organización hoy?

Hay tres escenarios que se podrían aplicarse a los usuarios de su organización:

* **Escenario 1**: Si la organización ya tiene un entorno de Office 365 existente y todos los usuarios tienen cuentas de Office 365, no se producirá ningún cambio en la forma de administrar la identidad.

* **Escenario 2**: Si la organización ya tiene un entorno de Office 365 existente pero no todos los usuarios tienen cuentas de Office 365, se crea un usuario en el inquilino y se asignan licencias en función de la dirección de correo electrónico profesional o educativa del usuario.

    Como resultado, el número de usuarios que administra en cualquier momento determinado crecerá a medida que los usuarios de la organización se suscriben al servicio.

* **Escenario 3**: Si la organización no tiene un entorno de Office 365 conectado al dominio de correo electrónico, no se producirá ningún cambio en la forma de administrar las identidades.

    El servicio agrega usuarios a un nuevo directorio de usuario solo en la nube. También puede optar por asumir el control como administrador de inquilinos y administrarlos.

### <a name="how-do-we-manage-power-bi"></a>¿Cómo se administra Power BI?

Power BI proporciona un portal de administración que permite ver estadísticas de uso, proporciona un vínculo al Centro de administración de Microsoft 365 para administrar usuarios y grupos, y ofrece la posibilidad de controlar la configuración de todos los inquilinos.

Para usar al portal de administración de Power BI, debe marcar la cuenta como **Administrador global** dentro de Office 365 o Azure Active Directory, o bien alguien debe asignar el rol de administrador del servicio Power BI a la cuenta de usuario. Para más información, vea [Descripción del rol de administrador de Power BI](service-admin-role.md) y [Portal de administración de Power BI](service-admin-portal.md).

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Si dispongo de varios dominios, ¿puedo controlar el inquilino de Office 365 al que se agregan usuarios?

Si no hace nada, el servicio crea un inquilino para cada dominio y subdominio de correo electrónico del usuario. Si desea que todos los usuarios se encuentren en el mismo inquilino independientemente de sus extensiones de dirección de correo electrónico: Cree con antelación un inquilino de destino, o bien use uno existente. Después, agregue todos los dominios y subdominios existentes que quiera que se consoliden en ese inquilino. Todos los usuarios cuyas direcciones de correo electrónico terminen en esos dominios y subdominios se unirán de forma automática al inquilino de destino al suscribirse.

> [!IMPORTANT]
> Después de haber creado a los usuarios, no se admite ningún mecanismo automático para moverlos entre inquilinos. Para obtener información sobre cómo agregar dominios a un solo inquilino de Office 365, consulte [Pasos para comprobar dominio en Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>¿Cómo quito Power BI para los usuarios que ya están suscritos?

Si un usuario se suscribió a Power BI, pero ya no desea que tenga acceso a Power BI, puede quitar la licencia de Power BI para ese usuario.

1. Vaya al [Centro de administración de Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. En la barra de navegación izquierda, seleccione **Usuarios** > **Usuarios activos**.

1. Busque el usuario para el que desea quitar la licencia y seleccione su nombre.

    También puede realizar la administración masiva de licencias para los usuarios. Para ello, seleccione varios usuarios y luego **Editar licencias de productos**.

1. En la página de detalles del usuario, junto a **Licencias de productos**, seleccione **Editar**.

1. En función de la licencia que haya aplicado a la cuenta, establezca **Power BI (gratis)** o **Power BI Pro** en **Desactivado**.

1. Seleccione **Guardar**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>¿Cómo sé cuándo nuevos usuarios se han unido a mi inquilino?

A los usuarios que se han unido al inquilino como parte de este programa se les asigna una licencia única por la que se puede filtrar dentro el panel de usuario activo en el panel de administración. Para crear esta vista, siga estos pasos.

1. Vaya al [Centro de administración de Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. En la barra de navegación izquierda, seleccione **Usuarios** > **Usuarios activos**.

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

Para obtener información sobre el Acuerdo de Nivel de Servicio de Power BI, vea el artículo [Licensing Terms and Documentation](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) (Documentación y términos de licencia) de la sección **Licensing** (Licencias) del sitio web de licencias de Microsoft.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>¿Cómo controla Power BI la alta disponibilidad y la conmutación por error?

Para obtener información sobre alta disponibilidad y conmutación por error, vea [P+F sobre alta disponibilidad, conmutación por error y recuperación ante desastres en Power BI](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Seguridad en Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>¿Cumple Power BI los requisitos de cumplimiento nacionales, regionales y específicos del sector?

Para obtener más información acerca de la compatibilidad de Power BI, consulte el [Centro de confianza de Microsoft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>¿Cómo funciona la seguridad en Power BI?

Microsoft ha creado Power BI sobre Office 365, que a su vez se basa en servicios de Azure como Azure Active Directory. Para obtener información general de la arquitectura de Power BI, vea [Seguridad de Power BI](service-admin-power-bi-security.md).

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

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview