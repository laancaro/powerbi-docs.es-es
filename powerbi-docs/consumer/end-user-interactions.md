---
title: Descripción de cómo interactúan los objetos visuales en un informe
description: Documentación para los usuarios finales de Power BI que explica cómo interactúan los objetos visuales en una página de informe.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413179"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Aplicación de un filtro cruzado entre objetos visuales en un informe de Power BI
Una de las grandes características de Power BI es la manera en que están conectados entre sí todos los objetos visuales en la página de un informe. Si selecciona un punto de datos en uno de los objetos visuales, todos los demás objetos visuales de la página que contienen ese dato cambian para adaptarse a la selección. 

![vídeo de interacción de objetos visuales](media/end-user-interactions/interactions.gif)

De forma predeterminada, seleccionar un punto de datos en una visualización en una página del informe, se filtrará, resaltado cruzado y explorar las otras visualizaciones en la página. 

Esto puede ser útil identificar cómo un valor de los datos que contribuye a otro. Por ejemplo, seleccionar el segmento moderación en el gráfico de anillos, resalta la contribución de ese segmento para cada columna en el Total de unidades por gráfico del mes, y ha filtrado el gráfico de líneas a la derecha.

![imagen de interacción de objetos visuales](media/end-user-interactions/power-bi-interactions.png)

Consulte [Filtros y resaltado en informes de Power BI](../power-bi-reports-filters-and-highlighting.md). 

El modo exacto en que interactúan los objetos visuales de una página se establece mediante el informe *diseñador*. Los diseñadores tienen opciones para activar y desactivar las interacciones de objetos visuales y para cambiar el valor predeterminado del filtrado cruzado, el resaltado cruzado y la profundización en detalles. 
  
> [!NOTE]
> Los términos *filtro cruzado* y *resaltado cruzado* se usan para distinguir el comportamiento que aquí se describe de lo que sucede cuando se usa el panel **Filtros** para filtrar y resaltar visualizaciones.  

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
- Si el informe tiene una visualización que admita [perforación](../power-bi-visualization-drill-down.md), de forma predeterminada, la obtención de detalles de una visualización no influye en las demás visualizaciones en la página del informe.     
- Si usa visualA para interactuar con visualB, filtros de nivel de objeto visual desde visualA se aplicará a visualB.

## <a name="next-steps"></a>Pasos siguientes
[Uso de filtros de informe](../power-bi-how-to-report-filter.md)
