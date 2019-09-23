---
title: Usar la agrupación y la discretización en Power BI Desktop
description: Obtenga información sobre cómo agrupar y discretizar elementos en Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b8d742e9238d438775115fd1ee2e287cf0ba0388
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454267"
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Usar la agrupación y la discretización en Power BI Desktop
Cuando **Power BI Desktop** crea objetos visuales, agrega los datos en fragmentos (o grupos) en función de los valores que se encuentran en los datos subyacentes. A menudo esto es suficiente, pero puede haber ocasiones en las que quiera refinar la manera en que se presentan los fragmentos. Por ejemplo, tal vez le interese colocar tres categorías de productos en una categoría mayor (un *grupo*). También podría querer ver las cifras de ventas en tamaños de discretización de 1 000 000 dólares, en lugar de 923 983 dólares divididos uniformemente.

En Power BI Desktop, puede **agrupar** puntos de datos para ver, analizar y explorar más claramente datos y tendencias en los objetos visuales. También puede definir la opción **Tamaño de la discretización**, que a menudo se denomina *discretización*, para colocar los valores en grupos de igual tamaño que le permitan visualizar los datos de manera coherente.

## <a name="using-grouping"></a>Usar la agrupación
Para usar la agrupación, seleccione dos o más elementos de un objeto visual mediante Ctrl + clic. Después, haga clic con el botón derecho en uno de los elementos seleccionados y elija **Grupo** en el menú que aparece.

![](media/desktop-grouping-and-binning/grouping-binning_1.png)

Una vez creado, el grupo se agrega al cubo **Leyenda** del objeto visual y también aparece en la lista **Campos**.

![](media/desktop-grouping-and-binning/grouping-binning_2.png)

Una vez que tenga un grupo, puede editar fácilmente los miembros de ese grupo. Para ello, haga clic con el botón derecho en el campo del cubo **Leyenda**, o de la lista **Campos**, y seleccione **Editar grupos**.

![](media/desktop-grouping-and-binning/grouping-binning_3.png)

En la ventana **Grupos** que aparece, puede crear grupos o modificar grupos existentes. Si quiere *cambiar el nombre* de un grupo, haga doble clic en el título del grupo en el cuadro **Grupos y miembros** y escriba un nuevo nombre.

Se puede hacer de todo con los grupos. Los elementos de la lista **Valores no agrupados** se pueden agregar a un grupo nuevo o a uno de los grupos existentes. Para crear un grupo nuevo, seleccione dos o más elementos (con Ctrl + clic) en el cuadro **Valores no agrupados** y, después, haga clic en el botón **Grupo** que está debajo de ese cuadro.

Puede agregar un valor no agrupado a un grupo existente: simplemente seleccione el valor no agrupado, luego seleccione el grupo existente al que desee agregarlo y haga clic en el botón **Grupo**. Para quitar un elemento de un grupo, selecciónelo en el cuadro **Grupos y miembros** y luego haga clic en **Desagrupar**. También puede seleccionar si las categorías sin agrupar deben colocarse en el grupo **Otros** o permanecer sin agrupar.

![](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> Puede crear grupos para cualquier campo del área **Campos** sin necesidad de realizar una selección múltiple en un objeto visual existente. Basta con que haga clic con el botón derecho en el campo y que seleccione **Nuevo grupo** en el menú que aparece.

## <a name="using-binning"></a>Usar la discretización
Puede establecer el tamaño de discretización de campos numéricos y de tiempo en **Power BI Desktop.** Puede usar la discretización para ajustar el tamaño de los datos que **Power BI Desktop** muestra.

Para aplicar un tamaño de discretización, haga clic con el botón derecho en un **Campo** y seleccione **Nuevo grupo**.

![](media/desktop-grouping-and-binning/grouping-binning_5.png)

En la ventana **Grupos**, establezca el **Tamaño de la discretización** hasta el tamaño que quiera.

![](media/desktop-grouping-and-binning/grouping-binning_6.png)

Cuando seleccione **Aceptar**, observará que aparece un campo nuevo en el panel **Campos** con *(ubicaciones)* anexado. Después, puede arrastrar ese campo al lienzo para usar el tamaño de discretización en un objeto visual.

![](media/desktop-grouping-and-binning/grouping-binning_7.png)

Para ver la **discretización** en acción, eche un vistazo a este [vídeo](https://www.youtube.com/watch?v=BRvdZSfO0DY).

Esto es todo lo que necesita saber para usar la **agrupación** y la **discretización** para asegurarse de que en los objetos visuales de los informes se muestran los datos tal y como usted quiere.

