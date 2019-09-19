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
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/16/2019
ms.locfileid: "66413179"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Aplicación de un filtro cruzado entre objetos visuales en un informe de Power BI
Una de las grandes características de Power BI es la manera en que están conectados entre sí todos los objetos visuales en la página de un informe. Si selecciona un punto de datos en uno de los objetos visuales, todos los demás objetos visuales de la página que contienen ese dato cambian para adaptarse a la selección. 

![vídeo de interacción de objetos visuales](media/end-user-interactions/interactions.gif)

De forma predeterminada, al seleccionar un punto de datos en una visualización en una página de informe, se aplica filtro cruzado, resaltado cruzado y exploración a las demás visualizaciones en la página. 

Esto puede ser útil para identificar cómo contribuye un valor de los datos a otro. Por ejemplo, si selecciona el segmento Moderación del gráfico de anillos, se resalta la contribución de ese segmento a cada columna del gráfico Unidades totales por mes y se ha filtrado el gráfico de líneas de la derecha.

![Imagen de interacción de objetos visuales](media/end-user-interactions/power-bi-interactions.png)

Consulte [Filtros y resaltado en informes de Power BI](../power-bi-reports-filters-and-highlighting.md). 

El modo exacto en que interactúan los objetos visuales de una página se establece mediante el informe *diseñador*. Los diseñadores tienen opciones para activar y desactivar las interacciones de objetos visuales y para cambiar el valor predeterminado del filtrado cruzado, el resaltado cruzado y la profundización en detalles. 
  
> [!NOTE]
> Los términos *filtro cruzado* y *resaltado cruzado* se usan para distinguir el comportamiento que aquí se describe de lo que sucede cuando se usa el panel **Filtros** para filtrar y resaltar visualizaciones.  

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
- Si el informe tiene una visualización compatible con la [exploración](../power-bi-visualization-drill-down.md), de forma predeterminada, la exploración de una visualización no afecta a las demás visualizaciones de la página del informe.     
- Si usa visualA para interactuar con visualB, los filtros de nivel visual de visualA se aplican a visualB.

## <a name="next-steps"></a>Pasos siguientes
[Uso de filtros de informe](../power-bi-how-to-report-filter.md)
