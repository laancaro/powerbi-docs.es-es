---
title: La nueva experiencia de filtro en los informes de Power BI (versión preliminar)
description: Los filtros de Power BI van a tener una nueva funcionalidad y un nuevo diseño.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0a9e4986ae2f686eb8a8fd2d9fa07b169661ce60
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65853472"
---
# <a name="the-new-filter-experience-in-power-bi-reports-preview"></a>La nueva experiencia de filtro en los informes de Power BI (versión preliminar)

Filtros en Power BI tienen nuevas funcionalidades y un nuevo diseño. Al optar a la nueva experiencia de filtro, puede dar formato el panel de filtros para buscar como el resto del informe. Puede bloquear y ocultar incluso filtros. Al diseñar el informe, ya no verá el panel de filtros antiguo en absoluto en el panel visualizaciones. Hacer todo el filtro de edición y el formato en un único panel de filtros. 

![Nueva experiencia de filtro](media/power-bi-report-filter-preview/power-bi-filter-reading.png)

> [!NOTE]
> La nueva experiencia de filtro está en versión preliminar. Las compilaciones nuevas pueden invalidar el formato que ya haya configurado.

Como un diseñador de informes, aquí está lo que puede hacer en el panel de filtros único nuevo:

- Agregar y quitar campos para el filtro. 
- Cambiar el estado del filtro.
- Aplicar formato y personalizar el panel de filtros, por lo que parece que parte del informe.
- Definir si el panel de filtros está abierto o contraído de forma predeterminada cuando un consumidor abre el informe.
- Ocultar el panel de filtros de todo o filtros específicos que no desea que los consumidores de informes para ver.
- Control bookmark incluso la visibilidad, abrir y contrae el estado del nuevo panel de filtros.
- Bloquear los filtros que no desea que editen los consumidores.

Con la nueva experiencia de filtro, también pueden mantener los consumidores de informes a través de cualquier objeto visual para ver una lista de solo lectura de todos los filtros o segmentaciones de datos que afectan a ese objeto visual.

![Lista de filtros para un objeto visual](media/power-bi-report-filter-preview/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>Activar la nueva experiencia de filtro 

La nueva experiencia de filtro se habilita en Power BI Desktop. Luego, puede modificar ahí los filtros o en el servicio Power BI (https://app.powerbi.com). Dado que esta nueva experiencia de filtro se encuentra en versión preliminar, primero debe habilitarla en Power BI Desktop. Si empieza por crear un informe en el servicio Power BI, no puede tener nuevos filtros.

### <a name="turn-on-new-filters-for-all-new-reports"></a>Activar los nuevos filtros para todos los nuevos informes

1. En Power BI Desktop, seleccione **Archivo** > **Opciones y configuración** > **Opciones** > **Características de versión preliminar** y, luego, active la casilla **Nueva experiencia de filtro**. 
2. Reinicie Power BI Desktop para ver la nueva experiencia de filtro en todos los nuevos informes.

Después de reiniciar Power BI Desktop, está habilitada de forma predeterminada para todos los nuevos informes que se creen.  

### <a name="turn-on-new-filters-for-an-existing-report"></a>Activar nuevos filtros para un informe existente

También puede habilitar los nuevos filtros para informes existentes.

1. En Power BI Desktop, en un informe existente, seleccione **Archivo** > **Opciones y configuración** > **Opciones**.
2. En la barra de navegación izquierdo, bajo **archivo actual**, seleccione **notificar valores**.
3. En **filtrado experiencia**, seleccione **habilitar el panel Filtro actualizado y muestra los filtros en el encabezado para este informe visual**.

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Ver los filtros de un objeto visual en modo de lectura

En el modo de lectura, puede mantener el mouse sobre un icono de filtro de un objeto visual y ver una ventana emergente con todos los filtros, segmentaciones, etc., que afectan a ese objeto visual. El formato del elemento emergente es el mismo que el formato del panel de filtros. 

![Filtros que afectan a un objeto visual](media/power-bi-report-filter-preview/power-bi-filter-per-visual.png)

Estos son los tipos de filtros que se muestran en esta vista: 
- Filtros básicos
- Segmentaciones
- Resaltado cruzado 
- Filtrado cruzado
- Filtros avanzados
- N filtros principales
- Filtros de fecha relativa
- Segmentaciones de sincronización
- Filtros de inclusión o exclusión
- Filtros que se pasan mediante una dirección URL

## <a name="build-the-new-filters-pane"></a>Crear el nuevo panel de filtros

Después de habilitar el nuevo panel de filtros, se ve a la derecha de la página del informe, con formato según la configuración actual del informe de forma predeterminada. Utilice el nuevo panel de filtros para configurar los filtros para incluir y actualizar los filtros existentes en el nuevo panel. El nuevo panel de filtros muestra lo que los consumidores de informes se verán al publicar el informe. 

1. De forma predeterminada, los consumidores de informes pueden ver el panel filtros. Si no desea verlo, seleccione el icono de ojo junto a **filtros**.

    ![Icono de ojo de filtro de Power BI](media/power-bi-report-filter-preview/power-bi-filter-eye.png)

2. Para empezar a crear el nuevo panel de filtros, arrastrar campos de interés en el nuevo panel de filtros como visual, página o filtros de nivel de informe.

Cuando se agrega un objeto visual a un lienzo de informe, Power BI agrega automáticamente un filtro en el panel de filtros para cada campo en el objeto visual. 

## <a name="lock-or-hide-filters"></a>Bloquear u ocultar filtros

Puede bloquear u ocultar tarjetas de filtro individuales. Si bloquea un filtro, los consumidores de informes pueden verlo pero no modificarlo. Si lo oculta, no podrán ni siquiera verlo. Ocultar tarjetas de filtro es normalmente útil si necesita ocultar filtros de limpieza de datos que excluyen los valores nulos o inesperados. 

- En el nuevo panel de filtros, active o desactive el **Zamknout filtr** o **ocultar filtro** iconos en una tarjeta de filtro.

   ![Ocultar o bloquear filtros](media/power-bi-report-filter-preview/power-bi-filter-lock-hide.png)

Activar estas opciones y desactivar en el nuevo panel de filtros, ve los cambios reflejados en el informe. Los filtros ocultos no se muestran en la ventana emergente de filtros de un objeto visual.

También puede configurar el estado nueva del panel filtros para enviar con los marcadores de informe. Los estados abierto, cerrado y de visibilidad del panel se pueden todos guardar como marcador.
 
## <a name="format-the-new-filters-pane"></a>Aplicar formato el nuevo panel de filtros

Una parte importante de esta nueva experiencia es que puede dar formato el panel de filtros para que coincida con la apariencia del informe. Puede dar formato el panel de filtros de forma diferente para cada página del informe. Estos son los elementos a los que puede aplicar formato: 

- Color de fondo
- Transparencia del fondo
- Borde activado o desactivado
- Color del borde
- Tamaño de fuente, color y texto de título y el encabezado

También puede aplicar formato a estos elementos en las tarjetas de filtro, según si se han aplicado (establecido en algún valor) o están disponibles (desactivados): 

- Color de fondo
- Transparencia del fondo
- Borde: activar o desactivar
- Color del borde
- Tamaño de texto, color y fuente
- Color del cuadro de entrada

### <a name="format-the-filters-pane-and-cards"></a>Dar formato al panel de filtros y las tarjetas

1. En el informe, haga clic en el informe propiamente dicho o en el fondo (*papel tapiz*) y, en el panel **Visualizaciones**, seleccione **Formato**. 
    Vea las opciones de formato de la página del informe, el papel tapiz y también el panel filtros y las tarjetas de filtro.

    ![Seleccionar el icono de formato](media/power-bi-report-filter-preview/power-bi-filter-format.png)    

1. Expanda **Panel de filtros** para establecer el color del fondo, el icono y el borde izquierdo, a fin de complementar la página del informe.

    ![Expandir el panel de filtros](media/power-bi-report-filter-preview/power-bi-filter-format-pane-font.png)

1. Expanda **Tarjetas de filtro** para establecer el color y el borde **Disponible** y **Aplicado**. Si crea las tarjetas disponibles y aplicadas con diferentes colores, es obvio qué filtros se aplican. 
  
    ![Expandir la tarjeta de filtro](media/power-bi-report-filter-preview/power-bi-filter-format-card-font.png)

## <a name="theming-for-filter-pane"></a>Creación de temas para el panel de filtros
Ahora puede modificar la configuración predeterminada del panel de filtro con el archivo de tema. Este es un fragmento de tema de ejemplo para comenzar:

 
```
"outspacePane": [{ 

"backgroundColor": {"solid": {"color": "#0000ff"}}, 

"foregroundColor": {"solid": {"color": "#00ff00"}}, 

"transparency": 50, 

"titleSize": 35, 

"headerSize": 8, 

"fontFamily": "Georgia", 

"border": true, 

"borderColor": {"solid": {"color": "#ff0000"}} 

}], 

"filterCard": [ 

{ 

"$id": "Applied", 

"transparency": 0, 

"backgroundColor": {"solid": {"color": "#ff0000"}}, 

"foregroundColor": {"solid": {"color": "#45f442"}}, 

"textSize": 30, 

"fontFamily": "Arial", 

"border": true, 

"borderColor": {"solid": {"color": "#ffffff"}}, 

"inputBoxColor": {"solid": {"color": "#C8C8C8"}} 

}, 

{ 

"$id": "Available", 

"transparency": 40, 

"backgroundColor": {"solid": {"color": "#00ff00"}}, 

"foregroundColor": {"solid": {"color": "#ffffff"}}, 

"textSize": 10, 

"fontFamily": "Times New Roman", 

"border": true, 

"borderColor": {"solid": {"color": "#123456"}}, 

"inputBoxColor": {"solid": {"color": "#777777"}} 

}] 
```

## <a name="sort-the-filter-pane"></a>El panel de filtros de ordenación

Funcionalidad de ordenación personalizado forma parte de la nueva experiencia de panel de filtro. Creadores de informes pueden arrastrar y colocar filtros para reorganizarlos en el orden que deseen.

![Reorganizar el orden del filtro](media/power-bi-report-filter-preview/power-bi-filter-sort.gif)

El criterio de ordenación predeterminado es alfabético para los filtros. Para iniciar el modo de ordenación personalizada, solo tiene que arrastrar cualquier filtro a una nueva posición. Solo puede ordenar los filtros del nivel que se aplican a, por ejemplo, un filtro de nivel de objeto visual, nivel de página o nivel de informe.

## <a name="filters-pane-scaling"></a>Escalado del panel de filtros

El nuevo panel de filtros adapta a la página del informe y los objetos visuales, por lo que la página del informe y filtra permanecer de panel en la proporción entre sí.

## <a name="improved-filters-pane-accessibility"></a>Mejor accesibilidad del panel de filtros

Hemos mejorado la navegación mediante el teclado para el nuevo panel de filtros. Puede desplazarse por todas las partes del panel de filtros y usar la clave de contexto en el teclado o MAYÚS + F10 para abrir el menú contextual.

![Accesibilidad del panel de filtros](media/power-bi-report-filter-preview/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Cambiar el nombre de los filtros
Cuando se editan en el panel filtros, haga doble clic en el título para editarlo. Cambiar el nombre es útil si desea actualizar la tarjeta de filtro para que tenga más sentido para los usuarios finales. Tenga en cuenta que cambiar el nombre de la tarjeta de filtro *no* cambiar el nombre para mostrar del campo en la lista de campos. Solo cambia el nombre para mostrar usado en la ficha de filtro.

![Cambiar el nombre de un filtro](media/power-bi-report-filter-preview/power-bi-filter-rename.png)

## <a name="restrict-changes-to-filter-type"></a>Restringir los cambios para el tipo de filtro

Sección de la configuración del informe que tienen una opción para controlar si los usuarios pueden cambiar el tipo de filtro de experiencia en el filtrado.

![Restringir el tipo de filtro de variación](media/power-bi-report-filter-preview/power-bi-filter-restrict-change.png)

## <a name="next-steps"></a>Pasos siguientes

Pruebe la nueva experiencia de filtro. Envíenos sus comentarios para esta característica y cómo podemos mejorarlo, en el [sitio de Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

- [Uso de filtros de informe](consumer/end-user-report-filter.md)
- [Filtrado y resaltado en informes](power-bi-reports-filters-and-highlighting.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

