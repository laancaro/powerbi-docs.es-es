---
title: Uso de segmentaciones de datos en Power BI Desktop
description: Puede usar segmentaciones de datos en Power BI Desktop para filtrar, resaltar y personalizar los informes.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 161ea8f20db36c129787e84242ea002980d0f8dd
ms.sourcegitcommit: 70192daf070ede3382ac13f6001e0c8b5fb8d934
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2018
ms.locfileid: "46565875"
---
# <a name="using-slicers-power-bi-desktop"></a>Uso de segmentaciones de datos en Power BI Desktop

Puede usar una **segmentación de datos** en **Power BI Desktop** para filtrar los resultados de los objetos visuales en la página del informe. Y con las segmentaciones de datos, puede ajustar fácilmente el filtro que se aplica mediante la interacción con la propia segmentación de datos. También puede especificar opciones para la forma en que aparece la segmentación de datos y la interacción con ella. La siguiente imagen muestra una segmentación de datos con su menú desplegable *Tipo* visible. 

![Segmentaciones en Desktop](./media/desktop-slicers/desktop-slicers_01.png)

Una segmentación de datos se puede mostrar en alguno de estos tipos:

* Lista
* Desplegable
* Entre
* Menor o igual que
* Mayor o igual que

Puede agregar una segmentación de datos a un informe; para ello, haga clic en el objeto visual **segmentación de datos** del panel **Visualizaciones**.

![Tipo de objeto visual de la segmentación](./media/desktop-slicers/desktop-slicers_02.png)

Las segmentaciones de datos se comportan de forma similar en **Power BI Desktop** y el **servicio Power BI**. Para ver un artículo sobre cómo usar las segmentaciones, vea [Segmentaciones en el servicio Power BI](power-bi-visualization-slicers.md).

## <a name="synchronize-slicers-across-report-pages"></a>Sincronización de las segmentaciones de datos en varias páginas del informe

En **Power BI Desktop** puede sincronizar las segmentaciones de datos en varias páginas del informe. Para sincronizar las segmentaciones de datos, en el panel **Vista** de la cinta de opciones, seleccione **Segmentaciones de sincronización**. Al sincronizar las segmentaciones de datos, aparece el panel **Segmentaciones de sincronización**, como se muestra en la siguiente imagen.

![Mostrar el panel Sincronización de segmentaciones](./media/desktop-slicers/desktop-slicers_03.png)

En el panel **Segmentaciones de sincronización**, puede especificar cómo se debe sincronizar la segmentación de datos en las páginas del informe. Puede especificar si cada segmentación de datos debe **aplicarse** a cada página del informe individual, y si la segmentación de datos debe ser **visible** en cada página del informe individual.

Por ejemplo, puede colocar una segmentación de datos en la **página 2** del informe, como se muestra en la siguiente imagen. A continuación, puede seleccionar si desea que esa segmentación de datos se *aplique* a cada página seleccionada, y si esa segmentación de datos debe ser *visible* en cada página seleccionada del informe. Puede aplicar cualquier combinación de estas opciones para cada segmentación. 

![Segmentaciones de sincronización](./media/desktop-slicers/desktop-slicers_04.png)

Al utilizar el vínculo **Agregar a todo** del panel se aplica la segmentación seleccionada a todas las páginas del informe.


Tenga en cuenta que las selecciones que se muestran en el panel **Segmentaciones de sincronización** se aplican solo a la *segmentación seleccionada*. Puede aplicar varias segmentaciones a distintas páginas, y usar el panel para definir cómo se aplica individualmente cada segmentación de datos a través de las distintas páginas del informe. 

Mientras que la selección de segmentaciones de datos se puede sincronizar, otras selecciones como la aplicación de estilos, la edición y la eliminación *no* se sincronizan. 

## <a name="advanced-options-for-slicers"></a>Opciones avanzadas de las segmentaciones

También se puede aplicar un **nombre de grupo** a una colección de segmentaciones en la sección **Opciones avanzadas** del panel **Sincronización de segmentaciones**, así como sincronizar las segmentaciones que compartan el mismo grupo en todas las páginas. 

![Nombre de un grupo de segmentaciones](./media/desktop-slicers/desktop-slicers_05.png)

Esta característica permite crear un grupo personalizado de segmentaciones para mantenerlas sincronizadas. Se indica un nombre predeterminado, pero se puede usar el nombre que se quiera. 

El nombre del grupo proporciona una mayor flexibilidad en las segmentaciones. Así, se pueden crear grupos independientes para sincronizar segmentaciones que usen el mismo campo, o incluir en el mismo grupo segmentaciones que usen campos distintos. 


## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Segmentaciones en el servicio Power BI](power-bi-visualization-slicers.md)
* [Uso de la segmentación de intervalos numéricos en Power BI Desktop](../desktop-slicer-numeric-range.md)
* [Uso de un filtro o una segmentación de fecha relativa en Power BI Desktop](desktop-slicer-filter-date-range.md)

