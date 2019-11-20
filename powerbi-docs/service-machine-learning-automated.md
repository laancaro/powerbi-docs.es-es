---
title: Machine Learning automatizado en Power BI
description: Aprenda a usar Automated Machine Learning (AutoML) en Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 49615e1b6c205d9b894df0bcca7ef4979f153ba7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872119"
---
# <a name="automated-machine-learning-in-power-bi"></a>Machine Learning automatizado en Power BI

Automated Machine Learning (AutoML) para flujos de trabajo permite a los analistas de negocios entrenar, validar e invocar modelos de Machine Learning (ML) directamente en Power BI. Incluye una experiencia sencilla para crear un modelo de aprendizaje automático en el que los analistas pueden usar sus flujos de datos para especificar los datos de entrada para entrenar el modelo. El servicio extrae automáticamente las características más apropiadas, selecciona un algoritmo adecuado, y ajusta y valida el modelo de ML. Después de entrenar un modelo, Power BI genera automáticamente un informe de rendimiento que incluye los resultados de la validación. El modelo se puede invocar sobre los datos nuevos o actualizados del flujo de datos.

![Pantalla de Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Automated Machine Learning está disponible únicamente para flujos de datos hospedados en las capacidades Premium y Embedded.

## <a name="working-with-automl"></a>Uso de AutoML

Los [flujos de datos de Power BI](service-dataflows-overview.md) ofrecen autoservicio de preparación de los datos para macrodatos. AutoML está integrado en flujos de datos y le permite aprovechar el trabajo de preparación de los datos para compilar modelos de Machine Learning, directamente en Power BI.

AutoML en Power BI permite a los analistas de datos usar flujos de datos para compilar modelos de aprendizaje automático con una experiencia simplificada, solo con usar los conocimientos de Power BI. Power BI realiza de forma automática la mayor parte de la ciencia de datos que está en la base de la creación de los modelos de ML. Tiene límites de protección para asegurarse de que el modelo generado sea de buena calidad y proporcione una visibilidad sobre el proceso que se usa para crear el modelo de ML.

AutoML admite la creación de modelos de **predicción binaria**, **clasificación** y **regresión** para flujos de datos. Estos son tipos de técnicas de aprendizaje automático supervisados, lo que significa que aprenden de los resultados conocidos de las observaciones anteriores para predecir los resultados de otras observaciones. El conjunto de datos de entrada para entrenar un modelo de AutoML es un conjunto de registros que se **etiquetan** con los resultados conocidos.

AutoML en Power BI integra el [aprendizaje automático automatizado](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) del [servicio Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) para crear los modelos de aprendizaje automático. Sin embargo, no necesita una suscripción a Azure para usar AutoML en Power BI. El proceso de entrenamiento y hospedaje de los modelos de aprendizaje automático se administra por completo en el servicio Power BI.

Después de entrenar un modelo de aprendizaje automático, AutoML genera automáticamente un informe de Power BI que explica el rendimiento probable del modelo. AutoML acentúa la explicabilidad y resalta los influenciadores clave en sus entradas que influyen en las predicciones que devuelve el modelo. El informe también incluye métricas clave para el modelo.

Otras páginas del informe generado muestran el resumen estadístico del modelo y los detalles del entrenamiento. El resumen estadístico es de interés para los usuarios que desean ver las medidas estándar de ciencia de datos del rendimiento del modelo. Los detalles de entrenamiento resumen todas las iteraciones que se ejecutaron para crear el modelo, con los parámetros de modelado asociados. También se describe cómo se usó cada entrada para crear el modelo de aprendizaje automático.

Luego, puede aplicar su modelo de aprendizaje automático a los datos para puntuarlos. Cuando se actualiza el flujo de datos, los datos se actualizan con predicciones del modelo de ML. Power BI también incluye una explicación individualizada de cada predicción específica que genera el modelo de ML.

## <a name="creating-a-machine-learning-model"></a>Creación de un modelo de aprendizaje automático

En esta sección se describe cómo crear un modelo de AutoML.

### <a name="data-prep-for-creating-an-ml-model"></a>Preparación de los datos para crear un modelo de aprendizaje automático

Para crear un modelo de Machine Learning en Power BI, primero debe crear un flujo de datos para los datos que incluya información de los resultados históricos; esta información se usa para entrenar el modelo de ML. También debe agregar columnas calculadas para las métricas empresariales que puedan ser unos fuertes predictores del resultado que intenta predecir. Para más información sobre cómo configurar el flujo de datos, consulte [Autoservicio de preparación de los datos en Power BI](service-dataflows-overview.md).

AutoML presenta unos requisitos de datos específicos para entrenar un modelo de aprendizaje automático. Estos requisitos se describen en las secciones siguientes, en función de los tipos de modelo respectivos.

### <a name="configuring-the-ml-model-inputs"></a>Configuración de las entradas del modelo de aprendizaje automático

Para crear un modelo de AutoML, seleccione el icono de ML en la columna **Acciones** de la entidad de flujo de datos y, luego, **Agregar un modelo de Machine Learning**.

![Adición de un modelo de Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Comienza una experiencia simplificada, que consta de un asistente que le guía por el proceso de creación del modelo de aprendizaje automático. El asistente incluye estos sencillos pasos.

**1. Seleccione la entidad con los datos históricos y el campo de resultados para el que quiere una predicción**

El campo de resultados identifica el atributo de etiqueta para entrenar el modelo de ML, que se muestra en la siguiente imagen.

![Selección de los datos de resultados históricos](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

**2. Elija un tipo de modelo**

Al especificar el campo de resultados, AutoML analiza los datos de etiqueta para recomendar el tipo de modelo de ML más probable que se puede entrenar. Puede elegir un tipo de modelo diferente, como se muestra a continuación, haciendo clic en "Seleccionar otro modelo".

![Selección de un modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

> [!NOTE]
> Puede que algunos tipos de modelos no se admitan con los datos que ha seleccionado y, por lo tanto, estarían deshabilitados. En el ejemplo anterior, la regresión está deshabilitada, ya que hay una columna de texto seleccionada como campo de resultados.

**3. Seleccione las entradas que quiere que use el modelo como señales predictivas**

AutoML analiza una muestra de la entidad seleccionada para sugerir las entradas que se pueden usar para entrenar el modelo de ML. Se proporcionarán explicaciones junto a los campos que no estén seleccionados. Si un campo concreto tiene demasiados valores distintos o solo un valor, o una correlación baja o alta con el campo de salida, no se recomendará su uso.

Las entradas que dependan del campo de resultados (o del campo de etiqueta) no se deben utilizar para entrenar el modelo de ML, dado que afectan al rendimiento. Estos campos se marcarán como si tuvieran una "correlación sospechosamente alta con el campo de salida". Al introducir estos campos en los datos de entrenamiento, se produce una fuga de etiquetas, donde el modelo funciona bien en los datos de prueba o validación, pero no puede alcanzar ese rendimiento cuando se utiliza en producción para la puntuación. La pérdida de etiquetas puede ser un posible problema en los modelos de AutoML, cuando el rendimiento del modelo de entrenamiento sea demasiado bueno para ser verdad.

Esta recomendación de características se basa en una muestra de datos, por lo que debe revisar las entradas utilizadas. Tiene la opción de cambiar las selecciones para que se incluyan solo los campos que desea que estudie el modelo. También puede seleccionar todos los campos, para ello, active la casilla junto al nombre de la entidad.

![Personalizar campos de entrada](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

**4. Asigne un nombre al modelo y guarde la configuración**

En el paso final, puede asignar un nombre al modelo, y seleccionar Guardar y entrenar, lo que comenzará a entrenar el modelo de ML. Puede optar por reducir el tiempo de entrenamiento para ver unos resultados rápidos o aumentar la cantidad de tiempo empleado en el entrenamiento para obtener el mejor modelo.

![Asignación de un nombre al modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

### <a name="ml-model-training"></a>Entrenamiento del modelo de aprendizaje automático

El entrenamiento de modelos de AutoML forma parte de la actualización del flujo de datos. AutoML prepara primero los datos para el entrenamiento.
Luego divide los datos históricos proporcionados en conjuntos de datos de entrenamiento y prueba. El conjunto de datos de prueba es un conjunto de datos de exclusión que se usa para validar el rendimiento del modelo después del entrenamiento. Estos conjuntos de datos se consideran entidades de **entrenamiento y prueba** en el flujo de datos. AutoML usa la validación cruzada para la validación del modelo.

A continuación, se analiza cada campo de entrada y se aplica imputación, que reemplaza los valores que faltan por valores sustitutos. AutoML usa un par de estrategias de imputación diferentes. En el caso de atributos de entrada tratados como características numéricas, la media de los valores de columna se utiliza para imputación. En el caso de atributos de entrada tratados como características de categorías, AutoML utiliza el modo de los valores de columna para imputación. La plataforma AutoML calcula la media y el modo de los valores usados para imputación en el conjunto de datos de entrenamiento de submuestreo.

A continuación, se aplica a los datos el muestreo y la normalización, tal como sea necesario. En el caso de los modelos de clasificación, AutoML ejecuta los datos de entrada mediante el muestreo estratificado y equilibra las clases para asegurarse de que los recuentos de filas son iguales para todos.

AutoML aplica varias transformaciones a cada campo de entrada seleccionado en función de su tipo de datos y sus propiedades estadísticas. Luego, usa estas transformaciones para extraer características que se emplean para entrenar el modelo de aprendizaje automático.

El proceso de entrenamiento de los modelos de AutoML consta de hasta 50 iteraciones con distintos algoritmos de modelado y configuraciones de hiperparámetros hasta encontrar el modelo con el mejor rendimiento. El entrenamiento puede finalizar pronto con iteraciones menores si AutoML ve que no se observa ninguna mejora del rendimiento. El rendimiento de cada uno de estos modelos se evalúa mediante la validación con el conjunto de datos de prueba de exclusión. Durante este paso del entrenamiento, AutoML crea varias canalizaciones para el entrenamiento y la validación de estas iteraciones. El proceso de evaluación del rendimiento de los modelos puede llevar tiempo, entre varios minutos y un par de horas, hasta el tiempo de entrenamiento configurado en el asistente, según el tamaño del conjunto de datos y los recursos de capacidad dedicados disponibles.

En algunos casos, el modelo final generado puede usar el aprendizaje de conjunto, donde se emplean varios modelos para ofrecer un mejor rendimiento predictivo.

### <a name="automl-model-explainability"></a>Explicabilidad del modelo de AutoML

Después de entrenar el modelo, AutoML analiza la relación entre las características de entrada y la salida del modelo. Evalúa la magnitud del cambio con la salida del modelo con respecto al conjunto de datos de prueba de exclusión de cada característica de entrada. Esto se conoce como _importancia de característica_. Esto sucede como parte de la actualización una vez que se haya completado el entrenamiento. Por lo tanto, la actualización puede tardar más que el tiempo de entrenamiento configurado en el asistente.

![Importancia de característica](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

### <a name="automl-model-report"></a>Informe del modelo de AutoML

AutoML genera un informe de Power BI que resume el rendimiento del modelo durante la validación, junto con la importancia de característica global. Se puede tener acceso a este informe en la pestaña Modelo de Machine Learning una vez que la actualización del flujo de datos sea correcta. En él se resumen los resultados de aplicar el modelo de aprendizaje automático a los datos de prueba de exclusión y comparar las predicciones con los valores de resultado conocidos.

Puede revisar el informe del modelo para comprender su rendimiento. También puede validar que los influenciadores clave del modelo se alineen con las conclusiones empresariales sobre los resultados conocidos.

Los gráficos y las medidas que se usan para describir el rendimiento del modelo en el informe dependen del tipo de modelo. Estos gráficos y medidas del rendimiento se describen en las secciones siguientes.

Otras páginas del informe pueden describir medidas estadísticas sobre el modelo desde una perspectiva de la ciencia de datos. Por ejemplo, el informe de **Predicción binaria** incluye un gráfico de ganancia y la curva ROC del modelo.

También incluye una página **Detalles de aprendizaje** con una descripción de cómo se entrenó el modelo y un gráfico que indica el rendimiento del modelo en cada ejecución de iteraciones.

![Detalles del entrenamiento](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

Otra sección de esta página describe el tipo detectado del campo de entrada y el método de imputación que se usa para rellenar los valores que faltan. También incluye los parámetros que usa el modelo final.

![Más información del modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Si el modelo generado usa el aprendizaje de conjunto, la página **Detalles del aprendizaje** también incluye un gráfico en el que se muestra el peso de cada modelo constituyente en el conjunto, así como sus parámetros.

![Peso en el conjunto](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

## <a name="applying-the-automl-model"></a>Aplicación del modelo de AutoML

Si está satisfecho con el rendimiento del modelo de aprendizaje automático creado, puede aplicarlo a los datos nuevos o actualizados cuando se actualice el flujo de datos. Puede hacerlo desde el informe del modelo, seleccionando el botón **Aplicar** en la esquina superior derecha o el botón Aplicar el modelo de ML en Acciones en la pestaña Modelos de Machine Learning.

Para aplicar el modelo de aprendizaje automático, debe especificar el nombre de la entidad a la que debe aplicarse y un prefijo para las columnas que se agregarán a esta entidad en la salida del modelo. El prefijo predeterminado de los nombres de columna es el nombre del modelo. La función _Aplicar_ puede incluir parámetros adicionales específicos del tipo de modelo.

Al aplicar el modelo de ML, se crean dos nuevas entidades de flujo de datos que contienen las predicciones y las explicaciones individualizadas para cada fila que puntúa en la entidad de salida. Por ejemplo, si aplica el modelo _PurchaseIntent_ a la entidad _OnlineShoppers_, la salida generará las entidades **OnlineShoppers enriched PurchaseIntent** y **OnlineShoppers enriched PurchaseIntent explanations**. Para cada fila de la entidad enriquecida, **Explanations** se divide en varias filas de la entidad de explicaciones enriquecidas basada en la característica de entrada. **ExplanationIndex** ayuda a asignar las filas de la entidad de explicaciones enriquecidas a la fila en una entidad enriquecida.

![Editor de consultas](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

Tras aplicar el modelo, AutoML mantiene siempre las predicciones actualizadas cuando se actualiza el flujo de datos.

Para usar las conclusiones y las predicciones del modelo de aprendizaje automático en un informe de Power BI, puede conectarse a la entidad de salida desde Power BI Desktop mediante el conector de **flujos de datos**.

## <a name="binary-prediction-models"></a>Modelos de predicción binaria

Los modelos de predicción binaria, conocidos más formalmente como **modelos de clasificación binaria**, se usan para clasificar un conjunto de datos en dos grupos. Se usan para predecir eventos que puedan tener un resultado binario. Por ejemplo, si una oportunidad de ventas se va a convertir, si una cuenta se va a renovar, si una factura se va a pagar a tiempo, si una transacción es fraudulenta, etc.

La salida de un modelo de predicción binaria es una puntuación de probabilidad, que identifica la probabilidad de que se alcance el resultado objetivo.

### <a name="training-a-binary-prediction-model"></a>Entrenamiento de un modelo de predicción binaria

Requisitos previos:

- Se requieren 20 filas como mínimo de datos históricos para cada clase de resultados.

El proceso de creación de un modelo de predicción binaria sigue los mismos pasos que otros modelos de AutoML. Estos pasos se describen en la sección anterior **Configuración de las entradas del modelo de aprendizaje automático**. La única diferencia se encuentra en el paso "Seleccionar un modelo", donde puede seleccionar el valor del resultado objetivo en el que está más interesado. Puede proporcionar igualmente etiquetas descriptivas para los resultados que se van a usar en el informe generado automáticamente y que resumirá los resultados de la validación del modelo.

![Asistente para predicción binaria](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

### <a name="binary-prediction-model-report"></a>Informe del modelo de predicción binaria

El modelo de predicción binaria genera como salida una probabilidad de que un registro logre el resultado objetivo. El informe incluye una segmentación de datos para el umbral de probabilidad, que influye en cómo se interpretan las puntuaciones por encima y por debajo del umbral de probabilidad.

El informe describe el rendimiento del modelo en términos de _verdaderos positivos, falsos positivos, verdaderos negativos y falsos negativos_. Los verdaderos positivos y verdaderos negativos son resultados que se predicen correctamente para las dos clases de los datos de resultados. Los falsos positivos son registros de los que se predijo que tendrían un resultado objetivo, pero en realidad no lo tuvieron. Por el contrario, los falsos negativos son registros que tuvieron un resultado objetivo, pero de los que se predijo que no lo tendrían.

Las medidas, como la precisión y la recuperación, describen el efecto del umbral de probabilidad en los resultados de predicción. Puede usar la segmentación de datos del umbral de probabilidad para seleccionar un umbral que logre un compromiso equilibrado entre la precisión y la recuperación.

![Vista previa de la precisión](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

El informe también incluye una herramienta de análisis de costos y beneficios que ayuda a identificar el subconjunto de la población al que debe dirigirse para obtener las mayores ganancias. Dado un costo unitario estimado de destino y un beneficio unitario de lograr un resultado objetivo, el análisis de costos y beneficios intenta maximizar las ganancias. Puede usar esta herramienta para elegir el umbral de probabilidad en función del punto máximo del gráfico para maximizar las ganancias. También puede utilizar el gráfico para calcular las ganancias o los costos para el umbral de probabilidad elegido.

![Costos y beneficios](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

La página **Accuracy Report** (Informe de precisión) del informe del modelo incluye el gráfico _Cumulative Gains_ (Ganancias acumulativas) y la curva de ROC del modelo. Estas son medidas estadísticas del rendimiento del modelo. Los informes incluyen descripciones de los gráficos que se muestran.

![Pantalla del informe de precisión](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

### <a name="applying-a-binary-prediction-model"></a>Aplicación de un modelo de predicción binaria

Para aplicar un modelo de predicción binaria, debe especificar la entidad con los datos a los que quiere aplicar las predicciones del modelo de aprendizaje automático. Otros parámetros incluyen el prefijo de nombre de la columna de salida y el umbral de probabilidad para clasificar el resultado de predicción.

![Entradas de predicción](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Cuando se aplica un modelo de predicción binaria, se agregan cuatro columnas de salida a la entidad de salida enriquecida: **Outcome**, **PredictionScore**, **PredictionExplanation** y **ExplanationIndex**. El prefijo se especifica en los nombres de columna de la entidad al aplicar el modelo.

**PredictionScore** es una probabilidad porcentual, que identifica la probabilidad de que se alcance el resultado objetivo.

La columna **Outcome** contiene la etiqueta del resultado de predicción. Los registros con probabilidades que superan el umbral se predicen como probables para lograr el resultado objetivo y se etiquetan como verdaderos. Los registros que se encuentran por debajo del umbral se predicen como improbables para lograr el resultado y se etiquetan como falsos.

La columna **PredictionExplanation** contiene una explicación con la influencia específica que tuvieron las características de entrada en **PredictionScore**.

## <a name="classification-models"></a>Modelos de clasificación

Los modelos de clasificación se usan para clasificar un conjunto de datos en varios grupos o clases. Se utilizan para predecir eventos que pueden tener uno de los diversos resultados posibles. Por ejemplo, si es probable que un cliente tenga un valor de duración muy alto, alto, medio o bajo; si el riesgo de impago es alto, moderado, bajo o muy bajo; etc.

La salida de un modelo de clasificación es una puntuación de probabilidad, que identifica la probabilidad de que un registro alcance los criterios de una clase determinada.

### <a name="training-a-classification-model"></a>Entrenamiento de un modelo de clasificación

La entidad de entrada que contiene los datos de entrenamiento para un modelo de clasificación debe tener un campo de número entero o de cadena como campo de resultados para identificar los resultados conocidos anteriores.

Requisitos previos:

- Se requieren 20 filas como mínimo de datos históricos para cada clase de resultados.

El proceso de creación de un modelo de clasificación sigue los mismos pasos que otros modelos de AutoML. Estos pasos se describen en la sección anterior **Configuración de las entradas del modelo de aprendizaje automático**.

### <a name="classification-model-report"></a>Informe del modelo de clasificación

El informe del modelo de clasificación se genera mediante la aplicación del modelo de aprendizaje automático a los datos de prueba de exclusión y la comparación de la clase de predicción de un registro con la clase conocida real.

El informe del modelo incluye un gráfico con el desglose de los registros clasificados correcta e incorrectamente para cada clase conocida.

![Informe del modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-17.png)

Una exploración en profundidad adicional específica de la clase permite analizar cómo se distribuyen las predicciones de una clase conocida. Esto muestra las otras clases en las que es probable que los registros de esa clase conocida estén mal clasificados.

La explicación del modelo en el informe también incluye los principales predictores de cada clase.

El informe del modelo de clasificación también incluye una página de detalles de entrenamiento similar a las páginas de otros tipos de modelos, como se describe en la sección **Informe del modelo de AutoML**.

### <a name="applying-a-classification-model"></a>Aplicación de un modelo de clasificación

Para aplicar un modelo de aprendizaje automático de clasificación, debe especificar la entidad con los datos de entrada y el prefijo del nombre de la columna de salida.

Cuando se aplica un modelo de clasificación, se agregan cinco columnas de salida a la entidad de salida enriquecida: **ClassificationScore**, **ClassificationResult**, **ClassificationExplanation**, **ClassProbabilities** y **ExplanationIndex**. El prefijo se especifica en los nombres de columna de la entidad al aplicar el modelo.

La columna **ClassProbabilities** contiene la lista de puntuaciones de probabilidad del registro de cada clase posible.

**ClassificationScore** es el porcentaje de probabilidad, que identifica la probabilidad de que un registro alcance los criterios de una clase determinada.

La columna **ClassificationResult** contiene la clase de predicción más probable para el registro.

La columna **ClassificationExplanation** contiene una explicación con la influencia específica que tuvieron las características de entrada en **ClassificationScore**.

## <a name="regression-models"></a>Modelos de regresión

Los modelos de regresión se usan para predecir un valor numérico. Por ejemplo, los ingresos que es probable que se obtengan de un contrato de ventas, el valor de duración de una cuenta, el importe de una factura de cobro que es probable que se pague, la fecha en la que se puede pagar una factura, etc.

La salida de un modelo de regresión es el valor de predicción.

### <a name="training-a-regression-model"></a>Entrenamiento de un modelo de regresión

La entidad de entrada que contiene los datos de entrenamiento de un modelo de regresión debe tener un campo numérico como campo de resultados para identificar los valores de resultados conocidos.

Requisitos previos:

- En un modelo de regresión se requieren 100 filas como mínimo de datos históricos para cada clase de resultados.

El proceso de creación de un modelo de regresión sigue los mismos pasos que otros modelos de AutoML. Estos pasos se describen en la sección anterior **Configuración de las entradas del modelo de aprendizaje automático**.

### <a name="regression-model-report"></a>Informe del modelo de regresión

Al igual que los demás informes del modelo de AutoML, el informe de regresión se basa en los resultados de aplicar el modelo a los datos de prueba de exclusión.

El informe del modelo incluye un gráfico que compara los valores de predicción con los valores reales. En este gráfico, la distancia desde la diagonal indica el error en la predicción.

El gráfico de errores residuales muestra la distribución del porcentaje de error medio de los distintos valores del conjunto de datos de prueba de exclusión. El eje horizontal representa la media del valor real del grupo, donde el tamaño de la burbuja muestra la frecuencia o el recuento de valores en ese intervalo. El eje vertical es el error residual medio.

![Gráfico de errores residuales](media/service-machine-learning-automated/automated-machine-learning-power-bi-18.png)

El informe del modelo de regresión también incluye una página de detalles de aprendizaje como los informes de otras tipos de modelos, como se describe en la sección **Informe del modelo de AutoML** anterior.

### <a name="applying-a-regression-model"></a>Aplicación de un modelo de regresión

Para aplicar un modelo de aprendizaje automático de regresión, debe especificar la entidad con los datos de entrada y el prefijo del nombre de la columna de salida.

![Aplicar una regresión](media/service-machine-learning-automated/automated-machine-learning-power-bi-19.png)

Cuando se aplica un modelo de regresión, se agregan tres columnas de salida a la entidad de salida enriquecida: **RegressionResult**, **RegressionExplanation** y **ExplanationIndex**. El prefijo se especifica en los nombres de columna de la entidad al aplicar el modelo.

La columna **RegressionResult** contiene el valor de predicción del registro en función de los campos de entrada. La columna **RegressionExplanation** contiene una explicación con la influencia específica que tuvieron las características de entrada en **RegressionResult**.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporciona información general de Automated Machine Learning para flujos de datos en el servicio Power BI. Los siguientes artículos también pueden resultarle útiles.

- [Tutorial: Creación de un modelo de Machine Learning en Power BI (versión preliminar) ](service-tutorial-build-machine-learning-model.md)
- [Tutorial: Uso de Cognitive Services en Power BI](service-tutorial-use-cognitive-services.md)
- [Tutorial: Invocación de un modelo de Machine Learning Studio en Power BI (versión preliminar)](service-tutorial-invoke-machine-learning-model.md)
- [Cognitive Services en Power BI](service-cognitive-services.md)
- [Integración de Azure Machine Learning en Power BI](service-machine-learning-integration.md)

Para más información sobre los flujos de datos, puede leer estos artículos:

- [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
- [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
- [Uso de flujos de datos con orígenes de datos locales](service-dataflows-on-premises-gateways.md)
- [Recursos para desarrolladores sobre flujos de datos de Power BI](service-dataflows-developer-resources.md)
- [Integración de flujos de datos y Azure Data Lake (versión preliminar)](service-dataflows-azure-data-lake-integration.md)
