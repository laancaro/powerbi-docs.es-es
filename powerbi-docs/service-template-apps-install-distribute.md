---
title: 'Distribución de aplicaciones de plantilla en la organización: Power BI'
description: Obtenga información sobre cómo instalar, personalizar y distribuir aplicaciones de plantilla de la organización en Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 158345c44f8801a98e19dcd9b4c7dde14aa6126b
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264536"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>Instalación y distribución de aplicaciones de plantilla en la organización: Power BI

¿Es un analista de Power BI? Si es así, este artículo explica cómo instalar *aplicaciones de plantilla* para conectarse a muchos de los servicios que usa para dirigir su negocio, como Salesforce, Microsoft Dynamics y Google Analytics. Puede modificar los paneles e informes para satisfacer las necesidades de su organización y distribuirlos después a sus compañeros de trabajo como una *aplicación*. 

![Aplicaciones de Power BI instaladas](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Si está interesado en crear aplicaciones de plantilla para distribuirlas usted mismo, vea [Creación de una plantilla de aplicación en Power BI](service-template-apps-create.md). Los asociados de Power BI pueden crear aplicaciones de Power BI con poca o ninguna codificación e implementarlas en los clientes de Power BI. 

## <a name="prerequisites"></a>Requisitos previos  

Estos son los requisitos para instalar, personalizar y distribuir una aplicación de plantilla: 

- Una [licencia de Power BI Pro](service-self-service-signup-for-power-bi.md).
- Familiaridad con los [conceptos básicos de Power BI](service-basic-concepts.md).
- Vínculo de instalación válido del creador de la aplicación plantilla o AppSource. 
- Permisos para instalar aplicaciones de plantilla. 

## <a name="install-a-template-app"></a>Instalación de una aplicación de plantilla

Es posible que reciba un vínculo a una aplicación de plantilla. En caso contrario, puede buscar una que le interese en AppSource. En cualquier caso, después de la instalación, puede modificarla y distribuirla a su propia organización.

### <a name="search-appsource-from-a-browser"></a>Búsqueda en AppSource desde un explorador

En un explorador, haga clic en este vínculo para abrir AppSource filtrado por las aplicaciones de Power BI:

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>Búsqueda en AppSource desde el servicio Power BI

1. En el panel de navegación de la izquierda del servicio Power BI, haga clic en **Aplicaciones** > **Obtener aplicaciones**.

    ![Obtener aplicaciones](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. En AppSource, haga clic en **Aplicaciones**.

    ![Búsqueda en AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. Examine o busque la aplicación, y después haga clic en **Obtenerla ahora**.

4. En el cuadro de diálogo, haga clic en **Instalar**.

    ![Instalación de una aplicación](media/service-template-apps-install-distribute/power-install-dialog.png) Si tiene una licencia de Power BI Pro, la aplicación se instala con su área de trabajo de la aplicación asociada. La aplicación se personaliza en el área de trabajo asociada.

    Cuando la instalación se realice correctamente, verá una notificación en la que se indica que la nueva aplicación está lista.
4. Haga clic en **Ir a la aplicación**.
5. En **Empezar a trabajar con la nueva aplicación**, seleccione una de las tres opciones:

    ![Empezar a trabajar con la aplicación](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **Explorar la aplicación**: exploración básica de datos de ejemplo. Comience aquí para obtener la apariencia de la aplicación. 
    - **Conectar datos**: cambie el origen de datos de los datos de ejemplo al suyo propio. Puede volver a definir los parámetros de conjunto de datos y las credenciales del origen de datos. Vea [Limitaciones conocidas](service-template-apps-tips.md#known-limitations) en el artículo sobre sugerencias para aplicaciones de plantilla. 
    - **Ir a área de trabajo** (opción más avanzada): puede realizar cualquier cambio permitido por el desarrollador de la aplicación.

    O bien, omita este cuadro de diálogo y acceda a un área de trabajo asociada directamente a través de **Áreas de trabajo** en el panel de navegación de la izquierda.
    >[!NOTE]
    >Instalación de una aplicación de plantilla instalada tanto en una *aplicación de organización* como en una *aplicación de área de trabajo*. Obtenga más información sobre la [distribución de aplicaciones en Power BI](service-create-distribute-apps.md).
 
6. Antes de compartirla con lo compañeros de trabajo, le interesará conectarse a sus propios datos. También querrá modificar el informe o el panel para que funcione para la organización. Además, en este momento puede agregar otros informes o paneles.

   Si selecciona un vínculo de instalación de una aplicación que no figure en AppSource, se le mostrará el cuadro de diálogo de validación, en el que deberá confirmar su elección.

   ![Instalar aplicación](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >Para instalar aplicaciones de la plantilla que no figuren en AppSource, deberá solicitar permiso al administrador. Vea la [configuración de aplicaciones de plantilla en el portal de administración](service-admin-portal.md#template-apps-settings) de Power BI para obtener más información.

## <a name="update-and-distribute-the-app"></a>Actualización y distribución de la aplicación

Después de actualizar la aplicación para la organización, está listo para publicarla. Los pasos son los mismos que para publicar cualquier otra aplicación.

1. Cuando haya terminado la personalización, en la lista de áreas de trabajo seleccione **Actualizar aplicación** en la esquina superior derecha.  

    ![Inicio de la instalación de la aplicación](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. En **Detalles**, puede modificar el color de fondo y la descripción.

   ![Configuración de la descripción y el color de la aplicación](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. En **Contenido**, puede seleccionar una página de aterrizaje, ya sea el panel o el informe.

   ![Configuración de la página de aterrizaje de la aplicación](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. En **Acceso**, conceda acceso a usuarios concretos o a toda la organización.  

   ![Configuración del acceso a la aplicación](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. Haga clic en **Actualizar aplicación**. 

6. Una vez publicada correctamente, puede copiar el vínculo y compartirlo con los usuarios a quienes haya proporcionado acceso. Si lo ha compartido con ellos, también la verán en la pestaña **Mi organización** de AppSource.

## <a name="next-steps"></a>Pasos siguientes 

[Creación de áreas de trabajo con sus compañeros en Power BI](service-create-workspaces.md)





￼ 

 
