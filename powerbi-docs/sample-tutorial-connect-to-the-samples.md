---
title: Usar los ejemplos de Power BI
description: Usar los ejemplos de Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/23/2018
ms.author: mihart
LocalizationGroup: Samples
ms.openlocfilehash: 02c3998a95e7d481ee032513054933f1484ae7f9
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36944615"
---
# <a name="the-power-bi-samples"></a>Ejemplos de Power BI

Se recomienda empezar por el artículo [Conjuntos de datos de ejemplo para Power BI](sample-datasets.md). En ese artículo aprenderá todo acerca de los ejemplos: cómo obtenerlos, dónde guardarlos, cómo usarlos y algunas de las cosas que nos explica cada ejemplo. A continuación, cuando ya conozca los conceptos básicos, vuelva a este Tutorial.   

### <a name="prerequisites"></a>Requisitos previos
Los ejemplos están disponibles para el servicio Power BI y Power BI Desktop. Para continuar, usaremos el ejemplo Retail Analysis.

El paquete de contenido *Ejemplo de análisis de minoristas* que se usa en este tutorial se compone de un panel, un informe y un conjunto de datos.
Para familiarizarse con este paquete de contenido particular y su escenario, quizás quiera [realice un recorrido por el ejemplo de análisis de minoristas](sample-retail-analysis.md) antes de comenzar.

## <a name="about-this-tutorial"></a>Acerca de este tutorial
En este tutorial se explica cómo 
- Importar un paquete de contenido de ejemplo, agregarlo al servicio Power BI y abrir el contenido. Un *paquete de contenido* es un tipo de ejemplo en el que el conjunto de datos está integrado en un panel y un informe. 
-  Abrir un archivo .pbix de ejemplo en Power BI Desktop.


## <a name="samples-and-power-bi-service"></a>Ejemplos y el servicio Power BI

1. Abra el servicio Power BI e inicie sesión en él (app.powerbi.com).
2. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo. Si no ve la opción **Obtener datos**, seleccione el ![icono de tres barras](media/sample-tutorial-connect-to-the-samples/expand-nav.png) para expandir el panel de navegación.
   
   ![Icono Obtener datos](media/sample-tutorial-connect-to-the-samples/pbi_getdata.png)
5. Seleccione **Ejemplos**.  
   
   ![Botón Ejemplos](media/sample-tutorial-connect-to-the-samples/pbi_samplesdownload.png)
6. Seleccione el *Ejemplo Análisis de venta directa* y elija **Conectar**.   
   
   ![Botón amarillo Conectar](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-exactly-was-imported"></a>¿Qué se importó exactamente?
Con los paquetes de contenido de ejemplo, cuando selecciona **Conectar**, Power BI realmente crea una copia de ese paquete de contenido y la almacena en la nube. Como la persona que creó el paquete de contenido incluyó un conjunto de datos, un informe y un panel, eso es justamente lo que obtendrá si hace clic en **Conectar**. 

1. Power BI crea el nuevo panel y lo muestra en la pestaña **Paneles**. El asterisco amarillo le indicará que es nuevo.
   
   ![Mensaje de proceso correcto](media/sample-tutorial-connect-to-the-samples/power-bi-new-dashboard.png)
2. Abra la pestaña **Informes**.  Aquí verá un nuevo informe denominado *Ejemplo Análisis de venta directa*.
   
   ![Cuadro fucsia alrededor de Ejemplo de análisis de venta directa y una estrella amarilla](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Compruebe la pestaña **Conjuntos de datos**.  Allí verá un conjunto de datos nuevo.
   
   ![Cuadro fucsia alrededor de Ejemplo de análisis de venta directa](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Explorar el contenido nuevo
Ahora, explore el panel, el conjunto de datos y los informes por su cuenta. Hay muchas maneras diferentes de navegar por los paneles, informes y conjuntos de datos, pero solo una de ellas se describe a continuación.  

> [!TIP]
> ¿Quiere primero algo de orientación?  Consulte el [paseo por el ejemplo de análisis de venta directa](sample-retail-analysis.md) para ver un tutorial detallado sobre este ejemplo.
> 
> 

1. Vuelva a la pestaña **Paneles** y seleccione el panel *Ejemplo Análisis de venta directa* para abrirlo.    
   
   ![Pestaña Paneles seleccionada](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards.png)
2. El panel se abre.  Cuenta con una serie de iconos de visualización.
   
   ![Panel con un objeto visual resaltado](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)
3. Seleccione uno de los iconos para abrir el informe subyacente.  En este ejemplo, se seleccionará el gráfico de áreas (resaltado en rosa en la imagen anterior). El informe se abre en la página que contiene ese gráfico de áreas.
   
    ![Página del informe con un objeto visual coincidente resaltado](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Si el icono se ha creado mediante [Preguntas y respuestas de Power BI](power-bi-q-and-a.md), se abrirá la página de Preguntas y respuestas en su lugar. Si el icono estaba [anclado desde Excel](service-dashboard-pin-tile-from-excel.md), Excel Online se habría abierto en Power BI.
   > 
   > 
1. De vuelta en la pestaña **Conjuntos de datos**, tiene varias opciones para explorar el conjunto de datos.  No podrá abrirla y ver todas las filas y columnas (como podría hacer en Power BI Desktop o Excel).  Cuando un usuario comparte un paquete de contenido con sus compañeros, normalmente lo que desea es compartir la información, no dar a sus compañeros acceso directo a los datos. Pero eso no significa que no pueda explorar el conjunto de datos.  
   
   ![Pestaña Conjuntos de datos](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon2.png)
   
   * Una manera de explorarlo es mediante la creación de sus propios informes y visualizaciones desde cero.  Seleccione el icono de gráfico ![Icono de informe](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) para abrir el conjunto de datos en el modo de edición del informe.
     
       ![Informe completamente nuevo](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)
   * Otra manera de explorar el conjunto de datos es ejecutar [Información rápida](service-insights.md). Seleccione el botón de puntos suspensivos (...) y elija **Obtener información**. Cuando la información ya está lista, seleccione **Ver información**.
     
       ![Informe de conclusiones](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="samples-and-power-bi-desktop"></a>Ejemplos y el Power BI Desktop 
Al abrir por primera vez el archivo PBIX de ejemplo, se muestra en la vista de informe, donde se puede explorar, crear y modificar cualquier número de páginas del informe con visualizaciones. La vista de informes proporciona prácticamente la misma experiencia de diseño que la vista de edición de un informe en el servicio de Power BI. Puede mover visualizaciones, copiar y pegar, combinar, etc.

La diferencia entre ellas es que al usar Power BI Desktop, también puede trabajar con las consultas y modelar los datos para asegurarse de que los datos admiten las mejores perspectivas en los informes. A continuación, puede guardar el archivo de Power BI Desktop donde quiera, ya sea en la unidad local o en la nube.

1. Abra el [archivo .pbix del ejemplo Retail Analysis](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) en Power BI Desktop. 

    ![Ejemplo abierto en la vista de informe de Power BI](media/sample-tutorial-connect-to-the-samples/power-bi-samples-desktop.png)

1. El archivo se abre en la vista de informe. ¿Se ha fijado en las cuatro pestañas de la parte inferior del editor de informes? Esto significa que hay cuatro páginas en este informe y la página "New Stores" está seleccionada. 

    ![Vista de cerca de las pestañas de la parte inferior y "New Stores" resaltadas](media/sample-tutorial-connect-to-the-samples/power-bi-sample-tabs.png).

3. Para profundizar en el editor de informes, consulte [Un paseo por el editor de informes](service-the-report-editor-take-a-tour.md).

## <a name="what-exactly-was-imported"></a>¿Qué se importó exactamente?
Cuando abre el archivo PBIX de ejemplo en Desktop, Power BI realmente crea una copia de esos datos y los almacena en la nube. Desde Desktop, tendrá acceso al informe ***y al conjunto de datos subyacente***. Cuando se carguen los datos, Power BI Desktop intentará buscar y crear relaciones automáticamente.  

1. Cambie a la [vista de datos](desktop-data-view.md) seleccionando el icono de tabla ![Icono de tabla](media/sample-tutorial-connect-to-the-samples/power-bi-data-icon.png).
 
    ![Vista de datos de Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-sample-data.png)

    La visa de datos le ayuda a inspeccionar, explorar y comprender los datos en el modelo de Power BI Desktop. Es diferente de cómo ve las tablas, columnas y datos en el Editor de consultas. Con la vista de datos, ve los datos después de que se hayan cargado en el modelo.

    Cuando se están modelando los datos, a veces desea ver lo que hay realmente en una tabla o columna sin crear un elemento visual en el lienzo del informe, normalmente justo debajo del nivel de fila. Esto es especialmente cierto cuando crea columnas calculadas y medidas, o tiene que identificar un tipo de datos o una categoría de datos.

1. Cambie a la [vista de relaciones](desktop-relationship-view.md) seleccionando el icono ![Icono con el aspecto de tres cuadros conectados](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-relationship-icon.png).
 
    ![Vista de relaciones en Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-relationships.png)

    La vista de relaciones muestra todas las tablas, columnas y relaciones en el modelo. Desde aquí puede ver, cambiar y crear relaciones.

## <a name="explore-your-new-content"></a>Explorar el contenido nuevo
Ahora, explore el conjunto de datos, las relaciones y los informes por su cuenta. Para obtener ayuda acerca de cómo empezar, consulte [Introducción a Power BI Desktop](desktop-getting-started.md).    


## <a name="next-steps"></a>Pasos siguientes
[Conceptos básicos de Power BI](service-basic-concepts.md)

[Ejemplos del servicio Power BI](sample-datasets.md)

[Orígenes de datos de Power BI](service-get-data.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

