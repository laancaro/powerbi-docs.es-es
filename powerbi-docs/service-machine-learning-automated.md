---
title: Aprendizaje automático automatizado en Power BI (versión preliminar)
description: Aprenda a usar Automated Machine Learning (AutoML) en Power BI
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236835"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Aprendizaje automático automatizado en Power BI (versión preliminar)

Automated Machine Learning (AutoML) para flujos de trabajo permite a los analistas de negocios entrenar, validar e invocar modelos de Machine Learning directamente en Power BI. Incluye una experiencia sencilla para crear un modelo de aprendizaje automático en el que los analistas pueden usar sus flujos de datos para especificar los datos de entrada para entrenar el modelo. El servicio extrae automáticamente las características más significativas, selecciona un algoritmo adecuado y ajusta y valida el modelo de aprendizaje automático. Después de entrenar un modelo, Power BI genera automáticamente un informe con los resultados de validación que explica el rendimiento y los resultados a los analistas. El modelo se puede invocar sobre los datos nuevos o actualizados del flujo de datos.

![Pantalla de Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Automated Machine Learning está disponible únicamente para flujos de datos hospedados en las capacidades Premium y Embedded. En esta versión preliminar, AutoML le permite entrenar modelos de aprendizaje automático de predicción binaria, clasificación y regresión.

## <a name="working-with-automl"></a>Uso de AutoML

Los [flujos de datos de Power BI](service-dataflows-overview.md) ofrecen autoservicio de preparación de los datos para macrodatos. AutoML le permite aprovechar el trabajo de preparación de los datos para compilar modelos de aprendizaje automático, directamente en Power BI.

AutoML en Power BI permite a los analistas de datos usar flujos de datos para compilar modelos de aprendizaje automático con una experiencia simplificada, solo con usar los conocimientos de Power BI. La mayor parte de la ciencia de datos que subyace a la creación de los modelos de aprendizaje automático se automatiza mediante Power BI, con protecciones para garantizar que el modelo generado tenga buena calidad, y visibilidad para proporcionarle una visión completa del proceso que se usa para crearlo.

AutoML admite la creación de modelos de **predicción binaria**, **clasificación** y **regresión** para flujos de datos. Estos son tipos de modelos de aprendizaje automático supervisados, lo que significa que aprenden de los resultados conocidos de las observaciones anteriores para predecir los resultados de otras observaciones. El conjunto de datos de entrada para entrenar un modelo de AutoML es un conjunto de registros que se **etiquetan** con los resultados conocidos.

AutoML en Power BI integra el [aprendizaje automático automatizado](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) del [servicio Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) para crear los modelos de aprendizaje automático. Sin embargo, no necesita una suscripción a Azure para usar AutoML en Power BI. El proceso de entrenamiento y hospedaje de los modelos de aprendizaje automático se administra por completo en el servicio Power BI.

Después de entrenar un modelo de aprendizaje automático, AutoML genera automáticamente un informe de Power BI que explica el rendimiento probable del modelo. AutoML acentúa la explicabilidad y resalta los influenciadores clave en sus entradas que influyen en las predicciones que devuelve el modelo. El informe también incluye métricas clave para el modelo, según el tipo de modelo de aprendizaje automático.

Otras páginas del informe generado muestran el resumen estadístico del modelo y los detalles del entrenamiento. El resumen estadístico es de interés para los usuarios que desean ver las medidas estándar de ciencia de datos del rendimiento del modelo. Los detalles de entrenamiento resumen todas las iteraciones que se ejecutaron para crear el modelo, con los parámetros de modelado asociados. También se describe cómo se usó cada entrada para crear el modelo de aprendizaje automático.

Luego, puede aplicar su modelo de aprendizaje automático a los datos para puntuarlos. Cuando se actualiza el flujo de datos, las predicciones del modelo de aprendizaje automático se aplican automáticamente a los datos. Power BI también incluye una explicación individualizada de cada puntuación de predicción específica que genera el modelo de aprendizaje automático.

## <a name="creating-a-machine-learning-model"></a>Creación de un modelo de aprendizaje automático

En esta sección se describe cómo crear un modelo de aprendizaje de AutoML. 

### <a name="data-prep-for-creating-an-ml-model"></a>Preparación de los datos para crear un modelo de aprendizaje automático

Para crear un modelo de aprendizaje automático en Power BI, primero debe crear un flujo de datos para los datos con la información de resultados históricos; esta información se usa para entrenar el modelo de aprendizaje automático. Para más información sobre cómo configurar el flujo de datos, consulte [Autoservicio de preparación de los datos en Power BI](service-dataflows-overview.md).

En la versión actual, Power BI emplea datos de una sola entidad para entrenar el modelo de aprendizaje automático. Por tanto, si los datos históricos se componen de varias entidades, debe combinar manualmente los datos en una sola entidad de flujo de datos. También debe agregar columnas calculadas para las métricas empresariales que puedan ser unos fuertes predictores del resultado que intenta predecir.

AutoML presenta unos requisitos de datos específicos para entrenar un modelo de aprendizaje automático. Estos requisitos se describen en las secciones siguientes, en función de los tipos de modelo respectivos.

### <a name="configuring-the-ml-model-inputs"></a>Configuración de las entradas del modelo de aprendizaje automático

Para crear un modelo de AutoML, seleccione el icono de aprendizaje automático en la columna **Acciones** de la entidad de flujo de datos con los datos históricos, y seleccione **Agregar un modelo de Machine Learning**.

![Adición de un modelo de Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Comienza una experiencia simplificada, que consta de un asistente que le guía por el proceso de creación del modelo de aprendizaje automático. El asistente incluye estos sencillos pasos.

1. Seleccione la entidad con los datos de resultados históricos y el campo del que quiere una predicción.
2. Elija un tipo de modelo según el tipo de predicción que quiere ver.
3. Seleccione las entradas que quiere que use el modelo como señales predictivas.
4. Asigne un nombre al modelo y guarde la configuración.

El campo de resultados históricos identifica el atributo de etiqueta para entrenar el modelo de aprendizaje automático, que se muestra en la siguiente imagen.

![Selección de los datos de resultados históricos](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Al especificar el campo de resultados históricos, AutoML analiza los datos de etiqueta para identificar los tipos de modelos de aprendizaje automático que se pueden entrenar para esos datos y sugiere el tipo más probable. 

> [!NOTE]
> Puede que algunos tipos de modelos no se admitan con los datos que ha seleccionado.

AutoML también analiza todos los campos de la entidad seleccionada para sugerir las entradas que se pueden usar para entrenar el modelo de aprendizaje automático. Este proceso es aproximado y se basa en análisis estadísticos, por lo que debe revisar las entradas usadas. Las entradas que dependan del campo de resultados históricos (o del campo de etiqueta) no se deben usar para entrenar el modelo de aprendizaje automático, dado que afectan al rendimiento.

![Personalizar campos de entrada](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

En el paso final, puede asignar un nombre al modelo y guardar su configuración.

En esta fase, se le pide que actualice el flujo de datos. Esta acción inicia el proceso de entrenamiento del modelo de aprendizaje automático.

### <a name="ml-model-training"></a>Entrenamiento del modelo de aprendizaje automático

El entrenamiento de modelos de AutoML forma parte de la actualización del flujo de datos. AutoML prepara primero los datos para el entrenamiento.

Luego divide los datos históricos que se proporcionan en conjuntos de datos de entrenamiento y prueba. El conjunto de datos de prueba es un conjunto de datos de exclusión que se usa para validar el rendimiento del modelo después del entrenamiento. Estos conjuntos de datos se consideran entidades de **entrenamiento y prueba** en el flujo de datos. AutoML usa la validación cruzada para la validación del modelo.

A continuación, se analiza cada campo de entrada y se aplica imputación, que reemplaza los valores que faltan por valores sustitutos. AutoML usa un par de estrategias de imputación diferentes. A continuación, se aplica a los datos el muestreo y la normalización necesarios.

AutoML aplica varias transformaciones a cada campo de entrada seleccionado en función de su tipo de datos y sus propiedades estadísticas. Luego, usa estas transformaciones para extraer características que se emplean para entrenar el modelo de aprendizaje automático.

El proceso de entrenamiento de los modelos de AutoML consta de hasta 50 iteraciones con distintos algoritmos de modelado y configuraciones de hiperparámetros hasta encontrar el modelo con el mejor rendimiento. El rendimiento de cada uno de estos modelos se evalúa mediante la validación con el conjunto de datos de prueba de exclusión. Durante este paso del entrenamiento, AutoML crea varias canalizaciones para el entrenamiento y la validación de estas iteraciones. El proceso de evaluación del rendimiento de los modelos puede llevar tiempo, desde varios minutos hasta un par de horas, según el tamaño del conjunto de datos y los recursos de capacidad dedicados disponibles.

En algunos casos, el modelo final generado puede usar el aprendizaje de conjunto, donde se emplean varios modelos para ofrecer un mejor rendimiento predictivo.

### <a name="automl-model-explainability"></a>Explicabilidad del modelo de AutoML

Después de entrenar el modelo, AutoML analiza la relación entre las características de entrada y la salida del modelo. Evalúa la magnitud y la dirección del cambio con la salida del modelo con respecto al conjunto de datos de prueba de exclusión de cada característica de entrada. Esto se conoce como *importancia de característica*.

![Importancia de característica](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>Informe del modelo de AutoML

AutoML genera un informe de Power BI que resume el rendimiento del modelo durante la validación, junto con la importancia de característica global. En él se resumen los resultados de aplicar el modelo de aprendizaje automático a los datos de prueba de exclusión y comparar las predicciones con los valores de resultado conocidos.

Puede revisar el informe del modelo para comprender su rendimiento. También puede validar que los influenciadores clave del modelo se alineen con las conclusiones empresariales sobre los resultados conocidos.

Los gráficos y las medidas que se usan para describir el rendimiento del modelo en el informe dependen del tipo de modelo. Estos gráficos y medidas del rendimiento se describen en las secciones siguientes.

Otras páginas del informe pueden describir medidas estadísticas sobre el modelo desde una perspectiva de la ciencia de datos. Por ejemplo, el informe de **Predicción binaria** incluye un gráfico de ganancia y la curva ROC del modelo.

También incluye una página de **Detalles de aprendizaje** que incluye una descripción de cómo se entrenó el modelo, junto con un gráfico que indica el rendimiento del modelo en cada una de las ejecuciones de iteraciones.

![Detalles del entrenamiento](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Otra sección de esta página describe cómo se usa el método de imputación para rellenar los valores que faltan en los campos de entrada, así como la forma en que se transformó cada campo de entrada para extraer las características usadas en el modelo. También incluye los parámetros que usa el modelo final.

![Más información del modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Si el modelo generado usa aprendizaje de conjunto, la página **Detalles de aprendizaje** también incluye una sección en la que se describe el peso de cada modelo constituyente en el conjunto, así como sus parámetros.

![Peso en el conjunto](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Aplicación del modelo de AutoML

Si está satisfecho con el rendimiento del modelo de aprendizaje automático creado, puede aplicarlo a los datos nuevos o actualizados cuando se actualice el flujo de datos. Para hacerlo desde el informe del modelo, seleccione el botón **Aplicar** en la esquina superior derecha.

Para aplicar el modelo de aprendizaje automático, debe especificar el nombre de la entidad a la que debe aplicarse y un prefijo para las columnas que se agregarán a esta entidad en la salida del modelo. El prefijo predeterminado de los nombres de columna es el nombre del modelo. La función *Aplicar* puede incluir parámetros adicionales específicos del tipo de modelo.

Al aplicar el modelo de aprendizaje automático, se crea una nueva entidad de flujo de datos con el sufijo **<nombre_del_modelo> enriched**. Por ejemplo, si aplica el modelo _PurchaseIntent_ a la entidad _OnlineShoppers_, la salida generará **OnlineShoppers enriched PurchaseIntent**.

Actualmente, la entidad de salida no se puede usar para obtener una vista previa de los resultados del modelo de aprendizaje automático en el Editor de Power Query. Las columnas de salida siempre muestran NULL como resultado. Para ver los resultados, se crea una segunda entidad de salida con el sufijo **enriched <nombre_del_modelo> Preview** cuando se aplica el modelo.

Debe actualizar el flujo de datos para obtener una vista previa de los resultados en el Editor de consultas.

![Editor de consultas](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Al aplicar el modelo, AutoML siempre mantiene las predicciones actualizadas cuando se actualiza el flujo de datos.

AutoML también incluye una explicación individualizada para cada fila que puntúa en la entidad de salida.

Para usar las conclusiones y las predicciones del modelo de aprendizaje automático en un informe de Power BI, puede conectarse a la entidad de salida desde Power BI Desktop mediante el conector de **flujos de datos**.

## <a name="binary-prediction-models"></a>Modelos de predicción binaria

Los modelos de predicción binaria, conocidos más formalmente como **modelos de clasificación binaria**, se usan para clasificar un conjunto de datos en dos grupos. Se emplean para predecir eventos que pueden tener un resultado binario, por ejemplo, si una oportunidad de ventas se convertirá, si una cuenta se va a renovar, si una factura se va a pagar a tiempo, si una transacción es fraudulenta, etc.

Dado que el resultado es binario, Power BI espera que la etiqueta de un modelo de predicción binaria sea un valor booleano, donde los resultados conocidos se etiquetan como **true** o **false**. Por ejemplo, en un modelo de conversión de oportunidades de ventas, las oportunidades de ventas que se han ganado se etiquetan como verdaderas, las que se han perdido como falsas y las que están abiertas como nulas.

La salida de un modelo de predicción binaria es una puntuación de probabilidad, que identifica la probabilidad de que se alcance el resultado correspondiente al valor de la etiqueta que es verdadero.

### <a name="training-a-binary-prediction-model"></a>Entrenamiento de un modelo de predicción binaria

Para crear un modelo de predicción binaria, la entidad de entrada que contiene los datos de entrenamiento debe tener un campo booleano como campo de resultados históricos para identificar los resultados conocidos anteriores.

Requisitos previos:

* Se debe usar un campo booleano como campo de resultados históricos.
* Se requieren 50 filas como mínimo de datos históricos para cada clase de resultados.

En general, si los resultados anteriores se identifican por campos de un tipo de datos diferente, puede agregar una columna calculada para transformarlos en un valor booleano mediante Power Query.

El proceso de creación de un modelo de predicción binaria sigue los mismos pasos que otros modelos de AutoML. Estos pasos se describen en la sección anterior **Configuración de las entradas del modelo de aprendizaje automático**.

### <a name="binary-prediction-model-report"></a>Informe del modelo de predicción binaria

El modelo de predicción binaria genera como salida una probabilidad de que un registro logre el resultado definido por el valor verdadero de la etiqueta booleana. El informe incluye una segmentación de datos para el umbral de probabilidad, que influye en cómo se interpretan las puntuaciones por encima y por debajo del umbral de probabilidad.

El informe describe el rendimiento del modelo en términos de *verdaderos positivos*, *falsos positivos*, *verdaderos negativos* y *falsos negativos*. Los verdaderos positivos y verdaderos negativos son resultados que se predicen correctamente para las dos clases de los datos de resultados. Los falsos positivos son resultados que tenían la etiqueta booleana real de valor falso, pero se predijeron como verdaderos. Por el contrario, los falsos negativos son resultados en los que el valor real de la etiqueta booleana era verdadero, pero se predijeron como falsos.

Las medidas, como la precisión y la recuperación, describen el efecto del umbral de probabilidad en los resultados de predicción. Puede usar la segmentación de datos del umbral de probabilidad para seleccionar un umbral que logre un compromiso equilibrado entre la precisión y la recuperación.

![Vista previa de la precisión](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

La página **Accuracy Report** (Informe de precisión) del informe del modelo incluye el gráfico *Cumulative Gains* (Ganancias acumulativas) y la curva de ROC del modelo. Estas son medidas estadísticas del rendimiento del modelo. Los informes incluyen descripciones de los gráficos que se muestran.

![Pantalla del informe de precisión](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Aplicación de un modelo de predicción binaria

Para aplicar un modelo de predicción binaria, debe especificar la entidad con los datos a los que quiere aplicar las predicciones del modelo de aprendizaje automático. Otros parámetros incluyen el prefijo de nombre de la columna de salida y el umbral de probabilidad para clasificar el resultado de predicción.

![Entradas de predicción](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Cuando se aplica un modelo de predicción binaria, se agregan tres columnas de salida a la entidad de salida enriquecida. Y son **PredictionScore**, **PredictionOutcome** y **PredictionExplanation**. El prefijo se especifica en los nombres de columna de la entidad al aplicar el modelo.

La columna **PredictionOutcome** contiene la etiqueta del resultado de predicción. Los registros con probabilidades que superan el umbral se predicen como probables de lograr el resultado, y los que están por debajo como poco probables de lograrlo.

La columna **PredictionExplanation** contiene una explicación con la influencia específica que tuvieron las características de entrada en **PredictionScore**. Esta es una colección de pesos con formato JSON de las características de entrada de la predicción.

## <a name="classification-models"></a>Modelos de clasificación

Los modelos de clasificación se usan para clasificar un conjunto de datos en varios grupos o clases.  Se emplean para predecir eventos que pueden tener uno de varios resultados posibles, como por ejemplo, si es probable que un cliente tenga un valor de duración muy alto, alto, medio o bajo; si el riesgo de impago es alto, moderado, bajo o muy bajo; etc.

La salida de un modelo de clasificación es una puntuación de probabilidad, que identifica la probabilidad de que un registro alcance los criterios de una clase determinada.

### <a name="training-a-classification-model"></a>Entrenamiento de un modelo de clasificación

La entidad de entrada que contiene los datos de entrenamiento para un modelo de clasificación debe tener un campo numérico o de cadena como campo de resultados históricos para identificar los resultados conocidos anteriores.

Requisitos previos:

* Se requieren 50 filas como mínimo de datos históricos para cada clase de resultados.

El proceso de creación de un modelo de clasificación sigue los mismos pasos que otros modelos de AutoML. Estos pasos se describen en la sección anterior **Configuración de las entradas del modelo de aprendizaje automático**.

### <a name="classification-model-report"></a>Informe del modelo de clasificación

El informe del modelo de clasificación se genera mediante la aplicación del modelo de aprendizaje automático a los datos de prueba de exclusión y la comparación de la clase de predicción de un registro con la clase conocida real.

El informe del modelo incluye un gráfico con el desglose de los registros clasificados correcta e incorrectamente para cada clase conocida.

![Informe del modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Una exploración en profundidad adicional específica de la clase permite analizar cómo se distribuyen las predicciones de una clase conocida. Esto incluye las otras clases en las que es probable que los registros de esa clase conocida estén mal clasificados.

![Informe de análisis](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

La explicación del modelo en el informe también incluye los principales predictores de cada clase.

El informe del modelo de clasificación también incluye una página de detalles de entrenamiento similar a las páginas de otros tipos de modelos, como se describe en la sección **Informe del modelo de AutoML**.

### <a name="applying-a-classification-model"></a>Aplicación de un modelo de clasificación

Para aplicar un modelo de aprendizaje automático de clasificación, debe especificar la entidad con los datos de entrada y el prefijo del nombre de la columna de salida.

Cuando se aplica un modelo de clasificación, se agregan tres columnas de salida a la entidad de salida enriquecida. Estas columnas son **PredictionScore**, **PredictionClass** y **PredictionExplanation**. El prefijo se especifica en los nombres de columna de la entidad al aplicar el modelo.

La columna **PredictionClass** contiene la clase de predicción más probable para el registro. La columna **PredictionScore** contiene la lista de puntuaciones de probabilidad del registro de cada clase posible.

La columna **PredictionExplanation** contiene una explicación con la influencia específica que tuvieron las características de entrada en **PredictionScore**. Esta es una colección de pesos con formato JSON de las características de entrada de la predicción.

## <a name="regression-models"></a>Modelos de regresión

Los modelos de regresión se usan para predecir un valor, como los ingresos que es probable que se obtengan de un contrato de ventas, el valor de duración de una cuenta, el importe de una factura de cobro que es probable que se pague, la fecha en la que se puede pagar una factura, etc.

La salida de un modelo de regresión es el valor de predicción.

### <a name="training-a-regression-model"></a>Entrenamiento de un modelo de regresión

La entidad de entrada que contiene los datos de entrenamiento de un modelo de regresión debe tener un campo numérico como campo de resultados históricos para identificar los resultados conocidos anteriores.

Requisitos previos:

* En un modelo de regresión se requieren 100 filas como mínimo de datos históricos para cada clase de resultados.

El proceso de creación de un modelo de regresión sigue los mismos pasos que otros modelos de AutoML. Estos pasos se describen en la sección anterior **Configuración de las entradas del modelo de aprendizaje automático**.

### <a name="regression-model-report"></a>Informe del modelo de regresión

Al igual que los demás informes del modelo de AutoML, el informe de regresión se basa en los resultados de aplicar el modelo a los datos de prueba de exclusión.

El informe del modelo incluye un gráfico que compara los valores de predicción con el valor real. En este gráfico, la distancia desde la diagonal indica el error en la predicción.

El gráfico de errores residuales muestra la distribución del porcentaje de error medio de los distintos valores del conjunto de datos de prueba de exclusión. El eje horizontal representa la media del valor real del grupo, donde el tamaño de la burbuja muestra la frecuencia o el recuento de valores en ese intervalo. El eje vertical es el error residual medio.

![Gráfico de errores residuales](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

El informe del modelo de regresión también incluye una página de detalles de aprendizaje como los informes de otras tipos de modelos, como se describe en la sección **Informe del modelo de AutoML** anterior.

### <a name="applying-a-regression-model"></a>Aplicación de un modelo de regresión

Para aplicar un modelo de aprendizaje automático de regresión, debe especificar la entidad con los datos de entrada y el prefijo del nombre de la columna de salida.

![Aplicar una regresión](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Cuando se aplica un modelo de regresión, se agregan dos columnas de salida a la entidad de salida enriquecida. Estas columnas son **PredictionValue** y **PredictionExplanation**. El prefijo se especifica en los nombres de columna de la entidad al aplicar el modelo.

La columna **PredictionValue** contiene el valor de predicción del registro en función de los campos de entrada. La columna **PredictionExplanation** contiene una explicación con la influencia específica que tuvieron las características de entrada en **PredictionValue**. Esta es una colección con formato JSON de los pesos de las características de entrada.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporciona información general de Automated Machine Learning para flujos de datos en el servicio Power BI. Los siguientes artículos también pueden resultarle útiles.

* [Tutorial: Creación de un modelo de Machine Learning en Power BI (versión preliminar)](service-tutorial-build-machine-learning-model.md)
* [Tutorial: Uso de Cognitive Services en Power BI](service-tutorial-use-cognitive-services.md)
* [Tutorial: Invocación de un modelo de Machine Learning Studio en Power BI (versión preliminar)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services en Power BI (versión preliminar)](service-cognitive-services.md)
* [Integración de Azure Machine Learning en Power BI (versión preliminar)](service-machine-learning-integration.md)

Para más información sobre los flujos de datos, puede leer estos artículos:
* [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
* [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso de flujos de datos con orígenes de datos locales](service-dataflows-on-premises-gateways.md)
* [Recursos para desarrolladores sobre flujos de datos de Power BI](service-dataflows-developer-resources.md)
* [Integración de flujos de datos y Azure Data Lake (versión preliminar)](service-dataflows-azure-data-lake-integration.md)


