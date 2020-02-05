---
title: Uso de Kerberos para el inicio de sesión único (SSO) en SAP BW con gx64krb5
description: Configuración del servidor de SAP BW para habilitar el SSO desde el servicio Power BI con gx64krb5
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c8b62cf798d2fbbd09dab0603d216448d04487c
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "75000144"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Uso de Kerberos para el inicio de sesión único (SSO) en SAP BW con gx64krb5

En este artículo se describe cómo configurar el origen de datos de SAP BW para habilitar el inicio de sesión único del servicio Power BI con gx64krb5.

> [!NOTE]
> Puede completar los pasos de este artículo junto con los de [Configuración del SSO de Kerberos](service-gateway-sso-kerberos.md) para permitir la actualización basada en SSO de los informes basados en el servidor de aplicaciones de SAP BW en el servicio Power BI. Pero Microsoft recomienda el uso de CommonCryptoLib, no de gx64krb5, como biblioteca de SNC. SAP ya no es compatible con gx64krb5 y los pasos necesarios para configurarlo para la puerta de enlace son mucho más complejos en comparación con CommonCryptoLib. Para más información sobre la configuración del inicio de sesión único mediante CommonCryptoLib, consulte [Configuración de SAP BW para el inicio de sesión único con CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md). Debe usar CommonCryptoLib _o_ gx64krb5 como su biblioteca de SNC. No complete los pasos de configuración para ambas bibliotecas.

Esta guía es completa; si ya ha realizado algunos de los pasos descritos, puede omitirlos. Por ejemplo, es posible que ya haya configurado el servidor de SAP BW para el SSO con gx64krb5.

## <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>Configuración de gx64krb5 en el equipo de la puerta de enlace y el servidor de SAP BW

> [!NOTE]
> La biblioteca gx64krb5 ya no es compatible con SAP. Para obtener más información, consulte la [nota 352295 de SAP](https://launchpad.support.sap.com/#/notes/352295). Tenga en cuenta que gx64krb5 no permite conexiones de inicio de sesión único desde la puerta de enlace de datos para los servidores de mensajería de SAP BW; solo son posibles las conexiones a los servidores de aplicaciones de SAP BW. Esta restricción no existe si usa [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) como biblioteca de SNC. Aunque otras bibliotecas de SNC también podrían servir para el inicio de sesión único de BW, no son compatibles oficialmente con Microsoft.

Tanto el cliente como el servidor deben usar la biblioteca gx64krb5 para que se complete una conexión de inicio de sesión único mediante la puerta de enlace. Es decir, tanto el cliente como el servidor deben usar la misma biblioteca de SNC.

1. Descargue gx64krb5.dll desde la [nota de SAP 2115486](https://launchpad.support.sap.com/) (es necesario ser usuario-s de SAP). Asegúrese de tener al menos la versión 1.0.11.x o posterior. Descargue también gsskrb5.dll (la versión de la biblioteca de 32 bits) si quiere probar la conexión de inicio de sesión único en la interfaz gráfica de usuario de SAP antes de intentar la conexión de inicio de sesión único mediante la puerta de enlace (procedimiento recomendado). Se necesita la versión de 32 bits para realizar la prueba con la GUI de SAP, ya que esta solo está disponible en 32 bits.

1. Coloque gx64krb5.dll en una ubicación de la máquina de la puerta de enlace que sea accesible para el usuario del servicio de puerta de enlace. Si quiere probar la conexión de inicio de sesión único mediante la interfaz gráfica de usuario de SAP, coloque también una copia de gsskrb5.dll en la máquina y establezca la variable de entorno **SNC_LIB** para que apunte a ella. Tanto el usuario del servicio de puerta de enlace como los usuarios de Active Directory (AD) que el usuario del servicio va a suplantar necesitan permisos de lectura y ejecución para la copia de gx64krb5.dll. Se recomienda conceder permisos para el archivo. dll al grupo usuarios autenticados. A efectos de prueba, también puede conceder estos permisos explícitamente al usuario del servicio de la puerta de enlace y al usuario de Active Directory que usará para hacer la prueba.

1. Si el servidor de BW todavía no está configurado para el inicio de sesión único con gx64krb5.dll, coloque otra copia del archivo .dll en la máquina del servidor de SAP BW en una ubicación a la que pueda acceder el servidor de SAP BW. 

    Consulte la [documentación de SAP](https://launchpad.support.sap.com/#/notes/2115486) (es necesario ser usuario-s de SAP) para más información sobre la configuración de gx64krb5.dll para su uso con un servidor de SAP BW.

1. En las máquinas del cliente y del servidor, establezca las variables de entorno **SNC_LIB** y **SNC_LIB_64**: 
    - Si usa gsskrb5.dll, establezca la variable **SNC_LIB** en su ruta de acceso absoluta. 
    - Si utiliza gx64krb5.dll, establezca la variable **SNC_LIB_64** en su ruta de acceso absoluta.

## <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>Configuración de un usuario de servicio de SAP BW y habilitación de la comunicación SNC en el servidor de BW

Complete esta sección si todavía no ha configurado el servidor de SAP BW para la comunicación SNC (por ejemplo, el inicio de sesión único) con gx64krb5.

> [!NOTE]
> En esta sección se supone que ya ha creado un usuario de servicio para BW y le ha enlazado un SPN adecuado (es decir, un nombre que empiece por *SAP/* ).

1. Otorgue al usuario del servicio acceso al servidor de aplicaciones de SAP BW:

    1. En la máquina del servidor de SAP BW, agregue el usuario de servicio al grupo de administradores locales. Abra el programa **Computer Management** (Administración de equipos) e identifique el grupo de administradores locales del servidor. 

        ![Programa Computer Management (Administración de equipos)](media/service-gateway-sso-kerberos/computer-management.png)

    1. Haga doble clic en el grupo Administrador local y haga clic en **Agregar** para agregar el usuario del servicio al grupo. 

    1. Seleccione **Check Names** (Comprobar nombres) para asegurarse de que ha escrito el nombre correctamente y seleccione **Aceptar**.

1. Establezca el usuario de servicio del servidor de SAP BW como el usuario que inicia el servicio del servidor de SAP BW en la máquina del servidor de SAP BW:

    1. Abra **Ejecutar** y escriba **Services.msc**. 

    1. Busque el servicio correspondiente a la instancia del servidor de aplicaciones SAP BW, haga clic en él con el botón derecho y seleccione **Propiedades**.

        ![Captura de pantalla de Servicios, con Propiedades resaltado](media/service-gateway-sso-kerberos/server-properties.png)

    1. Cambie a la pestaña **Inicio de sesión** y sustituya el usuario por el usuario del servicio de SAP BW. 

    1. Escriba la contraseña del usuario y seleccione **Aceptar**.

1. En el inicio de sesión de SAP, inicie sesión el servidor y establezca los siguientes parámetros de perfil mediante la transacción RZ10:

    1. Establezca el parámetro de perfil **snc/identity/as** en *p:&lt;usuario de servicio de SAP BW que ha creado&gt;* . Por ejemplo, *p:BWServiceUser\@MYDOMAIN.COM*. Tenga en cuenta que *p:* precede al UPN del usuario de servicio, en lugar de *p:CN=* , que precede al UPN al usarse CommonCryptoLib como biblioteca de SNC.

    1. Establezca el parámetro de perfil **snc/gssapi\_lib** en *&lt;ruta de acceso a gx64krb5.dll en el servidor de BW&gt;* . Coloque la biblioteca en una ubicación a la cual pueda acceder el servidor de aplicaciones de SAP BW.

    1. Establezca los siguientes parámetros de perfil adicionales; para ello, cambie los valores que necesite. Las últimas cinco opciones permiten a los clientes conectarse al servidor de SAP BW mediante el inicio de sesión de SAP sin necesidad de tener SNC configurado.

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

    1. Establezca la propiedad **snc/enable** en 1.

1. Después de establecer estos parámetros de perfil, abra la consola de administración de SAP en la máquina del servidor y reinicie la instancia de SAP BW. 

   Si no se inicia el servidor, confirme que ha establecido correctamente los parámetros de perfil. Para más información sobre la configuración de parámetros de perfil, consulte la [documentación de SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). También puede consultar la sección [Solución de problemas](#troubleshooting) de este artículo.

## <a name="map-an-sap-bw-user-to-an-active-directory-user"></a>Asignación de un usuario de SAP BW a un usuario de Active Directory

Si todavía no lo ha hecho, asigne un usuario de Active Directory a un usuario del servidor de aplicaciones de SAP BW y pruebe la conexión de inicio de sesión único en el inicio de sesión de SAP.

1. Inicie sesión el servidor de SAP BW mediante el inicio de sesión de SAP. Ejecute la transacción SU01.

1. En **User** (Usuario), escriba el usuario de SAP BW para el que desea habilitar la conexión de inicio de sesión único. Seleccione el icono **Edit** (Editar) (icono de lápiz) situado cerca de la parte superior izquierda de la ventana de inicio de sesión de SAP.

    ![Pantalla de mantenimiento de usuario de SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Seleccione la pestaña **SNC**. En el cuadro de entrada del nombre de SNC, escriba *p:&lt;su usuario de Active Directory&gt;@&lt;su dominio&gt;* . Para el nombre de SNC, la *p:* obligatoria debe preceder al UPN del usuario de Active Directory. Tenga en cuenta que el UPN distingue mayúsculas de minúsculas.

   El usuario de Active Directory que especifique debe pertenecer a la persona u organización para la cual quiere habilitar el acceso SSO al servidor de aplicaciones de SAP BW. Por ejemplo, si quiere habilitar el acceso de inicio de sesión único para el usuario testuser\@TESTDOMAIN.COM, escriba *p:testuser\@TESTDOMAIN.COM*.

    ![Pantalla Maintain users (Mantener usuarios) de SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Seleccione el icono **Save** (Guardar) (la imagen del disquete) cerca de la parte superior izquierda de la pantalla.

## <a name="test-sign-in-via-sso"></a>Prueba de inicio de sesión mediante el inicio de sesión único

Compruebe que puede iniciar sesión en el servidor mediante el inicio de sesión de SAP con el inicio de sesión único como el usuario de Active Directory para el cual acaba de habilitar el acceso mediante inicio de sesión único:

1. Con el usuario de Active Directory para el que acaba de habilitar el acceso mediante inicio de sesión único, inicie sesión en una máquina del dominio en el que esté instalado el inicio de sesión de SAP. Inicie el inicio de sesión de SAP y cree una conexión nueva.

1. Copie el archivo gsskrb5.dll que ha descargado antes en una ubicación de la máquina en la que ha iniciado sesión. Establezca la variable de entorno **SNC_LIB** en la ruta de acceso absoluta de esta ubicación.

1. Inicie el inicio de sesión de SAP y cree una conexión nueva.

1. En la pantalla **Create New System Entry** (Crear entrada del sistema), seleccione **User Specified System** (Sistema especificado del usuario) y **Next** (Siguiente).

    ![Pantalla Create new System Entry (Crear entrada del sistema)](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Rellene los detalles adecuados en la siguiente página, incluidos el servidor de aplicaciones, el número de instancia y el ID del sistema. A continuación, seleccione **Finish** (Finalizar).

1. Haga clic con el botón derecho en la nueva conexión, seleccione **Properties** (Propiedades) y la pestaña **Network** (Red). 

1. En el cuadro de texto **SNC Name** (Nombre de SNC), escriba *p:&lt;UPN del usuario de servicio de SAP BW&gt;* . Por ejemplo, *p:BWServiceUser\@MYDOMAIN.COM*. Seleccione **Aceptar**.

    ![Pantalla System Entry Properties (Propiedades de la entrada del sistema)](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Haga doble clic en la conexión que acaba de crear para intentar una conexión SSO al servidor SAP BW. 

   Si esta conexión se realiza correctamente, continúe con la siguiente sección. En caso contrario, revise los pasos anteriores de este documento para asegurarse de que los ha completado correctamente o revise la sección [Solución de problemas](#troubleshooting). Si no se puede conectarse al servidor de SAP BW mediante el inicio de sesión único en este contexto, no podrá conectarse al servidor de SAP BW mediante el inicio de sesión único en el contexto de la puerta de enlace.

## <a name="add-registry-entries-to-the-gateway-machine"></a>Adición de entradas del Registro a la máquina de puerta de enlace

Agregue las entradas del registro necesarias al registro de la máquina en la que está instalada la puerta de enlace y a las máquinas que se van a conectar desde Power BI Desktop. Para agregar estas entradas del registro, ejecute los siguientes comandos:

- ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

- ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

## <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Incorporación de un nuevo origen de datos de servidor de aplicaciones de SAP BW en el servicio Power BI o edición de uno existente

1. En la ventana de configuración del origen de datos, especifique el **nombre de host**, el **número del sistema** y el **ID de cliente** del servidor de aplicaciones de SAP BW como si fuera a iniciar sesión el servidor de SAP BW desde Power BI Desktop.

1. En el campo **Nombre de asociado de SNC**, escriba el *p:&lt;SPN que asignó al usuario de servicio de SAP BW&gt;* . Por ejemplo, si el SPN es SAP/BWServiceUser\@MYDOMAIN.COM, escriba *p:SAP/BWServiceUser\@MYDOMAIN.COM* en el campo **Nombre de asociado de SNC**.

1. Para la biblioteca de SNC, seleccione **SNC\_LIB** o **SNC\_LIB\_64**. En el equipo de la puerta de enlace, asegúrese de que **SNC\_LIB\_64** apunte a gx64krb5.dll. También puede seleccionar la opción **Personalizado** y proporcionar la ruta de acceso absoluta a gx64krb5.dll (en la máquina de la puerta de enlace).

1. Seleccione la casilla **Usar un SSO mediante Kerberos para las consultas de DirectQuery** y **Aplicar**. Si la conexión de prueba no es correcta, compruebe que los pasos de instalación y configuración anteriores se hayan completado correctamente.

1. [Ejecución de un informe de Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Solución de problemas

### <a name="troubleshoot-gx64krb5-configuration"></a>Solución de problemas con la configuración de gx64krb5

Si detecta alguno de estos problemas, realice los pasos siguientes para solucionar los problemas de instalación de gx64krb5 y de las conexiones de inicio de sesión único:

* Se producen errores al completar los pasos de configuración de gx64krb5. Por ejemplo, el servidor de SAP BW no se iniciará después de haber cambiado los parámetros de perfil. Consulte los registros del servidor (...work\dev\_w0 en la máquina del servidor) para solucionar estos errores. 

* No puede iniciar el servicio SAP BW debido a un error de inicio de sesión. Es posible que haya proporcionado una contraseña incorrecta al establecer el usuario *de inicio* de SAP BW. Inicie sesión en una máquina del entorno de Active Directory como usuario de servicio de SAP BW para comprobar la contraseña.

* Si recibe errores sobre las credenciales del origen de datos subyacente (por ejemplo, SQL Server) que impiden que se inicie el servidor, compruebe que le ha concedido el acceso de usuario de servicio a la base de datos de SAP BW.

* Recibirá el mensaje siguiente: *(GSS-API) specified target is unknown or unreachable* ([GSS-API] El destino especificado no es accesible o es desconocido). Normalmente, este error significa que se ha especificado un nombre de SNC incorrecto. Asegúrese de usar *p:* solo, no *p:CN=* antes del UPN del usuario de servicio en la aplicación cliente.

* Recibirá el mensaje siguiente: *(GSS-API) An invalid name was supplied* ([GSS-API] Se ha proporcionado un nombre no válido). Asegúrese de que *p:* es el valor del parámetro de perfil de identidad SNC del servidor.

* Recibirá el mensaje siguiente: *(SNC error) the specified module could not be found* ([Error de SNC] No se ha encontrado el módulo especificado). Este error suele deberse a la colocación de gx64krb5.dll en una ubicación que requiere privilegios elevados (derechos de administrador) de acceso.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Solución de problemas de conectividad de la puerta de enlace

1. Compruebe los registros de la puerta de enlace. Abra la aplicación de configuración de la puerta de enlace, seleccione **Diagnósticos** y después **Exportar registros**. Los errores más recientes están en la parte inferior de los archivos de registro que examine.

    ![Aplicación de la puerta de enlace de datos local, con Diagnósticos resaltado](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Active el seguimiento de SAP BW y revise los archivos de registro generados. Hay varios tipos de seguimiento de SAP BW disponibles (por ejemplo, el seguimiento de CPIC):

   a. Para habilitar el seguimiento de CPIC, establezca dos variables de entorno: **CPIC\_TRACE** y **CPIC\_TRACE\_DIR**.

      La primera variable establece el nivel de seguimiento y la segunda, el directorio del archivo de seguimiento. El directorio debe ser una ubicación en la que puedan escribir los miembros del grupo de usuarios autenticados. 
 
    b. Establezca **CPIC\_TRACE** en *3* y **CPIC\_TRACE\_DIR** en el directorio en el que quiere que se escriban los archivos de seguimiento. Por ejemplo:

      ![Seguimiento de CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    c. Reproduzca el problema y asegúrese de que **CPIC\_TRACE\_DIR** contiene archivos de seguimiento. 
    
    d. Examine el contenido de los archivos de seguimiento para determinar el problema de bloqueo. Por ejemplo, puede que gx64krb5.dll no se haya cargado correctamente o que un usuario de Active Directory distinto del que esperaba que iniciara el intento de conexión de SSO.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la puerta de enlace de datos local y DirectQuery, consulte los recursos siguientes:

* [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
