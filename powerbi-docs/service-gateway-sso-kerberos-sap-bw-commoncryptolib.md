---
title: Uso del inicio de sesión único de Kerberos para el SSO en SAP BW con CommonCryptoLib (sapcrypto.dll)
description: Configuración del servidor de SAP BW para habilitar el SSO del servicio Power BI con CommonCryptoLib (sapcrypto.dll)
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 02c8ac991fbf84051ae795ef4a80f2b3dc07a1ce
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000190"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>Uso del inicio de sesión único de Kerberos para el SSO en SAP BW con CommonCryptoLib (sapcrypto.dll)

En este artículo se describe cómo configurar el origen de datos de SAP BW para habilitar el inicio de sesión único del servicio Power BI mediante CommonCryptoLib (sapcrypto.dll).

> [!NOTE]
> Antes de intentar actualizar un informe basado en SAP BW que usa el inicio de sesión único de Kerberos, complete los dos pasos de este artículo y los de [Configuración del inicio de sesión único de Kerberos](service-gateway-sso-kerberos.md). El uso de CommonCryptoLib como la biblioteca de SNC permite establecer conexiones SSO tanto a los servidores de aplicaciones de SAP BW como a los servidores de mensajería de SAP BW.

## <a name="configure-sap-bw-to-enable-sso-using-commoncryptolib"></a>Configuración de SAP BW para habilitar el SSO mediante CommonCryptoLib

> [!NOTE]
> La puerta de enlace de datos local es software de 64 bits, por lo que se requiere la versión de 64 bits de CommonCryptoLib (sapcrypto.dll) para realizar el SSO de BW. Si planea probar la conexión de inicio de sesión único al servidor de SAP BW en la interfaz gráfica de usuario de SAP antes de intentar una conexión de inicio de sesión único mediante la puerta de enlace (procedimiento recomendado), también necesitará la versión de 32 bits de CommonCryptoLib, ya que la interfaz gráfica de usuario de SAP es un software de 32 bits.

1. Asegúrese de que el servidor de BW está configurado correctamente para el SSO de Kerberos con CommonCryptoLib. Si es así, puede usar el inicio de sesión único para acceder al servidor de BW (ya sea de manera directa o mediante un servidor de mensajería de SAP BW) con una herramienta de SAP como la interfaz gráfica de usuario que se configuró para usar CommonCryptoLib. 

   Para obtener más información sobre los pasos de configuración, consulte [SAP Single Sign-On: Authenticate with Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/) (Inicio de sesión único de SAP: Autenticarse con Kerberos/SPNEGO). El servidor de BW debe usar CommonCryptoLib como biblioteca de SNC y tener un nombre de SNC que empiece por *CN=* , como *CN=BW1*. Para más información sobre los requisitos de nombre de SNC (en particular el parámetro snc/identity/as), consulte los [Parámetros de SNC para la configuración de Kerberos](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/360534094511490d91b9589d20abb49a.html).

1. Si aún no lo ha hecho, instale la versión x64 del [conector .NET de SAP](https://support.sap.com/en/product/connectors/msnet.html) en el equipo en el que se ha instalado la puerta de enlace. 
   
   Puede comprobar si el componente se ha instalado si se intenta conectar al servidor de BW en Power BI Desktop desde el equipo de puerta de enlace. Si no se puede conectar con la implementación 2.0, el conector .NET no está instalado o no se ha instalado en la caché global de ensamblados.

1. Asegúrese de que Secure Login Client (SLC) de SAP no se esté ejecutando en el equipo en el que está instalada la puerta de enlace. 

   SLC almacena en caché los vales de Kerberos de forma que puede interferir con la posibilidad de que la puerta de enlace use Kerberos para SSO. 

1. Si SLC está instalado, desinstálelo o asegúrese de salir de Secure Login Client de SAP. Haga clic con el botón derecho en el icono de la bandeja del sistema y seleccione **Log out** (Cerrar sesión) y **Salir** antes de intentar una conexión de inicio de sesión único mediante la puerta de enlace. 

   No se admite el uso de SLC en máquinas con Windows Server. Para obtener más información, consulte la [nota 2780475 de SAP](https://launchpad.support.sap.com/#/notes/2780475) (se requiere s-user).

   ![SAP Secure Login Client](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

1. Si desinstala SLC o selecciona **Log Out** (Cerrar sesión) y **Salir**, abra una ventana de comandos y escriba `klist purge` para borrar cualquier vale de Kerberos almacenado en caché antes de intentar una conexión de inicio de sesión único mediante la puerta de enlace.

1. Descargue la versión *8.5.25 o posterior* de CommonCryptoLib (sapcrypto.dll) de 64 bits desde SAP Launchpad y cópiela en una carpeta de la máquina de la puerta de enlace. En el mismo directorio donde copió sapcrypto.dll, cree un archivo denominado sapcrypto.ini con el siguiente contenido:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    El archivo .ini contiene información de configuración requerida por CommonCryptoLib para habilitar el inicio de sesión único en el escenario de puerta de enlace.

    > [!NOTE]
    > Estos archivos se deben almacenar en la misma ubicación; en otras palabras, _/path/to/sapcrypto/_ debe contener tanto sapcrypto.ini como sapcrypto.dll.

    Tanto el usuario de servicio de la puerta de enlace como el usuario de Active Directory (AD) que el primero va a suplantar necesitan permisos de lectura y ejecución para ambos archivos. Se recomienda conceder permisos para los archivos .ini y .dll al grupo de usuarios autenticados. A efectos de prueba, también puede conceder estos permisos explícitamente al usuario de servicio de la puerta de enlace y al usuario de Active Directory que usará para hacer la prueba. En la captura de pantalla siguiente se ha concedido al grupo de usuarios autenticados permisos de **lectura y ejecución** en sapcrypto.dll:

    ![Usuarios autenticados](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Si todavía no tiene un origen de datos de SAP BW asociado a la puerta de enlace a través de la que quiere que se transmita la conexión de SSO, agregue uno en la página **Administrar puertas de enlace** del servicio Power BI. Si ya tiene este tipo de origen de datos, edítelo: 
    - Elija **SAP Business Warehouse** como el **tipo de origen de datos** si quiere crear una conexión SSO a un servidor de aplicaciones de BW. 
    - Seleccione **Servidor de mensajería de SAP Business Warehouse** si quiere crear una conexión SSO a un servidor de mensajería de BW.

1. Como **Biblioteca de SNC**, seleccione la variable de entorno **SNC\_LIB** o **SNC\_LIB\_64** o **Personalizada**. 

   - Si selecciona **SNC\_LIB**, debe establecer el valor de la variable de entorno **SNC\_LIB\_64** en la máquina de la puerta de enlace en la ruta de acceso absoluta de la copia de sapcrypto.dll de 64 bits de la máquina de la puerta de enlace, por ejemplo, *C:\Users\Test\Desktop\sapcrypto.dll*.

   - Si elige **Personalizada**, pegue la ruta de acceso absoluta a *sapcrypto.dll* en el campo Ruta de biblioteca SNC personalizada que aparece en la página **Administrar puertas de enlace**. 

1. En **Nombre de asociado de SNC**, escriba el nombre de SNC del servidor de BW. En **Configuración avanzada**, asegúrese de que la opción **Usar SSO mediante Kerberos para las consultas de DirectQuery** esté activada. Rellene los demás campos como si estuviera estableciendo una conexión de autenticación de Windows desde PBI Desktop.

1. Cree una variable de entorno del sistema **CCL\_PROFILE** y establezca su valor en la ruta de acceso a sapcrypto.ini.

    ![Variable de entorno del sistema CCL\_PROFILE](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Los archivos .dll e .ini de sapcrypto deben estar en la misma ubicación. En el ejemplo anterior, sapcrypto.ini y sapcrypto.dll se encuentran en el escritorio.

1. Reinicie el servicio de puerta de enlace.

    ![Reinicio del servicio de puerta de enlace](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Ejecución de un informe de Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Solución de problemas

Si no puede actualizar el informe en el servicio Power BI, puede usar el seguimiento de puerta de enlace, el seguimiento de CPIC y de CommonCryptoLib para diagnosticar el problema. Como el seguimiento de CPIC y CommonCryptoLib son productos de SAP, Microsoft no puede ofrecer compatibilidad directa con ellos.

### <a name="gateway-logs"></a>Registros de puerta de enlace

1. Reproduzca el problema.

2. Abra la [aplicación de puerta de enlace](https://docs.microsoft.com/data-integration/gateway/service-gateway-app) y seleccione **Exportar registros** de la pestaña **Diagnóstico**.

      ![Exportación de registros de puerta de enlace](media/service-gateway-sso-kerberos/export-gateway-logs.png)

### <a name="cpic-tracing"></a>Seguimiento de CPIC

1. Para habilitar el seguimiento de CPIC, establezca dos variables de entorno: **CPIC\_TRACE** y **CPIC\_TRACE\_DIR**. 

   La primera variable establece el nivel de seguimiento y la segunda, el directorio del archivo de seguimiento. El directorio debe ser una ubicación en la que puedan escribir los miembros del grupo de usuarios autenticados. 
 
2. Establezca **CPIC\_TRACE** en *3* y **CPIC\_TRACE\_DIR** en el directorio en el que quiere que se escriban los archivos de seguimiento. Por ejemplo:

   ![Seguimiento de CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

3. Reproduzca el problema y asegúrese de que **CPIC\_TRACE\_DIR** contiene archivos de seguimiento.
 
    El seguimiento de CPIC puede diagnosticar problemas de nivel superior, como un error al cargar la biblioteca sapcrypto.dll. Por ejemplo, el siguiente es un fragmento de un archivo de seguimiento de CPIC donde se produjo un error de carga de .dll:

    ```
    [Thr 7228] *** ERROR => DlLoadLib()==DLENOACCESS - LoadLibrary("C:\Users\test\Desktop\sapcrypto.dll")
    Error 5 = "Access is denied." [dlnt.c       255]
    ```

    Si se produce un error de este estilo, pero estableció los permisos de lectura y ejecución en sapcrypto.dll y sapcrypto.ini tal como se describe en la [sección anterior](#configure-sap-bw-to-enable-sso-using-commoncryptolib), intente establecer los mismos permisos de lectura y escritura en la carpeta que contiene los archivos.

    Si sigue sin poder cargar el .dll, intente activar la [auditoría del archivo](/windows/security/threat-protection/auditing/apply-a-basic-audit-policy-on-a-file-or-folder). Examinar los registros de auditoría resultantes en el Visor de eventos de Windows puede ayudarlo a determinar por qué se produce el error de carga. Busque una entrada de error iniciada por el usuario de Active Directory suplantado. Por ejemplo, para el usuario suplantado `MYDOMAIN\mytestuser`, un error del registro de auditoría tendría un aspecto similar al siguiente:

    ```
    A handle to an object was requested.

    Subject:
        Security ID:        MYDOMAIN\mytestuser
        Account Name:       mytestuser
        Account Domain:     MYDOMAIN
        Logon ID:       0xCF23A8

    Object:
        Object Server:      Security
        Object Type:        File
        Object Name:        <path information>\sapcrypto.dll
        Handle ID:      0x0
        Resource Attributes:    -

    Process Information:
        Process ID:     0x2b4c
        Process Name:       C:\Program Files\On-premises data gateway\Microsoft.Mashup.Container.NetFX45.exe

    Access Request Information:
        Transaction ID:     {00000000-0000-0000-0000-000000000000}
        Accesses:       ReadAttributes
                
    Access Reasons:     ReadAttributes: Not granted
                
    Access Mask:        0x80
    Privileges Used for Access Check:   -
    Restricted SID Count:   0
    ```

### <a name="commoncryptolib-tracing"></a>Seguimiento de CommonCryptoLib 

1. Active el seguimiento de CommonCryptoLib agregando estas líneas al archivo sapcrypto.ini que creó anteriormente:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

2. Cambie la opción `ccl/trace/directory` a una ubicación donde los miembros del grupo de usuarios autenticados puedan escribir. 

3. También puede crear otro archivo .ini para cambiar este comportamiento. En el mismo directorio en que están sapcrypto.ini y sapcrypto.dll, cree un archivo denominado sectrace.ini con el contenido siguiente. Reemplace la opción `DIRECTORY` por una ubicación en la máquina en la que los miembros del grupo de usuarios autenticados puedan escribir:

    ```
    LEVEL = 5
    DIRECTORY = <drive>:\logs\sectrace
    ```

4. Reproduzca el problema y compruebe que la ubicación a la que apunta **DIRECTORY** contiene archivos de seguimiento. 

5. Cuando haya terminado, desactive el seguimiento de CPIC y CCL.

    Para más información sobre el seguimiento de CommonCryptoLib, consulte la [nota 2491573 de SAP](https://launchpad.support.sap.com/#/notes/2491573) (es necesario ser usuario-s de SAP).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la puerta de enlace de datos local y DirectQuery, consulte los recursos siguientes:

* [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
