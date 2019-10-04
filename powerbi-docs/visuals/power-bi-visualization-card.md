---
title: Visualizaciones de tarjeta (iconos grandes de números)
description: Creación de una visualización de tarjeta en Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 268b69362f0f8c98ba01fbd0673fc46856d54ba2
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195512"
---
# <a name="card-visualizations"></a>Visualizaciones de tarjeta

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A veces, un único número es lo más importante que desea seguir en el panel o informe de Power BI, como las ventas totales, la cuota de mercado interanual o el total de oportunidades. Este tipo de visualización se denomina una *tarjeta*. Al igual que con casi todas las visualizaciones nativas de Power BI, se pueden crear tarjetas con el editor de informes o mediante Preguntas y respuestas.

![visualización de tarjetas](media/power-bi-visualization-card/pbi-opptuntiescard.png)

## <a name="prerequisite"></a>Requisito previo

En este tutorial se usa el [archivo PBIX del Ejemplo de análisis de minoristas](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** \> **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de minoristas**.

1. Abra el **archivo PBIX del Ejemplo de análisis de minoristas** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.

## <a name="option-1-create-a-card-using-the-report-editor"></a>Opción 1: Creación de una tarjeta con el editor de informes

El primer método para crear una tarjeta es usar el editor de informes en Power BI Desktop.

1. Comience en una página de informe en blanco y seleccione el campo **Tienda** \> **Abrir recuento de tiendas**.

    Power BI crea un gráfico de columnas con un solo número.

   ![Gráfico de mosaicos de número de ejemplo](media/power-bi-visualization-card/pbi-overview-chart.png)

2. En el panel Visualizaciones, seleccione el icono tarjeta.

   ![Tarjeta de título de número de ejemplo](media/power-bi-visualization-card/power-bi-card-visualization.png)

Ahora se ha creado correctamente una tarjeta con el editor de informes. Debajo se muestra la segunda opción para crear una tarjeta con el cuadro de preguntas y respuestas.

## <a name="option-2-create-a-card-from-the-qa-question-box"></a>Opción 2: Creación de una tarjeta a partir del cuadro de Preguntas y respuestas
El cuadro de preguntas y respuestas es otra opción que puede utilizar al crear una tarjeta. En la vista de informe de Power BI Desktop se encuentra disponible el cuadro de preguntas y respuestas.

1. Inicio en una página de informe en blanco

1. En la parte superior de la ventana, seleccione el icono **Hacer una pregunta**. 

    Power BI creará una tarjeta y un cuadro para la pregunta. 

   ![Ubicación del icono de hacer una pregunta](media/power-bi-visualization-card/power-bi-q-and-a-overview.png)

2. Por ejemplo, escriba "ventas totales para Tina" en el cuadro de pregunta.

    El cuadro de pregunta le ayuda con sugerencias y nuevas instrucciones y, por último, muestra el número total.  

   ![Ejemplo de cuadro de preguntas](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

   ![Ejemplo de tarjeta del método pregunta](media/power-bi-visualization-card/power-bi-q-and-a-card.png)

Ahora se ha creado correctamente una tarjeta con el cuadro de preguntas y respuestas. Debajo se indican los pasos necesarios para dar formato a su tarjeta en función de sus propias necesidades.

## <a name="format-a-card"></a>Formateo de una tarjeta
Tiene muchas opciones para cambiar las etiquetas, el texto, el color, etc. La mejor manera de aprender consiste en crear una tarjeta y explorar el panel de formato. A continuación se indican solo algunas de las opciones de formato disponibles. 

El panel de formato está disponible cuando se interactúa con la tarjeta en un informe. 

1. Para empezar, seleccione el icono de rodillo para abrir el panel de formato. 

    ![Tarjeta con el rodillo resaltado](media/power-bi-visualization-card/power-bi-format-card-2.png)

2. Con la tarjeta seleccionada, expanda **Etiqueta de datos** y cambie el color, el tamaño y la familia de las fuentes. Si tuviera miles de tiendas, podría usar **Mostrar unidades** para mostrar el número de tiendas por miles y controlar también las posiciones decimales. Por ejemplo, 125,8 K en lugar de 125 832,00.

    ![Ejemplo de tarjeta con formato de datos](media/power-bi-visualization-card/power-bi-card-format-2.png)

3.  Expanda **Etiqueta de categoría** y cambie el color y el tamaño.

    ![Ejemplo de tarjeta con categoría](media/power-bi-visualization-card/power-bi-card-format-category.png)

4. Expanda **Fondo** y mueva el control deslizante a la posición de activado.  Ahora puede cambiar el color de fondo y la transparencia.

    ![Control deslizante establecido en activado](media/power-bi-visualization-card/power-bi-format-color-2.png)

5. Siga explorando las opciones de formato hasta que la tarjeta esté exactamente cómo le gustaría. 

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
Si no ve un cuadro de pregunta, póngase en contacto con el administrador del sistema o del inquilino.    

## <a name="next-steps"></a>Pasos siguientes
[Gráficos combinados en Power BI](power-bi-visualization-combo-chart.md)

[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
