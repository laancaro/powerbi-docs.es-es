---
title: Gráficos de dispersión, de burbujas y de trazado de punto de Power BI
description: Gráficos de dispersión, de trazado de punto y de burbujas de Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8222194359077cb0d88286a33d1c9b2a05f6bd80
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390763"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Gráficos de dispersión, de burbujas y de trazado de punto de Power BI

Un gráfico de dispersión siempre tiene dos ejes de valores con el fin de mostrar un conjunto de datos numéricos en un eje horizontal y otro conjunto de valores numéricos a lo largo de un eje vertical. El gráfico muestra puntos en la intersección de un valor numérico x e y, y combina estos valores en puntos de datos únicos. Power BI puede distribuir estos puntos de datos de manera uniforme o desigual a través del eje horizontal. Depende de los datos que el gráfico representa.

Vea este vídeo para ver como Will crea un gráfico de dispersión y, después, siga los pasos que se indican a continuación para crear uno propio.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

Puede establecer el número de puntos de datos, hasta un máximo de 10 000.  

## <a name="when-to-use-a-scatter-chart-bubble-chart-or-a-dot-plot-chart"></a>Cuándo utilizar un gráfico de dispersión, un gráfico de burbujas o un gráfico de puntos

### <a name="scatter-and-bubble-charts"></a>Gráficos de dispersión y de burbujas

Un gráfico de dispersión muestra la relación entre dos valores numéricos. Un gráfico de burbujas reemplaza los puntos de datos con burbujas, cuyo *tamaño* representa una tercera dimensión adicional de datos.

![Captura de pantalla de un gráfico de burbujas de ejemplo.](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Los gráficos de dispersión son una opción excelente:

* Para mostrar las relaciones entre dos valores numéricos.

* Para trazar dos grupos de números como una serie de coordenadas x e y.

* Para usarlo en lugar de un gráfico de líneas cuando quiere cambiar la escala del eje horizontal.

* Para convertir el eje horizontal en una escala logarítmica.

* Para mostrar datos de la hoja de cálculo que incluyen pares o conjuntos de valores agrupados.

    > [!TIP]
    > En un gráfico de dispersión, puede ajustar las escalas independientes de los ejes para obtener más información acerca de los valores agrupados.

* Para mostrar patrones en grandes conjuntos de datos, por ejemplo, al mostrar los valores atípicos, las agrupaciones y las tendencias lineales o no lineales.

* Para comparar gran cantidad de números de puntos de datos sin tener en cuenta en el tiempo.  Cuantos más datos incluya en un gráfico de dispersión, podrá realizar mejores comparaciones.

Además de lo que los gráficos de dispersión pueden hacer, los gráficos de burbujas son una excelente opción:

* Si los datos tienen tres series de datos que contienen un conjunto de valores.

* Para presentar datos financieros.  Los tamaños de burbuja diferentes son útiles para resaltar visualmente valores específicos.

* Para usarlos con cuadrantes.

### <a name="dot-plot-charts"></a>Gráficos de trazado de puntos

Un gráfico de trazado de puntos es similar a un gráfico de burbujas y a un gráfico de dispersión, pero también se pueden trazar datos numéricos o categóricos a lo largo del eje X.

![Captura de pantalla de un gráfico de trazado de puntos.](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

Es una excelente elección si desea incluir datos de categorías en el eje X.

## <a name="prerequisites"></a>Requisitos previos

* El servicio Power BI

* Informe del Ejemplo de análisis de minoristas

## <a name="create-a-scatter-chart"></a>Crear un gráfico de dispersión

Para continuar, inicie sesión en el [servicio Power BI](https://app.powerbi.com) y abra el informe [Ejemplo de análisis de minoristas](../sample-datasets.md) en la vista [Editar informe](../service-interact-with-a-report-in-editing-view.md).

1. Seleccione ![Captura de pantalla del icono amarillo con el signo más.](media/power-bi-visualization-scatter/power-bi-yellow-plus-icon.png) para crear una página de informe en blanco.

1. En el panel **Campos**, seleccione estos campos:

    * **Ventas** > **Ventas por metro cuadrado**

    * **Ventas** >  **% de varianza de ventas total**

    * **Distrito** > **Distrito**

    ![Captura de pantalla del gráfico de columnas agrupadas, el panel Visualizaciones y el panel Campos con los campos que ha seleccionado indicados.](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

1. En el panel **Visualización**, seleccione ![Captura de pantalla del icono del gráfico de dispersión.](media/power-bi-visualization-scatter/power-bi-scatter-chart-icon.png) Para convertir el gráfico de columnas agrupadas en un gráfico de dispersión.

   ![Captura de pantalla del gráfico de columnas agrupadas que se convierte en un gráfico de dispersión.](media/power-bi-visualization-scatter/power-bi-scatter-new.png)

1. Arrastre **Distrito** desde **Detalles** a **Leyenda**.

    Power BI muestra un gráfico de dispersión que traza el **porcentaje de varianza de ventas total** a lo largo del eje Y y las **ventas por metro cuadrado** en el eje X. Los colores del punto de datos representan distritos:

    ![Captura de pantalla del gráfico de dispersión.](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Ahora vamos a agregar una tercera dimensión.

## <a name="create-a-bubble-chart"></a>Crear un gráfico de burbujas

1. En el panel **Campos**, arrastre **Ventas** > **Ventas de este año** > **Valor** al área **Tamaño**. Los puntos de datos se expanden a volúmenes proporcionales al valor de ventas.

   ![Captura de pantalla del gráfico de dispersión que se convierte en un gráfico de burbujas al agregar el valor de ventas al área Tamaño.](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

1. Mantenga el mouse encima de una burbuja. El tamaño de la burbuja refleja el valor de **Ventas de este año**.

    ![visualización de información sobre herramientas](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

1. Para establecer el número de puntos de datos que se van a mostrar en el gráfico de burbujas, en la sección **Formato** del panel **Visualizaciones**, expanda la **General** y ajuste el **Volumen de datos**.

    ![Captura de pantalla del panel Visualizaciones con el icono Formato, el menú desplegable General y la opción de volumen de datos indicados.](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png)

    Puede establecer el volumen de datos máximo en cualquier número hasta 10 000. Si va a usar cifras más altas, recomendamos probar primero para garantizar un buen rendimiento.

    > [!NOTE]
    > Más puntos de datos pueden significar un tiempo de carga más largo. Si decide publicar informes con límites en el extremo superior de la escala, asegúrese de probar los informes también en la web y en el dispositivo móvil. Desea confirmar que el rendimiento del gráfico se adapta a las expectativas de los usuarios.

1. Puede [aplicar formato a los colores de la visualización, las etiquetas, los títulos, el fondo, etc.](service-getting-started-with-color-formatting-and-axis-properties.md)

    Para [mejorar la accesibilidad](../desktop-accessibility.md), considere la posibilidad de agregar formas de marcador a cada línea. Para seleccionar la forma del marcador, expanda **Formas**, seleccione **Forma de marcador** y seleccione una forma.

    ![Captura de pantalla de la lista desplegable Formas con las opciones de Forma de marcador indicadas.](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

    Puede cambiar la forma del marcador en forma de rombo, triángulo o cuadrado. El empleo de una forma de marcador distinta para cada línea permite que los lectores del informe puedan diferenciar cada una de las líneas (o áreas) con más facilidad.

## <a name="create-a-dot-plot-chart"></a>Creación de un gráfico de trazado de punto

Para crear un gráfico de trazado de punto, sustituya el campo numérico del **eje X** por un campo categórico.

Desde el panel **Eje X**, quite **Ventas por metro cuadrado** y reemplácelo por **Distrito** > **Administrador del distrito**.

![Captura de pantalla de un nuevo trazado de puntos.](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

### <a name="your-scatter-chart-has-only-one-data-point"></a>El gráfico de dispersión solo tiene un punto de datos

¿El gráfico de dispersión tiene solo un punto de datos que agrega todos los valores de los ejes X e Y?  ¿O quizás agrega todos los valores a lo largo de una sola línea horizontal o vertical?

![Captura de pantalla de un gráfico de dispersión con un punto de datos.](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Agregue un campo en el área **Detalles** para indicar a Power BI cómo se deben agrupar los valores. El campo debe ser único para cada punto que quiera trazar. Un campo de identificador o un número de fila simple será suficiente.

![Captura de pantalla de un gráfico de dispersión con RowNum agregado al área Detalles.](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Si sus datos no incluyen eso, cree un campo que concatene los valores X e Y en un valor exclusivo por cada punto:

![Captura de pantalla de un gráfico de dispersión con TempTime agregado al área Detalles.](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Para crear un nuevo campo, [use el Editor de consultas de Power BI Desktop para agregar una columna de índice](../desktop-add-custom-column.md) al conjunto de datos. A continuación, agregue esta columna al área **Detalles** de la visualización.

## <a name="next-steps"></a>Pasos siguientes

* [Muestreo de alta densidad en los gráficos de dispersión de Power BI](desktop-high-density-scatter-charts.md)

* [Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
