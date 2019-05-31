---
title: Configuración de presentación de página en un informe de Power BI
description: Configuración de la presentación de página y configuración de la vista de página de un informe
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 8a96371d6cb54d47d412165ef179df78a34b8e19
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412944"
---
# <a name="page-display-settings-in-a-power-bi-report"></a>Configuración de presentación de página en un informe de Power BI
Somos conscientes de que es fundamental mantener el píxel del diseño de informe perfecto. En ocasiones, puede resultar complicado, ya que usted y sus compañeros pueden ver esos informes en pantallas con relaciones de aspecto diferentes y tamaños. 

La vista de pantalla predeterminada es **Ajustar a la página** y el tamaño de pantalla predeterminado es **16:9**. Si desea fijar otra relación de aspecto o ajustar su informe de forma diferente, hay dos herramientas que le ayudarán: ***Vista de página*** configuración y ***tamaño de página*** configuración.


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>Dónde encontrar la configuración de la vista de página en el servicio Power BI y Power BI Desktop
Configuración de la vista de página está disponible en el servicio Power BI y Power BI Desktop, pero la interfaz es ligeramente diferente. Las secciones siguientes explican dónde puede encontrar ver la configuración en cada herramienta de Power BI.

### <a name="in-power-bi-desktop"></a>En Power BI Desktop
En la vista de informe, seleccione la pestaña **Vista** para abrir la configuración de la vista de página, así como la configuración del diseño de teléfono.

  ![Configuración de la vista de página de escritorio](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>En el servicio Power BI (app.powerbi.com)
En el servicio Power BI, abra un informe y seleccione **vista** desde la barra de menús superior izquierdo.

![configuración de la vista de página del servicio](media/power-bi-report-display-settings/power-bi-change-page-view.png)

Configuración de la vista de página está disponible tanto en [la vista de lectura y vista de edición](consumer/end-user-reading-view.md). En la vista de edición, el propietario de un informe puede asignar la configuración de la vista de página a páginas individuales del informe y esa configuración se guarda con el informe. Cuando los compañeros abren ese informe en la vista de lectura, ven las páginas del informe con la configuración del propietario. En la vista de lectura, los compañeros pueden cambiar *algunos* de la **vista de página** configuración, pero los cambios no se guardarán cuando cierre el informe.

## <a name="page-view-settings"></a>Configuración de la vista de página
El primer conjunto de configuración de la vista de página controla la presentación de la página del informe en relación con la ventana del explorador. Puede elegir entre:

* **Ajustar a la página** (valor predeterminado): Contenido se escala para ajustarse mejor a la página
* **Ajustar al ancho**: Contenido se escala para ajustarse al ancho de la página
* **Tamaño real**: Se muestra el contenido en tamaño completo

El segundo conjunto de controles de configuración de vista de página, la posición de los objetos en el lienzo del informe. Puede elegir entre:

* **Mostrar líneas de cuadrícula**: Activar las líneas de cuadrícula para colocar los objetos en el lienzo del informe.
* **Ajustar a la cuadrícula**: Usar con **mostrar líneas de cuadrícula** para colocar y alinear objetos en el lienzo del informe con precisión. 
* **Bloquear objetos**: Bloquear todos los objetos en el lienzo para que no se puede mover o cambiar de tamaño.
* **Panel selección**: El **selección** panel enumera todos los objetos en el lienzo. Puede decidir que se va a mostrar y que se va a ocultar.

    ![panel Selección](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>Configuración de tamaño de página
![cambiar la configuración de tamaño de página](media/power-bi-report-display-settings/power-bi-page-size.png)

**Tamaño de página** opciones solo están disponibles para los propietarios de informes. En el servicio Power BI (app.powerbi.com), esto significa que puede abrir el informe en [la vista de edición](consumer/end-user-reading-view.md). **Tamaño de página** configuración se encuentra en la **visualizaciones** panel y la proporción de presentación del control y el tamaño real (en píxeles) del lienzo del informe:   

* Relación 4:3
* Relación 16:9 (valor predeterminado)
* Cortana
* Carta
* Personalizado (alto y ancho en píxeles)

## <a name="next-steps"></a>Pasos siguientes
[Vista de informe en Power BI Desktop](desktop-report-view.md)

[Cambiar vista de página y la configuración de tamaño de página en sus propios informes de Power BI](consumer/end-user-report-view.md)

Más información sobre [informes de Power BI](consumer/end-user-reports.md)

[Conceptos básicos de los consumidores del servicio Power BI](consumer/end-user-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

