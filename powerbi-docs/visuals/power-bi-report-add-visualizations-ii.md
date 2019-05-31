---
title: Parte II, Incorporación de visualizaciones a un informe de Power BI
description: Parte II, Incorporación de visualizaciones a un informe de Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c42d96fea37a6309908dd357425c3d0504e18397
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61410261"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>Parte II, Incorporación de visualizaciones a un informe de Power BI
En la [parte I](power-bi-report-add-visualizations-ii.md), creó una visualización básica activando las casillas junto a los nombres de campo.  En la parte II, aprenderá a usar arrastrar y colocar, y a emplear toda la funcionalidad de los paneles **Campos** y **Visualizaciones** para crear y modificar visualizaciones.

### <a name="prerequisites"></a>Requisitos previos
- [Parte 1](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop: se pueden agregar visualizaciones a los informes con el servicio Power BI o Power BI Desktop. En este tutorial se usa Power BI Desktop. 
- [Ejemplo de análisis de minoristas](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>Creación de una nueva visualización
En este tutorial, nos adentraremos en el conjunto de datos de análisis de minoristas y crearemos algunas visualizaciones clave.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Abra un informe y agregue una nueva página en blanco.
1. Abra el archivo .PBIX del Ejemplo de análisis de minoristas en Power BI Desktop. 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2. Agregue una nueva página mediante el icono de signo más de color amarillo de la parte inferior del lienzo.

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Agregue una visualización que examine las ventas de este año en comparación con las del año pasado.
1. De la tabla **Sales**, seleccione **This Year Sales** >  y **Last Year Sales** en **Valor**. Power BI crea un gráfico de columnas.  Parece interesante y desea explorarlo en más profundidad. ¿Cómo son las ventas mensuales?  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. Desde la tabla Time, arrastre **MesFiscal** al área **Eje**.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [Cambie la visualización](power-bi-report-change-visualization-type.md) a un gráfico de áreas.  Hay muchos tipos de visualizaciones para elegir (consulte las [descripciones, las sugerencias de procedimientos recomendadas y los tutoriales](power-bi-visualization-types-for-reports-and-q-and-a.md) de cada uno para decidir cuál deber usar. En el panel Visualizaciones, haga clic en el icono del gráfico de áreas ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png).
4. Para ordenar la visualización, haga clic en el botón de puntos suspensivos (...) y seleccione **Ordenar por MesFiscal**.
5. [Cambie el tamaño de la visualización](power-bi-visualization-move-and-resize.md). Para ello, elíjala, seleccione uno de los círculos del esquema y arrástrelo. Debería ser lo bastante ancha como para que desaparezca la barra de desplazamiento y no demasiado grande, para que quede espacio suficiente para agregar otra visualización.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Guarde el informe](../service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Incorporación de una visualización de mapa que examina las ventas por ubicación
1. En la tabla **Tienda**, seleccione **Territorio**. Power BI reconoce que Territorio es una ubicación y crea una visualización de mapa.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. Arrastre **Total Stores** al área Tamaño.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. Agregue una leyenda.  Para ver los datos por nombre de tienda, arrastre **Cadena** al área Leyenda.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>Pasos siguientes
* Más información sobre [Visualizaciones en Power BI](power-bi-report-visualizations.md).  
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

