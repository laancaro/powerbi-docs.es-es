---
title: 'Tutorial: Establecer alertas de datos en los paneles del servicio Power BI'
description: En este tutorial, aprenderá a establecer alertas que le envíen notificaciones cada vez que los datos de sus paneles cambien más allá de los límites establecidos en el servicio Microsoft Power BI.
author: mihart
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 5f4dc1d1f3e707a59ef81e63be42714c499d050f
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496531"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Tutorial: Establecer alertas en paneles de Power BI

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Establezca alertas que le envíen notificaciones cada vez que los datos de sus paneles cambien por encima o por debajo de los límites establecidos. Las alertas funcionan en medidores, KPI y tarjetas. Esta característica sigue evolucionando, así que vea la sección [Sugerencias y solución de problemas](#tips-and-troubleshooting) más adelante.

![icono, tarjeta, KPI](media/end-user-alerts/card-gauge-kpi.png)

Nadie más podrá ver las alertas que establezca, aunque comparta el panel. Las alertas de datos están completamente sincronizadas en las plataformas; establezca y vea las alertas de datos [en las aplicaciones móviles de Power BI](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) y en el servicio Power BI. 

> [!WARNING]
> Estas alertas proporcionan información sobre los datos. Si consulta sus datos de Power BI en un dispositivo móvil y le roban ese dispositivo, se recomienda usar el servicio Power BI para desactivar todas las alertas.
> 

En este artículo se tratan los temas siguientes:
> [!div class="checklist"]
> * ¿Quién puede establecer alertas?
> * ¿Qué objetos visuales admiten alertas?
> * ¿Quién puede ver mis alertas?
> * ¿Las alertas funcionan en Power BI Desktop y en la versión para móviles?
> * Cómo crear una alerta
> * ¿Dónde recibiré mis alertas?

Si no está registrado en Power BI, [regístrese para obtener una evaluación gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de empezar.

En este ejemplo se usa un icono de tarjeta de panel de la aplicación de ejemplo Sales & Marketing. Esta aplicación está disponible en [Microsoft AppSource](https://appsource.microsoft.com). Para averiguar cómo obtener la aplicación, vea [Instalación y uso de aplicaciones con Power BI](end-user-app-view.md).

1. En un icono de tarjeta, KPI o medidor del panel, seleccione los puntos suspensivos.
   
   ![icono de tarjeta](media/end-user-alerts/power-bi-cards.png)
2. Haga clic en el icono de campana ![icono de alerta](media/end-user-alerts/power-bi-bell-icon.png), o bien en **Administrar alertas**, para agregar una o varias alertas para **Total de tiendas**.

   ![icono de tarjeta con puntos suspensivos seleccionados](media/end-user-alerts/power-bi-ellipses.png)

   
1. En el panel **Administrar alertas**, haga clic en **+ Agregar regla de alertas**.  Asegúrese de que el control deslizante esté **activado** y asigne un título a la alerta. Los títulos le ayudan a reconocer fácilmente las alertas.
   
   ![Ventana Administrar alertas](media/end-user-alerts/power-bi-manage-alert.png)
4. Desplácese hacia abajo y escriba los detalles de la alerta.  En este ejemplo, vamos a crear una alerta que nos enviará una notificación una vez al día si nuestra cuota de mercado es 35 o superior. Las alertas aparecen en nuestro Centro de notificaciones. Y haremos que Power BI nos envíe también un correo electrónico.
   
   ![Ventana Administrar alertas, establecimiento de umbral](media/end-user-alerts/power-bi-manage-alert-details.png)
5. Haga clic en **Guardar y cerrar**.
 
   > [!NOTE]
   > Las alertas solo funcionan en los datos que se actualizan. Cuando los datos se actualizan, Power BI busca si se ha configurado una alerta para esos datos. Si los datos han alcanzado un umbral de alerta, se activará una alerta. 
   > 

## <a name="receiving-alerts"></a>Recibir alertas
Si los datos de seguimiento llegan a uno de los umbrales que ha establecido, se realizan varias acciones. En primer lugar, Power BI comprueba si han pasado más de una hora, o de 24 horas (según la opción seleccionada), desde que se ha enviado la última alerta. Siempre que los datos superen el umbral, recibirá una alerta.

Después, Power BI envía una alerta al centro de notificaciones y, opcionalmente, un correo electrónico. Cada alerta contiene un vínculo directo a los datos. Seleccione el enlace para ver el icono pertinente.  

1. Si ha configurado la alerta para que se envíe un correo electrónico, encontrará algo parecido a esto en su bandeja de entrada. Esta alerta se configura en un panel diferente. En este panel se realiza un seguimiento de las tareas completadas por el equipo de facilidad de uso.
   
   ![Correo electrónico de alerta](media/end-user-alerts/power-bi-alert-email.png)
2. Power BI añade un mensaje a su **Centro de notificaciones** y una nueva alerta en el icono aplicable.
   
   ![Icono de notificación en el servicio Power BI](media/end-user-alerts/power-bi-task-alert.png)
3. Abra el Centro de notificaciones para ver los detalles de la alerta.
   
    ![Lectura de la alerta](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>Administración de alertas

Hay muchas maneras de administrar las alertas: desde el icono del panel, desde el menú de configuración de Power BI y en un icono individual en la [aplicación móvil de Power BI en el iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) o en la [aplicación móvil de Power BI para Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Desde el icono

1. Si necesita cambiar o quitar una alerta de un icono, vuelva a abrir la ventana **Administrar alertas** al seleccionar el icono de campana ![icono de alerta](media/end-user-alerts/power-bi-bell-icon.png). Se muestran todas las alertas que ha configurado para ese icono.
   
    ![Ventana Administrar alertas](media/end-user-alerts/power-bi-manage-alerts.png).
2. Para modificar una alerta, seleccione la flecha situada a la izquierda del nombre de la alerta.
   
    ![Flecha junto al nombre de la alerta](media/end-user-alerts/power-bi-modify-alert.png).
3. Para eliminar una alerta, seleccione la papelera situada a la derecha del nombre de la alerta.
   
      ![Icono de papelera seleccionado](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Desde el menú de configuración de Power BI

1. Seleccione el icono de engranaje de la barra de menús de Power BI.
   
    ![Icono de engranaje](media/end-user-alerts/powerbi-gear-icon.png).
2. En **Configuración**, seleccione **Alertas**.
   
    ![Pestaña Alertas de la ventana Configuración](media/end-user-alerts/power-bi-alert-settings.png)
3. Desde aquí, puede activar y desactivar alertas, abrir la ventana **Administrar de alertas** para realizar cambios o eliminar alertas.

## <a name="tips-and-troubleshooting"></a>Sugerencias y solución de problemas 

* Las alertas solo se pueden establecer en medidores, KPI y tarjetas.
* Si no puede establecer una alerta para un medidor, KPI o tarjeta, póngase en contacto con el administrador del sistema para pedir ayuda. A veces, las alertas se desactivan o no están disponibles para el panel o para tipos específicos de iconos del panel.
* Las alertas solo funcionan en los datos que se actualizan. No funcionan con datos estáticos. La mayoría de los ejemplos proporcionados por Microsoft son estáticos. 
* Los *consumidores* no crean sus propios paneles, sino que son los *diseñadores* quienes los crean y comparten con los consumidores. Para recibir y ver contenido compartido, se necesita una licencia Power BI Pro o Premium. Para más información, vea [¿Qué licencia tengo?](end-user-license.md) 


## <a name="clean-up-resources"></a>Limpieza de recursos
A continuación se dan instrucciones para eliminar alertas. En resumen, debe seleccionar el icono de engranaje de la barra de menús de Power BI. En **Configuración**, seleccione **Alertas** y elimine la alerta.

> [!div class="nextstepaction"]
> [Establecer alertas de datos en dispositivos móviles](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


