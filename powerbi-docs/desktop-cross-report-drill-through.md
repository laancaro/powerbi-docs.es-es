---
title: Uso de la obtención de detalles entre varios informes en Power BI Desktop
description: Aprenda a obtener detalles entre un informe y otro en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e735d45a7a49c4a0365e35d5bb95957c6145f934
ms.sourcegitcommit: db4fc5da8e65e0a3dc35582d7142a64ad3405de7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70903753"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Uso de la obtención de detalles entre varios informes en Power BI Desktop

Con la característica de obtención de detalles entre varios informes de Power BI Desktop, puede pasar contextualmente de un informe a otro. Esto es posible siempre y cuando los informes estén dentro de la misma área de trabajo o aplicación en el servicio Power BI. Use la obtención de detalles entre varios informes para conectar dos o más informes que tengan contenido relacionado y para pasar el contexto de filtro junto con la conexión entre informes. En este artículo, aprenderá a configurar la obtención de detalles entre varios informes de Power BI y conocerá lo que experimentan los usuarios cuando usan esta característica por sí mismos.

![Captura de pantalla de la opción de obtención de detalles de Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Antes de empezar a configurar y usar la obtención de detalles entre varios informes, es importante comprender las siguientes definiciones:

* **Objeto visual de origen:** el objeto visual que invoca la acción de obtención de detalles mediante su menú contextual.
* **Informe de origen:** el informe que contiene el objeto visual de origen para la obtención de detalles entre varios informes.
* **Página de destino:** la página en la que un usuario aterriza después de iniciar una acción de obtención de detalles.
* **Informe de destino:** el informe que contiene la página de destino para la obtención de detalles entre varios informes.


> [!NOTE]
> El acceso a los informes compartidos de manera individual en *Mi área de trabajo*, que son informes que aparecen como *[Compartido conmigo](service-share-dashboards.md#share-a-dashboard-or-report)* , solo puede tener lugar en el área de trabajo desde donde se compartieron originalmente. 


## <a name="enable-cross-report-drillthrough"></a>Habilitación de la obtención de detalles entre varios informes

Para permitir que un informe sea el destino de una obtención de detalles entre varios informes, debe habilitar la característica para ese informe en la ventana **Opciones**. Vaya a **Archivo** > **Opciones y configuración** > **Opciones** y, luego, vaya a **Configuración de informes** cerca de la parte inferior de la página de la izquierda.

Active la casilla **Permitir a los objetos visuales de este informe utilizar los destinos de obtención de detalles de otros informes**, como se muestra en la imagen siguiente.

![Captura de pantalla de la ventana Opciones, con la opción Configuración de informes resaltada](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

La obtención de detalles entre varios informes está ahora habilitada.

## <a name="set-up-cross-report-drillthrough"></a>Configuración de la obtención de detalles entre varios informes

La configuración de la obtención de detalles entre varios informes es similar a la configuración de la obtención de detalles en un informe. La obtención de detalles está habilitada en la página de destino, lo que permite a otros objetos visuales dirigirse a la página habilitada para la obtención de detalles. Para ver los pasos para crear la obtención de detalles en un único informe, consulte [Uso de la obtención de detalles en Power BI Desktop](desktop-drillthrough.md).

Para iniciar el proceso de configuración, debe realizar un par de pasos iniciales:

* Configure una página de destino de obtención de detalles, a la que se pueda acceder luego desde otros informes del área de trabajo o la aplicación.
* Permita que un informe vea las páginas de obtención de detalles desde fuera de su propio informe.

Busque opciones de obtención de detalles en la sección **Campos** del panel **Visualizaciones**, como se muestra en la siguiente imagen.

![Captura de pantalla del panel Visualizaciones, con opciones de obtención de detalles resaltadas](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

El primer paso para habilitar la obtención de detalles en una página es validar los modelos de datos de los informes de origen y destino. Compruebe los siguiente: 

* Los campos que quiere pasar existen en ambos modelos de datos.
* Los nombres de los campos y los nombres de las tablas a las que pertenecen son idénticos (las cadenas también deben coincidir y distinguen mayúsculas de minúsculas).

Por ejemplo, si quiere pasar un filtro al campo *País* dentro de la tabla *Geografía*, ambos modelos deben tener una tabla *Geografía* y un campo *País* dentro de esa tabla. Si no es así, debe actualizar el nombre del campo o el nombre de la tabla en el modelo subyacente. Para que funcione correctamente la obtención de detalles entre varios informes, no basta con actualizar simplemente el nombre para mostrar de los campos. (Tenga en cuenta que los esquemas de cada informe no tienen que ser exactamente iguales).

Para comenzar con la configuración, debe tener preparada la página de destino. En Power BI Desktop, vaya a la página y asegúrese de que la opción de alternancia de obtención de detalles **Entre varios informes** esté establecida en **Activado**. 

![Captura de pantalla de la opción de alternancia Entre varios informes establecida en Activado](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

A continuación, arrastre al lienzo los campos que quiera usar como destino de obtención de detalles. Seleccione si quiere que el campo se use como una categoría o se resuma como una medida. En este momento, puede seleccionar si quiere deshabilitar la opción de alternancia **Mantener todos los filtros** para el objeto visual. Si no quiere pasar otros filtros aplicados entre el objeto visual de origen y el objeto visual de obtención de detalles de destino, seleccione **Desactivado**.

> [!NOTE]
> Si va a usar la página solo para la obtención de detalles entre varios informes, debe eliminar el botón **Atrás** que se agrega automáticamente. El botón **Atrás** solo funciona para la navegación dentro de un único informe. 

Después de configurar el objeto visual, asegúrese de guardar el informe si está en el servicio Power BI; si está en Power BI Desktop, puede guardar y publicar el informe.

En la sección anterior se describe cómo habilitar la obtención de detalles entre varios informes para Power BI Desktop (en la ventana **Opciones**). Si va a usar el servicio Power BI para crear un destino de obtención de detalles entre varios informes, haga lo siguiente para habilitar esta característica: 

1. Seleccione el área de trabajo en la que residen los informes de origen y destino.
2. Seleccione **Informes**.
3. Seleccione el icono **Configuración** del informe de origen.
4. Asegúrese de que la opción de alternancia de obtención de detalles de varios informes está **activada**.
5. Guarde el informe

Ya está. El informe está listo para la experiencia de obtención de detalles entre varios informes. 

En la siguiente sección, vamos a echar un vistazo a la experiencia desde la perspectiva del usuario.

## <a name="cross-report-drillthrough-experience"></a>Experiencia de obtención de detalles entre varios informes

Al configurar la experiencia de obtención de detalles entre varios informes para un informe, puede activar la característica.

Seleccione el informe de origen en el servicio Power BI y, luego, seleccione un objeto visual que use el campo o los campos de la forma que especificó al configurar la página de destino. A continuación, haga clic con el botón derecho en un punto de datos para abrir el menú contextual del objeto visual y seleccione **Obtención de detalles**.

![Captura de pantalla del informe de origen en el servicio Power BI, con Obtención de detalles resaltada](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Los resultados puede verlos en la página de obtención de detalles entre varios informes de destino, tal como los configuró cuando creó el destino. Los resultados se filtran según la configuración de obtención de detalles.

> [!IMPORTANT]
> Power BI almacena en caché los destinos de obtención de detalles entre varios informes. Si realiza cambios, asegúrese de actualizar el explorador si no ve los destinos de obtención de detalles según lo esperado. 

El formato se aplica a los destinos de varios informes de la siguiente manera: 

`Target Page Name [Target Report Name]`

Después de seleccionar la página de destino en la que quiere obtener detalles, Power BI va a esa página. Pasa por el contexto de filtro en función de la configuración de la página de destino. 

El contexto de filtro del objeto visual de origen puede incluir lo siguiente: 

* Filtros de nivel de informe, página y objeto visual que afectan al objeto visual de origen. 
* Filtro cruzado y resaltado cruzado que afectan al objeto visual de origen. 
* Segmentaciones en la página y segmentaciones de sincronización.
* Parámetros de dirección URL.

Al aterrizar en el informe de destino para la obtención de detalles, Power BI solo aplica filtros en los campos en los que encuentra coincidencias exactas de cadena con el nombre de campo y el nombre de tabla. Power BI no aplica filtros permanentes desde el informe de destino. Sin embargo, aplica el marcador personal predeterminado, si existe uno. Por ejemplo, si el marcador personal predeterminado incluye un filtro de nivel de informe para *País = US*, Power BI aplica primero ese filtro antes de aplicar el contexto de filtro del objeto visual de origen. 

Para la obtención de detalles entre varios informes, Power BI pasa el contexto de filtro a todas las páginas estándar del informe de destino. Power BI no pasa el contexto de filtro para las páginas de información sobre herramientas, ya que estas páginas se filtran en función del objeto visual de origen que invoca la información sobre herramientas.

Si quiere regresar al informe de origen después de la acción de obtención de detalles entre varios informes, use el botón **Atrás** del explorador. 

## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Uso de segmentaciones de datos en Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Uso de la obtención de detalles en Power BI Desktop](desktop-drillthrough.md)

