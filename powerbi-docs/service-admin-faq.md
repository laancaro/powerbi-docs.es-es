---
title: 'Administración de Power BI: preguntas más frecuentes (P+F)'
description: Obtenga información sobre las respuestas a las preguntas más frecuentes sobre la suscripción, la administración de inquilinos y otras tareas administrativas de Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 25d6c8020e500096507ba5e80a020a7a1c3052a6
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "57980436"
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
* [¿Cómo puedo comprobar si tengo el bloque activado en el inquilino?](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [¿Cómo puedo impedir que mis usuarios existentes comiencen a usar Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [¿Cómo puedo permitir a mis usuarios existentes que se suscriban a Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Sección Administración de Power BI

* [¿Cómo cambiará esto la manera de administrar identidades para usuarios de mi organización hoy?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [¿Cómo se administra Power BI?](#how-do-we-manage-power-bi)
* [¿Cuál es el proceso para administrar un inquilino creado por Microsoft para mis usuarios?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Si dispongo de varios dominios, ¿puedo controlar el inquilino de Office 365 al que se agregan usuarios?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [¿Cómo quito Power BI para los usuarios que ya están suscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [¿Cómo sé cuándo nuevos usuarios se han unido a mi inquilino?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [¿Hay aspectos adicionales para los que debería estar preparado?](#are-there-any-additional-things-i-should-be-prepared-for)
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

Como administrador, puede suscribirse a Power BI en el [sitio web de Power BI](https://powerbi.microsoft.com) o en la página de [compras de servicios](https://admin.microsoft.com/AdminPortal/Home#/catalog) del Centro de administración de Office 365. Cuando un administrador se suscribe a Power BI, puede asignar licencias de usuario a usuarios que deben tener acceso.

Además, los usuarios individuales de la organización pueden suscribirse a Power BI a través del [sitio web de Power BI](https://powerbi.microsoft.com). Cuando un usuario de la organización se suscribe a Power BI, a ese usuario se le asigna automáticamente una licencia de Power BI. Para obtener más información, consulte [Registro en Power BI como usuario individual](service-self-service-signup-for-power-bi.md) y [Licencias de Power BI en la organización](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>¿Cómo se suscriben los usuarios individuales de mi organización?

Hay tres escenarios que se podrían aplicarse a los usuarios de su organización:

* **Escenario 1**: Su organización ya tiene un entorno de Office 365 existente y el usuario que se suscribe a Power BI ya tiene una cuenta de Office 365.
    En este escenario, si un usuario ya tiene una cuenta profesional o educativa en el inquilino (por ejemplo, contoso.com) pero todavía no tiene Power BI, Microsoft simplemente activa el plan para esa cuenta y automáticamente se notifica al usuario sobre cómo utilizar el servicio Power BI.

* **Escenario 2**: Su organización tiene un entorno de Office 365 existente, pero el usuario que se suscribe a Power BI no tiene una cuenta de Office 365.
    En este escenario, el usuario tiene una dirección de correo electrónico en el dominio de su organización (por ejemplo, contoso.com), pero todavía no tiene una cuenta de Office 365. En este caso, el usuario puede suscribirse a Power BI y automáticamente se le asigna una cuenta. Esto permite al usuario acceder al servicio Power BI. Por ejemplo, si una empleada llamada Nancy usa su dirección de correo del trabajo (por ejemplo, nancy@contoso.com) para suscribirse, Microsoft agrega automáticamente a Nancy como un usuario en el entorno de Office 365 de Contoso y activa Power BI para esa cuenta.

* **Escenario 3**: Su organización no tiene un entorno de Office 365 conectado a su dominio de correo electrónico.
    No hay ninguna acción administrativa que su organización necesite llevar a cabo para aprovechar las ventajas de Power BI. Los usuarios se agregan a un nuevo directorio de usuario solo en la nube, y tiene la opción de asumir el control como el administrador de inquilinos y administrarlos.

> [!IMPORTANT]
> Si su organización tiene varios dominios de correo y usted prefiere que todas las extensiones de dirección de correo estén en el mismo inquilino, agregue todos los dominios de dirección de correo a un inquilino de Azure Active Directory antes de suscribir ningún usuario. No hay ningún mecanismo automático para mover usuarios entre inquilinos después de haberlos creado. Para obtener más información sobre este proceso, consulte [Si dispongo de varios dominios, ¿puedo controlar el inquilino de Office 365 al que se agregan usuarios?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to) más adelante en este artículo y [Agregar un dominio a Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>¿Cómo puedo impedir que los usuarios se unan a mi inquilino de Office 365 existente?

Hay pasos que puede realizar, como administrador, para impedir que los usuarios se unan a su inquilino de Office 365 existente. Si bloquea el acceso, los intentos de los usuarios para suscribirse no se podrán realizar y se les redirigirá para que se pongan en contacto con el administrador de su organización. No es necesario repetir este proceso si ya ha deshabilitado la distribución automática de licencias (por ejemplo, mediante Office 365 para el ámbito educativo para estudiantes, profesores y docentes).

Use el siguiente script de PowerShell para impedir que los nuevos usuarios se unan a un inquilino administrado. ([Más información sobre PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> El bloqueo del acceso impide que los nuevos usuarios de su organización se suscriban a Power BI. Los usuarios que se suscriben a Power BI antes de deshabilitar nuevas suscripciones para su organización aún conservarán sus licencias. Para quitar un usuario, consulte [¿Cómo quito Power BI para los usuarios que ya están suscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) más adelante en este artículo.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>¿Cómo puedo permitir que los usuarios se unan a mi inquilino de Office 365 existente?

Use el siguiente script de PowerShell para permitir que los nuevos usuarios se unan a un inquilino administrado. ([Más información sobre PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>¿Cómo puedo comprobar si tengo el bloque activado en el inquilino?

Use el siguiente script de PowerShell para verificar la configuración. *AllowEmailVerifiedUsers* debe ser false. ([Más información sobre PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>¿Cómo puedo impedir que mis usuarios existentes comiencen a utilizar Power BI?

La opción de configuración de Azure AD que controla esto es **AllowAdHocSubscriptions**. La mayoría de los inquilinos tienen esta propiedad establecida en true, lo que significa que está habilitada. Si adquirió Power BI a través de un asociado, esta opción podría ser false, lo que significaría que está deshabilitada.

Use el siguiente script de PowerShell para deshabilitar las suscripciones ad hoc. ([Más información sobre PowerShell][1].)

1. Inicie sesión en Azure Active Directory usando sus credenciales de Office 365. La primera línea del siguiente script de PowerShell le pide las credenciales. La segunda línea se conecta a Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Inicio de sesión de Azure Active Directory](media/service-admin-licensing-organization/aad-signin.png)

1. Después de iniciar sesión, ejecute el comando siguiente para ver cómo está configurado actualmente el inquilino.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```
1. Ejecute este comando para habilitar ($true) o deshabilitar ($false) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> La marca AllowAdHocSubscriptions se usa para controlar varias funcionalidades de usuario en su organización, incluida la capacidad para que los usuarios se suscriban al servicio Azure Rights Management. El cambio de esta marca afecta a todas estas funcionalidades.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>¿Cómo puedo permitir a mis usuarios existentes que se suscriban a Power BI?

Para permitir que los usuarios existentes se suscriban a Power BI, ejecute el comando enumerado para la pregunta anterior, pero pase true en lugar de false en el último paso.

## <a name="administration-of-power-bi"></a>Administración de Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>¿Cómo cambiará esto la manera de administrar identidades para usuarios de mi organización hoy?

Hay tres escenarios que se podrían aplicarse a los usuarios de su organización:

* **Escenario 1**: Si su organización ya tiene un entorno de Office 365 existente y todos los usuarios de dicha organización tienen cuentas de Office 365, no se producirá ningún cambio en la forma de administrar la identidad.

* **Escenario 2**: Si su organización ya tiene un entorno de Office 365 existente pero no todos los usuarios de dicha organización tienen cuentas de Office 365, crearemos un usuario en el inquilino y asignaremos licencias basadas en la dirección de correo electrónico profesional o educativa del usuario.

    Esto significa que el número de usuarios que está administrando en cualquier momento determinado crecerá a medida que los usuarios de su organización se suscriben al servicio.

* **Escenario 3**: Si la organización no tiene un entorno de Office 365 conectado al dominio de correo electrónico, no se producirá ningún cambio en la forma de administrar las identidades.

    Los usuarios se agregan a un nuevo directorio de usuario solo en la nube, y tiene la opción de asumir el control como el administrador de inquilinos y administrarlos.

### <a name="how-do-we-manage-power-bi"></a>¿Cómo se administra Power BI?

Power BI proporciona un portal de administración que permite ver estadísticas de uso, proporciona un vínculo al Centro de administración de Office 365 para administrar usuarios y grupos y ofrece la capacidad de controlar toda la configuración de los inquilinos.

Para acceder al portal de administración de Power BI, la cuenta debe estar marcada como **Administrador global** dentro de Office 365 o Azure Active Directory, o que se le haya asignado el rol de administrador del servicio Power BI. Para más información, vea [Descripción del rol de administrador de Power BI](service-admin-role.md) y [Portal de administración de Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>¿Cuál es el proceso para administrar un inquilino creado por Microsoft para mis usuarios?

Cuando un usuario de autoservicio se suscribe a un servicio en la nube que usa Azure AD, se agrega a un directorio de Azure AD no administrado en función de su dominio de correo electrónico. Puede reclamar y administrar el inquilino que se creó mediante un proceso conocido como *adquisición por el administrador*. El tipo de adquisición que realice dependerá de si existe un inquilino administrado asociado a su dominio:

* Utilice una *adquisición interna* para crear otro inquilino administrado para el dominio.

* Utilice una *adquisición externa* para mover el dominio a un inquilino administrado existente.

Para más información, vea cómo [adquirir un directorio no administrado como administrador en Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover).

Al realizar una adquisición externa, el contenido de Power BI creado antes de la adquisición se coloca en un [área de trabajo de archivado de Power BI](service-admin-power-bi-archived-workspace.md). Debe migrar manualmente cualquier contenido que quiera utilizar en el nuevo inquilino.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Si dispongo de varios dominios, ¿puedo controlar el inquilino de Office 365 al que se agregan usuarios?

Si no hace nada, se creará un inquilino para cada dominio y subdominio de correo electrónico del usuario. Si desea que todos los usuarios se encuentren en el mismo inquilino independientemente de sus extensiones de dirección de correo electrónico: Crear un inquilino de destino por adelantado, o use un inquilino existente, y agregue todos los dominios subdominios existentes que desee consolidados dentro de ese inquilino. A partir de ese momento, todos los usuarios cuyas direcciones de correo electrónico terminen en esos dominios y subdominios se unirán automáticamente al inquilino de destino al suscribirse.

> [!IMPORTANT]
> No hay ningún mecanismo automático admitido para mover usuarios entre inquilinos una vez creados. Para obtener información sobre cómo agregar dominios a un solo inquilino de Office 365, consulte [Pasos para comprobar dominio en Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>¿Cómo quito Power BI para los usuarios que ya están suscritos?

Si un usuario se suscribió a Power BI, pero ya no desea que tenga acceso a Power BI, puede quitar la licencia de Power BI para ese usuario.

1. Vaya al [Centro de administración de Office 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. En la barra de navegación izquierda, seleccione **Usuarios** > **Usuarios activos**.

1. Busque el usuario para el que desea quitar la licencia y seleccione su nombre.

    También puede realizar la administración masiva de licencias para los usuarios. Para ello, seleccione varios usuarios y luego **Editar licencias de productos**.

1. En la página de detalles del usuario, junto a **Licencias de productos**, seleccione **Editar**.

1. Establezca **Power BI (gratis)** o **Power BI Pro** en **desactivado**, en función de qué licencia se aplicó a su cuenta.

1. Seleccione **Guardar**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>¿Cómo sé cuándo nuevos usuarios se han unido a mi inquilino?

A los usuarios que se han unido al inquilino como parte de este programa se les asigna una licencia única por la que puede filtrar dentro el panel de usuario activo en el panel de administración. Para crear esta vista, siga estos pasos.

1. Vaya al [Centro de administración de Office 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. En la barra de navegación izquierda, seleccione **Usuarios** > **Usuarios activos**.

1. En el menú **Vistas**, seleccione **Agregar vista personalizada**.

1. Asigne un nombre a la nueva vista y, en **Licencia de producto asignada**, seleccione **Power BI (gratis)** o **Power BI Pro**.

    Solo puede tener una licencia seleccionada por vista. Si tiene tanto la licencia **Power BI (gratis)** como la licencia **Power BI Pro** en su organización, puede crear dos vistas.

1. Escriba cualquier otra condición que desee y después seleccione **Agregar**.

1. Una vez creada la vista, estará disponible en el menú **Vistas**.

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>¿Hay aspectos adicionales para los que debería estar preparado?

Es posible que experimente un aumento en las solicitudes de restablecimiento de contraseña. Para obtener información sobre este proceso, consulte [Restablecer una contraseña de usuario en Office 365](/office365/admin/add-users/reset-passwords).

Puede quitar un usuario del inquilino mediante el proceso estándar en el Centro de administración de Office 365. Sin embargo, si el usuario todavía tiene una dirección de correo electrónico activa de su organización, puede volver a unirse a menos que bloquee todos los usuarios para impedirles que se unan.

### <a name="where-is-my-power-bi-tenant-located"></a>¿Dónde se encuentra mi inquilino de Power BI?

Para obtener información sobre en qué región de datos se encuentra su inquilino de Power BI, vea [¿Dónde se encuentra mi inquilino de Power BI?](service-admin-where-is-my-tenant-located.md)

### <a name="what-is-the-power-bi-sla"></a>¿Qué es el Acuerdo de Nivel de Servicio?

Para obtener información sobre el Acuerdo de Nivel de Servicio de Power BI, vea el artículo [Licensing Terms and Documentation](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) (Documentación y términos de licencia) en la sección **Licensing** (Licencias) del sitio web de licencias de Microsoft.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>¿Cómo controla Power BI la alta disponibilidad y la conmutación por error?

Para obtener información sobre alta disponibilidad y conmutación por error, vea [Power BI high availability, failover, and disaster recovery FAQ](service-admin-failover.md) (Preguntas más frecuentes sobre alta disponibilidad, conmutación por error y recuperación ante desastres en Power BI).

## <a name="security-in-power-bi"></a>Seguridad en Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>¿Cumple Power BI los requisitos de cumplimiento nacionales, regionales y específicos del sector?

Para obtener más información acerca de la compatibilidad de Power BI, consulte el [Centro de confianza de Microsoft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>¿Cómo funciona la seguridad en Power BI?

Power BI se basa en Office 365, que a su vez se basa en los servicios de Azure como Azure Active Directory. Para obtener información general de la arquitectura de Power BI, vea [Seguridad de Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Pasos siguientes

[Portal de administración de Power BI](service-admin-portal.md)  
[Descripción del rol de administrador de Power BI](service-admin-role.md)  
[Registro de autoservicio para Power BI](service-self-service-signup-for-power-bi.md)  
[Adquisición de Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[¿Qué es Power BI Premium?](service-premium.md)  
[Adquisición de Power BI Premium](service-admin-premium-purchase.md)  
[Notas del producto de Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Administración del grupo en Power BI y Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Administración de cuentas de usuario de Office 365](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Administración de grupos de Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview