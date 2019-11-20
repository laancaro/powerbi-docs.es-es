---
title: Ejecución y visualización de conclusiones en los iconos del panel
description: Como usuario final de Power BI, aprenda cómo obtener conclusiones sobre los iconos del panel.
author: mihart
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 9/22/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: ab37c806aaf3cd666c71dc22ee1f3d4d457647e0
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863401"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Visualización de conclusiones de datos en los iconos del panel con Power BI
Cada [icono](end-user-tiles.md) de objeto visual del panel es una puerta de entrada a la exploración de datos. Cuando se selecciona un icono, se abre un informe o las [Preguntas y respuestas](end-user-q-and-a.md), donde puede filtrar y ordenar, así como profundizar en el conjunto de datos subyacente al informe. Y al extraer información, Power BI realiza la exploración de datos por usted.

![modo del menú de puntos suspensivos](./media/end-user-insights/power-bi-insight.png)

Extraiga información para generar objetos visuales interactivos interesantes basados en los datos. Se puede extraer información en un icono de un panel específico e incluso conclusiones a partir de información detallada.

La característica de información detallada se basa en un creciente [conjunto de algoritmos de análisis avanzados](end-user-insight-types.md) desarrollado en combinación con Microsoft Research, que vamos a seguir usando para que más personas encuentren información en sus datos de formas nuevas e intuitivas.

## <a name="run-insights-on-a-dashboard-tile"></a>Información en un icono del panel
Al extraer información en un icono de panel, Power BI busca solo los datos utilizados para crear ese icono de panel único. 

1. [Abra un panel](end-user-dashboards.md).
2. Mantenga el puntero encima de un icono. Seleccione **Más opciones** (...) y elija **Ver información**. 

    ![modo del menú de puntos suspensivos](./media/end-user-insights/power-bi-hovers.png)


3. El icono se abre en [modo de enfoque](end-user-focus.md) con las tarjetas de información a la derecha.    
   
    ![Modo de enfoque](./media/end-user-insights/power-bi-insights-tile.png)    
4. ¿Alguna información capta su interés? Seleccione esa tarjeta de información para profundizar aún más. A la izquierda, se muestra la información seleccionada y, a la derecha, nuevas tarjetas de información, basadas solo en los datos de esa única información.    

 ## <a name="interact-with-the-insight-cards"></a>Interacción con las tarjetas de información
Una vez que tenga abierta una conclusión, siga explorando.

   * Filtre el objeto visual en el lienzo.  Para mostrar los filtros, en la esquina superior derecha, seleccione la flecha para expandir el panel Filtros.

      ![Información y menú Filtros expandido](./media/end-user-insights/power-bi-filters.png)
   
   * Información en la propia tarjeta. A esto se le conoce como **información relacionada**. Seleccione una tarjeta de información para activarla. Aparecerá en el lienzo del informe.
   
      ![Información y menú Filtros expandido](./media/end-user-insights/power-bi-insight-card.png)
   
   * En la esquina superior derecha, seleccione el icono de bombilla ![icono de Obtener información](./media/end-user-insights/power-bi-bulb-icon.png) u **Obtener información**. A la izquierda, se muestra la información y, a la derecha, nuevas tarjetas basadas solo en los datos de esa única información.
     
     ![Barra de menús con el icono de Obtener información](./media/end-user-insights/power-bi-related.png)
     
Para volver al informe, en la esquina superior izquierda, seleccione **Salir del modo de enfoque**.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
- **Ver información** no funciona con todos los tipos de iconos del panel. Por ejemplo, no está disponible para objetos visuales personalizados.<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Pasos siguientes
Obtenga información acerca de los [tipos de información rápida disponibles](end-user-insight-types.md)

