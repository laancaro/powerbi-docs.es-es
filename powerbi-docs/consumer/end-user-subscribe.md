---
title: Suscripción a informes y paneles en el servicio Power BI
description: Aprenda a suscribirse y a suscribir a otros usuarios a una instantánea de un informe y panel de Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/04/2018
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: a410871263316b4aa811ca39116acf69331f7bc5
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2018
ms.locfileid: "52979453"
---
# <a name="subscribe-to-a-report-or-dashboard-in-power-bi-service"></a>Suscripción a un informe o panel en el servicio Power BI 
Nunca antes ha sido tan fácil mantenerse al día de los paneles e informes más importantes. Suscríbase a las páginas de informes y paneles que más le interesen y Power BI le enviará por correo electrónico una instantánea a la bandeja de entrada. Puede indicarle a Power BI la frecuencia con la que quiere recibir los mensajes de correo electrónico: desde una vez al día hasta una vez por semana. 

El correo electrónico y la instantánea usarán el idioma establecido en la configuración de Power BI (consulte [Idiomas y países o regiones admitidos para Power BI](../supported-languages-countries-regions.md)). Si no se ha definido ningún idioma, Power BI usa el idioma de acuerdo con la configuración regional del explorador actual. Para ver o establecer las preferencias de idioma, seleccione el icono de engranaje ![icono de engranaje](./media/end-user-subscribe/power-bi-settings-icon.png) > **Configuración > General > Idioma**. 

![Menú desplegable de idiomas](./media/end-user-subscribe/power-bi-language.png)

Cuando reciba el correo electrónico, incluirá un vínculo para "ir al informe o panel". En los dispositivos móviles con aplicaciones de Power BI instaladas, al seleccionar este vínculo, se inicia la aplicación (en lugar de la acción predeterminada de abrir el informe o el panel en el sitio web de Power BI).


## <a name="requirements"></a>Requisitos
- **Crear** una suscripción es una característica de Power BI Pro. 
- Puesto que solo se envían mensajes de correo electrónico de suscripción cuando un conjunto de datos subyacente se actualiza o se vuelve a cargar, las suscripciones no funcionan en conjuntos de datos que no se actualicen.

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>Suscribirse a un panel o una página de informe
El proceso de suscripción a un panel es muy similar al de un informe. El mismo botón permite suscribirse a los paneles e informes del servicio Power BI.
 
![Selección del icono de suscripción](./media/end-user-subscribe/power-bi-subscribe-orientation.png).

1. Abra el panel o el informe.
2. En la barra de menús superior, seleccione **Suscribirse** o el icono de sobre ![icono de suscripción](./media/end-user-subscribe/power-bi-icon-envelope.png).
   
   ![Icono de suscripción](./media/end-user-subscribe/power-bi-subscribe-icon.png)

3. Use el control deslizante amarillo para activar y desactivar la suscripción.  Aunque el control deslizante se establezca en desactivado, no se eliminará la suscripción. Para eliminarla, seleccione el icono de papelera.

4. Opcionalmente, agregue los detalles del mensaje de correo electrónico. 

    En las capturas de pantalla siguiente, tenga en cuenta que, cuando se suscribe a un informe, realmente se está suscribiendo a una de sus *páginas*.  Para suscribirse a más de una página de un informe, seleccione **Agregar otra suscripción** y seleccione una página diferente. 
      
   ![Ventana de suscripción](./media/end-user-subscribe/power-bi-emails.png)

5. Seleccione **Guardar y cerrar** para guardar la suscripción. Recibirá un correo electrónico y una instantánea del panel o de la página de informe siempre que se modifique uno de sus conjuntos de datos. Si el panel o el informe se actualiza más de una vez al día, el correo electrónico solo se enviará tras la primera actualización.  
   
   ![Instantánea del panel por correo electrónico](./media/end-user-subscribe/power-bi-dashboard-email-new.jpg)
   
La actualización de la página del informe no actualiza el conjunto de datos. El propietario del conjunto de datos es el único que puede actualizar manualmente un conjunto de datos. Para buscar el nombre de los conjuntos de datos subyacentes, seleccione **Ver relacionados** en la barra de menús superior.
   
![Conjuntos de datos relacionados](./media/end-user-subscribe/power-bi-view-related-screen.png)

## <a name="how-the-email-schedule-is-determined"></a>Cómo se determina la programación de correos electrónicos
En la tabla siguiente se describe la frecuencia con recibirá un correo electrónico. Todo depende del método de conexión del conjunto de datos en el que se basa el panel o el informe (DirectQuery, conexión dinámica, importación a Power BI o archivo de Excel en OneDrive o SharePoint Online) y de las opciones de suscripción disponibles y seleccionadas (diaria, semanal o ninguna).

|  | **DirectQuery** | **Live Connect** | **Actualización programada (importación)** | **Archivo de Excel en OneDrive o SharePoint Online** |
| --- | --- | --- | --- | --- |
| **¿Con qué frecuencia se actualiza el informe o panel?** |Cada 15 minutos |Power BI realiza una comprobación cada 15 minutos y, si el conjunto de datos ha cambiado, el informe se actualiza. |El usuario selecciona la frecuencia: ninguna, diaria o semanal. La frecuencia diaria puede ser de hasta 8 veces al día. La frecuencia semanal es en realidad una programación semanal que crea el usuario y que establece la actualización como mínimo una vez por semana y como máximo cada día. |Una vez cada hora |
| **¿Cuánto control tiene el usuario sobre la programación de correos electrónicos de la suscripción?** |Opciones: diaria o semanal. |Sin opciones: los usuarios reciben un correo electrónico si se actualiza el informe, pero no más de una vez al día. |Si la programación de actualización es diaria, las opciones son diaria y semanal.  Si la programación de actualización es semanal, la única opción es semanal. |Sin opciones: el usuario recibe un correo electrónico cada vez que se actualiza el conjunto de datos, pero no más de una vez al día. |

## <a name="manage-your-subscriptions"></a>Administrar sus suscripciones
Solo usted puede administrar sus suscripciones. Seleccione **Suscribirse** de nuevo y elija **Administrar todas las suscripciones** (vea las capturas de pantalla del paso 4 anterior). 

![Vista de todas las suscripciones en Mi área de trabajo](./media/end-user-subscribe/power-bi-subscriptions.png)

Una suscripción finalizará si expira la licencia de Pro, el propietario elimina el panel o el informe o se elimina la cuenta de usuario utilizada para crear la suscripción.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
* En las suscripciones de correo electrónico de panel, si se ha aplicado la seguridad de nivel de fila (RLS) a algún icono, dicho icono no se mostrará.  En cuanto a las suscripciones de correo electrónico de informe, si el conjunto de datos usa RLS, no podrá crear una suscripción.
* Las suscripciones a una página del informe están asociadas con el nombre de la página del informe. Si se suscribe a una página del informe y cambia su nombre, tendrá que volver a crear la suscripción.
* Es posible que su organización haya configurado ciertos parámetros en Azure Active Directory que podrían limitar la capacidad de utilizar las suscripciones de correo electrónico en Power BI.  Esto incluye, entre otras cosas, la autenticación multifactor o restricciones de intervalo de IP al obtener acceso a los recursos.
* Para las suscripciones de correo electrónico en conjuntos de datos de conexiones dinámicas, solo recibirá correos electrónicos cuando los datos cambien. Por lo tanto, si se produce una actualización pero los datos no cambian, Power BI no le enviará un correo electrónico.
* Las suscripciones de correo electrónico no admiten la mayoría de los [objetos visuales personalizados](../power-bi-custom-visuals.md).  La única excepción son esos objetos visuales personalizados que se han [certificado](../power-bi-custom-visuals-certified.md).  
* En estos momentos, las suscripciones de correo electrónico no admiten los objetos visuales personalizados con la tecnología de R.  
* Si se ha aplicado la seguridad de nivel de fila (RLS) a algún icono de panel, este no se mostrará.
* Las suscripciones de correo electrónico se envían con los estados de segmentación y filtros predeterminados del informe. En el correo electrónico no se mostrarán los cambios en los valores predeterminados que realice tras suscribirse.    
* Para las suscripciones de unos paneles en concreto, no se admiten aún ciertos tipos de iconos.  Entre estos se incluyen: transmisión en secuencias de mosaicos, iconos de vídeo, iconos de contenido web personalizado.     
* Las suscripciones pueden provocar errores en paneles o informes con imágenes muy grandes debido a las limitaciones de tamaño del correo electrónico.    
* Power BI detiene automáticamente la actualización en los conjuntos de datos asociados con los paneles e informes que no se han visitado en más de 2 meses.  Sin embargo, si agrega una suscripción a un panel o informe, no se detendrá incluso si no recibe visitas.    

## <a name="next-steps"></a>Pasos siguientes
* ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)    
* [Leer la entrada del blog](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)

