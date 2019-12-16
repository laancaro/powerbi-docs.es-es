---
title: Optimización de las capacidades de Microsoft Power BI Premium
description: Se describen estrategias de optimización para las capacidades de Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 4d03419105244b7fddafea3b26b69e4f4f5f874c
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958549"
---
# <a name="optimizing-premium-capacities"></a>Optimización de las capacidades Premium

Cuando surgen problemas de rendimiento de la capacidad Premium, un primer enfoque común consiste en optimizar o ajustar las soluciones para restaurar tiempos de respuesta aceptables. La lógica es poder evitar la compra de más capacidad Premium, a menos que esté justificada.

Cuando se necesita más capacidad Premium, hay dos opciones que se describen en este artículo:

- Escalado vertical de una capacidad Premium existente
- Adición de una capacidad Premium nueva

Por último, el artículo concluye con los enfoques de prueba y ajuste del tamaño de la capacidad Premium.

## <a name="best-practices"></a>Procedimientos recomendados

Al intentar obtener el uso y rendimiento óptimos, existen algunos procedimientos recomendados, entre los que se incluyen los siguientes:

- Uso de las nuevas áreas de trabajo en lugar de las personales.
- Separación de inteligencia empresarial de autoservicio (SSBI) y crítica para la empresa en diferentes capacidades.

  ![Separación de inteligencia empresarial de autoservicio y crítica para la empresa en diferentes capacidades](media/service-premium-capacity-optimize/separate-capacities.png)

- Si el contenido solo se comparte con usuarios de Power BI Pro, es posible que no sea necesario almacenarlo en una capacidad dedicada.
- Use capacidades dedicadas cuando quiera lograr una hora de actualización específica, o bien cuando se requieran determinadas características. Por ejemplo, con conjuntos de datos grandes o informes paginados.

### <a name="addressing-common-questions"></a>Solución de preguntas habituales

La optimización de las implementaciones de Power BI Premium es un tema complejo que implica una comprensión de los requisitos de carga de trabajo, los recursos disponibles y su uso eficaz.

En este artículo se abordan siete preguntas de soporte técnico comunes, en las que se describen posibles problemas y explicaciones, así como información sobre cómo identificarlos y resolverlos.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>¿Por qué la capacidad es lenta y qué puedo hacer?

Hay muchas razones que pueden contribuir a la lentitud de una capacidad Premium. Esta pregunta requiere más información para comprender lo que se entiende por lentitud. ¿Los informes tardan en cargarse? ¿O bien no se pueden cargar? ¿Los objetos visuales de informes tardan en cargarse o actualizarse cuando los usuarios interactúan con el informe? ¿La actualización tarda en completarse más de lo esperado o de lo que se ha experimentado antes?

Una vez que se entiende el motivo, puede empezar a investigar. Las respuestas a las seis preguntas siguientes le ayudarán a abordar problemas más específicos.

### <a name="what-content-is-using-up-my-capacity"></a>¿Qué contenido está usando mi capacidad?

Puede usar la aplicación **Métricas de capacidad de Power BI Premium** para filtrar por capacidad y revisar las métricas de rendimiento del contenido del área de trabajo. Se pueden revisar las métricas de rendimiento y el uso de los recursos por hora durante los últimos siete días para todo el contenido almacenado dentro de una capacidad Premium. La supervisión suele ser el primer paso a la hora de solucionar un problema general relacionado con el rendimiento de la capacidad Premium.

Entre las métricas clave que se deben supervisar se incluyen las siguientes:

- Uso medio de CPU y recuento de uso alto.
- Promedio de memoria y recuento de uso alto, y uso de memoria para conjuntos de datos, flujos de datos e informes paginados específicos.
- Conjuntos de datos activos cargados en memoria.
- Duración media y máxima de las consultas.
- Promedios de tiempos de espera de consulta.
- Tiempo medio de actualización de conjuntos de datos y flujos de datos.

En la aplicación Métricas de capacidad de Power BI Premium, la memoria activa muestra la cantidad total de memoria asignada a un informe que no se puede expulsar porque se ha usado en los últimos tres minutos. Un pico elevado en el tiempo de espera de actualización podría estar relacionado con un conjunto de datos grande o activo.

En el gráfico **Top 5 by Average Duration** (Cinco principales por duración promedio) se resaltan los cinco principales conjuntos de datos, informes paginados y flujos de dados que consumen recursos de capacidad. El contenido de las listas de 5 principales es candidato para la investigación y posible optimización.

### <a name="why-are-reports-slow"></a>¿Por qué son lentos los informes?

En las tablas siguientes se muestran los posibles problemas y maneras de identificarlos y administrarlos.

#### <a name="insufficient-capacity-resources"></a>Recursos de capacidad insuficientes

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Memoria activa total elevada (el modelo no se puede expulsar porque está en uso en los últimos tres minutos).<br><br> Varios picos elevados en los tiempos de espera de consulta.<br><br> Varios picos elevados en los tiempos de espera de actualización. | Supervise las métricas de memoria \[[1](#endnote-1)\] y los recuentos de expulsión \[[2](#endnote-2)\]. | Reduzca el tamaño del modelo o conviértalo al modo DirectQuery. Vea la sección [Optimización de modelos](#optimizing-models) de este artículo.<br><br> Escale verticalmente la capacidad.<br><br> Asigne el contenido a otra capacidad. |

#### <a name="inefficient-report-designs"></a>Diseños de informe ineficaces

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Las páginas del informe contienen demasiados objetos visuales (el filtrado interactivo puede desencadenar al menos una consulta por objeto visual).<br><br> Los objetos visuales recuperan más datos de los necesarios. | Revise los diseños de informes.<br><br> Entreviste a los usuarios de los informes para entender cómo interactúan con ellos.<br><br> Supervise las métricas de consulta de conjunto de datos \[[3](#endnote-3)\]. | Vuelva a diseñar los informes con menos objetos visuales por página. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>El conjunto de datos es lento, especialmente cuando antes los informes se han ejecutado de forma correcta

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Grandes volúmenes de datos de importación cada vez mayores.<br><br> Lógica de cálculo compleja o ineficaz, incluidos los roles de RLS.<br><br> El modelo no está totalmente optimizado.<br><br> Latencia de puerta de enlace (DQ/LC).<br><br> Tiempos de respuesta de consulta lentos de origen de DirectQuery. | Revise los diseños del modelo.<br><br> Supervise los contadores de rendimiento de puerta de enlace. | Vea la sección [Optimización de modelos](#optimizing-models) de este artículo. |

#### <a name="high-concurrent-report-usage"></a>Uso elevado de informes simultáneos

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Tiempos de espera de consulta elevados.<br><br> Saturación de la CPU.<br><br> Se han superado los límites de conexión de DQ/LC. | Supervise las métricas de Utilización de CPU \[[4](#endnote-4)\], tiempos de espera de consulta y uso de DQ/LC \[[5](#endnote-5)\], y las duraciones de las consultas. Si hay fluctuaciones, pueden indicar problemas de simultaneidad. | Escale verticalmente la capacidad o asigne el contenido a otra capacidad.<br><br> Vuelva a diseñar los informes con menos objetos visuales por página. |

**Notas:**    
<a name="endnote-1"></a>\[1\] Promedio de uso de la memoria (GB) y Consumo de memoria máximo (GB).   
<a name="endnote-2"></a>\[2\] Expulsiones de conjuntos de datos.   
<a name="endnote-3"></a>\[3\] Consultas de conjunto de datos, Duración media de consulta del conjunto de datos (ms), Recuento de espera de conjunto de datos y Tiempo promedio de espera de conjunto de datos (ms).   
<a name="endnote-4"></a>\[4\] Recuento de uso alto de CPU y Hora de uso más alto de la CPU (últimos siete días).   
<a name="endnote-5"></a>\[5\] Recuento de uso alto de DQ/LC y Hora de uso más alto de DQ/LC (últimos siete días).   

### <a name="why-are-reports-not-loading"></a>¿Por qué no se cargan los informes?

Cuando los informes no se cargan, es una señal evidente de que la capacidad no tiene memoria suficiente y está sobrecalentada. Esto puede ocurrir cuando todos los modelos cargados se consultan de forma activa, por lo que no se pueden expulsar, y las operaciones de actualización se han pausado o retrasado. El servicio Power BI intentará cargar el conjunto de datos durante 30 segundos y el error se notificará al usuario de forma correcta con una sugerencia para que lo intente de nuevo en breve.

En la actualidad no existe ninguna métrica para supervisar los errores de carga de informes. Puede identificar la posibilidad de este problema si supervisa la memoria del sistema, en concreto el uso más alto y la hora de uso más alto. Los valores elevados de expulsiones de conjunto de datos y tiempo de espera promedio de actualización del conjunto de datos podrían sugerir que se está produciendo este problema.

Si esto solo sucede de forma ocasional, es posible que no se considere un problema prioritario. Se informa a los usuarios del informe de que el servicio está ocupado y que deben volver a intentarlo después de un breve período de tiempo. Si esto ocurre con demasiada frecuencia, el problema se puede resolver mediante el escalado vertical de la capacidad Premium o la asignación del contenido a otra capacidad.

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica **Errores de consulta** para determinar cuándo sucede esto. También pueden reiniciar la capacidad, y restablecer todas las operaciones en caso de sobrecarga del sistema.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>¿Por qué no se inician las actualizaciones según la programación?

Las horas de inicio de la actualización programada no están garantizadas. Recuerde que el servicio Power BI siempre dará prioridad a las operaciones interactivas sobre las operaciones en segundo plano. La actualización es una operación en segundo plano que se puede producir cuando se cumplen dos condiciones:

- Hay memoria suficiente
- No se supera el número de actualizaciones simultáneas admitidas para la capacidad Premium

Cuando no se cumplen las condiciones, la actualización se pone en cola hasta que las condiciones sean favorables.

Para una actualización completa, recuerde que al menos se requiere el doble del tamaño de la memoria del conjunto de datos actual. Si no hay suficiente memoria disponible, la actualización no se puede iniciar hasta que la expulsión del modelo libere memoria, lo que supone retrasos hasta que uno o varios conjuntos de datos queden inactivos y se puedan expulsar.

Recuerde que el número de actualizaciones simultáneas máximas que se admite se establece en 1,5 veces los núcleos virtuales de back-end, redondeado hacia arriba.

Se producirá un error en una actualización programada cuando no se pueda iniciar antes de que se inicie la siguiente actualización programada. Una actualización a petición desencadenada de forma manual desde la interfaz de usuario intentará ejecutarse hasta tres veces antes de que se produzca un error.

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica de **tiempo de espera promedio de actualización (minutos)** para determinar el retraso medio entre la hora programada y el inicio de la operación.

Aunque no suele ser una prioridad administrativa, para influir en las actualizaciones de datos puntuales, asegúrese de que haya suficiente memoria disponible. Esto puede implicar el aislamiento de los conjuntos de datos en capacidades con recursos suficientes conocidos. También es posible que los administradores se coordinen con los propietarios del conjunto de datos para ayudar a escalonar o reducir los tiempos de actualización de datos programados con el fin de minimizar las colisiones. Tenga en cuenta que no es posible que un administrador vea la cola de actualización ni que recupere las programaciones del conjunto de datos.

### <a name="why-are-refreshes-slow"></a>¿Por qué son lentas las actualizaciones?

Las actualizaciones pueden ser lentas o percibirse como tales (como se aborda en la pregunta común anterior).

Cuando la actualización es realmente lenta, puede deberse a varios motivos:

- CPU insuficiente (la actualización puede consumir mucha CPU).
- Memoria insuficiente, lo que produce una pausa de la actualización (que requiere que se inicie de nuevo cuando las condiciones sean favorables para reiniciarse).
- Razones no relacionadas con la capacidad, incluida la latencia de red, permisos no válidos, el rendimiento de la puerta de enlace o la capacidad de respuesta del sistema del origen de datos.
- Volumen de datos: una buena razón para configurar la actualización incremental, como se describe a continuación.

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica **Duración promedio de la actualización (minutos)** para determinar un banco de pruebas para la comparación en el tiempo, y la métrica **Tiempo de espera promedio de actualización (minutos)** para determinar el retraso medio entre la hora programada y el inicio de la operación.

La actualización incremental puede reducir significativamente la duración de la actualización de datos, especialmente en el caso de tablas de modelos grandes. Hay cuatro ventajas asociadas con la actualización incremental:

- **Las actualizaciones son más rápidas**: solo es necesario cargar un subconjunto de una tabla, lo que reduce el uso de la CPU y la memoria, y el paralelismo puede ser mayor al actualizar varias particiones.
- **Las actualizaciones solo se producen cuando son necesarias**: se pueden configurar directivas de actualización incremental para que solo se carguen cuando los datos han cambiado.
- **Las actualizaciones son más confiables**: las conexiones de ejecución más corta a sistemas de origen de datos volátiles son menos susceptibles a la desconexión.
- **Los modelos permanecen recortados**: se pueden configurar directivas de actualización incremental para quitar automáticamente el historial más allá de una ventana deslizante de tiempo.

Para más información, vea [Actualizaciones incrementales en Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>¿Por qué no se completan las actualizaciones de datos?

Cuando la actualización de datos comienza pero no se completa, puede deberse a varios motivos:

- Memoria insuficiente, incluso si solo hay un modelo en la capacidad Premium, es decir, el tamaño del modelo es muy grande.
- Razones no relacionadas con la capacidad, incluida la desconexión del sistema de origen de datos, permisos no válidos o un error de la puerta de enlace.

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica **Refresh Failures due to out of Memory** (Errores de consulta debido a memoria insuficiente).

## <a name="optimizing-models"></a>Optimización de modelos

El diseño de modelos óptimos es fundamental para ofrecer una solución eficaz y escalable. Pero proporcionar una explicación completa queda fuera del ámbito de este artículo. En su lugar, en esta sección se proporcionarán las áreas clave que se deben tener en cuenta al optimizar los modelos.

### <a name="optimizing-power-bi-hosted-models"></a>Optimización de modelos hospedados en Power BI

La optimización de los modelos hospedados en una capacidad Premium se puede lograr en los niveles del origen de datos y el modelo.

Tenga en cuenta las posibilidades de optimización de un modelo de importación:

![Posibilidades de optimización de un modelo de importación](media/service-premium-capacity-optimize/import-model-optimizations.png)

En el nivel de origen de datos:

- Los orígenes de datos relacionales se pueden optimizar para garantizar la actualización más rápida posible mediante la integración previa de los datos, la aplicación de los índices adecuados, la definición de particiones de tabla acordes con los períodos de actualización incremental y la materialización de cálculos (en lugar de tablas y columnas de modelos calculados), o bien mediante la adición de lógica de cálculo a las vistas.
- Los orígenes de datos no relacionales se pueden integrar previamente con almacenes relacionales.
- Asegúrese de que las puertas de enlace tienen recursos suficientes, preferiblemente en equipos dedicados, con suficiente ancho de banda de red y que están cerca de los orígenes de datos.

En el nivel de modelo:

- Los diseños de consulta de Power Query pueden minimizar o quitar transformaciones complejas, especialmente las que combinan distintos orígenes de datos (los almacenes de datos lo logran durante su fase de extracción, transformación y carga). Además, al asegurarse de que se establecen los niveles de privacidad del origen de datos adecuados, se puede evitar la necesidad de que Power BI cargue resultados completos para generar un resultado combinado en las consultas.
- La estructura del modelo determina los datos que se van a cargar y tiene un impacto directo en el tamaño del modelo. Se puede diseñar para evitar la carga de datos innecesarios mediante la eliminación de columnas y filas (especialmente datos históricos), o la carga de datos resumidos (a costa de cargar datos detallados). Se puede lograr una reducción drástica del tamaño si se quitan las columnas de cardinalidad (especialmente las columnas de texto) que no se almacenan ni comprimen de manera muy eficaz.
- El rendimiento de la consulta del modelo se puede mejorar mediante la configuración de relaciones de dirección única, a menos que haya una buena razón para permitir el filtrado bidireccional. Considere también la posibilidad de usar la función [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) en lugar del filtrado bidireccional.
- Las tablas de agregación pueden obtener respuestas de consulta rápidas mediante la carga de datos resumidos previamente, pero esto aumentará el tamaño del modelo y dará lugar a tiempos de actualización más largos. Por lo general, las tablas de agregación se deben reservar para modelos muy grandes o diseños de modelos compuestos.
- Las tablas y columnas calculadas aumentan el tamaño del modelo y dan lugar a tiempos de actualización más largos. Por lo general, se puede lograr un tamaño de almacenamiento más pequeño y un tiempo de actualización más rápido cuando los datos se materializan o calculan en el origen de datos. Si esto no es posible, el uso de columnas personalizadas de Power Query puede ofrecer una compresión de almacenamiento mejorada.
- Es posible que se puedan ajustar expresiones DAX para medidas y reglas de RLS, y reescribir la lógica para evitar fórmulas costosas
- La actualización incremental puede reducir drásticamente el tiempo de actualización y conservar la memoria y la CPU. La actualización incremental también se puede configurar para quitar datos históricos y mantener el recorte de los tamaños de modelo.
- Un modelo se podría rediseñar como dos cuando existen patrones de consulta diferentes y en conflicto. Por ejemplo, algunos informes presentan agregados generales de todo el historial y pueden tolerar una latencia de 24 horas. Otros informes se limitan a los datos actuales y necesitan acceso pormenorizado a transacciones individuales. En lugar de diseñar un único modelo para satisfacer todos los informes, cree dos modelos optimizados para cada requisito.

Tenga en cuenta las posibilidades de optimización de un modelo de DirectQuery. A medida que el modelo emite solicitudes de consulta al origen de datos subyacente, la optimización del origen de datos es fundamental para entregar consultas de modelo que respondan.

 ![Posibilidades de optimización de un modelo de DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

En el nivel de origen de datos:

- El origen de datos se puede optimizar para garantizar la consulta más rápida posible mediante la integración previa de los datos (que no es posible en el nivel de modelo), la aplicación de los índices adecuados, la definición de particiones de tabla, la materialización de datos resumidos (con vistas indexadas) y la minimización de la cantidad de cálculos. La mejor experiencia se consigue cuando las consultas de paso a través solo necesitan filtrar y realizar combinaciones internas entre tablas o vistas indexadas.
- Asegúrese de que las puertas de enlace tienen recursos suficientes, preferiblemente en equipos dedicados, con suficiente ancho de banda de red y están cerca del origen de datos.

En el nivel de modelo:

- Preferiblemente, los diseños de consulta de Power Query no deberían aplicar transformaciones; de lo contrario, intente mantener las transformaciones al mínimo absoluto.
- El rendimiento de la consulta del modelo se puede mejorar mediante la configuración de relaciones de dirección única, a menos que haya una buena razón para permitir el filtrado bidireccional. Además, las relaciones del modelo se deben configurar para asumir que se aplica la integridad referencial (cuando este es el caso) y, como resultado, en las consultas de orígenes de datos se usarán combinaciones internas más eficaces (en lugar de combinaciones externas).
- Evite crear columnas personalizadas de consultas de Power Query o columnas calculadas del modelo: intente materializarlas en el origen de datos, siempre que sea posible.
- Es posible que se puedan ajustar expresiones DAX para medidas y reglas de RLS, y reescribir la lógica para evitar fórmulas costosas.

Tenga en cuenta las posibilidades de optimización de un modelo compuesto. Recuerde que un modelo compuesto permite una combinación de tablas de importación y de DirectQuery.

![Posibilidades de optimización de un modelo compuesto](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Por lo general, la optimización de los modelos de importación y DirectQuery se aplica a las tablas de modelo compuesto en las que se usan estos modos de almacenamiento.
- Es habitual intentar lograr un diseño equilibrado mediante la configuración de tablas de tipo de dimensión (que representan entidades empresariales) en modo de almacenamiento dual, y las tablas de tipo de hechos (a menudo tablas grandes que representan hechos operativos) en modo de almacenamiento de DirectQuery. El modo de almacenamiento dual equivale a los modos de almacenamiento de importación y de DirectQuery, lo que permite al servicio Power BI determinar el modo de almacenamiento más eficaz para usarlo al generar una consulta nativa para la operación de paso a través.
- Asegúrese de que las puertas de enlace tienen recursos suficientes, preferiblemente en equipos dedicados, con suficiente ancho de banda de red y que están cerca de los orígenes de datos
- Las tablas de agregaciones configuradas como modo de almacenamiento de importación pueden mejorar de forma considerable el rendimiento de las consultas cuando se usan para resumir tablas de tipo de hechos en modo de almacenamiento de DirectQuery. En este caso, las tablas de agregación aumentarán el tamaño del modelo y el tiempo de actualización, lo que a menudo resulta aceptable y compensa para obtener consultas más rápidas.

### <a name="optimizing-externally-hosted-models"></a>Optimización de modelos hospedados externamente

Muchas de las posibilidades de optimización descritas en la sección [Optimización de modelos hospedados en Power BI](#optimizing-power-bi-hosted-models) también se aplican a los modelos desarrollados con Azure Analysis Services y SQL Server Analysis Services. Las excepciones evidentes son ciertas características que no se admiten en la actualidad, incluidos los modelos compuestos y las tablas de agregación.

Una consideración adicional para los conjuntos de datos hospedados externamente es el hospedaje de la base de datos en relación con el servicio Power BI. Para Azure Analysis Services, esto significa crear el recurso de Azure en la misma región que el inquilino de Power BI (la región principal). Para SQL Server Analysis Services, en el caso de IaaS, esto significa hospedar la máquina virtual en la misma región y, para el entorno local, garantizar una configuración de puerta de enlace eficaz.

Por otra parte, puede ser de interés destacar que en las bases de datos de Azure Analysis Services y las bases de datos tabulares de SQL Server Analysis Services es necesario que los modelos se carguen completamente en memoria y que permanezcan allí de forma continua para admitir las consultas. Como sucede en el servicio Power BI, debe haber memoria suficiente para la actualización si el modelo debe permanecer en línea durante la actualización. A diferencia de lo que ocurre en el servicio Power BI, no hay ningún concepto de que la memoria de los modelos aumente o disminuya de forma automática en función del uso. Por tanto, Power BI Premium ofrece un enfoque más eficaz para maximizar las consultas de modelos con un menor uso de memoria.

## <a name="capacity-planning"></a>Planeamiento de capacidad

El tamaño de una capacidad Premium determina la memoria disponible y los recursos del procesador y los límites impuestos en la capacidad. También se debe tener en cuenta el número de capacidades Premium, ya que la creación de varias capacidades Premium puede facilitar el aislamiento de las cargas de trabajo entre sí. Recuerde que el almacenamiento es de 100 TB por nodo de capacidad, lo que probablemente sea más que suficiente para cualquier carga de trabajo.

Determinar el tamaño y el número de capacidades Premium puede ser un reto, especialmente para las capacidades iniciales que cree. Al ajustar el tamaño de la capacidad, el primer paso consiste es comprender el promedio de carga de trabajo que representa el uso cotidiano esperado. Es importante entender que no todas las cargas de trabajo son iguales. Por ejemplo, en un extremo de un espectro, 100 usuarios simultáneos que acceden a una sola página de un informe que contiene un solo objeto visual se puede conseguir fácilmente. Pero, en el otro extremo del espectro, 100 usuarios simultáneos que acceden a 100 informes distintos, cada uno con 100 objetos visuales en la página del informe, supondrá una demanda muy distinta de los recursos de la capacidad.

Por tanto, los administradores de capacidad deberán tener en cuenta muchos factores específicos del entorno, el contenido y el uso esperado. El objetivo de invalidación es maximizar la utilización de la capacidad, a la vez que se proporcionan tiempos de consulta coherentes, tiempos de espera aceptables y tasas de expulsión. Algunos factores que se deben tener en cuenta son los siguientes:

- **Tamaño del modelo y características de los datos**: los modelos de importación se deben cargar totalmente en memoria para permitir la consulta o la actualización. Los conjuntos de datos de LC/DQ pueden requerir mucho tiempo de procesador y posiblemente mucha memoria para evaluar medidas complejas o reglas RLS. El tamaño de la memoria y del procesador, y el rendimiento de las consultas LC/DQ están restringidos por el tamaño de la capacidad.
- **Modelos activos simultáneos**: la consulta simultánea de diferentes modelos de importación proporcionará mejor capacidad de respuesta y rendimiento cuando permanecen en la memoria. Debe haber memoria suficiente para hospedar todos los modelos que se consultan de manera intensiva, con memoria adicional para permitir su actualización.
- **Importación de la actualización del modelo**: el tipo de actualización (completa o incremental), la duración y la complejidad de las consultas de Power Query y la lógica de tablas o columnas calculadas pueden afectar a la memoria y, en especial, al uso del procesador. Las actualizaciones simultáneas están limitadas por el tamaño de la capacidad (1,5 x núcleos virtuales de back-end, redondeado hacia arriba).
- **Consultas simultáneas**: muchas consultas simultáneas pueden dar lugar a informes que no responden cuando las conexiones del procesador o LC/DQ superan el límite de la capacidad. Esto sucede especialmente con las páginas de informe que incluyen muchos objetos visuales.
- **Flujos de datos e informes paginados**: la capacidad se puede configurar para admitir flujos de datos e informes paginados, y cada uno requiere un porcentaje máximo de memoria de la capacidad que se puede configurar. La memoria se asigna de manera dinámica a los flujos de datos, pero de forma estática a los informes paginados.

Además de estos factores, los administradores de capacidad pueden considerar la posibilidad de crear varias capacidades. Varias capacidades permiten el aislamiento de las cargas de trabajo y se pueden configurar para garantizar que las cargas de trabajo prioritarias tengan recursos garantizados. Por ejemplo, se pueden crear dos capacidades para separar las cargas de trabajo críticas para la empresa de las cargas de trabajo de inteligencia empresarial con características de autoservicio (SSBI). La capacidad crítica para la empresa se puede usar para aislar modelos corporativos de gran tamaño proporcionándoles recursos garantizados, y conceder el acceso de creación solo al departamento de TI. La capacidad de SSBI se puede usar para hospedar un número creciente de modelos más pequeños, y conceder el acceso a los analistas de negocios. La capacidad de SSBI puede experimentar ocasionalmente esperas de consulta o actualización tolerables.

Con el tiempo, los administradores de capacidad pueden equilibrar las áreas de trabajo entre las capacidades si mueven contenido entre las áreas de trabajo, o bien las áreas de trabajo entre las capacidades, y si escalan las capacidades vertical u horizontalmente. Por lo general, para hospedar modelos más grandes se escala verticalmente y para una mayor simultaneidad se escala horizontalmente.

Recuerde que la compra de una licencia proporciona núcleos virtuales al inquilino. La compra de una suscripción **P3** se puede usar para crear una o hasta cuatro capacidades Premium, es decir, 1 x P3, 2 x P2 o 4 x P1. Además, antes de convertir una capacidad P2 a una capacidad P3, se puede considerar la posibilidad de dividir los núcleos virtuales para crear dos capacidades P1.

## <a name="testing-approaches"></a>Enfoques de prueba

Una vez que se ha decidido el tamaño de la capacidad, se pueden realizar pruebas mediante la creación de un entorno controlado. Una opción práctica y económica consiste en crear una capacidad de Azure (SKU), sin olvidar que una capacidad P1 tiene el mismo tamaño que una capacidad A4, y que las capacidades P2 y P3 tienen el mismo tamaño que las capacidades A5 y A6, respectivamente. Las capacidades de Azure se pueden crear de forma rápida y se facturan por hora. Por tanto, una vez completadas las pruebas, se pueden eliminar fácilmente para dejar de acumular costos.

El contenido de las pruebas se puede agregar a las áreas de trabajo creadas en la capacidad de Azure y, después, como un solo usuario que puede ejecutar informes para generar una carga de trabajo realista y representativa de las consultas. Si hay modelos de importación, también se debe realizar una actualización de cada uno. Se pueden usar herramientas de supervisión para revisar todas las métricas y comprender el uso de los recursos.

Es importante que las pruebas sean repetibles. Las pruebas se deben ejecutar varias veces y deben proporcionar aproximadamente el mismo resultado cada vez. Se puede usar un promedio de estos resultados para extrapolar y calcular una carga de trabajo en condiciones reales de producción.

Si ya tiene una capacidad y los informes para los que quiere realizar pruebas de carga, use la [herramienta de generación de cargas de PowerShell](https://aka.ms/PowerBILoadTestingTool) para generar rápidamente una prueba de carga. La herramienta permite calcular el número de instancias de cada informe que la capacidad puede ejecutar en una hora. Puede usar la herramienta para evaluar si la capacidad puede representar informes individuales o varios informes diferentes en paralelo. Para más información, vea el vídeo [Microsoft Power BI: capacidad Premium](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Para generar una prueba más compleja, considere la posibilidad de desarrollar una aplicación de prueba de carga que simule una carga de trabajo realista. Para más información, vea el seminario web [Load Testing Power BI Applications with Visual Studio Load Test](https://powerbi.microsoft.com/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/) (Pruebas de carga de aplicaciones de Power BI con la prueba de carga de Visual Studio).

## <a name="acknowledgements"></a>Agradecimientos

Este artículo es obra de Peter Myers, MVP de plataforma de datos y experto independiente de BI con [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Escenarios de las capacidades Premium](service-premium-capacity-scenarios.md)   
  
¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)