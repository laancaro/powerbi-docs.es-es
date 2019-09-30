---
title: Uso de Kerberos para el inicio de sesión único (SSO) en SAP BW con gx64krb5
description: Configuración del servidor de SAP BW para habilitar el SSO desde el servicio Power BI con gx64krb5
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5dd31dc4333dc03100370100e16eadab6012c1f0
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106340"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Uso de Kerberos para el inicio de sesión único (SSO) en SAP BW con gx64krb5

En este artículo se describe cómo configurar el servidor de SAP BW para habilitar el SSO del servicio Power BI con gx64krb5.

> [!NOTE]
> Puede completar los pasos de este artículo junto con los pasos de [configuración del SSO de Kerberos](service-gateway-sso-kerberos.md) para permitir la actualización de los informes basados en el servidor de aplicaciones de SAP BW que usan el SSO de Kerberos en el servicio Power BI. Sin embargo, Microsoft recomienda el uso de CommonCryptoLib como su biblioteca de SNC. SAP ya no ofrece compatibilidad con gx64krb5 y los pasos necesarios para configurarlo para su uso con la puerta de enlace son mucho más complejos en comparación con CommonCryptoLib. Consulte [Configuración de SAP BW para SSO con CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) para saber cómo configurar el SSO con CommonCryptoLib. Debe completar la configuración de CommonCryptoLib _o_ gx64krb5. No complete los pasos de configuración para ambas bibliotecas.

### <a name="set-up-gx64krb5gsskrb5-on-gateway-machine-and-the-sap-bw-server"></a>Configuración de gx64krb5/gsskrb5 en la máquina de la puerta de enlace y el servidor de SAP BW

> [!NOTE]
> SAP ya no ofrece soporte técnico activo para `gx64krb5` ni para `gsskrb5`. Para obtener más información, consulte la [nota 352295 de SAP](https://launchpad.support.sap.com/#/notes/352295). Tenga en cuenta también que `gx64krb5` no permite conexiones SSO entre la puerta de enlace de datos y los servidores de mensajería SAP BW. Solo es posible establecer la conexión con los servidores de aplicaciones SAP BW. Esta restricción solo del servidor de aplicaciones no existe si usa [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) como su biblioteca de SNC. Otras bibliotecas de SNC también podrían servir para el SSO de BW, pero no son compatibles oficialmente con Microsoft.

Tanto el cliente como el servidor deben usar `gx64krb5` \ `gsskrb5` para completar una conexión SSO a través de la puerta de enlace; es decir, tanto el cliente como el servidor deben usar la misma biblioteca de SNC.

1. Descargue `gx64krb5` desde [SAP Note 2115486](https://launchpad.support.sap.com/) (es necesario ser usuario-s de SAP). Asegúrese de tener al menos la versión 1.0.11.x o posterior. Descargue también `gsskrb5` (la versión de la biblioteca de 32 bits) si quiere probar la conexión SSO en la GUI de SAP antes de intentar la conexión SSO a través de la puerta de enlace (recomendado). La versión de 32 bits es necesaria para realizar la prueba con la GUI de SAP porque la GUI de SAP solo está disponible en 32 bits.

1. Coloque `gx64krb5` en una ubicación en el equipo de puerta de enlace a la cual pueda acceder el usuario del servicio de la puerta de enlace (y también la GUI de SAP, si quiere probar la conexión SSO con el inicio de sesión de SAP). Tanto el usuario del servicio de puerta de enlace como los usuarios de Active Directory (AD) que el usuario del servicio va a suplantar necesitan permisos de lectura y ejecución para el archivo .dll. Se recomienda conceder permisos para el archivo. dll al grupo usuarios autenticados. A efectos de prueba, también puede conceder estos permisos explícitamente al usuario del servicio de la puerta de enlace y al usuario de Active Directory que usará para hacer la prueba.

1. Si el servidor de BW todavía no está configurado para el SSO con gx64krb5/gsskrb5, coloque otra copia en equipo servidor de SAP BW en una ubicación a la que pueda acceder el servidor de SAP BW. 

1. En los equipos cliente y servidor, establezca las variables de entorno `SNC_LIB` o `SNC_LIB_64`. Si usa gsskrb5, establezca la variable `SNC_LIB` en la ruta de acceso absoluta de gsskrb5.dll. Si usa gx64krb5, establezca la variable `SNC_LIB_64` en la ruta de acceso absoluta de gx64krb5.dll.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication"></a>Configure un usuario de servicio de SAP BW y habilitación de la comunicación SNC

Complete esta sección si todavía no configura el servidor de SAP BW para la comunicación SNC (por ejemplo, SSO) con gx64krb5/gsskrb5.

> [!NOTE]
> En esta sección se supone que ya ha creado un usuario de servicio para BW y le ha enlazado un SPN adecuado (por ejemplo, algo que empiece por `SAP/`).

1. Otorgue al usuario del servicio acceso al servidor de aplicaciones de SAP BW:

    1. En el equipo servidor de SAP BW, agregue el usuario de servicio al grupo de administradores locales. Abra el programa Administración de equipos y haga doble clic en el grupo Administrador local del servidor.

        ![Captura de pantalla del programa Administración de equipos](media/service-gateway-sso-kerberos/computer-management.png)

    1. Haga doble clic en el grupo Administrador local y haga clic en **Agregar** para agregar el usuario del servicio al grupo. Haga clic en **Comprobar nombres** para asegurarse de que ha escrito el nombre correctamente. Seleccione **Aceptar**.

1. Establezca el usuario de servicio del servidor de SAP BW como el usuario que inicia el servicio del servidor de SAP BW en el equipo servidor de SAP BW.

    1. Abra **Ejecutar** y escriba "Services.msc". Busque el servicio que corresponde a la instancia de servidor de aplicaciones de SAP BW. Haga clic con el botón derecho en él y seleccione **Propiedades**.

        ![Captura de pantalla de Servicios, con Propiedades resaltado](media/service-gateway-sso-kerberos/server-properties.png)

    1. Cambie a la pestaña **Inicio de sesión** y sustituya el usuario por el usuario del servicio de SAP BW. Escriba la contraseña del usuario y haga clic en **Aceptar**.

1. Inicie sesión el servidor en el inicio de sesión de SAP y establezca los siguientes parámetros de perfil mediante la transacción RZ10:

    1. Establezca el parámetro de perfil snc/identity/as en p:\<el usuario del servicio de SAP BW que ha creado\>, como p:BWServiceUser@MYDOMAIN.COM. Tenga en cuenta que la p: precede al UPN del usuario del servicio. No es p:CN= como cuando se usa la biblioteca común de criptografía como la biblioteca SNC.

    1. Establezca el parámetro de perfil snc/gssapi\_lib en la \<ruta de acceso a gsskrb5.dll/gx64krb5.dll en el equipo servidor de BW (la biblioteca que se va a usar depende del valor de bits del sistema operativo)\>. Recuerde colocar la biblioteca en una ubicación a la cual pueda tener acceso el servidor de aplicaciones de SAP BW.

    1. Establezca también los siguientes parámetros de perfil adicionales, cambiando los valores según sea necesario para ajustarse a sus necesidades. Tenga en cuenta que las últimas cinco opciones permiten a los clientes conectarse al servidor de SAP BW mediante el inicio de sesión de SAP sin necesidad de tener SNC configurado.

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

1. Después de establecer estos parámetros de perfil, abra la consola de administración de SAP en el equipo servidor y reinicie la instancia de SAP BW. Si no se inicia el servidor, confirme que ha establecido correctamente los parámetros de perfil. Para obtener más información sobre la configuración de parámetros de perfil, vea la [documentación de SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Si tiene problemas, también puede consultar la información de solución de problemas más adelante en esta sección.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Asignación de un usuario de SAP BW a un usuario de Active Directory

Si todavía no lo ha hecho, asigne un usuario de Active Directory a un usuario del servidor de aplicaciones de SAP BW y pruebe la conexión SSO en el inicio de sesión de SAP.

1. Inicie sesión el servidor de SAP BW mediante el inicio de sesión de SAP. Ejecute la transacción SU01.

1. Para **Usuario**, escriba el usuario de SAP BW para el cual quiere habilitar las conexiones SSO (en la captura de pantalla anterior se establecen los permisos para BIUSER). Haga clic en el icono **Editar** (la imagen de un lápiz) situado cerca de la parte superior izquierda de la ventana de inicio de sesión de SAP.

    ![Captura de la pantalla de mantenimiento de usuario de SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Seleccione la pestaña **SNC**. En el cuadro de entrada del nombre de SNC, escriba p:\<su usuario de Active Directory\>@\<su dominio\>. Tenga en cuenta la p: obligatoria debe preceder al UPN del usuario de Active Directory. El usuario de Active Directory que especifique debe pertenecer a la persona u organización para la cual quiere habilitar el acceso SSO al servidor de aplicaciones de SAP BW. Por ejemplo, si quiere habilitar el acceso SSO para el usuario testuser\@TESTDOMAIN.COM, escriba p:testuser@TESTDOMAIN.COM.

    ![Captura de la pantalla Mantener usuarios de SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Haga clic en el icono **Guardar** (la imagen del disquete) cerca de la parte superior izquierda de la pantalla.

### <a name="test-sign-in-by-using-sso"></a>Prueba del inicio de sesión con SSO

Compruebe que puede iniciar sesión en el servidor mediante el inicio de sesión de SAP mediante SSO como el usuario de Active Directory para el cual acaba de habilitar el acceso.

1. Con el usuario de Active Directory para el cual acaba de habilitar el acceso SSO, inicie sesión en el equipo en el que está instalado el inicio de sesión de SAP. Inicie el inicio de sesión de SAP y cree una conexión nueva.

1. En la pantalla **Crear nueva entrada del sistema**, haga clic en **Sistema especificado del usuario** > **Siguiente**.

    ![Captura de la pantalla Crear nueva entrada del sistema](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Rellene los detalles adecuados en la siguiente página, incluidos el servidor de aplicaciones, el número de instancia y el ID del sistema. A continuación, haga clic en **Finalizar**.

1. Haga clic con el botón derecho en la conexión nueva y seleccione **Propiedades**. Seleccione la pestaña **Red**. En el cuadro de texto **Nombre de SNC**, escriba p:\<UPN del usuario del servicio de SAP BW\>, como p:BWServiceUser@MYDOMAIN.COM. Después, seleccione **Aceptar**.

    ![Captura de la pantalla Propiedades de la entrada del sistema](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Haga doble clic en la conexión que acaba de crear para intentar una conexión SSO al servidor SAP BW. Si esta conexión se realiza correctamente, continúe con el paso siguiente. En caso contrario, revise los pasos anteriores en este documento para asegurarse de que se ha completado correctamente, o consulte la siguiente sección de solución de problemas. Tenga en cuenta que si no se puede conectar al servidor de SAP BW mediante SSO en este contexto, no podrá conectarse al servidor de SAP BW mediante SSO en el contexto de la puerta de enlace.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Adición de entradas del Registro a la máquina de puerta de enlace

Agregue las entradas del registro necesarias al registro del equipo en el que está instalada la puerta de enlace, así como a las máquinas que se van a conectar desde Power BI Desktop. Estos son los comandos que hay que ejecutar:

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Incorporación de un nuevo origen de datos de servidor de aplicaciones de SAP BW en el servicio Power BI o edición de uno existente

1. En la ventana de configuración del origen de datos, especifique el **nombre de host**, el **número del sistema** y el **ID de cliente** del servidor de aplicaciones tal como lo haría para iniciar sesión el servidor de SAP BW desde Power BI Desktop.

1. En el campo **Nombre de asociado de SNC**, escriba p: \<el SPN asignado al usuario del servicio SAP BW\>. Por ejemplo, si el SPN es SAP/BWServiceUser@MYDOMAIN.COM, debe escribir p:SAP/BWServiceUser@MYDOMAIN.COM en el campo **Nombre de asociado de SNC**.

1. Para la biblioteca de SNC, seleccione **SNC_LIB** o **SNC_LIB_64**. Asegúrese de que SNC_LIB_64 en la máquina de la puerta de enlace apunte a gx64krb5.dll. También puede seleccionar la opción "Personalizado" y proporcionar la ruta de acceso absoluta a gx64krb5. dll (en la máquina de puerta de enlace).

1. Seleccione la casilla **Usar SSO mediante Kerberos para las consultas de DirectQuery** y, después, haga clic en **Aplicar**. Si la conexión de prueba no es correcta, compruebe que los pasos de instalación y configuración anteriores se hayan completado correctamente.

1. [Ejecución de un informe de Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Solución de problemas

### <a name="troubleshoot-gx64krb5gsskrb5-configuration"></a>Solución de problemas con la configuración de gx64krb5/gsskrb5

Si detecta algún problema, siga estos pasos para solucionar problemas de instalación de gx64krb5/gsskrb5 y de las conexiones SSO desde el inicio de sesión de SAP.

* La visualización de los registros del servidor (...work\dev\_w0 en el equipo servidor) puede ser útil para solucionar los errores que se producen al completar los pasos de configuración de gx64krb5/gsskrb5, especialmente si el servidor de SAP BW no se inicia tras cambiar los parámetros de perfil.

* Si no puede iniciar el servicio de SAP BW debido a un error de inicio de sesión, quizás haya proporcionado una contraseña incorrecta al establecer el usuario de SAP BW utilizado para el inicio. Compruebe la contraseña iniciando sesión en un equipo en el entorno de Active Directory como usuario del servicio de SAP BW.

* Si recibe errores relacionados con las credenciales de SQL que impiden que se inicie el servidor, compruebe que se le ha concedido el acceso de usuario del servicio a la base de datos de SAP BW.

* Es posible que obtenga el siguiente mensaje: "El destino especificado de (GSS-API) es desconocido o no está disponible". Normalmente, esto significa que se ha especificado un nombre de SNC incorrecto. Asegúrese de usar "p:" únicamente, no "p:CN=" o cualquier otra descripción en la aplicación cliente, que no sea el UPN del usuario del servicio.

* Es posible que obtenga el siguiente mensaje: "(GSS-API) Se ha suministrado un nombre no válido". Asegúrese de que "p:" está en el valor del parámetro de perfil de identidad SNC del servidor.

* Es posible que obtenga el siguiente mensaje: "(Error de SNC) No se ha encontrado el módulo especificado". Esto puede deberse a que se ha colocado `gsskrb5.dll/gx64krb5.dll` en algún sitio que requiere privilegios elevados (derechos de administrador) para el acceso.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Solución de problemas de conectividad de la puerta de enlace

1. Compruebe los registros de la puerta de enlace. Abra la aplicación de configuración de la puerta de enlace y haga clic en **Diagnósticos** > **Exportar registros**. Los errores más recientes están en la parte inferior de los archivos de registro que examine.

    ![Captura de pantalla de la aplicación Puerta de enlace de datos local, con Diagnósticos resaltado](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Active el seguimiento de SAP BW y revise los archivos de registro generados. Hay varios tipos de seguimiento de SAP BW disponibles. Para obtener más información, consulte la documentación de SAP.

## <a name="next-steps"></a>Pasos siguientes

Para más información acerca de la **puerta de enlace de datos local** y **DirectQuery**, consulte los recursos siguientes:

* [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
