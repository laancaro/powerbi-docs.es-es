---
title: 'Uso de Proxy de aplicación web y Servicios de federación de Active Directory: Power BI Report Server'
description: Obtenga información sobre cómo usar Proxy de aplicación web (WAP) y Servicios de federación de Active Directory (AD FS) para conectarse a Power BI Report Server y SQL Server Reporting Services (SSRS) 2016 y versiones posteriores.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 2caa96aceef90ad1d25a521cbf4a3f699a2a64e0
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76042449"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Uso de Proxy de aplicación web y Servicios de federación de Active Directory: Power BI Report Server

En este artículo se explica cómo usar Proxy de aplicación web (WAP) y Servicios de federación de Active Directory (AD FS) para conectarse a Power BI Report Server y SQL Server Reporting Services (SSRS) 2016 y versiones posteriores. A través de esta integración, los usuarios que están fuera de la red corporativa pueden acceder a sus informes de Power BI Report Server y Reporting Services desde sus exploradores cliente y estar protegidos mediante la autenticación previa de AD FS. Para las aplicaciones móviles de Power BI, también debe [configurar OAuth para conectarse a Power BI Report Server y SSRS](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Requisitos previos

### <a name="domain-name-services-dns-configuration"></a>Configuración de servicios de nombres de dominio (DNS)

- Determine la dirección URL pública a la que se conectará el usuario. Puede tener un aspecto similar al siguiente ejemplo: `https://reports.contosolab.com`.
- Configure el registro DNS para que el nombre de host, `reports.contosolab.com`, por ejemplo, apunte a la dirección IP pública del servidor proxy de aplicación web (WAP).
- Configure un registro DNS público para el servidor de AD FS. Por ejemplo, es posible que haya configurado el servidor de AD FS con la siguiente dirección URL: `https://adfs.contosolab.com`.
- Configure el registro DNS para que apunte a la dirección IP pública del servidor proxy de aplicación web (WAP), por ejemplo `adfs.contosolab.com`. Se publica como parte de la aplicación WAP.

### <a name="certificates"></a>Certificados

Deberá configurar los certificados de la aplicación de WAP y del servidor AD FS. Ambos certificados deben formar parte de una entidad de certificación válida que reconozcan sus máquinas.

## <a name="1-configure-the-report-server"></a>1. Configurar el servidor de informes

Debemos asegurarnos de que tenemos un nombre de entidad de seguridad de servicio (SPN). El SPN válido permite que se produzca la autenticación Kerberos apropiada y habilita el servidor de informes para la autenticación de negociación.

### <a name="service-principal-name-spn"></a>Nombre de entidad de seguridad de servicio (SPN)

El SPN es un identificador único para un servicio que usa la autenticación Kerberos. Asegúrese de que tiene un SPN de HTTP apropiado para el servidor de informes.

Para obtener información sobre cómo configurar el nombre de entidad de seguridad de servicio (SPN) correcto para el servidor de informes, consulte [Registrar un nombre principal de servicio (SPN) para un servidor de informes](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Habilitar la autenticación Negociar

Para permitir que un servidor de informes use la autenticación Kerberos, debe configurar el tipo de autenticación del servidor de informes como RSWindowsNegotiate. Configúrelo en el archivo rsreportserver.config.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Para obtener más información, consulte [Modificar un archivo de configuración de Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) y [Configurar la autenticación de Windows en el servidor de informes](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Configurar Servicios de federación de Active Directory (AD FS)

Tendrá que configurar AD FS en un servidor de Windows 2016 en su entorno. Para ello, puede usar el Administrador del servidor y seleccionar Agregar roles y características en Administrar. Para obtener más información, consulte [Servicios de federación de Active Directory](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services).

En el servidor de AD FS, mediante la aplicación de administración de AD FS, complete estos pasos.

1. Haga clic con el botón derecho en **Veracidades de usuarios de confianza** > **Agregar relación de confianza para usuario autenticado**.

    ![Agregar relaciones de confianza para usuario autenticado](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Siga los pasos en el Asistente para **agregar relación de confianza para usuario autenticado**.

    Elija la opción **No compatible con notificaciones** para usar la seguridad integrada de Windows como mecanismo de autenticación.

    ![Bienvenido al Asistente para agregar relación de confianza para usuario autenticado](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Escriba el nombre que prefiera en **Especificar nombre para mostrar** y seleccione **Siguiente**.
    Agregue el identificador de relación de confianza para usuario autenticado: `<ADFS\_URL>/adfs/services/trust`

    Por ejemplo: `https://adfs.contosolab.com/adfs/services/trust`

    ![Servidor de informes](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Elija la **directiva de control de acceso** que se adapte a las necesidades de su organización y seleccione **Siguiente**.

    ![Elegir control de acceso](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Seleccione **Siguiente** y, a continuación, seleccione **Finalizar** para completar el Asistente para **agregar relación de confianza para usuario autenticado**.

    Al completarse, las propiedades de las veracidades de usuarios de confianza deben tener el aspecto siguiente.

    ![Veracidades de usuarios de confianza](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Configurar Proxy de aplicación web (WAP)

Deberá habilitar el rol de Windows Web Application Proxy (rol) en un servidor de su entorno. Debe tratarse de un servidor de Windows 2016. Para obtener más información, consulte [Web Application Proxy in Windows Server 2016 (Proxy de aplicación web en Windows Server 2016)](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) y [Publishing Applications using AD FS Preauthentication (Publicar aplicaciones usando la autenticación previa de AD FS)](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Configuración de la delegación restringida

Para realizar la transición de la autenticación de Forms a la autenticación de Windows, es necesario usar la delegación restringida con transición de protocolo. Este paso forma parte de la configuración de Kerberos. Ya hemos definido el SPN del servidor de informes en la configuración del servidor de informes.

Es necesario configurar la delegación restringida en la cuenta de equipo del servidor WAP dentro de Active Directory. Puede que tenga que trabajar con un administrador de dominio si no tiene derechos en Active Directory.

Para configurar la delegación limitada, siga estos pasos.

1. En un equipo que tenga instaladas las herramientas de Active Directory, inicie **Usuarios y equipos de Active Directory**.
2. Busque la cuenta de equipo para el servidor WAP. De forma predeterminada, estará en el contenedor de **equipos**.
3. Haga clic con el botón derecho en el servidor WAP y vaya a **Propiedades**.
4. En la pestaña **Delegación**, seleccione **Confiar en este equipo para la delegación solo a los servicios especificados** y, después, **Usar cualquier protocolo de autenticación**.

    ![Confiar en este equipo](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Esta opción configura la delegación restringida para esta cuenta de equipo del servidor WAP. Después, es necesario especificar los servicios que se pueden delegar en esta máquina.
2. Seleccione **Agregar** en el cuadro de servicios.

    ![Agregar relación de confianza de AD FS](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Seleccione **Usuarios o equipos**.
2. Escriba la cuenta de servicio que usa para el servidor de informes. Esta cuenta es la misma que usó para agregar el SPN de HTTP en la sección de [configuración del servidor de informes](#1-configure-the-report-server) anterior. 

3. Seleccione el SPN de HTTP para el servidor de informes y, a continuación, seleccione **Aceptar**.

    > [!NOTE]
    > Puede que solo vea el SPN de NetBIOS. Realmente seleccionará los SPN de NetBIOS y FQDN si existen ambos.

1. Al activar la casilla **Expandido**, el resultado debería ser similar al siguiente ejemplo.

    ![Propiedades WAP](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Agregar la aplicación WAP

1. En el servidor Proxy de aplicación web, abra la consola de **administración de acceso remoto** y seleccione **Proxy de aplicación web** en el panel de navegación. 

2. En el panel **Tareas**, seleccione **Publicar**.

2. En la página principal, seleccione **Siguiente**.

    ![Bienvenido del Asistente para publicar](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. En la página **Autenticación previa**, seleccione **Servicios de federación de Active Directory (AD FS)** y, a continuación, seleccione **Siguiente**.

    ![Autorización previa](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Seleccione la autenticación previa de **Web y MSOFBA**, ya que vamos a configurar solo el acceso del explorador para el servidor de informes y no el acceso a aplicaciones móviles.

    ![Clientes compatibles](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Agregue el **usuario de confianza** que creamos en el servidor de AD FS como se muestra a continuación y, a continuación, seleccione **Siguiente**.

    ![Usuario de confianza del Asistente para publicar](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. En la sección **Dirección URL externa**, escriba la dirección URL accesible públicamente configurada en el servidor WAP. Agregue la dirección URL configurada con el servidor de informes (Administrador de configuración del servidor de informes) como se muestra a continuación en la sección **Dirección URL del servidor back-end**. Agregue el SPN del servidor de informes en la sección **Dirección SPN del servidor back-end**.

    ![Configuración de la publicación](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Seleccione **Siguiente** y **Publicar**.
8. Ejecute el siguiente comando de PowerShell para comprobar la configuración de WAP.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![Comando de PowerShell](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Conexión al servidor de informes a través del explorador

A continuación, puede obtener acceso a la dirección URL WAP pública, por ejemplo, `https://reports.contosolab.com/ReportServer` para el servicio web y `https://reports.contosolab.com/Reports` para el portal web desde el explorador. Cuando se haya autenticado correctamente, podrá ver los informes.

![Inicio de sesión de AD FS](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Pasos siguientes

* [Configurar OAuth para conectarse a Power BI Report Server y a SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[¿Qué es Power BI Report Server?](get-started.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

