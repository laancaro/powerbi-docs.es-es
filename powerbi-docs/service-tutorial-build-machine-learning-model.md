---
title: 'Tutorial: Creación de un modelo de Machine Learning en Power BI (versión preliminar)'
description: En este tutorial, creará un modelo de Machine Learning en Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61407195"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutorial: Creación de un modelo de Machine Learning en Power BI (versión preliminar)

En este tutorial, se usa **Automated Machine Learning** para crear y aplicar un modelo de predicción binaria en Power BI. Se incluyen instrucciones para crear un flujo de datos de Power BI y usar las entidades definidas en él para entrenar y validar un modelo de aprendizaje automático directamente en Power BI. A continuación, usaremos ese modelo para puntuar los datos a fin de generar predicciones.

En primer lugar, creará un modelo de aprendizaje automático de predicción binaria para predecir la intención de compra de los compradores en línea según un conjunto de sus atributos de sesión en línea. Para este ejercicio se usa un conjunto de datos de aprendizaje automático de referencia. Después de entrenar un modelo, Power BI genera automáticamente un informe de validación en el que se explican los resultados del modelo. Luego, puede revisar el informe de validación y aplicar el modelo a los datos para su puntuación.

Este tutorial consta de los siguientes pasos:

> [!div class="checklist"]
> * Creación de un flujo de datos con los datos de entrada
> * Creación y entrenamiento de un modelo de aprendizaje automático
> * Revisión del informe de validación del modelo
> * Aplicación del modelo a una entidad de flujo de datos
> * Uso de la salida puntuada del modelo en un informe de Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Creación de un flujo de datos con los datos de entrada

La primera parte de este tutorial va dirigida a crear un flujo de datos con datos de entrada. Ese proceso conlleva algunos pasos, como se muestra en las secciones siguientes, que comienza con la obtención de datos.

### <a name="get-data"></a>Obtener datos

El primer paso para crear un flujo de datos es tener preparados los orígenes de datos. En nuestro caso, se va usar un conjunto de datos de aprendizaje automático de un conjunto de sesiones en línea, algunas de las cuales culminaron en una compra. El conjunto de datos contiene un conjunto de atributos sobre estas sesiones, que se usarán para entrenar nuestro modelo.

Puede descargar el conjunto de datos del sitio web de UC Irvine.  Para los fines de este tutorial, también está disponible en el siguiente vínculo: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Creación de las entidades

Para crear las entidades en su flujo de datos, inicie sesión en el servicio Power BI y vaya a un área de trabajo de su capacidad dedicada que tenga habilitada la versión preliminar de AI.

Si aún no tiene un área de trabajo, puede crear una; para ello, vaya a **Áreas de trabajo** en el menú de navegación izquierdo del servicio Power BI y seleccione **Crear área de trabajo de la aplicación** en la parte inferior del panel que aparece. Se abre un panel a la derecha para especificar los datos del área de trabajo. Escriba un nombre de área de trabajo y seleccione **Avanzado**. Confirme que el área de trabajo usa capacidad dedicada mediante el botón de radio, y que está asignada a una instancia de capacidad dedicada que tiene activada la versión preliminar de IA. Luego seleccione **Guardar**.

![Creación de un área de trabajo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Después de crear el área de trabajo, puede seleccionar **Omitir** en la parte inferior derecha de la pantalla de bienvenida, tal como se muestra en la siguiente imagen.

![Omitir si tiene un área de trabajo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Seleccione la pestaña **Flujos de datos (versión preliminar)** . Seleccione el botón **Crear** en la parte superior derecha del área de trabajo y, luego, **Flujo de datos**.

![Crear flujo de datos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Seleccione **Agregar entidades nuevas**. Se inicia un editor de **Power Query** en el explorador.

![Agregar entidad nueva](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Seleccione **Text/CSV File** (Archivo de texto/CSV) como origen de datos, como se muestra en la imagen siguiente.

![Archivo de texto/CSV seleccionado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

En **Conectarse a un origen de datos** que aparece a continuación, pegue el siguiente vínculo en *online_shoppers_intention.csv* en el cuadro **Ruta o dirección URL del archivo** y, luego, seleccione **Siguiente**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Ruta del archivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

El Editor de Power Query muestra una versión preliminar de los datos del archivo CSV. Seleccione **Transformar tabla** en la cinta de opciones de comando y, luego, seleccione **Usar la primera fila como encabezado** en el menú que aparece. Con esta acción, se agrega el paso de la consulta _Encabezados promovidos_ en la sección **Pasos aplicados** situado a la derecha de la pantalla. Puede cambiar el nombre de la consulta por otro más descriptivo en el cuadro **Nombre** que se encuentra en el panel derecho. Por ejemplo, podría cambiar el nombre de la consulta por _Online Visitor_ (Visitante en línea).

![Cambiar por un nombre descriptivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Algunos de los tipos de datos de atributo de este conjunto de datos son _numéricos_ o _booleanos_, si bien **Power Query** puede interpretarlos como cadenas. Seleccione el icono tipo de atributo situado en la parte superior de cada encabezado de columna para cambiar las columnas que se enumeran a continuación por los siguientes tipos:

* **Número decimal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Verdadero/falso:** Weekend; Revenue

![Cambio del tipo de datos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

El modelo de **predicción binaria** que se va a entrenar requiere un campo booleano como etiqueta que identifique los resultados de las observaciones anteriores. En este conjunto de datos, el atributo _Revenue_ indica la compra y este atributo ya está disponible como booleano. Por lo tanto, no es necesario agregar una columna calculada para la etiqueta. En otros conjuntos de datos, puede que tenga que transformar los atributos de etiqueta existentes en una columna booleana.

Seleccione el botón **Hecho** para cerrar el Editor de Power Query. Se muestra la lista de entidades con los datos de _Online Visitors_  (Visitantes en línea) que hemos agregado. Seleccione **Guardar** en la esquina superior derecha, proporcione un nombre para el flujo de datos y, luego, seleccione **Guardar** en el cuadro de diálogo, como se muestra en la siguiente imagen.

![Guardar el flujo de datos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Actualizar el flujo de datos

Al guardar el flujo de datos, se muestra una notificación que indica que el flujo de datos se ha guardado. Seleccione **Actualizar ahora** para ingerir los datos del origen en el flujo de datos.

![Actualizar ahora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Seleccione **Cerrar** en la esquina superior derecha y espere a que se complete la actualización del flujo de datos.

También puede actualizar su flujo de datos con los comandos **Acciones**. El flujo de datos muestra la marca de tiempo del momento de la actualización.

![Marca de tiempo de actualización](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Creación y entrenamiento de un modelo de aprendizaje automático

Tras finalizar la actualización, seleccione el flujo de datos. Para agregar un modelo de aprendizaje automático, seleccione el botón **Aplicar el modelo de ML** en la lista **Acciones** de la entidad base que contiene los datos de entrenamiento y la información de etiqueta y, luego, seleccione **Agregar un modelo de Machine Learning**.

![Agregar un modelo de Machine Learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

El primer paso para crear el modelo de aprendizaje automático es identificar los datos históricos, como el campo de etiqueta que quiere predecir. El modelo se crea con el aprendizaje de estos datos.

En el caso del conjunto de datos que vamos a usar, es el campo **Revenue** (Ingresos). Seleccione **Revenue** (Ingresos) como valor de "campo de resultados históricos" y, luego, seleccione **Siguiente**.

![Seleccionar datos históricos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

A continuación, es necesario seleccionar el tipo de modelo de aprendizaje automático que se va a crear. Power BI analiza los valores del campo de resultados históricos que ha identificado y sugiere los tipos de modelos de aprendizaje automático que se pueden crear para predecir ese campo.

En este caso, dado que vamos a predecir un resultado binario de si un usuario realiza una compra o no, seleccione **Predicción binaria** como tipo de modelo y, luego, seleccione Siguiente.

![Predicción binaria seleccionada](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Seguidamente, Power BI realiza un examen preliminar de los datos y sugiere las entradas que el modelo podría usar. Tiene la opción de personalizar los campos de entrada usados en el modelo. En nuestro conjunto de datos mantenido, para seleccionar todos los campos, active la casilla junto al nombre de la entidad. Seleccione **Siguiente** para aceptar las entradas.

![Activar la casilla Siguiente](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

En el paso final, debemos proporcionar un nombre para el modelo, así como las etiquetas descriptivas de los resultados que se van a usar en el informe generado automáticamente que resumirá los resultados de la validación del modelo. Después, tenemos que asignar al modelo el nombre _Purchase Intent Prediction_ (Predicción de la intención de compra) y a las etiquetas de verdadero y falso _Purchase_ (Compra) y _No-Purchase_ (No compra). Luego seleccione **Guardar**.

![Guardar el modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Nuestro modelo de aprendizaje automático ya está listo para el entrenamiento. Seleccione **Actualizar ahora** para empezar a entrenar el modelo.

![Actualizar ahora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

El proceso de entrenamiento comenzará con el muestreo y la normalización de los datos históricos y la división del conjunto de datos en dos nuevas entidades *Purchase Intent Prediction Training Data* (Datos de entrenamiento de predicción de la intención de compra) y *Purchase Intent Prediction Testing Data* (Datos de prueba de predicción de la intención de compra).

Dependiendo del tamaño del conjunto de datos, el proceso de entrenamiento puede tardar desde unos minutos hasta un par de horas. En este punto, puede ver el modelo en la pestaña **Modelos de Machine Learning** del flujo de datos. El estado _Listo_ indica que el modelo se ha puesto en cola para el entrenamiento o ya se está entrenando.

![Listo para entrenamiento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Mientras el modelo se está entrenando, no podrá ver ni editar el flujo de datos. Puede confirmar que el modelo se está entrenando y validando mediante el estado del flujo de datos. Este estado aparece como una actualización de datos en curso en la pestaña **Flujos de datos** del área de trabajo.

![En curso](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Una vez completado el entrenamiento del modelo, el flujo de datos muestra una hora de actualización. Para confirmar que el modelo está entrenado, vaya a la pestaña **Modelos de Machine Learning** en el flujo de datos. El modelo que ha creado debe mostrar el estado **Entrenado** y la hora de **Último aprendizaje** debe estar ahora actualizada.

![Último aprendizaje el](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Revisión del informe de validación del modelo

Para revisar el informe de validación del modelo, vaya a **Modelos de Machine Learning** y seleccione el botón **Ver informe de rendimiento y aplicar modelo** en la columna **Acciones** del modelo. En este informe se describe cómo es probable que funcione el modelo de aprendizaje automático.

En la página **Rendimiento del modelo** del informe, seleccione **Influenciadores clave** para ver los principales predictores del modelo. Puede seleccionar uno de los predictores para ver cómo se asocia la distribución de resultados con ese predictor.

![Rendimiento del modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Puede usar el control deslizante **Umbral de probabilidad** de la página Rendimiento del modelo para examinar su influencia en la precisión y la recuperación del modelo.

![Umbral de probabilidad](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Las demás páginas del informe describen las métricas estadísticas de rendimiento del modelo.

El informe también incluye una página de detalles de aprendizaje que describe las distintas iteraciones que se ejecutaron, cómo se extrajeron las características de las entradas y los hiperparámetros del modelo final usado.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Aplicación del modelo a una entidad de flujo de datos

Seleccione el botón **Aplicar modelo** en la parte superior del informe para invocar este modelo cuando se actualice el flujo de datos. En el cuadro de diálogo **Aplicar**, puede especificar la entidad de destino que tiene los datos de origen a los que se debe aplicar el modelo.

![Aplicar el modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Cuando se le solicite, debe seleccionar **Actualizar** para actualizar el flujo de datos a fin de obtener una vista previa de los resultados del modelo.

Al aplicar el modelo se crea una entidad, con el sufijo **enriched <nombre_del_modelo>** anexado a la entidad a la que se aplicó el modelo. En nuestro caso, al aplicar el modelo a la entidad **OnlineShoppers** se crea **OnlineShoppers enriched Purchase Intent Prediction**, que incluye la salida de predicción del modelo.

Al aplicar un modelo de predicción binaria, se agregan tres columnas con el resultado de predicción, la puntuación de probabilidad y los principales influenciadores específicos del registro para la predicción, cada uno con el nombre de columna especificado como prefijo.

![Tres columnas de resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Debido a un problema conocido, solo se puede tener acceso a las columnas de salida puntuadas de la entidad enriquecida desde Power BI Desktop. Para obtener una vista previa de ellas en el servicio, debe usar una entidad de vista previa especial.

Cuando se haya completado la actualización del flujo de entrada, puede seleccionar la entidad **OnlineShoppers enriched Purchase Intent Prediction Preview** para ver los resultados.

![Ver los resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Uso de la salida puntuada del modelo en un informe de Power BI

Para usar la salida puntuada del modelo de aprendizaje automático, puede conectarse a su flujo de entrada desde Power BI Desktop mediante el conector de flujos de datos. Ahora se puede usar la entidad **OnlineShoppers enriched Purchase Intent Prediction** para incorporar las predicciones del modelo en los informes de Power BI.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha creado y aplicado un modelo de predicción binaria en Power BI mediante estos pasos:

* Creación de un flujo de datos con los datos de entrada
* Creación y entrenamiento de un modelo de aprendizaje automático
* Revisión del informe de validación del modelo
* Aplicación del modelo a una entidad de flujo de datos
* Uso de la salida puntuada del modelo en un informe de Power BI

Para más información sobre la automatización de Machine Learning en Power BI, consulte [Automated Machine Learning en Power BI (versión preliminar) ](service-machine-learning-automated.md).
