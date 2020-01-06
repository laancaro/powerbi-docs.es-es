---
title: Escenarios adecuados para las capacidades de Microsoft Power BI Premium
description: Describe los escenarios adecuados para las capacidades más habituales de Microsoft Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 9b3e06172d29f218f9234cf1f3d7e1f623495001
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "74697276"
---
# <a name="premium-capacity-scenarios"></a>Escenarios de las capacidades Premium

En este artículo se describen escenarios del mundo real en los que se han implementado las capacidades Premium de Power BI. También se describen problemas y desafíos habituales, cómo identificar los problemas y se proporciona ayuda para solucionarlos:

- [Mantenimiento actualizado de los conjuntos de datos](#keeping-datasets-up-to-date)
- [Identificación de los conjuntos de datos de respuesta lenta](#identifying-slow-responding-datasets)
- [Identificación de los motivos por los cuales los conjuntos de datos presentan esporádicamente una respuesta lenta](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinar si hay suficiente memoria](#determining-whether-there-is-enough-memory)
- [Determinar si hay suficiente CPU](#determining-whether-there-is-enough-cpu)

Los pasos, junto con los gráficos y las tablas de ejemplo, proceden de la **aplicación Métricas de capacidad de Power BI Premium** a la que accede un administrador de Power BI.

## <a name="keeping-datasets-up-to-date"></a>Mantenimiento actualizado de los conjuntos de datos

En este escenario, se ha iniciado una investigación porque los usuarios se han quejado de que los datos del informe parecían a veces antiguos u "obsoletos".

En la aplicación, el administrador interactúa con el objeto visual **Actualizaciones**, ordenando los conjuntos de datos según las estadísticas de **tiempo de espera máximo** en orden descendente. Este objeto visual ayuda a mostrar los conjuntos de datos que tienen los tiempos de espera más largos, agrupados por nombre de área de trabajo.

![Actualizaciones de conjuntos de datos en orden descendente según el tiempo de espera máximo, agrupados por área de trabajo](media/service-premium-capacity-scenarios/dataset-refreshes.png)

En el objeto visual **Tiempos de espera de actualización promedio por hora** se puede observar que el pico de los tiempos de espera de actualización se produce normalmente alrededor de las 4 p. m. cada día.

![Pico de espera de actualización que se produce normalmente a las 4 p. m.](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Hay varias posibles explicaciones para estos resultados:

- Puede que se produzcan demasiados intentos de actualización al mismo tiempo, superando los límites que define el nodo de capacidad. En este caso hay seis actualizaciones simultáneas en P1 con asignación de memoria predeterminada.

- Los conjuntos de datos que se van a actualizar pueden ser demasiado grandes para la memoria disponible (ya que se requiere al menos el doble de memoria de la que se necesita para una actualización completa).
- Una lógica de Power Query ineficaz puede resultar en un pico de uso de memoria durante la actualización del conjunto de datos. En el caso de una capacidad ocupada, este pico puede alcanzar ocasionalmente el límite físico, lo cual hará que se produzca un error en la actualización que posiblemente afecte a otras operaciones de vista de informes sobre la capacidad.
- Los conjuntos de valores que se consultan con frecuencia y que necesitan permanecer en la memoria pueden afectar a la capacidad de actualización de otros conjuntos de datos debido a que la memoria disponible está limitada.

Para ayudar con la investigación, el administrador de Power BI puede buscar:

- Poca memoria disponible en el momento de actualizar los datos cuando la memoria disponible es menor que el doble del tamaño del conjunto de datos que se va a actualizar.
- Conjuntos de datos que no se actualizan y que no están en la memoria antes de la actualización y que, sin embargo, han empezado a mostrar tráfico interactivo durante los tiempos de actualización intensos. Para ver los conjuntos de datos que hay cargados en la memoria en un momento dado, el administrador de Power BI puede ver el área de conjuntos de datos de la pestaña **Conjuntos de datos** de la aplicación. Después, el administrador puede realizar un filtrado cruzado en un momento dado haciendo clic en una de las barras de **Recuentos de conjuntos de datos cargados por hora**. Un pico local, como el que aparece en la siguiente imagen, indica una hora en la que varios conjuntos de datos se cargaron en memoria, lo que pudo retrasar el inicio de las actualizaciones programadas.
- Un aumento de las expulsiones de conjuntos de datos que tiene lugar en el momento en que, según la programación, van a comenzar las actualizaciones de datos. Las expulsiones pueden indicar que hubo un uso excesivo de memoria provocado por la realización de muchos informes interactivos diferentes con anterioridad al momento de la actualización. El objeto visual **Consumo de memoria y expulsiones de conjuntos de datos por horas** puede indicar con claridad picos en el número de expulsiones.

En la siguiente imagen se muestra un pico local en el número de conjuntos de datos cargados que sugiere que las consultas interactivas retrasaron el inicio de las actualizaciones. Si selecciona un período de tiempo en el objeto visual **Recuentos de conjuntos de datos cargados por hora** se realizará un filtrado cruzado en el objeto visual **Tamaños de conjuntos de datos**.

![Un pico local en el número de conjuntos de datos cargados indica que las consultas interactivas retrasaron el inicio de las actualizaciones.](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

El administrador de Power BI puede intentar resolver el problema tomando medidas para garantizar que haya suficiente memoria disponible para que las actualizaciones de datos se inicien. Para ello debe hacer lo siguiente:

- Ponerse en contacto con los propietarios de los conjuntos de datos y pedirles que escalonen y espacien la programación de las actualizaciones de datos.
- Reducir la carga de consultas de los conjuntos de datos mediante la eliminación de paneles innecesarios o de los iconos que contienen, especialmente aquellos que sirven para aplicar la seguridad de nivel de fila.
- Acelerar las actualizaciones de los datos mediante la optimización de la lógica de Power Query. Mejore el modelado de tablas o columnas calculadas. Reduzca los tamaños de los conjuntos de datos o configure conjuntos de datos más grandes para realizar una actualización incremental de los datos.

## <a name="identifying-slow-responding-datasets"></a>Identificación de los conjuntos de datos de respuesta lenta

En este escenario, se ha iniciado una investigación porque los usuarios se han quejado de que determinados informes tardaban demasiado tiempo en abrirse y, a veces, se bloqueaban.

En la aplicación, el administrador de Power BI puede utilizar el objeto visual **Duraciones de consulta** para determinar los conjuntos de datos de peor rendimiento mediante la ordenación de estos en orden descendente por **Duración promedio**. Este objeto visual también muestra los recuentos de consultas de conjuntos de datos, por lo que puede ver la frecuencia con que se consultan estos.

![Conjuntos de datos de peor rendimiento](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

El administrador puede consultar el objeto visual **Distribución de la duración de consulta**, que muestra una distribución general del rendimiento de las consultas en cubos (<= 30 ms, 0-100 ms) para el período de tiempo filtrado. Por lo general, la mayoría de los usuarios consideran que las consultas que tardan un segundo o menos son rápidas y las que tardan más tiempo tienden a crear una sensación de bajo rendimiento.

El objeto visual **Distribuciones por horas de la duración de consulta** permite al administrador de Power BI identificar los períodos de una hora en los que el rendimiento de la capacidad podría haberse percibido como deficiente. Cuanto más superen el límite de un segundo los segmentos de la barra que representan las duraciones de las consultas, mayor será el riesgo de que los usuarios perciban un rendimiento deficiente.

El objeto visual es interactivo y, cuando se selecciona un segmento de la barra, se realiza un filtrado cruzado en el objeto visual correspondiente de la tabla **Duraciones de consulta** en la página de informe para mostrar los conjuntos de datos que representa. Este filtrado cruzado permite al administrador de Power BI identificar fácilmente qué conjuntos de datos responden lentamente.

En la imagen siguiente se muestra un objeto visual que se ha filtrado por **Distribuciones por horas de la duración de consulta**, y que se centra en los conjuntos de datos de peor rendimiento en intervalos de una hora. 

![Objeto visual filtrado "Distribuciones por horas de la duración de consulta" que muestra los conjuntos de datos de peor rendimiento](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Una vez que se identifica el conjunto de datos con mal rendimiento en un intervalo de tiempo específico de una hora, el administrador de Power BI puede investigar si el rendimiento es deficiente debido a una capacidad sobrecargada o a un conjunto de datos o informes mal diseñado. También puede consultar el objeto visual **Tiempos de espera de consulta** y ordenar los conjuntos de datos en orden descendente según el promedio de tiempo de espera de las consultas. Si hay un gran porcentaje de consultas en espera, es probable que la causa sea una demanda excesiva del conjunto de datos. Si el tiempo promedio de espera de consulta es significativo (> 100 ms), puede que merezca la pena revisar el conjunto de datos y el informe para ver si se pueden realizar optimizaciones. Por ejemplo, incluir menos objetos visuales en determinadas páginas del informe o una optimización de la expresión DAX.

![El objeto visual "Tiempos de espera de consulta" ayuda a revelar conjuntos de datos con un rendimiento deficiente](media/service-premium-capacity-scenarios/query-wait-times.png)

Hay varios motivos para la acumulación de tiempos de espera de consulta en los conjuntos de datos:

- Un diseño poco óptimo del modelo, las expresiones de medida o incluso el diseño de informe pueden contribuir a consultas de larga duración que consumen altos niveles de CPU. Esto obliga a que las nuevas consultas tengan que esperar hasta que los subprocesos de la CPU estén disponibles y puede crear un efecto de "caravana" (piense en un atasco de tráfico), que normalmente se puede observar durante el pico de las horas laborales. La página **Tiempos de espera de consulta** será el recurso principal para determinar si los conjuntos de datos tienen promedios elevados de tiempos de espera de consulta.
- Un gran número de usuarios simultáneos de la capacidad (de cientos a miles) que están utilizando el mismo informe o conjunto de datos. Incluso los conjuntos de datos bien diseñados pueden tener un rendimiento deficiente si superan un umbral simultaneidad. Esto queda de manifiesto si hay un único conjunto de datos que muestra un valor de recuento de consultas mucho más elevado que el de otros conjuntos de datos (por ejemplo, 300 000 consultas para un determinado conjunto de datos frente a menos de 30 000 consultas para el resto de conjuntos de datos). En algún momento, los tiempos de espera de consulta empezarán a escalonarse. Esto se puede observar en el objeto visual **Duraciones de consulta**.
- Consulta simultánea de muchos conjuntos de datos diferentes, lo que provoca una hiperpaginación de la memoria, ya que los conjuntos de datos entran y salen frecuentemente de esta. Esto hace que los usuarios experimenten un rendimiento lento cuando el conjunto de datos se carga en la memoria. Para confirmarlo, el administrador de Power BI puede consultar el objeto visual **Consumo de memoria y expulsiones de conjuntos de datos por horas** que puede indicar que se están expulsando repetidamente un gran número de conjuntos de datos cargados en la memoria.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificación de los motivos por los cuales los conjuntos de datos presentan esporádicamente una respuesta lenta

En este escenario, se inició una investigación cuando los usuarios indicaron que, en ocasiones, los objetos visuales de los informes eran lentos al responder o que incluso no respondían, mientras que, en otras ocasiones, tenían un tiempo de respuesta aceptable.

En la aplicación, se usó la sección **Duraciones de consulta** para encontrar el conjunto de datos causante de la siguiente manera:

- En el objeto visual **Duraciones de consulta** el administrador filtró por conjuntos de datos (empezando por los conjuntos de datos más consultados) y examinó las barras con filtros cruzados del objeto visual **Distribuciones por horas de la duración de consulta**.
- Si una sola barra de una hora mostró cambios significativos en la relación entre todos los grupos de duración de consultas en comparación con otras barras de una hora de ese conjunto de datos (por ejemplo, las relaciones entre los colores cambiaron drásticamente), significa que este conjunto de datos mostró un cambio esporádico de rendimiento.
- Las barras de una hora que muestran una porción irregular de consultas con un rendimiento deficiente indican un intervalo de tiempo en el que ese conjunto de datos se ha visto afectado por un efecto de "vecino ruidoso", es decir, un efecto provocado por las actividades de otros conjuntos de datos.

En la imagen siguiente se muestra una hora del día 30 de enero, en la que se produjo un retroceso significativo en el rendimiento de un conjunto de datos, como lo indica el tamaño del intervalo de duración de la ejecución de "(3,10 s)". Al hacer clic en esa barra de una hora, se muestran todos los conjuntos de datos que se cargaron en la memoria durante ese intervalo de tiempo y se muestran los posibles conjuntos de datos que provocaron el efecto de "vecino ruidoso".

![Barra que muestra el peor rendimiento en una gran parte](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Una vez que se identifica un intervalo de tiempo problemático (por ejemplo, durante el 30 de enero en la imagen anterior), el administrador de Power BI puede eliminar todos los filtros de los conjuntos de datos y, a continuación, filtrar solo por ese intervalo de tiempo para determinar qué conjuntos de datos se consultaron activamente durante ese intervalo. El conjunto de datos causante del efecto de "vecino ruidoso" es normalmente el conjunto de datos más consultado o el que tiene la duración media de consultas más larga.

Una solución a este problema podría ser la distribución de los conjuntos de datos causantes en diferentes áreas de trabajo con distintas capacidades Premium, o en la capacidad compartida si esta admite el tamaño del conjunto de datos, los requisitos de consumo y los patrones de actualización de datos.

El proceso inverso también puede ser verdadero. El administrador de Power BI puede identificar los momentos en los que el rendimiento de consultas de un conjunto de datos mejora drásticamente y, a continuación, buscar lo que ha desaparecido. Si falta cierta información en ese momento, esto puede ayudar a identificar el problema causante.

## <a name="determining-whether-there-is-enough-memory"></a>Determinar si hay suficiente memoria

Para determinar si hay suficiente memoria para que la capacidad complete sus cargas de trabajo, el administrador de Power BI puede consultar el objeto visual **Porcentajes de memoria consumida** de la pestaña **Conjuntos de datos** de la aplicación. La opción **Todo** (total) representa la memoria que usan los conjuntos de datos que se cargaron en la memoria, independientemente de si estos se consultan o procesan activamente. La memoria **Activa** representa la memoria que usan los conjuntos de datos que se están procesando activamente.

En una capacidad adecuada, el objeto visual será parecido al siguiente, mostrando un intervalo entre la memoria total y la memoria activa:

![Una capacidad adecuada mostrará un intervalo entre la memoria total y la memoria activa](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

En una capacidad que experimenta presión por una cuestión de memoria, el mismo objeto visual muestra claramente cómo convergen la memoria activa y la total, lo que significa que no es posible cargar conjuntos de datos adicionales en la memoria. En este caso, el administrador de Power BI puede hacer clic en **Reinicio de la capacidad** (en **Opciones avanzadas** del área de configuración de la capacidad en el portal de administración). Al reiniciar la capacidad, se vacían todos los conjuntos de datos de la memoria y se permite volver a cargarlos según sea necesario (mediante consultas o actualización de datos).

![Memoria **activa** convergiendo con la memoria **total**](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Determinar si hay suficiente CPU

En general, el uso medio de la CPU de una capacidad debería permanecer por debajo del 80 %. Si se supera este valor, eso significa que la capacidad se está aproximando a un estado de saturación de la CPU.

Los efectos de la saturación de la CPU dan como resultado operaciones que tardan más tiempo del que deberían porque la capacidad tiene que realizar muchos cambios de contexto de la CPU ya que esta intenta procesar todas las operaciones. En una capacidad Premium con un gran número de consultas simultáneas, esto se indica mediante tiempos de espera de consulta elevados. Una consecuencia de estos tiempos de espera de consulta elevados es una capacidad de respuesta más lenta de lo habitual. Para que el administrador de Power BI pueda identificar fácilmente si la CPU está saturada debe observar el objeto visual **Distribuciones del tiempo de espera de consulta por hora**. Los recuentos de picos periódicos de tiempo de espera de consultas indican la posible saturación de la CPU.

![Los recuentos de picos periódicos de tiempo de espera de consultas indican la posible saturación de la CPU.](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

A veces se puede detectar un patrón similar en las operaciones en segundo plano si estas contribuyen a la saturación de la CPU. Un administrador de Power BI puede buscar un pico periódico en las horas de actualización de un conjunto de datos específico, lo que puede indicar una saturación de la CPU en ese momento (probablemente debido a otras actualizaciones de conjuntos de datos en curso o a consultas interactivas). En este ejemplo, la consulta de la vista **Sistema** de la aplicación puede no revelar necesariamente que la CPU está al 100 %. La vista **Sistema** muestra los promedios por hora, pero la CPU puede saturarse durante varios minutos de operaciones intensivas, lo cual aparece como picos en los tiempos de espera.

Hay más matices a la hora de ver el efecto de la saturación de la CPU. Aunque el número de consultas en espera es importante, siempre se producirá un tiempo de espera de estas hasta un cierto grado sin que esto cause una degradación observable del rendimiento. Algunos conjuntos de datos (aquellos con un tiempo medio de consulta más largo que indica complejidad o tamaño) son más propensos a los efectos de la saturación de la CPU que otros. Para identificar fácilmente estos conjuntos de datos, el administrador de Power BI puede buscar cambios en la composición de color de las barras del objeto visual **Distribución por horas del tiempo de espera**. Después de detectar una barra con valores atípicos, el administrador puede buscar los conjuntos de datos que tuvieron tiempos de espera de consulta durante esa hora y observar también el tiempo medio de espera de esas consultas en comparación con la duración media de una consulta. Cuando estas dos métricas son de la misma magnitud y la carga de trabajo de consulta del conjunto de datos no es trivial, es probable que una CPU insuficiente afecte al conjunto de datos.

Este efecto puede ser especialmente visible cuando un conjunto de datos se utiliza en ráfagas cortas de consultas de alta frecuencia por parte de varios usuarios (por ejemplo, en una sesión de formación), lo que provocará una saturación de la CPU durante cada ráfaga. En este caso, se pueden experimentar unos tiempos de espera de consultas significativos en este conjunto de datos y esto también puede afectar a otros conjuntos de datos de la capacidad (efecto de "vecino ruidoso").

En algunos casos, los administradores de Power BI pueden solicitar que los propietarios de los conjuntos de datos creen una carga de trabajo de consultas menos volátil mediante la creación de un panel (que realiza consultas periódicas con cualquier actualización del conjunto de datos de los iconos en caché) en lugar de un informe. Esto puede ayudar a evitar picos cuando se carga el panel. Esta solución no siempre es posible para determinados requisitos empresariales pero puede ser una manera eficaz de evitar la saturación de la CPU sin realizar cambios en el conjunto de datos.

## <a name="acknowledgements"></a>Agradecimientos

Este artículo es obra de Peter Myers, MVP de plataforma de datos y experto independiente de BI con [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Supervisión de capacidades Premium con la aplicación](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Supervisión de capacidades en el portal de administración](service-admin-premium-monitor-portal.md)   

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

||||||