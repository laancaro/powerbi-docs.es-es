---
title: Aplicación de un filtro cruzado entre objetos visuales en un informe (para consumidores de informes)
description: Documentación para los usuarios finales de Power BI que explica cómo interactúan los objetos visuales en una página de informe.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 838b881622dd19eb881aa53ac895f223cf9bc460
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180516"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Aplicación de un filtro cruzado entre objetos visuales en un informe de Power BI
Una de las grandes características de Power BI es la manera en que están conectados entre sí todos los objetos visuales en la página de un informe. Si selecciona un punto de datos en uno de los objetos visuales, todos los demás objetos visuales de la página que contienen ese dato cambian para adaptarse a la selección. 

![vídeo de interacción de objetos visuales](media/end-user-interactions/interactions.gif)

De forma predeterminada, las visualizaciones en una página de informe pueden usarse para el filtro cruzado, el resaltado cruzado y la profundización de las otras visualizaciones en la página. Por ejemplo, la selección de un estado en una visualización de mapa puede resaltar el gráfico de columnas y filtrar el gráfico de líneas para mostrar solo los datos aplicables a ese estado.

Consulte [Filtros y resaltado en informes de Power BI](../power-bi-reports-filters-and-highlighting.md). Si tiene una visualización compatible con la [obtención de detalles](../power-bi-visualization-drill-down.md), de manera predeterminada, la obtención de detalles de una visualización no afecta a otras visualizaciones de la página de informe. 

El modo exacto en que interactúan los objetos visuales de una página se establece mediante el informe *diseñador*. Los diseñadores tienen opciones para activar y desactivar las interacciones de objetos visuales y para cambiar el valor predeterminado del filtrado cruzado, el resaltado cruzado y la profundización en detalles.
  
> [!NOTE]
> Los términos *filtro cruzado* y *resaltado cruzado* se usan para distinguir el comportamiento que aquí se describe de lo que sucede cuando se usa el panel **Filtros** para filtrar y resaltar visualizaciones.  

### <a name="next-steps"></a>Pasos siguientes
[Uso de filtros de informe](../power-bi-how-to-report-filter.md)
