---
title: Creación de aplicaciones de plantilla en Power BI (versión preliminar)
description: Cómo crear aplicaciones de plantilla en Power BI que puede distribuir a cualquier cliente de Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: maggies
ms.openlocfilehash: c08b7e60777b720aa4fc2489b02c212bdd3e7169
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2019
ms.locfileid: "56250036"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Creación de una aplicación de plantilla en Power BI (versión preliminar)

Las nuevas *aplicaciones de plantilla* de Power BI permiten a los asociados de Power BI crear aplicaciones de Power BI con poca o ninguna codificación, e implementarlas en cualquier cliente de Power BI.  Este artículo contiene instrucciones paso a paso para crear una aplicación de plantilla de Power BI. 

Si puede crear paneles e informes de Power BI, puede convertirse en un *desarrollador de aplicaciones de plantilla* que compila y empaqueta contenido analítico en una *aplicación*. Después, puede implementar la aplicación en otros inquilinos de Power BI a través de cualquier plataforma disponible, como AppSource, o bien usarla en un servicio web propio. Como desarrollador, puede crear un paquete de análisis protegido para su distribución. 

Los administradores de inquilinos de Power BI controlan quién de la organización puede crear aplicaciones de plantilla y quién puede instalarlas. Los que estén autorizados pueden instalar la aplicación de plantilla y después modificarla y distribuirla a los consumidores de Power BI en su organización.

## <a name="prerequisites"></a>Requisitos previos 

Estos son los requisitos para crear una aplicación la plantilla:  

- Una [licencia de Power BI Pro](service-self-service-signup-for-power-bi.md).
- Una [instalación de Power BI Desktop](desktop-get-the-desktop.md) (opcional).
- Familiaridad con los [conceptos básicos de Power BI](service-basic-concepts.md).
- Permisos para crear una aplicación de plantilla. Vea la [configuración de aplicaciones de plantilla en el portal de administración](service-admin-portal.md#template-apps-settings-preview) de Power BI para obtener más información.

## <a name="enable-app-developer-mode"></a>Habilitación del modo de desarrollador de aplicaciones

Para crear una aplicación de plantilla que se pueda distribuir a otros inquilinos de Power BI, tendrá que estar en modo de desarrollador de aplicaciones. En caso contrario, simplemente se crea una aplicación para los consumidores de Power BI en su propia organización.
 
1. Abra el servicio Power BI en un explorador.
2. Vaya a **Configuración** > **General** > **Desarrollador** > **Habilitar modo de desarrollo de aplicaciones de plantilla**.

    ![Habilitación de las aplicaciones de plantilla](media/service-template-apps-create/power-bi-dev-template-app.png)

    Si no ve esta opción, póngase en contacto con el administrador de Power BI para que le conceda [permisos para el desarrollo de aplicaciones de plantilla](service-admin-portal.md#template-apps-settings-preview) en el portal de administración.

3. Seleccione **Aplicar**.

## <a name="create-the-template-app-workspace"></a>Creación del área de trabajo de la aplicación de plantilla

Para crear una aplicación de plantilla que se pueda distribuir a otros inquilinos de Power BI, tendrá que crearla en una de las nuevas áreas de trabajo de la aplicación. 
 
1. En el servicio Power BI, haga clic en **Áreas de trabajo** > **Crear área de trabajo de la aplicación**. 
 
    ![Crear área de trabajo de la aplicación](media/service-template-apps-create/power-bi-new-workspace.png)

3. En **Crear un área de trabajo**, en **Vista previa de las áreas de trabajo mejoradas**, haga clic en **Intentar ahora**.

    ![Prueba de las nuevas áreas de trabajo](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

5. Proporcione un nombre, una descripción (opcional) y un logotipo de imagen (opcional) para el área de trabajo de la aplicación.

4. Active **Desarrollar una aplicación de plantilla**.

    ![Desarrollar una aplicación de plantilla](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Seleccione **Guardar**.

## <a name="create-the-content-in-your-template-app"></a>Creación del contenido en la plantilla de aplicación

Como sucede con un área de trabajo de la aplicación estándar de Power BI, el siguiente paso consiste en crear el contenido en el área de trabajo.  En esta versión de versión preliminar de las aplicaciones de plantilla, solo se admite uno de cada tipo: un conjunto de datos, un informe y un panel.

- [Cree el contenido de Power BI](power-bi-creator-landing.md) en el área de trabajo de la aplicación.

Si va a usar parámetros en Power Query, asegúrese de que tengan tipos bien definidos (por ejemplo, Texto). Los tipos Todo y Binario no se admiten. 

En [Sugerencias para la creación de aplicaciones de plantilla en Power BI (versión preliminar)](service-template-apps-tips.md) se proporcionan sugerencias que puede tener en cuenta al crear informes y paneles para la aplicación de plantilla.

## <a name="create-the-test-template-app"></a>Creación de la aplicación de plantilla de prueba

Ahora que tiene contenido en el área de trabajo, está listo para empaquetarlo en una aplicación de plantilla. El primer paso consiste en crear una aplicación de plantilla de prueba, accesible únicamente desde dentro de la organización en su inquilino.

1. En el área de trabajo de la aplicación de plantilla, haga clic en **Crear aplicación**. 

    ![Crear aplicación](media/service-template-apps-create/power-bi-create-app.png)
 
    Aquí, tendrá que rellenar parámetros adicionales para la aplicación de plantilla, en cuatro categorías. 

    **Personalización de marca**

    - Nombre de aplicación 
    - Descripción
    - Logotipo de la aplicación (opcional)
    - Color de la aplicación 

    **Contenido** 

    - Página de aterrizaje de la aplicación (opcional): defina un informe o panel como la página de aterrizaje de la aplicación.  
    
    **Control** 

    Controle varias limitaciones y restricciones que tendrán los usuarios de la aplicación con el contenido de esta. Puede usar este control para proteger determinada propiedad intelectual que la aplicación pueda contener.

    **Acceso**

    - En la fase de prueba, decida qué otros usuarios de la organización pueden instalar y probar la aplicación.

    No se preocupe, siempre puede volver y cambiar estas opciones más adelante.  

2. Haga clic en **Crear aplicación**. 

    Verá un mensaje que indica que la aplicación de prueba está lista, con un vínculo para copiar y compartir con los evaluadores de la aplicación.

    ![Aplicación de prueba lista](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    También ha realizado el primer paso del proceso de administración de versiones, que se muestra a continuación.

    

## <a name="manage-the-template-app-release"></a>Administración de la versión de la plantilla de aplicación

Antes de publicar esta aplicación de plantilla, querrá asegurarse de que esté lista. Power BI ha creado el panel de administración de versiones, donde puede realizar el seguimiento e inspeccionar la ruta de versiones completa de la aplicación. También puede desencadenar la transición de una etapa a otra. Las fases comunes son: 

- Generar la aplicación de prueba: solo para realizar pruebas en la organización. 
- Promover el paquete de prueba a la fase de preproducción: para realizar pruebas fuera de la organización.
- Promover el paquete de preproducción a producción: la versión de producción. 
- Eliminar todos los paquetes o comenzar de nuevo desde la fase anterior. 

A continuación se analizan las fases.

1. En el área de trabajo de la aplicación de plantilla, haga clic en **Release Management** (Administración de versiones).

    ![Icono de Release Management](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Haga clic en **Crear aplicación**. 

    Si anteriormente ha creado la aplicación de prueba en **Creación de la aplicación de plantilla de prueba**, el punto de color amarillo junto a **Pruebas** ya está rellenado y no es necesario hacer clic en **Crear aplicación** aquí. Si hace clic, retrocederá al proceso de creación de la aplicación de plantilla.
 
3. Haga clic en **Obtener vínculo**.

    ![Crear la aplicación, obtener el vínculo](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)
 
9. Para probar la experiencia de instalación de la aplicación, copie el vínculo de la ventana de notificación y péguelo en otra ventana del explorador. 

    Desde aquí, seguirá los mismos pasos que seguirán los clientes. Vea [Instalación y distribución de aplicaciones de plantilla en la organización](service-template-apps-install-distribute.md) para obtener su versión.
 
10. En el cuadro de diálogo, haga clic en **Instalar**.

    Cuando la instalación se realice correctamente, verá una notificación en la que se indica que la nueva aplicación está lista. 
 
11. Haga clic en **Ir a la aplicación**.
 
12. En **Empezar a trabajar con la nueva aplicación**, verá la aplicación como la ven los clientes. 

    ![Empezar a trabajar con la aplicación](media/service-template-apps-create/power-bi-template-app-get-started.png)

13. Haga clic en **Explorar la aplicación** para comprobar la aplicación de prueba con los datos de ejemplo.

1. Para realizar cambios, vuelva a la aplicación en el área de trabajo original. Actualice la aplicación de prueba hasta que esté satisfecho.

9. Cuando esté listo para promover la aplicación al entorno de preproducción para realizar más pruebas fuera del inquilino, vuelva al panel **Release Management** y haga clic en **Promover aplicación** junto a **Pruebas**.
 
    ![Promoción de la aplicación a preproducción](media/service-template-apps-create/power-bi-template-app-promote.png)

11. Haga clic en **Promover** para confirmar la elección. 

12. Copie esta nueva dirección URL para compartir fuera del inquilino con el fin de realizar pruebas. Este vínculo también es el que se envía para comenzar el proceso de distribución de la aplicación en AppSource.

12. Cuando la aplicación esté lista para producción o para compartirla a través de AppSource, vuelva al panel **Release Management** y haga clic en **Promover aplicación** junto a **Preproducción**.
 
11. Haga clic en **Promover** para confirmar la elección. 

    Ahora la aplicación está en producción, lista para su distribución.

    ![Aplicación en producción](media/service-template-apps-create/power-bi-template-app-production.png)

Para hacer que la aplicación esté disponible a miles de usuarios de Power BI en todo el mundo, le animamos a enviarla a AppSource. Vea [Oferta de aplicación de Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obtener más información. 

## <a name="update-your-app"></a>Actualización de la aplicación

Ahora que la aplicación está en producción, puede empezar de nuevo en la fase de prueba, sin interrumpir la aplicación en producción. 

1. En el panel **Release Management**, haga clic en **Crear aplicación**.

1. Vuelva a realizar el proceso de creación de la aplicación. 
2. Después de establecer **Personalización de marca**, **Contenido**, **Control** y **Acceso**, vuelva a hacer clic en **Crear aplicación**.
3. Haga clic en **Cerrar** y vuelva a **Release Management**. 

    Ahora verá que tiene dos versiones: la versión en producción, además de una nueva versión de prueba. 

    ![Dos versiones de una aplicación de plantilla](media/service-template-apps-create/power-bi-template-app-2-versions.png)

## <a name="next-steps"></a>Pasos siguientes

Vea cómo interactúan los clientes con la aplicación de plantilla en [Instalación, personalización y distribución de aplicaciones de plantilla en la organización](service-template-apps-install-distribute.md).

Vea [Oferta de aplicación de Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obtener información sobre cómo distribuir la aplicación.





