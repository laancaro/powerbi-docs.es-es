---
title: Configuración de las opciones de interacción de los informes
description: Obtenga más información sobre cómo invalidar la configuración de interacción predeterminada de los informes.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: painbar
ms.openlocfilehash: fee89c65328b70e1f312b39fbad75d7148bd92f2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542298"
---
# <a name="configure-report-interaction-settings"></a>Configuración de las opciones de interacción de los informes

## <a name="overview"></a>Información general

La aplicación móvil de Power BI tiene una serie de opciones de "interacción" configurables que permiten controlar cómo se interactúa con los datos y cómo se comportan algunos de los elementos de la aplicación móvil de Power BI. Actualmente hay opciones para:
* [Diferencias entre la interacción de pulsación única y doble en objetos visuales de los informes](#single-tap)
* [Diferencias entre pies de página de informe acoplados y dinámicos](#docked-report-footer-android-phones) (Android)
* [Diferencias entre la actualización de los informes iniciada por el botón y la función de deslizar para actualizar](#report-refresh-android-phones) (Android)

Para ir a la configuración de la interacción, pulse en la imagen del perfil para abrir el [panel lateral](./mobile-apps-home-page.md#header), elija **Configuración** y busque la sección **Interacción**.

![Configuración de la interacción](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

>[!NOTE]
>La configuración de la interacción para el botón de actualización y para acoplar el pie de página del informe actualmente no afecta a los informes de Report Server. Esto cambiará con la versión de enero de 2020 de Report Server.

## <a name="interaction-settings"></a>Configuración de la interacción

### <a name="single-tap"></a>Pulsación única
Al descargar la aplicación móvil de Power BI, está establecida para la interacción de pulsación única. Esto significa que, al pulsar un objeto visual para realizar una acción, como seleccionar un elemento de segmentación, resaltado cruzado, hacer clic en un vínculo o botón, etc., la pulsación selecciona el objeto visual y realiza la acción deseada.

Si lo prefiere, puede desactivar la interacción de pulsación única. Después, también tiene la interacción de pulsar dos veces. Con la interacción de pulsar dos veces, primero debe pulsar un objeto visual para seleccionarlo y, después, volver a pulsarlo para realizar la acción deseada.

### <a name="docked-report-footer-android-phones"></a>Pie de página de informe acoplado (teléfonos Android)

La configuración de pie de página de informe acoplado determina si el pie de página del informe permanece acoplado (es decir, fijo y siempre visible) en la parte inferior del informe, o bien si se oculta y vuelve a aparecer en función de las acciones que realice en el informe, como el desplazamiento.

En los teléfonos Android, la configuración de pie de página de informe acoplado está **activada** de forma predeterminada, lo que significa que el pie de página del informe está acoplado y siempre visible en la parte inferior del informe. Si prefiere un pie de página de informe dinámico que aparezca y desaparezca, en función de las acciones que realice en el informe, **desactívela**.

### <a name="report-refresh-android-phones"></a>Actualización de los informe (teléfonos Android)

La configuración de actualización de los informes define cómo se inician las actualizaciones de estos. Puede elegir entre tener un botón de actualización en todos los encabezados de informe, o bien usar la acción de deslizar para actualizar (y deslizar suavemente de arriba abajo) en la página del informe para actualizarlo. En la figura siguiente se muestran las dos alternativas. 

![Botón de actualización frente a deslizar para actualizar](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

En los teléfonos Android, se agrega un botón de actualización de forma predeterminada.

Para cambiar la configuración de actualización de un informe, vaya al elemento Actualizar informe de la configuración de interacción. Se mostrará la configuración actual. Pulse el valor para abrir una ventana emergente en la que puede elegir un valor nuevo.

![Establecimiento de la actualización](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Configuración remota

Un administrador también puede configurar de forma remota las interacciones mediante una herramienta de MDM con un archivo de configuración de la aplicación. De este modo, se puede estandarizar la experiencia de interacción de los informes en toda la organización o en grupos específicos de usuarios de la organización. Para obtener más información, vea [Configuración de la interacción con la administración de dispositivos móviles](./mobile-app-configuration.md).


## <a name="next-steps"></a>Pasos siguientes
* [Interacción con los informes](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Configuración de la interacción con la administración de dispositivos móviles](./mobile-app-configuration.md)
