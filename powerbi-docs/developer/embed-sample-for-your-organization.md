---
title: Insertar contenido de Power BI en una aplicación para la organización
description: Obtenga información para integrar o insertar un informe, un panel o un icono en una aplicación web mediante las API de Power BI para la organización.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 544429528ed51dd2928eb82632f512ff3f7d5afd
ms.sourcegitcommit: fecea174721d0eb4e1927c1116d2604a822e4090
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39359740"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-organization"></a>Tutorial: Insertar un informe, un panel o un icono de Power BI en una aplicación para la organización
En este tutorial se explica cómo integrar un informe en una aplicación con el **SDK de .NET para Power BI** junto con la **API de JavaScript para Power BI** al insertar **Power BI** en una aplicación para la organización. Con **Power BI**, puede insertar informes, paneles o iconos en una aplicación con el ejemplo **User owns data**. **User owns data** permite a la aplicación ampliar el servicio Power BI.

![Ver aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

En este tutorial, obtendrá información sobre cómo:
>[!div class="checklist"]
>* Registrar una aplicación en Azure.
>* Insertar un informe de Power BI en una aplicación.

## <a name="prerequisites"></a>Requisitos previos
Para empezar, necesita una cuenta de **Power BI Pro** y una suscripción a **Microsoft Azure**.

* Si no está registrado en **Power BI Pro**, [regístrese para obtener una evaluación gratuita](https://powerbi.microsoft.com/en-us/pricing/) antes de empezar.
* Si no tiene una suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de empezar.
* Debe tener su propio [inquilino de Azure Active Directory ](create-an-azure-active-directory-tenant.md) configurado.
* También debe tener [Visual Studio](https://www.visualstudio.com/) instalado (versión 2013 o posterior).

## <a name="setup-your-embedded-analytics-development-environment"></a>Configuración del entorno de desarrollo de análisis integrados

Antes de empezar a insertar informes, paneles o iconos en la aplicación, debe asegurarse de que su entorno está configurado para permitir la inserción. Como parte de la configuración debe hacer lo siguiente.

Puede seguir los pasos que encontrará en la [herramienta de la experiencia de incorporación](https://aka.ms/embedsetup/UserOwnsData) para empezar a trabajar rápidamente y descargar una aplicación de ejemplo con la que podrá seguir los pasos para crear un entorno e insertar un informe.

Si prefiere configurar el entorno manualmente, siga los pasos que se indican más adelante.
### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registro de una aplicación en Azure Active Directory (Azure AD)

La aplicación se registra en Azure Active Directory para permitir que esta acceda a las API de REST de Power BI. Esto le permite establecer una identidad para la aplicación y especificar los permisos para los recursos de REST de Power BI.

1. Acepte los [Términos de la API de Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Inicie sesión en [Azure Portal](https://portal.azure.com).

    ![Página principal de Azure Portal](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

3. En el panel de navegación izquierdo, elija **Todos los servicios**, seleccione **Registros de aplicaciones** y luego seleccione **Nuevo registro de aplicaciones**.

    ![Búsqueda de registro de aplicaciones](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)</br>
    ![Nuevo registro de aplicaciones](media/embed-sample-for-your-organization/embed-sample-for-your-organization-004.png)

4. Siga las indicaciones y cree una nueva aplicación. En **User owns data**, necesita usar **Aplicación web o API** para el tipo de aplicación. También debe proporcionar una **URL de inicio de sesión** que **Azure AD** use para devolver respuestas de token. Escriba un valor que sea específico de la aplicación (por ejemplo, http://localhost:13526/).

    ![Crear aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Aplicación de permisos a la aplicación en Azure Active Directory

Hay que habilitar más permisos relativos a la aplicación, además de los proporcionados en la página de registro de la aplicación. Para habilitar los permisos, tiene que iniciar sesión con una cuenta de *administrador global*.

### <a name="use-the-azure-active-directory-portal"></a>Uso del portal de Azure Active Directory

1. Vaya a [Registros de aplicaciones](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) en Azure Portal y seleccione la aplicación que va a usar para insertar.

    ![Elegir aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

2. Seleccione **Configuración** y, luego, en **Acceso de API**, seleccione **Permisos necesarios**.

    ![Permisos necesarios](media/embed-sample-for-your-organization/embed-sample-for-your-organization-008.png)

3. Seleccione **Microsoft Azure Active Directory** y asegúrese de que la opción **Acceder al directorio como usuario con sesión iniciada** esté activada. Seleccione **Guardar**.

    ![Permisos de Microsoft Azure AD](media/embed-sample-for-your-organization/embed-sample-for-your-organization-011.png)

4. Seleccione **Agregar**.

    ![Agregar permisos](media/embed-sample-for-your-organization/embed-sample-for-your-organization-012.png)

5. Haga clic en **Seleccionar una API**.

    ![Agregar acceso de API](media/embed-sample-for-your-organization/embed-sample-for-your-organization-013.png)

6. Seleccione **Servicio Power BI** y después haga clic en **Seleccionar**.

    ![Seleccionar Servicio PBI](media/embed-sample-for-your-organization/embed-sample-for-your-organization-014.png)

7. Seleccione todos los permisos en **Permisos delegados**. Debe seleccionarlos uno por uno para guardar las selecciones. Seleccione **Guardar** cuando haya finalizado.

    ![Seleccionar permisos delegados](media/embed-sample-for-your-organization/embed-sample-for-your-organization-015.png)

## <a name="setup-your-power-bi-environment"></a>Configuración del entorno de Power BI

### <a name="create-an-app-workspace"></a>Crear área de trabajo de la aplicación

Si va a insertar informes, paneles o iconos para los clientes, tiene que colocar el contenido en un área de trabajo de la aplicación.

1. Comience por crear el área de trabajo. Seleccione **Áreas de trabajo** > **Crear área de trabajo de la aplicación**. Aquí es donde hay que poner el contenido al que la aplicación necesita acceder.

    ![Crear área de trabajo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-020.png)

2. Asigne un nombre al área de trabajo. Si el **Id. de área de trabajo** correspondiente no está disponible, puede editarlo para tener un identificador único. Este debe ser también el nombre de la aplicación.

    ![Asignar nombre al área de trabajo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-021.png)

3. Tiene que establecer algunas opciones. Si elige **Pública**, cualquier persona de la organización puede ver el contenido del área de trabajo. **Privada**, por otro lado, significa que solo los miembros del área de trabajo pueden ver su contenido.

    ![Privada y pública](media/embed-sample-for-your-organization/embed-sample-for-your-organization-022.png)

    No puede cambiar la configuración pública o privada una vez creado el grupo.

4. También puede elegir si los miembros pueden **editar** o tener acceso de **solo lectura**.

    ![Adición de miembros](media/embed-sample-for-your-organization/embed-sample-for-your-organization-023.png)

5. Agregue las direcciones de correo electrónico de las personas que desea que tengan acceso al área de trabajo y seleccione **Agregar**. No se pueden agregar alias de grupo, solo individuales.

6. Decida si cada persona es un miembro o un administrador. Los administradores pueden editar el área de trabajo y agregar otros miembros. Los miembros pueden editar el contenido del área de trabajo, a menos que tengan acceso de solo lectura. Los administradores y los miembros pueden publicar la aplicación.

    Ahora puede ver el área de trabajo nueva. Power BI crea el área de trabajo y la abre. Aparece en la lista de áreas de trabajo de las que es miembro. Dado que es un administrador, puede seleccionar los puntos suspensivos (...) para volver atrás y realizar cambios, agregar nuevos miembros o cambiar sus permisos.

    ![Crear área de trabajo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-025.png)

### <a name="create-and-publish-your-reports"></a>Creación y publicación de informes

Puede crear sus propios informes y conjuntos de datos mediante Power BI Desktop y publicar esos informes en un área de trabajo de la aplicación. El usuario final que publique los informes deberá tener una licencia de Power BI Pro para publicar en un área de trabajo de la aplicación.

1. Descargue la [demostración de blog](https://github.com/Microsoft/powerbi-desktop-samples) de ejemplo de GitHub.

    ![ejemplo de informe](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026-1.png)

2. Abra el informe de ejemplo PBIX en **Power BI Desktop**.

   ![Informe de PBI Desktop](media/embed-sample-for-your-organization/embed-sample-for-your-organization-027.png)

3. Publíquelo en el **área de trabajo de la aplicación**.

   ![Informe de PBI Desktop](media/embed-sample-for-your-organization/embed-sample-for-your-organization-028.png)

    Ahora puede ver el informe en el servicio Power BI en línea.

   ![Informe de PBI Desktop](media/embed-sample-for-your-organization/embed-sample-for-your-organization-029.png)

## <a name="embed-your-content-using-the-sample-application"></a>Inserción de contenido mediante la aplicación de ejemplo

Siga estos pasos para empezar a insertar contenido con una aplicación de ejemplo.

1. Descargue el [ejemplo User Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) de GitHub para comenzar.  Hay tres aplicaciones de ejemplo diferentes, una para [informes](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), otra para [paneles](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) y la última para [iconos](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app).  Este artículo se refiere a la aplicación de **informes**, como se explica en los pasos siguientes.

    ![Ejemplo de aplicación User Owns Data](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026.png)

2. Abra el archivo Cloud.config de la aplicación de ejemplo. Hay varios campos que debe rellenar para ejecutar la aplicación correctamente. **ClientID** y **ClientSecret**.

    ![Archivo Cloud.config](media/embed-sample-for-your-organization/embed-sample-for-your-organization-030.png)

    Rellene la información de **ClientID** con el **identificador de aplicación** de **Azure**. La aplicación usa **ClientID** para identificarse ante los usuarios a los que solicita permisos.

    Para obtener **ClientID**, siga estos pasos:

    Inicie sesión en [Azure Portal](https://portal.azure.com).

    ![Página principal de Azure Portal](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

    En el panel de navegación izquierdo, elija **Todos los servicios** y seleccione **Registros de aplicaciones**.

    ![Búsqueda de registros de aplicaciones](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)

    Seleccione la aplicación que necesita usar **ClientID**.

    ![Elegir aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

    Debe ver un **identificador de la aplicación** que aparece como un GUID. Use este **identificador de aplicación** como **ClientID** de la aplicación.

    ![ClientID](media/embed-sample-for-your-organization/embed-sample-for-your-organization-007.png)

    Rellene la información de **ClientSecret** a partir de la sección **Claves** de la sección **Registros de aplicaciones** de **Azure**.

    Para obtener **ClientSecret**, siga estos pasos:

    Inicie sesión en [Azure Portal](https://portal.azure.com).

    ![Página principal de Azure Portal](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

    En el panel de navegación izquierdo, elija **Todos los servicios** y seleccione **Registros de aplicaciones**.

    ![Búsqueda de registros de aplicaciones](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)

    Seleccione la aplicación que necesita usar **ClientSecret**.

    ![Elegir aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

    Seleccione **Configuración**.

    ![Configuración](media/embed-sample-for-your-organization/embed-sample-for-your-organization-038.png)

    Seleccione **Claves**.

    ![Claves](media/embed-sample-for-your-organization/embed-sample-for-your-organization-039.png)

    Rellene **Descripción** con un nombre y seleccione un valor para **Duración**; luego seleccione **Guardar** para obtener el **Valor** para la aplicación. Una vez que se cierra la hoja **Claves** después de guardar el **valor de clave**, el campo de valor se muestra solo como **_Oculto_** y, en ese punto, no se puede recuperar el **valor de clave**. Si pierde el **valor de clave**, tiene que crear uno nuevo en **Azure Portal**.

    ![Claves](media/embed-sample-for-your-organization/embed-sample-for-your-organization-031.png)

     Rellene la información del **identificador de grupo** con el **GUID del área de trabajo de la aplicación** de Power BI.

    ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    Rellene la información del **identificador de informe** con el **GUID de informe** de Power BI.

    ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

3. Ejecute la aplicación.

    Primero seleccione **Ejecutar** en **Visual Studio**.

    ![Ejecutar la aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-033.png)

    Luego seleccione **Obtener informe**.

    ![Seleccionar un contenido](media/embed-sample-for-your-organization/embed-sample-for-your-organization-034.png)

    Ahora puede ver el informe en la aplicación de ejemplo.

    ![Ver aplicación](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

## <a name="embed-your-content-within-your-application"></a>Inserción de contenido en la aplicación
Aunque los pasos para insertar el contenido se pueden llevar a cabo con las [API de REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), la inserción de los códigos de ejemplo descritos en este artículo se efectúa con el **SDK de .NET**.

Para integrar un informe en una aplicación web, use la **API de REST de Power BI** o el **SDK de C# de Power BI** y un **token de acceso** de autorización de Azure Active Directory (AD) para obtener un informe. Luego cargue el informe con el mismo **token de acceso**. La **API de REST de Power BI** proporciona acceso mediante programación a recursos concretos de **Power BI**. Para obtener más información, vea [Power BI REST APIs](https://docs.microsoft.com/rest/api/power-bi/) (API de REST de Power BI) y la [API de JavaScript de Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

### <a name="get-an-access-token-from-azure-ad"></a>Obtener un token de acceso de Azure AD
En la aplicación, primero tiene que obtener un **token de acceso**, desde Azure AD, para poder realizar llamadas a la API de REST de Power BI. Para más información, consulte [Authenticate users and get an Azure AD access token for your Power BI app](get-azuread-access-token.md) (Autenticación de usuarios y obtención de un token de acceso de Azure AD para su aplicación de Power BI).

### <a name="get-a-report"></a>Obtener un informe
Para obtener un informe de **Power BI**, use la operación [Obtener informes](https://docs.microsoft.com/rest/api/power-bi/reports/getreports), que obtiene una lista de **informes de Power BI**. En la lista de informes, puede obtener un identificador de informe.

### <a name="get-reports-using-an-access-token"></a>Obtención de informes mediante un token de acceso
La operación [Obtener informes](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) devuelve una lista de informes. Puede obtener un informe de la lista de informes.

Para realizar la llamada de API de REST, debe incluir un encabezado *Autorización* con el formato de *Portador {token de acceso}*.

#### <a name="get-reports-with-the-rest-api"></a>Obtención de informes con la API de REST

Este es un ejemplo de código para recuperar informes con la **API de REST**.

*En el archivo **_Default.aspx.cs_** de la [aplicación de ejemplo](#embed-your-content-using-the-sample-application) hay disponible un ejemplo para obtener un elemento de contenido que se quiera insertar (informe, panel o icono).*

```csharp
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-using-the-net-sdk"></a>Obtención los informes mediante el SDK de .NET
Puede usar el SDK de .NET para recuperar una lista de informes, en lugar de llamar directamente a la API de REST. Este es un ejemplo de código para enumerar informes.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It is used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

### <a name="load-a-report-using-javascript"></a>Cargar un informe mediante JavaScript
Puede usar JavaScript para cargar un informe en un elemento div en su página web.

Este es un ejemplo de código para recuperar un informe de un área de trabajo determinada.

*En el archivo **_Default.aspx_** de la [aplicación de ejemplo](#embed-your-content-using-the-sample-application) hay disponible un ejemplo para cargar un elemento de contenido, ya sea un informe, un panel o un icono, que se quiera insertar.*

```javascript
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```javascript
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReporte, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    }
  );
}
```

## <a name="using-a-power-bi-premium-dedicated-capacity"></a>Uso de una capacidad dedicada de Power BI Premium

Ahora que ya ha terminado de desarrollar la aplicación, es hora de agregar capacidad dedicada al área de trabajo de la aplicación.

### <a name="create-a-dedicated-capacity"></a>Crear una capacidad dedicada
Al crear una capacidad dedicada, puede aprovechar las ventajas de disponer de un recurso dedicado para el contenido del área de trabajo de la aplicación. Puede crear una capacidad dedicada mediante [Power BI Premium ](../service-premium.md).

En la tabla siguiente se enumeran las SKU de Power BI Premium disponibles en [Office 365](../service-admin-premium-purchase.md).

| Nodo de capacidad | Total de núcleos virtuales<br/>*(Back-end y front-end)* | Núcleos virtuales de back-end | Núcleos virtuales de front-end | Límites de conexiones dinámicas/DirectQuery | Representaciones de páginas máximas en horas punta |
| --- | --- | --- | --- | --- | --- |
| EM1 |1 núcleo V |5 núcleos virtuales, 10 GB de RAM |.5 núcleos virtuales |3,75 por segundo |150-300 |
| EM2 |2 núcleos V |1 núcleo virtual, 10 GB de RAM |1 núcleo V |7,5 por segundo |301-600 |
| EM3 |4 núcleos V |2 núcleos virtuales, 10 GB de RAM |2 núcleos V |15 por segundo |601-1200 |
| P1 |8 núcleos V |4 núcleos virtuales, 25 GB de RAM |4 núcleos V |30 por segundo |1201-2400 |
| P2 |16 núcleos V |8 núcleos virtuales, 50 GB de RAM |8 núcleos V |60 por segundo |2401-4800 |
| P3 |32 núcleos V |16 núcleos virtuales, 100 GB de RAM |16 núcleos V |120 por segundo |4,801-9600 |
| P4 |64 núcleos virtuales |32 núcleos virtuales, 200 GB de RAM |32 núcleos V |240 por segundo |9601-19200
| P5 |128 núcleos virtuales |64 núcleos virtuales, 400 GB de RAM |64 núcleos virtuales |480 por segundo |19201-38400

*Con **_SKU EM_**, **puede** acceder al contenido con una licencia gratuita de Power BI cuando intente realizar la inserción con **_aplicaciones de MS Office_**, pero **no puede acceder** al contenido con una licencia gratuita de Power BI al usar **_Powerbi.com_** o **_Power BI Mobile_**.*

*Con **_SKU P_**, **puede** acceder al contenido con una licencia gratuita de Power BI cuando intente realizar la inserción con **_aplicaciones de MS Office_**, mediante el uso de **_Powerbi.com_** o **_Power BI Mobile_**.*

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Asignación de un área de trabajo de aplicación a la capacidad dedicada

Una vez creada una capacidad dedicada, puede asignar el área de trabajo de la aplicación a esa capacidad dedicada. Para hacerlo, siga estos pasos.

1. En el **servicio Power BI**, expanda las áreas de trabajo y seleccione el botón de puntos suspensivos del área de trabajo en la que quiera insertar contenido. A continuación, seleccione **Editar áreas de trabajo**.

    ![Editar área de trabajo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-036.png)

2. Expanda **Avanzadas**, habilite **Capacidad dedicada** y luego seleccione la capacidad dedicada que ha creado. Luego seleccione **Guardar**.

    ![Asignar capacidad dedicada](media/embed-sample-for-your-organization/embed-sample-for-your-organization-024.png)

3. Después de seleccionar **Guardar**, se debe ver un **diamante** junto al nombre del área de trabajo de la aplicación.

    ![Área de trabajo de aplicación asociada a una capacidad](media/embed-sample-for-your-organization/embed-sample-for-your-organization-037.png)

## <a name="admin-settings"></a>Configuración de administración

Los administradores globales, o los administradores de servicios de Power BI, pueden activar o desactivar la capacidad para usar las API de REST de un inquilino. Los administradores de Power BI pueden establecer esta opción de configuración para toda la organización o para grupos de seguridad individuales. De forma predeterminada, está habilitada para toda la organización. Puede hacerlo mediante el [portal de administración de Power BI](../service-admin-portal.md).

## <a name="next-steps"></a>Pasos siguientes
En este tutorial ha aprendido a insertar contenido de Power BI en una aplicación mediante la **cuenta de organización de Power BI**. Ahora puede intentar insertar contenido de Power BI en una aplicación mediante aplicaciones.  También puede intentar insertar contenido de Power BI para los clientes.

> [!div class="nextstepaction"]
> [Insertar desde aplicaciones](embed-from-apps.md)

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
