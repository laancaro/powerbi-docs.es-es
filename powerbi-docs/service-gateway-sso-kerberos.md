---
title: Uso de Kerberos para el inicio de sesión único (SSO) en orígenes de datos locales
description: Configuración de la puerta de enlace con Kerberos para habilitar SSO desde Power BI en los orígenes de datos locales
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 04f67f82552f7915f8ca4fc6e639de3e616c2f8a
ms.sourcegitcommit: 5bd9bd890db9a7f9d5988c81232f40b9b260a96f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55147597"
---
# <a name="use-kerberos-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Uso de Kerberos para el inicio de sesión único (SSO) de Power BI a orígenes de datos locales

Use la [delegación restringida de Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para habilitar la conectividad de inicio de sesión único directa. La habilitación de SSO facilita la tarea de los paneles y los informes de Power BI para actualizar los datos de orígenes locales.

## <a name="supported-data-sources"></a>Orígenes de datos compatibles

Actualmente se admiten estos orígenes de datos:

* SQL Server
* SAP HANA
* SAP BW
* Teradata
* Spark
* Impala

También ofrecemos compatibilidad para SAP HANA con [SAML (Lenguaje de marcado de aserción de seguridad)](service-gateway-sso-saml.md).

### <a name="sap-hana"></a>SAP HANA

Para habilitar SSO para SAP HANA, primero siga estos pasos:

* Asegúrese de que el servidor de SAP HANA ejecuta la versión mínima requerida, que depende del nivel de plataforma de su servidor de SAP HANA:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* En el equipo de puerta de enlace, instale el controlador ODBC de HANA más reciente de SAP.  La versión mínima es HANA ODBC versión 2.00.020.00, de agosto de 2017.

Para obtener más información acerca de cómo instalar y configurar un inicio de sesión único para SAP HANA con Kerberos, vea el tema [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/en-US/1885fad82df943c2a1974f5da0eed66d.html) (Inicio de sesión único con Kerberos) en la Guía de seguridad de SAP HANA y los vínculos de esa página, especialmente la nota de SAP 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory].

## <a name="preparing-for-kerberos-constrained-delegation"></a>Preparación de la delegación restringida de Kerberos

Deben configurarse varios elementos para que la delegación restringida de Kerberos funcione correctamente, incluidos los *nombres principales de servicio* (SPN) y la configuración de delegación de cuentas de servicio.

### <a name="prerequisite-1-install--configure-the-on-premises-data-gateway"></a>Requisito previo 1: instalación y configuración de la puerta de enlace de datos local

Esta versión de la puerta de enlace de datos local admite la actualización en contexto, así como la recepción de la configuración de las puertas de enlace existentes.

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>Requisito previo 2: ejecución del servicio de Windows de puerta de enlace como cuenta de dominio

En una instalación estándar, la puerta de enlace se ejecuta como una cuenta de servicio de la máquina local (en concreto, *NT Service\PBIEgwService*) como se muestra en la siguiente imagen:

![Cuenta de servicio](media/service-gateway-sso-kerberos/service-account.png)

Para habilitar la **delegación restringida de Kerberos**, debe ejecutar la puerta de enlace como una cuenta de dominio, a menos que Azure AD ya esté sincronizado con su Active Directory local (mediante Azure AD DirSync o Azure AD Connect). Si necesita cambiar la cuenta a una cuenta de dominio, consulte [Cambio de la puerta de enlace a una cuenta de dominio](#switching-the-gateway-to-a-domain-account), más adelante en este artículo.

> [!NOTE]
> Si Azure AD DirSync o Azure AD Connect están configurados y las cuentas de usuario están sincronizadas, el servicio de puerta de enlace no necesita realizar búsquedas de AD locales en tiempo de ejecución y puede usar el SID de servicio local (en lugar de requerir una cuenta de dominio) para el servicio de puerta de enlace. Los pasos de configuración de la delegación restringida de Kerberos que se describen en este artículo son los mismos que esa configuración (simplemente se aplican al objeto informático de la puerta de enlace de Active Directory, en lugar de la cuenta de dominio).

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Requisito previo 3: tener derechos de administrador de dominio para configurar los SPN (SetSPN) y la configuración de la delegación restringida de Kerberos

Aunque es técnicamente posible para un administrador de dominio otorgar derechos temporales o permanentes a otra persona para configurar SPN y la delegación de Kerberos sin necesidad de derechos de administrador de dominio, no es el enfoque recomendado. En la sección siguiente, se tratan detenidamente los pasos de configuración necesarios para el **Requisito previo 3**.

## <a name="configuring-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Configuración de la delegación restringida de Kerberos para el origen de datos y la puerta de enlace

Para configurar correctamente el sistema, es necesario configurar o validar los dos elementos siguientes:

1. Si es necesario, configure un SPN para la cuenta de dominio del servicio de puerta de enlace.

2. Configure las opciones de delegación en la cuenta de dominio del servicio de puerta de enlace.

Tenga en cuenta que debe ser un administrador de dominio para realizar esos dos pasos de configuración.

En las siguientes secciones se describen estos pasos.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Configuración de un SPN para la cuenta de servicio de la puerta de enlace

En primer lugar, determine si ya se ha creado un nombre de entidad de seguridad de servicio para la cuenta de dominio que se usa como la cuenta de servicio de la puerta de enlace, pero siguiendo estos pasos:

1. Como administrador de dominio, inicie **Usuarios y equipos de Active Directory**.

2. Haga clic con el botón derecho en el dominio, seleccione **Buscar** y escriba el nombre de la cuenta de servicio de la puerta de enlace

3. En el resultado de la búsqueda, haga clic con el botón derecho en la cuenta de servicio de la puerta de enlace y seleccione **Propiedades**.

4. Si la pestaña **Delegación** está visible en el cuadro de diálogo **Propiedades**, ya se ha creado un SPN y puede pasar a la siguiente subsección sobre cómo configurar la delegación.

    Si no hay pestaña **Delegación** en el cuadro de diálogo **Propiedades**, puede crear manualmente un SPN en dicha cuenta, lo cual agrega la pestaña **Delegación** (esa es la manera más fácil de configurar la delegación). Puede crear un SPN utilizando la [herramienta setspn](https://technet.microsoft.com/library/cc731241.aspx) que viene con Windows (necesita derechos de administrador de dominio para crear el SPN).

    Imagine, por ejemplo, que la cuenta de servicio de la puerta de enlace es "PBIEgwTest\GatewaySvc" y el nombre del equipo que ejecuta el servicio de puerta de enlace es **Machine1**. Para establecer el SPN para la cuenta de servicio de la puerta de enlace para esa máquina en este ejemplo, ejecutaría el comando siguiente:

    ![Establecer el SPN](media/service-gateway-sso-kerberos/set-spn.png)

    Con ese paso completado, podemos continuar con la configuración de las opciones de delegación.

### <a name="configure-delegation-settings-on-the-gateway-service-account"></a>Configuración de los valores de delegación en la cuenta de servicio de la puerta de enlace

El segundo requisito de la configuración es la configuración de la delegación en la cuenta de servicio de la puerta de enlace. Hay varias herramientas que puede usar para realizar estos pasos. En este artículo, vamos a usar **Usuarios y equipos de Active Directory**, que es un complemento de Microsoft Management Console (MMC) que puede usar para administrar y publicar información en el directorio. Está disponible en los controladores de dominio de forma predeterminada. También puede habilitarlo a través de la configuración de las **Características de Windows** en otros equipos.

Es necesario configurar la **delegación restringida de Kerberos** con tránsito de protocolo. Con la delegación restringida, debe ser explícito acerca de los servicios que quiere delegar. Por ejemplo, solo SQL Server o el servidor de SAP HANA aceptarán llamadas de delegación de la cuenta de servicio de la puerta de enlace.

En esta sección se da por supuesto que ya ha configurado los SPN de los orígenes de datos subyacentes (como SQL Server, SAP HANA, Teradata, Spark, etc.). Para obtener información sobre cómo configurar los SPN del servidor del origen de datos, consulte la documentación técnica para el servidor de bases de datos respectivo. También puede buscar en la entrada de blog que describe [ *¿Qué SPN requiere la aplicación?*](https://blogs.msdn.microsoft.com/psssql/2010/06/23/my-kerberos-checklist/)

En los pasos siguientes, se asume que disponemos de un entorno local con dos equipos: un equipo de puerta de enlace y un servidor de bases de datos que ejecuta SQL Server. Para este ejemplo, también asumiremos la configuración y los nombres siguientes:

* Nombre de la máquina de la puerta de enlace: **PBIEgwTestGW**
* Cuenta de servicio de puerta de enlace: **PBIEgwTest\GatewaySvc** (nombre para mostrar de la cuenta: Gateway Connector)
* Nombre de la máquina del origen de datos de SQL Server: **PBIEgwTestSQL**
* Cuenta de servicio del origen de datos de SQL Server: **PBIEgwTest\SQLService**

Con esos nombres y configuración de ejemplo, los pasos de configuración son los siguientes:

1. Con derechos de administrador de dominio, inicie **Usuarios y equipos de Active Directory**.

2. Haga clic con el botón derecho en la cuenta de servicio de la puerta de enlace (**PBIEgwTest\GatewaySvc**) y seleccione **Propiedades**.

3. Seleccione la ficha **Delegación**.

4. Seleccione **Confiar en este equipo para la delegación solo a los servicios especificados.**

5. Seleccione **Usar cualquier protocolo de autenticación.**

6. En **Servicios en los que esta cuenta puede presentar credenciales delegadas**, seleccione **Agregar**.

7. En el cuadro de diálogo nuevo, seleccione **Usuarios o equipos**.

8. Escriba la cuenta de servicio para el servicio de base de datos de SQL Server (**PBIEgwTest\SQLService**) y seleccione **Aceptar**.

9. Seleccione el SPN que ha creado para el servidor de base de datos. En nuestro ejemplo, el SPN comenzará con **MSSQLSvc**. Si ha agregado tanto el SPN de FQDN como el de NetBIOS, seleccione ambos. Es posible que solo vea uno.

10. Seleccione **Aceptar**. Ahora debería ver el SPN en la lista.

11. Si quiere, puede seleccionar **Expandido** para mostrar el SPN de FQDN y el de NetBIOS.

12. El cuadro de diálogo debe ser similar al siguiente si ha seleccionado **Expandido**. Seleccione **Aceptar**.

    ![Propiedades del conector de puerta de enlace](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

Por último, en la máquina que ejecuta el servicio de puerta de enlace (**PBIEgwTestGW** en nuestro ejemplo), la cuenta de servicio de la puerta de enlace debe tener la directiva local "Suplantar a un cliente tras la autenticación". Puede realizar y comprobar esto con el Editor de directivas de grupo local (**gpedit**).

1. En el equipo de puerta de enlace, ejecute: *gpedit.msc*.

1. Vaya a **Directiva de equipo Local > Configuración del equipo > Configuración de Windows > Configuración de seguridad > Directivas locales > Asignación de derechos de usuario**, como se muestra en la siguiente imagen.

    ![Asignación de derechos de usuario](media/service-gateway-sso-kerberos/user-rights-assignment.png)

1. En la lista de directivas en **Asignación de derechos de usuario**, seleccione **Suplantar a un cliente tras la autenticación**.

    ![Suplantación de un cliente](media/service-gateway-sso-kerberos/impersonate-client.png)

    Haga clic con el botón derecho y abra las **Propiedades** de **Suplantar a un cliente tras la autenticación** y compruebe la lista de cuentas. Debe incluir la cuenta de servicio de la puerta de enlace (**PBIEgwTest\GatewaySvc**).

1. En la lista de directivas en **Asignación de derechos de usuario**, seleccione **Actuar como parte del sistema operativo (SeTcbPrivilege)**. Asegúrese también de que la cuenta de servicio de la puerta de enlace está incluida en la lista de cuentas.

1. Reinicie el proceso del servicio de la **puerta de enlace de datos local**.

Si usa SAP HANA, se recomienda seguir estos pasos adicionales, que pueden comportar una pequeña mejora de rendimiento.

1. En el directorio de instalación de la puerta de enlace, busque y abra este archivo de configuración: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

1. Busque la propiedad *FullDomainResolutionEnabled* y cambie su valor a *True*.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

## <a name="running-a-power-bi-report"></a>Ejecución de un informe de Power BI

Después de completar todos los pasos de configuración que se describen anteriormente en este artículo, puede utilizar la página **Administrar puerta de enlace** en Power BI para configurar el origen de datos. Posteriormente, en su **Configuración avanzada**, habilite SSO y publique los enlaces de los conjuntos de datos y los informes al origen de datos.

![Configuración avanzada](media/service-gateway-sso-kerberos/advanced-settings.png)

Esta configuración funciona en la mayoría de los casos. Sin embargo, con Kerberos puede haber distintas configuraciones en función de su entorno. Si todavía no se pudo cargar el informe, debe ponerse en contacto con el administrador de dominio para investigar en profundidad.

## <a name="switching-the-gateway-to-a-domain-account"></a>Cambio de la puerta de enlace a una cuenta de dominio

Anteriormente en este artículo, analizamos el cambio de la puerta de enlace de una cuenta de servicio local para que se ejecute como una cuenta de dominio, usando la interfaz de usuario **Puerta de enlace de datos local**. Estos son los pasos necesarios para hacerlo.

1. Inicie la herramienta de configuración de la **puerta de enlace de datos local**.

   ![Aplicación de escritorio de puerta de enlace](media/service-gateway-sso-kerberos/gateway-desktop-app.png)

2. Seleccione el botón **Inicio de sesión** situado en la página principal e inicie sesión con su cuenta de Power BI.

3. Una vez completado el inicio de sesión, seleccione la pestaña **Configuración del servicio**.

4. Seleccione **Cambiar cuenta** para iniciar el tutorial guiado, tal como se muestra en la imagen siguiente.

   ![Cambiar cuenta](media/service-gateway-sso-kerberos/change-account.png)

## <a name="configuring-sap-bw-for-sso"></a>Configuración de SAP BW para SSO

Ahora que comprende el funcionamiento de Kerberos con una puerta de enlace, puede configurar SSO para SAP Business Warehouse (SAP BW). En los siguientes pasos se asume que está [preparado para la delegación restringida de Kerberos](#preparing-for-kerberos-constrained-delegation), tal como se describe anteriormente en este artículo.

Esta guía trata de ser lo más completa posible. Si ya ha completado algunos de estos pasos, puede omitirlos: por ejemplo, ya ha creado un usuario del servicio para el servidor BW y le ha asignado un nombre de entidad de seguridad de servicio (SPN), o bien ya ha instalado la biblioteca gsskrb5.

### <a name="setup-gsskrb5-on-client-machines-and-the-bw-server"></a>Configuración de gsskrb5 en equipos clientes y en el servidor BW

> [!NOTE]
> SAP ya no ofrece soporte técnico activo para gsskrb5. Para obtener más información, consulte la [nota 352295 de SAP](https://launchpad.support.sap.com/#/notes/352295). Tenga en cuenta también que gsskrb5 no permite conexiones SSO entre la puerta de enlace de datos y los servidores de mensajería BW. Solo es posible establecer la conexión con los servidores de aplicaciones BW.

gsskrb5 debe estar en uso en el cliente y el servidor para completar una conexión de inicio de sesión único a través de la puerta de enlace. La biblioteca común de criptografía (sapcrypto) no se admite actualmente.

1. Descargue gsskrb5/gx64krb5 desde la [nota de SAP 2115486](https://launchpad.support.sap.com/) (se requiere el s-usuario de SAP). Asegúrese de que tiene al menos la versión 1.0.11.x de gsskrb5.dll y gx64krb5.dll.

1. Coloque la biblioteca en una ubicación en el equipo de puerta de enlace a la cual pueda acceder la instancia de puerta de enlace (y también la GUI de SAP, si quiere probar la conexión SSO con el inicio de sesión o la GUI de SAP).

1. Coloque otra copia en equipo servidor de BW en una ubicación a la cual pueda acceder el servidor de BW.

1. En los equipos cliente y servidor, establezca las variables de entorno SNC\_LIB y SNC\_LIB\_64 para que apunten a las ubicaciones de gsskrb5.dll y gx64krb5.dll, respectivamente.

### <a name="create-a-bw-service-user-and-enable-snc-communication-using-gsskrb5-on-the-bw-server"></a>Creación de un usuario del servicio de BW y habilitación de la comunicación SNC mediante gsskrb5 en el servidor BW

Además de la configuración de puerta de enlace que ya ha realizado, hay algunos pasos adicionales específicos de SAP BW. La sección [**Configuración de los valores de delegación en la cuenta de servicio de la puerta de enlace**](#configure-delegation-settings-on-the-gateway-service-account) de la documentación asume que ya se han configurado los SPN de los orígenes de datos subyacentes. Para completar esta configuración para SAP BW:

1. En un servidor del Controlador de dominio de Active Directory, cree un usuario de servicio (inicialmente solo un usuario de Active Directory sin formato) para el servidor de aplicaciones de BW en su entorno de Active Directory. A continuación, asígnele un SPN.

    SAP recomienda iniciar SPN con SAP/, pero también deben admitirse otros prefijos como HTTP/. Lo que viene después de SAP/ depende de usted; una opción es usar el nombre del usuario del servicio del servidor de BW. Por ejemplo, si crea BWServiceUser@\<DOMINIO\> como usuario del servicio, puede usar el SPN SAP/BWServiceUser. Una manera de establecer la asignación de SPN es el comando setspn. Por ejemplo, para establecer el SPN en el usuario del servicio que acabamos de crear, ejecutaremos el comando siguiente desde una ventana Comandos en un equipo del controlador de dominio: `setspn -s SAP/ BWServiceUser DOMAIN\ BWServiceUser`. Para más información, consulte la documentación sobre SAP BW.

1. Otorgue al usuario del servicio acceso al servidor de aplicaciones de BW:

    1. En el equipo servidor de BW, agregue el usuario del servicio al grupo de administradores locales para el servidor de BW: abra el programa de administración de equipos y haga doble clic en el grupo de administradores locales para el servidor.

        ![Administración de equipos](media/service-gateway-sso-kerberos/computer-management.png)

    1. Haga doble clic en el grupo de administradores locales y, a continuación, seleccione **Agregar** para agregar el usuario del servicio de BW al grupo. Use el botón **Comprobar nombres** para asegurarse de que ha escrito correctamente el nombre. Seleccione **Aceptar**.

1. Establezca el usuario del servicio del servidor de BW como el usuario que inicia el servicio del servidor de BW en el equipo servidor de BW.

    1. Abra el programa "Ejecutar" y escriba "Services.msc". Busque el servicio que corresponde a la instancia de servidor de aplicaciones de BW. Haga clic con el botón derecho en él y seleccione **Propiedades**.

        ![Propiedades del servidor](media/service-gateway-sso-kerberos/server-properties.png)

    1. Cambie a la pestaña **Inicio de sesión** y cambie el usuario al usuario del servicio de BW, tal como se especifica. Escriba la contraseña del usuario y seleccione **Aceptar**.

1. Inicie sesión el servidor en el inicio de sesión o la GUI de SAP y establezca los siguientes parámetros de perfil mediante la transacción RZ10:

    1. Establezca el parámetro de perfil snc/identity/as en p:\<el usuario del servicio de BW que ha creado\>, como p:BWServiceUser@MYDOMAIN.COM. Observe la p: que precede al UPN del usuario del servicio; no es p:CN= como cuando se usa la biblioteca Common Crypto como la biblioteca de SNC.

    1. Establezca el parámetro de perfil snc/gssapi\_lib en \<ruta de acceso a gsskrb5.dll/gx64krb5.dll en el equipo servidor (la biblioteca que se va a usar depende del valor de bits del sistema operativo)\>. Recuerde colocar la biblioteca en una ubicación a la cual pueda tener acceso el servidor de aplicaciones de BW.

    1. Establezca también los siguientes parámetros de perfil adicionales, cambiando los valores según sea necesario para ajustarse a sus necesidades. Tenga en cuenta que las últimas cinco opciones permiten a los clientes conectarse al servidor de BW mediante el inicio de sesión o la GUI de SAP sin necesidad de tener SNC configurado.

        | **Configuración** | **Valor** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Establezca la propiedad snc/enable en 1.

1. Después de establecer estos parámetros de perfil, abra la consola de administración de SAP en el equipo servidor y reinicie la instancia de BW. Si no se inicia el servidor, vuelva a comprobar que ha establecido correctamente los parámetros de perfil. Para obtener más información sobre la configuración de parámetros de perfil, vea la [documentación de SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). También puede consultar nuestra información de solución de problemas más adelante en esta sección, si tiene problemas.

### <a name="map-a-bw-user-to-an-active-directory-user"></a>Asignación de un usuario de BW a un usuario de Active Directory

Asigne un usuario de Active Directory a un usuario del servidor de aplicaciones de SAP BW y pruebe la conexión SSO en el inicio de sesión o la GUI de SAP.

1. Inicie sesión el servidor de BW mediante el inicio de sesión o la GUI de SAP. Ejecute transacciones SU01.

1. Para **Usuario**, escriba el usuario de BW para el cual quiere habilitar las conexiones SSO (en la captura de pantalla anterior se establecen los permisos para BIUSER). Seleccione el icono **Editar** situado cerca de la parte superior izquierda de la ventana de inicio de sesión de SAP (la imagen de un lápiz).

    ![Mantenimiento del usuario](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Seleccione la pestaña **SNC**. En el cuadro de entrada del nombre de SNC, escriba p:\<usuario de active directory\>@\<dominio\>. Tenga en cuenta la p: obligatoria debe preceder al UPN del usuario de Active Directory. El usuario de Active Directory que especifique debe pertenecer a la persona u organización para la cual quiere habilitar el acceso SSO al servidor de aplicaciones de BW. Por ejemplo, si quiere habilitar el acceso SSO para el usuario [testuser@TESTDOMAIN.COM](mailto:testuser@TESTDOMAIN.COM), escriba p:testuser@TESTDOMAIN.COM.

    ![Mantenimiento de usuarios](media/service-gateway-sso-kerberos/maintain-users.png)

1. Seleccione el icono de guardar (el disquete cerca de la esquina superior izquierda de la pantalla).

### <a name="test-sign-in-using-sso"></a>Prueba del inicio de sesión con SSO

Compruebe que puede iniciar sesión en el servidor mediante el inicio de sesión o la GUI de SAP mediante SSO como el usuario de Active Directory para el cual acaba de habilitar el acceso.

1. Inicie sesión en un equipo donde esté instalado el inicio de sesión de SAP *como el usuario de Active Directory para el cual acaba de habilitar el acceso SSO* e inicie la GUI o el inicio de sesión de SAP. Cree una nueva conexión.

1. En la ventana para **Crear una nueva entrada del sistema**, seleccione el **Sistema especificado del usuario** y seleccione **Siguiente**.

    ![Nueva entrada del sistema](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Rellene los detalles adecuados en la siguiente página, incluido el servidor de aplicaciones, el número de instancia y el ID del sistema y, a continuación, seleccione **Finalizar**.

1. Haga clic con el botón derecho en la conexión nueva y seleccione **Propiedades**. Seleccione la pestaña **Red**. En la ventana del **Nombre de SNC**, escriba p:\<UPN del usuario del servicio de BW\>, como p:BWServiceUser@MYDOMAIN.COM y luego seleccione **Aceptar**.

    ![Propiedades de la entrada del sistema](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Haga doble clic en la conexión que acaba de crear para intentar una conexión SSO al servidor BW. Si esta conexión se realiza correctamente, continúe con el paso siguiente. En caso contrario, revise los pasos anteriores en este documento para asegurarse de que se ha completado correctamente, o consulte la siguiente sección de solución de problemas. Tenga en cuenta que si no se puede conectar al servidor de BW mediante SSO en este contexto, no podrá conectarse al servidor de BW mediante SSO en el contexto de la puerta de enlace.

### <a name="troubleshoot-installation-and-connections"></a>Solución de problemas de instalación y de las conexiones

Si detecta algún problema, siga estos pasos para solucionar problemas de instalación de gsskrb5 y de las conexiones SSO desde el inicio de sesión o la GUI de SAP.

1. La visualización de los registros del servidor (...work\dev\_w0 en el equipo del servidor) puede ser útil para solucionar los errores que se producen al completar los pasos de configuración de gsskrb5, especialmente si el servidor de BW no se inicia tras cambiar los parámetros de perfil.

1. Si no puede iniciar el servicio de BW debido a un "error de inicio de sesión", quizás haya proporcionado una contraseña incorrecta al establecer el usuario de BW utilizado para el inicio. Compruebe la contraseña iniciando sesión en un equipo en el entorno de Active Directory como usuario del servicio de BW.

1. Si recibe errores relacionados con las credenciales de SQL que impiden que se inicie el servidor, compruebe que se le ha concedido el acceso de usuario del servicio a la base de datos de BW.

1. "(GSS-API) El destino especificado no es accesible o es desconocido": normalmente significa que tiene un nombre de SNC incorrecto especificado. Asegúrese de usar "p:" únicamente, no "p:CN=" o cualquier otra descripción en la aplicación cliente, que no sea el UPN del usuario del servicio.

1. "(GSS-API) Se ha suministrado un nombre no válido": asegúrese de que "p:" está en el valor del parámetro de perfil de identidad SNC del servidor.

1. "(Error de SNC) No se ha podido encontrar el módulo especificado": normalmente se debe a que gsskrb5.dll/gx64krb5.dll está situado en algún lugar que requiere privilegios elevados (derechos de administrador) para el acceso.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Adición de entradas del Registro a la máquina de puerta de enlace

Agregue las entradas del registro necesarias en el registro del equipo en el cual está instalada la puerta de enlace.

1. En una ventana Comandos, ejecute los comandos siguientes:

    1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

    1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="set-configuration-parameters-on-the-gateway-machine"></a>Definición de los parámetros de configuración de la máquina de puerta de enlace

Hay dos opciones para establecer los parámetros de configuración, en función de si Azure AD DirSync está configurado para que los usuarios puedan iniciar sesión en el servicio Power BI como un usuario de Azure AD.

Si Azure AD DirSync está configurado, siga estos pasos.

1. Abra el archivo de configuración de puerta de enlace principal *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll*. Este archivo se almacena, de forma predeterminada, en *C:\Archivos de programa\Puerta de enlace de datos local*.

1. Asegúrese de que la propiedad **FullDomainResolutionEnabled** está establecida en True y, **SapHanaSsoRemoveDomainEnabled**, en False.

1. Guarde el archivo de configuración.

1. Reinicie el servicio Puerta de enlace en la pestaña Servicios del Administrador de tareas (haga clic con el botón derecho en Reiniciar).

    ![Reinicio de una puerta de enlace](media/service-gateway-sso-kerberos/restart-gateway.png)

Si Azure AD DirSync no está configurado, siga estos pasos para **cada usuario del servicio Power BI que desee asignar a un usuario de Azure AD**. Estos pasos sirven para vincular manualmente un usuario del servicio Power BI a un usuario de Active Directory con permisos para iniciar sesión en BW.

1. Abra el archivo de configuración de puerta de enlace principal Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll. Este archivo se almacena, de forma predeterminada, en C:\Archivos de programa\Puerta de enlace de datos local.

1. Establezca **ADUserNameLookupProperty** en msDS-cloudExtensionAttribute1 y **ADUserNameReplacementProperty** en SAMAccountName. Guarde el archivo de configuración.

1. Reinicie el servicio Puerta de enlace a través de la pestaña **Servicios** del Administrador de tareas (haga clic con el botón derecho en **Reiniciar**).

    ![Reinicio de una puerta de enlace](media/service-gateway-sso-kerberos/restart-gateway.png)

1. Establezca la propiedad msDS-cloudExtensionAttribute1 del usuario de Active Directory que ha asignado a un usuario de BW en el usuario del servicio Power BI para el que quiere habilitar el SSO de Kerberos. Una forma de establecer la propiedad msDS-cloudExtensionAttribute1 es mediante el complemento de MMC Usuarios y equipos de Active Directory (tenga en cuenta que también se pueden utilizar otros métodos).

    1. Inicie sesión como usuario administrador en un equipo del controlador de dominio.

    1. Abra la carpeta **Usuarios** en la ventana del complemento y haga doble clic en el usuario de Active Directory que ha asignado a un usuario de BW.

    1. Seleccione la pestaña **Editor de atributos**.

        Si no ve esta pestaña, deberá buscar para obtener instrucciones sobre cómo habilitarla o utilizar otro método para establecer la propiedad msDS-cloudExtensionAttribute1. Seleccione uno de los atributos y, a continuación, la tecla "m" para ir a las propiedades de Active Directory que empiezan por "m". Busque la propiedad msDS-cloudExtensionAttribute1 y haga doble clic en ella. Establezca el valor en el nombre de usuario que se utilizará para iniciar sesión en el servicio Power BI, con el formato YourUser@YourDomain.

    1. Seleccione **Aceptar**.

        ![Edición de atributo](media/service-gateway-sso-kerberos/edit-attribute.png)

    1. Seleccione **Aplicar**. Compruebe que se ha establecido el valor correcto en la columna Valor.

### <a name="add-a-new-bw-application-server-data-source-to-the-power-bi-service"></a>Adición de un nuevo origen de datos de servidor de aplicaciones de BW al servicio Power BI

Para agregar el origen de datos de BW a la puerta de enlace, siga las instrucciones que aparecen anteriormente en este artículo acerca de la [ejecución de un informe](#running-a-power-bi-report).

1. En la ventana de configuración del origen de datos, especifique el **nombre de host**, el **número del sistema** y el **ID de cliente** del servidor de aplicaciones tal como lo haría para iniciar sesión el servidor de BW desde Power BI Desktop. Para el **Método de autenticación**, seleccione **Básico**.

1. En el campo **Nombre de asociado de SNC**, escriba p: \<el SPN asignado al usuario del servicio BW\>. Por ejemplo, si el SPN es SAP/BWServiceUser@MYDOMAIN.COM, debe escribir p:SAP/BWServiceUser@MYDOMAIN.COM en el campo **Nombre de asociado de SNC**.

1. Para la biblioteca de SNC, seleccione SNC\_LIB o SNC\_LIB\_64.

1. El **Nombre de usuario** y la **Contraseña** deben ser el nombre de usuario y la contraseña de un usuario de Active Directory con permiso para iniciar sesión en el servidor de BW mediante SSO (un usuario de Active Directory que se ha asignado a un usuario de BW mediante la transacción SU01). Estas credenciales se usarán solo si el cuadro para **Usar SSO mediante Kerberos para las consultas de DirectQuery** *no*está activado.

1. Seleccione el cuadro **Usar SSO mediante Kerberos para las consultas de DirectQuery** y seleccione **Aplicar**. Si la conexión de prueba no es correcta, compruebe que los pasos de instalación y configuración anteriores se hayan completado correctamente.

    La puerta de enlace siempre usa las credenciales que escribió para establecer una conexión de prueba con el servidor y para realizar actualizaciones programadas de informes basados en la importación. La puerta de enlace solo intenta establecer una conexión de inicio de sesión único si el cuadro **Usar SSO mediante Kerberos para las consultas de DirectQuery** está seleccionado, y el usuario accede a un conjunto de datos o a un informe basado en DirectQuery.

### <a name="test-your-setup"></a>Comprobación de la configuración

Publique un informe de DirectQuery de Power BI Desktop al servicio Power BI para probar la configuración. Asegúrese de haber iniciado sesión en el servicio Power BI como un usuario de Azure AD o como un usuario asignado a la propiedad msDS-cloudExtensionAttribute1 de un usuario de Azure AD. Si la configuración se ha completado correctamente, debe poder crear un informe basado en el conjunto de datos publicado en el servicio Power BI y extraer datos mediante los objetos visuales del informe.

### <a name="troubleshooting-gateway-connectivity-issues"></a>Solución de problemas de conectividad de la puerta de enlace

1. Compruebe los registros de la puerta de enlace. Abra la aplicación de configuración de puerta de enlace, seleccione **Diagnósticos** y seleccione **Exportar registros**. Los errores más recientes estarán en la parte inferior de los archivos de registro que examine.

    ![Diagnósticos de la puerta de enlace](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Active el seguimiento de BW y revise los archivos de registro generados. Hay varios tipos diferentes de seguimiento de BW disponibles. Para obtener más información, consulte la documentación de SAP.

## <a name="errors-from-an-insufficient-kerberos-configuration"></a>Errores de una configuración de Kerberos incompleta

Si el servidor de base de datos y la puerta de enlace subyacentes no están configurados correctamente para la **delegación restringida de Kerberos**, puede recibir el mensaje de error siguiente:

![Error al cargar datos](media/service-gateway-sso-kerberos/load-data-error.png)

Y los detalles técnicos asociados con el mensaje de error (DM_GWPipeline_Gateway_ServerUnreachable) pueden ser similares a los siguientes:

![El servidor es inaccesible](media/service-gateway-sso-kerberos/server-unreachable.png)

El resultado es que la puerta de enlace no pudo suplantar al usuario de origen correctamente y el intento de conexión a la base de datos produjo un error.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la **Puerta de enlace de datos local** y **DirectQuery**, consulte los recursos siguientes:

* [On-premises Data Gateway (Puerta de enlace de datos local)](service-gateway-onprem.md)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)