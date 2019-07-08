---
title: Gráficos de rectángulos en Power BI
description: Gráficos de rectángulos en Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c28071917dbe5669e6e35bd416236ef7047eb24
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408678"
---
# <a name="treemaps-in-power-bi"></a>Gráficos de rectángulos en Power BI

Los gráficos de rectángulos muestran los datos jerárquicos como un conjunto de rectángulos anidados. Cada nivel de la jerarquía se representa mediante un rectángulo de color (rama) que contiene rectángulos más pequeños (hojas). Power BI basa el tamaño del espacio dentro de cada rectángulo en el valor medido. Los rectángulos se organizan por tamaño desde la esquina superior izquierda (mayor) a la inferior derecha (menor).

![Captura de pantalla de un recuento de productos por categoría y el gráfico de rectángulos de fabricante.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Por ejemplo, si está analizando sus ventas, es posible que tenga ramas de alto nivel para las categorías de ropa: **Urbana**, **Rural**, **Joven** y **Mezcla**. Power BI dividiría los rectángulos de su categoría en hojas, para los fabricantes de ropa dentro de esa categoría. Estas hojas cambiarán de tamaño y se sombrearán en función del número vendido.

En la rama **Urban** anterior, se vendieron mucha ropa de **VanArsdel**. Se vendió menos de **Natura** y **Fama**. Solo se vendieron unos pocos **Leo**. Por lo tanto, la rama **Urban** del gráfico de rectángulos tiene:

* El rectángulo más grande para **VanArsdel** en la esquina superior izquierda.

* Rectángulos ligeramente más pequeños para **Natura** y **Fama**.

* Muchos otros rectángulos para todas las demás prendas vendidas.

* Un pequeño rectángulo para **Leo**.

Podría comparar el número de elementos vendidos en las demás categorías de prendas si comparo el tamaño y el sombreado de cada nodo de hoja; los rectángulos de mayor tamaño y más oscuros significarán un valor mayor.

¿Quiere ver primero a otra persona creando un gráfico de rectángulos? Vaya al minuto 2:10 de este vídeo para ver cómo Amanda crea un gráfico de rectángulos.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>Cuándo usar un gráfico de rectángulos

Los gráficos de rectángulos son una excelente opción:

* Para mostrar grandes cantidades de datos jerárquicos.

* Cuando un gráfico de barras no puede administrar eficazmente un gran número de valores.

* Para mostrar las proporciones entre cada parte y el todo.

* Para mostrar el patrón de la distribución de la medida en cada nivel de categorías de la jerarquía.

* Para mostrar los atributos mediante códigos de color y tamaño.

* Para detectar patrones, valores atípicos, colaboradores más importantes y excepciones.

## <a name="prerequisites"></a>Requisitos previos

* Servicio Power BI o Power BI Desktop

* Informe del Ejemplo de análisis de minoristas

## <a name="get-the-retail-analysis-sample-report"></a>Obtención del ejemplo de análisis de minoristas

Estas instrucciones usan el Ejemplo de análisis de minoristas. La creación de una visualización requiere permisos de edición para el conjunto de datos e informes. Por suerte, los ejemplos de Power BI son todos editables. Si alguien comparte un informe con usted, no podrá crear visualizaciones en informes. Para continuar, abra el [ informe Ejemplo de análisis de minoristas](../sample-datasets.md).

Después de obtener el conjunto de datos **Ejemplo de análisis de minoristas**, puede empezar a trabajar.

## <a name="create-a-basic-treemap"></a>Crear un gráfico de rectángulos básico

Va a crear un informe y agregar un gráfico de rectángulos básico.

1. En **Mi área de trabajo**, seleccione **Conjuntos de datos** > **Crear un informe**.

    ![Captura de pantalla de Conjuntos de datos > Crear un informe.](media/power-bi-visualization-treemaps/power-bi-create-a-report.png)

1. En el panel **Campos**, seleccione la medida **Ventas** > **Ventas del último año**.

   ![Captura de pantalla de Ventas > Ventas del último año seleccionados y el objeto visual resultante.](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)

1. Seleccione el icono de gráfico de rectángulos ![Captura de pantalla del icono del gráfico de rectángulos](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) para convertir el gráfico en un gráfico de rectángulos.

   ![Captura de pantalla del gráfico de rectángulos sin configuración.](media/power-bi-visualization-treemaps/treemapconvertto_new.png)

1. Arrastre **Elemento** > **Categoría** al área **Grupo**.

    Power BI crea un gráfico de rectángulos donde el tamaño de los rectángulos se basa en las ventas totales y el color representa la categoría. En esencia, creó una jerarquía que describe visualmente el tamaño relativo de las ventas totales por categoría. La categoría **Hombres** tiene las ventas más altas y la categoría **Calcetería** tiene los valores más bajos.

    ![Captura de pantalla del gráfico de rectángulos configurado.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Arrastre **Store** > **Chain** al área **Detalles** para completar el gráfico de rectángulos. Ahora puede comparar las ventas del último año por categoría y cadena.

   ![Captura de pantalla del gráfico de rectángulos con Tienda > Cadena agregada a los detalles.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > La saturación de color y los detalles no se pueden usar al mismo tiempo.

1. Mantenga el mouse encima de un área de **Cadena** para que aparezca la información sobre herramientas de la parte de la **Categoría**.

    Por ejemplo, al pasar el cursor sobre **Fashions Direct** en el rectángulo **090-Home**, se muestra la información en pantalla para la parte Fashions Direct de la categoría Home.

   ![Captura de pantalla de la información sobre herramientas de Inicio que aparece.](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)

1. Agregue el gráfico de rectángulos como un [icono de panel (ancle el objeto visual)](../service-dashboard-tiles.md).

1. Guarde [el informe](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Resaltado y filtrado cruzado

Para más información sobre el uso del panel **Filtros**, consulte [Adición de un filtro a un informe](../power-bi-report-add-filter.md).

Al resaltar una **categoría** o un **detalle** en un gráfico de rectángulos, se realiza un resaltado y un filtrado cruzados de las demás visualizaciones de la página de informe, y viceversa. Para poder continuar, agregue algunos objetos visuales a esta página del informe o copie el gráfico de rectángulos en una de las otras páginas de este informe.

1. En el gráfico de rectángulos, seleccione una **categoría** o una **cadena** dentro de una **categoría**. Esto realiza un resaltado cruzado de las demás visualizaciones de la página. Si se selecciona **050-Shoes**, por ejemplo, se muestra que las ventas de zapatos del último año fueron de **$3,640,471** de las cuales **Fashions Direct** representaron **$2,174,185** de dichas ventas.

   ![Captura de pantalla del informe Información general las ventas de la tienda que muestra el resaltado cruzado.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. En el gráfico circular **Last Year Sales by Chain**, seleccione el sector **Fashions Direct**.
   ![GIF de demostración de la característica de filtrado cruzado.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Para administrar cómo se realiza un resaltado y un filtrado cruzados de los gráficos, consulte [Cambiar cómo interactúan los objetos visuales en un informe de Power BI](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Pasos siguientes

* [Gráficos de cascada en Power BI](power-bi-visualization-waterfall-charts.md)

* [Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
