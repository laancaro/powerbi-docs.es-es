---
title: Usar la agrupación y la discretización en Power BI Desktop
description: Obtenga información sobre cómo agrupar y discretizar elementos en Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 525f7bf4c967722d8f98a9184127bc8c7907cea1
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75729932"
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Usar la agrupación y la discretización en Power BI Desktop
Cuando Power BI Desktop crea objetos visuales, agrega los datos en fragmentos (o grupos) en función de los valores que se encuentran en los datos subyacentes. A menudo esto es suficiente, pero puede haber ocasiones en las que quiera refinar la manera en que se presentan los fragmentos. Por ejemplo, tal vez le interese colocar tres categorías de productos en una categoría mayor (un *grupo*). También podría querer ver las cifras de ventas en tamaños de discretización de 1 000 000 dólares, en lugar de fragmentos de tamaños de 923 983 dólares.

En Power BI Desktop, puede *agrupar* puntos de datos para ver, analizar y explorar más claramente datos y tendencias en los objetos visuales. También puede definir la opción *Tamaño de la discretización* para colocar los valores en grupos de igual tamaño que le permitan visualizar los datos de manera coherente. Esta acción a menudo se denomina *discretización*.

## <a name="using-grouping"></a>Usar la agrupación
Para usar la agrupación, seleccione dos o más elementos de un objeto visual mediante Ctrl + clic para seleccionar varios elementos. A continuación, haga clic con el botón derecho en uno de los diversos elementos seleccionados y elija **Grupo** en el menú contextual.

![Comando de grupo, Gráfico, Agrupación, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_1.png)

Una vez creado, el grupo se agrega al cubo **Leyenda** del objeto visual. El grupo también aparece en la lista **Campos**.

![Listas de Leyendas y Campos, Agrupación, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_2.png)

Una vez que tenga un grupo, podrá editar fácilmente los miembros de ese grupo. Haga clic con el botón derecho en el campo del cubo **Leyenda** o de la lista **Campos** y, a continuación, elija **Editar grupos**.

![Comando Editar grupos, listas Leyenda y Campos, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_3.png)

En el cuadro de diálogo **Grupos**, puede crear grupos o modificar grupos existentes. También puede *cambiar el nombre* de cualquier grupo. Simplemente haga doble clic en el título del grupo en el cuadro **Grupos y miembros** y, a continuación, escriba un nombre nuevo.

Puede hacer de todo con los grupos. Los elementos de la lista **Valores no agrupados** se pueden agregar a un grupo nuevo o a uno de los grupos existentes. Para crear un grupo nuevo, seleccione dos o más elementos (con Ctrl + clic) en el cuadro **Valores no agrupados** y, después, seleccione el botón **Agrupar** que está debajo de ese cuadro.

Puede agregar un valor no agrupado a un grupo existente: simplemente seleccione un **Valor no agrupado**, luego seleccione el grupo existente al que desee agregarlo y seleccione el botón **Agrupar**. Para quitar un elemento de un grupo, selecciónelo en el cuadro **Grupos y miembros** y luego seleccione **Desagrupar**. También puede desplazar categorías no agrupadas al grupo **Otros** o dejarlas sin agrupar.

![Cuadro de diálogo Grupos, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> Puede crear grupos para cualquier campo del área **Campos** sin necesidad de seleccionar varios elementos de un objeto visual existente. Basta con que haga clic con el botón derecho en el campo y que seleccione **Nuevo grupo** en el menú que aparece.

## <a name="using-binning"></a>Usar la discretización
Puede establecer el tamaño de discretización de campos numéricos y de tiempo en **Power BI Desktop.** Puede usar la discretización para ajustar el tamaño de los datos que Power BI Desktop muestra.

Para aplicar un tamaño de discretización, haga clic con el botón derecho en un **Campo** y elija **Nuevo grupo**.

![Comando Nuevo grupo, lista de campos, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_5.png)

En el cuadro de diálogo **Grupos**, establezca el **Tamaño de la discretización** hasta el tamaño que quiera.

![Tamaño de la discretización, cuadro de diálogo Grupos, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_6.png)

Cuando seleccione **Aceptar**, observará que aparece un campo nuevo en el panel **Campos** con **(ubicaciones)** anexado. Después, puede arrastrar ese campo al lienzo para usar el tamaño de discretización en un objeto visual.

![Arrastrar campo de ubicaciones a un lienzo, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_7.png)

Para ver la *discretización* en acción, eche un vistazo a este [vídeo](https://www.youtube.com/watch?v=BRvdZSfO0DY).

Esto es todo lo que necesita saber para usar la *agrupación* y la *discretización* para asegurarse de que en los objetos visuales de los informes se muestran los datos tal y como usted quiere.
