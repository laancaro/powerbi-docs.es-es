---
title: Crear áreas de trabajo con sus compañeros en Power BI
description: Aprenda a crear áreas de trabajo, colecciones de paneles e informes creados para proporcionar métricas clave a su organización.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f12974d4e53217fc6c29ad172153ec9c51ecc44e
ms.sourcegitcommit: 6c6aa214dc36c26a01b29e823598d217a3e2b8a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2018
ms.locfileid: "53451430"
---
# <a name="create-workspaces-with-your-colleagues-in-power-bi"></a>Crear áreas de trabajo con sus compañeros en Power BI

En Power BI, puede crear *áreas de trabajo*, lugares donde colaborar con compañeros para crear y perfeccionar las colecciones de paneles e informes. Después, los agrupa en *aplicaciones*  que puede distribuir en toda la organización, a grupos o usuarios específicos. 

![Aplicaciones de Power BI](media/service-create-workspaces/power-bi-apps-left-nav.png)

Cuando crea un área de trabajo, crea un grupo de Office 365 subyacente, asociado. Toda la administración del área de trabajo se realiza en Office 365. Puede agregar compañeros a estas áreas de trabajo como miembros o administradores. En el área de trabajo, es posible colaborar en paneles, informes y otros artículos que planee publicar para un público más amplio. Todos los usuarios que agregue a un área de trabajo de la aplicación necesita una licencia de Power BI Pro. 

**¿Sabía qué?** Power BI está realizando una versión preliminar de una nueva experiencia de áreas de trabajo. Lea [Crear nuevas áreas de trabajo (versión preliminar)](service-create-the-new-workspaces.md) para ver cómo cambiarán las áreas de trabajo en el futuro. 

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicaciones y áreas de trabajo de aplicación
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-an-app-workspace-based-on-an-office-365-group"></a>Crear un área de trabajo de la aplicación en función de un grupo de Office 365

Cuando crea un área de trabajo de la aplicación, se crea en función de un grupo de Office 365.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

La primera vez que la cree puede que tenga que esperar una hora aproximadamente hasta que el área de trabajo se propague a Office 365. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Agregar una imagen a su área de trabajo de la aplicación de Office 365 (opcional)
De forma predeterminada, Power BI crea un pequeño círculo coloreado para la aplicación, con las iniciales de la aplicación. Pero tal vez desee personalizarlo con una imagen. Para agregar una imagen, necesita una licencia de Exchange Online.

1. Seleccione **Áreas de trabajo**, seleccione el botón de puntos suspensivos (...) junto al nombre del área de trabajo y, a continuación, seleccione **Miembros**. 
   
     ![Seleccionar miembros del área de trabajo](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    La cuenta de Outlook de Office 365 del área de trabajo se abre en una nueva ventana del navegador.
2. Al situarse sobre el círculo coloreado en la parte superior izquierda, se convierte en un icono de lápiz. Selecciónela.
   
     ![Icono de lápiz de Office 365](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Vuelva a seleccionar el icono de lápiz y busque la imagen que desea utilizar.
   
     ![Volver a seleccionar el lápiz](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)

4. Seleccione **Guardar**.
   
     ![Seleccionar Guardar](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    La imagen reemplaza al círculo coloreado en la ventana de Outlook de Office 365. 
   
     ![Imagen personalizada](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    En unos minutos, aparecerá también en la aplicación de Power BI.
   
     ![Imagen personalizada](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="add-content-to-your-app-workspace"></a>Agregar contenido al área de trabajo de la aplicación

Después de crear un área de trabajo de la aplicación, es el momento de agregarle contenido. Esto es igual que agregar contenido a Mi área de trabajo, excepto que las otras personas del área de trabajo pueden verlo y también trabajar con él. Una gran diferencia es que, cuando haya finalizado, podrá publicar el contenido como una aplicación. Al ver el contenido en una lista de contenido de un área de trabajo de la aplicación, el nombre del área de trabajo de la aplicación se muestra como el propietario.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Conectarse a servicios de terceros en las áreas de trabajo de la aplicación

Las aplicaciones se proporcionan para todos los servicios de terceros compatibles con Power BI, lo que facilita la obtención de datos de los servicios que usa, como Microsoft Dynamics CRM, Salesforce o Google Analytics. Puede publicar aplicaciones de la organización para ofrecer a los usuarios los datos internos que necesitan.

En las áreas de trabajo actuales, también puede conectarse mediante paquetes de contenido de la organización y a paquetes de contenido de terceros, como Microsoft Dynamics CRM, Salesforce o Google Analytics. Considere la posibilidad de migrar los paquetes de contenido de la organización a las aplicaciones.

## <a name="distribute-an-app"></a>Distribución de una aplicación

Si el contenido está listo, elija en qué paneles e informes quiere publicarlo y publíquelo como una *aplicación*. Sus compañeros de trabajo pueden obtener las aplicaciones de varias maneras diferentes. Si el administrador de Power BI le concede permiso, puede instalarlas automáticamente en las cuentas de Power BI de sus compañeros de trabajo. En caso contrario, pueden buscar e instalar estas aplicaciones desde Microsoft AppSource, o bien puede enviarles un vínculo directo. Obtienen las actualizaciones automáticamente y se puede controlar la frecuencia con la que se actualizan los datos. Vea [Publicar aplicaciones con los paneles e informes de Power BI](service-create-distribute-apps.md) para obtener más detalles.

## <a name="power-bi-apps-faq"></a>Preguntas más frecuentes sobre las aplicaciones de Power BI

### <a name="how-are-apps-different-from-organizational-content-packs"></a>¿En qué se diferencian las aplicaciones de los paquetes de contenido organizativo?
Las aplicaciones son la evolución de los paquetes de contenido organizativos. Si ya tiene paquetes de contenido organizativos, estos seguirán funcionando en paralelo con las aplicaciones. Las aplicaciones y los paquetes de contenido tienen algunas diferencias importantes. 

* Después de que los usuarios empresariales instalan un paquete de contenido, este pierde su identidad agrupada: es solo una lista de paneles e informes que se combinan con otros paneles e informes. Por otro lado, las aplicaciones mantienen su agrupación e identidad incluso después de la instalación. Esto facilita que los usuarios empresariales continúen yendo a ellas en el tiempo.
* Puede crear varios paquetes de contenido de cualquier área de trabajo, pero una aplicación tiene una relación de 1:1 con su área de trabajo. 
* Con el tiempo, tenemos previsto dejar de utilizar paquetes de contenido organizativos, por lo que recomendamos crear aplicaciones de ahora en adelante.  
* Con la versión preliminar de la experiencia de las nuevas áreas de trabajo, se están dando los primeros pasos para dejar en desuso los paquetes de contenido de la organización. No los puede usar ni crear en las áreas de trabajo de la versión preliminar.

Vea [¿En qué se diferencian las áreas de trabajo de la aplicación nuevas y las áreas de trabajo actuales?](service-create-the-new-workspaces.md#how-are-the-new-app-workspaces-different-from-current-app-workspaces) para comparar las áreas de trabajo de la aplicación actuales y las nuevas. 

## <a name="next-steps"></a>Pasos siguientes
* [Instalar y usar aplicaciones en Power BI](service-create-distribute-apps.md)
- [Crear nuevas áreas de trabajo (versión preliminar)](service-create-the-new-workspaces.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
