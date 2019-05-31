---
title: 'Tutorial: Crear un modelo de Machine Learning en Power BI (versión preliminar)'
description: En este tutorial compilará un modelo de aprendizaje automático en Power BI.
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61407195"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutorial: Crear un modelo de Machine Learning en Power BI (versión preliminar)

En este artículo tutorial, usará **automatizada de Machine Learning** para crear y aplicar un modelo de predicción binario en Power BI. El tutorial incluye instrucciones para crear un flujo de datos de Power BI y uso de las entidades definidas en el flujo de datos para entrenar y validar un modelo de machine learning directamente en Power BI. A continuación, usamos ese modelo para puntuar para generar predicciones.

En primer lugar, creará una predicción binaria modelo de machine learning, para predecir la intención de compra de los compradores en línea según un conjunto de sus atributos de la sesión en línea. Para este ejercicio, se usa un conjunto de datos de aprendizaje de máquina de pruebas comparativas. Una vez que se entrena un modelo, Power BI generará automáticamente un informe de validación que explica los resultados del modelo. A continuación, puede revisar el informe de validación y aplicar el modelo a los datos para la puntuación.

Este tutorial consta de los pasos siguientes:

> [!div class="checklist"]
> * Crear un flujo de datos con los datos de entrada
> * Crear y entrenar un modelo de aprendizaje automático
> * Revisar el informe de validación de modelo
> * Aplicar el modelo a una entidad de flujo de datos
> * Con la salida con puntuación del modelo en un informe de Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Crear un flujo de datos con los datos de entrada

La primera parte de este tutorial es crear un flujo de datos con datos de entrada. Este proceso tarda unos pocos pasos, tal como se muestra en las secciones siguientes, comenzando con la obtención de datos.

### <a name="get-data"></a>Obtener datos

El primer paso para crear un flujo de datos es la lista de orígenes de datos. En nuestro caso, usamos un conjunto de datos de aprendizaje automático de un conjunto de las sesiones en línea, algunos de los cuales culminan en una compra. El conjunto de datos contiene un conjunto de atributos acerca de estas sesiones, que se usará para el entrenamiento de nuestro modelo.

Puede descargar el conjunto de datos desde el sitio Web de UC Irvine.  También tenemos disponible, para este tutorial, en el siguiente vínculo: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Crear las entidades

Para crear las entidades en su flujo de datos, inicie sesión en el servicio Power BI y vaya a un área de trabajo de su capacidad dedicada que tenga habilitada la versión preliminar de AI.

Si aún no tiene un área de trabajo, puede crear uno mediante la selección **las áreas de trabajo** en el menú de navegación izquierdo, en el servicio Power BI y seleccione **Crear área de trabajo de aplicación** en la parte inferior del panel que aparece. Se abrirá un panel de la derecha para especificar los detalles de área de trabajo. Escriba un nombre de área de trabajo y seleccione **avanzadas**. Confirme que el área de trabajo utiliza la capacidad dedicada con el botón de radio y que se asigna a una instancia de capacidad dedicada que tenga la versión preliminar de inteligencia artificial activada. Luego seleccione **Guardar**.

![Creación de un área de trabajo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Una vez creado el área de trabajo, puede seleccionar **Skip** en la esquina inferior derecha de la pantalla de bienvenida, tal como se muestra en la siguiente imagen.

![Omita si tiene un área de trabajo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Seleccione el **flujos de datos (versión preliminar)** ficha. Seleccione el **crear** situado en la parte superior derecha del área de trabajo y, a continuación, seleccione **Dataflow**.

![Crear flujo de datos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Seleccione **Agregar entidades nuevas**. Esto inicia un **Power Query** editor en el explorador.

![Agregar entidad nueva](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Seleccione **archivo de texto o CSV** como origen de datos, se muestra en la siguiente imagen.

![Archivo de texto/CSF seleccionado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

En el **conectarse a un origen de datos** que aparece a continuación, pegue el vínculo siguiente para el *online_shoppers_intention.csv* en el **ruta de acceso o dirección URL** cuadro y, a continuación, seleccione  **Siguiente**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Ruta de acceso de archivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

El Editor de Power Query se muestra una vista previa de los datos del archivo CSV. Seleccione **transformar tabla** en la cinta de opciones de comando y, a continuación, seleccione **usar primera fila como encabezados** en el menú que aparece. Esto agrega el _promover encabezados_ paso de consulta en el **los pasos aplicados** sección a la derecha de la pantalla. Puede cambiar el nombre la consulta a un nombre más descriptivo, cambie el valor en el **nombre** cuadro se encuentra en el panel derecho. Por ejemplo, puede cambiar el nombre de la consulta a _visitante en línea_.

![Cambiar a un nombre descriptivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Algunos de los tipos de datos de atributo en este conjunto de datos son _numérico_ o _booleano_, aunque estos se pueden interpretar como cadenas por **Power Query**. Seleccione el icono de tipo de atributo en la parte superior de cada encabezado de columna para cambiar las columnas siguientes a los siguientes tipos:

* **Número decimal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **True/False:** Fin de semana; Ingresos

![Cambio del tipo de datos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

El **predicción binaria** vamos a entrenar el modelo requiere un campo booleano como una etiqueta de identificación de los resultados de las observaciones anteriores. En este conjunto de datos, el _ingresos_ atributo indica la compra, y este atributo ya está disponible como un valor booleano. Por lo tanto, no es necesario agregar una columna calculada para la etiqueta. En otros conjuntos de datos, es posible que deba Transformar atributos de etiqueta existente en una columna booleana.

Seleccione el **realiza** botón para cerrar el Editor de Power Query. Esto muestra la lista de entidades con el _visitantes en línea_ datos que se ha agregado. Seleccione **guardar** en la esquina superior derecha, proporcione un nombre para el flujo de datos y, a continuación, seleccione **guardar** en el cuadro de diálogo, como se muestra en la siguiente imagen.

![Guardar el flujo de datos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Actualizar el flujo de datos

Guardar los resultados del flujo de datos en que se muestra una notificación, que indica que se ha guardado el flujo de datos. Seleccione **actualizar ahora** para introducir los datos desde el origen en el flujo de datos.

![Actualizar ahora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Seleccione **Cerrar** en la esquina superior derecha y espere a que se complete la actualización del flujo de datos.

También puede actualizar el flujo de datos mediante el **acciones** comandos. El flujo de datos muestra la marca de tiempo cuando se haya completado la actualización.

![Marca de tiempo de actualización](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Crear y entrenar un modelo de aprendizaje automático

Seleccione el flujo de datos una vez completada la actualización. Para agregar un modelo de aprendizaje automático, seleccione el **modelo de aprendizaje automático se aplican** situado en la **acciones** lista para la entidad base que contiene la información de etiqueta y de datos de entrenamiento y, a continuación, seleccione **agregar un modelo de aprendizaje automático**.

![Agregar un modelo de Machine Learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

Es el primer paso para crear nuestro modelo de aprendizaje automático identificar los datos históricos, incluido el campo de etiqueta que desea predecir. Creará el modelo de aprendizaje a partir de estos datos.

En el caso estamos usando el conjunto de datos, se trata la **ingresos** campo. Seleccione **ingresos** como el valor de 'campo resultado históricos' y seleccione **siguiente**.

![Seleccione los datos históricos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

A continuación, debemos seleccionamos el tipo de modelo para crear de aprendizaje automático. Power BI analiza los valores en el campo de resultado históricos que ha identificado y sugiere los tipos de modelos de aprendizaje automático que se pueden crear para predecir ese campo.

En este caso, puesto que estamos predecir resultados binarios de si un usuario realizar una compra o no, seleccione **predicción binaria** para el tipo de modelo y, a continuación, seleccione siguiente.

![Predicción binaria seleccionado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

A continuación, Power BI realiza un análisis preliminar de los datos y sugiere las entradas que podría usar el modelo. Tiene la opción de personalizar los campos de entrada utilizados para el modelo. En nuestro vasto conjunto de datos, para seleccionar todos los campos, seleccione la casilla de verificación situada junto al nombre de entidad. Seleccione **siguiente** para aceptar las entradas.

![Seleccione la casilla de verificación siguiente](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

En el paso final, nos debemos proporcionar un nombre para nuestro modelo, así como las etiquetas descriptivas para los resultados que se usará en el informe generado automáticamente que resumirá los resultados de la validación del modelo. Luego, tenemos que asignar nombre al modelo _compra intención predicción_y las etiquetas true y false como _compra_ y _No compra_. Luego seleccione **Guardar**.

![Guardar el modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Nuestro modelo de aprendizaje automático ahora está listo para el entrenamiento. Seleccione **actualizar ahora** para iniciar el entrenamiento del modelo.

![Actualizar ahora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Se iniciará el proceso de entrenamiento de muestreo y la normalización de los datos históricos y dividir el conjunto de datos en dos nuevas entidades *datos de entrenamiento de predicción de intención de compra* y *pruebas de predicción de intención de compra Datos*.

Según el tamaño del conjunto de datos, el proceso de entrenamiento puede tardar desde unos minutos a un par de horas. En este momento, puede ver el modelo en el **modelos de aprendizaje automático** ficha del flujo de datos. El _listo_ estado indica que el modelo se ha puesto en cola para el entrenamiento o está por debajo del entrenamiento.

![Listo para el entrenamiento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Aunque el modelo es aprendizaje, no podrá ver o editar el flujo de datos. Puede confirmar que el modelo se está entrenado y valida el estado del flujo de datos. Esto aparece como una actualización de datos en curso en el **Dataflows** ficha del área de trabajo.

![En proceso](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Una vez completado el entrenamiento del modelo, el flujo de datos muestra una hora de actualización actualizado. Puede confirmar que el modelo está entrenado, yendo a la **modelos de aprendizaje automático** ficha en el flujo de datos. El modelo creado debe mostrar el estado como **calificado** y **última entrenado** tiempo ahora debe actualizarse.

![Formado por última vez en](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Revisar el informe de validación de modelo

Para revisar el informe de validación del modelo, en el **modelos de aprendizaje automático, s** optar por la **Ver informe de rendimiento y aplicar el modelo** situado en la **acciones** columna del modelo . Este informe describe cómo el modelo de aprendizaje automático es probable que realice.

En el **rendimiento del modelo** página del informe, seleccione **Influenciadores clave** para ver los indicadores principales para el modelo. Puede seleccionar uno de los indicadores para ver cómo la distribución de resultado asociado con ese elemento de predicción.

![Rendimiento del modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Puede usar el **umbral de probabilidad** segmentación en la página de rendimiento del modelo para examinar su influencia en la precisión y la recuperación para el modelo.

![Umbral de probabilidad](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Las otras páginas del informe describen las métricas de rendimiento estadísticas para el modelo.

El informe también incluye una página de detalles de entrenamiento que se describe las diferentes iteraciones que se ejecutaron, cómo las características se han extraído de las entradas y los hiperparámetros para el modelo final se usa.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Aplicar el modelo a una entidad de flujo de datos

Seleccione el **aplicar modelo** situado en la parte superior del informe que se invoca este modelo cuando se actualiza el flujo de datos. En el **aplicar** cuadro de diálogo, puede especificar la entidad de destino que contenga los datos de origen a la que se debe aplicar el modelo.

![Aplicar el modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Cuando se le pida, debe **actualizar** el flujo de datos para obtener una vista previa de los resultados del modelo.

Aplicar el modelo creará una nueva entidad, con el sufijo **enriquecido < model_name >** anexado a la entidad a la que se aplica el modelo. En nuestro caso, al aplicar el modelo a la **OnlineShoppers** creará la entidad **OnlineShoppers enriquecido compra intención predicción**, que incluye los resultados de predicción del modelo.

Al aplicar un modelo de predicción binario agrega tres columnas con el resultado de predicción, puntuación de probabilidad y los principales influenciadores específico del registro para la predicción, cada uno prefijado con el nombre de columna especificado.

![Tres columnas de resultado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Debido a un problema conocido, las columnas de salida con puntuación de la entidad enriquecida solo son accesibles desde Power BI Desktop. Para obtener una vista previa en el servicio, debe usar una entidad de la versión preliminar especial.

Una vez completada la actualización de flujo de datos, puede seleccionar la **OnlineShoppers enriquecido de vista previa de predicción de intención de compra** entidad para ver los resultados.

![Ver los resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Con la salida con puntuación del modelo en un informe de Power BI

Para usar la salida con puntuación de su modelo de aprendizaje automático, puede conectarse a su flujo de datos desde Power BI desktop, mediante el conector de flujos de datos. El **OnlineShoppers enriquecido compra intención predicción** entidad ahora se puede usar para incorporar las predicciones del modelo en los informes de Power BI.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, crea y aplica un modelo de predicción binario en Power BI que siguiendo estos pasos:

* Crear un flujo de datos con los datos de entrada
* Crear y entrenar un modelo de aprendizaje automático
* Revisar el informe de validación de modelo
* Aplicar el modelo a una entidad de flujo de datos
* Con la salida con puntuación del modelo en un informe de Power BI

Para obtener más información acerca de la automatización de Machine Learning en Power BI, consulte [automatizada de Machine Learning en Power BI (versión preliminar)](service-machine-learning-automated.md).
