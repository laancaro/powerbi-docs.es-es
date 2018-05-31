---
title: Insertar contenido de Power BI en una aplicación para los clientes
description: Aprenda a integrar, o insertar, un informe, un panel o un icono, en una aplicación web mediante las API de Power BI para los clientes.
services: powerbi
author: markingmyname
ms.author: maghan
ms.date: 05/07/2018
ms.topic: tutorial
ms.service: powerbi
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2d4fdee8d3e4cca60294acd0a9167da1f048afa5
ms.sourcegitcommit: 9fa954608e78dcdb8d8a503c3c9b01c43ca728ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051942"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Tutorial: Inserción de un informe, un panel o un icono de Power BI en una aplicación para los clientes
Con **Power BI Embedded en Azure**, puede insertar informes, paneles o iconos en una aplicación para que los clientes puedan compartir datos. Suele tratarse de un escenario para **desarrolladores de ISV** en el que se usa una estructura en que la **aplicación posee los datos**. **Aplicación posee los datos** significa insertar el contenido de Power BI para sus propios clientes. Por ejemplo, el usuario de contenido de Power BI puede ver informes, paneles o iconos sin necesidad de iniciar sesión en **Power BI**. En este tutorial se explica cómo integrar o insertar un informe en una aplicación con el SDK de .NET para **Power BI** junto con la API de JavaScript para **Power BI** al usar **Power BI Embedded en Azure** para los clientes que usan la **aplicación que posee los datos**.

En este tutorial, obtendrá información sobre cómo:
>[!div class="checklist"]
>* Registrar una aplicación en Azure.
>* Insertar un informe, un panel o un icono en una aplicación con Power BI Embedded en Azure.

## <a name="prerequisites"></a>Requisitos previos
Para empezar, necesita una cuenta de **Power BI Pro** y una cuenta de **Microsoft Azure**.

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

### <a name="create-your-power-bi-embedded-dedicated-capacity-in-azure"></a>Crear capacidad dedicada de Power BI Embedded en Azure

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

    ![Página principal de Azure Portal](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

2. En el panel de navegación izquierdo, elija **Todos los servicios** y seleccione **Power BI Embedded**.

    ![Búsqueda de PBIE](media/embed-sample-for-customers/embed-sample-for-customers-017.png)

3. Siga las indicaciones y rellene la información correcta necesaria para crear capacidad dedicada de **Power BI Embedded** y luego seleccione **Crear**. Al elegir el **Plan de tarifa**, revise la tabla siguiente para decidir qué plan se adapta mejor a sus necesidades. Luego seleccione **Crear** y espere a que el recurso se complete.

    ![Configuración de PBIE](media/embed-sample-for-customers/embed-sample-for-customers-018.png)

| Nodo de capacidad | Núcleos totales<br/>*(Back-end y front-end)* | Núcleos de back-end | Núcleos de front-end | Límites de conexiones dinámicas/DirectQuery | Representaciones de páginas máximas en horas punta |
| --- | --- | --- | --- | --- | --- |
| A1 |1 núcleo V |.5 núcleos, 3 GB de RAM |5 núcleos | 5 por segundo |1-300 |
| A2 |2 núcleos V |1 núcleo, 5 GB de RAM |1 núcleo | 10 por segundo |301-600 |
| A3 |4 núcleos V |2 núcleos, 10 GB de RAM |2 núcleos | 15 por segundo |601-1200 |
| A4 |8 núcleos V |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |1201-2400 |
| A5 |16 núcleos V |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |2401-4800 |
| A6 |32 núcleos V |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |4,801-9600 |

Ahora puede ver la nueva **capacidad dedicada de Power BI Embedded**.

   ![Capacidad dedicada de PBIE](media/embed-sample-for-customers/embed-sample-for-customers-019.png)

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

7. Expanda **Avanzadas**, habilite **Capacidad dedicada** y luego seleccione la **Capacidad dedicada de Power BI Embedded** que ha creado. Luego seleccione **Guardar**.

    ![Adición de miembros](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

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

Para obtener un ejemplo completo del uso de la API de JavaScript, puede usar la [herramienta de área de juegos](https://microsoft.github.io/PowerBI-JavaScript/demo). Se trata de una forma rápida de reproducir diferentes tipos de ejemplos de Power BI Embedded. También puede obtener más información sobre la API de JavaScript si consulta la página de la [wiki de PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Si tiene más preguntas sobre Power BI Embedded, visite la página de [Preguntas más frecuentes](embedded-faq.md).  Si tiene problemas con Power BI Embedded dentro de la aplicación, visite la página de [solución de problemas](embedded-troubleshoot.md).

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/) 