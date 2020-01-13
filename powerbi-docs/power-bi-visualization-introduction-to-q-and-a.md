---
title: Creación de un objeto visual con Preguntas y respuestas de Power BI
description: Aprenda a crear un objeto visual en el servicio Power BI con Preguntas y respuestas mediante el ejemplo de análisis de venta directa
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 817ce82b94817530854d85c7dbcca17a313fc438
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "73874456"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Creación de un objeto visual con Preguntas y respuestas de Power BI

A veces, la manera más rápida de obtener una respuesta de sus datos es formular una pregunta con un lenguaje natural.  En este artículo veremos dos formas distintas de crear la misma visualización: en primer lugar, formulando una pregunta con Preguntas y respuestas y, en segundo lugar, creándola en un informe. Vamos a usar el servicio Power BI para crear el objeto visual en el informe, pero el proceso es casi idéntico con Power BI Desktop.

![Gráfico relleno de Power BI](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Para poder continuar, debe utilizar un informe que pueda editar, por lo que vamos a usar uno de los ejemplos disponibles con Power BI.

## <a name="create-a-visual-with-qa"></a>Creación de un objeto visual con Preguntas y respuestas

¿Cómo podría crear este gráfico de líneas mediante Preguntas y respuestas?

1. En el área de trabajo de Power BI, seleccione **Obtener datos** \> **Ejemplos** \> **Ejemplo de análisis de minoristas** > **Conectar**.

1. Abra el panel del ejemplo de análisis de ventas y coloque el cursor en el cuadro de diálogo Preguntas y respuestas, en **Pregunte algo sobre sus datos**.

    ![Colocar el cursor en el cuadro de diálogo Preguntas y respuestas](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. En este cuadro, escriba algo parecido a esta pregunta:
   
    **cuáles fueron las ventas de este año y del año pasado por mes como gráfico de áreas**
   
    A medida que escriba la pregunta, Preguntas y respuestas seleccionará la mejor visualización para mostrar la respuesta; la visualización cambia de forma dinámica a medida que se modifica la pregunta. Además, Preguntas y respuestas le ayuda a dar formato a la pregunta con sugerencias, Autocomplete y correcciones ortográficas. Preguntas y respuestas recomienda un pequeño cambio en la formulación: "ventas de este año y ventas del último año por *períodos mensuales* como gráfico de áreas".  

    ![Formulación corregida en Preguntas y respuestas](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Seleccione la frase para aceptar la sugerencia. 
   
   Cuando termine de escribir la pregunta, el resultado será el mismo gráfico que vio en el panel.
   
   ![Gráfico de áreas relleno de Preguntas y respuestas](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Para anclar el gráfico a su panel, seleccione el icono de anclaje. ![Icono de anclaje](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) en la esquina superior derecha.

## <a name="create-a-visual-in-the-report-editor"></a>Creación de un objeto visual en el editor de informes

1. Vuelva al panel del ejemplo de análisis de venta directa.
   
2. El panel contiene el mismo icono de gráfico de área para "Ventas del último año y ventas de este año".  Seleccione este icono. No seleccione el icono que creó con Preguntas y respuestas. Si lo hace, se abrirá Preguntas y respuestas. El icono del gráfico de áreas original se creó en un informe por lo que este se abrirá en la página que contiene esta visualización.

    ![Panel del ejemplo de análisis de minoristas](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Seleccione **Editar informe**para abrir el informe en la Vista de edición.  Si no es el propietario de un informe, no tiene la opción de abrirlo en la vista de edición.
   
    ![Botón Editar informe](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Seleccione el gráfico de área y revise la configuración en el panel **Campos** .  Para crear este gráfico, el creador del informe ha seleccionado estos tres valores (**Ventas del año anterior** y **Ventas de este año > Valor** de la tabla **Ventas**, y **MesFiscal** de la tabla **Tiempo**) y los ha organizado en las áreas **Eje** y **Valores**.
   
    ![Panel Visualizaciones](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Puede ver que han finalizado con el mismo objeto visual. Crearlo de esta manera no era demasiado complicado. Pero crearlo con Preguntas y respuestas fue mucho más fácil.

## <a name="next-steps"></a>Pasos siguientes

- [Uso de Preguntas y respuestas en paneles e informes](power-bi-tutorial-q-and-a.md)  
- [Preguntas y respuestas para consumidores](consumer/end-user-q-and-a.md)
- [Funcionamiento correcto de los datos con Preguntas y respuestas en Power BI](service-prepare-data-for-q-and-a.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

