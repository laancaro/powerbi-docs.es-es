---
title: Aprendizaje automático automatizado en Power BI (versión preliminar)
description: Aprenda a usar automatizada Machine Learning (AutoML) en Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236835"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Aprendizaje automático automatizado en Power BI (versión preliminar)

Automatizadas aprendizaje automático (AutoML) para flujos de datos permite a los analistas de negocios entrenar, validar e invocar los modelos de Machine Learning directamente en Power BI. Incluye una experiencia simple para crear un nuevo modelo de aprendizaje automático donde los analistas pueden utilizar sus flujos de datos para especificar los datos de entrada para entrenar el modelo. El servicio automáticamente extrae las características más relevantes, selecciona un algoritmo apropiado y optimiza y valida el modelo de aprendizaje automático. Después se entrena un modelo, Power BI genera automáticamente un informe que incluye los resultados de validación que se explica el rendimiento y los resultados a los analistas. A continuación, se puede invocar el modelo en los datos nuevos o actualizados en el flujo de datos.

![Pantalla de Machine learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Automatizada machine learning está disponible para los flujos de datos que se hospedan en las capacidades de Power BI Premium e incrustada. En esta versión preliminar, AutoML permite entrenar modelos de aprendizaje automático para los modelos de predicción binaria, clasificación y regresión.

## <a name="working-with-automl"></a>Trabajar con AutoML

[Power BI dataflows](service-dataflows-overview.md) ofrecen la preparación de datos de autoservicio para big data. AutoML le permite aprovechar el esfuerzo de preparación de datos para la creación de modelos de aprendizaje automático, directamente en Power BI.

AutoML en Power BI permite a los analistas de datos usar flujos de datos para crear modelos de aprendizaje automático con una experiencia simplificada, usando los conocimientos de Power BI solo. La mayoría de la ciencia de datos detrás de la creación de los modelos de aprendizaje automático se automatiza mediante Power BI, con las barreras de seguridad para asegurarse de que el modelo generado tiene buena calidad y la visibilidad para proporcionarle una completa perspectiva de proceso usado para crear el modelo de aprendizaje automático.

AutoML admite la creación de **predicción binaria**, **clasificación**, y **regresión** modelos para flujos de datos. Estos son tipos de modelos de aprendizaje automático supervisado, lo que significa que aprenden de los resultados conocidos de observaciones anteriores para predecir los resultados de otros observaciones. El conjunto de datos de entrada para entrenar un modelo AutoML es un conjunto de registros que son **con la etiqueta** con los resultados conocidos.

AutoML en Power BI se integra [automatizada ML](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) desde el [servicio Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) para crear los modelos de aprendizaje automático. Sin embargo, no necesita una suscripción de Azure para usar AutoML en Power BI. El proceso de entrenamiento y hospedar los modelos de aprendizaje automático se gestiona totalmente mediante el servicio Power BI.

Después se entrena un modelo de aprendizaje automático, AutoML genera automáticamente un informe de Power BI que explica el rendimiento de su modelo de aprendizaje automático probable. AutoML enfatiza explainability, resaltando los influenciadores clave entre las entradas que influyen en las predicciones devueltas por el modelo. El informe también incluye las métricas clave para el modelo, según el tipo de modelo de aprendizaje automático.

Otras páginas del informe generado muestran el resumen de estadístico del modelo y los detalles de entrenamiento. Es el resumen estadístico de interés para los usuarios que le gustaría ver las medidas de ciencia de datos estándar de rendimiento para el modelo. Los detalles de entrenamiento resumen todas las iteraciones que se ejecutaron para crear el modelo, con los parámetros de modelado asociadas. También se describe cómo cada entrada se usó para crear el modelo de aprendizaje automático.

A continuación, puede aplicar el modelo de aprendizaje automático a los datos para puntuación. Cuando se actualiza el flujo de datos, las predicciones a partir de su modelo de aprendizaje automático se aplican automáticamente a los datos. Power BI también incluye una explicación individualizada para cada puntuación de predicción específicas que genera el modelo de aprendizaje automático.

## <a name="creating-a-machine-learning-model"></a>Creación de un modelo de aprendizaje automático

En esta sección se describe cómo crear un modelo de aprendizaje AutoML. 

### <a name="data-prep-for-creating-an-ml-model"></a>Preparación de datos para crear un modelo de aprendizaje automático

Para crear un modelo de aprendizaje automático en Power BI, primero debe crear un flujo de datos para los datos con la información histórica del resultado, que se utiliza para entrenar el modelo de aprendizaje automático. Para obtener más información sobre cómo configurar el flujo de datos, vea [de preparación de datos de autoservicio en Power BI](service-dataflows-overview.md).

En la versión actual, Power BI usa datos de solo una sola entidad para entrenar el modelo de aprendizaje automático. Por lo que si los datos históricos constan de varias entidades, debe unir manualmente los datos en una entidad única de flujo de datos. También debe agregar las columnas calculadas para todas las métricas empresariales que pueden ser indicadores seguros para el resultado que está intentando predecir.

AutoML tiene requisitos específicos de datos para entrenar un modelo de aprendizaje automático. Estos requisitos se describen en las secciones siguientes, según los tipos de modelo correspondiente.

### <a name="configuring-the-ml-model-inputs"></a>Configurar las entradas del modelo de aprendizaje automático

Para crear un modelo AutoML, seleccione el icono de aprendizaje automático en el **acciones** columna de la entidad de flujo de datos con los datos históricos y seleccione **agregar un modelo de aprendizaje automático**.

![Agregar un modelo de aprendizaje automático](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Se inicia una experiencia simplificada, que consta de un asistente que le guíe a través del proceso de creación del modelo de aprendizaje automático. El asistente incluye los siguientes pasos sencillos.

1. Seleccione la entidad con los datos históricos del resultado y el campo para el que desea que una predicción
2. Elija un tipo de modelo según el tipo de predicción que gustaría ver
3. Seleccione las entradas que desea que el modelo que se usará como señales predictivas
4. El modelo de nombre y guardar la configuración

El campo resultado históricos identifica el atributo de etiqueta para entrenar el modelo de aprendizaje automático, que se muestra en la siguiente imagen.

![Seleccione los datos históricos de resultado](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Cuando se especifica el campo resultado históricos, AutoML analiza los datos de etiqueta para identificar los tipos de modelos de aprendizaje automático que pueden aprender de los datos y sugiere el tipo de modelo de aprendizaje automático más probable que se puede entrenar. 

> [!NOTE]
> Algunos tipos de modelo no es posible que se admite para los datos que ha seleccionado.

AutoML también analiza todos los campos de la entidad seleccionada para sugerir las entradas que se pueden usar para entrenar el modelo de aprendizaje automático. Este proceso es aproximado y se basa en el análisis estadístico, por lo que debe revisar las entradas usadas. Las entradas que son dependientes en el campo resultado históricos (o el campo de etiqueta) no deben usarse para entrenar el modelo de aprendizaje automático, ya que afectará a su rendimiento.

![Personalizar campos de entrada](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

En el paso final, puede asignar nombre al modelo y guardar su configuración.

En esta fase, deberá actualizar el flujo de datos, que comienza el proceso de entrenamiento para el modelo de aprendizaje automático.

### <a name="ml-model-training"></a>Entrenamiento del modelo de aprendizaje automático

Entrenamiento de modelos AutoML es una parte de la actualización de flujo de datos. En primer lugar, AutoML prepara los datos para el entrenamiento.

AutoML divide los datos históricos proporcionados en conjuntos de datos de prueba y entrenamiento. El conjunto de datos de prueba es un conjunto de datos de exclusión que se utiliza para validar el rendimiento del modelo después del entrenamiento. Estos se realizan como **entrenar y probar** entidades en el flujo de datos. AutoML usa la validación cruzada para la validación del modelo.

A continuación, cada campo de entrada se analiza y se aplica, que reemplaza los valores que faltan por valores sustituidos. AutoML utiliza un par de estrategias de imputación diferentes. A continuación, cualquier muestreo necesario y la normalización se aplican a los datos.

Se aplica AutoML varias transformaciones son cada campo de entrada seleccionado según su tipo de datos y sus propiedades estadísticas. AutoML usa estas transformaciones para extraer las características para su uso en entrenar el modelo de aprendizaje automático.

El proceso de entrenamiento de modelos AutoML consta de un máximo de 50 iteraciones con algoritmos de modelado diferentes y la configuración de hiperparámetros para encontrar el modelo con el mejor rendimiento. Se evalúa el rendimiento de cada uno de estos modelos mediante validación con el conjunto de datos de prueba de exclusión. Durante este paso de aprendizaje, AutoML crea varias canalizaciones para el entrenamiento y validación de las iteraciones. El proceso de evaluar el rendimiento de los modelos puede tardar tiempo, desde varios minutos en un par de horas, dependiendo del tamaño del conjunto de datos y los recursos de capacidad dedicada disponibles.

En algunos casos, el modelo final generado puede usar el conjunto de aprendizaje, donde se utilizan varios modelos para proporcionar un mejor rendimiento predictivo.

### <a name="automl-model-explainability"></a>AutoML explainability de modelo

Una vez entrenado el modelo, AutoML analiza la relación entre las características de entrada y la salida del modelo. Evalúa la magnitud y la dirección del cambio en la salida del modelo del conjunto de datos de prueba de exclusión para cada característica de entrada. Esto se conoce como el *importancia de características*.

![Importancia de características](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>Informe del modelo AutoML

AutoML genera un informe de Power BI que resume el rendimiento del modelo durante la validación, junto con la importancia de la función global. El informe resume los resultados de aplicar el modelo de aprendizaje automático a los datos de prueba de exclusión y comparar las predicciones con los valores de resultado conocido.

Puede revisar el informe de modelo para estudiar su rendimiento. También puede validar que los influenciadores clave del modelo se alinean con la información empresarial sobre los resultados conocidos.

Los gráficos y las medidas que se usan para describir el rendimiento del modelo en el informe dependen del tipo de modelo. En las secciones siguientes se describen estos gráficos de rendimiento y las medidas.

Páginas adicionales en el informe pueden describir medidas estadísticas sobre el modelo desde una perspectiva de ciencia de datos. Por ejemplo, el **predicción binaria** informe incluye un gráfico de ganancia y la curva ROC para el modelo.

Los informes también incluyen un **detalles del aprendizaje** se ejecuta la página que incluye una descripción de cómo el modelo se entrenó e incluye un gráfico que describe el rendimiento del modelo a través de cada una de las iteraciones.

![Detalles del entrenamiento](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Otra sección en esta página describe cómo imputación utiliza el método para rellenar los valores que faltan para los campos de entrada, así como la forma se transforma cada campo de entrada para extraer las características usadas en el modelo. También incluye los parámetros utilizados por el modelo final.

![Para obtener más información para el modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Si el modelo generado usa el aprendizaje de conjunto, la **detalles del aprendizaje** página también incluye una sección que describe el peso de cada modelo que lo constituyen en conjunto, así como sus parámetros.

![En el conjunto de peso](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Aplicar el modelo AutoML

Si está satisfecho con el rendimiento del modelo de aprendizaje automático creado, puede aplicar a los datos nuevos o actualizados cuando se actualiza el flujo de datos. Puede hacerlo desde el informe del modelo, seleccionando la **aplicar** situado en la esquina superior derecha.

Para aplicar el modelo de aprendizaje automático, debe especificar el nombre de la entidad a la que se debe aplicar y un prefijo para las columnas que se agregarán a esta entidad para la salida del modelo. El prefijo predeterminado para los nombres de columna es el nombre del modelo. El *aplicar* función puede incluir parámetros adicionales específicos del tipo de modelo.

Aplicar el modelo de aprendizaje automático, crea una nueva entidad de flujo de datos con el sufijo **enriquecido < model_name >** . Por ejemplo, si aplica el _PurchaseIntent_ modelos a la _OnlineShoppers_ entidad, se generará la salida de la **OnlineShoppers enriquecido PurchaseIntent**.

Actualmente, no se puede usar la entidad de salida para obtener una vista previa de los resultados del modelo de aprendizaje automático en el editor de Power Query. Las columnas de salida siempre muestran null como resultado. Para ver los resultados, una segunda salida de la entidad con el sufijo **enriquecido < model_name > versión preliminar** se crea cuando se aplica el modelo.

Debe actualizar el flujo de datos, para obtener una vista previa de los resultados en el Editor de consultas.

![Editor de consultas](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Al aplicar el modelo, AutoML siempre mantiene las predicciones actualizado cuando se actualiza el flujo de datos.

AutoML también incluye una explicación para cada fila que puntúa individualizada en la entidad de salida.

Para usar la información y las predicciones del modelo de aprendizaje automático en un informe de Power BI, puede conectarse a la entidad de salida desde Power BI Desktop mediante el **dataflows** conector.

## <a name="binary-prediction-models"></a>Modelos de predicción binario

Modelos de predicción binarios, conocidos más formalmente como **modelos de clasificación binaria**, se usan para clasificar un conjunto de datos en dos grupos. Se usa para predecir los eventos que pueden tener los resultados binarios, por ejemplo, si convierte una oportunidad de venta, si se abandona una cuenta, si se dará una factura en el tiempo; Si una transacción es fraudulento y así sucesivamente.

Puesto que el resultado es binario, Power BI espera que la etiqueta para un modelo de predicción binario ser un valor booleano, con resultados conocidos con la etiqueta que se va a **true** o **false**. Por ejemplo, en un modelo de conversión de la oportunidad de venta, oportunidades de ventas ganados se etiquetan true, los que se han perdido se etiquetan en falsos y las oportunidades de ventas pendientes se etiquetan null.

El resultado de un modelo de predicción binaria es una puntuación de probabilidad, que identifica la probabilidad de que se logran el resultado correspondiente al valor de etiqueta que se va a true.

### <a name="training-a-binary-prediction-model"></a>Entrenar un modelo de predicción binario

Para crear un modelo de predicción binario, la entidad de entrada que contiene los datos de entrenamiento debe tener un campo booleano como el campo de resultado histórica para identificar los últimos resultados conocidos.

Requisitos previos:

* Se debe usar un campo booleano como el campo resultado históricos
* Se requiere para cada clase de resultados de un mínimo de 50 filas de datos históricos

En general, si los resultados anteriores se identifican los campos de un tipo de datos diferente, puede agregar una columna calculada para transformar estos elementos en un valor booleano mediante Power Query.

El proceso de creación de un modelo de predicción binario sigue el mismo pasos como otros modelos AutoML, se describe en la sección **configurar las entradas del modelo de aprendizaje automático** anteriormente.

### <a name="binary-prediction-model-report"></a>Informe del modelo de predicción binario

El modelo de predicción binario genera como salida una probabilidad de que un registro proporcionará el resultado que define el valor de etiqueta booleana como True. El informe incluye una segmentación de datos para el umbral de probabilidad, lo que influye en cómo se interpretan las puntuaciones por encima y por debajo del umbral de probabilidad.

El informe describe el rendimiento del modelo en términos de *verdaderos positivos*, *falsos positivos*, *verdaderos* y *falsos negativos*. True positivos y negativos verdaderos son los resultados predichos correctamente para las dos clases en los datos de resultado. Falsos positivos son los resultados que tenían la etiqueta real booleano del valor False, pero se predijeron como True. Por el contrario, falsos negativos son los resultados, donde el valor de etiqueta booleana real era True pero se predijeron como False.

Medidas, como la precisión y la recuperación, describen el efecto del umbral de probabilidad en los resultados. Puede usar a la segmentación de umbral de probabilidad para seleccionar un umbral que se obtenga un compromiso equilibrado entre la precisión y la recuperación.

![Vista previa de precisión](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

El **precisión informe** página del informe del modelo incluye la *ganancias acumuladas* gráfico y la ROC de curva del modelo. Estos son medidas estadísticas de rendimiento del modelo. Los informes incluyen descripciones de los gráficos que se muestra.

![Pantalla de informe de precisión](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Aplicar un modelo de predicción binario

Para aplicar un modelo de predicción binario, debe especificar la entidad con los datos a la que desea aplicar las predicciones del modelo de aprendizaje automático. Otros parámetros incluyen el prefijo del nombre de columna de salida y el umbral de probabilidad para clasificar el resultado de predicción.

![Entradas de predicción](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Cuando se aplica un modelo de predicción binario, agrega tres columnas de salida a la entidad de salida enriquecida. Estos son los **PredictionScore**, **PredictionOutcome** y **PredictionExplanation**. Los nombres de columna en la entidad tienen el prefijo especificado cuando se aplica el modelo.

El **PredictionOutcome** columna contiene la etiqueta de resultado de predicción. Los registros con las probabilidades que superan el umbral se ha predicho que probablemente lograr el resultado y los anteriores se ha predicho tan pocas probabilidades de alcanzar el resultado.

El **PredictionExplanation** columna contiene una explicación con la influencia específica que tenían las características de entrada en el **PredictionScore**. Se trata de una colección con formato JSON de ponderaciones de las características de entrada para la predicción.

## <a name="classification-models"></a>Modelos de clasificación

Los modelos de clasificación se usan para clasificar un conjunto de datos en varios grupos o clases.  Se usa para predecir los eventos que pueden tener uno de varios resultados posibles, por ejemplo, si es probable que tenga una muy alta, alta, Media o baja valor de duración; un cliente Si el riesgo para el valor predeterminado es alto, moderado, baja o muy baja; y así sucesivamente.

El resultado de un modelo de clasificación es una puntuación de probabilidad, que identifica la probabilidad de que un registro proporcionará los criterios para una clase determinada.

### <a name="training-a-classification-model"></a>Entrenar un modelo de clasificación

La entidad de entrada que contiene los datos de entrenamiento de un modelo de clasificación debe tener una cadena o un campo numérico como el campo de resultado históricos, que identifica los últimos resultados conocidos.

Requisitos previos:

* Se requiere para cada clase de resultados de un mínimo de 50 filas de datos históricos

El proceso de creación de un modelo de clasificación sigue el mismo pasos como otros modelos AutoML, se describe en la sección **configurar las entradas del modelo de aprendizaje automático** anteriormente.

### <a name="classification-model-report"></a>Informe del modelo de clasificación

La clasificación de informe del modelo se ha generado aplicando el modelo de aprendizaje automático para la exclusión probar datos y comparación de la clase de predicción para un registro con la clase real conocida.

Informe del modelo incluye un gráfico que incluye el desglose de los registros clasificados correctamente e incorrectamente para cada clase conocido.

![Informe del modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Una obtención de detalles de más específico de la clase permite un análisis de cómo se distribuyen las predicciones para una clase conocida. Esto incluye las otras clases en el que los registros de que conoce la clase puedan que se clasificaron incorrectamente.

![Informe de análisis](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

La explicación del modelo en el informe también incluye los indicadores principales para cada clase.

Informe del modelo de clasificación también incluye una página de detalles del aprendizaje similar a las páginas para otros tipos de modelos, como se describe en la sección **informe del modelo AutoML** anteriormente en este artículo.

### <a name="applying-a-classification-model"></a>Aplicar un modelo de clasificación

Para aplicar un modelo de aprendizaje automático de clasificación, debe especificar la entidad con los datos de entrada y el prefijo del nombre de columna de salida.

Cuando se aplica un modelo de clasificación, lo agrega que tres columnas de salida para la entidad de salida enriquecida. Estos son los **PredictionScore**, **PredictionClass** y **PredictionExplanation**. Los nombres de columna en la entidad tienen el prefijo especificado cuando se aplica el modelo.

El **PredictionClass** columna contiene la clase de predicción más probable es que para el registro. El **PredictionScore** columna contiene la lista de las puntuaciones de probabilidad para el registro para cada clase posibles.

El **PredictionExplanation** columna contiene una explicación con la influencia específica que tenían las características de entrada en el **PredictionScore**. Se trata de una colección con formato JSON de ponderaciones de las características de entrada para la predicción.

## <a name="regression-models"></a>Modelos de regresión

Se utilizan los modelos de regresión para predecir un valor, como los ingresos puedo llevarse a cabo desde una cantidad de ventas, el valor de duración de una cuenta, la cantidad de una factura de clientes que es probable que se paga por la fecha en la que se puede pagar una factura , y así sucesivamente.

El resultado de un modelo de regresión es el valor de predicción.

### <a name="training-a-regression-model"></a>Entrenar un modelo de regresión

La entidad de entrada que contiene los datos de entrenamiento de un modelo de regresión debe tener un campo numérico como el campo de resultado históricos, que identifica los últimos valores de resultado conocido.

Requisitos previos:

* Se requiere para un modelo de regresión un mínimo de 100 filas de datos históricos

El proceso de creación de un modelo de regresión sigue el mismo pasos como otros modelos AutoML, se describe en la sección **configurar las entradas del modelo de aprendizaje automático** anteriormente.

### <a name="regression-model-report"></a>Informe del modelo de regresión

Al igual que los otros informes de modelo AutoML, el informe de regresión se basa en los resultados de aplicar el modelo a los datos de prueba de exclusión.

Informe del modelo incluye un gráfico que compara los valores de predicción con el valor real. En este gráfico, la distancia desde la diagonal indica el error en la predicción.

El gráfico de error residual muestra la distribución del porcentaje de error promedio para los distintos valores del conjunto de datos de prueba de exclusión. El eje horizontal representa el promedio del valor real para el grupo, con el tamaño de la burbuja que se muestra la frecuencia o el recuento de valores en ese intervalo. El eje vertical es el error promedio residual.

![Gráfico de error residual](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Informe del modelo de regresión también incluye una página de detalles del aprendizaje, como los informes para otros tipos de modelos, como se describe en la sección **informe del modelo AutoML** anteriormente.

### <a name="applying-a-regression-model"></a>Aplicar un modelo de regresión

Para aplicar un modelo de aprendizaje automático de regresión, debe especificar la entidad con los datos de entrada y el prefijo del nombre de columna de salida.

![Aplicar una regresión](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Cuando se aplica un modelo de regresión, agrega dos columnas de salida a la entidad de salida enriquecida. Estos son los **PredictionValue**, y **PredictionExplanation**. Los nombres de columna en la entidad tienen el prefijo especificado cuando se aplica el modelo.

El **PredictionValue** columna contiene el valor de predicción para el registro en función de los campos de entrada. El **PredictionExplanation** columna contiene una explicación con la influencia específica que tenían las características de entrada en el **PredictionValue**. Se trata de una colección con formato JSON de ponderaciones de las características de entrada.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporciona información general sobre automatizada de Machine Learning para flujos de datos en el servicio Power BI. Los siguientes artículos también pueden resultarle útiles.

* [Tutorial: Crear un modelo de Machine Learning en Power BI (versión preliminar)](service-tutorial-build-machine-learning-model.md)
* [Tutorial: Uso de Cognitive Services en Power BI](service-tutorial-use-cognitive-services.md)
* [Tutorial: Invocación de un modelo de Machine Learning Studio en Power BI (versión preliminar)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services en Power BI (versión preliminar)](service-cognitive-services.md)
* [Integración de Azure Machine Learning en Power BI (versión preliminar)](service-machine-learning-integration.md)

Para más información sobre los flujos de datos, puede leer estos artículos:
* [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
* [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso de flujos de datos con orígenes de datos locales](service-dataflows-on-premises-gateways.md)
* [Recursos para desarrolladores sobre flujos de datos de Power BI](service-dataflows-developer-resources.md)
* [Integración de flujos de datos y Azure Data Lake (versión preliminar)](service-dataflows-azure-data-lake-integration.md)


