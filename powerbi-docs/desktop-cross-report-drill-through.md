---
title: Uso de la obtención de detalles entre varios informes en Power BI Desktop
description: Aprenda a obtener detalles entre un informe y otro en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e500cb29bcc4472c59e7e8215fc0a7e7e728ea0d
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538902"
---
# <a name="use-cross-report-drillthrough-in-power-bi"></a>Uso de la obtención de detalles de varios informes en Power BI

Con la característica de *obtención de detalles de varios informes* de Power BI, puede pasar contextualmente de un informe a otro en la misma área de trabajo o aplicación del servicio Power BI. Puede usar la obtención de detalles de varios informes para conectar dos o más informes que tengan contenido relacionado y para pasar el contexto de filtro junto con la conexión entre informes. 

Para iniciar la obtención de detalles de varios informes, seleccione un punto de datos en un *objeto visual de origen* o un *informe de origen* y, después, seleccione el destino **Obtención de detalles** de varios informes en el menú contextual. 

![Opción de obtención de detalles de varios informes de Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

La acción de obtención de detalles abre la *página de destino* en el *informe de destino*. 

![Destino de la obtención de detalles de varios informes en Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

En este artículo se muestra cómo configurar y usar la obtención de detalles de varios informes para informes de Power BI.

> [!NOTE]
> La obtención de detalles de varios informes no se puede usar con los [informes Compartidos conmigo](service-share-dashboards.md#share-a-dashboard-or-report), es decir, los compartidos de forma individual en **Mi área de trabajo**. Para usar la obtención de detalles de varios informes, debe acceder a los informes en el área de trabajo desde la que se han compartido.

## <a name="enable-cross-report-drillthrough"></a>Habilitación de la obtención de detalles entre varios informes

El primer paso para habilitar la obtención de detalles de varios informes es validar los modelos de datos de los informes de origen y destino. Aunque no es necesario que los esquemas de cada informe sean los mismos, los campos que quiera pasar deben existir en ambos modelos de datos. Los nombres de los campos y de las tablas a las que pertenecen deben ser idénticos. Las cadenas deben coincidir y distinguir mayúsculas de minúsculas.

Por ejemplo, si quiere pasar un filtro por un campo **Estado** dentro de la tabla **Estados de EE. UU.** , ambos modelos deben tener una tabla **Estados de EE. UU.** y un campo **Estado** dentro de esa tabla. Si no es así, debe actualizar el nombre del campo o el nombre de la tabla en el modelo subyacente. Para que funcione correctamente la obtención de detalles entre varios informes, no basta con actualizar simplemente el nombre para mostrar de los campos.

Después de validar los modelos, habilite el informe de origen para usar la obtención de detalles de varios informes. 

1. En Power BI Desktop, vaya a **Archivo** > **Opciones y configuración** > **Opciones**. 
1. En la ventana **Opciones** de navegación de la izquierda, en la parte inferior de la sección **Archivo actual**, seleccione **Configuración de informes**. 
1. En la esquina inferior derecha, debajo de **Obtención de detalles de varios informes**, seleccione **Permitir a los objetos visuales de este informe utilizar los destinos de obtención de detalles de otros informes**. 
1. Seleccione **Aceptar**. 
   
   ![Habilitación de la obtención de detalles de varios informes en Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

También puede habilitar la obtención de detalles de varios informes desde el servicio Power BI.
1. En el servicio Power BI, seleccione el área de trabajo que contiene los informes de origen y de destino.
1. Junto al nombre del informe de origen en la lista de áreas de trabajo, seleccione el símbolo **Más opciones** y, después, **Configuración**. 
1. Junto a la parte inferior del panel **Configuración**, debajo de **Obtención de detalles de varios informes**, seleccione **Permitir a los objetos visuales de este informe utilizar los destinos de obtención de detalles de otros informes** y, luego, **Guardar**.
   
   ![Habilitación de la obtención de detalles de varios informes en el servicio Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drillthrough-target"></a>Configuración de un destino de obtención de detalles de varios informes

La configuración de una página de destino para la obtención de detalles de varios informes es similar a la de la obtención de detalles en un informe. La habilitación de la obtención de detalles en la página de destino permite destinar otros objetos visuales a la página para la obtención de detalles. Para crear la obtención de detalles en un único informe, vea [Uso de la obtención de detalles en Power BI Desktop](desktop-drillthrough.md).

Puede configurar un destino para la obtención de detalles de varios informes en Power BI Desktop o en el servicio Power BI. 
1. Edite el archivo de destino y, en la página destino del informe de destino, seleccione la sección **Campos** del panel **Visualizaciones**. 
1. En **Obtención de detalles**, establezca la opción **Entre varios informes** en **Activada**. 
1. Arrastre los campos que quiera usar como destinos de obtención de detalles a **Agregue los campos de obtención de detalles aquí**. Para cada campo, seleccione si quiere permitir la obtención de detalles cuando el campo se use como una categoría, o bien cuando se resuma como una medida. 
1. Seleccione si quiere **Mantener todos los filtros** para el objeto visual. Si no quiere pasar los filtros aplicados al objeto visual de origen al de destino, seleccione **Desactivado**.
   
   ![Panel Visualizaciones, con las opciones de obtención de detalles resaltadas](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. Si solo va a usar la página para la obtención de detalles de varios informes, elimine el botón **Atrás** que se agrega automáticamente al lienzo. El botón **Atrás** solo funciona para la navegación dentro de un informe. 
1. Después de configurar la página de destino, guarde el informe si usa el servicio Power BI, o bien, si usa Power BI Desktop, guárdelo y publíquelo.

Ya está. Los informes están listos para la obtención de detalles de varios informes. 

## <a name="use-cross-report-drillthrough"></a>Uso de la obtención de detalles en varios informes

Para usar la obtención de detalles de varios informes, seleccione el informe de origen en el servicio Power BI y, luego, seleccione un objeto visual que use el campo de obtención de detalles de la forma que haya especificado al configurar la página de destino. Haga clic con el botón derecho en un punto de datos para abrir el menú contextual del objeto visual, seleccione **Obtención de detalles** y, después, el destino de obtención de detalles. Los destinos de obtención de detalles de varios informes tienen el formato **Nombre de página [nombre de informe]** .

![Opción de obtención de detalles de varios informes de Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Puede ver los resultados en la página de destino de obtención de detalles de varios informes, como los haya configurado al crear el destino. Los resultados se filtran según la configuración de obtención de detalles.

![Destino de la obtención de detalles de varios informes en Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> Power BI almacena en caché los destinos de obtención de detalles entre varios informes. Si realiza cambios y no ve los destinos de obtención de detalles según lo esperado, asegúrese de actualizar el explorador. 

Si establece **Mantener todos los filtros** en **Activado** al configurar la página de destino, el contexto de filtro del objeto visual de origen puede incluir lo siguiente: 

- Filtros de nivel de informe, página y objeto visual que afectan al objeto visual de origen 
- Filtro cruzado y resaltado cruzado que afectan al objeto visual de origen 
- Segmentaciones y segmentaciones de sincronización en la página
- Parámetros de dirección URL

Al aterrizar en el informe de destino para la obtención de detalles, Power BI solo aplica filtros en los campos que tengan coincidencias exactas de cadena con el nombre del campo y de la tabla. 

Power BI no aplica filtros permanentes del informe de destino, pero sí el marcador personal predeterminado, si tiene uno. Por ejemplo, si el marcador personal predeterminado incluye un filtro de nivel de informe para *País = EE. UU.* , Power BI aplica ese filtro antes de aplicar el contexto de filtro del objeto visual de origen. 

Para la obtención de detalles de varios informes, Power BI pasa el contexto de filtro a las páginas estándar del informe de destino. Power BI no pasa el contexto de filtro para las páginas de información sobre herramientas, ya que estas páginas se filtran en función del objeto visual de origen que invoca la información sobre herramientas.

Si quiere regresar al informe de origen después de la acción de obtención de detalles entre varios informes, use el botón **Atrás** del explorador. 

## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

- [Segmentaciones en Power BI](visuals/power-bi-visualization-slicers.md)
- [Uso de la obtención de detalles en Power BI Desktop](desktop-drillthrough.md)

