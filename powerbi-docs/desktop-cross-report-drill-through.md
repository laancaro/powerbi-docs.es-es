---
title: Usar la obtención de detalles entre informes en Power BI Desktop
description: Obtenga información sobre cómo obtener detalles de un informe a otro en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375194"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Usar la obtención de detalles entre informes en Power BI Desktop

Con la característica de obtención de detalles entre informes en Power BI Desktop, puede saltar contextualmente desde un informe a otro informe. Esto es cierto, siempre y cuando los informes están dentro del mismo área de trabajo o aplicación en el servicio Microsoft Power BI. Utilice entre informes detallados para conectar dos o más informes que han contenido relacionado y pasar el contexto de filtro junto con la conexión entre informes. En este artículo, obtendrá información sobre cómo configurar la obtención de detalles entre informes para informes de Power BI, y lo que los usuarios experimentan al usar la obtención de detalles entre informes por sí mismos.

![Opción de obtención de detalles de captura de pantalla de Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Las definiciones siguientes son importantes para comprender, antes de comenzar cómo configurar y usar cross-informe de obtención de detalles:

* **Objeto visual de origen:** El objeto visual que invoca la acción de obtención de detalles mediante el menú contextual visual.
* **Informe de origen:** El informe que contiene el objeto visual de origen para la obtención de detalles entre informes.
* **Página de destino:** La página que llega un usuario después de iniciar una acción de obtención de detalles.
* **Informe de destino:** El informe que contiene la página de destino entre informes detallados.

## <a name="enable-cross-report-drillthrough"></a>Habilitar obtención de detalles entre informes

Para habilitar un informe para ser el destino de obtención de detalles entre informes, debe habilitar la característica para el informe en el **opciones** ventana. Vaya a **archivo** > **opciones y configuración** > **opciones**y, a continuación, vaya a **notificar valores** cerca de la parte inferior de la página de la izquierda.

Seleccione el **permitir que los objetos visuales en este informe para usar destinos de obtención de detalles desde otros informes** casilla de verificación, como se muestra en la siguiente imagen.

![Ventana de captura de pantalla de opciones, con la configuración de informe resaltado](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Obtención de detalles entre informes ahora está habilitado.

## <a name="set-up-cross-report-drillthrough"></a>Configurar entre informes detallados

Configuración de obtención de detalles entre informes es similar a la configuración de obtención de detalles en un informe. Obtención de detalles está habilitada en la página de destino, lo que permite a otros objetos visuales a la página habilitada para la obtención de detalles de destino. Para que conocer los pasos crear dentro de un único informe de obtención de detalles, consulte [utilizar la obtención de detalles en Power BI Desktop](desktop-drillthrough.md).

Para iniciar el proceso de instalación, debe tener un par de pasos inicial:

* Configurar una página de destino de obtención de detalles, que, a continuación, se puede acceder desde otros informes en el área de trabajo o la aplicación.
* Permitir que un informe para ver las páginas de obtención de detalles desde fuera de su propio informe.

Encuentre opciones de obtención de detalles en el **campos** sección de la **visualizaciones** panel, como se muestra en la siguiente imagen.

![Panel de la captura de pantalla de visualizaciones, con opciones de obtención de detalles resaltadas](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

El primer paso para habilitar la obtención de detalles para una página es validar los modelos de datos para los informes de origen y destino. Asegúrese de que: 

* Los campos que van a pasar existen en ambos modelos de datos.
* Los nombres de los campos y los nombres de las tablas a las que pertenecen, son idénticos (las cadenas deben coincidir también y distinguen mayúsculas de minúsculas).

Por ejemplo, si desea pasar un filtro en el campo *país* dentro de la tabla *Geography*, ambos modelos deben tener un *Geography* tabla y un *país* campo dentro de esa tabla. Si no es así, debe actualizar el nombre de campo o el nombre de tabla en el modelo subyacente. Simplemente actualizando el nombre para mostrar de los campos no funcionará correctamente para la obtención de detalles entre informes. (Tenga en cuenta que los esquemas en cada informe no tienen que ser exactamente el mismo.)

Para empezar a trabajar con la instalación, deberá preparar la página de destino. En Power BI Desktop, vaya a la página y asegúrese de que el **entre informes** alternancia de obtención de detalles está establecido en **en**. 

![Captura de pantalla de alternar entre informes activado](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

A continuación, arrastre los campos que desea usar como destino de obtención de detalles hasta el lienzo. Seleccione si desea que el campo se utiliza como una categoría o resumir como una medida. En este momento, puede seleccionar si desea deshabilitar el **conservar todos los filtros** alternar para el objeto visual. Si no desea pasar otros filtros aplicados desde el origen de visual para la obtención de detalles del destino visual, seleccione **desactivar**.

> [!NOTE]
> Si usa la página de sólo obtención de detalles entre informes, debe eliminar el **volver** botón que se agrega automáticamente. El **volver** botón solo funciona para nagivation dentro de un único informe. 

Después de haber configurado el objeto visual, asegúrese de guardar el informe si se encuentra en el servicio Power BI, o guardar y publicar el informe si usa Power BI Desktop.

La sección anterior describe cómo habilitar la obtención de detalles de entre-informe de Power BI Desktop (en el **opciones** ventana). Si usa el servicio Power BI para crear un destino entre informes detallados, para habilitar la obtención de detalles entre informes, debe: 

1. Seleccione el área de trabajo en el que residen el informe de destino y el informe de origen.
2. Seleccione **informes**.
3. Seleccione el **configuración** icono para el informe de origen.
4. Asegúrese de que es el botón de alternancia de obtención de detalles entre informes **en**.
5. Guarde el informe.

Ya está. El informe esté listo para la experiencia entre informes detallados. 

En la siguiente sección, echamos un vistazo a la experiencia desde la perspectiva del usuario.

## <a name="cross-report-drillthrough-experience"></a>Experiencia de obtención de detalles entre informes

Al configurar la experiencia de obtención de detalles entre informes para un informe, puede colocar la característica para usar.

Seleccione el informe de origen en el servicio Power BI y, a continuación, seleccione un objeto visual que utiliza el campo o campos de la manera que especificó al configurar la página de destino. A continuación, haga clic en un punto de datos para abrir el menú contextual visual y seleccione **obtención de detalles**.

![Captura de pantalla de informe de origen en el servicio Power BI, con resaltado de obtención de detalles](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

A continuación, verá los resultados en la página de obtención de detalles entre informes de destino, tal como configurarlas cuando creó el destino. Los resultados se filtran según la configuración de obtención de detalles.

> [!IMPORTANT]
> Power BI almacena en caché de destinos de obtención de detalles entre informes. Si realiza cambios, asegúrese de que actualizar el explorador si no ve los destinos de obtención de detalles, según lo previsto. 

Los destinos entre informes tienen el formato de la siguiente manera: 

`Target Page Name [Target Report Name]`

Después de seleccionar la página de destino al que desea obtener detalles, Power BI permite ir a esa página. Pasa el contexto de filtro según la configuración de la página de destino. 

Contexto de filtro desde el objeto visual de origen puede incluir lo siguiente: 

* Informes, página y filtros de nivel visual que afectan al objeto visual de origen. 
* Aplicar un filtro cruzado y resaltado cruzado que afectan al objeto visual de origen. 
* Segmentaciones de datos en la página y segmentaciones de sincronización.
* Parámetros de URL.

Cuando lleguen en el informe de destino para la obtención de detalles, Power BI solo se aplica a los filtros de campos para que busca coincide con la cadena exacta de nombre de tabla y campo. Power BI no aplica filtros rápidos desde el informe de destino. Sin embargo, se, aplicar el favorito personal de forma predeterminada si existe alguno. Por ejemplo, si el marcador personal de forma predeterminada incluye un filtro de nivel de informe para *Country = US*, Power BI aplica dicho filtro en primer lugar, antes de aplicar el contexto de filtro desde el objeto visual de origen. 

Cross-informe de obtención de detalles, Power BI pasa el contexto de filtro a todas las páginas estándares en el informe de destino. Power BI no pasa el contexto de filtro para las páginas de información sobre herramientas, porque las páginas de información sobre herramientas se filtran en función en el objeto visual de origen que invoca la información sobre herramientas.

Si desea volver al informe de origen después de la acción de obtención de detalles entre informes, utilice el explorador **volver** botón. 

## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Uso de segmentaciones de datos en Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Uso de la obtención de detalles en Power BI Desktop](desktop-drillthrough.md)

