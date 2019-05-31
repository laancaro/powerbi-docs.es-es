---
title: Use Power BI preguntas y respuestas para explorar y crear objetos visuales
description: Aprenda a utilizar Power BI preguntas y respuestas para crear nuevas visualizaciones en paneles e informes.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: c6fd8967a49515af4d0614653b3d7550c335052f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625424"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Usar Power BI preguntas y respuestas para explorar los datos y crear objetos visuales

A veces, la manera más rápida de obtener una respuesta de sus datos es formular una pregunta con un lenguaje natural. La característica preguntas y respuestas en Power BI le permite explorar los datos en sus propias palabras.  La primera parte de este artículo muestra cómo usar preguntas y respuestas en los paneles en el servicio Power BI. La segunda parte muestra lo que puede hacer con preguntas y respuestas al crear informes en el servicio Power BI o Power BI Desktop. Para obtener más información, consulte el [preguntas y respuestas para los consumidores](consumer/end-user-q-and-a.md) artículo. 

[Preguntas y respuestas en las aplicaciones móviles de Power BI](consumer/mobile/mobile-apps-ios-qna.md) y [preguntas y respuestas con Power BI Embedded](developer/qanda.md) se tratan en artículos independientes. 

Preguntas y respuestas es interactivo y divertido. A menudo, una pregunta conduce a otros usuarios como las visualizaciones revelan interesantes rutas para descubrir. Observe cómo Amanda muestra el uso de Preguntas y respuestas para crear visualizaciones, indagar en los objetos visuales y anclarlos en paneles.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>Parte 1: Uso de preguntas y respuestas en un panel en el servicio Power BI

En el servicio Power BI (app.powerbi.com), un panel contiene iconos anclados desde uno o varios conjuntos de datos, por lo que puede hacer preguntas sobre cualquiera de los datos contenidos en cualquiera de estos conjuntos de datos. Para ver los informes y conjuntos de datos que se usaron para crear el panel, seleccione **ver relacionados** desde la barra de menús.

![Ver conjuntos de datos e informes relacionados](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

El cuadro de pregunta de preguntas y respuestas se encuentra en la esquina superior izquierda del panel, donde se escribe la pregunta con lenguaje natural. ¿No ve el cuadro de preguntas y respuestas? Consulte [consideraciones y solución de problemas](consumer/end-user-q-and-a.md#considerations-and-troubleshooting) en el **preguntas y respuestas para los consumidores** artículo.  Preguntas y respuestas reconoce las palabras que escribe y determina dónde (en qué conjunto de datos) para encontrar la respuesta. Preguntas y respuestas también le ayuda a formar la pregunta con autocompletar, redefinición y otras ayudas textuales y visuales.

![Cuadro de preguntas y respuestas](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

La respuesta a su pregunta se muestra como una visualización interactiva y se actualiza cuando modifica la pregunta.

1. Abra un panel y coloque el cursor en el cuadro de pregunta. En la esquina superior derecha, seleccione **nuevo de preguntas y respuestas**.

    ![Experiencia de respuestas Q nuevas de Power BI](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Incluso antes de comenzar a escribir, Preguntas y respuestas muestra una nueva pantalla con sugerencias que le ayudarán a realizar la pregunta. Vea las frases y preguntas completadas que contiene los nombres de las tablas en los conjuntos de datos subyacente y puede incluso ver una lista si ha creado el propietario del conjunto de datos de preguntas [preguntas destacadas](service-q-and-a-create-featured-questions.md),

   ![Preguntas y respuestas a preguntas sugeridas](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Puede elegir una de estas preguntas como punto de partida y continuar perfeccionando la pregunta para encontrar una respuesta específica. O use un nombre de tabla para ayudarle a plantear una pregunta nueva.

2. Seleccione en la lista de preguntas, o comience a escribir su pregunta y seleccione en la lista desplegable sugerencias.

   ![Seleccione una pregunta en la lista](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. A medida que escribe una pregunta, preguntas y respuestas escoge la mejor visualización para mostrar la respuesta.

   ![Preguntas y respuestas almacena cuántos por estado](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. La visualización cambia dinámicamente en el que modifica la pregunta.

   ![Preguntas y respuestas cuántos almacena el estado como gráfico de barras](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. Al escribir una pregunta, Power BI busca la mejor respuesta en cualquier conjunto de datos que tenga un icono en ese panel.  Si todos los iconos son del *conjunto de datos A*, entonces su respuesta procederá del *conjunto de datos A*.  Si hay iconos del *conjunto de datos a* y *conjunto de datos b*, a continuación, preguntas y respuestas buscará la mejor respuesta en estos conjuntos de 2 datos.

   > [!TIP]
   > Tenga cuidado si solo tiene un icono del *conjunto de datos A* y lo quita de su panel; si hace esto, Preguntas y respuestas dejará de tener acceso al *conjunto de datos A*.
   >

5. Cuando esté satisfecho con el resultado, ancle la visualización a un panel seleccionando el icono de anclaje en la esquina superior derecha. Si el panel se compartió con usted o forma parte de una aplicación, no podrá anclarlo.

   ![Preguntas y respuestas de anclar el objeto visual](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Parte 2: Uso de Preguntas y respuestas en un informe en el servicio Power BI o en Power BI Desktop

Use Preguntas y respuestas para explorar el conjunto de datos y agregar visualizaciones al informe y los paneles. Un informe se basa en un único conjunto de datos y podría estar completamente en blanco o contener páginas enteras de visualizaciones. Que un informe esté en blanco no significa que no haya ningún dato para explorar; el conjunto de datos está vinculado al informe y está esperando para que lo explore y cree visualizaciones.  Para ver qué conjunto de datos se ha utilizado para crear un informe, abra el informe en la vista de lectura del servicio Power BI y seleccione **Ver relacionado** desde la barra de menús.

![Ver conjuntos de datos relacionados](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Para usar preguntas y respuestas en los informes, debe tener permisos de edición para el informe y conjunto de datos subyacente. En el [preguntas y respuestas para los consumidores](consumer/end-user-q-and-a.md) artículo, nos referiremos a ella como una *creador* escenario. Si en su lugar le *consumiendo* un informe que se ha compartido con usted, preguntas y respuestas no está disponible.

1. Abra un informe en la vista de edición (servicio Power BI) o la vista de informe (Power BI Desktop) y seleccione **formular una pregunta** desde la barra de menús.

    **Power BI Desktop**    
    ![Seleccione una pregunta en Power BI Desktop](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Servicio**    
    ![Seleccione una pregunta en el servicio Power BI](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Se muestra un cuadro de pregunta de Preguntas y respuestas en el lienzo del informe. En el ejemplo siguiente, el cuadro de pregunta se muestra en la parte superior de otra visualización. Esto es correcto, pero podría ser mejor agregar una página en blanco al informe antes de formular una pregunta.

    ![Cuadro de preguntas y respuestas](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Coloque el cursor en el cuadro de pregunta. A medida que escribe, Preguntas y respuestas muestra sugerencias para ayudarle a construir la pregunta.

   ![Escriba en el cuadro de preguntas y respuestas](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. A medida que escriba la pregunta, Preguntas y respuestas selecciona la mejor [visualización](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md) para mostrar la respuesta; la visualización cambia de forma dinámica a medida que se modifica la pregunta.

   ![Preguntas y respuestas crea una visualización](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Cuando tenga la visualización que desea, presione ENTRAR. Para guardar la visualización con el informe, seleccione **Archivo > Guardar**.

6. Interactúe con la nueva visualización. No importa cómo se creó la visualización, están disponibles la misma interactividad, formato y características.

   ![Interactuar con la visualización](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Si ha creado la visualización en el servicio Power BI, puede incluso [anclarla a un panel](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Indica a Preguntas y respuestas qué visualización usar
Con Preguntas y respuestas, no solo puede pedir a sus datos que sean suficientemente aclaratorios, también puede indicar a Power BI cómo mostrar la respuesta. Solo tiene que agregar "como un <visualization type>" al final de la pregunta.  Por ejemplo, "mostrar volumen de inventario por planta como un mapa" y "mostrar total del inventario como una tarjeta".  Pruébelo usted mismo.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
- Si se ha conectado a un conjunto de datos mediante una conexión dinámica o una puerta de enlace, Preguntas y respuestas deben ser [habilitado para ese conjunto de datos](service-q-and-a-direct-query.md).

- Ha abierto un informe y no ve la opción de Preguntas y respuestas. Si está utilizando el servicio Power BI, asegúrese de que abre el informe en la vista de edición. Si no se puede abrir la vista de edición significa que no tiene permisos de edición para el informe y puede usar preguntas y respuestas con ese informe específico.

## <a name="next-steps"></a>Pasos siguientes

- [Preguntas y respuestas para los consumidores](consumer/end-user-q-and-a.md)   
- [Sugerencias para hacer preguntas en Preguntas y respuestas](consumer/end-user-q-and-a-tips.md)   
- [Preparación de un libro para Preguntas y respuestas](service-prepare-data-for-q-and-a.md)  
- [Preparar un conjunto de datos local para preguntas y respuestas](service-q-and-a-direct-query.md)   
- [Anclar un icono al panel desde Preguntas y respuestas](service-dashboard-pin-tile-from-q-and-a.md)
