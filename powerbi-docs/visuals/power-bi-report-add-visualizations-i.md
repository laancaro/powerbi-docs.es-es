---
title: Parte I, Incorporación de visualizaciones a un informe de Power BI
description: Parte I, Incorporación de visualizaciones a un informe de Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8095db86b8954b3f91a83f2e83c0108d1676cf76
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2018
ms.locfileid: "44748847"
---
# <a name="part-i-add-visualizations-to-a-power-bi-report"></a>Parte I, Incorporación de visualizaciones a un informe de Power BI
En este artículo, se ofrece una introducción rápida a la creación de una visualización en un informe mediante el servicio Power BI o Power BI Desktop.  Para ver contenido más avanzado, [consulte la parte II](power-bi-report-add-visualizations-ii.md). Vea cómo Amanda demuestra algunas maneras de crear, editar y dar formato a objetos visuales en el lienzo del informe. A continuación, inténtelo usted usando el [ejemplo de marketing y ventas](../sample-datasets.md) para crear su propio informe.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Abrir un informe y agregar una nueva página
1. Abra un [informe en la Vista de edición](../service-reading-view-and-editing-view.md). En este tutorial, se usa el [ejemplo de ventas y marketing](../sample-datasets.md).
2. Si el panel Campos no está visible, seleccione el icono de flecha para abrirlo. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. [Agregue una página en blanco al informe](../power-bi-report-add-page.md).

## <a name="add-visualizations-to-the-report"></a>Agregar visualizaciones al informe
1. Cree una visualización seleccionando un campo en el panel **Campos** .  
   
   **Comience con un campo numérico** como SalesFact > Sales $. Power BI crea un gráfico de columnas con una sola columna.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **O bien, comience con un campo de categoría**, como Nombre o Producto: Power BI crea una tabla y agrega ese campo al contenedor **Valores**.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **O bien, comience con un campo de geografía**, como Geografía > Ciudad. Power BI y mapas de Bing crean una visualización de mapa.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Cree una visualización y, a continuación, cambie su tipo. Seleccione **Producto > Categoría** y después **Producto > Recuento de productos** para agregarlos al área **Valores**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Cambie la visualización a un gráfico de columnas seleccionando el icono de gráfico de columnas.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. Cuando cree visualizaciones en el informe, puede [anclarlas al panel](../service-dashboard-pin-tile-from-report.md). Para anclar la visualización, seleccione el icono de anclaje ![](media/power-bi-report-add-visualizations-i/pinnooutline.png).
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
  

## <a name="next-steps"></a>Pasos siguientes
 Continuar con la [parte II del tutorial que le muestra cómo agregar visualizaciones a un informe de Power BI](power-bi-report-add-visualizations-ii.md).
   
   [Interactuar con las visualizaciones](../service-reading-view-and-editing-view.md) en el informe.
   
   [Hacer más cosas incluso con visualizaciones](power-bi-report-visualizations.md).
   
   [Guardar el informe](../service-report-save.md).
