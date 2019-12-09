---
title: 'Solución de problemas de puertas de enlace: Power BI'
description: En este artículo se proporcionan formas de solucionar los problemas que surjan con la puerta de enlace de datos local y Power BI. Proporciona posibles soluciones a problemas conocidos, así como herramientas para ayudarle.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: troubleshooting
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 73e2c923500a2d78072a711bc7662a5923811bba
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699346"
---
# <a name="troubleshoot-gateways---power-bi"></a>Solución de problemas de puertas de enlace: Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

En este artículo se examinan algunos problemas comunes del uso de la puerta de enlace de datos local con Power BI. Si encuentra un problema que no aparece aquí, puede usar el sitio de la [Comunidad](https://community.powerbi.com) de Power BI. O bien, puede crear una [incidencia de soporte técnico](https://powerbi.microsoft.com/support).

## <a name="configuration"></a>Configuración

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>Error: el servicio Power BI informó de que no se puede acceder a la puerta de enlace local. Reinicie la puerta de enlace e inténtelo de nuevo.

Cuando finalice la configuración, se vuelve a llamar al servicio Power BI para validar la puerta de enlace. El servicio Power BI no informa de que la puerta de enlace sea dinámica. El reinicio del servicio de Windows puede permitir que la comunicación se realice correctamente. Para obtener más información, puede recopilar y revisar los registros, como se describe en [Recopilación de registros de la aplicación de puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

## <a name="data-sources"></a>Orígenes de datos

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>Error: No se puede conectar. Detalles: "Credenciales de conexión no válidas"

En **Mostrar detalles**, se muestra el mensaje de error recibido desde el origen de datos. En el caso de SQL Server, se ve algo parecido a lo siguiente:

    Login failed for user 'username'.

Compruebe que tenga el nombre de usuario y la contraseña correctos. Además, compruebe que esas credenciales puedan conectarse correctamente con el origen de datos. Asegúrese de que la cuenta que se usa coincide con el método de autenticación.

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>Error: No se puede conectar. Detalles: "No se puede conectar con la base de datos"

Pudo conectarse al servidor, pero no a la base de datos proporcionada. Compruebe el nombre de la base de datos y que la credencial del usuario tenga el permiso adecuado para acceder a esa base de datos.

En **Mostrar detalles**, se muestra el mensaje de error recibido desde el origen de datos. En el caso de SQL Server, se ve algo parecido a lo siguiente:

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>Error: No se puede conectar. Detalles: "Error desconocido en la puerta de enlace de datos"

Este error puede producirse por diferentes motivos. Asegúrese de validar que puede conectarse al origen de datos desde la máquina que hospeda la puerta de enlace. Esta situación podría deberse a la imposibilidad de acceder al servidor.

En **Mostrar detalles**, puede ver el código de error **DM_GWPipeline_UnknownError**.

También puede mirar en **Registros de eventos** > **Registros de aplicaciones y servicios** > **Servicio de puerta de enlace de datos local** para más información.

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>Error: Hemos detectado un error al intentar conectar con \<servidor\>. Detalles: "Se conectó con una puerta de enlace de datos, pero esta no puede acceder al origen de datos en el entorno local".

No se pudo establecer la conexión al origen de datos especificado. Asegúrese de validar la información proporcionada para ese origen de datos.

En **Mostrar detalles**, puede ver el código de error **DM_GWPipeline_Gateway_DataSourceAccessError**.

Si el mensaje de error subyacente es similar al siguiente, significa que la cuenta que usa para el origen de datos no es un administrador del servidor para esa instancia de Analysis Services. Para más información, consulte [Concesión de derechos de administrador de servidor a una instancia de Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance).

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

Si el mensaje de error subyacente es similar al siguiente, podría significar que en la cuenta de servicio para Analysis Services es posible que falte el atributo de directorio [token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx) (TGGAU).

    The username or password is incorrect.

Los dominios con acceso de compatibilidad de versiones anteriores a Windows 2000 tienen el atributo TGGAU habilitado. Los dominios creados más recientemente no permiten este atributo de forma predeterminada. Para más información, consulte [Algunas aplicaciones y API requieren acceso a información de autorización en los objetos de cuenta](https://support.microsoft.com/kb/331951).

Para confirmar si el atributo está habilitado, siga estos pasos.

1. Conéctese con el equipo de Analysis Services en SQL Server Management Studio. En las propiedades avanzadas de conexión, incluya EffectiveUserName para el usuario en cuestión y compruebe si esta adición reproduce el error.
2. Puede usar la herramienta dsacls de Active Directory para comprobar si se muestra el atributo. Esta herramienta se encuentra en un controlador de dominio. Debe saber cuál es el nombre de dominio distintivo de la cuenta y pasar dicho nombre a la herramienta.

        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"

    En los resultados querrá ver algo parecido a lo siguiente:

            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

Para corregir este problema, debe habilitar TGGAU en la cuenta usada para el servicio de Windows de Analysis Services.

#### <a name="another-possibility-for-the-username-or-password-is-incorrect"></a>Otra posibilidad es que el nombre de usuario o la contraseña no sean correctos.

Este error también se puede producir si el servidor de Analysis Services está en un dominio diferente al de los usuarios y no hay una confianza bidireccional establecida.

Tiene que trabajar con los administradores del dominio para verificar la relación de confianza entre dominios.

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>Unable to see the data gateway data sources in the 'Get Data' experience for Analysis Services from the Power BI service (No se pueden ver orígenes de datos de la puerta de enlace de datos en la experiencia "Obtener datos" para Analysis Services desde el servicio Power BI)

Asegúrese de que su cuenta aparece en la ficha **Usuarios** del origen de datos dentro de la configuración de puerta de enlace. Si no tiene acceso a la puerta de enlace, consulte con el administrador de la puerta de enlace y pídale que realice la comprobación. Solo las cuentas de la lista **Usuarios** pueden ver el origen de datos enumerado en la lista de Analysis Services.

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>Error: No tiene ninguna puerta de enlace instalada o configurada para los orígenes de datos de este conjunto de datos.

Asegúrese de que haya agregado al menos un origen de datos a la puerta de enlace, tal como se describe en [Adición de un origen de datos](service-gateway-data-sources.md#add-a-data-source). Si la puerta de enlace no se muestra en **Administrar puertas de enlace** en el portal de administración, intente borrar la memoria caché del explorador o cerrar sesión en el servicio. Después, vuelva a iniciar sesión.

## <a name="datasets"></a>Conjuntos de datos

### <a name="error-there-is-not-enough-space-for-this-row"></a>Error: No hay suficiente espacio para esta fila.

Este error se produce si tiene una sola fila que ocupe más de 4 MB. Determine de qué fila del origen de datos se trata e intentar filtrarla o reducir su tamaño.

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>Error: El nombre del servidor proporcionado no coincide con el nombre del servidor en el certificado SSL de SQL Server.

Este error puede ocurrir cuando el nombre común del certificado es para el nombre de dominio completo (FQDN) del servidor, pero solo se ha proporcionado el nombre NETBIOS para el servidor. Esto provoca un error de coincidencia del certificado. Para resolver este problema, debe hacer que el nombre del servidor dentro del origen de datos de la puerta de enlace y del archivo PBIX use el nombre de dominio completo del servidor.

### <a name="error-you-dont-see-the-on-premises-data-gateway-present-when-you-configure-scheduled-refresh"></a>Error: No veo la puerta de enlace de datos local al configurar la actualización programada.

Algunos escenarios diferentes podrían ser responsables de este error:

- El nombre del servidor y de la base de datos no coinciden con lo que se especificó en Power BI Desktop y el origen de datos configurado para la puerta de enlace. Estos nombres deben ser los mismos. No distinguen mayúsculas de minúsculas.
- La cuenta no aparece en la pestaña **Usuarios** del origen de datos dentro de la configuración de la puerta de enlace. El administrador de la puerta de enlace debe agregarle a esa lista.
- El archivo de Power BI Desktop contiene varios orígenes de datos y no todos están configurados con la puerta de enlace de datos. Debe hacer que cada origen de datos esté definido con la puerta de enlace para que esta aparezca en la actualización programada.

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>Error: Los datos no comprimidos recibidos en el cliente de la puerta de enlace han superado el límite.

El límite exacto es de 10 GB de datos sin comprimir por tabla. Si surge este problema, existen opciones para optimizar y evitar el problema. En concreto, puede reducir el uso de valores de cadena muy repetitivos y largos y, en su lugar, utilizar una clave normalizada. También resulta útil quitar la columna si no está en uso.

## <a name="reports"></a>Informes

### <a name="error-report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>Error: El informe no pudo acceder al origen de datos porque no tiene acceso a nuestro origen de datos a través de una puerta de enlace de datos local.

Este error puede deberse a uno de los siguientes motivos:

- La información del origen de datos no coincide con el conjunto de datos subyacente. El servidor y el nombre de la base de datos deben coincidir con el origen de datos definido para la puerta de enlace de datos local y con lo que se suministra en Power BI Desktop. Si usa una dirección IP en Power BI Desktop, el origen de datos para la puerta de enlace de datos local también debe usar una dirección IP.
- No hay ningún origen de datos disponible en ninguna puerta de enlace en la organización. Puede configurar el origen de datos en una puerta de enlace de datos local nueva o existente.

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>Error: Error de acceso al origen datos. Póngase en contacto con el administrador de la puerta de enlace.

Si este informe usa una conexión activa de Analysis Services, podría producirse un problema con un valor que se pasa a EffectiveUserName y que no es válido o bien no tiene permisos en el equipo de Analysis Services. Normalmente, un problema de autenticación se debe a que el valor que se pasa para EffectiveUserName no coincide con un nombre principal de usuario local (UPN).

Para confirmar el nombre de usuario efectivo, siga estos pasos.

1. Busque el nombre de usuario efectivo en los [registros de puerta de enlace](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).
2. Después de obtener el valor que se pasa, compruebe que es correcto. Si es su usuario, puede utilizar el siguiente comando desde un símbolo del sistema para ver el UPN. Su aspecto es parecido a una dirección de correo electrónico.

        whoami /upn

También puede ver qué obtiene Power BI de Azure Active Directory.

1. Vaya a [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Seleccione **Iniciar sesión** en la esquina superior derecha.
3. Ejecute la siguiente consulta. Verá una respuesta JSON bastante grande.

        https://graph.windows.net/me?api-version=1.5
4. Busque **userPrincipalName**.

Si el UPN de Azure Active Directory no coincide con el UPN local de Active Directory, puede usar la característica [Asignar nombres de usuario](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources) para cambiarlo por un valor válido. O bien, puede ponerse en contacto con su administrador de inquilinos o administrador de Active Directory local para que cambie el UPN.

## <a name="kerberos"></a>Kerberos

Si el servidor de base de datos subyacente y la puerta de enlace de datos local no están configurados correctamente para la [delegación restringida de Kerberos](service-gateway-sso-kerberos.md), habilite el [registro detallado](/data-integration/gateway/service-gateway-performance#slow-performing-queries) en la puerta de enlace. Después, investigue en función de los errores o seguimientos de los archivos de registro de la puerta de enlace como punto de partida para la solución de problemas. Para recopilar los registros de puerta de enlace para su visualización, vea [Recopilación de registros desde la aplicación de puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

### <a name="impersonationlevel"></a>ImpersonationLevel

ImpersonationLevel está relacionado con la configuración del SPN o la configuración de directiva local.

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**Solución**

Siga estos pasos para solucionar el problema.

1. Configure un SPN para la puerta de enlace local.
2. Configure la delegación restringida en Active Directory.

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException: No se pudo crear la identidad de Windows para el userid del usuario

Se produce la excepción FailedToImpersonateUserException si no se puede suplantar a otro usuario. Este error también puede ocurrir si la cuenta que intenta suplantar es de un dominio distinto al del servicio de puerta de enlace. Esta es una limitación.

**Solución**

* Compruebe que la configuración sea correcta según los pasos descritos en la sección "ImpersonationLevel" anterior.
* Asegúrese de que el identificador de usuario que intenta suplantar es una cuenta de Active Directory válida.

### <a name="general-error-1033-error-while-you-parse-the-protocol"></a>Error general: error 1033 al analizar el protocolo

Recibe el error 1033 cuando el identificador externo que está configurado en SAP HANA no coincide con el inicio de sesión si el usuario se suplanta con el UPN (alias@domain.com). En los registros, aparece el UPN original "alias@domain.com" reemplazado por un UPN "alias@domain.com" nuevo en la parte superior de los registros de errores, como se muestra aquí:

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**Solución**

* SAP HANA requiere que el usuario suplantado use el atributo sAMAccountName en Active Directory (alias de usuario). Si este atributo no es correcto, verá el error 1033.

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount.png)

* En los registros verá el valor sAMAccountName (alias) y no el UPN, que es el alias seguido del dominio (alias@doimain.com).

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] Communication link failure;-10709 Connection failed (RTE:[-1] Kerberos error. Principal: "Miscellaneous failure [851968]" (Error diverso [851968]). Secundario: "No credentials are available in the security package" (No hay credenciales disponibles en el paquete de seguridad)

Recibe el mensaje de error "-10709 Error de conexión" si la delegación no está configurada correctamente en Active Directory.

**Solución**

* Asegúrese de tener el servidor SAP HANA en la pestaña de delegación en Active Directory para la cuenta de servicio de puerta de enlace.

   ![Pestaña Delegación](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="refresh-history"></a>Actualizar historial

Cuando se usa la puerta de enlace para una actualización programada, **Actualizar historial** puede ayudarle a ver los errores que se han producido. También puede proporcionar datos útiles si necesita crear una solicitud de soporte técnico. Puede ver las actualizaciones programadas y las actualizaciones a petición. En los pasos siguientes se muestra cómo acceder a la opción de actualizar historial.

1. En el panel de navegación de Power BI, seleccione un conjunto de datos en **Conjuntos de datos**. Abra el menú y seleccione **Programar actualización**.

    ![Procedimientos para seleccionar Programar actualización](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. En **Configuración de...** &gt; **Programar actualización**, seleccione **Actualizar historial**.

    ![Selección de Actualizar historial](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![Representación de Actualizar historial](media/service-gateway-onprem-tshoot/refresh-history.png)

Para más información sobre la solución de problemas de escenarios de actualización, consulte [Solución de problemas de escenarios de actualización](refresh-troubleshooting-refresh-scenarios.md).

## <a name="fiddler-trace"></a>Seguimiento de Fiddler

[Fiddler](https://www.telerik.com/fiddler) es una herramienta gratuita de Telerik que supervisa el tráfico HTTP. Puede ver todas las perspectivas con el servicio Power BI desde el equipo cliente. Esta lista de tráfico puede mostrar errores y otra información relacionada.

![Uso del seguimiento de Fiddler](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>Pasos siguientes

* [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot)
* [Configuración de los valores del proxy para la puerta de enlace de datos local](/data-integration/gateway/service-gateway-proxy)  
* [Administrar el origen de datos: Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Administrar el origen de datos: SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Administrar el origen de datos: SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Administrar el origen de datos: importación o actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md)  

¿Tiene más preguntas? Consulte la [Comunidad de Power BI](https://community.powerbi.com/).
