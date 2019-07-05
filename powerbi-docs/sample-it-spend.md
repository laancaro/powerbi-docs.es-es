---
title: 'Ejemplo de análisis de gasto en TI para Power BI: Dar un paseo'
description: 'Ejemplo de análisis de gasto en TI para Power BI: Dar un paseo'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/20/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 3fc93f255d6645ffa6f15676b9a70f24326fcfdc
ms.sourcegitcommit: a2c4f912af1729fdfdf20369bf3eff67c3927eec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67349204"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Ejemplo de análisis de gasto en TI para Power BI: Dar un paseo

## <a name="overview-of-the-it-spend-analysis-sample"></a>Introducción al Ejemplo de análisis de gastos de TI
El paquete de contenido Ejemplo de análisis de gastos de TI contiene un panel, informe y conjunto de datos que analizan los costos planeados frente a los costos reales de un departamento de TI. Esta comparación nos ayuda a comprender la calidad del planeamiento anual y de la investigación de las áreas con enormes desviaciones del planeamiento que ha realizado la empresa. La empresa de este ejemplo pasa por un ciclo de planeamiento anual y produce trimestralmente un nuevo último cálculo que ayuda a analizar los cambios del gasto en TI durante el año fiscal.

![Panel del Ejemplo de análisis de gastos de TI](media/sample-it-spend/it1.png)

Este ejemplo forma parte de una serie en la que se muestra cómo puede usar Power BI con datos, informes y paneles empresariales. Se creó con datos reales de [obviEnce](http://www.obvience.com/) que son anónimos. Los datos están disponibles en varios formatos: paquete de contenido o app, libro de Excel o archivo .pbix de Power BI Desktop. Consulte [Ejemplos de Power BI](sample-datasets.md). 

Este tutorial usa el servicio Power BI y el paquete de contenido Ejemplo de análisis de gastos de TI. Debido a que las experiencias del informe son tan similares, también puede seguir utilizando Power BI Desktop y el archivo .pbix de ejemplo.

## <a name="prerequisites"></a>Requisitos previos

 Para poder usar el ejemplo, primero debe descargarlo como un [paquete de contenido](#get-the-content-pack-for-this-sample), un [archivo .pbix](#get-the-pbix-file-for-this-sample) o un [libro de Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obtención del paquete de contenido de este ejemplo

1. Abra el servicio Power BI (app.powerbi.com), inicie sesión y abra el área de trabajo donde desea guardar el ejemplo.

2. En la esquina inferior izquierda, seleccione **Obtener datos**.
   
   ![Seleccionar Obtener datos](media/sample-datasets/power-bi-get-data.png)
3. En la página **Obtener datos**, seleccione **Ejemplos**.
   
4. Seleccione **Ejemplo de análisis de gastos de TI** y elija **Conectar**.  
  
   ![Conectarse al ejemplo](media/sample-it-spend/it-connect.png)
   
5. Power BI importa el paquete de contenido y agrega un nuevo panel, informe y conjunto de datos en el área de trabajo actual.
   
   ![Entrada de Ejemplo de análisis de gastos de TI](media/sample-it-spend/it-spend-analysis-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obtención del archivo .pbix de este ejemplo

Como alternativa, puede descargar el Ejemplo de análisis de gastos de TI como un [archivo .pbix](http://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix), que está diseñado para su uso con Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obtención del libro de Excel de este ejemplo

Si desea ver el origen de datos de este ejemplo, también está disponible como un [libro de Excel](http://go.microsoft.com/fwlink/?LinkId=529783). El libro contiene hojas de Power View que puede ver y modificar. Para ver los datos sin procesar, habilite los complementos de análisis de datos y, a continuación, seleccione **Power Pivot > Administrar**. Para habilitar los complementos Power View y Power Pivot, vea [Consulta de los ejemplos de Excel desde Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obtener más información.

## <a name="it-spend-analysis-sample-dashboard"></a>Panel Ejemplo de análisis de gastos de TI
Los dos iconos de números de la izquierda del panel, **% de desviación del planeamiento** y el **% de desviación del último cálculo del tercer trimestre**, nos aportan una visión general de la calidad de nuestro trabajo con respecto al planeamiento y el cálculo del último trimestre (LE3 = último cálculo del tercer trimestre). En términos generales, tenemos una desviación del 6 % del planeamiento. Exploremos la causa de esta desviación: cuándo, dónde y en qué categoría.

## <a name="ytd-it-spend-trend-analysis-page"></a>Página de análisis de tendencia de gasto en TI hasta la fecha
Cuando selecciona el icono del panel **Var Plan % by Sales Region** (% de desviación del planeamiento por región de venta), se muestra la página **YTD IT Spend Trend Analysis** (Análisis de tendencias de gasto en TI hasta la fecha) del informe Ejemplo de análisis de gastos de TI. Vemos de un vistazo que tenemos una desviación positiva en Estados Unidos y Europa y una desviación negativa en Canadá, América Latina y Australia. Estados Unidos tiene alrededor de un 6 % de desviación positiva en el último cálculo, mientras que Australia tiene alrededor de un 7 % de desviación negativa en el último cálculo.

![% de planeación de desviación por región de ventas](media/sample-it-spend/it2.png)

Pero si solo miramos este gráfico y sacamos conclusiones podemos equivocarnos. Tenemos que analizar los importes reales para poner las cosas en perspectiva.

1. Seleccione **Australia y Nueva Zelanda** en el gráfico **Var Plan % by Sales Region** (% de desviación del planeamiento por región de venta) y observe el gráfico **Var Plan by IT Area** (Desviación del planeamiento por área de TI).

   ![Página de análisis de tendencia de gasto en TI hasta la fecha](media/sample-it-spend/it3.png)
2. Ahora seleccione **EE. UU.** Para hacerse una idea, Australia supone una parte muy reducida de nuestro gasto general en comparación con EE. Tenga en cuenta que Australia y Nueva Zelanda son una parte muy pequeña de nuestro gasto general en comparación con Estados Unidos.

    A continuación, veamos qué categoría en EE. UU. está causando la desviación.

## <a name="ask-questions-of-the-data"></a>Pregunte sobre los datos
1. Seleccione **Ejemplo de análisis de gasto de TI** en la barra de navegación superior para volver al panel del ejemplo.
2. Seleccione **Pregunte algo sobre sus datos**.
3. En la lista **Preguntas para empezar** del lado izquierdo, seleccione **what is the plan by IT area** (¿cuál es el plan por área de TI).

   ![Gráfico Plan por área de TI](media/sample-it-spend/it-area-chart.png)

4. En el cuadro de preguntas y respuestas, desactive la entrada anterior y escriba *mostrar gráfico de barras de áreas de TI, % de desviación del planeamiento y % de desviación le3*.

   ![Gráfico % de desviación del planeamiento y % de desviación LE3 por área de TI](media/sample-it-spend/it4.png)

   En la primera área de TI, **Infraestructura**, observe que el porcentaje cambió radicalmente entre la desviación del planeamiento inicial y el último cálculo de la desviación del planeamiento.

## <a name="ytd-spend-by-cost-elements-page"></a>Página YTD Spend by Cost Elements (Gasto hasta la fecha por elementos de costo)

1. Vuelva al panel y observe el icono del panel **Variance Plan %, Variance Latest Estimate % - Quarter 3** (% de desviación del planeamiento, % de desviación del último cálculo: trimestre 3).

   ![Icono % de desviación del planeamiento, desviación LE3](media/sample-it-spend/it5.png)

   Tenga en cuenta que el área Infraestructura destaca con una gran desviación positiva para el plan.

1. Seleccione este icono para abrir el informe y ver la página **YTD Spend by Cost Elements** (Gasto hasta la fecha por elementos de costo).
2. Seleccione la barra **Infraestructura** del gráfico **% de desviación del planeamiento y % de desviación del último cálculo del tercer trimestre por área de TI** en la parte inferior derecha y observe los valores de desviación del planeamiento en el gráfico **% de desviación del planeamiento por región de venta** en la parte inferior izquierda.

    ![Página YTD Spend by Cost Elements (Gasto hasta la fecha por elementos de costo)](media/sample-it-spend/it6.png)
3. Seleccione cada nombre por turnos en la segmentación **Cost Element Group** (Grupo de elementos de costo) para encontrar el elemento de costo con la mayor desviación.
4. Tras seleccionar **Otros**, seleccione **Infraestructura** en la segmentación **IT Area** (Área de TI) y seleccione las subáreas en la segmentación **IT Sub Area** (Subárea de TI) para encontrar la subárea con la mayor desviación.  

   Tenga en cuenta la gran desviación para **Redes**. Aparentemente, la empresa decidió proporcionar a sus empleados servicios telefónicos como beneficio, a pesar de que este movimiento no estaba previsto.

## <a name="plan-variance-analysis-page"></a>Página Plan Variance Analysis (Análisis de desviación del planeamiento)

1. Seleccione la pestaña **Plan Variance Analysis** (Análisis de desviación del planeamiento) en la parte inferior de la página.

2. En el gráfico **Var Plan and Var Plan % by Business Area** (Desviación del planeamiento y % de desviación del planeamiento por área de negocio) de la izquierda, seleccione la columna **Infraestructura** para resaltar los valores del área de negocio de la infraestructura en el resto de la página.

    ![Página Plan Variance Analysis (Análisis de desviación del planeamiento)](media/sample-it-spend/it7.png)

   Observe que en el gráfico **Var plan % by Month and Business Area** (% de desviación del planeamiento por mes y área de negocio) el área de negocio de la infraestructura se ha iniciado con una desviación positiva en febrero. Además, observe cómo el valor de desviación del planeamiento para esa área de negocio varía según el país, en comparación con todas las demás áreas de negocio. 

3. Use las segmentaciones **IT Area** (Área de TI) e **IT Sub Area** (Subárea de TI) de la derecha para filtrar los valores del resto de la página y explorar los datos. 

## <a name="edit-the-report"></a>Editar el informe
Seleccione **Editar informe** en la esquina superior izquierda para explorar en la vista de edición:

* Vea cómo se realizan las páginas: los campos de cada gráfico y los filtros de las páginas.
* Agregue páginas y gráficos basándose en los mismos datos.
* Cambie el tipo de visualización para cada gráfico.
* Ancle gráficos de interés al panel.

Este entorno es seguro porque puede elegir no guardar los cambios. Pero si los guarda, en **Obtener datos** podrá obtener una nueva copia de este ejemplo siempre que lo desee.

## <a name="next-steps-connect-to-your-data"></a>Pasos siguientes: Conexión con los datos
Esperamos que este paseo le haya mostrado cómo los paneles de Power BI, Preguntas y respuestas y los informes pueden ofrecer recomendaciones sobre los datos de gasto en TI. Ahora es su turno: conéctese a sus propios datos. Con Power BI puede conectarse a una gran variedad de orígenes de datos. Para obtener más información, consulte [Introducción al servicio Power BI](service-get-started.md).
