---
title: Publicación de una aplicación en Power BI
description: Obtenga información sobre cómo publicar las aplicaciones nuevas, que son colecciones de paneles e informes con navegación integrada.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 67678a150b4fce802bef2b287211cf438b832e82
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66459573"
---
# <a name="publish-an-app-in-power-bi"></a>Publicación de una aplicación en Power BI

En Power BI, puede crear contenido empaquetado oficial y luego distribuirlo a un público amplio como una *aplicación*. Cree aplicaciones en *áreas de trabajo de la aplicación*, donde puede colaborar en contenido de Power BI con sus compañeros. Después, puede publicar las aplicaciones terminadas en grandes grupos de usuarios de su organización. 

![Aplicaciones de Power BI](media/service-create-distribute-apps/power-bi-new-apps.png)

Los usuarios empresariales suelen necesitar varios paneles e informes de Power BI para hacer funcionar sus negocios. Con las aplicaciones de Power BI, puede crear colecciones de paneles e informes y publicar estas aplicaciones para toda la organización o para grupos o usuarios específicos. Los creadores de informes o los administradores verán lo fácil que es administrar permisos sobre estas colecciones con las aplicaciones.

Los usuarios empresariales obtienen las aplicaciones de varias maneras diferentes:

- Pueden buscar e instalar la aplicación desde Microsoft AppSource.
- Les puede enviar un vínculo directo.
- Si el administrador de Power BI le concede permiso, puede instalarla automáticamente en las cuentas de Power BI de los compañeros de trabajo.

Puede crear la aplicación con su propia navegación integrada, para que los usuarios puedan desplazarse con facilidad por el contenido. No pueden modificar el contenido de la aplicación. Pueden interactuar con ella en el servicio Power BI o en una de las aplicaciones móviles: pueden filtrar, resaltar y ordenar los datos por sí mismos. Obtienen las actualizaciones automáticamente y se puede controlar la frecuencia con la que se actualizan los datos. Obtenga información sobre la [experiencia de aplicación para usuarios empresariales](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licencias para aplicaciones
Para crear o actualizar una aplicación necesita una licencia de Power BI Pro. Los *consumidores* de la aplicación tienen dos opciones.

* Opción 1: todos los usuarios empresariales necesitan licencias de **Power BI Pro** para ver la aplicación. 
* Opción 2: si el área de trabajo de la aplicación reside en una capacidad de Power BI Premium, los usuarios de la organización con la versión gratuita pueden ver el contenido de la aplicación. Para más información, lea [What is Power BI Premium?](service-premium.md) (¿Qué es Power BI Premium?)

## <a name="publish-your-app"></a>Publicar su aplicación
Cuando los paneles e informes en el área de trabajo estén listos, elija cuáles quiere publicar y luego publíquelos como una aplicación. 

1. En la vista de lista del área de trabajo, decida qué paneles e informes quiere **incluir en la aplicación**.

     ![Seleccionar el panel que va a publicar](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Si decide no incluir un informe que tiene un panel relacionado, verá una advertencia junto al informe. Todavía puede publicar la aplicación, pero el panel relacionado no tendrá los iconos de ese informe.

     ![Advertencia sobre un panel relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Seleccione el botón **Publicar aplicación** de la esquina superior derecha para iniciar el proceso de creación y publicación de una aplicación desde el área de trabajo.
   
     ![Publicar aplicación](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. En **Configuración**, rellene el nombre y la descripción para ayudar a los usuarios a encontrar la aplicación. Puede establecer un color de tema para personalizarla. También puede agregar un vínculo a un sitio de soporte técnico.
   
     ![Compilación de la aplicación](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. En **Navegación**, seleccione el contenido que se va a publicar como parte de la aplicación. Después, agregue navegación de la aplicación, para organizar el contenido en secciones. Vea [Diseño de la experiencia de navegación de la aplicación](#design-the-navigation-experience-for-your-app) en este artículo para obtener más información.
   
     ![Navegación de la aplicación](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. En **Permiso**, decida quién tiene acceso a la aplicación y qué puede hacer con ella. 
    - En [Áreas de trabajo clásicas](service-create-workspaces.md): todas las personas de la organización, usuarios específicos o grupos de seguridad de Azure Active Directory (AAD).
    - En las [áreas de trabajo de la nueva experiencia](service-create-the-new-workspaces.md): usuarios específicos, grupos de seguridad de AAD y listas de distribución, y grupos de Office 365.

6. Puede instalar la aplicación de forma automática para los destinatarios, si el administrador de Power BI ha habilitado esta opción automáticamente en el Portal de administración de Power BI. Obtenga más información sobre [la instalación automática de una aplicación](#automatically-install-apps-for-end-users) en este artículo.

     ![Permisos de aplicación](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Al seleccionar **Publicar aplicación**, verá un mensaje en el que se confirma que está lista para publicarse. En el cuadro de diálogo **Compartir esta aplicación**, puede copiar la dirección URL que es un vínculo directo a esta aplicación.
   
     ![Finalización de la aplicación](media/service-create-distribute-apps/power-bi-apps-success.png)

Puede enviar ese vínculo directo a los usuarios con los que la ha compartido, o bien pueden encontrar la aplicación en la pestaña Aplicaciones, en **Descargar y explorar más aplicaciones de AppSource**. Obtenga información sobre la [experiencia de aplicación para usuarios empresariales](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Cambiar la aplicación publicada
Después de publicar la aplicación, puede que desee cambiarla o actualizarla. Es fácil actualizarla si es un administrador o miembro de la nueva área de trabajo de la aplicación. 

1. Abra el área de trabajo de aplicación que corresponde a la aplicación. 
   
     ![Abrir área de trabajo](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Realice los cambios que quiera en los paneles o informes.
 
     El área de trabajo de aplicación es el área de ensayo, por lo que los cambios no se envían en directo a la aplicación hasta que la vuelva a publicar. Esto le permite realizar cambios sin que ello afecte a las aplicaciones publicadas.  
 
    > [!IMPORTANT]
    > Si quita un informe y actualiza la aplicación, incluso si vuelve a agregar el informe a la aplicación, los consumidores de la aplicación perderán todas las personalizaciones, como marcadores, comentarios, etc.  
 
3. Vuelva a la lista de contenidos del área de trabajo de la aplicación y seleccione **Actualizar aplicación** en la esquina superior derecha.
   
1. Si es necesario, actualice **Instalación**, **Navegación** y **Permisos**, y después seleccione **Actualizar aplicación**.
   
Las personas para las que ha publicado la aplicación ven automáticamente la versión actualizada de la aplicación. 

## <a name="design-the-navigation-experience-for-your-app"></a>Diseño de la experiencia de navegación de la aplicación
La opción **Nuevo generador de navegación** permite crear una navegación personalizada para la aplicación. La navegación personalizada hace que la búsqueda y el uso del contenido de la aplicación resulten más fáciles para los usuarios. En las aplicaciones existentes esta opción está desactivada y en las nuevas está activada de forma predeterminada.

Cuando la opción está desactivada, puede seleccionar que la **Página de aterrizaje de la aplicación** sea **Contenido específico** (por ejemplo, un panel o un informe), o bien seleccionar **Ninguno** para mostrar al usuario una lista de contenido básico.

Al activar **Nuevo generador de navegación**, puede diseñar una navegación personalizada. De forma predeterminada, todos los paneles, informes y libros de Excel que se incluyen en la aplicación se muestran como una lista plana. 

![Navegación de la aplicación](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Puede personalizar aún más la navegación de aplicación si:
* Reordena los elementos mediante las flechas Arriba y Abajo. 
* Cambia el nombre de los elementos en **Detalles del informe**, **Detalles del panel** y **Detalles del libro**.
* Oculta elementos concretos en el panel de navegación.
* Usa la opción **Nueva** para agregar **secciones** para agrupar contenido relacionado.
* Usa la opción **Nuevo** para agregar un **vínculo** a un recurso externo en el panel de navegación de la izquierda. 

Cuando se agrega un **vínculo**, en **Detalles del vínculo** puede elegir dónde se abre el vínculo. De forma predeterminada los vínculos se abren en la **Pestaña actual**, pero puede seleccionar **Nueva pestaña** o **Área de contenido**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Consideraciones sobre el uso de la nueva opción Generador de navegación
Estos son aspectos generales que deben tenerse en cuenta al usar el nuevo Generador de navegación:
* Las páginas del informe se muestran en el área de navegación de la aplicación como una sección expandible.
* Si desactiva el nuevo generador de navegación y después publica o actualiza la aplicación, se perderán las personalizaciones que haya realizado. Por ejemplo, se perderán las secciones, la ordenación, los vínculos y los nombres personalizados para los elementos de navegación.

Al agregar vínculos a la navegación de la aplicación y seleccionar la opción Área de contenido:
* Asegúrese de que el vínculo se puede insertar. Algunos servicios bloquean la inserción de su contenido en sitios de terceros como Power BI.
* No se admite la inserción de contenido del servicio Power BI, como informes o paneles en otras áreas de trabajo. 
* Inserte contenido de Power BI Report Server a través de su dirección URL de inserción de contenido nativa desde una implementación local. Siga los pasos descritos en [Creación de la dirección URL de Power BI Report Server](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) para obtener la dirección URL. Tenga en cuenta que se aplican las reglas de autenticación convencionales, de modo que para ver el contenido se necesita una conexión VPN al servidor local. 
* Se muestra una advertencia de seguridad en la parte superior del contenido insertado para indicar que no está en Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Instalar aplicaciones para usuarios finales de forma automática
Si un administrador le concede permisos, puede instalar aplicaciones de forma automática, para *insertarlas* en los usuarios finales. Esta funcionalidad de inserción facilita la distribución de las aplicaciones correctas a los usuarios o grupos adecuados. La aplicación aparecerá de forma automática en la lista de contenido Aplicaciones de los usuarios finales. No tendrán que buscarla en Microsoft AppSource ni seguir un vínculo de instalación. Vea cómo los administradores habilitan [la inserción de aplicaciones en los usuarios finales](service-admin-portal.md#push-apps-to-end-users) en el artículo del portal de administración de Power BI.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Procedimientos para insertar una aplicación de forma automática en los usuarios finales
Una vez que el administrador le haya asignado los permisos, tiene una nueva opción para **instalar la aplicación automáticamente**. Si activa la casilla y selecciona **Publicar aplicación** (o **Actualizar aplicación**), la aplicación se inserta en todos los usuarios o grupos definidos en la sección **Permisos** de la aplicación, en la pestaña **Acceso**.

![Habilitar la inserción de aplicaciones](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Cómo obtienen los usuarios las aplicaciones que les inserta
Después de insertar una aplicación, se muestra de forma automática en la lista Aplicaciones. De esta forma, puede ajustar las aplicaciones que roles de usuario o de trabajo específicos de la organización necesitan tener a su alcance.

![Habilitar la inserción de aplicaciones](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Consideraciones para instalar automáticamente las aplicaciones
Estos son aspectos que debe tener en cuenta al publicar aplicaciones para los usuarios finales:

* La instalación de una aplicación de forma automática para los usuarios puede llevar tiempo. La mayoría de las aplicaciones se instalan inmediatamente para los usuarios, pero la inserción puede llevar tiempo.  Depende del número de elementos de la aplicación y del número de usuarios con acceso. Se recomienda publicar aplicaciones durante las horas sin actividad con bastante tiempo antes de que los usuarios las necesiten. Compruebe con varios usuarios antes de enviar una comunicación general sobre la disponibilidad de las aplicaciones.

* Actualice el explorador. Para poder ver la aplicación insertada en la lista de aplicaciones, es posible que el usuario necesite actualizar, o cerrar y volver a abrir, el explorador.

* Si los usuarios no ven inmediatamente la aplicación en la lista Aplicaciones, tendrán que actualizar o cerrar y volver a abrir el explorador.

* Intente no abrumar a los usuarios. Tenga cuidado de no insertar demasiadas aplicaciones para que los usuarios perciban que las aplicaciones preinstaladas son útiles. Es mejor controlar quién puede insertar aplicaciones para los usuarios finales a fin de coordinar la programación. Establezca un punto de contacto para insertar las aplicaciones de la organización para los usuarios finales.

* A los usuarios invitados que no hayan aceptado una invitación no se les instalarán las aplicaciones de forma automática.  

## <a name="unpublish-an-app"></a>Cancelar la publicación de una aplicación
Cualquier miembro de un área de trabajo de la aplicación puede cancelar la publicación de la aplicación.

>[!IMPORTANT]
>Cuando cancela la publicación de una aplicación, los usuarios de la aplicación pierden sus personalizaciones. Pierden todos los marcadores personales, comentarios o suscripciones asociados al contenido de la aplicación. Cancele la publicación de una aplicación solo si es necesario quitarla.
> 
> 

* En un área de trabajo de la aplicación, seleccione el botón de puntos suspensivos ( **…** ) en la esquina superior derecha > **Unpublish app** (Cancelar publicación de aplicación).
  
     ![Cancelar publicación de la aplicación](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Esta acción desinstala la aplicación para todos los usuarios para los que se haya publicado, los cuales dejarán de tener acceso a ella. No se elimina el área de trabajo de la aplicación ni su contenido.

## <a name="view-your-published-app"></a>Visualización de la aplicación publicada

Cuando los consumidores de la aplicación la abran, verán el panel de navegación que ha creado, en lugar del panel de navegación izquierdo estándar de Power BI. La navegación de la aplicación enumera los informes y paneles en las secciones que haya definido. También se muestran las páginas individuales de cada informe, no solo el nombre del informe.

![Aplicación con navegación](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Pasos siguientes
* [Crear área de trabajo de la aplicación](service-create-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](consumer/end-user-apps.md)
* [Conectarse a los servicios con los paquetes de contenido de Power BI](service-connect-to-services.md)
* [Portal de administración de Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
