---
title: Análisis integrado para insertar contenido de Power BI en una aplicación para los clientes
description: Aprenda a integrar, o insertar, un informe, un panel o un icono, en una aplicación web mediante las API de Power BI para realizar análisis integrados para los clientes. Aprenda a integrar Power BI en su aplicación mediante software de análisis integrado, herramientas de análisis integrado o herramientas de inteligencia empresarial integrada.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: nishalit
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: seodec18
ms.date: 02/05/2019
ms.openlocfilehash: eb1147875accff47b80dcdaf8a4051b57e627625
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762637"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-customers"></a>Tutorial: Insertar contenido de Power BI en una aplicación para los clientes

Con **Power BI Embedded en Azure**, puede insertar informes, paneles o iconos en una aplicación mediante aplicaciones que poseen datos. Una **aplicación que posee los datos** consiste en tener una aplicación que use Power BI como plataforma de análisis integrados. Como **desarrollador ISV**, puede crear contenido de Power BI que muestre informes, paneles o iconos en una aplicación que esté completamente integrada e interactiva, sin necesidad de que los usuarios dispongan de una licencia de Power BI. En este tutorial se explica cómo integrar un informe en una aplicación mediante el SDK de .NET para Power BI con la API de JavaScript para Power BI cuando se usa **Power BI Embedded en Azure** para los clientes.

En este tutorial, obtendrá información sobre cómo:
> [!div class="checklist"]
> * Registrar una aplicación en Azure.
> * Insertar un informe de Power BI en una aplicación.

## <a name="prerequisites"></a>Requisitos previos

Para empezar, es necesario que tenga:

* Una [cuenta de Power BI Pro](../service-self-service-signup-for-power-bi.md) (una cuenta maestra que es el nombre de usuario y la contraseña para iniciar sesión en la cuenta de Power BI Pro), o bien una [entidad de servicio (token de solo aplicación)](embed-service-principal.md).
* Una suscripción a [Microsoft Azure](https://azure.microsoft.com/).
* Debe tener configurado un [inquilino de Azure Active Directory](create-an-azure-active-directory-tenant.md) propio.

Si no está registrado en **Power BI Pro**, [regístrese para obtener una evaluación gratuita](https://powerbi.microsoft.com/pricing/) antes de empezar.

Si no tiene una suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de empezar.

## <a name="set-up-your-embedded-analytics-development-environment"></a>Configuración del entorno de desarrollo de análisis integrados

Antes de empezar a insertar informes, paneles o iconos en la aplicación, debe asegurarse de que su entorno permita la inserción con Power BI.

Puede seguir los pasos de la [herramienta de configuración de integración](https://aka.ms/embedsetup/AppOwnsData) para empezar a trabajar rápidamente y descargar una aplicación de ejemplo que sirve para crear un entorno e insertar un informe.

Si prefiere configurar el entorno manualmente, siga los pasos que se indican más adelante.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registro de una aplicación en Azure Active Directory (Azure AD)

[Registre la aplicación](register-app.md) con Azure Active Directory para permitir que acceda a las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/). El hecho de registrar su aplicación permite establecer una identidad para esta y especificar los permisos para los recursos de REST de Power BI. En función de si quiere usar una cuenta maestra o una [entidad de servicio](embed-service-principal.md) se determina cómo empezar a registrar una aplicación.

El método que adopte afectará al tipo de aplicación que se registra en Azure.

Si continúa con una cuenta maestra, continúe con el registro de una aplicación **nativa**. Se usa una aplicación nativa porque se trabaja con un inicio de sesión no interactivo.

Pero si continúa con la entidad de servicio, tendrá que continuar con el registro de una **aplicación web del lado servidor**. Una aplicación web del lado servidor se registra para crear un secreto de aplicación.

## <a name="set-up-your-power-bi-environment"></a>Configuración del entorno de Power BI

### <a name="create-an-app-workspace"></a>Crear área de trabajo de la aplicación

Si va a insertar informes, paneles o iconos para los clientes, tiene que colocar el contenido en un área de trabajo de la aplicación. Existen distintos tipos de áreas de trabajo que se pueden configurar: las [áreas de trabajo tradicionales](../service-create-workspaces.md) o las [áreas de trabajo nuevas](../service-create-the-new-workspaces.md). Si usa una cuenta *maestra*, entonces no importa qué tipo de áreas de trabajo utilice. Pero si usa una *[entidad de servicio](embed-service-principal.md)* para iniciar sesión en la aplicación, tendrá que usar las áreas de trabajo nuevas. En cualquier caso, tanto la cuenta *maestra* como la *entidad de servicio* debe ser un administrador de las áreas de trabajo de aplicación relacionadas con la aplicación.

### <a name="create-and-publish-your-reports"></a>Creación y publicación de informes

Puede crear sus propios informes y conjuntos de datos mediante Power BI Desktop y publicar esos informes en un área de trabajo de la aplicación. Existen dos formas de realizar esta tarea: Como usuario final, puede publicar informes en un área de trabajo de la aplicación tradicional con una cuenta maestra (licencia de Power BI Pro). Si usa la entidad de servicio, puede publicar informes en las áreas de trabajo nuevas mediante las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/imports/postimportingroup).

En los pasos siguientes se explica cómo publicar el informe PBIX en el área de trabajo de Power BI.

1. Descargue la [demostración de blog](https://github.com/Microsoft/powerbi-desktop-samples) de ejemplo de GitHub.

    ![ejemplo de informe](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Abra el informe PBIX de ejemplo en **Power BI Desktop**.

   ![Informe de PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publíquelo en **áreas de trabajo de la aplicación**. Este proceso es diferente en función de si usa una cuenta maestra (licencia de Power Pro) o una entidad de servicio. Si usa una cuenta maestra, puede publicar el informe a través de Power BI Desktop.  Pero si usa la entidad de servicio, tendrá que usar las API REST de Power BI.

## <a name="embed-content-using-the-sample-application"></a>Inserción de contenido mediante la aplicación de ejemplo

Este ejemplo se mantiene deliberadamente sencillo para fines de demostración. La protección del secreto de aplicación o de las credenciales de la cuenta maestra le corresponde a usted o a los desarrolladores.

Siga estos pasos para empezar a insertar contenido mediante la aplicación de ejemplo.

1. Descargue [Visual Studio](https://www.visualstudio.com/) (versión 2013 o posterior). Asegúrese de descargar el [paquete NuGet](https://www.nuget.org/profiles/powerbi) más reciente.

2. Descargue el [ejemplo de la aplicación posee los datos](https://github.com/Microsoft/PowerBI-Developer-Samples) de GitHub para comenzar.

    ![Ejemplo de aplicación que posee los datos](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

3. Abra el archivo **Web.config** de la aplicación de ejemplo. Hay campos que debe rellenar para ejecutar la aplicación. Puede elegir **MasterUser** o **ServicePrincipal** para el valor de **AuthenticationType**. En función del tipo de método de autenticación elija, tendrá que completar campos diferentes.

    > [!Note]
    > En este ejemplo, el valor predeterminado de **AuthenticationType** es MasterUser.

    <center>

    | **MasterUser** </br> (Licencia de Power BI Pro) | **ServicePrincipal** </br> (token de solo aplicación)|
    |---------------|-------------------|
    | [applicationId](#application-id) | [applicationId](#application-id) |
    | [workspaceId](#workspace-id) | [workspaceId](#workspace-id) |
    | [reportId](#report-id) | [reportId](#report-id) |
    | [pbiUsername](#power-bi-username-and-password) |  |
    | [pbiPassword](#power-bi-username-and-password) |  |
    |  | [applicationsecret](#application-secret) |
    |  | [tenant](#tenant) |

   </center>

    ![Archivo de configuración web](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

### <a name="application-id"></a>Id. de aplicación

Este atributo es necesario para los dos valores de AuthenticationType (cuenta maestra y [entidad de servicio](embed-service-principal.md)).

Rellene la información de **applicationId** con el **identificador de aplicación** de **Azure**. La aplicación usa **applicationId** para identificarse ante los usuarios a los que solicita permisos.

Para obtener **applicationId**, siga estos pasos:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. En el panel de navegación izquierdo, elija **Todos los servicios** y seleccione **Registros de aplicaciones**.

    ![Búsqueda de registros de aplicaciones](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. Seleccione la aplicación que necesite el valor **applicationId**.

    ![Elegir aplicación](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

4. Hay un **identificador de la aplicación** que se muestra como un GUID. Use este **identificador de aplicación** como **applicationId** de la aplicación.

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

### <a name="workspace-id"></a>Id. del área de trabajo

Este atributo es necesario para los dos valores de AuthenticationType (cuenta maestra y [entidad de servicio](embed-service-principal.md)).

Rellene la información del valor **workspaceId** con el GUID del área de trabajo de la aplicación (grupo) de Power BI. Puede obtener esta información de la dirección URL cuando inicie sesión en el servicio Power BI o mediante Powershell.

URL </br>

![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

PowerShell </br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test"
```

   ![Valor de workspaceId de PowerShell](media/embed-sample-for-customers/embed-sample-for-customers-031-ps.png)

### <a name="report-id"></a>Report ID (Id. de informe)

Este atributo es necesario para los dos valores de AuthenticationType (cuenta maestra y [entidad de servicio](embed-service-principal.md)).

Rellene la información de **reportId** con el GUID de informe de Power BI. Puede obtener esta información de la dirección URL cuando inicie sesión en el servicio Power BI o mediante Powershell.

URL</br>

![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

PowerShell </br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test" | Get-PowerBIReport
```

![Valor reportId de PowerShell](media/embed-sample-for-customers/embed-sample-for-customers-032-ps.png)

### <a name="power-bi-username-and-password"></a>Nombre de usuario y contraseña de Power BI

Estos atributos solo son necesarios para el valor de cuenta maestra de AuthenticationType.

Si usa la [entidad de servicio](embed-service-principal.md) para la autenticación, no es necesario rellenar los atributos de nombre de usuario o contraseña.

* Rellene la información del elemento **pbiUsername** con la cuenta maestra de Power BI.
* Rellene la información del elemento **pbiPassword** con la contraseña de la cuenta maestra de Power BI.

### <a name="application-secret"></a>Secreto de aplicación

Este atributo solo es necesario para el valor [entidad de servicio](embed-service-principal.md) de AuthenticationType.

Rellene la información de **ApplicationSecret** a partir de la sección **Claves** de la sección **Registros de aplicaciones** de **Azure**.  Este atributo funciona cuando se usa la [entidad de servicio](embed-service-principal.md).

Para obtener **ApplicationSecret**, siga estos pasos:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. En el panel de navegación de la izquierda, haga clic en **Todos los servicios** y después en **Registros de aplicaciones**.

    ![Búsqueda de registros de aplicaciones](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)

3. Seleccione la aplicación que necesite usar **ApplicationSecret**.

    ![Elección de una aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

4. Seleccione **Configuración**.

    ![Selección de Configuración](media/embed-sample-for-your-organization/embed-sample-for-your-organization-038.png)

5. Seleccione **Claves**.

    ![Selección de Claves](media/embed-sample-for-your-organization/embed-sample-for-your-organization-039.png)

6. Escriba un nombre en el cuadro **Descripción** y seleccione una duración. Después, haga clic en **Guardar** para obtener el **valor** para la aplicación. Cuando se cierra el panel **Claves** después de guardar el valor de clave, el campo de valor solo se muestra como oculto. En ese momento, no puede recuperar el valor de clave. Si pierde el valor de clave, cree uno nuevo en Azure Portal.

    ![Valor de clave](media/embed-sample-for-your-organization/embed-sample-for-your-organization-031.png)

### <a name="tenant"></a>Inquilino

Este atributo solo es necesario para el valor [entidad de servicio](embed-service-principal.md) de AuthenticationType.

Rellene la información del elemento **tenant** con el identificador del inquilino de Azure. Puede obtener esta información del [portal de Azure AD](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id#use-the-azure-ad-portal) cuando inicie sesión en el servicio Power BI o mediante Powershell.

### <a name="run-the-application"></a>Ejecutar la aplicación

1. Seleccione **Ejecutar** en **Visual Studio**.

    ![Ejecutar la aplicación](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

2. Luego seleccione **Insertar informe**. En función del contenido con el que desee realizar las pruebas, es decir, informes, paneles o iconos, seleccione la opción correspondiente en la aplicación.

    ![Seleccionar un contenido](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

3. Ahora puede ver el informe en la aplicación de ejemplo.

    ![Ver aplicación](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-content-within-your-application"></a>Inserción de contenido en la aplicación

Aunque los pasos para insertar el contenido se realizan con las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), la inserción de los códigos de ejemplo descritos en este artículo se realiza con el **SDK de .NET**.

La inserción para los clientes de la aplicación requiere que obtenga un **token de acceso** para la cuenta maestra o una [entidad de servicio](embed-service-principal.md) de **Azure AD**. Tendrá que obtener un [token de acceso de Azure AD](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) para la aplicación de Power BI antes de llamar a las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Para crear el cliente de Power BI con el **token de acceso**, deberá crear el objeto de cliente de Power BI, que permite interactuar con las [API de REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/). Para crear un objeto de cliente de Power BI, ajuste el valor de **AccessToken** con un objeto ***Microsoft.Rest.TokenCredentials***.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Obtención del elemento de contenido que desea insertar

Puede usar el objeto de cliente de Power BI para recuperar una referencia al elemento que quiera insertar.

A continuación tiene un código de ejemplo sobre cómo recuperar el primer informe de un área de trabajo determinada.

*En el archivo Services\EmbedService.cs de la [aplicación de ejemplo](https://github.com/Microsoft/PowerBI-Developer-Samples) se incluye un ejemplo de cómo obtener un elemento de contenido, ya sea un informe, un panel o un icono, que se quiere insertar.*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Creación del token de inserción

Se genera un token de inserción que se pueda usar desde la API de JavaScript. El token de inserción es específico del elemento que va a insertar. Esto significa que, siempre que quiera insertar un fragmento de contenido de Power BI, deberá crear un nuevo token de inserción específico. Para más información, incluido el **accessLevel** que debe usar, consulte [GenerateToken API](https://msdn.microsoft.com/library/mt784614.aspx).

*En el archivo Services\EmbedService.cs de la [aplicación de ejemplo](https://github.com/Microsoft/PowerBI-Developer-Samples) se incluye un ejemplo de cómo crear un token de inserción para un informe, un panel o un icono que se quiere insertar.*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

Se crea una clase para **EmbedConfig** y **TileEmbedConfig**. Hay un ejemplo disponible en los archivos **Models\EmbedConfig.cs** y **Models\TileEmbedConfig.cs**.

### <a name="load-an-item-using-javascript"></a>Carga de un elemento por medio de JavaScript

Puede usar JavaScript para cargar un informe en un elemento div en su página web.

Para obtener un ejemplo completo del uso de la API de JavaScript, puede usar la [herramienta del sitio de prueba](https://microsoft.github.io/PowerBI-JavaScript/demo). La herramienta de área de juegos es una forma rápida de reproducir diferentes tipos de ejemplos de Power BI Embedded. También puede obtener más información sobre la API de JavaScript si consulta la página de la [wiki de PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

En este ejemplo se utiliza un modelo **EmbedConfig** y otro **TileEmbedConfig**, junto con las vistas de un informe.

*En los archivos Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml o Views\Home\Embedtile.cshtml de la [aplicación de ejemplo](#embed-your-content-within-a-sample-application) encontrará un ejemplo sobre cómo agregar una vista de un informe, panel o icono.*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>Pasar a producción

Ahora que ya ha terminado de desarrollar la aplicación, es el momento de proporcionar una capacidad dedicada al área de trabajo de la aplicación. 

> [!Important]
> Se necesita capacidad dedicada para pasar a producción.

### <a name="create-a-dedicated-capacity"></a>Crear una capacidad dedicada

Al crear una capacidad dedicada, puede aprovechar las ventajas de disponer de un recurso dedicado de su cliente. Puede comprar una capacidad dedicada en [Microsoft Azure Portal](https://portal.azure.com). Para obtener más información sobre cómo crear la capacidad de Power BI Embedded, consulte [Creación de una capacidad de Power BI Embedded en Azure Portal](azure-pbie-create-capacity.md).

Use la tabla siguiente para determinar qué capacidad de Power BI Embedded se adecúa mejor a sus necesidades.

| Nodo de capacidad | Núcleos totales<br/>*(Back-end y front-end)* | Núcleos de back-end | Núcleos de front-end | Límites de conexiones dinámicas/DirectQuery|
| --- | --- | --- | --- | --- | --- |
| A1 |1 núcleo virtual |0,5 núcleos, 3 GB de RAM |0,5 núcleos |0,5 por segundo |
| A2 |2 núcleos virtuales |1 núcleo, 5 GB de RAM |1 núcleo | 10 por segundo |
| A3 |4 núcleos virtuales |2 núcleos, 10 GB de RAM |2 núcleos | 15 por segundo |
| A4 |8 núcleos virtuales |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |
| A5 |16 núcleos virtuales |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |
| A6 |32 núcleos virtuales |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |

**_Las SKU de Azure no permiten acceder al contenido de Power BI mediante una licencia gratuita de Power BI._**

El uso de tokens de inserción con licencias PRO está pensado para pruebas de desarrollo, de modo que el número de tokens de inserción que puede generar una cuenta maestra o una entidad de servicio de Power BI es limitado. Se necesita una capacidad dedicada para realizar inserciones en un entorno de producción. No hay ningún límite en cuanto a la cantidad de tokens de inserción que puede generar con una capacidad dedicada. Vaya a [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) (Características disponibles) para comprobar el valor de uso que indica el porcentaje de uso actual de Power BI Embedded. El porcentaje de uso depende de la cuenta maestra.

Para más información, consulte las [notas del producto de planeamiento de la capacidad de análisis integrado](https://aka.ms/pbiewhitepaper).

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Asignación de un área de trabajo de aplicación a la capacidad dedicada

Una vez creada una capacidad dedicada, puede asignar el área de trabajo de la aplicación a esa capacidad dedicada.

Para asignar una capacidad dedicada a un área de trabajo mediante la [entidad de servicio](embed-service-principal.md), use la [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/capacities/groups_assigntocapacity). Cuando use las API REST de Power BI, asegúrese de usar el [identificador de objeto de entidad de servicio](embed-service-principal.md#how-to-get-the-service-principal-object-id).

Siga estos pasos para asignar una capacidad dedicada a un área de trabajo mediante una **cuenta maestra**.

1. En el **servicio Power BI**, expanda las áreas de trabajo y seleccione el botón de puntos suspensivos del área de trabajo en la que quiera insertar contenido. A continuación, seleccione **Editar áreas de trabajo**.

    ![Editar área de trabajo](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Expanda **Avanzadas**, habilite **Capacidad dedicada** y luego seleccione la capacidad dedicada que ha creado. Luego seleccione **Guardar**.

    ![Asignar capacidad dedicada](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. Después de hacer clic en **Guardar**, debería ver un **rombo** junto al nombre del área de trabajo de la aplicación.

    ![Área de trabajo de aplicación asociada a una capacidad](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>Pasos siguientes

En este tutorial ha aprendido a insertar contenido de Power BI en una aplicación para sus clientes. También puede intentar insertar contenido de Power BI para su organización.

> [!div class="nextstepaction"]
>[Insertar para la organización](embed-sample-for-your-organization.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
