---
title: Solución de problemas de una aplicación insertada
description: En este artículo se examinan algunos problemas comunes que pueden encontrarse al insertar contenido desde Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: troubleshooting
ms.date: 02/05/2019
ms.openlocfilehash: 7bb380a5b54ad3d844edd1596332316ae3b7b209
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74264103"
---
# <a name="troubleshoot-your-embedded-application"></a>Solución de problemas de una aplicación insertada

En este artículo se examinan algunos problemas comunes que pueden encontrarse al insertar contenido desde Power BI.

## <a name="tools-to-troubleshoot"></a>Herramientas para la solución de problemas

### <a name="fiddler-trace"></a>Seguimiento de Fiddler

[Fiddler](https://www.telerik.com/fiddler) es una herramienta gratuita de Telerik que supervisa el tráfico HTTP.  Puede ver el tráfico con las API de Power BI desde la máquina cliente. Esta herramienta puede mostrar errores y otra información relacionada.

![Seguimiento de Fiddler](media/embedded-troubleshoot/fiddler.png)

### <a name="f12-in-browser-for-front-end-debugging"></a>F12 en el explorador para la depuración del servidor front-end.

F12 inicia la ventana del desarrollador en el explorador. Esta herramienta ofrece la posibilidad de ver el tráfico de red y otra información.

![F12 Depuración del explorador](media/embedded-troubleshoot/browser-f12.png)

### <a name="extract-error-details-from-power-bi-response"></a>Extracción de detalles del error a partir de la respuesta de Power BI

Este fragmento de código muestra cómo extraer los detalles del error de la excepción de HTTP:

```csharp
public static string GetExceptionText(this HttpOperationException exc)
{
    var errorText = string.Format("Request: {0}\r\nStatus: {1} ({2})\r\nResponse: {3}",
    exc.Request.Content, exc.Response.StatusCode, (int)exc.Response.StatusCode, exc.Response.Content);
    if (exc.Response.Headers.ContainsKey("RequestId"))
    {
        var requestId = exc.Response.Headers["RequestId"].FirstOrDefault();
        errorText += string.Format("\r\nRequestId: {0}", requestId);
    }

    return errorText;
}
```

Se recomienda registrar los identificadores de solicitud (y los detalles del error para solucionar el problema).
Proporcione el identificador de solicitud cuando entre en contacto con el equipo de soporte técnico de Microsoft.

## <a name="app-registration"></a>Registro de la aplicación

### <a name="app-registration-failure"></a>Error en el registro de la aplicación

Los mensajes de error de Azure Portal o de la página de registro de aplicaciones de Power BI indican que no hay privilegios suficientes. Para registrar una aplicación, debe ser administrador en el inquilino de Azure AD o los registros de aplicaciones deben estar habilitados para los usuarios que no son administradores.

### <a name="power-bi-service-doesnt-appear-in-the-azure-portal-when-registering-a-new-app"></a>El servicio Power BI no aparece en Azure Portal al registrar una nueva aplicación

Al menos un usuario debe estar registrado en Power BI. Si no ve **Servicio Power BI** en la lista de API, significa que no hay usuarios suscritos a Power BI.

## <a name="rest-api"></a>API de REST

### <a name="api-call-returning-401"></a>La llamada a la API devuelve 401

Es posible que se necesite una captura de Fiddler para poder investigar más. El ámbito de permisos requerido pueden faltar en la aplicación registrada en Azure AD. Compruebe que el ámbito necesario se encuentra en el registro de aplicaciones de Azure AD en Azure Portal.

### <a name="api-call-returning-403"></a>La llamada a la API devuelve 403

Es posible que se necesite una captura de Fiddler para poder investigar más. El error 403 puede deberse a varios motivos.

* El usuario ha superado la cantidad de tokens de inserción que se pueden generar en una capacidad compartida. Adquiera capacidades de Azure para generar tokens de inserción y asignar el área de trabajo a esa capacidad. Vea [Creación de una capacidad de Power BI Embedded en Azure Portal](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity).
* El token de autenticación de Azure AD ha expirado.
* El usuario autenticado no es miembro del grupo (área de trabajo).
* El usuario autenticado no es administrador del grupo (área de trabajo).
* El usuario autenticado no tiene permisos. Los permisos se pueden actualizar con la [API refreshUserPermissions](https://docs.microsoft.com/rest/api/power-bi/users/refreshuserpermissions)
* Es posible que el encabezado de la autorización no aparezca correctamente. Asegúrese de que no hay errores tipográficos.

Es posible que el back-end de la aplicación tenga que actualizar el token de autenticación antes de llamar a GenerateToken.

    ```
    GET https://wabi-us-north-central-redirect.analysis.windows.net/metadata/cluster HTTP/1.1
    Host: wabi-us-north-central-redirect.analysis.windows.net
    ...
    Authorization: Bearer eyJ0eXAiOi...
    ...

    HTTP/1.1 403 Forbidden
    ...

    {"error":{"code":"TokenExpired","message":"Access token has expired, resubmit with a new access token"}}
    ```

## <a name="authentication"></a>Autenticación

### <a name="authentication-failed-with-aadsts90002-tenant-authorize-not-found"></a>Error de autenticación AADSTS90002: No se ha encontrado el inquilino "authorize"

 Si recibe mensajes de registro como ***error: invalid_request, error_description: AADSTS90002: No se ha encontrado el inquilino "authorize"***, se debe a que ADAL 4.x no admite "https://login.microsoftonline.com/{Tenant}/oauth2/authorize/" como una dirección URL de autoridad.
 
Para resolver este problema, debe quitar "oauth2/authorize/" del final de la dirección URL de la autoridad, vea [Power BI Developer Samples](https://github.com/Microsoft/PowerBI-Developer-Samples) (Ejemplos para desarrolladores de Power BI) como referencia.

 Consulte [Better Authority validation](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Changes-adalnet-4.0#better-authority-validation) (Validación de autoridades mejorada) en las notas de la versión de ADAL 4.x.

### <a name="authentication-failed-with-aadsts70002-or-aadsts50053"></a>Error de autenticación AADSTS70002 o AADSTS50053

**_(AADSTS70002: Error al validar las credenciales. AADSTS50053: Ha intentado iniciar sesión demasiadas veces con un identificador de usuario o una o contraseña incorrectos)_**

Si usa Power BI Embedded y recurre a la autenticación directa de Azure AD, y recibe mensajes de registro como ***error:unauthorized_client,error_description:AADSTS70002: Error al validar las credenciales. AADSTS50053: Ha intentado iniciar sesión demasiadas veces con un identificador de usuario o una o contraseña incorrectos***, se debe a que la autenticación directa dejó de usarse de forma predeterminada el 14 de junio de 2018.

Hay una manera de volver a activar esta opción por medio de una [directiva de Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/configure-authentication-for-federated-users-portal#enable-direct-authentication-for-legacy-applications), que se puede limitar al ámbito de la organización o a una [entidad de servicio](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects#service-principal-object).

Se recomienda que habilite esta directiva solo por aplicación.

Para crear esta directiva, debe ser un **administrador global** en el directorio donde esté creando y asignando la directiva. Este es un script de ejemplo para crear la directiva y asignarla a la entidad de servicio en esta aplicación:

1. Instale el [módulo de versión preliminar de Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).

2. Ejecute los siguientes comandos de PowerShell línea a línea (procurando que la variable $sp no tenga más de una aplicación como resultado).

```powershell
Connect-AzureAD
```

```powershell
$sp = Get-AzureADServicePrincipal -SearchString "Name_Of_Application"
```

```powershell
$policy = New-AzureADPolicy -Definition @("{`"HomeRealmDiscoveryPolicy`":{`"AllowCloudPasswordValidation`":true}}") -DisplayName EnableDirectAuth -Type HomeRealmDiscoveryPolicy -IsOrganizationDefault $false
```

```powershell
Add-AzureADServicePrincipalPolicy -Id $sp.ObjectId -RefObjectId $policy.Id 
```

Después de asignar la directiva, espere aproximadamente 15-20 segundos a que se propague antes de probarla.

### <a name="generate-token-fails-when-providing-effective-identity"></a>Error en la generación del token al proporcionar una identidad efectiva

GenerateToken puede generar un error, con la identidad efectiva proporcionada, por diversas razones.

* El conjunto de datos no admite la identidad efectiva
* No se proporcionó el nombre de usuario
* No se proporcionó el rol
* No se proporcionó DatasetId
* El usuario no tiene los permisos correctos

Para comprobar cuál es, pruebe lo siguiente.

* Ejecute [get dataset](https://docs.microsoft.com/rest/api/power-bi/datasets). ¿Tiene la propiedad IsEffectiveIdentityRequired el valor true?
* El nombre de usuario es obligatorio en todas las instancias de EffectiveIdentity.
* Si el valor de IsEffectiveIdentityRolesRequired es true, se requiere el rol.
* DatasetId es obligatorio en todas las instancias de EffectiveIdentity.
* En Analysis Services, el maestro tiene que ser un administrador de puerta de enlace.

### <a name="aadsts90094-the-grant-requires-admin-permission"></a>AADSTS90094: La concesión requiere permiso de administrador

**_Síntomas:_**<br>
Cuando un usuario sin derechos administrativos intenta iniciar sesión en una aplicación por primera vez y da su consentimiento, obtiene uno de los errores siguientes:

* La prueba de consentimiento necesita permiso para acceder a los recursos de la organización que solo un administrador puede conceder. Póngase en contacto con un administrador que conceda permisos en esta aplicación para poder usarla.
* AADSTS90094: La concesión requiere permiso de administrador.

    ![Prueba de consentimiento](media/embedded-troubleshoot/consent-test-01.png)

Un usuario administrador puede iniciar sesión y conceder el consentimiento correctamente.

**_:_**<br>
El consentimiento de usuario está deshabilitado en este inquilino.

**_Existen varias correcciones viables:_**

*Habilitar el consentimiento de usuario en todo el inquilino (todos los usuarios, todas las aplicaciones)*

1. En Azure Portal, vaya a "Azure Active Directory" = > "Usuarios y grupos" = > "Configuración de usuario".
2. Habilite la opción "Los usuarios pueden permitir que las aplicaciones accedan a los datos de la compañía en su nombre" y guarde los cambios.

    ![Corrección de la prueba de consentimiento](media/embedded-troubleshoot/consent-test-02.png)

*Conceda permisos* a la aplicación por un administrador, ya sea para todo el inquilino o para un usuario específico.

### <a name="cs1061-error"></a>Error CS1061

Descargue [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) si aparece un error "AuthenticationContext no contiene una definición para AcquireToken y no se encontró ningún elemento AcquireToken accesible que acepte un primer argumento del tipo AuthenticationContext (¿falta una directiva de uso o una referencia de ensamblado?)".

## <a name="data-sources"></a>Orígenes de datos

### <a name="isv-wants-to-have-different-credentials-for-the-same-data-source"></a>ISV desea contar con otras credenciales para el mismo origen de datos

Un origen de datos puede tener un único conjunto de credenciales para un usuario maestro. Si necesita utilizar otras credenciales, cree más maestros adicionales. A continuación, asigne las distintas credenciales en cada uno de los contextos de usuario maestros e insértelas mediante el token de Azure AD de ese usuario.

## <a name="troubleshoot-your-embedded-application-with-the-ierror-object"></a>Solución de problemas de las aplicaciones insertadas con el objeto IError

Use el [**objeto IError** que devuelve el evento *error* del **SDK de JavaScript**](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Troubleshooting-and-debugging-of-embedded-parts) para depurar la aplicación y comprender mejor la causa de sus errores.

Después de adquirir el objeto IError, debe consultar la tabla adecuada de errores comunes que se ajusta al tipo de inserción usada. Compare las **propiedades de IError** con las de la tabla y busque los posibles motivos del error.

### <a name="typical-errors-when-embedding-for-power-bi-users"></a>Errores habituales al insertar las aplicaciones para usuarios de Power BI

| Mensaje | Mensaje detallado | Código de error | Posible motivo: |
|-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-----------|--------------------------------------------------------|
| TokenExpired | Expiró el token de acceso, vuelva a realizar el envío con uno nuevo. | 403 | Token expirado  |
| PowerBIEntityNotFound | Error al obtener el informe | 404 | <li> Identificador de informe incorrecto <li> El informe no existe  |
| Parámetros no válidos | No se ha especificado el parámetro powerbiToken | N/D | <li> No se ha proporcionado ningún token de acceso <li> No se ha proporcionado ningún identificador de informe |
| LoadReportFailed | No se pudo inicializar: no se pudo resolver el clúster | 403 | * Token de acceso incorrecto * El tipo de inserción no coincide con el tipo de token |
| PowerBINotAuthorizedException | Error al obtener el informe | 401 | <li> Identificador de grupo incorrecto <li> Grupo no autorizado |
| TokenExpired | Expiró el token de acceso, vuelva a realizar el envío con uno nuevo. No se ha podido procesar un objeto visual de informe denominado: <visual title> | N/D | Token de datos de consulta expirado |
| OpenConnectionError | No se puede mostrar el objeto visual. No se ha podido procesar un objeto visual de informe denominado: <visual title> | N/D | Capacidad en pausa o eliminada mientras un informe relacionado con la capacidad estaba abierto en una sesión |
| ExplorationContainer_FailedToLoadModel_DefaultDetails | No se ha podido cargar el esquema de modelo asociado a este informe. Asegúrese de que tiene una conexión al servidor e inténtelo de nuevo. | N/D | <li> Capacidad en pausa <li> Capacidad eliminada |

### <a name="typical-errors-when-embedding-for-non-power-bi-users-using-an-embed-token"></a>Errores habituales al insertar para usuarios que no usan Power BI (mediante un token de inserción)

| Mensaje | Mensaje detallado | Código de error | Motivos |
|-------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|------------|-------------------------------------------------|
| TokenExpired | Expiró el token de acceso, vuelva a realizar el envío con uno nuevo. | 403 | Token expirado  |
| LoadReportFailed | Error al obtener el informe | 404 | <li> Identificador de informe incorrecto <li> El informe no existe  |
| LoadReportFailed | Error al obtener el informe | 403 | El identificador de informe no coincide con el token |
| LoadReportFailed | Error al obtener el informe | 500 | El identificador de informe proporcionado no es un GUID |
| Parámetros no válidos | No se ha especificado el parámetro powerbiToken | N/D | <li> No se ha proporcionado ningún token de acceso <li> No se ha proporcionado ningún identificador de informe |
| LoadReportFailed | No se pudo inicializar: no se pudo resolver el clúster | 403 | Tipo de token incorrecto, Token incorrecto |
| PowerBINotAuthorizedException | Error al obtener el informe | 401 | Identificador de grupo incorrecto o no autorizado |
| TokenExpired | Expiró el token de acceso, vuelva a realizar el envío con uno nuevo. No se ha podido procesar un objeto visual de informe denominado: <visual title> | N/D | Token de datos de consulta expirado |
| OpenConnectionError | No se puede mostrar el objeto visual. No se ha podido procesar un objeto visual de informe denominado: <visual title> | N/D | Capacidad en pausa o eliminada mientras un informe relacionado con la capacidad estaba abierto en una sesión |
| ExplorationContainer_FailedToLoadModel_DefaultDetails | No se ha podido cargar el esquema de modelo asociado a este informe. Asegúrese de que tiene una conexión al servidor e inténtelo de nuevo. | N/D | <li> Capacidad en pausa <li> Capacidad eliminada |

## <a name="content-rendering"></a>Representación de contenido

### <a name="performance"></a>Rendimiento

[Procedimientos recomendados de rendimiento de Power BI Embedded](embedded-performance-best-practices.md)

### <a name="rendering-or-consumption-of-embedded-content-fails-or-times-out"></a>La representación o el consumo de contenido insertado generan un error o agotan el tiempo de espera

Asegúrese de que el token de insertar no ha expirado. Asegúrese de que comprueba la caducidad del token de inserción y que lo actualiza. Para más información, consulte [Refresh token using JavaScript SDK](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Refresh-token-using-JavaScript-SDK-example) (Actualización de un token mediante el SDK de JavaScript).

### <a name="report-or-dashboard-doesnt-load"></a>El informe o el panel no se cargan

Si el usuario no puede ver el informe o el panel, asegúrese de que ambos se cargan correctamente en powerbi.com. El informe o el panel no funcionan en la aplicación si no se cargan en powerbi.com.

### <a name="report-or-dashboard-is-performing-slowly"></a>El informe o el panel se ejecutan con lentitud

Abra el archivo desde Power BI Desktop, o en powerbi.com, y compruebe que el rendimiento es aceptable para descartar problemas relacionados con la aplicación o con las API de inserción.

## <a name="embed-setup-tool"></a>Herramienta de configuración de inserción

Puede ver la [herramienta de configuración de inserción](https://aka.ms/embedsetup) para descargar rápidamente una aplicación de ejemplo. Después, puede comparar su aplicación con la aplicación de ejemplo.

### <a name="prerequisites"></a>Requisitos previos

Compruebe que cumple todos los requisitos previos antes de usar la herramienta de configuración de inserción. Necesita una cuenta de **Power BI Pro** y una suscripción de **Microsoft Azure**.

* Si no está registrado en **Power BI Pro**, [regístrese para obtener una evaluación gratuita](https://powerbi.microsoft.com/pricing/) antes de empezar.
* Si no tiene una suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de empezar.
* Debe tener su propio [inquilino de Azure Active Directory ](create-an-azure-active-directory-tenant.md) configurado.
* También debe tener [Visual Studio](https://www.visualstudio.com/) instalado (versión 2013 o posterior).

### <a name="common-issues"></a>Problemas comunes

Estos son algunos de los problemas comunes que pueden surgir al hacer pruebas con la herramienta de configuración de inserción:

#### <a name="using-the-embed-for-your-customers-sample-application"></a>Usar la aplicación de ejemplo de inserción para clientes

Si está trabajando con la experiencia de **inserción para los clientes**, guarde el archivo *PowerBI-Developer-Samples.zip* y descomprímalo. Después, abra la carpeta *PowerBI-Developer-Samples-master\App Owns Data* y ejecute el archivo *PowerBIEmbedded_AppOwnsData.sln*.

Al seleccionar **Conceder permisos** (el paso Conceder permisos), obtendrá este error:

    AADSTS70001: Application with identifier <client ID> wasn't found in the directory <directory ID>

Para solucionarlo, cierre la ventana emergente, espere unos segundos e inténtelo de nuevo. Es posible que tenga que repetir esta acción varias veces. Un intervalo de tiempo provoca el problema de completar el proceso de registro de la aplicación cuando esta esté disponible para las API externas.

Aparece este mensaje de error cuando se ejecuta la aplicación de ejemplo:

    Password is empty. Please fill password of Power BI username in web.config.

Este error se produce porque el único valor que no se está insertado en la aplicación de ejemplo es la contraseña de usuario. Abra el archivo Web.config de la solución y rellene el campo pbiPassword con la contraseña del usuario.

Si recibe el error AADSTS50079: El usuario debe usar autenticación multifactor.

    Need to use an AAD account that doesn't have MFA enabled.

#### <a name="using-the-embed-for-your-organization-sample-application"></a>Usar la aplicación de ejemplo de inserción para la organización

Si está trabajando con la experiencia de **inserción para la organización**, guarde el archivo *PowerBI-Developer-Samples.zip* y descomprímalo. Después, abra la carpeta *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* y ejecute el archivo *pbi-saas-embed-report.sln*.

Al ejecutar la aplicación de ejemplo de **inserción para la organización**, obtendrá este error:

    AADSTS50011: The reply URL specified in the request doesn't match the reply URLs configured for the application: <client ID>

Este error se debe a que la dirección URL de redireccionamiento especificada para la aplicación del servidor web es diferente de la dirección URL de la aplicación de ejemplo. Si quiere registrar la aplicación de ejemplo, use `https://localhost:13526/` como dirección URL de redireccionamiento.

Si quiere editar la aplicación registrada, deberá aprender a [actualizarla en Azure AD](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app), para que la aplicación pueda proporcionar acceso a las API web.

Si quiere editar los datos o el perfil de usuario de Power BI, deberá aprender a editar los [datos de Power BI](https://docs.microsoft.com/power-bi/service-basic-concepts).

Si recibe el error AADSTS50079: El usuario debe usar autenticación multifactor.

    Need to use an AAD account that doesn't have MFA enabled.

Para más información, consulte [Preguntas más frecuentes acerca de Power BI Embedded](embedded-faq.md).

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

Si necesita más ayuda, [póngase en contacto con el soporte técnico](https://powerbi.microsoft.com/support/pro/?Type=documentation&q=power+bi+embedded) o [cree una incidencia de soporte técnico mediante Azure Portal](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) y proporcione los mensajes de error que haya encontrado.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, vea [Preguntas frecuentes](embedded-faq.md).

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
