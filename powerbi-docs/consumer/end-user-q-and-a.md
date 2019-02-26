---
title: Introducción a Preguntas y respuestas en el servicio Power BI
description: Tema de información general de la documentación acerca de las consultas en lenguaje natural de Preguntas y respuestas de Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: e6f95eedbd84ad5f512bbc1a1255cee7130a60d7
ms.sourcegitcommit: a054782370dec56d49bb205ee10b7e2018f22693
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56661987"
---
# <a name="qa-for-power-bi-consumers"></a>Preguntas y respuestas para **consumidores** de Power BI
## <a name="what-is-qa"></a>¿Qué son las preguntas y respuestas?
A veces, la manera más rápida de obtener una respuesta de sus datos es formular una pregunta con un lenguaje natural. Por ejemplo, "¿Cuáles fueron las ventas totales del año pasado?"  
Use Preguntas y respuestas para explorar los datos a través de las capacidades de lenguaje natural e intuitivo y reciba respuestas en forma de gráficos. Preguntas y respuestas es diferente de un motor de búsqueda, ya que solamente proporciona resultados sobre los datos de Power BI.

**Preguntas y respuestas de Power BI** solo permite responder a las consultas expresadas en lenguaje natural efectuadas en inglés. Hay una vista previa disponible para idioma español que puede habilitar el administrador de Power BI.

**Preguntas y respuestas de Power BI** está disponible con una licencia Pro o Premium. 
>

![gráfico de rectángulos creado de preguntas y respuestas](media/end-user-q-and-a/power-bi-qna.png)

La formulación de la pregunta es solo el principio.  Diviértase mientras recorre sus datos, perfecciona o amplía su pregunta, descubre valiosa información nueva, profundice al máximo en los detalles u obtenga una visión más amplia. Se sentirá encantado con la información y los descubrimientos realizados.

La experiencia es verdaderamente interactiva... ¡y rápida! Con la tecnología del almacenamiento en memoria, la respuesta es casi instantánea.

## <a name="where-can-i-use-qa"></a>¿Dónde se pueden usar Preguntas y respuestas?
Encontrará Preguntas y respuestas en los paneles del servicio Power BI, en la parte inferior del panel en Power BI Mobile y sobre la visualización en Power BI Embedded. A menos que el diseñador le haya concedido permisos de edición, podrá usar Preguntas y respuestas para explorar los datos, pero no podrá guardar las visualizaciones creadas con Preguntas y respuestas.

![cuadro de preguntas](media/end-user-q-and-a/powerbi-qna.png)

## <a name="how-does-qa-know-how-to-answer-questions"></a>¿Cómo se responden preguntas en Preguntas y respuestas?
Preguntas y respuestas busca respuestas en todos los conjuntos de datos asociados con el panel. Si un conjunto de datos tiene un icono en el panel, Preguntas y respuestas buscará las respuestas en ese conjunto de datos. 

## <a name="how-do-i-start"></a>¿Cómo empiezo?
En primer lugar, familiarícese con el contenido. Eche un vistazo a las visualizaciones en el panel y en el informe. Hágase una idea clara del tipo y el intervalo de datos que están disponibles para usted. Posteriormente vuelva a centrarse en el panel y coloque el cursor en el cuadro de pregunta. Se abrirá la pantalla de Preguntas y respuestas.

![Pantalla de Preguntas y respuestas](media/end-user-q-and-a/power-bi-qna-screen.png) 

* Si las etiquetas y valores del eje de visualizaciones incluyen "ventas", "cuenta", "mes" y "oportunidades", puede entonces hacer preguntas como: "Qué *cuenta* tiene la más alta *oportunidad* o mostrar *ventas* por mes como un gráfico de barras".

* Si tiene datos de rendimiento del sitio web en Google Analytics, puede preguntar a Preguntas y respuestas sobre el tiempo transcurrido en una página web, el número de visitas únicas a una página y el índice de fidelidad de los usuarios. O bien, si está consultando datos demográficos, podría preguntar sobre la edad y los ingresos por ubicación.

En la parte inferior de la pantalla verá otros elementos útiles. Para cada conjunto de datos, Preguntas y respuestas muestran las palabras clave y a veces incluso muestra algunas sugerencias o ejemplos de preguntas. Seleccione cualquiera de estos elementos para agregarlos al cuadro de pregunta. 

Otra manera en que Preguntas y respuestas puede ayudar a formular preguntas es mediante peticiones de confirmación, rellenado automático o indicaciones visuales. 

![Vídeo](media/end-user-q-and-a/qa.gif) 


### <a name="which-visualization-does-qa-use"></a>¿Qué visualización usa Preguntas y respuestas?
Preguntas y respuestas escoge la mejor visualización en función de los datos que se muestran. A veces los datos del conjunto de datos subyacente se definen como un determinado tipo o categoría y esto ayuda a Preguntas y respuestas a saber cómo mostrarlos. Por ejemplo, si los datos se definen como un tipo de fecha, es más probable que se muestren como un gráfico de líneas. Los datos que se clasifican como ciudad es más probable que se muestren como un mapa.

También puede indicar a Preguntas y respuestas qué visualización usar agregándolo a su pregunta. Pero tenga en cuenta que no siempre es posible para Preguntas y respuestas mostrar los datos en el tipo de visualización solicitado. Preguntas y respuestas le pedirá confirmación acerca de una lista de tipos de visualización factibles.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
**Pregunta:** No veo Preguntas y respuestas en este panel.    
**Respuesta 1:** Si no ve un cuadro de pregunta, compruebe primero la configuración. Para ello, en la esquina superior derecha de la barra de herramientas de Power BI, seleccione el icono de engranaje.   
![icono de engranaje](media/end-user-q-and-a/power-bi-settings.png)

A continuación, elija **Configuración** > **Paneles**. Asegúrese de que hay una marca de verificación junto a **Mostrar el cuadro de búsqueda de Preguntas y respuestas en este panel**.
![Configuración de Preguntas y respuestas para el panel](media/end-user-q-and-a/power-bi-turn-on.png)  


**Respuesta 2:** A veces, el *diseñador* del panel o el administrador desactiva Preguntas y respuestas. Póngase en contacto con ellos para ver si pueden volver a activarlo.   

**Pregunta:** No obtengo los resultados que quiero ver cuando escribo una pregunta.    
**Respuesta:** Póngase en contacto con el *diseñador* del panel. El diseñador puede hacer muchas cosas para mejorar los resultados de Preguntas y respuestas. Por ejemplo, el diseñador puede cambiar el nombre de las columnas del conjunto de datos para usar unos términos que se entiendan fácilmente (`CustomerFirstName` en lugar de `CustFN`). Dado que el diseñador conoce realmente bien el conjunto de datos, el diseñador también puede plantear preguntas útiles y agregarlas al lienzo de Preguntas y respuestas.

![pregunta destacada remarcada](media/end-user-q-and-a/power-bi-featured-q.png)

## <a name="next-steps"></a>Pasos siguientes

