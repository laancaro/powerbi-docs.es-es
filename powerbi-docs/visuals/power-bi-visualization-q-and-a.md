---
title: Uso del objeto visual Preguntas y respuestas de Power BI
description: Configuración del objeto visual Preguntas y respuestas de Power BI
author: mihart
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/19/2019
ms.author: mohaali
ms.openlocfilehash: a17f98859e637621fbae037610359c8f29391a98
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "75762287"
---
# <a name="introduction-to-power-bi-qa-visualizations"></a>Introducción a las visualizaciones de preguntas y respuestas de Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-are-qa-visualizations"></a>¿Qué son las visualizaciones de preguntas y respuestas?

El objeto visual Preguntas y respuestas permite a los usuarios realizar preguntas con lenguaje natural y obtener las respuestas en forma de objeto visual. 

![Tutorial del objeto visual Preguntas y respuestas](../natural-language/media/qna-visual-walkthrough.gif)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

El objeto visual Preguntas y respuestas se puede usar no solo como una herramienta que permita a los *consumidores* obtener respuestas rápidamente para sus datos, sino que también pueden usarlo los *diseñadores* para crear objetos visuales en un informe simplemente haciendo doble clic en cualquier parte del mismo y usando lenguaje natural desde el principio. Al comportarse como cualquier otro, el objeto visual Preguntas y respuestas admite los filtros cruzados y los elementos destacados cruzados, así como los marcadores. El objeto visual Preguntas y respuestas también admite temas y otras opciones de formato predeterminadas que están disponibles en Power BI.

El objeto visual Preguntas y respuestas consta de cuatro componentes principales:

- El cuadro de preguntas. Ahí es donde los usuarios escriben sus preguntas y donde se muestran sugerencias que les ayudan a completar su pregunta.
- Una lista rellenada previamente de preguntas sugeridas.
- Icono para convertir el objeto visual Preguntas y respuestas en un objeto visual estándar. 
- Icono para abrir las herramientas de Preguntas y respuestas que permiten a los diseñadores configurar el motor de lenguaje natural subyacente.

## <a name="prerequisites"></a>Requisitos previos

1. En este tutorial se usa el [archivo .PBIX del ejemplo de ventas y marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix). 

1. En la sección superior izquierda de la barra de menús de Power BI Desktop, seleccione **Archivo** > **Abrir**.
   
2. Busque su copia del **archivo .PBIX de ejemplo de ventas y marketing**.

1. Abra el archivo en la vista de informe. ![Captura de pantalla del icono de vista de informe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.


Si aparece algún error al crear un objeto visual Preguntas y respuestas, asegúrese de consultar la sección de [limitaciones](../natural-language/q-and-a-limitations.md) para ver si se admite la configuración del origen de datos.

## <a name="create-a-qa-visual-using-a-suggested-question"></a>Creación de un objeto visual Preguntas y respuestas mediante una pregunta sugerida
En este ejercicio, vamos a seleccionar una de las preguntas sugeridas para crear un objeto visual Preguntas y respuestas. 

1. Inicie una página de informe en blanco y seleccione el icono de objeto visual Preguntas y respuestas en el panel Visualizaciones.

    ![Panel Visualizaciones con el icono de objeto visual Preguntas y respuestas resaltado](media/power-bi-visualization-q-and-a/power-bi-icon.png)

2. Arrastre el borde para cambiar el tamaño del objeto visual.

    ![Objeto visual Preguntas y respuestas en el lienzo](media/power-bi-visualization-q-and-a/power-bi-qna.png)

3. Para crear el objeto visual, seleccione una de las preguntas que se sugieren o empiece a escribir en el cuadro de preguntas. En este ejemplo, hemos seleccionado los **top geo states by sum of revenue** (estados geográficos con mayor suma de ingresos). Power BI selecciona lo mejor posible el tipo de objeto visual que se va a usar. En este caso, es un mapa.

    ![Mapa del objeto visual Preguntas y respuestas](media/power-bi-visualization-q-and-a/power-bi-map.png)

    Pero puede indicar a Power BI qué tipo de objeto visual se va a usar. Para ello, no tiene más que agregarlo a su consulta en lenguaje natural. Tenga en cuenta que no todos los tipos de objetos visuales funcionan o tienen sentido con sus datos. Por ejemplo, estos datos no generarían un gráfico de dispersión significativo. Sin embargo, funcionan como un mapa coroplético.

    ![Objeto visual Preguntas y respuestas como un mapa coroplético](media/power-bi-visualization-q-and-a/power-bi-specify-map.png)

## <a name="create-a-qa-visual-using-a-natural-language-query"></a>Creación de un objeto visual Preguntas y respuestas mediante el uso de una consulta en lenguaje natural
En el ejemplo anterior, seleccionamos una de las preguntas sugeridas para crear un objeto visual Preguntas y respuestas.  En este, vamos a escribir nuestra propia pregunta. A medida que escribimos la pregunta, Power BI nos ayuda con Autocompletar, sugerencias y comentarios.

Si no está seguro del tipo de preguntas que se deben formular o la terminología que se utiliza, expanda **Mostrar todas las sugerencias** o examine el panel Campos, que se puede encontrar en el lado derecho del lienzo. Esto le ayudará a familiarizarse con los términos y el contenido del conjunto de datos Sales & Marketing.

![Lienzo con la opción Mostrar todas las sugerencias y el panel Campos destacados](media/power-bi-visualization-q-and-a/power-bi-terminology.png)


1. Escriba una pregunta en el campo de preguntas y respuestas. Power BI subraya en rojo las palabras que no reconoce. Siempre que es posible, Power BI ayuda a definir las palabras que no se reconocen.  En el primer ejemplo que aparece a continuación, se podrá seleccionar cualquiera de las sugerencias.  

    ![Escritura de una pregunta en el cuadro de preguntas de Preguntas y respuestas](media/power-bi-visualization-q-and-a/power-bi-red-suggest.png)

2. A medida que escribimos más contenido de la pregunta, Power BI nos hace saber que no entiende la pregunta e intenta ayudarnos. En el ejemplo siguiente, Power BI nos pregunta "¿quiso decir..." y sugiere una manera diferente de formular la pregunta con terminología del conjunto de datos. 

    ![El objeto Preguntas y respuestas muestra sugerencias](media/power-bi-visualization-q-and-a/power-bi-define.png)

5. Con la ayuda de Power BI, pudimos formular una pregunta con todos los términos reconocibles. Power BI muestra los resultados en forma de gráfico de líneas. 

    ![Resultados del objeto visual Preguntas y respuestas](media/power-bi-visualization-q-and-a/power-bi-type.png)


6. Vamos a cambiar el objeto visual a un gráfico de columnas. 

    ![Objeto visual Preguntas y respuestas con "como un gráfico de columnas" agregado a la pregunta](media/power-bi-visualization-q-and-a/power-bi-specify-visual.png)

7.  Agregue más objetos visuales a la página del informe y vea cómo interactúa el objeto visual Preguntas y respuestas con los demás objetos visuales de la página. En este ejemplo, el objeto visual Preguntas y respuestas ha aplicado un filtro cruzado al gráfico de líneas y al mapa, y ha aplicado un resaltado cruzado al gráfico de barras.

    ![Objeto visual Preguntas y respuestas con una barra seleccionada y el impacto en los otros tres objetos visuales en la página del informe](media/power-bi-visualization-q-and-a/power-bi-filters.png)

## <a name="format-and-customize-the-qa-visual"></a>Formato y personalización del objeto visual Preguntas y respuestas
El objeto Preguntas y respuestas se puede personalizar tanto desde el panel de formato como aplicando un tema. 

### <a name="apply-a-theme"></a>Aplicación de un tema
Al seleccionar un tema, este se aplica a toda la página del informe. Hay muchos temas entre los que elegir, así que pruébelos hasta que obtenga la apariencia que desee. 

1. En la barra de menús, seleccione la pestaña **Inicio** y elija **Cambiar tema**. 

    ![Escritorio con Cambiar tema seleccionado](media/power-bi-visualization-q-and-a/power-bi-themes.png)

    
    
2. En este ejemplo hemos seleccionado **Más temas** > **Color blind safe** (Para daltónicos).

    ![Objeto visual Preguntas y respuestas con el tema Color blind (Para daltónicos) aplicado](media/power-bi-visualization-q-and-a/power-bi-color-blind.png)

### <a name="format-the-qa-visual"></a>Formato del objeto visual Preguntas y respuestas
Dé formato al objeto visual Preguntas y respuestas, al campo de preguntas y a la forma en que se muestran las sugerencias. Puede cambiar todos los elementos, desde el fondo de un título hasta el color de las palabras no reconocidas cuando se pasa el puntero. Aquí hemos agregado un fondo gris al cuadro de preguntas y hemos cambiado el subrayado a amarillo y verde. El título está centrado y tiene un fondo amarillo. 

![El objeto visual Preguntas y respuestas muestra los resultados de la asignación de formato](media/power-bi-visualization-q-and-a/power-bi-q-and-a-format.png)

## <a name="convert-your-qa-visual-into-a-standard-visual"></a>Conversión de un objeto visual Preguntas y respuestas en un objeto visual estándar
Hemos dado algo de formato al objeto visual del gráfico de columnas del tema Color blind safe (Para daltónicos): hemos agregado un título y un borde, y ya estamos preparados para convertirlo en un objeto visual estándar del informe y a anclarlo a un panel.

Seleccione el ![icono de engranaje](media/power-bi-visualization-q-and-a/power-bi-convert-icon.png) para **convertir este objeto Preguntas y respuestas en un objeto visual estándar**.

![Objeto visual Preguntas y respuestas con una flecha que apunta al icono de objeto visual estándar](media/power-bi-visualization-q-and-a/power-bi-visual-convert.png)

Este ya no es un objeto visual Preguntas y respuestas, sino un gráfico de columnas estándar. Se puede anclar a un panel. En el informe, este objeto visual se comporta de la misma forma que los restantes objetos visuales estándar. Observe que en el panel Visualizaciones está seleccionado el icono de gráfico de columnas en lugar del icono del objeto visual Preguntas y respuestas.

Si usa el ***servicio Power BI***, ahora puede anclar el objeto visual a un panel, para lo que debe seleccionar el icono Anclar. 


![El servicio Power BI con el icono Anclar resaltado](media/power-bi-visualization-q-and-a/power-bi-pin.png)


## <a name="advanced-features-of-the-qa-visual"></a>Características avanzadas del objeto visual Preguntas y respuestas
Al seleccionar el icono de engranaje, se abre el panel de herramientas del objeto visual Preguntas y respuestas. 

![Objeto visual Preguntas y respuestas con el icono de herramientas seleccionado](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling.png)

Use el panel de herramientas para enseñar a los términos de Preguntas y respuestas que no se reconocen, a administrar esos términos y a administrar las preguntas sugeridas para este conjunto de herramientas e informe. En el panel de herramientas también puede examinar las preguntas que se han formulado mediante este objeto visual Preguntas y respuestas, y ver las preguntas que han marcado los usuarios. Para más información, consulte el artículo en el que se realiza una [introducción a las herramientas de Preguntas y respuestas](../natural-language/q-and-a-tooling-intro.md).

![El panel de herramientas de Preguntas y respuestas](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling-pane.png)

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
El objeto visual Preguntas y respuestas se integra con Office y Bing para intentar encuadrar las palabras comunes que no se reconocen en los campos del conjunto de datos.  

## <a name="next-steps"></a>Pasos siguientes

Hay varias formas de integrar el lenguaje natural. Para más información, consulte los siguientes artículos:

* [Introducción a Preguntas y respuestas](../natural-language/q-and-a-tooling-intro.md)
* [Procedimientos recomendados de Preguntas y respuestas](../natural-language/q-and-a-best-practices.md)
