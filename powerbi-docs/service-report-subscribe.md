---
title: Suscribirse a usted y a otros a informes y paneles - Power BI
description: Obtenga información sobre cómo suscribirse a usted y a otros a una instantánea de una página de informe de Power BI, panel o informe paginado.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: a344e3cdd93fbd237387b61fb4735b41f22625e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65991132"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>Suscripción personal y de otros usuarios a informes y paneles en el servicio Power BI

Puede suscribirse usted y sus compañeros a las páginas de informes, paneles e informes paginados que más le interesen. Power BI envía un correo electrónico una instantánea a la Bandeja de entrada. Puede indicarle a Power BI la frecuencia con la que quiere recibir los mensajes de correo electrónico: una vez al día, una vez por semana o diariamente después de la actualización de los datos iniciales.  Si elige diariamente o semanalmente, puede elegir la hora que le gustaría tener la suscripción que se ejecute.  En resumen, puede establecer hasta 24 suscripciones distintas por día para cada página de informe y panel.

![Instantánea del panel por correo electrónico](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

Solo se pueden crear suscripciones en el servicio Power BI. Recibirá un correo electrónico con una instantánea de la página del informe o panel, con un vínculo para abrir el informe o panel. En los dispositivos móviles con aplicaciones de Power BI instaladas, al hacer clic en este vínculo, se inicia la aplicación de Power BI, en lugar de abrir el informe o el panel en el sitio web de Power BI.

## <a name="requirements"></a>Requisitos

- **Crear** una suscripción es una característica de Power BI Pro.
- No necesita permisos de edición para el contenido (panel o informe) para crear una suscripción personal, pero debe tener permisos de edición para crear una para otro usuario. 
- A partir de enero de 2019, ya no es necesario configurar la actualización del conjunto de datos para ejecutar una suscripción.  Se ejecuta de forma independiente a las actualizaciones programadas que haya configurado.  

## <a name="subscribe-to-a-dashboard-report-page-or-paginated-report"></a>Suscribirse a un panel, una página del informe o un informe paginado

Si se suscribe a un panel, informe, o informe paginado, el proceso es similar. El mismo botón permite suscribirse a los paneles e informes del servicio Power BI.

Suscribirse a informes paginados es un poco diferente. Consulte [suscribirse usted mismo y a otros usuarios a un informe paginado en el servicio Power BI](paginated-reports-subscriptions.md) para obtener más información.
 
![Selección del icono de suscripción](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Abra el panel o el informe.
2. En la barra de menús superior, haga clic en **Suscribirse** o en el icono de sobre ![icono de suscripción](media/service-report-subscribe/power-bi-icon-envelope.png).
   
   ![Icono de suscripción](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. Use el control deslizante amarillo para activar y desactivar la suscripción.  Aunque el control deslizante se establezca en **desactivado**, la suscripción no se elimina. Para eliminarla, seleccione el icono de papelera.

4. El correo electrónico ya está en la bandeja **Suscribirse**. También puede agregar otras direcciones de correo electrónico a la suscripción, pero solo en el mismo dominio. Si el informe o el panel está hospedado en la [capacidad Premium](service-premium-what-is.md), puede suscribir otras direcciones de correo electrónico y alias de grupo. Si el informe o el panel no está hospedado en la capacidad Premium, puede suscribir a otros usuarios, pero también deberán tener licencias de Power BI Pro. Para obtener más detalles, vea [Consideraciones y solución de problemas](#considerations-and-troubleshooting). 

5. Rellene el **asunto** del correo electrónico y los detalles del **mensaje**. 

5. Seleccione una **Frecuencia** para la suscripción: **Diaria**,  **Semanal** o **Tras la actualización de los datos (una vez al día)** .  Para recibir el correo electrónico de suscripción solo en días concretos, seleccione **Semanal** y elija los días en los que quiera recibirlo.  Por ejemplo, si le gustaría recibir el correo electrónico de suscripción solo los días laborables, seleccione **Semanal** y desactive las casillas para **Sáb.** y **Dom**.  

6. Si elige **Diaria** o **Semanal**, también puede elegir una **Hora programada** para la suscripción.  Puede hacer que se ejecute a la hora, o bien pasados 15, 30 o 45 minutos.  Seleccione por la mañana (a. m.) o por la tarde/noche (p. m.). También puede especificar la zona horaria.

7. De forma predeterminada, la fecha de inicio para la suscripción es la fecha en la que la ha creado. Tiene la opción de seleccionar una fecha de finalización. Si no establece una fecha de finalización, automáticamente será un año después de la fecha de inicio. Puede cambiarla a cualquier fecha en el futuro (hasta el año 9999) en cualquier momento antes de que finalice la suscripción. Cuando una suscripción alcanza una fecha de finalización, se detiene hasta que vuelva a habilitarla. Recibirá notificaciones antes de la fecha de finalización programada para preguntarle si quiere ampliarla.    

    En la captura de pantalla siguiente, tenga en cuenta que, cuando se suscribe a un informe, realmente se está suscribiendo a una de sus *páginas*.  Para suscribirse a más de una página de un informe, seleccione **Agregar otra suscripción** y seleccione una página diferente. 
      
   ![Panel de suscripción](media/service-report-subscribe/power-bi-subscribe-pane.png)  

7. Haga clic en **Guardar y cerrar**. Los que se hayan suscrito reciben un correo electrónico y una instantánea de la página de panel o informe para la frecuencia y la hora que se hayan seleccionado. En total, puede crear hasta 24 suscripciones por informe o panel, y pueden proporcionar destinatarios, horas y frecuencias únicos para cada suscripción.  Todas las suscripciones establecidas en **Tras la actualización de los datos** para el informe o panel solo enviarán un correo electrónico después de la primera actualización programada.   
      
   > [!TIP]
   > ¿Quiere enviar el correo electrónico desde una suscripción al instante o a petición en cualquier momento? Haga clic en **Ejecutar ahora** para las suscripciones del panel o informe que quiera enviar. Verá una notificación en la que se indica que hay un correo electrónico en camino para todos los usuarios de esa suscripción concreta.  Puede hacerlo con tanta frecuencia como sea necesario. No cuenta para el límite de 24 ejecuciones de suscripción programadas diariamente por informe o panel. No se desencadena una actualización de datos del conjunto de datos subyacente. 
   > 
   > 
   
## <a name="email-languages"></a>Idiomas de correo electrónico

En el correo electrónico y la instantánea se usa el idioma establecido en la configuración de Power BI (vea [Idiomas y países o regiones admitidos para Power BI](supported-languages-countries-regions.md)). Si no se ha definido ningún idioma, Power BI usa el idioma de acuerdo con la configuración regional del explorador actual. Para ver o establecer las preferencias de idioma, seleccione el icono de engranaje ![icono de engranaje](media/service-report-subscribe/power-bi-settings-icon.png) > **Configuración > General > Idioma**. 

![Menú desplegable de idiomas](media/service-report-subscribe/power-bi-language.png)

## <a name="manage-your-subscriptions"></a>Administrar sus suscripciones
Solo la persona que haya creado la suscripción podrá administrarla.  Hay dos rutas de acceso a la pantalla en la que se administran las suscripciones.  El primer paso es seleccionar **Administrar todas las suscripciones** en el cuadro de diálogo **Subscribirse a correos electrónicos** (vea el paso 4 anterior). La segunda es seleccionar el icono de engranaje de Power BI ![icono de engranaje](media/service-report-subscribe/power-bi-settings-icon.png) en la barra de menús superior y elegir **Configuración**.

![Selección de Configuración](media/service-report-subscribe/power-bi-subscribe-settings.png)

Las suscripciones concretas que se muestran dependen del área de trabajo que está activa en ese momento.  Para ver a la vez todas las suscripciones de todas las áreas de trabajo, asegúrese de que **Mi área de trabajo** está activa. Para entender las áreas de trabajo, consulte [Áreas de trabajo de Power BI](service-create-workspaces.md).

![Vista de todas las suscripciones en Mi área de trabajo](media/service-report-subscribe/power-bi-subscriptions.png)

Una suscripción finaliza si expira la licencia de Pro, el propietario elimina el panel o el informe, o bien se elimina la cuenta de usuario que se ha usado para crear la suscripción.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

* Es posible que los paneles con más de 25 iconos anclados, o bien con 4 páginas de informes activos ancladas, no se representen totalmente en los correos electrónicos de la suscripción enviados a los usuarios.  No se bloquean las suscripciones a los paneles a través de estos número de mosaicos. Sin embargo, se consideran no compatible si tiene problemas. Considere la posibilidad de modificarlas en consecuencia para que se encuentren dentro de un intervalo admitido.
* Al configurar las suscripciones de correo electrónico, tenga en cuenta que hay un retraso entre cuando se inicia el trabajo de suscripción y la hora exacta que se envía el correo electrónico.  Para minimizar el retraso entre los dos, configure una hora diferente para la actualización de datos programada que cuando la suscripción de correo electrónico está programada para ejecutarse.
* Para suscripciones de correo electrónico del panel, si dispone de los iconos de seguridad de nivel de fila (RLS) aplicada, no muestran los iconos.  
* Para las suscripciones de correo electrónico de informe, si el conjunto de datos usa RLS, puede crear una suscripción para usted mismo. No se puede suscribir a otros a un informe con la seguridad de nivel de fila (RLS) aplicada.
* Las suscripciones a una página del informe están asociadas con el nombre de la página del informe. Si se suscribe a una página del informe y después cambia el nombre, tendrá que volver a crear la suscripción.
* Su organización puede configurar ciertos parámetros en Azure Active Directory que limitan la capacidad de usar las suscripciones de correo electrónico en Power BI.  Estas limitaciones incluyen, entre otras, la autenticación multifactor o restricciones de intervalo de IP al acceder a los recursos.
* En estos momentos, al suscribir a otros usuarios, no se admiten las suscripciones de correo electrónico relativas a informes o paneles que usen conjuntos de datos con conexión dinámica.
* Las suscripciones de correo electrónico no admiten la mayoría de los [objetos visuales personalizados](power-bi-custom-visuals.md).  La única excepción son esos objetos visuales personalizados que se han [certificado](power-bi-custom-visuals-certified.md).  
* En la actualidad, las suscripciones de correo electrónico no admiten los objetos visuales personalizados con la tecnología de R.  
* Las suscripciones de correo electrónico se envían con los estados de segmentación y filtros predeterminados del informe. En el correo electrónico no se muestran los cambios en los valores predeterminados que realice tras suscribirse.    
* Para las suscripciones de paneles en concreto, todavía no se admiten ciertos tipos de iconos.  Entre estos se incluyen: transmisión en secuencias de mosaicos, iconos de vídeo, iconos de contenido web personalizado.     
* Si comparte un panel con un compañero de trabajo fuera de su inquilino, tampoco puede crear una suscripción para él. Por tanto, si es aaron@xyz.com, podrá compartir con anyone@ABC.com, pero todavía no podrá suscribir a anyone@ABC.com, y ese usuario no podrá suscribirse al contenido compartido.      
* Power BI detiene de forma automática la actualización en los conjuntos de datos asociados con los paneles e informes que no se han visitado en más de dos meses.  Pero si agrega una suscripción a un panel o informe, no se detiene incluso si no recibe visitas.    
* Si no recibe los mensajes de correo electrónico de suscripción, asegúrese de que el nombre principal de usuario (UPN) puede recibirlos. [El equipo de Power BI está trabajando para reducir este requisito](https://community.powerbi.com/t5/Issues/No-Mail-from-Cloud-Service/idc-p/205918#M10163). Esté atento a las novedades. 
* Si el panel o el informe están en la capacidad Premium, puede usar el alias de correo electrónico del grupo para las suscripciones en lugar de suscribir las direcciones de correo electrónico de sus compañeros de trabajo de una en una. Los alias se basan en el directorio actual de Active Directory. 

## <a name="next-steps"></a>Pasos siguientes

- [Suscribirse a usted y otros usuarios a un informe paginado en el servicio Power BI](paginated-reports-subscriptions.md)
- ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)    
- [Leer la entrada del blog](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)
