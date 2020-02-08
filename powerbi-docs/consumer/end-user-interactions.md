---
title: Descripción de cómo interactúan los objetos visuales en un informe
description: Documentación para los usuarios finales de Power BI que explica cómo interactúan los objetos visuales en una página de informe.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 512ef5058fdb586a893c5ff9406abf6902ccc4e2
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2020
ms.locfileid: "76888509"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Aplicación de un filtro cruzado entre objetos visuales en un informe de Power BI
Una de las grandes características de Power BI es la manera en que están conectados entre sí todos los objetos visuales en la página de un informe. Si selecciona un punto de datos en uno de los objetos visuales, todos los demás objetos visuales de la página que contienen ese dato cambian para adaptarse a la selección. 

![vídeo de interacción de objetos visuales](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Cómo interactúan los objetos visuales entre sí

De forma predeterminada, al seleccionar un punto de datos en un objeto visual de una página de informe, se aplica filtro cruzado o resaltado cruzado a los demás objetos visuales en la página. El modo exacto en que interactúan los objetos visuales de una página se establece mediante el informe *diseñador*. Los *diseñadores* tienen opciones para activar y desactivar las interacciones de objetos visuales, y para cambiar el comportamiento predeterminado del filtrado cruzado, el resaltado cruzado y la [exploración en profundidad](end-user-drill.md). 

Si todavía no ha encontrado jerarquías o exploración en profundidad, puede leer [Explorar en profundidad en Power BI](end-user-drill.md) para obtener más información. 

### <a name="cross-filtering-and-cross-highlighting"></a>Resaltado cruzado y filtrado cruzado

El filtrado cruzado y el resaltado cruzado pueden ser útiles para identificar cómo contribuye un valor de los datos a otro. Los términos *filtro cruzado* y *resaltado cruzado* se usan para distinguir el comportamiento que aquí se describe de lo que sucede cuando se usa el panel **Filtros** para filtrar y resaltar objetos visuales.  

A continuación se definirán estos términos a medida que se examinan las páginas de informe siguientes. El gráfico de anillos "Volumen total de categoría por segmento" tiene dos valores: "Moderación" y "Comodidad". 

![Página del informe](media/end-user-interactions/power-bi-interactions-before.png)

1. A continuación se verá lo que sucede al seleccionar **Moderación**.

    ![Página del informe después de seleccionar el segmento Moderación del gráfico de anillos](media/end-user-interactions/power-bi-interactions-after.png)

2. El **filtrado cruzado** quita los datos que no se aplican. Al seleccionar **Moderación** en el gráfico de anillos, se realiza un filtrado cruzado del gráfico de líneas. Ahora en el gráfico de líneas solo se muestran los puntos de datos para el segmento Moderación. 

3. El **resaltado cruzado** conserva todos los puntos de datos originales, pero atenúa la parte que no se aplica a la selección. Al seleccionar **Moderación** en el gráfico de anillos, se realiza el resaltado cruzado del gráfico de columnas. El gráfico de columnas atenúa todos los datos que se aplican al segmento Comodidad y resalta todos los que se aplican al segmento Moderación. 


## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
- Si el informe tiene un objeto visual compatible con la [exploración](end-user-drill.md), de forma predeterminada, la exploración de un objeto visual no afecta a los demás de la página del informe. Sin embargo, el *diseñador* de informes puede cambiar este comportamiento, así que compruebe los objetos visuales que se pueden detallar para ver si ha habilitado los **filtros de detalles en otros objetos visuales**.
    
- Los filtros de nivel de objeto visual se conservan al realizar el filtrado y el resaltado cruzado de otros objetos visuales en la página del informe. Por tanto, si el objeto visual A tiene filtros de nivel de objeto visual aplicados por el diseñador de informes o usted mismo, y usa el objeto visual A para interactuar con el objeto visual B, los filtros de nivel de objeto visual de A se aplicarán a B.

    ![Página del informe después de seleccionar el segmento Moderación del gráfico de anillos](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Pasos siguientes
[Uso de filtros de informe](../power-bi-how-to-report-filter.md)    


[Acerca del filtrado y el resaltado](end-user-report-filter.md). 
