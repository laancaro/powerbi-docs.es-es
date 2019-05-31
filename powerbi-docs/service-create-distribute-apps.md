---
title: Publicar una aplicación en Power BI
description: Obtenga información sobre cómo publicar las nuevas aplicaciones, que son colecciones de paneles e informes con la navegación integrada.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941560"
---
# <a name="publish-an-app-in-power-bi"></a>Publicar una aplicación en Power BI

En Power BI, puede crear contenido oficial empaquetada y luego distribuirlo a un público amplio como un *aplicación*. Cree aplicaciones en *áreas de trabajo de la aplicación*, donde puede colaborar en contenido de Power BI con sus compañeros. Después, puede publicar las aplicaciones terminadas en grandes grupos de usuarios de su organización. 

![Aplicaciones de Power BI](media/service-create-distribute-apps/power-bi-new-apps.png)

Los usuarios empresariales suelen necesitar varios paneles e informes de Power BI para hacer funcionar sus negocios. Con las aplicaciones de Power BI, puede crear colecciones de paneles e informes y publicar estas aplicaciones para toda la organización o para grupos o usuarios específicos. Los creadores de informes o los administradores verán lo fácil que es administrar permisos sobre estas colecciones con las aplicaciones.

Los usuarios empresariales obtienen sus aplicaciones de varias maneras diferentes:

- Pueden encontrar e instalar la aplicación desde Microsoft AppSource
- Se puede enviarles un vínculo directo.
- Si el administrador de Power BI le concede permiso, puede instalarla automáticamente en las cuentas de Power BI de los compañeros de trabajo.

Puede crear la aplicación con su propia navegación integrada, por lo que los usuarios puedan encontrar fácilmente su camino por su contenido. No pueden modificar el contenido de la aplicación. Pueden interactuar con él en el servicio Power BI o una de las aplicaciones móviles-: filtrado, resaltado y ordenar los datos por sí mismos. Obtienen las actualizaciones automáticamente y se puede controlar la frecuencia con la que se actualizan los datos. Obtenga información sobre la [experiencia de aplicación para usuarios empresariales](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licencias para aplicaciones
Para crear o actualizar una aplicación, necesita una licencia de Power BI Pro. Para la aplicación *consumidores*, hay dos opciones.

* Opción 1: todos los usuarios empresariales necesitan licencias de **Power BI Pro** para ver la aplicación. 
* Opción 2: Si el área de trabajo de aplicación reside en una capacidad de Power BI Premium, libere a los usuarios de su organización puede ver el contenido de la aplicación. Para más información, lea [What is Power BI Premium?](service-premium.md) (¿Qué es Power BI Premium?)

## <a name="publish-your-app"></a>Publicar su aplicación
Cuando los paneles e informes en el área de trabajo estén listos, elija cuáles quiere publicar y luego publíquelos como una aplicación. 

1. En la vista de lista del área de trabajo, decida qué paneles e informes que desee **incluido en la aplicación**.

     ![Seleccionar el panel que va a publicar](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Si elige no incluyen un informe que tiene un panel relacionado, verá una advertencia junto al informe. Todavía puede publicar la aplicación, pero al panel relacionado no tendrá los iconos de ese informe.

     ![Advertencia sobre un panel relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Seleccione el **publicar aplicación** botón en la esquina superior derecha para iniciar el proceso de creación y publicación de una aplicación desde el área de trabajo.
   
     ![Publicar aplicación](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. En **instalación**, rellene el nombre y una descripción para ayudar a las personas a encontrar la aplicación. Puede establecer un color de tema para personalizarla. También puede agregar un vínculo a un sitio de soporte técnico.
   
     ![Compilar la aplicación](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. En **navegación**, seleccione el contenido se publique como parte de la aplicación. A continuación, Agregar navegación de la aplicación, para organizar el contenido en secciones. Consulte [diseñar la experiencia de navegación de la aplicación](#design-the-navigation-experience-for-your-app) en este artículo para obtener más información.
   
     ![Navegación de aplicación](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. En **acceso**, decidir quién tiene acceso a la aplicación. 
    - En [las áreas de trabajo clásicos](service-create-workspaces.md): todas las personas de su organización, usuarios específicos o grupos de seguridad de Azure Active Directory (AAD).
    - En el [nuevas áreas de trabajo de la experiencia](service-create-the-new-workspaces.md): personas específicas, grupos de seguridad AAD y las listas de distribución y grupos de Office 365.

6. Si tiene permisos, puede instalar la aplicación automáticamente para los destinatarios. El administrador de Power BI puede habilitar esta opción en el Portal de administración de Power BI. Obtenga más información sobre [instalar automáticamente una aplicación](#automatically-install-apps-for-end-users) en este artículo.

     ![Permisos de aplicación](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Al seleccionar **publicar aplicación**, verá un mensaje que confirma que está listo para publicar. En el **compartir esta aplicación** cuadro de diálogo, puede copiar la dirección URL que es un vínculo directo a esta aplicación.
   
     ![Finalización de la aplicación](media/service-create-distribute-apps/power-bi-apps-success.png)

Puede enviar que un vínculo directo a las personas ha compartido con, o pueden encontrar yendo a la aplicación en la pestaña aplicaciones **descargar y explorar más aplicaciones de AppSource**. Obtenga información sobre la [experiencia de aplicación para usuarios empresariales](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Cambiar la aplicación publicada
Después de publicar la aplicación, puede que desee cambiarla o actualizarla. Es fácil actualizarla si es un administrador o miembro del área de trabajo de aplicación nuevo. 

1. Abra el área de trabajo de aplicación que corresponde a la aplicación. 
   
     ![Abrir área de trabajo](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Realizar los cambios que desee en los paneles o informes.
 
     El área de trabajo de aplicación es el área de ensayo, por lo que los cambios no se envían en directo a la aplicación hasta que la vuelva a publicar. Esto le permite realizar cambios sin que ello afecte a las aplicaciones publicadas.  
 
    > [!IMPORTANT]
    > Si quita un informe y actualizar la aplicación, incluso si agrega el informe a la aplicación, los consumidores de la aplicación pierden todas las personalizaciones, como marcadores, comentarios, etcetera.  
 
3. Vuelva a la lista del área de trabajo de aplicaciones de contenido y seleccione **actualizar aplicación** en la esquina superior derecha.
   
1. Actualización **instalación**, **navegación**, y **permisos**, si necesita y luego seleccione **actualizar aplicación**.
   
Las personas para las que ha publicado la aplicación ven automáticamente la versión actualizada de la aplicación. 

## <a name="design-the-navigation-experience-for-your-app"></a>Diseñar la experiencia de navegación de la aplicación
El **nuevo generador de exploración** opción permite crear una navegación personalizada para la aplicación. El panel de navegación personalizada resulta más fácil para los usuarios a encontrar y usar el contenido en la aplicación. Las aplicaciones existentes tengan esta opción está desactivada y el nuevo valor predeterminado de las aplicaciones a la opción de.

Cuando la opción está desactivada, puede seleccionar la **página de aterrizaje de la aplicación** sea **contenido específico**, por ejemplo, un panel o informe o seleccione **ninguno** para mostrar una lista de básico contenido al usuario.

Al activar **nuevo generador de exploración**, puede diseñar una navegación personalizada. De forma predeterminada, todos los paneles, informes y libros de Excel que incluye en la aplicación se muestran como una lista plana. 

![Navegación de aplicación](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Puede personalizar aún más la navegación de aplicación por:
* Reordenación de los elementos usando las / flecha abajo. 
* Cambiar el nombre de los elementos de la **informes detalles**, **detalles del panel**, y **detalles del libro**.
* Ocultar ciertos elementos en el panel de navegación.
* Mediante el **New** opción para agregar **secciones** al grupo de contenido relacionado.
* Mediante el **New** opción para agregar un **vínculo** a un recurso externo en el panel de navegación izquierdo. 

Cuando se agrega un **vínculo**, en **vincular detalles** puede elegir en el que se abre el vínculo. De forma predeterminada los vínculos se abren en el **ficha actual**, pero puede seleccionar **nueva pestaña**, o **área de contenido**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Consideraciones sobre el uso de la nueva opción de generador de exploración
Estas son cosas generales que tener en cuenta al usar el nuevo generador de exploración:
* Las páginas del informe se muestran en el área de navegación de la aplicación como una sección expandible
* Si desactivar el generador de navegación nueva y, a continuación, publicar o actualizar la aplicación, se perderán las personalizaciones que haya realizado. Por ejemplo, secciones, ordenación, vínculos y nombres personalizados para los elementos de navegación son todo perdidos.

Al agregar vínculos a la navegación de la aplicación y seleccionando la opción de área de contenido:
* Asegúrese de que se puede incrustar el vínculo. Algunos servicios de bloquean la incrustación de su contenido en sitios de terceros como Power BI.
* No se admite la incrustación de contenido del servicio Power BI, como informes o paneles en otras áreas de trabajo. 
* Insertar Power BI Report Server contenido a través de su nativo insertar contenido de la dirección URL de una implementación local. Siga los pasos de [crear la dirección URL del servidor de informes de Power BI](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) para obtener la dirección URL. Tenga en cuenta que se aplican las reglas de autenticación normal, para ver el contenido requiere una conexión VPN al servidor local. 
* Se muestra una advertencia de seguridad en la parte superior del contenido incrustado para indicar que el contenido no está en Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Instalar aplicaciones para usuarios finales de forma automática
Si un administrador le otorgue permisos, se pueden instalar aplicaciones automáticamente, *insertar* a los usuarios finales. Esta funcionalidad de inserción resulta más fácil distribuir las aplicaciones correctas a las personas o grupos adecuados. La aplicación aparecerá automáticamente en la lista de contenido de las aplicaciones de los usuarios finales. No tienen que le resulte desde Microsoft AppSource o seguir un vínculo de instalación. Vea cómo los administradores habilitar [publicar aplicaciones a los usuarios finales](service-admin-portal.md#push-apps-to-end-users) en el artículo de portal de administración de Power BI.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Cómo insertar una aplicación automáticamente a los usuarios finales
Una vez que el administrador le haya asignado los permisos, tiene una nueva opción para **instalar la aplicación automáticamente**. Cuando active la casilla y seleccione **publicar aplicación** (o **actualizar aplicación**), la aplicación se inserta en todos los usuarios o grupos definidos en el **permisos** sección de la aplicación en el **Acceso** ficha.

![Habilitar la inserción de aplicaciones](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Cómo obtienen los usuarios las aplicaciones que inserción en ellos
Después de insertar una aplicación, se muestra en la lista de sus aplicaciones automáticamente. De esta manera, puede ajustar las aplicaciones que determinados usuarios o roles de trabajo en su organización deben tener a su alcance.

![Habilitar la inserción de aplicaciones](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Consideraciones para instalar automáticamente las aplicaciones
Estos son aspectos que debe tener en cuenta al publicar aplicaciones para los usuarios finales:

* La instalación de una aplicación de forma automática para los usuarios puede llevar tiempo. Mayoría de las aplicaciones que instale inmediatamente para los usuarios, pero la inserción de aplicaciones puede tardar tiempo.  Depende del número de elementos de la aplicación y del número de usuarios con acceso. Se recomienda publicar aplicaciones durante las horas sin actividad con bastante tiempo antes de que los usuarios las necesiten. Compruebe con varios usuarios antes de enviar una comunicación general sobre la disponibilidad de las aplicaciones.

* Actualice el explorador. Para poder ver la aplicación insertada en la lista de aplicaciones, es posible que el usuario necesite actualizar, o cerrar y volver a abrir, el explorador.

* Si los usuarios no ven inmediatamente la aplicación en la lista de aplicaciones, deben actualizar o cerrar y volver a abrir su explorador.

* Intente no abrumar a los usuarios. Tenga cuidado de no insertar demasiadas aplicaciones para que los usuarios perciban que las aplicaciones preinstaladas son útiles. Es mejor controlar quién puede insertar aplicaciones para los usuarios finales a fin de coordinar la programación. Establecer un punto de contacto para obtener aplicaciones de la organización insertadas para los usuarios finales.

* Los usuarios invitados que no han aceptado una invitación no obtengan las aplicaciones instaladas automáticamente para ellos.  

## <a name="unpublish-an-app"></a>Cancelar la publicación de una aplicación
Cualquier miembro de un área de trabajo de la aplicación puede cancelar la publicación de la aplicación.

>[!IMPORTANT]
>Cuando cancela la publicación de una aplicación, los usuarios de la aplicación pierden sus personalizaciones. Que pierdan los marcadores personales, comentarios o las suscripciones asociadas con el contenido de la aplicación. Cancele la publicación de una aplicación solo si es necesario quitarla.
> 
> 

* En un área de trabajo de la aplicación, seleccione el botón de puntos suspensivos ( **…** ) en la esquina superior derecha > **Unpublish app** (Cancelar publicación de aplicación).
  
     ![Cancelar publicación de la aplicación](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Esta acción desinstala la aplicación para todos los usuarios para los que se haya publicado, los cuales dejarán de tener acceso a ella. No se elimina el área de trabajo de la aplicación ni su contenido.

## <a name="view-your-published-app"></a>Ver la aplicación publicada

Cuando los consumidores de la aplicación abra la aplicación, ve el panel de navegación que creó, en lugar del panel de navegación izquierdo de Power BI estándar. La navegación de la aplicación enumera los informes y paneles en las secciones que haya definido. También se muestran las páginas individuales de cada informe, sino que simplemente el nombre del informe.

![Aplicación con navegación](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Pasos siguientes
* [Crear área de trabajo de la aplicación](service-create-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](consumer/end-user-apps.md)
* [Conectarse a los servicios con los paquetes de contenido de Power BI](service-connect-to-services.md)
* [Portal de administración de Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
