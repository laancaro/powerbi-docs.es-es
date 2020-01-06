---
title: 'Ejemplo de análisis de adquisiciones: Dar un paseo'
description: 'Ejemplo de análisis de adquisiciones para Power BI: Dar un paseo'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 0998ebec15a4e02262ab54a3b08593a65f37af4e
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "73873874"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Ejemplo de análisis de adquisiciones para Power BI: Dar un paseo

El paquete de contenido de ejemplo de análisis de adquisiciones contiene un panel, un informe y un conjunto de datos que permiten analizar el gasto de un fabricante en proveedores por categoría y ubicación. En el ejemplo, exploramos estas áreas:

* Quiénes son los mejores proveedores
* En qué categorías se realiza el mayor gasto
* Qué proveedores nos ofrecen el mayor descuento y cuándo

![Panel del Ejemplo de análisis de adquisiciones](media/sample-procurement/procurement1.png)

Este ejemplo forma parte de una serie en la que se muestra cómo puede usar Power BI con datos, informes y paneles empresariales. Se ha creado mediante [obviEnce](http://www.obvience.com/) con datos reales anonimizados. Los datos están disponibles en varios formatos: paquete de contenido, archivo .pbix de Power BI Desktop o libro de Excel. Consulte [Ejemplos de Power BI](sample-datasets.md). 

En este tutorial se explora el paquete de contenido de ejemplo de análisis de adquisiciones del servicio Power BI. Dado que la experiencia de informes es similar en Power BI Desktop y en el servicio, también puede proceder con el archivo .pbix de ejemplo de Power BI Desktop. 

Para explorar los ejemplos de Power BI Desktop, no necesita una licencia de Power BI. Si no tiene una licencia de Power BI Pro, puede guardar el ejemplo en Mi área de trabajo del servicio Power BI. 

## <a name="get-the-sample"></a>Obtención del ejemplo

Para poder usar el ejemplo, primero debe descargarlo como un [paquete de contenido](#get-the-content-pack-for-this-sample), un [archivo .pbix](#get-the-pbix-file-for-this-sample) o un [libro de Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obtención del paquete de contenido de este ejemplo

1. Abra el servicio Power BI (app.powerbi.com), inicie sesión y abra el área de trabajo donde desea guardar el ejemplo. 

    Si no tiene una licencia de Power BI Pro, puede guardar el ejemplo en Mi área de trabajo.

2. En la esquina inferior izquierda, seleccione **Obtener datos**.

    ![Seleccionar Obtener datos](media/sample-datasets/power-bi-get-data.png)
3. En la página **Obtener datos**, seleccione **Ejemplos**.

4. Seleccione el **Ejemplo de análisis de adquisiciones** y elija **Conectar**.  
  
   ![Conectarse al ejemplo](media/sample-procurement/procurement1a.png)
   
5. Power BI importa el paquete de contenido y agrega un panel, un informe y un conjunto de datos nuevos en el área de trabajo actual.
   
   ![Entrada del Ejemplo de análisis de adquisiciones](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obtención del archivo .pbix de este ejemplo

Como alternativa, puede descargar el Ejemplo de análisis de adquisiciones como un [archivo .pbix](https://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix), que está diseñado para su uso con Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Obtención del libro de Excel de este ejemplo

Si desea ver el origen de datos de este ejemplo, también está disponible como un [libro de Excel](https://go.microsoft.com/fwlink/?LinkId=529784). El libro contiene hojas de Power View que puede ver y modificar. Para ver los datos sin procesar, habilite los complementos de análisis de datos y, a continuación, seleccione **Power Pivot > Administrar**. Para habilitar los complementos Power View y Power Pivot, vea [Consulta de los ejemplos de Excel desde Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obtener más información.


## <a name="spending-trends"></a>Tendencias de gastos
Veamos primero las tendencias de gastos por categoría y ubicación.  

1. En el área de trabajo donde guardó el ejemplo, abra la pestaña **Paneles** y elija el panel **Ejemplo de análisis de adquisiciones**. 
2. Seleccione el icono del panel **Total Invoice by Country/Region**, que se abre en la página **Spend Overview** del informe **Ejemplo de análisis de adquisiciones**.

    ![Página Spend Overview](media/sample-procurement/procurement2.png)

Tenga en cuenta los siguientes detalles:

* En el gráfico de líneas **Total Invoice by Month and Category**, la categoría **Direct** presenta gastos constantes, **Logistics** experimenta un pico en diciembre y **Other**, un pico en febrero.
* En el mapa **Total Invoice by Country/Region**, la mayor parte de los gastos corresponden a Estados Unidos.
* En el gráfico de columnas **Total Invoice by Sub Category**, las categorías que muestran unos gastos mayores son **Hardware** y **Indirect Goods & Services**.
* En el gráfico de barras **Total Invoice by Tier**, la mayor parte de los negocios se llevan a cabo con nuestros proveedores de nivel 1 (10 principales). De este modo, podremos administrar mejor las relaciones con proveedores.

## <a name="spending-in-mexico"></a>Gastos de México
Vamos a examinar las áreas de gasto en México.

1. En el mapa **Total Invoice by Country/Region**, seleccione la burbuja **Mexico**. Observe que, en el gráfico de columnas **Total Invoice by Sub Category**, la mayoría del gasto se encuentra en la subcategoría **Indirect Goods & Services**.

   ![Seleccione Mexico en la página de información general de gasto](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Explore en profundidad la columna **Indirect Goods & Services**:

   * En el gráfico **Total Invoice by Sub Category**, seleccione la flecha de exploración en profundidad ![Flecha de exploración en profundidad](media/sample-procurement/pbi_drilldown_icon.png), que encontrará en la esquina superior derecha del gráfico.
   * Seleccione la columna **Indirect Goods & Services**.

      Como puede ver, sin duda el gasto más alto es el de la subcategoría **Sales & Marketing**.
   * Seleccione **Mexico** en el mapa de nuevo.

      Para México, el mayor gasto es el de la subcategoría **Maintenance & Repair**.

      ![Exploración en profundidad de Indirect Goods & Services para México](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Seleccione la flecha arriba de la esquina superior izquierda del gráfico para volver a agrupar los datos.
4. Seleccione de nuevo la flecha de exploración en profundidad para desactivar la opción en cuestión.  
5. En el panel de navegación superior, seleccione **Ejemplo de análisis de adquisiciones** para volver al panel.

## <a name="evaluate-different-cities"></a>Evaluar las diferentes ciudades
Se puede usar el resaltado para evaluar diferentes ciudades.

1. Seleccione el icono del panel **Total Invoice, Discount % By Months**, que se abre en la página **Discount analysis** del informe **Ejemplo de análisis de adquisiciones**.
2. En el gráfico de rectángulos **Total Invoice by City**, seleccione cada ciudad en cuestión para ver una comparación. Observe que casi todas las facturas de Miami son de proveedores del nivel 1.

   ![Ciudad frente a porcentaje de descuento por nivel](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Descuentos de proveedor
Vamos a examinar los descuentos disponibles de los proveedores, así como los períodos de tiempo en los que conseguimos mayores descuentos:
* ¿Los descuentos son diferentes cada mes o no cambian?
* ¿Obtienen algunas ciudades más descuentos que otras?

![Página Discount analysis](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>Descuento por mes
Si examina el gráfico combinado **Total Invoice and Discount % by Month** , vemos que febrero es el mes más ocupado, mientras que septiembre es el menos ocupado. 

Examine el porcentaje de descuento durante estos meses: cuando se aumenta el volumen, el descuento se reduce; cuando queda poco volumen, el descuento aumenta. Cuanto más necesitemos el descuento, peor es el trato que obtenemos.

![Gráfico de porcentaje de total de facturas y descuento por mes](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Descuento por ciudad
Otra área para explorar es el descuento por ciudad. Seleccione cada ciudad en el gráfico de rectángulos y vea cómo cambian los demás gráficos:

* San Luis tuvo un pico grande en el total de facturas en febrero y una gran caída en ahorros por descuento en abril.
* Ciudad de México tiene el mayor porcentaje de descuento (11,05 %), mientras que Atlanta tiene el menor (0,08 %).

![Gráficos de descuento para Ciudad de México](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Editar el informe
Seleccione **Editar informe** en la esquina superior izquierda y examínelo en la vista de edición:

* Vea cómo se crean las páginas.
* Agregue páginas y gráficos basados en los mismos datos.
* Cambie el tipo de visualización de un gráfico; por ejemplo, cambie el gráfico de rectángulos por un gráfico de anillos.
* Puede anclar gráficos al panel.

## <a name="next-steps-connect-to-your-data"></a>Pasos siguientes: Conexión con los datos
Este entorno es seguro porque puede elegir no guardar los cambios. Pero si los guarda, en **Obtener datos** podrá obtener una nueva copia de este ejemplo siempre que lo desee.

Esperamos que este paseo le haya mostrado cómo los paneles de Power BI, Preguntas y respuestas y los informes pueden ofrecer recomendaciones sobre los datos de ejemplo. Ahora es su turno: conéctese a sus propios datos. Con Power BI puede conectarse a una gran variedad de orígenes de datos. Para obtener más información, consulte [Introducción al servicio Power BI](service-get-started.md).

