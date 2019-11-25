---
title: Obtener un token de acceso de autenticación
description: 'Tutorial para insertar datos: obtención de un token de acceso de autenticación'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/29/2019
ms.openlocfilehash: 5a96085791e8bd211ebe26b2d149c7b2ad92fc2f
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74264818"
---
# <a name="step-2-get-an-authentication-access-token"></a>Paso 2: Obtener un token de acceso de autenticación

Este artículo es el segundo paso de la serie [Inserción de datos en un conjunto de datos de Power BI](walkthrough-push-data.md).

En el paso 1, [registró una aplicación cliente en Azure AD](walkthrough-push-data-register-app-with-azure-ad.md). En este paso, obtendrá un token de acceso de autenticación. Las aplicaciones de Power BI se integran con Azure Active Directory para proporcionar a la aplicación un inicio de sesión seguro y autorización. La aplicación usa un token para autenticarse en Azure AD y acceder a los recursos de Power BI.

## <a name="get-an-authentication-access-token"></a>Obtener un token de acceso de autenticación

Antes de comenzar, asegúrese de que ha completado el [paso anterior](walkthrough-push-data-register-app-with-azure-ad.md) de la serie [Inserción de datos en un conjunto de datos de Power BI](walkthrough-push-data.md). 

Este procedimiento requiere Visual Studio 2015 o posterior.

1. En Visual Studio 2015, cree un nuevo proyecto de **aplicación de consola** de C#.

2. Instale la [Biblioteca de autenticación de Azure AD para el paquete NuGet de .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). La aplicación de .NET necesita este paquete para obtener un token de seguridad de autenticación. 

     a. Seleccione **Herramientas** > **Administrador de paquetes NuGet** > **Consola del Administrador de paquetes**.

     b. Escriba **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**.

     c. En Program.cs, agregue `using Microsoft.IdentityModel.Clients.ActiveDirectory;`.

3. Agregue el código de ejemplo que aparece después de estos pasos a Program.cs.

4. Reemplace "{ClientID}" por el **Identificador de cliente** que obtuvo en el [anterior artículo de la serie](walkthrough-push-data-register-app-with-azure-ad.md) cuando registró la aplicación.

5. Ejecute la aplicación de consola e inicie sesión en su cuenta de Power BI. 

   Debería aparecer una cadena de token en la ventana de consola.

**Ejemplo de código para obtener un token de seguridad de autenticación**

Agregue este código a Program {...}.

* Una variable de token para llamar a las operaciones: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* En static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Agregue un método GetToken():

```csharp
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Después de obtener un token de autenticación, puede llamar a cualquier operación de Power BI.

El siguiente artículo de esta serie muestra cómo [crear un conjunto de datos en Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Lista de código completa

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Pasos siguientes

[Siguiente artículo de esta serie > Creación de un conjunto de datos en Power BI](walkthrough-push-data-create-dataset.md)

[Información general sobre la API de REST de Power BI](overview-of-power-bi-rest-api.md)  
[API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)