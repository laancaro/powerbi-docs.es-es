---
title: Escenarios de capacidad de Microsoft Power BI Premium
description: Describe escenarios comunes de capacidad de Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565346"
---
# <a name="premium-capacity-scenarios"></a>Escenarios de capacidad Premium

En este artículo se describe situaciones del mundo real donde se han implementado las capacidades de Power BI premium. Problemas comunes y desafíos se describen, también cómo identificar problemas y ayudar a resolverlos:

- [Mantener actualizados los conjuntos de datos](#keeping-datasets-up-to-date)
- [Identificación de los conjuntos de datos de respuesta lento](#identifying-slow-responding-datasets)
- [Identificar las causas de forma esporádica lenta-responder los conjuntos de datos](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinar si hay suficiente memoria.](#determining-whether-there-is-enough-memory)
- [Determina si hay suficiente CPU](#determining-whether-there-is-enough-cpu)

Son los pasos, junto con ejemplos de gráfico y tabla desde el **métricas de capacidad de Power BI Premium app** que un administrador de Power BI tendrán acceso a.

## <a name="keeping-datasets-up-to-date"></a>Mantener actualizados los conjuntos de datos

En este escenario, se desencadenó una investigación cuando los usuarios reciben quejas que los datos de informe a veces parecían ser anterior o "obsoletas".

En la aplicación, el administrador interactúa con el **actualiza** visual, ordenar los conjuntos de datos la **de tiempo de espera máximo** estadísticas en orden descendente. Este objeto visual les ayuda a revelar los conjuntos de datos con los tiempos de espera más largos, agrupados por nombre de área de trabajo.

![Actualizaciones del conjunto de datos ordenadas por orden descendente de tiempo de espera máximo, agrupada por área de trabajo](media/service-premium-capacity-scenarios/dataset-refreshes.png)

En el **por hora promedio actualizar tiempos de espera de** visual, tenga en cuenta que los tiempos de espera de actualización de forma coherente máxima aproximadamente 4 P.M. cada día.

![Actualización de espera máximo periódicamente a las 4 P.M.](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Hay varios posibles explicaciones de estos resultados:

- Demasiados intentos de actualización podrían estar produciéndose al mismo tiempo, si se supera los límites definidos por el nodo de capacidad. En este caso, seis de las actualizaciones simultáneas en una P1 con asignación de memoria predeterminada.

- Actualizar conjuntos de datos pueden ser demasiado grande para caber en la memoria disponible (lo que requiere al menos 2 veces la memoria necesaria para la actualización completa).
- Lógica de Power Query ineficaz es posible que lo que en un pico de uso de memoria durante la actualización del conjunto de datos. En una capacidad ocupada, este aumento en ocasiones, puede alcanzar el límite físico, por error de la actualización y pueden afectar a otras operaciones de vista de informe en la capacidad.
- Conjuntos de datos consultados con más frecuencia que deben permanecer en memoria pueden afectar a la capacidad de otros conjuntos de datos para actualizar debido a la memoria disponible limitada.

Para ayudar a investigar, puede buscar el Administrador de Power BI:

- Poca memoria disponible en el momento de datos se actualiza cuando la memoria disponible es inferior a 2 veces el tamaño del conjunto de datos que se va a actualizar.
- Conjuntos de datos no se actualizan y no en la memoria antes de actualizar, aún empezó a mostrar tráfico interactiva durante las horas de actualización pesado. Para ver qué conjuntos de datos se cargan en memoria en un momento dado, un administrador de Power BI puede mirar el área de conjuntos de datos de **conjuntos de datos** pestaña en la aplicación. El administrador puede, a continuación, filtro cruzado a un momento dado, haga clic en una de las barras en el **conjunto de datos cargados por hora recuentos**. Un pico local, que se muestra en la imagen siguiente, indica una hora cuando varios conjuntos de datos se cargaron en la memoria, lo que podría retrasar el inicio de las actualizaciones programadas.
- Expulsiones de conjunto de datos mayor teniendo lugar cuando las actualizaciones de datos están programadas para iniciarse. Allí pueden indicar al expulsiones produjo alta presión de memoria que sirven para muchos informes interactivos diferentes antes de la fecha de actualización. El **expulsiones de conjunto de datos por hora y el consumo de memoria** visual puede indicar claramente los picos de expulsiones.

La siguiente imagen muestra un pico local en los conjuntos de datos cargado, lo que sugiere consultas interactivas retrasa el inicio de las actualizaciones de. Seleccionar un período de tiempo en el **conjunto de datos cargados por hora recuentos** visual cruzará filtro el **tamaños del conjunto de datos** visual.

![Un pico en cargar conjuntos de datos local sugiere interactivo Inicio demorado consultas de las actualizaciones](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

El Administrador de Power BI puede intentar resolver el problema realizando los pasos para asegurarse de que está disponible para las actualizaciones de datos por memoria suficiente:

- Ponerse en contacto con el conjunto de datos de los propietarios y que se les solicita para escalonar y Beba datos programaciones de actualización.
- Reducir el conjunto de datos de carga de consultas mediante la eliminación de paneles innecesarios o panel iconos, especialmente los que aplicar la seguridad de nivel de fila.
- Acelerar las actualizaciones de datos al optimizar la lógica de Power Query. Mejorar el modelado de las columnas calculadas o tablas. Reducir el tamaño del conjunto de datos o configurar más grandes conjuntos de datos para llevar a cabo la actualización de datos incrementales.

## <a name="identifying-slow-responding-datasets"></a>Identificación de los conjuntos de datos de respuesta lento

En este escenario, una investigación comenzó cuando los usuarios reciben quejas que determinados informes tardaron demasiado tiempo en Abrir y a veces dejaba de responder.

En la aplicación, puede usar el Administrador de Power BI el **consulta duraciones** visual para determinar los conjuntos de datos con peor rendimiento al ordenar por orden descendente de los conjuntos de datos **promedio de duración**. Este objeto visual también muestra conjunto de datos, los recuentos de consulta para que pueda ver con qué frecuencia se consultan los conjuntos de datos.

![Conjuntos de datos con peor rendimiento](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

El administrador puede hacer referencia a la **distribución de duración de la consulta** visual, que muestra una distribución global de rendimiento de las consultas de depósitos (< = ubicación 30, 0-100 ms) para el período de tiempo filtrado. Por lo general, las consultas que toman un segundo o menos se considera con capacidad de respuesta mediante la mayoría de los usuarios; las consultas que tardan más tiempo tienden a crear una percepción de rendimiento incorrecto.

El **distribución por hora de duración de consulta** visual permite que el Administrador de Power BI identificar los períodos de una hora cuando el rendimiento de capacidad podría haber ha percibe malos. Cuanto mayor sea la barra de segmentos de esa consulta representan duraciones durante un segundo, mayor será el riesgo de que los usuarios notarán un rendimiento deficiente.

El objeto visual es interactivo y, cuando se selecciona un segmento de la barra, el correspondiente **consulta duraciones** visual en la página del informe de tabla es realizar un filtrado cruzado para mostrar los conjuntos de datos representa. Este filtrado cruzado permite que el Administrador de Power BI identificar fácilmente que los conjuntos de datos responden con lentitud.

La siguiente imagen muestra un objeto visual filtrado **distribuciones por hora de duración de consulta**, especializado en los conjuntos de datos con peor rendimiento de los cubos de una hora. 

![Filtrado por hora consulta duración distribuciones visual muestra el peor realizar conjuntos de datos](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Una vez que se identifica el conjunto de datos de rendimiento deficiente en un intervalo de tiempo específico de una hora, el Administrador de Power BI puede investigar si está provocado por una capacidad sobrecargada un rendimiento deficiente o debido a un mal diseñado el conjunto de datos o informe. Puede hacer referencia a la **tiempos de espera de consulta** visual y conjuntos de datos de ordenar por orden descendente de tiempo de espera de la media de las consultas. Si está esperando un porcentaje elevado de consultas, una gran demanda para el conjunto de datos es probablemente la causa de demasiadas esperas de consulta. Si el tiempo de espera de la media de las consultas es importante (> 100 ms), es posible que vale la pena revisar el conjunto de datos y el informe para ver si se pueden realizar las optimizaciones. Por ejemplo, menos objetos visuales de recibir las páginas del informe o una optimización de la expresión de DAX.

![El objeto visual de tiempos de espera de consulta ayuda a revelar los conjuntos de datos de rendimiento bajo](media/service-premium-capacity-scenarios/query-wait-times.png)

Hay varias razones posibles para la acumulación de tiempo de espera de consulta en conjuntos de datos:

- Un modelo no óptimo, expresiones de medida o diseño de informe incluso - todas las circunstancias que pueden contribuir a las consultas que consumen los niveles altos de CPU de larga ejecución. Esto obliga a las nuevas consultas para esperar hasta que los subprocesos de CPU disponibles y pueden crear un efecto de convoy (atasco de tráfico de reflexión), que se observa habitualmente durante las horas punta. El **consulta espera** página será el principal recurso para determinar si los conjuntos de datos tienen tiempos de espera de la media alta de las consultas.
- Un gran número de usuarios simultáneos de capacidad (cientos de miles) consumiendo el mismo informe o conjunto de datos. Conjuntos de datos incluso bien diseñada pueden tener un mal rendimiento supera un umbral de simultaneidad. Esto normalmente se indica mediante un único conjunto de datos que muestra un valor considerablemente mayor para la consulta cuenta que otros mostrar conjuntos de datos (por ejemplo, 300 K consulta para un conjunto de datos en comparación con < 30 KB consultas para todos los otros conjuntos de datos). En algún momento las esperas de consulta para este conjunto de datos se iniciará escalonar, que se puede ver en el **consulta duraciones** visual.
- Muchos diversos conjuntos de datos consultados al mismo tiempo, provocando hiperpaginación como conjuntos de datos con frecuencia del ciclo dentro y fuera de la memoria. Esto resulta en usuarios experimenta un rendimiento lento cuando el conjunto de datos se carga en memoria. Para confirmar, el Administrador de Power BI puede hacer referencia a la **expulsiones de conjunto de datos por hora y el consumo de memoria** visual, que puede indicar que un gran número de conjuntos de datos se carga en memoria se repetidamente expulsan.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificar las causas de forma esporádica lenta-responder los conjuntos de datos

En este escenario, una investigación comenzó cuando los usuarios se describe que objetos visuales de informes a veces se tarda en responder o podrían dejar de responder, pero en otras ocasiones estaban con capacidad de respuesta aceptable.

Dentro de la aplicación, el **consulta duraciones** sección utilizada para buscar el conjunto de datos de la causa de la manera siguiente:

- En el **consulta duraciones** visual el administrador filtra el conjunto de datos (comenzando por los conjuntos de datos principales consultados) el conjunto de datos y examinar las barras de filtrado cruzadas en la **distribuciones de consulta por hora** visual.
- Cuando una sola barra una hora mostró cambios significativos en la relación entre todos los grupos de duración de consulta frente a otras barras de una hora para ese conjunto de datos (por ejemplo, las relaciones entre los colores cambia drásticamente), significa que este conjunto de datos muestra un cambio de esporádico rendimiento.
- Las barras de una hora que muestra una parte irregular de las consultas de rendimiento deficientes, indica un intervalo de tiempo donde ese conjunto de datos se haya visto afectado por un efecto de vecino ruidoso, causado por actividades de otros conjuntos de datos.

La imagen siguiente muestra una hora, 30 de enero, de donde se ha producido un obstáculo significativo del rendimiento de un conjunto de datos, indicado por el tamaño de la "(3,10s]"duración depósito de ejecución. Al hacer clic en esa barra de una hora, se muestra todos los conjuntos de datos cargados en la memoria durante ese tiempo, presentar conjuntos de datos posibles provocando el efecto de vecino ruidoso.

![Que muestra peor rendimiento por una gran parte de la barra](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Una vez que se identifica un intervalo de tiempo problemático (por ejemplo, durante el 30 de enero en la imagen anterior) del Administrador de Power BI puede quitar todos los filtros de conjunto de datos, a continuación, filtrar únicamente por ese intervalo de tiempo para determinar qué conjuntos de datos se consultaron activamente durante este tiempo. El conjunto de datos de la causa del efecto de vecino ruidoso normalmente es el conjunto de datos consultado superior o uno con la duración más larga Media de las consultas.

Una solución a este problema podría ser para distribuir al culpable se admiten conjuntos de datos a través de diferentes áreas de trabajo en las diferentes capacidades Premium, o en capacidad compartida si el tamaño del conjunto de datos, los requisitos de consumo y actualización de datos patrones.

También pudo true la inversa. El Administrador de Power BI podría identificar veces cuando un conjunto de datos de rendimiento de consulta mejora drásticamente y, a continuación, busque lo que ha desaparecido. Si falta cierta información en ese momento, que puede ayudar para que apunte al problema que producen.

## <a name="determining-whether-there-is-enough-memory"></a>Determinar si hay suficiente memoria.

Para determinar si hay suficiente memoria para la capacidad para completar sus cargas de trabajo, el Administrador de Power BI puede hacer referencia a la **porcentajes de memoria consumida** visual en el **conjuntos de datos** pestaña de la aplicación. **Todos los** memoria (total) representa la memoria consumida por los conjuntos de datos que se cargan en memoria, independientemente de si están consultar o procesar activamente. **Active** memoria representa la memoria consumida por los conjuntos de datos que se están procesando activamente.

En una capacidad en buen estado, el objeto visual aparecerá como esta, que muestra un intervalo entre todas (total) y la memoria activa:

![Una capacidad en buen estado mostrará un espacio entre todos los (total) y la memoria activa](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

En una capacidad que experimenta la presión de memoria, al mismo objeto visual mostrará claramente memoria activa y la memoria total convergen, lo que significa que no podrá cargar conjuntos de datos adicionales en la memoria, a continuación. En este caso, el Administrador de Power BI puede hacer clic **capacidad reiniciar** (en **opciones avanzadas** del área de configuración de la capacidad del portal de administración). Reiniciando los resultados de la capacidad en todos los conjuntos de datos que se va a vacían de la memoria y se le permite volver a cargar en la memoria según sea necesario (por las consultas o actualización de datos).

![** Activo memoria convergiendo con ** memoria All **](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Determina si hay suficiente CPU

En general, uso de una capacidad medio de CPU debe permanecer por debajo del 80%. Si se supera este valor significa que la capacidad se está aproximando a la saturación de la CPU.

Efectos de la saturación de la CPU se expresan mediante operaciones tardan más de debería, debido a la capacidad de realizar muchos cambios de contextos de CPU mientras intenta procesar todas las operaciones. En una capacidad Premium con un gran número de consultas simultáneas, esto se indica mediante los tiempos de espera de consulta alta. Una consecuencia de los tiempos de espera de consulta alta es la capacidad de respuesta más lenta de lo habitual. El Administrador de Power BI puede identificar fácilmente cuando la CPU está saturada observando el **distribuciones de tiempo de espera de consulta por hora** visual. Recuentos de indican posible saturación de la CPU de tiempo de espera de picos periódicos de consulta.

![Recuentos de indican posible saturación de la CPU de tiempo de espera de picos periódicos de consulta](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

A veces se puede detectar un patrón similar en operaciones en segundo plano si contribuyen a la saturación de la CPU. Un administrador de Power BI puede buscar un pico periódico en tiempos de actualización para un conjunto de datos específico, lo que puede indicar la saturación de la CPU en el momento (probablemente debido a otras actualizaciones en curso del conjunto de datos o consultas interactivas). En este caso, que hace referencia a la **sistema** vista de la aplicación puede no necesariamente revelar que la CPU está al 100%. El **sistema** vista muestra los promedios de cada hora, pero la CPU puede saturarse durante varios minutos de operaciones intensivas, que se muestra como los picos en tiempos de espera.

Hay más matices a ver el efecto de saturación de la CPU. Aunque el número de consultas que esperan es importante, tiempo de espera de consulta siempre se realizará en cierta medida sin causar una degradación del rendimiento perceptible. Algunos conjuntos de datos (con la hora media de las consultas más largo, que indica la complejidad o tamaño) son más propensas a los efectos de saturación de la CPU que otras. Para identificar fácilmente estos conjuntos de datos, el Administrador de Power BI pueda buscar cambios en la composición de color de las barras en el **distribución del tiempo de espera por hora** visual. Después de detectar una barra de valores atípicos, pueden buscar los conjuntos de datos que tenía esperas de consulta durante ese tiempo y examine también el tiempo de espera de la media de las consultas en comparación con el promedio de duración de la consulta. Cuando estas dos métricas son de la misma magnitud y la carga de trabajo de consulta del conjunto de datos no es trivial, es probable que el conjunto de datos se ve afectado por una CPU insuficiente.

Este efecto puede ser especialmente evidente cuando se consume un conjunto de datos en ráfagas cortas de las consultas de alta frecuencia por varios usuarios (por ejemplo, en una sesión de entrenamiento), lo que produce la saturación de CPU durante cada ráfagas. En este caso, se pueden experimentar tiempos de espera de consulta importantes en este conjunto de datos, así como afectar en otros conjuntos de datos en la capacidad (efecto de vecino ruidoso).

En algunos casos, los administradores de Power BI pueden solicitar que los propietarios del conjunto de datos crean una menor carga de trabajo volátiles consulta mediante la creación de un panel (actualización de las consultas que periódicamente con cualquier conjunto de datos para los iconos en caché) en lugar de un informe. Esto puede ayudar a evitar picos cuando se carga el panel. Esta solución no sea siempre posible dados los requisitos empresariales, pero puede ser una forma eficaz para evitar la saturación de CPU, sin realizar ningún cambio en el conjunto de datos.

## <a name="acknowledgements"></a>Confirmaciones

En este artículo se escribió por Peter Myers, MVP de la plataforma de datos y experto en BI independiente con [bit a bit soluciones](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Supervisar las capacidades Premium con la aplicación](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Capacidades del monitor en el portal de administración](service-admin-premium-monitor-portal.md)   

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

||||||