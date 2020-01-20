---
title: Uso de marcadores en Power BI Desktop para compartir información detallada y crear historias
description: Los marcadores de Power BI Desktop le permiten guardar vistas y configuraciones en los informes y crear presentaciones a modo de historias
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 08d222f03991bdf605f8e465ff0152d40d07d815
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761896"
---
# <a name="create-bookmarks-in-power-bi-desktop-to-share-insights-and-build-stories"></a>Creación de marcadores en Power BI Desktop para compartir información detallada y crear historias
Con los *marcadores* de Power BI Desktop, se captura la vista configurada actualmente de una página del informe, incluidos los filtros y el estado de los objetos visuales. Después, puede volver a ese estado si selecciona el marcador guardado. 

También puede crear una colección de marcadores, organizarlos en el orden que quiera y, posteriormente, usarlos en una presentación para resaltar una serie de informaciones detalladas o la historia que quiera contar a través de los objetos visuales e informes. 

![Marcadores en Power BI](media/desktop-bookmarks/bookmarks_01.png)

Los marcadores tienen muchos usos. Por ejemplo, puede usar marcadores para realizar el seguimiento del progreso en la creación de informes (los marcadores son fáciles de agregar, eliminar y cambiar de nombre), y también puede usarlos para crear una presentación similar a las de PowerPoint que recorra los marcadores en orden, lo que permite contar una historia a través del informe. 

> [!TIP]
> Para obtener información sobre el uso de marcadores personales en el servicio Power BI, vea [Anuncio de los marcadores personales en el servicio Power BI](https://powerbi.microsoft.com/blog/announcing-personal-bookmarks-in-the-power-bi-service/). 

## <a name="using-bookmarks"></a>Uso de marcadores
Para usar marcadores, seleccione la pestaña **Vista** en la cinta de Power BI Desktop y, después, seleccione **Panel Marcadores**. 

![Activación del panel Marcadores](media/desktop-bookmarks/bookmarks_03.png)

Cuando crea un marcador, los siguientes elementos se guardan con él:

* La página actual
* Filtros
* Segmentaciones de datos, incluidos el tipo de segmentación de datos (por ejemplo, menú desplegable o lista) y el estado de la segmentación de datos
* Estado de selección del objeto visual (por ejemplo, los filtros de resaltado cruzado)
* Criterio de ordenación
* Ubicación de exploración
* Visibilidad de un objeto (mediante el panel **Selección**)
* Los modos de enfoque o de **Destacados** de cualquier objeto visible

Configure una página de informe de la forma en que quiera que aparezca en el marcador. Una vez que la página del informe y los objetos visuales estén organizados como quiere, seleccione **Agregar** en el panel **Marcadores** para agregar un marcador. 

![Agregar un marcador](media/desktop-bookmarks/bookmarks_04.png)

Power BI Desktop crea un marcador y le asigna un nombre genérico. Puede **cambiar de nombre**, **eliminar** o **actualizar** un marcador con facilidad si selecciona los puntos suspensivos situados junto al nombre del marcador y, después, elige una acción en el menú que aparece.

![Selección del menú de marcadores mediante los puntos suspensivos](media/desktop-bookmarks/bookmarks_05.png)

Una vez que haya creado un marcador, selecciónelo en el panel **Marcadores**. 

También puede seleccionar si cada marcador aplicará propiedades de **datos**, como filtros y segmentaciones, propiedades de **visualización**, como destacados y su visibilidad, y cambios de **página actual** que presentan la página que estaba visible cuando se ha agregado el marcador. Estas funciones son útiles cuando se usan marcadores para cambiar entre vistas de informe o selecciones de objetos visuales, en cuyo caso es probable que quiera desactivar las propiedades de datos, de manera que los filtros no se restablezcan cuando los usuarios cambien de vistas al seleccionar un marcador. 

Para realizar estos cambios, seleccione los puntos suspensivos situados junto al nombre del marcador y, después, seleccione o anule la selección de las marcas de verificación junto a **Datos**, **Pantalla** y otros controles. 

## <a name="arranging-bookmarks"></a>Organización de los marcadores
A medida que cree marcadores, es posible que compruebe que el orden en que los crea sea distinto al que le gustaría presentar al público de destino. No hay problema, se puede reorganizar fácilmente el orden de los marcadores.

- En el panel **Marcadores**, arrastre y coloque los marcadores para cambiar su orden. 

   La barra amarilla entre marcadores indica donde se colocará el marcador arrastrado.

   ![Cambiar el orden de los marcadores mediante la opción de arrastrar y colocar](media/desktop-bookmarks/bookmarks_06.png)

El orden de los marcadores puede ser importante a la hora de usar la característica **Vista** de los marcadores, como se describe en la sección siguiente.

## <a name="bookmarks-as-a-slide-show"></a>Marcadores como una presentación con diapositivas
Si tiene una colección de marcadores que le gustaría presentar en orden, puede seleccionar **Vista** en el panel **Marcadores** para empezar una presentación.

Cuando está en el modo **Vista**, hay algunas características que tener en cuenta.

   ![Características de la barra de título del marcador](media/desktop-bookmarks/bookmarks_07.png)

1. El nombre del marcador aparece en la barra de título de este, la cual, a su vez, aparece en la parte inferior del lienzo.

2. La barra de título del marcador tiene flechas que le permiten moverse al marcador siguiente o al anterior.

3. Puede salir del modo **Vista** si selecciona **Salir** en el panel **Marcadores** o la **X** de la barra de título del marcador. 

Cuando está en modo **Vista**, puede cerrar el panel **Marcadores** si hace clic en la **X** de ese panel, para proporcionar más espacio para la presentación. Todos los objetos visuales son interactivos cuando están en el modo **Vista** y están disponibles para el resaltado cruzado, como lo estarían cuando se interactúa con ellos de forma directa. 

## <a name="visibility-using-the-selection-pane"></a>Visibilidad: Uso del panel Selección
Relacionado con el panel **Marcadores**, el panel **Selección** proporciona una lista de todos los objetos de la página actual y le permite seleccionar un objeto y especificar si es visible. 

![Habilitar el panel Selección](media/desktop-bookmarks/bookmarks_08.png)

En el panel **Selección**, seleccione un objeto y, para alternar si es visible actualmente, seleccione el icono de ojo situado a la derecha del objeto. 

![Panel Selección](media/desktop-bookmarks/bookmarks_09.png)

Al agregar un marcador, el estado de visibilidad de cada objeto también se guarda, en función de su configuración en el panel **Selección**. 

Es importante tener en cuenta que las segmentaciones siguen filtrando una página de informe, con independencia de si son visibles o no. Por tanto, puede crear muchos marcadores diferentes, con distintas configuraciones de segmentación, y hacer que una única página del informe tenga otro aspecto (y se resalten otros datos) en distintos marcadores.

## <a name="bookmarks-for-shapes-and-images"></a>Marcadores para formas e imágenes
También puede vincular formas e imágenes a los marcadores. Con esta característica, al seleccionar un objeto, muestra el marcador asociado a él. Esta característica puede ser especialmente útil cuando se trabaja con botones. Para más información, vea [Uso de botones en Power BI](desktop-buttons.md). 

Para asignar un marcador a un objeto: 

1. Seleccione el objeto en el lienzo del informe. Después, en el panel **Formato de forma** que aparece, **active** el control deslizante **Acción**.

2. Expanda la sección **Acción**. En **Tipo**, seleccione **Marcador**.

3. En **Marcadores**, seleccione un marcador.

   ![Agregar vínculo de marcador a un objeto](media/desktop-bookmarks/bookmarks_10.png)

Hay todo tipo de cosas interesantes que puede hacer con marcadores con objetos vinculados. Puede crear una tabla de objetos visuales en la página del informe, o bien proporcionar otras vistas (por ejemplo, los tipos de objeto visual) de la misma información.

Cuando esté en el modo de edición, presione **Ctrl** y seleccione el vínculo para seguirlo. Cuando no esté en el modo de edición, seleccione el objeto para seguir el vínculo. 

## <a name="bookmark-groups"></a>Grupos de marcadores

A partir de la versión de agosto de 2018 de Power BI Desktop, puede crear y usar grupos de marcadores. Un grupo de marcadores es una colección de marcadores que especifica y que se pueden mostrar y organizar como un grupo. 

Para crear un grupo de marcadores: 
1. Presione **Ctrl** y seleccione los marcadores que quiera incluir en el grupo. 

2. Seleccione los puntos suspensivos situados junto a los marcadores seleccionados y, después, seleccione **Grupo** en el menú que aparece.

   ![Crear un grupo de marcadores](media/desktop-bookmarks/bookmarks_15.png)

Power BI Desktop asigna el nombre *Grupo 1* al grupo de forma automática. Puede seleccionar los puntos suspensivos situados junto a este nombre, seleccionar **Cambiar el nombre**y cambiar el nombre por el que quiera.

![Cambiar el nombre de un grupo de marcadores](media/desktop-bookmarks/bookmarks_16.png)

Como sucede con cualquier grupo de marcadores, al expandir el nombre del grupo, solo se expande o contrae el grupo, y no se representa ningún marcador por sí mismo. 

Al usar la característica **Vista** de los marcadores, se aplican los detalles siguientes:

* Si el marcador seleccionado está en un grupo cuando se hace clic en **Ver** en los marcadores, solo los marcadores *de ese grupo* se muestran en la sesión de visualización. 

* Si el marcador seleccionado no está en un grupo, o si se encuentra en el nivel superior (por ejemplo, el nombre de un grupo de marcadores), se reproducen todos los marcadores del informe completo, incluidos los de cualquier grupo. 

Para desagrupar marcadores: 
1. Seleccione cualquier marcador de un grupo y seleccione los puntos suspensivos. 

2. En el menú que aparece, seleccione **Desagrupar**.

   ![Desagrupar un grupo de marcadores](media/desktop-bookmarks/bookmarks_17.png)

   Al seleccionar **Desagrupar** en cualquier marcador de un grupo, se quitan todos los marcadores del grupo; se elimina el grupo, pero no los marcadores. 

Para quitar un solo marcador de un grupo: 
1. Seleccione **Desagrupar** en cualquier miembro de ese grupo, lo que elimina el grupo completo. 

2. Seleccione los miembros que quiera en el grupo nuevo. Para ello, presione **Ctrl** y seleccione cada uno de los marcadores y, después, vuelva a seleccionar **Agrupar**. 


## <a name="using-spotlight"></a>Uso de Destacados
Otra característica que se ha publicado junto con los marcadores es *Destacados*. Con Destacados se puede llamar la atención sobre un gráfico concreto, por ejemplo, al presentar los marcadores en el modo **Vista**.

A continuación se comparará Destacados con el modo de enfoque para ver en qué se diferencian:

1. Con el modo de enfoque, se selecciona el icono **Modo de enfoque** de un objeto visual, para que rellene todo el lienzo.

2. Con Destacados, se selecciona **Destacados** desde los puntos suspensivos de un objeto visual para resaltarlo a su tamaño original, lo que hace que todos los demás objetos visuales de la página se atenúen hasta ser prácticamente transparentes. 

![Comparación de Destacados con el modo de enfoque](media/desktop-bookmarks/bookmarks_11.png)

Al seleccionar el icono del **modo de enfoque** del objeto visual de la imagen anterior, la página aparece de esta manera:

![Modo de enfoque](media/desktop-bookmarks/bookmarks_12.png)

En cambio, si se selecciona **Destacados** en el menú de puntos suspensivos del objeto visual, la página se parecerá a esta:

![Modo Destacados](media/desktop-bookmarks/bookmarks_13.png)

Si selecciona el modo de enfoque o Destacados al agregar un marcador, ese modo se conserva en el marcador.

## <a name="bookmarks-in-the-power-bi-service"></a>Marcadores en el servicio Power BI
Cuando publica un informe en el servicio Power BI con al menos un marcador, puede verlos e interactuar con ellos en el servicio Power BI. Cuando los marcadores están disponibles en un informe, los paneles **Selección** y **Marcadores** se muestran al seleccionar **Vista** > **Panel Selección** o **Vista** > **Panel Marcadores**. 

![Ver paneles de selección y de marcadores en el servicio Power BI](media/desktop-bookmarks/bookmarks_14.png)

En el servicio Power BI, el panel **Marcadores** funciona igual que en Power BI Desktop, incluida la posibilidad de seleccionar **Vista** para mostrar los marcadores en orden, como en una presentación con diapositivas.

Use la barra de título del marcador de color gris, en lugar de las flechas negras, para desplazarse por los marcadores. (Las flechas negras le desplazan a través de las páginas del informe, no de los marcadores).

## <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>Habilitar la versión preliminar de los marcadores (versiones anteriores a marzo de 2018)
Los marcadores están disponibles con carácter general a partir de la versión de marzo de 2018 de Power BI Desktop. 

Siempre se recomienda actualizar a la versión más reciente, pero si la versión de Power BI Desktop es anterior a esa, puede probar la característica de marcadores a partir de la versión de octubre de 2017 de Power BI Desktop y, en el caso de los informes habilitados para marcadores, también en el servicio Power BI. 

Para habilitar la característica de marcadores de versión preliminar: 

1. Seleccione **Archivo** > **Opciones y configuración** > **Opciones** > **Características de versión preliminar** y, luego, seleccione **Marcadores**. 

   ![Habilitar marcadores en la ventana de opciones](media/desktop-bookmarks/bookmarks_02.png)

2. Reinicie Power BI Desktop para habilitar la versión preliminar de los marcadores.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones
En esta versión de las características de marcadores, hay algunas limitaciones y consideraciones que debe tener en cuenta.

* La mayoría de objetos visuales personalizados deben funcionar bien con marcadores. Pero si experimenta problemas con los marcadores y un objeto visual personalizado, póngase en contacto con el creador de ese objeto visual personalizado y pídale que agregue compatibilidad con los marcadores a su objeto visual. 
* Si agrega un objeto visual en una página de informe después de crear un marcador, el objeto visual se muestra en su estado predeterminado. Es decir, si se introduce una segmentación en una página en la que previamente ha creado marcadores, la segmentación se comporta según su estado predeterminado.
* El desplazamiento por un objeto visual después de haber creado un marcador se reflejará de forma automática en este. 

## <a name="next-steps"></a>Pasos siguientes
Para más información sobre las características que son similares o que interactúan con los marcadores, vea los artículos siguientes:

* [Uso de la obtención de detalles en Power BI Desktop](desktop-drillthrough.md)
* [Representación de un icono de panel o un objeto visual de informe en modo de enfoque](consumer/end-user-focus.md)

