---
title: 'Ejemplo de análisis de oportunidades para Power BI: Dar un paseo'
description: 'Ejemplo de análisis de oportunidades para Power BI: Dar un paseo'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: d871fa15c999e5b6c83b0334d6c978b2ba3c9870
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858703"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Ejemplo de análisis de oportunidades para Power BI: Dar un paseo

El paquete de contenido del ejemplo del análisis de oportunidades contiene un panel, un informe y un conjunto de datos para una empresa de software que tiene dos canales de ventas: el de la *venta directa* y *a través de asociados*. La jefa de ventas creó este panel para hacer un seguimiento de las oportunidades y los ingresos por región, tamaño del acuerdo y canal.

Este ejemplo se basa en dos medidas de ingresos:

* Ingresos: la estimación de un vendedor con respecto a cuáles serán los ingresos.
* Ingresos factorizados: se calculan aplicando la fórmula Ingresos x % de probabilidad y se aceptan como predicción más exacta de los ingresos por ventas reales. La *fase de ventas* actual del acuerdo es el factor que determina la probabilidad:
  * Cliente potencial: 10 %  
  * Aprobación: 20 %  
  * Solución: 40 %  
  * Propuesta: 60 %  
  * Finalización: 80 %

![Panel del ejemplo de análisis de oportunidades](media/sample-opportunity-analysis/opportunity1.png)

Este ejemplo forma parte de una serie en la que se muestra cómo puede usar Power BI con datos, informes y paneles empresariales. Se ha creado mediante [obviEnce](http://www.obvience.com/) con datos reales anonimizados. Los datos están disponibles en varios formatos: paquete de contenido, archivo .pbix de Power BI Desktop o libro de Excel. Consulte [Ejemplos de Power BI](sample-datasets.md). 

En este tutorial se explora el paquete de contenido del ejemplo de análisis de oportunidades del servicio Power BI. Dado que la experiencia de informes es similar en Power BI Desktop y en el servicio, también puede proceder con el archivo .pbix de ejemplo de Power BI Desktop. 

Para explorar los ejemplos de Power BI Desktop, no necesita una licencia de Power BI. Si no tiene una licencia de Power BI Pro, puede guardar el ejemplo en Mi área de trabajo del servicio Power BI. 

## <a name="get-the-sample"></a>Obtención del ejemplo

Para poder usar el ejemplo, primero debe descargarlo como un [paquete de contenido](#get-the-content-pack-for-this-sample), un [archivo .pbix](#get-the-pbix-file-for-this-sample) o un [libro de Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obtención del paquete de contenido de este ejemplo

1. Abra el servicio Power BI (app.powerbi.com), inicie sesión y abra el área de trabajo donde desea guardar el ejemplo. 

    Si no tiene una licencia de Power BI Pro, puede guardar el ejemplo en Mi área de trabajo.

2. En la esquina inferior izquierda, seleccione **Obtener datos**.

    ![Seleccionar Obtener datos](media/sample-datasets/power-bi-get-data.png)
3. En la página **Obtener datos**, seleccione **Ejemplos**.

4. Seleccione **Ejemplo de análisis de oportunidades** y, luego, elija **Conectar**.  

   ![Conectarse al ejemplo](media/sample-opportunity-analysis/opportunity-connect.png)
5. Power BI importa el paquete de contenido y agrega un panel, un informe y un conjunto de datos nuevos en el área de trabajo actual.

   ![Entrada del ejemplo de análisis de oportunidades](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Obtención del archivo .pbix de este ejemplo

Como alternativa, puede descargar el Ejemplo de análisis de oportunidades como un [archivo .pbix](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix), que está diseñado para su uso con Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obtención del libro de Excel de este ejemplo

Si desea ver el origen de datos de este ejemplo, también está disponible como un [libro de Excel](https://go.microsoft.com/fwlink/?LinkId=529782). El libro contiene hojas de Power View que puede ver y modificar. Para ver los datos sin procesar, habilite los complementos de análisis de datos y, a continuación, seleccione **Power Pivot > Administrar**. Para habilitar los complementos Power View y Power Pivot, vea [Consulta de los ejemplos de Excel desde Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obtener más información.

## <a name="what-is-our-dashboard-telling-us"></a>¿Qué indica el panel?
La jefa de ventas creó un panel para realizar el seguimiento de las métricas que considera más importantes. Si encuentra algo interesante, puede seleccionar un icono para examinar los datos:

- Los ingresos de la empresa ascienden a los 2.000 millones de dólares y, los ingresos factorizados, a 461.
- El recuento de oportunidades y los ingresos siguen un patrón de embudo conocido, en el que los totales van disminuyendo con cada una de las fases subsiguientes.
- La mayoría de nuestras oportunidades se encuentran en la región Este.
- Las oportunidades grandes generan más ingresos que las medianas o las pequeñas.
- Los acuerdos a través de asociados de gran tamaño generan más ingresos: USD 8 millones en promedio en comparación con los USD 6 millones correspondientes a las ventas directas.

Como el esfuerzo para cerrar un acuerdo es el mismo, independientemente de si este se clasifica como grande, mediano o pequeño, nuestra empresa debe analizar los datos para obtener más información sobre las grandes oportunidades.

1. En el área de trabajo donde guardó el ejemplo, abra la pestaña **Paneles** y elija el panel **Ejemplo de análisis de oportunidades**.

2. Seleccione el icono **Opportunity Count by Partner Driven, Sales Stage** (Recuento de oportunidades por fase de ventas, controladas por asociado) para abrir la primera página del informe Ejemplo de análisis de oportunidad. 

    ![Icono Recuento de oportunidades por fase de ventas, controladas por asociado](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>Consultar las páginas del informe

Para ver cada página del informe, seleccione las pestañas de página que aparecen en la parte inferior.

### <a name="opportunity-count-overview-page"></a>Página Información general sobre el recuento de oportunidades
![Página Recuento de oportunidades](media/sample-opportunity-analysis/opportunity3.png)

Tenga en cuenta los siguientes detalles:
* El Este es la mayor región en cuanto a recuentos de oportunidades.  
* En el gráfico circular **Recuento de oportunidades por región**, seleccione cada región por separado para filtrar la página por región. En cada una de las regiones, observe que los asociados buscan oportunidades considerablemente mayores.   
* El gráfico de columnas **Recuento de oportunidades por su tamaño y por el control de los asociados** muestra que son estos quienes controlan la mayor parte de las grandes oportunidades, y que no ocurre lo mismo con las pequeñas y medianas oportunidades.
* En el gráfico de barras **Recuento de oportunidades por fase de ventas**, seleccione cada **fase de ventas** por separado para ver la diferencia en el recuento regional. Tenga en cuenta que si bien la región Este tiene el mayor recuento de oportunidades, las tres regiones en las fases de ventas de Solución, Propuesta y Finalización tienen recuentos comparables. Este resultado implica que cerramos un mayor porcentaje de acuerdos en las regiones Central y Oeste.

### <a name="revenue-analysis-page"></a>Página Análisis de ingresos
En esta página se examinan los datos de manera similar, pero usa una perspectiva de los ingresos (no de los recuentos).  

![Página Información general de los ingresos](media/sample-opportunity-analysis/opportunity4.png)

Tenga en cuenta los siguientes detalles:
* La región Este es la más grande, no solo en términos del recuento de oportunidades, sino también de los ingresos.  
* Si filtra el gráfico **Ingresos por fase de ventas y controlados por asociado** seleccionando **Sí** para **Controlados por asociado**, verá ingresos de USD 1500 millones e ingresos factorizados de USD 294 millones. Compare estos montos con los USD 644 millones y los USD 166 millones de los ingresos no controlados por los asociados. 
* Los ingresos promedio de las cuentas grandes son mayores (8 millones) en el caso de las oportunidades controladas por los asociados, en comparación con los 6 millones de una empresa no controlada por los asociados.  
* En el caso de los negocios controlados por los asociados, los ingresos promedio de las grandes oportunidades casi duplican los correspondientes a las oportunidades de tamaño medio.  
* Los ingresos medios de los negocios pequeños y medianos son comparables en ambos tipos de negocios (los que están controlados por los asociados y los que no).   

Claramente, nuestros asociados están obteniendo mejores resultados con las ventas a los clientes que quienes no son asociados. Tendría sentido canalizar más acuerdos a través de nuestros asociados.

### <a name="opportunity-count-by-region-and-stage"></a>Recuento de oportunidades por región y fase
En esta página del informe se analizan los datos de una manera similar a cómo se analizan los datos en la página anterior, pero se desglosan por región y fase. 

![Página Recuentos por región y fase](media/sample-opportunity-analysis/opportunity5.png)

Tenga en cuenta los siguientes detalles:
* Si selecciona **Este** en el gráfico circular **Recuento de oportunidades por región** para filtrar por la región Este, verá que las oportunidades de esta región se dividen casi por igual entre las oportunidades controladas por los asociados y las que no están controladas por los asociados.
* Las grandes oportunidades son más comunes en la región Central, las pequeñas en la región Este y, las medianas, en la región Oeste.

### <a name="upcoming-opportunities-by-month-page"></a>Página Próximas oportunidades por mes
En esta página se analizan factores similares, pero desde una perspectiva de fecha y hora. 
 
![Página Próximas oportunidades](media/sample-opportunity-analysis/opportunity6.png)

Nuestra directora financiera usa esta página para administrar la carga de trabajo. La posibilidad de consultar las oportunidades de ingresos por fase de ventas y mes le permite efectuar una planeación adecuada.

Tenga en cuenta los siguientes detalles:
* Los ingresos promedio más elevados son los de la fase de finalización de venta. Es prioritario cerrar estos acuerdos.
* Si se filtra por mes (seleccionando un mes en la segmentación **Mes**), verá que en enero hay una alta proporción de grandes acuerdos en la fase de finalización de ventas con ingresos factorizados de USD 75 millones. Por otro lado, en febrero se observa la mayor parte de los acuerdos medios en las fases de solución y propuesta.
* En general, las cifras de los ingresos factorizados fluctúan en función de la fase de ventas, el número de oportunidades y el tamaño del acuerdo. Agregue filtros para estos factores mediante el panel **Filtrar** que se encuentra a la derecha para obtener información detallada.

## <a name="next-steps-connect-to-your-data"></a>Pasos siguientes: Conexión con los datos
Este entorno es seguro porque puede elegir no guardar los cambios. Pero si los guarda, en **Obtener datos** podrá obtener una nueva copia de este ejemplo siempre que lo desee.

Esperamos que este paseo le haya mostrado cómo los paneles de Power BI, Preguntas y respuestas y los informes pueden ofrecer recomendaciones sobre los datos de ejemplo. Ahora es su turno: conéctese a sus propios datos. Con Power BI puede conectarse a una gran variedad de orígenes de datos. Para obtener más información, consulte [Introducción al servicio Power BI](service-get-started.md).

