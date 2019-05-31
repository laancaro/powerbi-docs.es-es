---
title: Crear áreas de trabajo clásicos en Power BI
description: Obtenga información sobre cómo crear áreas de trabajo, colecciones de paneles, informes e informes paginados creados para proporcionar métricas claves para su organización.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: dcf9b8befabfec98fcae154e6276f8e698b3ddc2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61151046"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Crear áreas de trabajo clásicos en Power BI

En Power BI, puede crear *las áreas de trabajo*, coloca para colaborar con compañeros para crear y perfeccionar las colecciones de paneles, informes y los informes paginados. A continuación, puede agrupar la colección en *aplicaciones* que se puede distribuir a toda la organización o a grupos o usuarios específicos. 

**¿Sabía qué?** Power BI ofrece una nueva experiencia de área de trabajo, que ahora es el valor predeterminado. Lectura [organizar el trabajo en las áreas de trabajo nueva](service-new-workspaces.md) para obtener más información acerca de las nuevas áreas de trabajo. 

Cuando se crea un área de trabajo clásico, creamos un grupo de Office 365 subyacente, asociado. Toda la administración del área de trabajo se realiza en Office 365. Puede agregar compañeros a estas áreas de trabajo como miembros o administradores. En el área de trabajo, es posible colaborar en paneles, informes y otros artículos que planee publicar para un público más amplio. Todos los usuarios que agregue a un área de trabajo de la aplicación necesita una licencia de Power BI Pro. 

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicaciones y áreas de trabajo de aplicación
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-app-workspace-based-on-an-office-365-group"></a>Crear un área de trabajo de aplicación clásico basado en un grupo de Office 365

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

     Las imágenes pueden ser archivos .png, .jpg o. bmp. Su tamaño de archivo puede ser grande, de hasta 3 MB. 

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

En las áreas de trabajo actuales, también puede conectarse mediante paquetes de contenido de la organización y paquetes de contenido de terceros, como Microsoft Dynamics CRM, Salesforce o Google Analytics. Considere la posibilidad de migrar los paquetes de contenido de la organización a las aplicaciones.

## <a name="distribute-an-app"></a>Distribución de una aplicación

Si desea distribuir contenido oficial para una gran audiencia dentro de su organización, puede publicar una aplicación desde el área de trabajo.  Cuando el contenido está listo, elija qué paneles e informes que desea publicar y, a continuación, publicarlo como un *aplicación*. Puede crear una aplicación desde cada área de trabajo.

La lista de aplicaciones en el panel izquierdo muestra todas las aplicaciones que haya instalado. Los compañeros de trabajo pueden obtener la aplicación de varias maneras diferentes. 
- Pueden encontrar e instalar la aplicación desde Microsoft AppSource
- Se puede enviarles un vínculo directo. 
- Si el administrador de Power BI le concede permiso, puede instalarla automáticamente en las cuentas de Power BI de los compañeros de trabajo. 

Los usuarios ver contenido de la aplicación actualizada automáticamente después de publicar una actualización del área de trabajo. Puede controlar con qué frecuencia se actualizan los datos mediante el establecimiento de la programación de actualización en los conjuntos de datos utilizado por el contenido de la aplicación en el área de trabajo. Consulte [publicar una aplicación de las nuevas áreas de trabajo en Power BI](service-create-distribute-apps.md) para obtener más información.

## <a name="power-bi-classic-apps-faq"></a>Aplicaciones de Power BI clásicas preguntas más frecuentes

### <a name="how-are-apps-different-from-organizational-content-packs"></a>¿En qué se diferencian las aplicaciones de los paquetes de contenido organizativo?
Las aplicaciones son la evolución de los paquetes de contenido organizativos. Si ya tiene paquetes de contenido organizativos, estos seguirán funcionando en paralelo con las aplicaciones. Las aplicaciones y los paquetes de contenido tienen algunas diferencias importantes. 

* Después de que los usuarios empresariales instalan un paquete de contenido, este pierde su identidad agrupada: es solo una lista de paneles e informes que se combinan con otros paneles e informes. Por otro lado, las aplicaciones mantienen su agrupación e identidad incluso después de la instalación. Este agrupamiento facilita que los usuarios empresariales continúen yendo a ellas a lo largo del tiempo.
* Puede crear varios paquetes de contenido de cualquier área de trabajo, pero una aplicación tiene una relación de 1:1 con su área de trabajo. 
* Con el tiempo, tenemos previsto dejar de utilizar paquetes de contenido organizativos, por lo que recomendamos crear aplicaciones de ahora en adelante.  
* Con la versión preliminar de la experiencia de las nuevas áreas de trabajo, se están dando los primeros pasos para dejar en desuso los paquetes de contenido de la organización. No los puede usar ni crear en las áreas de trabajo de la versión preliminar.

Vea [¿En qué se diferencian las áreas de trabajo de la aplicación nuevas y las áreas de trabajo actuales?](service-new-workspaces.md#how-are-the-new-workspaces-different-from-current-workspaces) para compararlas. 

## <a name="next-steps"></a>Pasos siguientes
* [Instalar y usar aplicaciones en Power BI](service-create-distribute-apps.md)
- [Crear nuevas áreas de trabajo (versión preliminar)](service-create-the-new-workspaces.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
