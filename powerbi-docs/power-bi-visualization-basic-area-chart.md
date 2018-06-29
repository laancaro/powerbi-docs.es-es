---
title: Gráficos de área básicos
description: Gráficos de área básicos
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/27/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 09322a1ead6ae4c3a00dc42e2b4a642dcc2d6181
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "34584148"
---
# <a name="basic-area-chart"></a>Gráficos de área básicos
El gráfico de área básico (también conocido como gráfico de área en capas) se basa en el gráfico de líneas. El área situada entre el eje y la línea se rellena con colores para indicar el volumen. 

Los gráficos de área destacan la magnitud del cambio con el tiempo y se pueden usar para llamar la atención sobre el valor total en una tendencia. Por ejemplo, se pueden trazar datos que representan el beneficio en el tiempo en un gráfico de área para destacar el beneficio total.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>Cuándo usar un gráfico de área básico
Los gráficos de área básicos son una excelente opción:

* Para ver y comparar la tendencia del volumen a través de una serie temporal. 
* Para las series individuales que representan un conjunto físicamente contable.

### <a name="prerequisites"></a>Requisitos previos
 - Servicio Power BI
 - Ejemplo de análisis de venta al por menor

Para continuar, inicie sesión en Power BI y seleccione **Obtener datos \> Ejemplos \> Ejemplo de análisis de minoristas > Conectar** y elija **Ir al panel**. 

## <a name="create-a-basic-area-chart"></a>Crear un gráfico de área básico
 

1. En el panel "Ejemplo de análisis de minoristas", seleccione el informe **Total de tiendas** para abrir el informe "Ejemplo de análisis de minoristas".
2. Seleccione **Editar informe** para abrir el informe en la Vista de edición.
3. Agregue una nueva página del informe mediante el icono de signo de suma amarillo (+) de la parte inferior del informe.
4. Cree un gráfico de área que muestra las ventas de este año y las ventas del año pasado por mes.
   
   a. En el panel Campos, seleccione **Ventas \> Ventas del último año** y **Ventas de este año > Valor**.

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Convierta el gráfico a un gráfico de área básico seleccionando el icono de gráfico de área en el panel VISUALIZACIONES.

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Seleccione **Tiempo \> Mes** para agregarlo al área **Ejes**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Para mostrar el gráfico por mes, seleccione el botón de puntos suspensivos (esquina superior derecha del objeto visual) y elija **Sort by month** (Ordenar por mes).

## <a name="highlighting-and-cross-filtering"></a>Resaltado y filtrado cruzado
Para más información sobre el uso del panel Filtros, consulte [Adición de un filtro a un informe](power-bi-report-add-filter.md).

Para resaltar un área concreta en el gráfico, seleccione ese área o su borde superior.  A diferencia de otros tipos de visualización, si hay otras visualizaciones en la misma página, el resaltado de un gráfico de área básico no realiza un filtrado cruzado de las otras visualizaciones de la página del informe. Pero otras visualizaciones de la página de informe pueden desencadenar el filtrado cruzado de los gráficos de área. Para más información, consulte [Interacciones de objetos visuales en los informes](service-reports-visual-interactions.md)


## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas   
* [Hacer que el informe sea más accesible para personas con discapacidades](desktop-accessibility.md)
* Los gráficos de área básicos no son eficaces para comparar valores debido a la ocultación de las áreas en capas. Power BI usa transparencias para indicar la superposición de áreas. Sin embargo, solo funciona bien con dos o tres áreas diferentes. Si necesita comparar tendencias de más de tres medidas, pruebe a usar los gráficos de líneas. Si necesita comparar volúmenes de más de tres medidas, pruebe a usar los gráficos de rectángulos.

## <a name="next-steps"></a>Pasos siguientes
[Informes en Power BI](service-reports.md)  
[Visualizaciones en informes de Power BI](power-bi-report-visualizations.md)  
[Power BI: Conceptos básicos](service-basic-concepts.md)  
¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

