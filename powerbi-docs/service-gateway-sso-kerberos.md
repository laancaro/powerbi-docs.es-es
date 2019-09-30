---
title: 'Configuración del SSO: Kerberos'
description: Configuración de la puerta de enlace con Kerberos para habilitar SSO desde Power BI en los orígenes de datos locales
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9958059fcf0d86323fc95f44f6fcfcb08fe7b52b
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71100438"
---
# <a name="configure-kerberos-based-sso-from-power-bi-service-to-on-premises-data-sources"></a>Configuración del SSO basado en Kerberos desde el servicio Power BI a los orígenes de datos locales

Use la [delegación restringida de Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para habilitar la conectividad directiva del SSO. La habilitación de SSO facilita la tarea de los paneles y los informes de Power BI para actualizar los datos de orígenes locales.

Deben configurarse varios elementos para que la delegación restringida de Kerberos funcione correctamente, incluidos los _nombres principales de servicio_ (SPN) y la configuración de delegación de cuentas de servicio.

### <a name="prerequisite-1-install-and-configure-the-microsoft-on-premises-data-gateway"></a>Requisito previo 1: instalar y configurar la puerta de enlace de datos local de Microsoft

La puerta de enlace de datos local admite la actualización local, así como la _adquisición de la configuración_ de las puertas de enlace existentes.

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>Requisito previo 2: ejecución del servicio de Windows de puerta de enlace como cuenta de dominio

En una instalación estándar, la puerta de enlace se ejecuta como una cuenta de servicio de la máquina local (en concreto, _NT Service\PBIEgwService_), como se muestra en la imagen siguiente:

![Captura de pantalla de la cuenta de servicio](media/service-gateway-sso-kerberos/service-account.png)

Para habilitar la delegación restringida de Kerberos, debe ejecutar la puerta de enlace como una cuenta de dominio, a menos que su instancia de Azure Active Directory (Azure AD) ya esté sincronizada con su instancia de Active Directory local (mediante Azure AD DirSync o Azure AD Connect). Para cambiar a una cuenta de dominio, consulte [Cambio de la cuenta de servicio de puerta de enlace](/data-integration/gateway/service-gateway-service-account).

> [!NOTE]
> Si Azure AD Connect está configurado y las cuentas de usuario están sincronizadas, el servicio de puerta de enlace no necesita realizar búsquedas de Azure AD locales en tiempo de ejecución. En su lugar, puede usar simplemente el SID de servicio local para que el servicio de puerta de enlace complete toda la configuración necesaria en Azure Active Directory. Los pasos de configuración de la delegación restringida de Kerberos que se describen en este artículo son los mismos que los pasos de configuración necesarios en el contexto de Azure Active Directory. Simplemente se aplican al objeto de equipo de la puerta de enlace (como lo identifica el SID de servicio local) en Azure AD, en lugar de la cuenta de dominio.

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Requisito previo 3: tener derechos de administrador de dominio para configurar los SPN (SetSPN) y la configuración de la delegación restringida de Kerberos

No se recomienda que un administrador de dominio conceda derechos temporales o permanentes a otro usuario para configurar SPN y la delegación de Kerberos sin requerir que esa persona tenga derechos de administrador de dominio. En la siguiente sección, trataremos con más detalle los pasos de configuración recomendados.

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Configuración de la delegación restringida de Kerberos para la puerta de enlace y el origen de datos

Con su rol de administrador de dominio, configure un SPN para la cuenta de dominio del servicio de la puerta de enlace (si se requiere) y configure la delegación en esa cuenta.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Configuración de un SPN para la cuenta de servicio de la puerta de enlace

En primer lugar, determine si ya se ha creado un nombre de entidad de seguridad de servicio para la cuenta de dominio que se usa como la cuenta de servicio de la puerta de enlace:

1. Como administrador de dominio, inicie **Usuarios y equipos de Active Directory**.

2. Haga clic con el botón derecho en el dominio, seleccione **Buscar** y escriba el nombre de la cuenta de servicio de la puerta de enlace.

3. En el resultado de la búsqueda, haga clic con el botón derecho en la cuenta de servicio de la puerta de enlace y seleccione **Propiedades**.

4. Si la pestaña **Delegación** aparece en el cuadro de diálogo **Propiedades**, ya se creó un SPN y es posible pasar directamente a [Decisión entre una delegación restringida de Kerberos estándar o una basada en recurso](#decide-on-resource-based-or-standard-kerberos-constrained-delegation).

    Si no hay ninguna pestaña **Delegación** en el cuadro de diálogo **Propiedades**, puede crear manualmente un SPN en la cuenta para su habilitación. Use la [herramienta setspn](https://technet.microsoft.com/library/cc731241.aspx) que viene con Windows (necesita derechos de administrador de dominio para crear el SPN).

    Por ejemplo, imagine que la cuenta de servicio de puerta de enlace es **Contoso\GatewaySvc**) y que el nombre de la máquina donde se ejecuta el servicio de puerta de enlace es **MyGatewayMachine**. Para establecer el SPN de la cuenta de servicio de puerta de enlace, debe ejecutar el comando siguiente:

    ![Imagen del comando setspn](media/service-gateway-sso-kerberos/set-spn.png)

    También puede establecer el SPN mediante el complemento Equipos y usuarios de Active Directory de MMC (Microsoft Management Console).

### <a name="decide-on-resource-based-or-standard-kerberos-constrained-delegation"></a>Decisión entre una delegación restringida de Kerberos estándar o una basada en recurso

La delegación se puede configurar _tanto_ para una delegación restringida de Kerberos basada en recurso como para una delegación restringida de Kerberos estándar. Use la delegación basada en recurso si el origen de datos pertenece a un dominio diferente al de la puerta de enlace, pero tenga en cuenta que este enfoque requiere Windows Server 2012 o posterior. Consulte la [página de información general sobre la delegación restringida de Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para más información sobre las diferencias entre ambos enfoques para la delegación.

 Una vez que decida qué enfoque quiere usar, vaya _o_ a la sección [Configuración de la cuenta de servicio de la puerta de enlace para la delegación restringida de Kerberos estándar](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation) _o a la sección_ [Configuración de la cuenta de servicio de la puerta de enlace para la delegación restringida de Kerberos basada en recurso](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation). No complete ambas subsecciones.

## <a name="configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation"></a>Configuración de la cuenta de servicio de la puerta de enlace para la delegación restringida de Kerberos estándar

> [!NOTE]
> Complete los pasos de esta sección si desea habilitar la delegación restringida de Kerberos estándar. Si quiere habilitar la delegación restringida de Kerberos basada en recurso, complete los pasos que aparecen en la subsección [Configuración de la cuenta de servicio de la puerta de enlace para la delegación restringida de Kerberos basada en recurso](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation).

Ahora estableceremos la configuración de delegación para la cuenta de servicio de la puerta de enlace. Hay varias herramientas que puede usar para realizar estos pasos. Aquí utilizaremos Usuarios y equipos de Active Directory, que es un complemento de Microsoft Management Console (MMC) que puede usar para administrar y publicar información en el directorio. Está disponible en los controladores de dominio de manera predeterminada, pero también se puede habilitar mediante la configuración de las Características de Windows en otras máquinas.

Es necesario configurar la delegación restringida de Kerberos con tránsito de protocolo. Con la delegación restringida, debe ser explícito con respecto a qué servicios desea permitir que la puerta de enlace presente credenciales delegadas. Por ejemplo, solo SQL Server o el servidor de SAP HANA aceptan llamadas de delegación de la cuenta de servicio de la puerta de enlace.

En esta sección se da por supuesto que ya ha configurado los SPN de los orígenes de datos subyacentes (como SQL Server, SAP HANA, SAP BW, Teradata o Spark). Para obtener información sobre cómo configurar los SPN del servidor del origen de datos, consulte la documentación técnica para el servidor de bases de datos respectivo. También puede ver el encabezado *What SPN does your app require?* (¿Qué SPN requiere la aplicación) en la entrada de blog [My Kerberos Checklist](https://techcommunity.microsoft.com/t5/SQL-Server-Support/My-Kerberos-Checklist-8230/ba-p/316160) (Mi lista de comprobación de Kerberos).

En los pasos siguientes, se asume que disponemos de un entorno local con dos equipos: un equipo de puerta de enlace y un servidor de bases de datos que ejecuta SQL Server que ya está configurado para el SSO basado en Kerberos. Los pasos se pueden adoptar para uno de los otros orígenes de datos admitidos, siempre y cuando el origen de datos ya se haya configurado para el inicio de sesión único basado en Kerberos. Para este ejemplo, también asumiremos la configuración y los nombres siguientes:

* Dominio de Active Directory (NetBIOS): Contoso
* Nombre de la máquina de la puerta de enlace: **MyGatewayMachine**
* Cuenta de servicio de puerta de enlace: **Contoso\GatewaySvc**
* Nombre de la máquina del origen de datos de SQL Server: **TestSQLServer**
* Cuenta de servicio del origen de datos de SQL Server: **Contoso\SQLService**

Aquí le mostramos cómo configurar las opciones de delegación:

1. Con derechos de administrador de dominio, abra **Usuarios y equipos de Active Directory**.

2. Haga clic con el botón derecho en la cuenta de servicio de la puerta de enlace (**Contoso\GatewaySvc**) y seleccione **Propiedades**.

3. Seleccione la ficha **Delegación**.

4. Seleccione **Confiar en este equipo para la delegación solo a los servicios especificados** > **Usar cualquier protocolo de autenticación**.

5. En **Servicios en los que esta cuenta puede presentar credenciales delegadas**, haga clic en **Agregar**.

6. En el cuadro de diálogo nuevo, seleccione **Usuarios o equipos**.

7. Escriba la cuenta de servicio para el origen de datos; por ejemplo, un origen de datos de SQL Server puede tener una cuenta de servicio como **Contoso\SQLService**. Una vez que se ha agregado la cuenta, seleccione **Aceptar**.

8. Seleccione el SPN que ha creado para el servidor de base de datos. En nuestro ejemplo, el SPN empieza por **MSSQLSvc**. Si ha agregado tanto el SPN de FQDN como el de NetBIOS, seleccione ambos. Puede que solo vea uno.

9. Seleccione **Aceptar**. Ahora debería ver el SPN en la lista.

    ![Captura de pantalla del cuadro de diálogo Propiedades del conector de puerta de enlace](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

Ahora, vaya a [Concesión de derechos de directiva local a la cuenta de servicio de la puerta de enlace en la máquina de la puerta de enlace](#grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine) para continuar el proceso de configuración.

## <a name="configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation"></a>Configuración de la cuenta de servicio de la puerta de enlace para la delegación restringida de Kerberos basada en recurso

> [!NOTE]
> Complete los pasos de esta sección si desea habilitar la delegación restringida de Kerberos basada en recurso. Si quiere habilitar la delegación restringida de Kerberos estándar, complete los pasos que aparecen en la subsección [Configuración de la cuenta de servicio de la puerta de enlace para la delegación restringida de Kerberos estándar](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation).

Use la [delegación restringida de Kerberos basada en recursos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para habilitar la conectividad de inicio de sesión único de Windows Server 2012 y versiones posteriores, que permite a los servicios front-end y back-end estar en dominios diferentes. Para que esto funcione, el dominio del servicio back-end debe confiar en el dominio del servicio front-end.

En los pasos siguientes, se asume que disponemos de un entorno local con dos equipos en distintos dominios: un equipo de puerta de enlace y un servidor de bases de datos que ejecuta SQL Server que ya está configurado para el SSO basado en Kerberos. Los pasos se pueden adoptar para uno de los otros orígenes de datos admitidos, siempre y cuando el origen de datos ya se haya configurado para el inicio de sesión único basado en Kerberos. Para este ejemplo, supongamos también la configuración y los nombres siguientes:

* Nombre de la máquina de la puerta de enlace: **MyGatewayMachine**
* Cuenta de servicio de puerta de enlace: **ContosoFrontEnd\GatewaySvc**
* Nombre de la máquina del origen de datos de SQL Server: **TestSQLServer**
* Cuenta de servicio del origen de datos de SQL Server: **ContosoBackEnd\SQLService**

Con esos nombres y configuración de ejemplo, complete estos pasos de configuración:

1. En el controlador de dominio para el dominio **ContosoFrontEnd**, asegúrese de que no se aplica ninguna configuración de delegación para la cuenta de servicio de la puerta de enlace mediante **Equipos y usuarios de Active Directory**, un complemento de Microsoft Management Console (MMC).

    ![Propiedades del conector de puerta de enlace](media/service-gateway-sso-kerberos-resource/gateway-connector-properties.png)

2. Al usar **Equipos y usuarios de Active Directory** en el controlador de dominio para el dominio **ContosoBackEnd**, asegúrese de que no se aplica ninguna configuración de delegación para la cuenta de servicio de back-end. Además, asegúrese de que el atributo **msDS-AllowedToActOnBehalfOfOtherIdentity** tampoco está configurado para esta cuenta. Puede encontrar este atributo en el **Editor de atributos**, tal como se muestra en la siguiente imagen:

    ![Propiedades del servicio SQL](media/service-gateway-sso-kerberos-resource/sql-service-properties.png)

3. Cree un grupo en **Equipos y usuarios de Active Directory**, en el controlador de dominio para el dominio **ContosoBackEnd**. Agregue la cuenta de servicio de puerta de enlace a este grupo como se muestra en la siguiente imagen. La imagen muestra un nuevo grupo denominado _ResourceDelGroup_ y la cuenta de servicio de la puerta de enlace **GatewaySvc**, que se agregó a este grupo.

    ![Propiedades del grupo](media/service-gateway-sso-kerberos-resource/group-properties.png)

4. Abra un símbolo del sistema y ejecute los comandos siguientes en el controlador de dominio para el dominio **ContosoBackEnd** para actualizar el atributo **msDS-AllowedToActOnBehalfOfOtherIdentity** de la cuenta de servicio de back-end:

    ```powershell
    $c = Get-ADGroup ResourceDelGroup
    Set-ADUser SQLService -PrincipalsAllowedToDelegateToAccount $c
    ```

5. Puede comprobar que la actualización se refleja en la pestaña "Editor de atributos" en las propiedades de la cuenta de servicio de back-end en **Equipos y usuarios de Active Directory**.

## <a name="grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine"></a>Concesión de derechos de directiva local a la cuenta de servicio de la puerta de enlace en la máquina de la puerta de enlace

Por último, en el equipo en el que se ejecuta el servicio de puerta de enlace (**MyGatewayMachine** en el ejemplo), debe conceder a la cuenta de servicio de la puerta de enlace la directiva local **Suplantar a un cliente tras la autenticación** y **Actuar como parte del sistema operativo (SeTcbPrivilege)** . Puede realizar y verificar esta configuración con el Editor de directivas de grupo local (**gpedit**).

1. En el equipo de puerta de enlace, ejecute: *gpedit.msc*.

2. Vaya a **Directiva de equipo local** > **Configuración del equipo** > **Configuración de Windows** > **Configuración de seguridad** > **Directivas locales** > **Asignación de derechos de usuario**.

    ![Captura de pantalla de la estructura de carpetas de la Directiva de equipo local](media/service-gateway-sso-kerberos/user-rights-assignment.png)

3. En la lista de directivas de **Asignación de derechos de usuario**, seleccione **Suplantar a un cliente tras la autenticación**.

    ![Captura de pantalla de Suplantar una directiva de cliente](media/service-gateway-sso-kerberos/impersonate-client.png)

    Haga clic con el botón derecho y abra **Propiedades**. Compruebe la lista de cuentas. Debe incluir la cuenta de servicio de la puerta de enlace (**Contoso\GatewaySvc**).

4. En la lista de directivas de **Asignación de derechos de usuario**, seleccione **Actuar como parte del sistema operativo (SeTcbPrivilege)** . Asegúrese también de que la cuenta de servicio de la puerta de enlace está incluida en la lista de cuentas.

5. Reinicie el proceso del servicio de la **puerta de enlace de datos local**.

### <a name="set-user-mapping-configuration-parameters-on-the-gateway-machine-if-required"></a>Establecimiento de los parámetros de configuración de la asignación de usuario en la máquina de la puerta de enlace si es necesario

Si no tiene configurado Azure AD Connect, siga estos pasos para asignar un usuario del servicio Power BI a un usuario de Active Directory local. Cada usuario de Active Directory asignado de este modo debe tener permisos de SSO para el origen de datos. Para más información, consulte este [vídeo de Guy in a Cube](https://www.youtube.com/watch?v=NG05PG9aiRw).

1. Abra el archivo de configuración de la puerta de enlace principal, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Este archivo se almacena, de forma predeterminada, en C:\Archivos de programa\Puerta de enlace de datos local.

1. Establezca la propiedad **ADUserNameLookupProperty** en un atributo de Active Directory sin usar. Supondremos que `msDS-cloudExtensionAttribute1` se usa en los pasos siguientes, aunque este atributo solo está disponible en Windows Server 2012 y versiones posteriores. Establezca **ADUserNameReplacementProperty** en `SAMAccountName`. Guarde el archivo de configuración.

1. En la pestaña **Servicios** del Administrador de tareas, haga clic con el botón derecho en el servicio de puerta de enlace y, después, haga clic en **Reiniciar**.

    ![Captura de pantalla de la pestaña Servicios del Administrador de tareas](media/service-gateway-sso-kerberos/restart-gateway.png)

1. En cada usuario del servicio Power BI para el que quiere habilitar el SSO de Kerberos, establezca la propiedad `msDS-cloudExtensionAttribute1` de un usuario de Active Directory local (con permiso de SSO para el origen de datos) en el nombre de usuario completo del usuario del servicio Power BI. Por ejemplo, si inicia sesión en el servicio Power BI como `test@contoso.com` y quiere asignar este usuario a un usuario de Active Directory local con permisos de SSO, como `test@LOCALDOMAIN.COM`, establezca el atributo `msDS-cloudExtensionAttribute1` de `test@LOCALDOMAIN.COM` en `test@contoso.com`.

Puede establecer la propiedad `msDS-cloudExtensionAttribute1` con el complemento Equipos y usuarios de Active Directory de Microsoft Management Console (MMC).

1. Como administrador de dominio, inicie Equipos y usuarios de Active Directory, un complemento de MMC.

1. Haga clic con el botón derecho en el dominio, seleccione Buscar y escriba el nombre de la cuenta del usuario de Active Directory local al que quiere asignar.

1. Seleccione la pestaña **Editor de atributos**.

    Localice la propiedad `msDS-cloudExtensionAttribute1` y haga doble clic en ella. Establezca el valor en el nombre de usuario completo del usuario que usa para iniciar sesión en el servicio Power BI.

1. Seleccione **Aceptar**.

    ![Captura de pantalla del cuadro de diálogo Editor de atributos de cadena](media/service-gateway-sso-kerberos/edit-attribute.png)

1. Seleccione **Aplicar**. Compruebe que se ha establecido el valor correcto en la columna **Valor**.

## <a name="complete-data-source-specific-configuration-steps"></a>Finalización de los pasos de configuración específicos para el origen de datos

SAP HANA y SAP BW tienen requisitos de configuración específicos de origen de datos adicionales y requisitos previos que deben cumplirse para poder establecer una conexión de SSO a través de la puerta de enlace a estos orígenes de datos. Consulte [la página de configuración de SAP HANA](service-gateway-sso-kerberos-sap-hana.md) y [la página de configuración de SAP BW: CommonCryptoLib (sapcrypto.dll)](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) para ver detalles. También es posible [configurar SAP BW para su uso con la biblioteca gx64krb5 de SNC](service-gateway-sso-kerberos-sap-bw-gx64krb.md), pero Microsoft no recomienda usar esta biblioteca porque ya no es compatible con SAP. Debe usar CommonCryptoLib _o_ gx64krb5 como su biblioteca de SNC. No complete los pasos de configuración para ambas bibliotecas.

> [!NOTE]
> Otras bibliotecas de SNC también podrían servir para el SSO de BW, pero no son compatibles oficialmente con Microsoft.

## <a name="run-a-power-bi-report"></a>Ejecutar un informe de Power BI

Después de completar todos los pasos de configuración, puede utilizar la página **Administrar puerta de enlace** en Power BI para configurar el origen de datos que usará para el SSO. Si tiene varias puertas de enlace, asegúrese de seleccionar la que ya configuró para el SSO de Kerberos. A continuación, en **Configuración avanzada** del origen de datos, asegúrese de que esté activada la opción "Usar SSO mediante Kerberos para las consultas de DirectQuery".

![Captura de pantalla de la opción Configuración avanzada](media/service-gateway-sso-kerberos/advanced-settings.png)

 Publique un informe **basado en DirectQuery** desde Power BI Desktop. Este informe debe utilizar datos que sean accesibles para el usuario que está asignado al usuario de (Azure) Active Directory que inicia sesión en el servicio Power BI. Debe usar DirectQuery en lugar de la importación, debido a la forma en que funciona la actualización. Al actualizar los informes basados en la importación, la puerta de enlace usa las credenciales especificadas en los campos **Nombre de usuario** y **Contraseña** al crear el origen de datos. En otras palabras, **no** se usa el SSO de Kerberos. Además, al publicar, asegúrese de seleccionar la puerta de enlace que ha configurado para el SSO si tiene varias puertas de enlace. En el servicio Power BI debería poder actualizar el informe o crear un informe basado en el conjunto de datos publicado.

Esta configuración funciona en la mayoría de los casos. Sin embargo, con Kerberos puede haber distintas configuraciones en función de su entorno. Si todavía no se pudo cargar el informe, póngase en contacto con el administrador del dominio para investigar en profundidad. Si el origen de datos es SAP BW, también puede consultar las secciones de solución de problemas de las páginas de configuración específicas del origen de datos para [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md#troubleshooting) y [gx64krb5/gsskrb5](service-gateway-sso-kerberos-sap-bw-gx64krb.md#troubleshooting).

## <a name="next-steps"></a>Pasos siguientes

Para más información acerca de la **puerta de enlace de datos local** y **DirectQuery**, consulte los recursos siguientes:

* [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
