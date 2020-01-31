---
title: Preguntas y respuestas para consumidores de Power BI
description: Tema de información general de la documentación acerca de las consultas en lenguaje natural de Preguntas y respuestas de Power BI.
author: mihart
ms.reviewer: mohammad ali
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: cc20d981e1e774eed109c614e146415ec3813601
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709802"
---
# <a name="qa-for-power-bi-consumers"></a>Preguntas y respuestas para consumidores de Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-qa"></a>¿Qué son las preguntas y respuestas?
A veces, la manera más rápida de obtener una respuesta de sus datos es formular una pregunta con un lenguaje natural. Por ejemplo, "¿Cuáles fueron las ventas totales del año pasado?"

Use Preguntas y respuestas para explorar los datos a través de las capacidades de lenguaje natural e intuitivo y reciba respuestas en forma de gráficos. Preguntas y respuestas es diferente de un motor de búsqueda, ya que solamente proporciona resultados sobre los datos de Power BI.

## <a name="which-visualization-does-qa-use"></a>¿Qué visualización usa Preguntas y respuestas?
Preguntas y respuestas escoge la mejor visualización en función de los datos que se muestran. A veces los datos del conjunto de datos subyacente se definen como un determinado tipo o categoría y esto ayuda a Preguntas y respuestas a saber cómo mostrarlos. Por ejemplo, si los datos se definen como un tipo de fecha, es más probable que se muestren como un gráfico de líneas. Los datos que se clasifican como ciudad es más probable que se muestren como un mapa.

También puede indicar a Preguntas y respuestas qué objeto visual usar agregándolo a su pregunta. Pero tenga en cuenta que no siempre es posible para Preguntas y respuestas mostrar los datos en el tipo de objeto visual solicitado. Preguntas y respuestas le pedirá confirmación acerca de una lista de tipos de objetos visuales factibles.

## <a name="where-can-i-use-qa"></a>¿Dónde se pueden usar Preguntas y respuestas?
Encontrará Preguntas y respuestas en los paneles del servicio Power BI, en la parte inferior del panel en Power BI Mobile. A menos que el diseñador le haya concedido permisos de edición, podrá usar Preguntas y respuestas para explorar los datos, pero no podrá guardar las visualizaciones creadas con Preguntas y respuestas.

![cuadro de preguntas](media/end-user-q-and-a/powerbi-qna.png)

También encontrará Preguntas y respuestas en los informes, si el *diseñador* del informe ha agregado un [objeto visual Preguntas y respuestas](../visuals/power-bi-visualization-q-and-a.md).   

![Objeto visual de Preguntas y respuestas](media/end-user-q-and-a/power-bi-q-and-a-default.png)

## <a name="qa-on-dashboards"></a>Preguntas y respuestas en los paneles

**Preguntas y respuestas de Power BI** está disponible con una licencia Pro o Premium.  [Preguntas y respuestas de las aplicaciones de Power BI Mobile](mobile/mobile-apps-ios-qna.md) y [Preguntas y respuestas de Power BI Embedded](../developer/qanda.md) se tratan en artículos independientes. En este momento, **Preguntas y respuestas de Power BI** solo admite la respuesta a las consultas en lenguaje natural en inglés, aunque hay una vista previa disponible en español que puede ser habilitada por el administrador de Power BI.


![gráfico de rectángulos creado de preguntas y respuestas](media/end-user-q-and-a/power-bi-treemap.png)

La formulación de la pregunta es solo el principio.  Diviértase mientras recorre sus datos, perfecciona o amplía su pregunta, descubre valiosa información nueva, profundice al máximo en los detalles u obtenga una visión más amplia. Se sentirá encantado con la información y los descubrimientos realizados.

La experiencia es verdaderamente interactiva... ¡y rápida! Con la tecnología del almacenamiento en memoria, la respuesta es casi instantánea.


## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>Uso de las Preguntas y respuestas en un panel del servicio Power BI
En el servicio Power BI (app.powerbi.com), un panel contiene iconos anclados desde uno o varios conjuntos de datos, por lo que puede formular preguntas sobre cualquiera de los datos contenidos en cualquiera de estos conjuntos de datos. Para ver los informes y conjuntos de datos que se usaron para crear el panel, seleccione **Ver relacionados** desde la lista desplegable **Más acciones**.

![Ver relacionados en la barra de menús](media/end-user-q-and-a/power-bi-q-and-a-view-related.png)

## <a name="how-do-i-start"></a>¿Cómo empiezo?
En primer lugar, familiarícese con el contenido. Eche un vistazo a los objetos visuales en el panel y en el informe. Hágase una idea clara del tipo y el intervalo de datos que están disponibles para usted. 

Por ejemplo:

* Si las etiquetas y valores del eje de un objeto visual incluyen "ventas", "cuenta", "mes" y "oportunidades", puede entonces hacer preguntas como: "Qué *cuenta* tiene la más alta *oportunidad* o mostrar *ventas* por mes como un gráfico de barras".

* Si tiene datos de rendimiento del sitio web en Google Analytics, puede preguntar a Preguntas y respuestas sobre el tiempo transcurrido en una página web, el número de visitas únicas a una página y el índice de fidelidad de los usuarios. O bien, si está consultando datos demográficos, podría preguntar sobre la edad y los ingresos por ubicación.

Una vez que esté familiarizado con los datos, vuelva a centrarse al panel y coloque el cursor en el cuadro de pregunta. Se abrirá la pantalla de Preguntas y respuestas.

![Pantalla de Preguntas y respuestas](media/end-user-q-and-a/power-bi-suggested.png) 

Incluso antes de comenzar a escribir, Preguntas y respuestas muestra una nueva pantalla con sugerencias que le ayudarán a realizar la pregunta. Verá las frases y preguntas que contienen los nombres de las tablas de los conjuntos de datos subyacentes y puede incluso ver una lista de preguntas *destacadas* creadas por el propietario del conjunto de datos.

Puede seleccionar cualquiera de ellas para agregarlas al cuadro de preguntas y luego refinarlas para encontrar una respuesta específica. 

![Pantalla de Preguntas y respuestas](media/end-user-q-and-a/power-bi-result.png) 

Otra manera en la que Power BI ayuda a formular preguntas es mediante características como peticiones de confirmación, rellenado automático o indicaciones visuales. Power BI proporciona esta ayuda para Preguntas y respuestas en los paneles, Preguntas y respuestas en los informes y con el objeto visual Preguntas y respuestas. Estas características se describirán con detalle a continuación, en la sección [Creación de un objeto visual de Preguntas y respuestas con una consulta en lenguaje natural](#create-a-qa-visual-by-typing-a-natural-language-query)

<!-- ![video](../visuals/media/end-user-q-and-a/qna4.gif) -->


## <a name="the-qa-visual-in-power-bi-reports"></a>El objeto visual de Preguntas y respuestas en informes de Power BI

El objeto visual Preguntas y respuestas le permite realizar preguntas con lenguaje natural y obtener las respuestas en forma de objeto visual. El objeto visual Preguntas y respuestas se comporta como cualquier otro en un informe y admite filtros cruzados, resaltados cruzados, marcadores y comentarios. 

Puede identificar una objeto visual Preguntas y respuestas por su cuadro de pregunta en la parte superior. Aquí es donde escribirá preguntas con lenguaje natural. El objeto visual Preguntas y respuestas se puede usar una y otra vez para formular preguntas sobre los datos. Al salir del informe, el objeto visual Preguntas y respuestas se restablece a su valor predeterminado. 

![Captura de pantalla del valor predeterminado del objeto visual Preguntas y respuestas](media/end-user-q-and-a/power-bi-q-and-a-default.png)


## <a name="use-qa"></a>Uso de Preguntas y respuestas 
Para usar el objeto visual Preguntas y respuestas en un panel o informe, seleccione una de las preguntas sugeridas o escriba una propia en lenguaje natural. 

### <a name="create-a-qa-visual-by-using-a-suggested-question"></a>Creación de un objeto visual Preguntas y respuestas mediante una pregunta sugerida

Aquí hemos seleccionado **principales estados geográficos por unidades totales**. Power BI elige el mejor tipo de objeto visual posible. En este caso, es un mapa.

![Mapa del objeto visual Preguntas y respuestas](media/end-user-q-and-a/power-bi-q-and-a-suggested.png)

Pero puede indicar a Power BI qué tipo de objeto visual se va a usar. Para ello, no tiene más que agregarlo a su consulta en lenguaje natural. Tenga en cuenta que no todos los tipos de objetos visuales funcionan o tienen sentido con sus datos. Por ejemplo, estos datos no generarían un gráfico de dispersión significativo. Sin embargo, funcionan como un mapa coroplético.

![Objeto visual Preguntas y respuestas como un mapa coroplético](media/end-user-q-and-a/power-bi-filled-map.png)

### <a name="create-a-qa-visual-by-typing-a-natural-language-query"></a>Creación de un objeto visual Preguntas y respuestas mediante la escritura de una consulta en lenguaje natural


Si no está seguro del tipo de preguntas que se deben formular o la terminología que se debe usar, expanda **Mostrar todas las sugerencias** o examine los otros objetos visuales del informe. Esto le ayudará a familiarizarse con los términos y el contenido del conjunto de datos.

1. Escriba su pregunta en el campo Preguntas y respuestas con lenguaje natural. A medida que escribe la pregunta, Power BI le ayuda con Autocompletar, sugerencias visuales y comentarios.

    **Autocompletar**: a medida que escribe la pregunta, Preguntas y respuestas de Power BI muestra sugerencias oportunas y contextuales para ayudarle a ser productivo rápidamente con el lenguaje natural. A medida que escribe, obtiene comentarios y resultados inmediatos. La experiencia es similar a escribir en un motor de búsqueda.

    En este ejemplo, la sugerencia que quiere es la última. 

    ![Preguntas y respuestas con una palabra subrayada en color azul](media/end-user-q-and-a/power-bi-autocomplete.png)

    **Subrayados en color rojo y azul**: Preguntas y respuestas de Power BI muestra palabras con subrayado para ayudarle a ver qué palabras ha reconocido Power BI o no. Un subrayado sólido de color azul indica que Power BI ha reconocido la palabra. En el ejemplo siguiente se muestra que Preguntas y respuestas ha reconocido la palabra **tienda**.

    ![Preguntas y respuestas con una lista desplegable de sugerencias para completar la pregunta](media/end-user-q-and-a/power-bi-blue.png)

    Seleccione una palabra subrayada en color azul para mostrar una lista desplegable de preguntas sugeridas. 

    ![Lista desplegable con sugerencias También puede usar](media/end-user-q-and-a/power-bi-try.png)


    A menudo, cuando escribe una palabra en Preguntas y respuestas, se marca con un subrayado de color rojo. Un subrayado rojo puede indicar uno de los dos posibles problemas. El primer tipo de problema se clasifica como confianza baja. Si escribe una palabra no precisa o ambigua, el campo aparece subrayado en rojo. Un ejemplo podría ser la palabra "Ubicación". Varios campos pueden contener la palabra "Ubicación", por lo que el sistema usa un subrayado de color rojo para pedirle que elija el campo que quiere. En este ejemplo, Power BI le pedirá que seleccione el campo que quiere usar para "VanArsdel".
    
    ![Término subrayado en rojo en el cuadro de preguntas de Preguntas y respuestas](media/end-user-q-and-a/power-bi-q-and-a-red.png)
    
    Otro ejemplo de confianza baja podría ser si escribe la palabra "Área", pero la columna que coincide es "Distrito". Preguntas y respuestas de Power BI reconoce palabras que significan lo mismo, gracias a la integración con Bing y Office. Preguntas y respuestas subraya la palabra en color rojo para que sepa que no es una coincidencia directa

    ![Preguntas y respuestas reformula la pregunta con un sinónimo](media/end-user-q-and-a/power-bi-red.png)

    El segundo tipo de problema se da cuando Preguntas y respuestas no reconoce la palabra. Un ejemplo podría ser el uso de la palabra "geografía", aunque no exista en ningún lugar de los datos. La palabra está en el diccionario, pero Preguntas y respuestas marca este término con un subrayado rojo. Preguntas y respuestas de Power BI no puede crear una visualización y le sugiere que pida al diseñador del informe que agregue el término.

    ![Preguntas y respuestas con una sugerencia de que le pida al diseñador que agregue la palabra geografía](media/end-user-q-and-a/power-bi-geography.png)

    **Sugerencias**: a medida que escribe más contenido de la pregunta, Power BI le hace saber si no la entiende e intenta ayudarle. En el ejemplo siguiente, Power BI le pregunta "¿quiso decir..." y sugiere una manera diferente de combinar palabras para la pregunta con la terminología del conjunto de datos. 

    ![Propuesta de correcciones sugeridas en el objeto visual Preguntas y respuestas](media/end-user-q-and-a/power-bi-q-and-a-did-you-mean.png)

    Después de seleccionar la corrección de Power BI, los resultados se muestran como un gráfico de líneas. 

    ![Resultados del objeto visual Preguntas y respuestas como un gráfico de líneas](media/end-user-q-and-a/power-bi-q-and-a-line.png)


    Sin embargo, puede cambiar el gráfico de líneas a otro tipo de objeto visual.  

    ![Objeto visual Preguntas y respuestas con "como un gráfico de columnas" agregado a la pregunta](media/end-user-q-and-a/power-bi-q-and-a-specify-type.png)



## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

**Pregunta:** No veo Preguntas y respuestas en este panel.    
**Respuesta 1:** Si no ve un cuadro de pregunta, compruebe primero la configuración. Para ello, en la esquina superior derecha de la barra de herramientas de Power BI, seleccione el icono de engranaje.   
![icono de engranaje](media/end-user-q-and-a/power-bi-settings.png)

A continuación, elija **Configuración** > **Paneles**. Asegúrese de que hay una marca de verificación junto a **Mostrar el cuadro de búsqueda de Preguntas y respuestas en este panel**.    
![Configuración de Preguntas y respuestas para el panel](media/end-user-q-and-a/power-bi-turn-on.png)  


**Respuesta 2:** A veces, no tendrá acceso a la configuración. Si el *diseñador* del panel o el administrador han desactivado Preguntas y respuestas, consulte con ellos para ver si es correcto volver a activarlo.   

**Pregunta:** No obtengo los resultados que quiero ver cuando escribo una pregunta.    
**Respuesta:** Seleccione la opción para ponerse en contacto con el propietario del panel o el informe. Puede hacerlo directamente desde la página del panel de Preguntas y respuestas o desde el objeto visual Preguntas y respuestas. O bien, puede buscar el propietario en el encabezado de Power BI.  El diseñador puede hacer muchas cosas para mejorar los resultados de Preguntas y respuestas. Por ejemplo, el diseñador puede cambiar el nombre de las columnas del conjunto de datos para usar unos términos que se entiendan fácilmente (`CustomerFirstName` en lugar de `CustFN`). Dado que el diseñador conoce realmente bien el conjunto de datos, el diseñador también puede plantear preguntas útiles y agregarlas a las preguntas sugeridas de Preguntas y respuestas.

![Mostrar información de contacto](media/end-user-q-and-a/power-bi-q-and-a-contact.png)

## <a name="privacy"></a>Privacidad

Microsoft puede usar sus preguntas para mejorar Power BI. Revise la [declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) para obtener más información al respecto.

## <a name="next-steps"></a>Pasos siguientes
Para obtener información sobre cómo un *diseñador* de informes puede crear y administrar un objeto visual Preguntas y respuestas, consulte [Tipo de objeto visual Preguntas y respuestas](../visuals/power-bi-visualization-q-and-a.md).
