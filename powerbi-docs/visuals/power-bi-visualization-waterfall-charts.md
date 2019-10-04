---
title: Gráficos de cascada en Power BI
description: Gráficos de cascada en Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3ab200194d89eb15892dc4f452079eb56df8a608
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2019
ms.locfileid: "71191341"
---
# <a name="waterfall-charts-in-power-bi"></a>Gráficos de cascada en Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Los gráficos de cascada muestran un total acumulado a medida que Power BI agrega y resta valores. Son útiles para comprender cómo afecta una serie de cambios positivos y negativos a un valor inicial (por ejemplo, ingresos netos).

Las columnas están codificadas por color para identificar rápidamente los aumentos y las disminuciones. Las columnas de valores iniciales y finales a menudo [comienzan en el eje horizontal](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "comienzan en el eje horizontal"), mientras que los valores intermedios son columnas flotantes. Debido a este estilo, los gráficos de cascada también se denominan gráficos de puente.

   > [!NOTE]
   > En este vídeo se usa una versión anterior de Power BI Desktop.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Cuándo usar un gráfico de cascada

Los gráficos de cascada son una excelente opción:

* Cuando la medida sufre cambios con el transcurso del tiempo y a través de una serie o de diferentes categorías.

* Para auditar los cambios más importantes que contribuyen al valor total.

* Para trazar el beneficio anual de la compañía mostrando varias fuentes de ingresos y obtener la ganancia total (o pérdida).

* Para ilustrar la plantilla inicial y final de su empresa en un año.

* Para visualizar la cantidad de dinero que genera y gasta cada mes, y el saldo corriente de su cuenta.

## <a name="prerequisite"></a>Requisito previo

En este tutorial se usa el [archivo PBIX del Ejemplo de análisis de minoristas](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de minoristas**.

1. Abra el **archivo PBIX del Ejemplo de análisis de minoristas** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.


## <a name="create-a-waterfall-chart"></a>Crear un gráfico de cascada

Vamos a crear un gráfico de cascada que muestre la varianza de las ventas (ventas estimadas frente a las ventas reales) por mes.

1. En el panel **Campos**, seleccione **Ventas** > **Varianza total de ventas**.

   ![Captura de pantalla de Ventas > Varianza total de ventas seleccionada y el objeto visual resultante.](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. Seleccione el icono de cascada ![Captura de pantalla del icono de cascada](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png)

    ![Plantillas de visualización](media/power-bi-visualization-waterfall-charts/convert-waterfall.png)

1. Seleccione **Tiempo** > **MesFiscal** para agregarlo al área **Categoría**.

    ![de cascada](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Asegúrese de que Power BI ordenó el gráfico de cascada cronológicamente. En la esquina superior derecha del gráfico, seleccione los puntos suspensivos (...).

    En este ejemplo, seleccionaremos **Orden ascendente**.

    Compruebe que hay un indicador amarillo junto a la izquierda de la opción **Orden ascendente**. Esto indica que se está aplicando la opción seleccionada.

    ![Seleccione Ordenar por > Orden ascendente.](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    Después, vamos a hacer clic en **Ordenar por** y seleccionar **FiscalMonth**. Como en el paso anterior, un indicador amarillo junto a la selección indica cuándo se aplica la opción de selección.

    ![Selección de Ordenar por > MesFiscal](media/power-bi-visualization-waterfall-charts/power-bi-sort-by-fiscal-month.png)

    También puede fijarse en los valores del eje X y comprobar que estén en orden de **Ene** a **Ago**.

    Profundice un poco más para ver lo que está contribuyendo más a los cambios de un mes a otro.

1.  Seleccione **Tienda** > **Territorio** para agregar **Territorio** al cubo **Desglose**.

    ![Se muestra Store en el cubo Desglose](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    De forma predeterminada, Power BI agrega los principales cinco factores que contribuyen a los aumentos o disminuciones por mes. En la imagen siguiente se ha expandido el panel de visualización para incluir más datos. 

    ![Se muestra Store en el cubo Desglose](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    Solo le interesan los dos factores principales.

1. En el panel **Formato**, seleccione **Desglose** y establezca **Número máximo de desgloses** en **2**.

    ![Formato > Desglose](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    Una revisión rápida revela que los territorios de Ohio y Pennsylvania son los factores que más contribuyen al movimiento, negativo y positivo, en el gráfico de cascada.

    ![gráfico de cascada](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

## <a name="next-steps"></a>Pasos siguientes

* [Cambiar cómo interactúan los objetos visuales en un informe de Power BI](../service-reports-visual-interactions.md)

* [Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
