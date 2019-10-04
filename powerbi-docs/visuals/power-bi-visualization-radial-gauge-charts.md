---
title: Gráficos de medidor radial en Power BI
description: Gráficos de medidor radial en Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 020d7edcf6bc499623df93a9def30285a37cffc6
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194190"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Gráficos de medidor radial en Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Un gráfico de medidor radial tiene un arco circular y muestra un único valor que mide el progreso hacia un objetivo o un indicador clave de rendimiento (KPI). La línea (o *aguja*) representa el objetivo o valor de destino. El sombreado representa el progreso hacia ese objetivo. El valor dentro del arco representa el valor del progreso. Power BI distribuye todos los valores posibles por igual a lo largo del arco, del mínimo (valor más a la izquierda) al máximo (valor más a la derecha).

![Captura de pantalla de medidor radial.](media/power-bi-visualization-radial-gauge-charts/gauge-m.png)

En este ejemplo, es un vendedor de automóviles y realiza el seguimiento de la media de ventas por mes del equipo de ventas. La aguja representa un objetivo de ventas de 140 automóviles. La media mínima posible de ventas es 0 y la máxima es 200.  El sombreado azul muestra que la media del equipo de ventas de este mes es de aproximadamente 120. Por suerte, hay todavía otra semana para alcanzar el objetivo.

Puede ver otro en el que Will muestra cómo crear objetos visuales de métricas individuales: medidores, tarjetas y KPI.
   > [!NOTE]
   > En este vídeo se usa una versión anterior de Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>Cuándo usar un medidor radial

Los medidores radiales son una excelente opción para:

* Mostrar el progreso hacia un objetivo.

* Representar una medida percentil, como un KPI.

* Mostrar el estado de una única medida.

* Mostrar la información que puede explorar y comprender rápidamente.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa el [archivo de Excel del Ejemplo financiero](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Obtener datos** > **Excel**.
   
2. Busque la copia del **archivo de Excel del Ejemplo financiero**.

1. Abra el **archivo de Excel del Ejemplo financiero** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccione **operaciones financieras** y **Sheet1**.

1. Haga clic en **Cargar**.

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.



## <a name="create-a-basic-radial-gauge"></a>Crear un medidor radial básico

### <a name="step-1-create-a-gauge-to-track-gross-sales"></a>Paso 1: Crear un medidor para realizar un seguimiento de las ventas brutas

1. Inicio en una página de informe en blanco

1. En el panel **Campos**, seleccione **Ventas brutas**.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue-new.png)

1. Cambie la agregación a **Media**.

   ![Captura de pantalla del panel Campos con las ventas brutas y el promedio agregado indicados.](media/power-bi-visualization-radial-gauge-charts/changetoaverage-new.png)

1. Seleccione el icono del medidor ![Captura de pantalla del icono del medidor.](media/power-bi-visualization-radial-gauge-charts/gaugeicon-new.png) para convertir el gráfico de columnas en un gráfico de medidor.

    ![Captura de pantalla del gráfico de medidor.](media/power-bi-visualization-radial-gauge-charts/gauge-no-target.png)

    Dependiendo de cuándo descargue el archivo **Ejemplo financiero**, es posible que vea números que no coinciden con estos números.

    > [!TIP]
    > De forma predeterminada, Power BI crea un gráfico de medidor, donde se supone que el valor actual (en este caso, **Media de ventas brutas**) está en el punto medio del medidor. Dado que el valor de la **media de ventas brutas** es de 182,76 USD, el valor inicial (mínimo) se establece en 0 y el valor final (máximo) se establece en el doble del valor actual.

### <a name="step-3-set-a-target-value"></a>Paso 3: Establecer un valor de destino

1. Arrastre **COGS** desde el panel **Campos** al área **Valor de destino**.

1. Cambie la agregación a **Media**.

   Power BI agrega una aguja para representar el valor del objetivo de **145 480 USD**.

   ![Captura de pantalla del gráfico de medidor con el promedio de COGS agregado.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress-new.png)

    Observe que hemos superado nuestro objetivo.

   > [!NOTE]
   > También puede escribir manualmente un valor de objetivo. Consulte la sección [Uso de las opciones de formato manual para establecer los valores mínimo, máximo y de destino](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Paso 4: Establecer un valor máximo

En el paso 2, Power BI usó el campo **Valor** para establecer automáticamente el valor mínimo y el valor máximo. ¿Qué ocurre si desea establecer su propio valor máximo? Supongamos que, en lugar de usar el doble del valor actual como valor máximo posible, desea establecerlo en la cifra de ventas brutas más alta del conjunto de datos.

1. Arrastre **Ventas brutas** desde el panel **Campos** al **Valor máximo**.

1. Cambie la agregación a **Máximo**.

   ![Captura de pantalla del panel Campos con las ventas brutas y el agregado máximo indicados.](media/power-bi-visualization-radial-gauge-charts/setmaximum-new.png)

   Se vuelve a dibujar el medidor con un nuevo valor final, 1,21 millones en ventas brutas.

   ![Captura de pantalla del gráfico de medidor finalizado.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Paso 5: Guardar el informe

1. [Guarde el informe](../service-report-save.md).

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Uso de las opciones de formato manual para establecer los valores mínimo, máximo y de destino

1. Quite **Ventas brutas máximas** del área **Valor máximo** .

1. Seleccione el icono del rodillo de pintura para abrir el panel **Formato**.

   ![Captura de pantalla del gráfico de medidor y el panel Formato con el icono de rodillo indicado.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Expanda el **Eje medidor** y escriba valores para **Mín.** y **Máx**.

    ![Captura de pantalla de las opciones de Eje medidor.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Desactive la opción **COGS** en el panel **Campos** para quitar el valor de destino.

    ![Captura de pantalla de la opción COGS borrada.](media/power-bi-visualization-radial-gauge-charts/pbi-remove-target.png)

1. Cuando el campo **Destino** aparezca debajo del **Eje medidor**, escriba un valor.

     ![Captura de pantalla de las opciones de Eje medidor con el objetivo indicado.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Si quiere, puede seguir dando formato al gráfico de medidor.

Una vez que haya terminado con estos pasos, tendrá un gráfico de medidor que se parece a este:

![Captura de pantalla del gráfico de medidor final.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Paso siguiente

* [Objetos visuales del indicador clave de rendimiento (KPI)](power-bi-visualization-kpi.md)

* [Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
