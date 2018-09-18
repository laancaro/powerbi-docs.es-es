---
title: Optimización de un objeto visual de Power BI de cualquier tamaño
description: Aprenda a optimizar objetos visuales en informes existentes de Power BI Desktop y el servicio Power BI para las aplicaciones de teléfono de Power BI.
author: maggiesMSFT
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d85d4bd60c341ef588cf56b1345f28aa25b810de
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2018
ms.locfileid: "44748707"
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Optimización de un objeto visual de Power BI de cualquier tamaño
De manera predeterminada, cuando se cree un nuevo informe, los objetos visuales tienen *capacidad de respuesta*: cambian de forma dinámica para mostrar la máxima cantidad de datos, independientemente del tamaño de la pantalla. Para los informes anteriores, puede establecer también sus objetos visuales para que cambien de tamaño de forma dinámica.

A medida que cambia el tamaño de un objeto visual, Power BI prioriza la vista de datos, por ejemplo, eliminando el relleno y desplazando la leyenda de la parte superior del objeto visual automáticamente, para que este siga siendo informativo aunque se haga de menor tamaño. La capacidad de respuesta es especialmente útil para los objetos visuales de la aplicación móvil de Power BI en teléfonos.

![Cambio de tamaño de un objeto visual con capacidad de respuesta](./media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Cualquier elemento visual con ejes X e Y, y segmentaciones, puede responder cambiando de tamaño.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Activación de la capacidad de respuesta en Power BI Desktop
1. En un informe anterior de Power BI Desktop, en la pestaña **Vista**, asegúrese de que se encuentra en **Diseño de escritorio**.
   
    ![Icono Diseño de escritorio](./media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Seleccione un objeto visual y en el panel de **visualizaciones**, seleccione la sección **Formato**.
3. Expanda **General** > deslice el control **Capacidad de respuesta** a **On**.
   
    ![Capacidad de respuesta activada](././media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Ahora cuando [cree un informe optimizado para el teléfono](../desktop-create-phone-report.md) y agregue este objeto visual, este cambiará de tamaño de forma correcta.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Activación de la capacidad de respuesta en el servicio Power BI
Puede activar la capacidad de respuesta de un objeto visual en un informe anterior en el servicio Power BI. Debe ser capaz de editar el informe.

1. En un informe del servicio Power BI ([https://powerbi.com](https://powerbi.com)), seleccione **Editar informe**.
2. Seleccione un objeto visual y en el panel de **visualizaciones**, seleccione la sección **Formato**.
3. Expanda **General** > deslice el control **Capacidad de respuesta** a **On**.
   
    ![Capacidad de respuesta activada](././media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Ahora cuando [cree una vista de teléfono de este informe](../desktop-create-phone-report.md) y agregue este objeto visual, este cambiará de tamaño de forma correcta.

## <a name="next-steps"></a>Pasos siguientes
* [Crear informes optimizados para las aplicaciones de teléfono de Power BI](../desktop-create-phone-report.md)
* [Ver informes de Power BI optimizados para el teléfono](../consumer/mobile/mobile-apps-view-phone-report.md)
* ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

