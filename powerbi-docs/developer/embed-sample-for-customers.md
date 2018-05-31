---
title: Insertar contenido de Power BI en una aplicación para los clientes
description: Aprenda a integrar, o insertar, un informe, un panel o un icono, en una aplicación web mediante las API de Power BI para los clientes.
author: markingmyname
ms.author: maghan
ms.date: 05/07/2018
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: dd46617f5a3b1445c597656148e4068ef3cfed92
ms.sourcegitcommit: aa8045e42b979206c600bce4a8d17de1f0620462
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34445242"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Tutorial: Inserción de un informe, un panel o un icono de Power BI en una aplicación para los clientes
Con **Power BI Embedded en Azure**, puede insertar informes, paneles o iconos en una aplicación con una **aplicación que posee los datos**. Una **aplicación que posee los datos** consiste en tener una aplicación que use Power BI como plataforma de análisis integrados. Este suele ser el caso de los **desarrolladores proveedores de software independientes (ISV)**. Como **desarrollador ISV**, puede crear contenido de Power BI que muestre informes, paneles o iconos en una aplicación completamente integrada e interactiva, sin necesidad de que los usuarios de la aplicación dispongan de una licencia de Power BI ni que sean conscientes del uso de esta plataforma. En este tutorial se explica cómo integrar un informe en una aplicación con el SDK de .NET para **Power BI** junto con la API de JavaScript para **Power BI** al usar **Power BI Embedded en Azure** para los clientes que usan una **aplicación que posee los datos**.

En este tutorial, obtendrá información sobre cómo:
>[!div class="checklist"]
>* Registrar una aplicación en Azure.
>* Insertar un informe de Power BI en una aplicación.

## <a name="prerequisites"></a>Requisitos previos
Para empezar, necesita una cuenta de **Power BI Pro**, que será la **cuenta maestra**, y una suscripción a **Microsoft Azure**.

* Si no está registrado en **Power BI Pro**, [regístrese para obtener una evaluación gratuita](https://powerbi.microsoft.com/en-us/pricing/) antes de empezar.
* Si no tiene una suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de empezar.
* Debe tener su propio [inquilino de Azure Active Directory ](create-an-azure-active-directory-tenant.md) configurado.
* También debe tener [Visual Studio](https://www.visualstudio.com/) instalado (versión 2013 o posterior).

## <a name="setup-your-embedded-analytics-development-environment"></a>Configuración del entorno de desarrollo de análisis integrados

Antes de empezar a insertar informes, paneles o iconos en la aplicación, debe asegurarse de que su entorno está configurado para permitir la inserción. Como parte de la configuración, debe hacer lo siguiente.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registro de una aplicación en Azure Active Directory (Azure AD)

La aplicación se registra en Azure Active Directory para permitir que esta acceda a las API de REST de Power BI. Esto le permite establecer una identidad para la aplicación y especificar los permisos para los recursos de REST de Power BI.

1. Acepte los [Términos de la API de Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Inicie sesión en [Azure Portal](https://portal.azure.com).
 
    ![Página principal de Azure Portal](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. En el panel de navegación izquierdo, elija **Todos los servicios**, seleccione **Registros de aplicaciones** y luego seleccione **Nuevo registro de aplicaciones**.
   
    ![Búsqueda de registro de aplicaciones](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Nuevo registro de aplicaciones](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Siga las indicaciones y cree una nueva aplicación. Para las aplicaciones que poseen datos debe usar el tipo de aplicación **Nativa**. También debe proporcionar un **URI de redirección** que usará **Azure AD** para devolver las respuestas de token. Escriba un valor que sea específico para la aplicación como, por ejemplo, http://localhost:13526/redirect).

    ![Crear aplicación](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Aplicación de permisos a la aplicación en Azure Active Directory

Tendrá que habilitar permisos adicionales para la aplicación, además de los proporcionados en la página de registro de la aplicación. Debe registrarse en la cuenta *maestra*, que se usó para la inserción, que debe ser una cuenta de administrador global.

### <a name="use-the-azure-active-directory-portal"></a>Uso del portal de Azure Active Directory

1. Vaya a [Registros de aplicaciones](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) en Azure Portal y seleccione la aplicación que va a usar para insertar.
   
    ![Elegir aplicación](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

2. Seleccione **Configuración** y, luego, en **Acceso de API**, seleccione **Permisos necesarios**.
   
    ![Permisos necesarios](media/embed-sample-for-customers/embed-sample-for-customers-008.png)

3. Seleccione **Microsoft Azure Active Directory** y asegúrese de que la opción **Acceder al directorio como usuario con sesión iniciada** esté activada. Seleccione **Guardar**.
   
    ![Permisos de Microsoft Azure AD](media/embed-sample-for-customers/embed-sample-for-customers-011.png)

4. Seleccione **Agregar**.

    ![Agregar permisos](media/embed-sample-for-customers/embed-sample-for-customers-012.png)

5. Haga clic en **Seleccionar una API**.

    ![Agregar acceso de API](media/embed-sample-for-customers/embed-sample-for-customers-013.png)

6. Seleccione **Servicio Power BI** y después haga clic en **Seleccionar**.

    ![Seleccionar Servicio PBI](media/embed-sample-for-customers/embed-sample-for-customers-014.png)

7. Seleccione todos los permisos en **Permisos delegados**. Debe seleccionarlos uno por uno para guardar las selecciones realizadas. Seleccione **Guardar** cuando haya finalizado.
   
    ![Seleccionar permisos delegados](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. En **Permisos necesarios**, seleccione **Conceder permisos**.
   
    La acción **Conceder permisos** es necesaria para evitar que Azure AD le solicite consentimiento a la *cuenta maestra*. Si la cuenta que realiza esta acción es de un administrador global, concederá permisos a todos los usuarios dentro de su organización para esta aplicación. Si la cuenta que realiza esta acción es la *cuenta maestra* y no es un administrador global, concederá permisos solo para la *cuenta maestra* de esta aplicación.
   
    ![Conceder permisos en el cuadro de diálogo de permisos necesarios](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

## <a name="setup-your-power-bi-environment"></a>Configuración del entorno de Power BI

### <a name="create-an-app-workspace"></a>Crear un área de trabajo de la aplicación

Si va a insertar informes, paneles o iconos para los clientes, tiene que colocar el contenido en un área de trabajo de la aplicación. La cuenta *maestra* debe corresponder a un administrador del área de trabajo de la aplicación.

1. Comience por crear el área de trabajo. Seleccione **Áreas de trabajo** > **Crear área de trabajo de la aplicación**. Aquí es donde se debe colocar el contenido al que la aplicación necesita acceder.

    ![Crear área de trabajo](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Asigne un nombre al área de trabajo. Si el **Id. de área de trabajo** correspondiente no está disponible, puede editarlo para tener un identificador único. Este será también el nombre de la aplicación.

    ![Asignar nombre al área de trabajo](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Tiene que establecer algunas opciones. Si elige **Pública**, cualquier persona de la organización puede ver el contenido del área de trabajo. **Privada**, por otro lado, significa que solo los miembros del área de trabajo pueden ver su contenido.

    ![Privada y pública](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    No puede cambiar la configuración pública o privada una vez creado el grupo.

4. También puede elegir si los miembros pueden **editar** o tener acceso de **solo lectura**.

    ![Adición de miembros](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Agregue las direcciones de correo electrónico de las personas que desea que tengan acceso al área de trabajo y seleccione **Agregar**. No se pueden agregar alias de grupo, solo individuales.

6. Decida si cada persona es un miembro o un administrador. Los administradores pueden editar el área de trabajo y agregar otros miembros. Los miembros pueden editar el contenido del área de trabajo, a menos que tengan acceso de solo lectura. Los administradores y los miembros pueden publicar la aplicación.

Ahora puede ver el área de trabajo nueva. Power BI crea el área de trabajo y la abre. Aparece en la lista de áreas de trabajo de las que es miembro. Dado que es un administrador, puede seleccionar los puntos suspensivos (...) para volver atrás y realizar cambios, agregar nuevos miembros o cambiar sus permisos.

   ![Nueva área de trabajo](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Creación y publicación de informes

Puede crear sus propios informes y conjuntos de datos mediante Power BI Desktop y publicar esos informes en un área de trabajo de la aplicación. El usuario final que publique los informes deberá tener una licencia de Power BI Pro para publicar en un área de trabajo de la aplicación.

1. Descargue la [demostración de blog](https://github.com/Microsoft/powerbi-desktop-samples) de ejemplo de GitHub.

    ![ejemplo de informe](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Abra el informe de ejemplo PBIX en **Power BI Desktop**.

   ![Informe de PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publíquelo en el **área de trabajo de la aplicación**.

   ![Informe de PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    Ahora puede ver el informe en línea en el servicio Power BI.

   ![Informe de PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content"></a>Inserción de contenido

La inserción de contenido para los clientes en la aplicación requiere disponer de un **token de acceso** para la cuenta maestra en **Azure AD**. Es necesario [obtener un token de acceso de Azure AD](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) para la aplicación de Power BI con una aplicación que posee los datos antes de realizar llamadas a la API de Power BI.

Siga estos pasos para empezar a insertar contenido con una aplicación de ejemplo.

1. Descargue el [ejemplo de la aplicación posee los datos](https://github.com/Microsoft/PowerBI-Developer-Samples) de GitHub para comenzar.

    ![Ejemplo de aplicación que posee los datos](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Abra el archivo Web.config en la aplicación de ejemplo. Hay cinco campos que debe rellenar para ejecutar la aplicación correctamente. **clientID**, **groupId**, **reportId**, **pbiUsername** y **pbiPassword**.

      ![Archivo de configuración web](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    * Rellene la información del campo **clientId** con el **identificador de la aplicación** de **Azure**. La aplicación usa el **identificador de cliente** para identificarse ante los usuarios a los que solicita permisos. Para obtener el **identificador de cliente**, siga estos pasos:

    1. Inicie sesión en [Azure Portal](https://portal.azure.com).

        ![Página principal de Azure Portal](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

    2. En el panel de navegación izquierdo, elija **Todos los servicios** y seleccione **Registros de aplicaciones**.

        ![Búsqueda de registros de aplicaciones](media/embed-sample-for-customers/embed-sample-for-customers-003.png)
    3. Seleccione la aplicación para la que desea obtener el **identificador de cliente**.

        ![Elegir aplicación](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

    4. Debe ver un **identificador de la aplicación** que aparece como un GUID. Use este **identificador de la aplicación** como el **identificador de cliente** de la aplicación.

        ![ClientID](media/embed-sample-for-customers/embed-sample-for-customers-007.png)     

    * Rellene la información del **identificador de grupo** con el **GUID del área de trabajo de la aplicación** de Power BI.

        ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    * Rellene la información del **identificador de informe** con el **GUID de informe** de Power BI.

        ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)    

    * Rellene la información del **nombre de usuario de PBI** con la cuenta de usuario maestra de Power BI.
    * Rellene la información de la **contraseña de PBI** con la contraseña de la cuenta de usuario maestra de Power BI.

3. Ejecute la aplicación.

    Primero seleccione **Ejecutar** en **Visual Studio**.

    ![Ejecutar la aplicación](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Luego seleccione **Insertar informe**. En función del contenido con el que desee realizar las pruebas, es decir, informes, paneles o iconos, seleccione la opción correspondiente en la aplicación.

    ![Seleccionar un contenido](media/embed-sample-for-customers/embed-sample-for-customers-034.png)
 
    Ahora puede ver el informe en la aplicación de ejemplo.

    ![Ver aplicación](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="move-to-production"></a>Pasar a producción

Ahora que ya ha desarrollado la aplicación, es hora de agregar capacidad dedicada al área de trabajo de la aplicación. Se necesita capacidad dedicada para pasar a producción.

### <a name="create-a-dedicated-capacity"></a>Crear una capacidad dedicada
Mediante la creación de una capacidad dedicada, puede aprovechar las ventajas de disponer de un recurso dedicada para su cliente. Si se trata de áreas de trabajo que no están asignadas a una capacidad dedicada, estas se encontrarán en una capacidad compartida. Puede crear una capacidad dedicada mediante la solución de [capacidad dedicada de Power BI Embedded](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity) en Azure.

>[!Note]
>Los tokens de inserción con licencias PRO están pensados para el desarrollo y las pruebas, de modo que el número de tokens de inserción que puede generar una cuenta maestra de Power BI es limitado. Debe adquirir capacidad dedicada para realizar inserciones en un entorno de producción. No hay ningún límite en cuanto a la cantidad de tokens de inserción que puede generar con una capacidad dedicada. Vaya a [Get Available Features](https://msdn.microsoft.com/library/mt846473.aspx) (Obtener características disponibles) para comprobar el valor de uso que indica el porcentaje de uso actual de Embedded.
>

### <a name="assign-app-workspace-to-dedicated-capacity"></a>Asignar el área de trabajo de aplicación con capacidad dedicada

Una vez creada la capacidad dedicada, asigne el área de trabajo de la aplicación a esta. Para hacerlo, siga estos pasos.

1. En el **servicio Power BI**, expanda las áreas de trabajo y seleccione el botón de puntos suspensivos para el área de trabajo en la que quiere insertar contenido. A continuación, seleccione **Editar áreas de trabajo**.

    ![Editar área de trabajo](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Expanda **Avanzadas**, habilite **Capacidad dedicada** y luego seleccione la capacidad dedicada que ha creado. Luego seleccione **Guardar**.

    ![Asignar capacidad dedicada](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

Para obtener un ejemplo completo del uso de la API de JavaScript, puede usar la [herramienta de área de juegos](https://microsoft.github.io/PowerBI-JavaScript/demo). Se trata de una forma rápida de reproducir diferentes tipos de ejemplos de Power BI Embedded. También puede obtener más información sobre la API de JavaScript si consulta la página de la [wiki de PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Si tiene más preguntas sobre Power BI Embedded, visite la página de [Preguntas más frecuentes](embedded-faq.md).  Si tiene problemas con Power BI Embedded dentro de la aplicación, visite la página de [solución de problemas](embedded-troubleshoot.md).

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)