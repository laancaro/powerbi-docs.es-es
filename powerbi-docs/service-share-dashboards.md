---
title: Uso compartido de informes y paneles de Power BI con compañeros y otros usuarios
description: Cómo compartir paneles e informes de Power BI con compañeros dentro y fuera de la organización, y lo que necesita saber sobre el uso compartido.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d82b03325991276924f25da5511baadfe53127e1
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2019
ms.locfileid: "68522999"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Uso compartido de informes y paneles de Power BI con compañeros y otros usuarios
*Compartir* es una buena manera de permitir que otros usuarios tengan acceso a sus paneles e informes. Power BI ofrece también [varias maneras de colaborar y distribuir los paneles e informes](service-how-to-collaborate-distribute-dashboards-reports.md).

![Icono de uso compartido de una lista de paneles favoritos](media/service-share-dashboards/power-bi-share-dash-report-favorites.png)

Con el uso compartido, si comparte contenido dentro o fuera de su organización, se necesita una [licencia de Power BI Pro](service-features-license-type.md). Sus destinatarios también necesitan licencias de Power BI Pro, excepto si el contenido está en una [función premium](service-premium-what-is.md). 

Puede compartir paneles e informes de la mayoría de las ubicaciones del servicio de Power BI: Favoritos, Recientes, Compartidos conmigo (si el propietario lo permite), Mi área de trabajo u otras áreas de trabajo. Cuando comparte un panel o un informe, los usuarios con quienes los comparte pueden verlos e interactuar con ellos, pero no pueden modificarlos. Ellos ven los mismos datos que usted ve en el panel o informe, a menos que se aplique la [seguridad de nivel de fila (RLS)](service-admin-rls.md). Los compañeros con los que los comparte también pueden compartirlos a su vez con sus propios compañeros, si tienen permiso para hacerlo. Los usuarios que no pertenezcan a su organización pueden ver el panel o informe, así como interactuar con estos, pero no podrán compartirlos. 

También puede [compartir un panel desde cualquiera de las aplicaciones móviles de Power BI](consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md). Pero no puede compartir paneles desde Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Vídeo: Compartir un panel
Vea cómo Amanda comparte el panel con sus compañeros dentro y fuera de la compañía. Luego, siga las instrucciones paso a paso que aparecen debajo del vídeo para intentarlo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Uso compartido de un panel o informe

1. En una lista de paneles o informes, o en un panel o informe abierto, seleccione **Compartir** ![icono de Compartir](media/service-share-dashboards/power-bi-share-icon.png).

2. En el cuadro superior, escriba las direcciones de correo electrónico completas de las personas, los grupos de distribución o los grupos de seguridad. No se puede compartir con listas de distribución dinámicas. 
   
   Puede compartir contenido con gente cuya dirección no pertenezca a su organización, pero recibirá una advertencia al hacerlo.
   
   ![Advertencia sobre el uso compartido externo](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >El cuadro de entrada admite como máximo 100 usuarios o grupos. Si necesita compartir con un gran número de usuarios, puede crear el panel en un área de trabajo y [distribuirlo como una aplicación](service-create-distribute-apps.md).
   > 
   > 


3. Agregue un mensaje si lo desea. Es opcional.
4. Para permitir que sus compañeros de trabajo compartan el contenido con otros, active la casilla **Permitir que los destinatarios compartan su panel (o informe)** .
   
   La acción de permitir que otras personas compartan se denomina *volver a compartir*. Si les deja, pueden volver a compartir desde el servicio Power BI y las aplicaciones móviles, o reenviar la invitación de correo electrónico a otras personas de su organización. La invitación expira transcurrido un mes. Los usuarios ajenos a su organización no pueden volver a compartir contenido. Como propietario del contenido, puede desactivar la posibilidad de volver a compartir o revocar usos compartidos de forma individual. Vea [Dejar de compartir o impedir que otros compartan](#stop-sharing-or-stop-others-from-sharing).

5. Seleccione **Compartir.**
   
   ![Selección del botón Compartir](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI envía una invitación por correo electrónico a cada usuario, pero no a los grupos, con un vínculo al contenido compartido. Verá una notificación de **correcto**. 
   
   Cuando los destinatarios de su organización hacen clic en el vínculo, Power BI agrega el panel o informe a su página de lista **Compartido conmigo**. Estos pueden seleccionar su nombre para ver el contenido que ha compartido. 
   
   ![Página de lista Compartido conmigo](media/service-share-dashboards/power-bi-shared-with-me-dashboards-reports.png)
   
   Cuando los destinatarios externos a su organización hacen clic en el vínculo, ven el panel o informe, pero no en el portal habitual de Power BI. Para obtener más información, vea [Uso compartido de un panel o informe con contactos externos a la organización](#share-a-dashboard-or-report-with-people-outside-your-organization).

## <a name="who-has-access-to-a-dashboard-or-report-you-shared"></a>¿Quién tiene acceso a un panel o informe que ha compartido?
A veces, tendrá que ver las personas con las que ha compartido y ver con quiénes lo han compartido a su vez esas personas:

1. En la lista de paneles e informes, o en el panel o informe propiamente dicho, seleccione **Compartir** ![Icono Compartir](media/service-share-dashboards/power-bi-share-icon.png). 
2. En el cuadro de diálogo **Compartir panel** o **Compartir informe**, seleccione **Acceso**.
   
    ![Cuadro de diálogo Compartir panel, pestaña Acceso](media/service-share-dashboards/power-bi-share-dialog-access.png)

    Los usuarios ajenos a su organización se muestran como **Invitado**.

## <a name="stop-sharing-or-stop-others-from-sharing"></a>Dejar de compartir o impedir que otros compartan
Solo el propietario del panel o informe puede activar y desactivar Volver a compartir.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Si aún no ha enviado la invitación para compartir
* Desactive la casilla **Permitir que los destinatarios compartan su panel (o informe)** en la parte inferior de la invitación antes de enviarla.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Si ya ha compartido el panel o informe
1. En la lista de paneles e informes, o en el panel o informe propiamente dicho, seleccione **Compartir** ![Icono Compartir](media/service-share-dashboards/power-bi-share-icon.png). 
2. En el cuadro de diálogo **Compartir panel** o **Compartir informe**, seleccione **Acceso**.
   
    ![Cuadro de diálogo Compartir panel, pestaña Acceso](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Seleccione los puntos suspensivos ( **...** ) junto a **Leer y volver a compartir** y seleccione:
   
   ![Puntos suspensivos de Leer y volver a compartir](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Lectura** para impedir que esa persona comparta con nadie más.
   * **Quitar acceso** para impedir que esa persona vea el contenido compartido.

4. En el cuadro de diálogo **Eliminar acceso**, decida si quiera quitar también el acceso al contenido relacionado, como informes y conjuntos de datos. Si quita elementos con un icono de advertencia ![icono de advertencia de Power BI](media/service-share-dashboards/power-bi-warning-icon.png), le recomendamos que quite también el contenido relacionado, ya que no se mostrará correctamente.

    ![Cuadro de diálogo de advertencia de uso compartido de Power BI](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="share-a-dashboard-or-report-with-people-outside-your-organization"></a>Uso compartido de un panel o informe con personas fuera de la organización
Al compartir con contactos externos a la organización, estos reciben un correo electrónico con un vínculo al panel o informe compartido, y tienen que iniciar sesión en Power BI para verlo. Si no tienen una licencia de Power BI Pro, puede registrarse para obtener una licencia después de hacer clic en el vínculo.

Después de iniciar sesión, verán el panel o informe compartido en su propia ventana del explorador, no en el portal de Power BI habitual. Para acceder más tarde a este panel o informe, necesitan agregar el vínculo a sus marcadores.

No pueden editar el contenido del panel ni del informe. Aunque pueden interactuar con los gráficos y cambiar filtros o segmentaciones, no pueden guardar los cambios. 

Solo los destinatarios directos pueden ver el panel o informe compartido. Por ejemplo, si se ha enviado el mensaje de correo electrónico a Vicki@contoso.com, solo Vicki puede ver el panel. Nadie más puede ver el panel, incluso aunque tengan el vínculo. Vicki tiene que usar la misma dirección de correo electrónico para acceder; si alguien se registra con cualquier otra dirección de correo electrónico, no tendrá acceso al panel.

Los usuarios ajenos a su organización no pueden ver ningún dato si se implementó seguridad de nivel de fila o de rol en los modelos tabulares de Analysis Services locales.

Si envía un vínculo desde una aplicación móvil de Power BI a contactos externos a su organización, al hacer clic en el vínculo, se abrirá el panel en el explorador, no en la aplicación móvil de Power BI.

Si [permite a los usuarios invitados externos editar y administrar el contenido de la organización](service-admin-portal.md#export-and-sharing-settings), la experiencia de solo consumo predeterminada no será válida en su caso. [Más información](service-admin-azure-ad-b2b.md).

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones
Aspectos que hay que tener en cuenta sobre el uso compartido de paneles e informes:

* Por lo general, usted y sus compañeros ven los mismos datos en el panel o informe. Por lo tanto, si tiene permisos para ver más datos que ellos, podrán ver todos sus datos en el panel o informe. Sin embargo, si se aplica la [seguridad de nivel de fila (RLS)](service-admin-rls.md) al conjunto de datos subyacente a un panel o informe, se usan las credenciales de cada persona para determinar los datos a los que puede tener acceso.
* Todos los usuarios con quienes comparta el panel podrán visualizarlo e interactuar con los informes relacionados en la [vista de lectura](consumer/end-user-reading-view.md#reading-view). No pueden crear informes ni guardar cambios en los informes existentes.
* Aunque ningún usuario puede ver o descargar el conjunto de datos, pueden acceder directamente al conjunto de datos mediante la característica Analizar en Excel. Un administrador puede restringir la capacidad de usar Analizar en Excel para todos los miembros de un grupo. Sin embargo, la restricción es para todos los usuarios de ese grupo para cada área de trabajo a la que pertenece el grupo.
* Todo el mundo puede [actualizar los datos](refresh-data.md) manualmente.
* Si usa Office 365 para el correo electrónico, puede compartir datos con los miembros de un grupo de distribución. Para ello, escriba la dirección de correo electrónico asociada al grupo de distribución.
* Los compañeros de trabajo que tengan el mismo dominio de correo electrónico y aquellos cuyo dominio sea distinto, pero esté registrado en el mismo inquilino, pueden compartir el panel con otros. Por ejemplo, si los dominios contoso.com y contoso2.com están registrados en el mismo inquilino y su dirección de correo electrónico es konrads@contoso.com, tanto ravali@contoso.com como gustav@contoso2.com podrán compartir, siempre que les haya concedido permiso para hacerlo.
* Si sus compañeros de trabajo ya tienen acceso a un panel o informe específico, puede enviar un vínculo directo con solo copiar la dirección URL cuando se encuentre dentro del panel o informe. Por ejemplo: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* Del mismo modo, si sus compañeros de trabajo ya tienen acceso a un panel específico, puede [enviar un vínculo directo al informe subyacente](service-share-reports.md). 
* Puede compartir, como máximo, con 100 usuarios o grupos en una sola acción de uso compartido. Sin embargo, puede conceder acceso a un elemento a más de 500 usuarios. Para hacerlo, puede compartir varias veces si especifica los usuarios de forma individual, o bien si comparte con un grupo de usuarios que contenga todos los usuarios.

## <a name="troubleshoot-sharing"></a>Solución de problemas de uso compartido

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Los destinatarios del panel ven un icono de bloqueo en un icono o un mensaje "Permisos requeridos"

Las personas con las que comparte puede que vean un icono de bloqueo en un panel o un mensaje "Permisos requeridos" al intentar ver un informe.

![Icono de bloqueo de Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

Si es así, tiene que conceder permiso al conjunto de datos subyacente:

1. Vaya a la pestaña **Conjuntos de datos** en la lista de contenido.

1. Seleccione el símbolo de puntos suspensivos ( **…** ) junto al conjunto de datos y, después, haga clic en **Administrar permisos**.

    ![Administrar permisos](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Seleccione **Agregar usuario**.

    ![Seleccionar Agregar usuario](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Escriba las direcciones de correo electrónico completas de las personas, los grupos de distribución o los grupos de seguridad. No se puede compartir con listas de distribución dinámicas.

    ![Agregar direcciones de correo electrónico](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Seleccione **Agregar**.

### <a name="i-cant-share-a-dashboard-or-report"></a>No se puede compartir un panel o informe

Para compartir un panel o informe, necesita permiso para volver a compartir el contenido subyacente (es decir, los informes y conjuntos de datos relacionados). Si ve un mensaje que indica que no se puede compartir, solicite al autor del informe que le conceda permisos para volver a compartir los informes y los conjuntos de datos.

![Mensaje "No se puede compartir"](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Pasos siguientes
* ¿Quiere hacer algún comentario? Vaya al [sitio de la comunidad de Power BI](https://community.powerbi.com/) para efectuar sus sugerencias.
* [¿Cómo debo compartir paneles e informes y colaborar en ellos?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartir un informe de Power BI filtrado](service-share-reports.md).
* ¿Tiene alguna pregunta? [Pruebe la comunidad de Power BI](http://community.powerbi.com/).

