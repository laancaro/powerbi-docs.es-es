---
title: Personalización de las propiedades de los ejes X e Y
description: Personalización de las propiedades de los ejes X e Y
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3bfe84acdf73fcb5ace791c9a84943262d0f73ab
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390246"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Personalización de las propiedades de los ejes X e Y

En este tutorial, aprenderá multitud de formas diferentes de personalizar los ejes X e Y de los objetos visuales. No todos los objetos visuales tienen ejes. Por ejemplo, los gráficos circulares no tienen ejes. Y las opciones de personalización varían de un objeto visual a otro. Hay demasiadas opciones para tratar en un único artículo, por tanto eche un vistazo a algunas de las personalizaciones de ejes más utilizadas y familiarícese con el panel **Formato** del objeto visual del lienzo de informes de Power BI.  

> [!NOTE]
> Esta página se aplica al servicio Power BI y a Power BI Desktop. Estas personalizaciones, que están disponibles cuando se selecciona el icono **Formato** (el icono de rodillo ![Captura de pantalla del icono de rodillo](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)), también están disponibles en Power BI Desktop.

Vea a Amanda personalizar los ejes X e Y. Mostrará las diferentes maneras de controlar la concatenación cuando se utiliza la exploración en profundidad y el resumen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Requisitos previos

- El servicio Power BI

- Informe del Ejemplo de análisis de minoristas

## <a name="customize-visualization-x--and-y-axes-in-reports"></a>Personalización de los ejes X e Y de visualización en los informes

Para continuar, inicie sesión en el [servicio Power BI](https://app.powerbi.com) y abra el informe [Ejemplo de análisis de minoristas](../sample-datasets.md) en la vista [Editar informe](../service-interact-with-a-report-in-editing-view.md).

### <a name="create-a-stacked-column-chart-visualization"></a>Creación de una visualización de gráfico de columnas apiladas

Antes de personalizar la visualización, tendrá que crearla.

1. En el servicio Power BI, expanda **Mi área de trabajo**.

1. Desplácese hacia abajo y seleccione **Ejemplo de análisis de minoristas** en la lista de **Conjuntos de datos**.

1. En el panel **Visualizaciones**, seleccione el icono del gráfico de columnas apiladas.

    ![Captura de pantalla del panel Visualizaciones y un gráfico de columnas apiladas vacío](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stacked-column-chart.png)

1. Para establecer los valores del eje X, desde el panel **Campos**, seleccione **Tiempo** > **MesFiscal**.

1. Para establecer los valores del eje Y, en el panel **Campos**, seleccione **Ventas** > **Ventas del año anterior** y **Ventas** > **Ventas de este año** > **Valor**.

    ![Captura de pantalla del gráfico de columnas apiladas rellenado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-create-chart.png)

### <a name="customize-the-x-axis"></a>Personalización del eje X

Ahora puede personalizar el eje X.

1. En el panel **Visualizaciones**, seleccione **Formato** (el icono de rodillo ![Captura de pantalla del icono de rodillo](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) para mostrar las opciones de personalización.

1. Expanda las opciones del eje X.

   ![Captura de pantalla de las opciones del eje X.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-axis.png)

1. Mueva el control deslizante del **eje X** a **Activar**.

    ![Captura de pantalla del control deslizante Activar.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Un motivo por el que podría desear desactivar el eje X es ahorrar espacio para más datos.

1. Aplicar formato mediante color del texto, tamaño y fuente:

    - **Color**: seleccione el color negro.

    - **Tamaño del texto**: especifique *14*.

    - **Familia de fuentes**: seleccione **Arial Black**.

1. Deslice la opción **Título** a **Activado** para mostrar el nombre del eje X. En este caso, es **FiscalMonth**.

1. Aplique formato mediante el color del texto, tamaño y fuente al título.

    - **Color del título**: seleccione el color naranja.

    - **Título del eje**: Escriba *Mes fiscal*.

    - **Tamaño del texto del título**: Escriba *21*.

Una vez finalizadas las personalizaciones, el gráfico de columnas apiladas tendrá un aspecto similar al siguiente:

![Captura de pantalla del gráfico de columnas apiladas personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-customize-axis.png)

Guarde los cambios realizados y pase a la sección siguiente.

Si necesita revertir todos los cambios, seleccione **Volver al valor predeterminado** en la parte inferior del panel de personalización del **eje X**.

### <a name="customize-the-y-axis"></a>Personalización del eje Y

A continuación, va a personalizar el eje Y.

1. Expanda las opciones del eje Y.

   ![Captura de pantalla de las opciones del eje Y.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis.png)

1. Mueva el control deslizante del **eje Y** a **Activar**.  

    ![Captura de pantalla del control deslizante Activar.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Un motivo por el que podría desear desactivar el eje Y es ahorrar espacio para más datos.

1. Establezca la **posición** del eje Y a la **derecha**.

1. Aplicar formato mediante color del texto, tamaño y fuente:

    - **Color**: seleccione el color negro.

    - **Tamaño del texto**: especifique *14*.

    - **Familia de fuentes**: seleccione **Arial Black**.

1. Establezca **Mostrar unidades** en **Millones** y **Posiciones decimales de valores** en *0*.

1. Para esta visualización, tener un título de eje Y no mejora el objeto visual, por lo que puede dejar **Título** en **Desactivar**.  

1. Vamos a hacer que las líneas de cuadrícula se resalten cambiando el color y aumentando el trazo:

    - **Color**: Seleccione el color gris oscuro.

    - **Trazo**: especifique *2*.

Después de todas estas personalizaciones, el gráfico de columnas debe tener un aspecto similar al siguiente:

![Captura de pantalla del gráfico con el eje Y personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-complete.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Personalización de visualizaciones con dos ejes Y

Primero deberá crear un gráfico combinado que busca el impacto que el recuento de tiendas tiene en las ventas. Este es el mismo gráfico que se crea en el [tutorial del gráfico combinado](power-bi-visualization-combo-chart.md). A continuación, deberá formatear los dos ejes Y.

### <a name="create-a-chart-with-two-y-axes"></a>Creación de un gráfico con dos ejes Y

1. Cree un nuevo gráfico de líneas que realice un seguimiento de **Ventas > Porcentaje de margen bruto** por **Tiempo > FiscalMonth**.

    ![Captura de pantalla del nuevo gráfico de líneas.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-line-chart.png)

    > [!NOTE]
    > Para ordenar por mes, consulte [Ordenación siguiendo otros criterios](../consumer/end-user-change-sort.md#other).

    En enero, el porcentaje de margen bruto fue del 35 %, alcanzó su punto máximo en abril con un 45 %, cayó en julio y volvió a alcanzar su punto máximo en agosto. ¿Se verá un patrón similar en las ventas del año anterior y este año?

1. Agregue **Ventas de este año > Valor** y **Ventas del último año** al gráfico de líneas.

    ![Captura de pantalla del gráfico de líneas con los nuevos datos agregados.](media/power-bi-visualization-customize-x-axis-and-y-axis/flatline_new.png)

    La escala de **porcentaje de margen bruto del último año** (la línea azul que está junto a la línea de cuadrícula de **0M%** ) es mucho menor que la escala de **Ventas**, lo que dificulta la comparación. Y los porcentajes de etiqueta del eje Y son absurdos.

1. Para que el objeto visual sea fácil de leer e interpretar, convierta el gráfico de líneas en un gráfico de columnas apiladas y de líneas.

   ![Captura de pantalla del panel Visualizaciones con el icono del gráfico de líneas y de columnas apiladas indicado.](media/power-bi-visualization-customize-x-axis-and-y-axis/converttocombo_new.png)

1. Arrastre el **Porcentaje de margen bruto del último año** de **Valores de columnas** a **Valores de líneas**.

    ![Captura de pantalla del gráfico de columnas apiladas y del gráfico de líneas con los tres valores claramente representados.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes.png)

    Ahora tiene el gráfico de columnas apiladas que creó en la primera sección con un gráfico de líneas sobrepuesto. Si lo desea, utilice lo aprendido anteriormente para dar formato de fuente, color y tamaño al eje.

   ![Captura de pantalla de la línea personalizada y el gráfico de columnas apiladas.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes-new.png)

   Power BI crea dos ejes Y que permiten que los conjuntos de datos se escalen de manera diferente. El eje izquierdo mide dólares y el eje derecho mide porcentajes.

### <a name="format-the-secondary-y-axis"></a>Formato del eje Y secundario

1. En el panel **Visualizaciones**, seleccione el icono de rodillo para mostrar las opciones de formato.

1. Expanda las opciones del eje Y.

1. Desplácese hacia abajo hasta que encuentre la opción **Mostrar secundario**. Compruebe que está en **Activar**.

   ![Captura de pantalla de la opción Mostrar secundario.](media/power-bi-visualization-customize-x-axis-and-y-axis/combo3.png)

1. (Opcional) Personalice los dos ejes. Si cambia **Posición** para el eje de columna o el eje de línea, los dos ejes intercambian los lados.

### <a name="add-titles-to-both-axes"></a>Incorporación de títulos a ambos ejes

Cuando la visualización es complicada, resulta útil agregar títulos a los ejes.  Los títulos ayudan a sus colegas a comprender la historia que está contando su visualización.

1. Cambie **Título** a **Activado** para **Eje Y (columna)** y **Eje Y (línea)** .

1. Establezca **Estilo** en **Mostrar solo el título** para ambos.

   ![Captura de pantalla de las opciones de título y estilo.](media/power-bi-visualization-customize-x-axis-and-y-axis/yaxissettings.png)

1. El gráfico combinado ahora muestra los dos ejes, ambos con títulos.

   ![Captura de pantalla del gráfico con los dos ejes Y personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo-chart.png)

Para más información, consulte [Sugerencias y trucos para el formato de color en Power BI](service-tips-and-tricks-for-color-formatting.md).

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

Si el eje X está clasificado por el propietario del informe como un tipo de fecha, se mostrará la opción **Tipo** y podrá seleccionar entre continuo o por categorías.

## <a name="next-steps"></a>Pasos siguientes

- [Visualizaciones en informes de Power BI](power-bi-report-visualizations.md)

- [Personalización de los títulos, las leyendas y los fondos de las visualizaciones](power-bi-visualization-customize-title-background-and-legend.md)

- [Introducción a las propiedades de eje y formato de color](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Conceptos básicos para los consumidores del servicio Power BI](../consumer/end-user-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
