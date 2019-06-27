---
title: Autenticación de usuarios y obtención de un token de acceso de Azure AD para la aplicación
description: Obtenga información sobre cómo registrar una aplicación en Azure Active Directory para su uso con la inserción de contenido de Power BI.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/04/2019
ms.openlocfilehash: f0e8a9931248860e11f783d04fead6172559afc1
ms.sourcegitcommit: 88e2a80b95b3e735689e75da7c35d84e24772e13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66814270"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Obtención de un token de acceso de Azure AD para la aplicación de Power BI

Este artículo muestra cómo puede autenticar a los usuarios en la aplicación de Power BI y recuperar un token de acceso para usarlo con la [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Antes de que la aplicación llame a la API REST, es preciso obtener un **token de acceso de autenticación** de Azure Active Directory (Azure AD). La aplicación usa un token para acceder a los paneles, iconos e informes de Power BI. Para más información, consulte [Autorización del acceso a aplicaciones web de Azure Active Directory mediante el flujo de concesión de código OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

En función de cómo vaya a insertar el contenido, el token de acceso se recupera de forma diferente. En este artículo se muestran dos enfoques diferentes.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Token de acceso para usuarios de Power BI (el usuario es propietario de los datos)

Este ejemplo tiene validez cuando los usuarios inician sesión de forma manual en Azure AD con su inicio de sesión de la organización. Esta tarea se utiliza para insertar contenido para los usuarios que tienen acceso al servicio Power BI.

### <a name="get-an-azure-ad-authorization-code"></a>Obtención de un código de autorización de Azure AD

El primer paso para obtener un **token de acceso** consiste en obtener un código de autorización de **Azure AD**. Cree una cadena de consulta con las propiedades siguientes y vuelva a **Azure AD**.

#### <a name="authorization-code-query-string"></a>Cadena de consulta del código de autorización

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

Después de crear una cadena de consulta, vuelva a **Azure AD** para obtener un **código de autorización**.  A continuación se muestra un método de C# completo para crear una cadena de consulta de **código de autorización** y volver a **Azure AD**. A continuación, use el **código de autorización** para obtener un **token de acceso**.

En redirect.aspx.cs, se llama a [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) para generar el token.

#### <a name="get-authorization-code"></a>Obtener código de autorización

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "http://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Obtener un token de acceso del código de autorización

Una vez que **Azure AD** le devuelve a la aplicación web con un **código de autorización**, puede utilizarlo para obtener un token de acceso. A continuación se muestra un ejemplo de C# que se puede usar en la página de redireccionamiento y en el evento `Page_Load` de la página default.aspx.

Puede recuperar el espacio de nombres **Microsoft.IdentityModel.Clients.ActiveDirectory** del paquete NuGet [Biblioteca de autenticación de Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Token de acceso para usuarios que no sean de Power BI (la aplicación es propietaria de los datos)

Este enfoque se usa normalmente para aplicaciones del tipo proveedor de software independiente (ISV) en las que la aplicación es propietaria del acceso a los datos. Los usuarios no son necesariamente usuarios de Power BI y la aplicación controla la autenticación y el acceso de los usuarios.

### <a name="access-token-with-a-master-account"></a>Token de acceso con una cuenta maestra

Para este enfoque, se usa una sola cuenta *maestra* que es un usuario de Power BI Pro. Las credenciales de la cuenta se almacenan con la aplicación. La aplicación se autentica en Azure AD con las credenciales almacenadas. El código de ejemplo que se muestra a continuación proviene del [ejemplo de App owns data](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Token de acceso con la entidad de servicio

Para este enfoque, se usa una [entidad de servicio](embed-service-principal.md), es decir un token **de solo aplicación**. La aplicación se autentica en Azure AD con la entidad de servicio. El código de ejemplo que se muestra a continuación proviene del [ejemplo de App owns data](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Solucionar problemas

Mensaje de error: "AuthenticationContext no contiene una definición para AcquireToken y no se encontró ningún elemento AcquireToken accesible que acepte un primer argumento del tipo AuthenticationContext (¿falta una directiva de uso o una referencia de ensamblado?)".

   Pruebe a descargar [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) si aparece este error.

## <a name="next-steps"></a>Pasos siguientes

Ahora que tiene el token de acceso, puede llamar a la API de REST de Power BI para insertar contenido. Para obtener información, consulte [Cómo insertar el contenido de Power BI](embed-sample-for-customers.md#embed-content-within-your-application).

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
