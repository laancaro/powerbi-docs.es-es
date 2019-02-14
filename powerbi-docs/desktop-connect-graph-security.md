---
title: Conexión a Microsoft Graph Security en Power BI Desktop
description: Conexión fácil a la API Microsoft Graph Security en Power BI Desktop
author: cpopell
manager: kfile
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 1594935d9dc156b03daff9e4447752bce2c0f06c
ms.sourcegitcommit: 88ac51106ec7d0ead8c2a1550a11afae0d502bb9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56086687"
---
# <a name="connect-to-microsoft-graph-security-in-power-bi-desktop"></a>Conexión a Microsoft Graph Security en Power BI Desktop

Puede usar Power BI Desktop para conectarse a la API Microsoft Graph Security mediante el conector Microsoft Graph Security de Power BI. Esto le permitirá crear paneles e informes para obtener conclusiones sobre sus [alertas](https://docs.microsoft.com/graph/api/resources/alert?view=graph-rest-1.0) relacionadas con la seguridad y su [Puntuación de seguridad](https://docs.microsoft.com/graph/api/resources/securescores?view=graph-rest-beta). La [API Microsoft Graph Security](https://aka.ms/graphsecuritydocs) se conecta a [varias soluciones de seguridad](https://aka.ms/graphsecurityalerts) de Microsoft y asociados del ecosistema para facilitar una correlación más sencilla de alertas, proporcionar acceso a información contextual enriquecida y simplificar la automatización. Esto permite a las organizaciones obtener conclusiones rápidamente y tomar medidas en sus productos de seguridad, a la vez que se reducen los costos y la complejidad de crear y mantener varias integraciones.

## <a name="prerequisites-to-connect-with-the-microsoft-graph-security-connector"></a>Requisitos previos para usar el conector de Microsoft Graph Security

* Para usar el conector Microsoft Graph Security, necesita tener el consentimiento *explícito* del administrador del inquilino de Azure Active Directory (AD), que forma parte de los [Requisitos de autenticación de Microsoft Graph Security](https://aka.ms/graphsecurityauth). Para recibir este consentimiento, necesita el nombre y el identificador de la aplicación del conector Microsoft Graph Security de Power BI, que encontrará en [Azure Portal](https://portal.azure.com):

   | Propiedad | Valor |
   |----------|-------|
   | **Nombre de la aplicación** | `MicrosoftGraphSecurityPowerBIConnector` |
   | **Identificador de la aplicación** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
   |||

   Para conceder el consentimiento para el conector, pida al administrador del inquilino de Azure AD que siga uno de estos procedimientos:

   * [Conceda el consentimiento del administrador del inquilino para aplicaciones de Azure AD](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent).

   * Durante la primera vista de la aplicación lógica, esta puede solicitar contenido al administrador del inquilino de Azure AD mediante la [experiencia de consentimiento de la aplicación](https://docs.microsoft.com/azure/active-directory/develop/application-consent-experience).
   
* La cuenta de usuario de inicio de sesión usada para el conector Microsoft Graph Security de Power BI tiene que ser miembro del rol de administrador limitado Lector de seguridad en Azure AD (Lector de seguridad o Administrador de seguridad). Siga los pasos que se indican en la sección [Asignar roles de Azure AD a usuarios](https://docs.microsoft.com/graph/security-authorization#assign-azure-ad-roles-to-users). 

## <a name="using-the-microsoft-graph-security-connector"></a>Uso del conector Microsoft Graph Security

Siga este procedimiento para usar el conector **Microsoft Graph Security**:

1. Seleccione **Obtener datos -> Más…** en la cinta de opciones **Inicio** en Power BI Desktop.
2. Seleccione **Servicios en línea** en la categoría de la izquierda.
3. Haga clic en **Microsoft Graph Security (Beta)**.

    ![Obtener datos](media/desktop-connect-graph-security/GetData.PNG)
    
4. En la ventana **Microsoft Graph Security**, seleccione la versión de la API Microsoft Graph que quiera usar para realizar consultas. Las opciones son v1.0 y Beta.

    ![Selección de la versión](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Cuando se le pida, inicie sesión con su cuenta de Azure Active Directory. La cuenta necesita tener el rol **Lector de seguridad**, como se indica en la sección de requisitos previos anterior.

    ![Iniciar sesión](media/desktop-connect-graph-security/SignIn.PNG)
    
6. Si es el administrador del inquilino **y** aún no ha concedido el consentimiento al conector (aplicación) Microsoft Graph Security de Power BI según los requisitos previos, se mostrará el siguiente cuadro de diálogo. Asegúrese de seleccionar "**Consentimiento en nombre de la organización**".

    ![Consentimiento del administrador](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. Después de iniciar sesión, verá la ventana siguiente, lo que indica que se ha autenticado. Seleccione **Conectar**.

    ![Sesión iniciada](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. Después de establecer correctamente la conexión, se mostrará la ventana **Navegador** con las entidades (alertas, etc.) disponibles en la [API Microsoft Graph Security](https://aka.ms/graphsecuritydocs) de la versión que haya seleccionado en los pasos anteriores. Seleccione una o varias entidades que quiera importar y usar en **Power BI Desktop**. Haga clic en **Cargar** para obtener la vista de resultados descrita en el paso 10.

   ![Tabla de navegación](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Para realizar una consulta avanzada en la API Microsoft Graph Security, seleccione la función **Especificar URL de Microsoft Graph Security personalizada para filtrar resultados**. Esto le permitirá realizar una consulta de [OData.Feed](https://docs.microsoft.com/power-bi/desktop-connect-odata) a la API Microsoft Graph Security con los permisos necesarios para acceder a ella.

   > [!NOTE]
   > El ejemplo serviceUri usado a continuación es `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'`. Vea los [parámetros de consulta de ODATA admitidos por Graph](https://docs.microsoft.com/graph/query-parameters) para crear consultas para filtrar, ordenar o recuperar los resultados más recientes.

   ![Fuente de OData](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   Al seleccionar **Invocar**, la función OData.Feed realiza una llamada a la API, que abre el editor de consultas y le permite filtrar y restringir el conjunto de datos que quiera usar y, después, cargar ese conjunto de datos restringido en Power BI Desktop.

10. En la imagen siguiente, se muestra la ventana de resultados para las entidades de Microsoft Graph Security con las que haya realizado consultas.

   ![Resultado](media/desktop-connect-graph-security/Result.PNG)
    

Ahora está listo para usar los datos importados del conector Microsoft Graph Security en Power BI Desktop para crear objetos visuales e informes, o bien para interactuar con cualquier otro dato al que quiera conectarse e importar, como otros libros de Excel, bases de datos o cualquier otro origen de datos.

## <a name="next-steps"></a>Pasos siguientes
* Vea las plantillas y ejemplos de Power BI en los que se usa este conector en el [Repositorio de ejemplo de Power BI de Microsoft Graph Security en GitHub](https://aka.ms/graphsecuritypowerbiconnectorsamples).

* Vea algunos escenarios de usuario e información adicional en la [entrada de blog del conector Microsoft Graph Security de Power BI](https://aka.ms/graphsecuritypowerbiconnectorblogpost).

* Hay todo tipo de datos a los que puede conectarse con Power BI Desktop. Para obtener más información sobre orígenes de datos, consulte los siguientes recursos:

    * [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
    * [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
    * [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
    * [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)
    * [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
