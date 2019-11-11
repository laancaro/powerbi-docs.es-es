---
title: Gráficos de área básicos
description: Gráficos de área básicos
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: ccba97d7fc4df050b9685dd9c2a69af36f62a485
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880970"
---
# <a name="basic-area-chart"></a>Gráficos de área básicos

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

El gráfico de área básico (también conocido como gráfico de área en capas) se basa en el gráfico de líneas. El área situada entre el eje y la línea se rellena con colores para indicar el volumen. 

Los gráficos de área destacan la magnitud del cambio con el tiempo y se pueden usar para llamar la atención sobre el valor total en una tendencia. Por ejemplo, se pueden trazar datos que representan el beneficio en el tiempo en un gráfico de área para destacar el beneficio total.

![](media/power-bi-visualization-basic-area-chart/power-bi-chart-example.png)

## <a name="when-to-use-a-basic-area-chart"></a>Cuándo usar un gráfico de área básico
Los gráficos de área básicos son una excelente opción:

* Para ver y comparar la tendencia del volumen a través de una serie temporal. 
* Para las series individuales que representan un conjunto físicamente contable.

### <a name="prerequisites"></a>Requisitos previos
En este tutorial se usa el [archivo PBIX del Ejemplo de análisis de minoristas](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de minoristas**.

1. Abra el **archivo PBIX del Ejemplo de análisis de minoristas** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.


## <a name="create-a-basic-area-chart"></a>Crear un gráfico de área básico
 

1. Estos pasos le ayudarán a crear un gráfico de áreas que muestra las ventas de este año y las ventas del año pasado por mes.
   
   a. En el panel Campos, seleccione **Ventas \> Ventas del último año** y **Ventas de este año > Valor**.

   ![Valores de datos del gráfico de áreas](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Para convertir el gráfico en un gráfico de áreas básico, haga clic en el icono de gráfico de áreas en el panel Visualizaciones.

   ![Icono del gráfico de áreas](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Seleccione **Time \> FiscalMonth** (Tiempo > Mes fiscal) para agregarlo al área **Eje**.   
   ![Valores de eje del gráfico de áreas](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Para mostrar el gráfico por mes, seleccione el botón de puntos suspensivos (esquina superior derecha del objeto visual) y elija **Sort by month** (Ordenar por mes). Para cambiar el criterio de ordenación, vuelva a hacer clic en los puntos suspensivos y seleccione **Orden ascendente** u **Orden descendente**.

## <a name="highlighting-and-cross-filtering"></a>Resaltado y filtrado cruzado
Para más información acerca de cómo usar el panel Filtros, consulte [Agregar un filtro a un informe](../power-bi-report-add-filter.md).

Para resaltar un área concreta en el gráfico, seleccione ese área o su borde superior.  A diferencia de otros tipos de visualización, si hay otras visualizaciones en la misma página, el resaltado de un gráfico de área básico no realiza un filtrado cruzado de las otras visualizaciones de la página del informe. Pero otras visualizaciones de la página de informe pueden desencadenar el filtrado cruzado de los gráficos de área. 

1. Para probarlo, seleccione el gráfico de áreas y cópielo en la página del informe **New Store Analysis** (Análisis de nuevas tiendas) (CTRL+C y CTRL+V).
2. Seleccione una de las áreas sombreadas del gráfico de áreas y, después, la otra. Comprobará que no afecta a las demás visualizaciones de la página.
1. Ahora seleccione un elemento. Fíjese en el impacto en el gráfico de áreas: se ha aplicado un filtro cruzado.

    ![Ejemplos de filtro](media/power-bi-visualization-basic-area-chart/power-bi-area-chart-filters.gif) 

Para más información, consulte [Interacciones de objetos visuales en los informes](../service-reports-visual-interactions.md)


## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas   
* [Hacer que el informe sea más accesible para personas con discapacidades](../desktop-accessibility.md)
* Los gráficos de área básicos no son eficaces para comparar valores debido a la ocultación de las áreas en capas. Power BI usa transparencias para indicar la superposición de áreas. Sin embargo, solo funciona bien con dos o tres áreas diferentes. Si necesita comparar tendencias de más de tres medidas, pruebe a usar los gráficos de líneas. Si necesita comparar volúmenes de más de tres medidas, pruebe a usar los gráficos de rectángulos.

## <a name="next-step"></a>Paso siguiente
[Informes en Power BI](power-bi-visualization-card.md)  

