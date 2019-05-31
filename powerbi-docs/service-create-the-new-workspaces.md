---
title: Crear nuevas áreas de trabajo - Power BI
description: Obtenga información sobre cómo crear nuevas áreas de trabajo, colecciones de paneles, informes e informes paginados creados para proporcionar métricas claves para su organización.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d0c0781ea5d3864f1cf3627cd42d53cca632102d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61142068"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Crear las nuevas áreas de trabajo en Power BI

Power BI presenta una nueva experiencia de área de trabajo. Las áreas de trabajo siguen siendo el lugar para colaborar con compañeros para crear colecciones de paneles, informes e informes paginados. A continuación, puede agrupar esa colección en un *aplicación* y distribuirlo a toda la organización o a grupos o usuarios específicos. 

Aquí es lo que es diferente. En las áreas de trabajo nueva, puede:

- Asignar roles de área de trabajo a grupos de usuarios: grupos de seguridad, listas de distribución, grupos de Office 365 y usuarios.
- Crear un área de trabajo en Power BI sin crear un grupo de Office 365.
- Usar roles de las áreas de trabajo más granulares para flexibilizar la administración de permisos en un área de trabajo.

> [!NOTE]
> Para aplicar la seguridad de nivel de fila (RLS) para examinar el contenido de un área de trabajo de usuarios de Power BI Pro, seguir usando [las áreas de trabajo clásicos](service-create-workspaces.md). Seleccione el **miembros solo pueden ver contenido de Power BI** opción. También puede publicar una aplicación de Power BI a los usuarios o uso compartido para distribuir contenido. El rol de visor próximamente permitirá este escenario en el futuro en nuevas áreas de trabajo de experiencia de área de trabajo.

Para obtener más información, consulte el [nuevas áreas de trabajo](service-new-workspaces.md) artículo.

## <a name="create-one-of-the-new-app-workspaces"></a>Creación de una de las nuevas áreas de trabajo de la aplicación

1. Comience por crear el área de trabajo de la aplicación. Seleccione **Áreas de trabajo** > **Crear área de trabajo de la aplicación**.
   
     ![Crear área de trabajo de la aplicación](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. Crea un área de trabajo actualizada, automáticamente, a menos que decida **revertir a clásico**.
   
     ![Nueva experiencia de área de trabajo](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Si selecciona **revertir a clásico**, cree un área de trabajo basado en un grupo de Office 365. Use esta opción si necesita la **miembros solo pueden ver contenido de Power BI** opción para exigir la seguridad de nivel de fila (RLS) para los miembros del área de trabajo.

2. Asigne un nombre al área de trabajo. Si el nombre no está disponible, editarlo para proponer un nombre único.
   
     La aplicación para el área de trabajo tendrá el mismo nombre y el icono como el área de trabajo.
   
1. Estos son algunos elementos opcionales que puede establecer para el área de trabajo:

    Cargar un **imagen del área de trabajo**. Los archivos pueden tener formato .png o .jpg. Tamaño del archivo debe ser inferior a 45 KB.
    
    [Agregar un **lista de contactos**](#workspace-contact-list). De forma predeterminada, los administradores del área de trabajo son los contactos. 
    
    [Especifique un **OneDrive del área de trabajo** ](#workspace-onedrive) escribiendo simplemente el nombre de un grupo existente de 365 de Office, no la dirección URL. Ahora esta área de trabajo puede usar la ubicación de almacenamiento de archivos de ese grupo de Office 365. 

    ![Especifique una ubicación de OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    Para asignar el área de trabajo a un **capacidad dedicada**, en el **Premium** ficha, seleccione **capacidad dedicada**.
     
    ![Capacidad dedicada](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Seleccione **Guardar**.

    Power BI crea el área de trabajo y la abre. Esta aparece en la lista de áreas de trabajo de las que es miembro. 

## <a name="workspace-contact-list"></a>Lista de contactos de área de trabajo

La nueva lista de contactos de área de trabajo permite especificar qué usuarios reciben una notificación acerca de los problemas que se producen en el área de trabajo. De forma predeterminada, cualquier usuario o grupo especificado como un área de trabajo se notifica al administrador, pero se puede personalizar la lista. Los usuarios o grupos que aparecen en la lista de contactos se mostrará en la interfaz de usuario (UI) para ayudar a los usuarios obtención ayuda relacionada con el área de trabajo.

1. Obtener acceso a la nueva **lista de contactos** establecer en uno de dos maneras:

    En el **crear un área de trabajo** panel cuando se crea por primera vez.

    En el panel de navegación izquierdo, seleccione la flecha situada junto a **las áreas de trabajo**, seleccione los puntos suspensivos (...) junto al nombre del área de trabajo > **configuración de área de trabajo**. El **configuración** se abre el panel.

    ![Configuración del área de trabajo](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. En **avanzadas** > **lista de contactos**, acepte el valor predeterminado, **administradores del área de trabajo**, o agregar su propia lista de **determinados usuarios o grupos**. 
3. Seleccione **Guardar**.

## <a name="workspace-onedrive"></a>OneDrive del área de trabajo

La característica de OneDrive del área de trabajo permite configurar un grupo de Office 365 está disponible para los usuarios del área de trabajo cuyo almacenamiento de archivo de biblioteca de documentos de SharePoint. Cree primero el grupo de Power BI. 

Power BI no sincronizará los permisos de usuarios o grupos que están configurados para tener acceso de área de trabajo con la pertenencia al grupo de Office 365. El procedimiento recomendado es proporcionar el mismo grupo de Office 365, configura en este grupo de configuración de Office 365, cuyo almacenamiento de archivos [acceso al área de trabajo](#give-access-to-your-workspace). Administrar el acceso de área de trabajo mediante la administración de pertenencia del grupo de Office 365. 

1. Obtener acceso a la nueva **OneDrive del área de trabajo** establecer en uno de dos maneras:

    En el **crear un área de trabajo** panel cuando se crea por primera vez.

    En el panel de navegación izquierdo, seleccione la flecha situada junto a **las áreas de trabajo**, seleccione los puntos suspensivos (...) junto al nombre del área de trabajo > **configuración de área de trabajo**. El **configuración** se abre el panel.

    ![Configuración del área de trabajo](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. En **avanzadas** > **OneDrive del área de trabajo**, escriba el nombre del grupo de Office 365 que creó anteriormente. Power BI recogerá de forma automática para el grupo de OneDrive.

    ![Especifique una ubicación de OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Seleccione **Guardar**.

### <a name="access-the-workspace-onedrive-location"></a>Obtener acceso a la ubicación de OneDrive del área de trabajo

Después de configurar la ubicación de OneDrive, puede obtener desde diferentes lugares en el área de trabajo:

- Seleccione **las áreas de trabajo** > *nombre de área de trabajo* > los puntos suspensivos ( **...** ) menú > **archivos**. 

    ![Ubicación de los archivos del área de trabajo](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Seleccione los puntos suspensivos ( **...** ) menú en la esquina superior derecha del área de trabajo > **archivos**.

    ![Ubicación de los archivos del área de trabajo](media/service-new-workspaces/power-bi-new-workspace-files-2.png)
    
- En el **obtener datos** > **archivos** experimentar. El **OneDrive – Business** entrada es OneDrive para la empresa. La segunda instancia de OneDrive es lo que se ha agregado.

    ![Ubicación de los archivos del área de trabajo: obtención de datos](media/service-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-app-workspace"></a>Agregar contenido al área de trabajo de la aplicación

Después de crear una nueva área de trabajo de experiencia de área de trabajo, es momento de agregar contenido a ella. Agregar contenido es similar en las áreas de trabajo nuevas y clásicas. Utilice el botón Crear o usar obtener datos para agregar contenido al área de trabajo.

1. En el **bienvenida** pantalla del área de trabajo nueva, puede agregar contenido. 

    ![Pantalla de bienvenida del área de trabajo nueva](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. Por ejemplo, seleccione **Ejemplos** > **Ejemplo de rentabilidad del cliente**.

> [!NOTE]
> En las áreas de trabajo nuevo, no puede consumir paquetes de contenido organizativos o paquetes de contenido de terceros. Las aplicaciones están disponibles para todo el contenido de terceros de módulos usó anteriormente. Usar áreas de trabajo clásicos si tiene que seguir usando los paquetes de contenido. Paquetes de contenido están en desuso, por lo que es una práctica recomendada para usar aplicaciones en su lugar.

Al ver el contenido en una lista de contenido de un área de trabajo de la aplicación, el nombre del área de trabajo de la aplicación se muestra como el propietario.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Conectarse a los servicios de terceros en nuevas áreas de trabajo

En la nueva experiencia de áreas de trabajo, estamos llevando a cabo un cambio para que esté centrada en las *aplicaciones*. Las aplicaciones para servicios de terceros facilitan a los usuarios la obtención de datos de los servicios que usan, como Microsoft Dynamics CRM, Salesforce o Google Analytics.

En la nueva experiencia de área de trabajo, no puede crear o consumir paquetes de contenido organizativos. En su lugar, puede usar las aplicaciones proporcionadas para conectarse a servicios de terceros, o pida a los equipos internos que proporcionen aplicaciones para cualquier paquete de contenido que usen actualmente. 

## <a name="give-access-to-your-workspace"></a>Conceder acceso al área de trabajo

1. En la lista de contenido del área de trabajo, porque es un administrador puede ver una nueva acción, **acceso**.

    ![Lista de contenido de las áreas de trabajo](media/service-create-the-new-workspaces/power-bi-workspace-content-list.png)

1. Seleccione **Acceso**.

1. Agregue grupos de seguridad, listas de distribución, grupos de Office 365 o usuarios a estas áreas de trabajo como miembros, colaboradores o administradores. Consulte [Roles en las nuevas áreas de trabajo](service-new-workspaces.md#roles-in-the-new-workspaces) para obtener una explicación de los distintos roles.

    ![Las áreas de trabajo agregan miembros, administradores y colaboradores](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. Seleccione **Agregar** > **Cerrar**.


## <a name="distribute-an-app"></a>Distribución de una aplicación

Si desea distribuir contenido oficial para una gran audiencia dentro de su organización, puede publicar una aplicación desde el área de trabajo.  Cuando el contenido está listo, elija qué paneles e informes que desea publicar y, a continuación, publicarlo como un *aplicación*. Puede crear una aplicación desde cada área de trabajo.

Obtenga información sobre [publicar una aplicación de las nuevas áreas de trabajo](service-create-distribute-apps.md)

## <a name="next-steps"></a>Pasos siguientes
* Obtenga información sobre [organizar el trabajo en la nueva experiencia de áreas de trabajo en Power BI](service-new-workspaces.md)
* [Crear áreas de trabajo clásicos](service-create-workspaces.md)
* [Publicar una aplicación de las nuevas áreas de trabajo en Power BI](service-create-distribute-apps.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
