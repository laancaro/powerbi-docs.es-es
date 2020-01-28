---
title: Aplicación Métricas de Power BI Premium
description: Aprenda a usar la aplicación Métricas de Power BI Premium para administrar y solucionar los problemas de capacidad Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/19/2019
LocalizationGroup: Premium
ms.openlocfilehash: b7a45309c3bfad27cc3b26990ee148a9e44b8998
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2020
ms.locfileid: "75927123"
---
# <a name="power-bi-premium-metrics-app"></a>Aplicación Métricas de Power BI Premium

Puede usar la **aplicación Métricas de Power BI Premium** para administrar el estado y la capacidad de su suscripción de Power BI Premium. Los administradores usan la página **Capacity health center** (Centro de mantenimiento de la capacidad) de la aplicación para ver e interactuar con los indicadores que supervisan el estado de su capacidad Premium. La aplicación Métricas consta de la página de aterrizaje denominada **Capacity Health Center** (Centro de mantenimiento de la capacidad), que muestra información detallada sobre tres métricas importantes:

* Memoria activa
* Esperas de consulta
* Tiempos de espera de actualización

![Aplicación Métricas de Power BI Premium](media/service-premium-metrics-app/premium-metrics-app-00.png)

En las secciones siguientes se describe de forma detallada la página de aterrizaje y las páginas del informe de tres métricas. 

## <a name="premium-capacity-health-center"></a>Centro de mantenimiento de la capacidad Premium

Al abrir la **aplicación Métricas de Power BI Premium**, aparece **Capacity health center** (Centro de mantenimiento de la capacidad), que proporciona información general sobre el mantenimiento de la capacidad de Power BI Premium.

![Centro de mantenimiento de la capacidad de la aplicación Métricas de la versión Premium](media/service-premium-metrics-app/premium-metrics-app-01.png)

En la página de aterrizaje, puede seleccionar la capacidad de Power BI Premium que quiere ver, en caso de que la organización tenga varias suscripciones Premium. Para ver una capacidad Premium, seleccione la lista desplegable situada cerca de la parte superior de la página llamada **Select a capacity to see its metrics** (Seleccionar una capacidad para ver sus métricas).

Los tres KPI muestran el estado actual de la capacidad Premium seleccionada, en función de la configuración aplicada a cada uno de los tres KPI. 

Para ver detalles específicos de cada KPI, seleccione el botón **Explore** (Explorar) en la parte inferior del objeto visual de cada KPI. En las secciones siguientes se describe cada KPI y los detalles que se proporcionan en su página.

## <a name="the-active-memory-metric"></a>La métrica de memoria activa

La métrica de **memoria activa** forma parte de la categoría de *planeamiento de capacidad*, que es un buen indicador de estado para evaluar el consumo de recursos para el uso de la capacidad, de modo que pueda ajustarla según sea necesario para planear su escala. 

![KPI de memoria activa](media/service-premium-metrics-app/premium-metrics-app-02.png)

La **memoria activa** es la memoria usada para procesar los conjuntos de datos que se utilizan actualmente y que, por tanto, no se desalojarán cuando se necesite memoria. La métrica de memoria activa indica si la capacidad puede administrar carga adicional o si carga actual de la capacidad ya está cerca o ha superado la capacidad. La memoria activa consumida actualmente significa que hay menos memoria disponible para admitir actualizaciones y consultas adicionales. 

El KPI de **memoria activa** mide el número de veces que la memoria activa de la capacidad ha superado el umbral del 70 % cincuenta veces (el marcador se establece en el 30 % de los últimos siete días), lo que indica que la capacidad se está aproximando a un punto en el que los usuarios pueden empezar a observar problemas de rendimiento con las consultas.

El objeto visual de medidor mostrado en esta sección revela que, en los últimos siete días desde el momento en que se actualizó el informe por última vez, la capacidad ha superado el umbral del 70 % cuatro veces, dividido por depósitos por hora. El valor máximo del medidor, 168, representa los últimos siete días, en horas.

Para más información sobre el KPI de memoria activa, haga clic en el botón **Explore** (Explorar) para ver una página del informe que proporciona visualizaciones específicas de sus métricas detalladas, junto con una guía de solución de problemas que se muestra en la columna derecha de la página. 

Se han explicado dos escenarios, que puede mostrar en la página del informe si selecciona **Scenario 1** (Escenario 1) o **Scenario 2** (Escenario 2) en la página. 

![Página de detalles de la memoria activa](media/service-premium-metrics-app/premium-metrics-app-03.png)

Las guías de solución de problemas, asociadas a cada escenario, proporcionan explicaciones detalladas sobre lo que significan las métricas, de modo que pueda comprender mejor el estado de la capacidad y lo que se puede hacer para mitigar los problemas. 

Estos dos escenarios se describen en las secciones siguientes.

### <a name="scenario-one---current-load-is-too-high"></a>Escenario uno: carga actual demasiado alta 

Para determinar si hay suficiente memoria para que la capacidad finalice sus cargas de trabajo, consulte el primer objeto visual de la página: **A: Consumed Memory Percentages** (Porcentajes de memoria consumida), que muestra la memoria consumida por los conjuntos de datos que se procesan activamente y, por tanto, no se pueden desalojar.

El umbral de alarma, que es la línea discontinua roja, marca los incidentes de consumo de memoria del 90 %.

El umbral de advertencia, que es la línea discontinua amarilla, marca los incidentes de consumo de memoria del 70 %. 

La línea discontinua negra indica la línea de tendencia del uso de memoria, en función del uso de memoria de la capacidad actual en el transcurso de la escala de tiempo del gráfico.

Los casos elevados de memoria activa por encima del umbral de alarma (línea discontinua roja) y la línea de tendencia de memoria (línea discontinua negra) indican la presión sobre la capacidad de memoria, lo que podría impedir que se carguen conjuntos de datos adicionales en la memoria durante ese tiempo. 

Cuando observe tales casos, debe revisar detenidamente los demás gráficos de la página para determinar mejor qué cantidad de memoria se está consumiendo con frecuencia y por qué y cómo equilibrar u optimizar la carga o, si es necesario, escalar verticalmente la capacidad. 

El segundo objeto visual de la página, **B: Hourly loaded active datasets** (Conjuntos de datos activos cargados por hora), muestra los recuentos del número máximo de conjuntos de datos que se cargaron en la memoria, en depósitos por hora. 

El tercer objeto visual, **C: Why datasets are in memory** (Por qué los conjuntos de datos están en memoria), es una tabla que muestra el conjunto de datos por nombre del área de trabajo, nombre del conjunto de datos y tamaño sin comprimir de los conjuntos de datos en memoria, y explica el motivo por el que se carga en la memoria (por ejemplo, para actualización, consulta o ambas cosas).

#### <a name="diagnosing-scenario-one"></a>Diagnóstico del escenario uno

Un uso elevado de la memoria activa de forma sistemática puede dar lugar a que se fuerce el desalojamiento de los conjuntos de datos que se usan activamente o bien impedir que nuevos conjuntos de datos puedan cargarse. Los siguientes pasos pueden ayudarle a diagnosticar problemas

1. Eche un vistazo al gráfico *A: Consumed memory percentages* (Porcentajes de memoria consumida)

    **a.** Si el gráfico A muestra que el umbral de alarma (90 %) se supera muchas veces o durante horas consecutivas, significa que la memoria de la capacidad se agota con demasiada frecuencia. En el siguiente gráfico, se puede ver que el umbral de advertencia (70 %) se ha superado cuatro veces.

    ![Gráfico a: porcentajes de memoria consumida](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** El gráfico llamado *B: Hourly loaded active datasets* (Conjuntos de datos activos cargados por hora) muestra el número máximo de conjuntos de datos únicos cargados en memoria por depósitos por hora. Al seleccionar una barra en el objeto visual se filtrarán de forma cruzada los conjuntos de datos de razones que hay en el objeto visual en memoria.  

    ![Gráfico b: memoria consumida por hora](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** Consulte la tabla **Why datasets are in memory** (Por qué los conjuntos de datos están en memoria) para ver una lista de los conjuntos de datos que se cargaron en memoria. Ordene por el *tamaño del conjunto de datos (MB)* para resaltar los conjuntos de datos que ocupan más memoria. Las operaciones de capacidad se clasifican como *interactivas* o *en segundo plano*. Las operaciones interactivas incluyen la representación de solicitudes y la respuesta a interacciones del usuario (filtrado, preguntas y respuestas, etc.). Las consultas y actualizaciones totales proporcionan una idea de si se han realizado operaciones interactivas (consultas) numerosas o en segundo plano (actualizaciones) en el conjunto de datos. Es importante comprender que las operaciones interactivas siempre tienen prioridad sobre las operaciones en segundo plano para garantizar la mejor experiencia del usuario posible. Si no hay recursos suficientes, las operaciones en segundo plano se agregan a una cola y se procesan una vez que se liberen recursos. El servicio Power BI puede detener las operaciones en segundo plano (como las actualizaciones del conjunto de datos) en mitad del proceso y agregarlas a una cola.
    
    ![Tabla c: lista de conjuntos de datos](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Soluciones para el escenario uno

Puede realizar los pasos siguientes para solucionar los problemas asociados con el escenario uno:

1. **Escalar verticalmente la capacidad**: el escalado vertical de la capacidad a la siguiente SKU hará que esté disponible el doble de memoria que en la SKU actual, con lo que se evita cualquier presión de memoria que experimente actualmente la capacidad.

2. **Mover los conjuntos de datos a otra capacidad**: si tiene otra capacidad con más memoria disponible, puede trasladar a esta las áreas de trabajo que contengan los conjuntos de datos más grandes.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Escenario dos: la carga futura superará los límites

Para determinar si hay suficiente memoria para que la capacidad pueda completar sus cargas de trabajo, puede consultar el objeto visual **A: Consumed Memory Percentages** (Porcentajes de memoria consumida) en la parte superior de la página, que representa la memoria consumida por los conjuntos de datos que se procesan activamente, por lo que no se pueden desalojar. La línea discontinua negra resalta las tendencias. En una capacidad que experimenta presión sobre la memoria, el mismo objeto visual mostrará claramente la línea de tendencia de memoria (línea discontinua negra) hacia arriba, lo que significa que es posible que se impida que se carguen en memoria conjuntos de datos adicionales en ese momento dado. La línea de tendencia, la línea discontinua negra, muestra la tendencia del crecimiento en función de los siete días de datos. 

![Página de detalles de la memoria activa](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>Diagnóstico del escenario dos

Para diagnosticar el escenario dos, determine si la línea de tendencia muestra una tendencia ascendente hacia los umbrales de advertencia o alarma. 

1. Considere el **gráfico A:**

    ![Gráfico de memoria consumida](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Si el gráfico muestra una pendiente ascendente, significa que el consumo de memoria ha aumentado en los últimos siete días.

    **b.** Asuma el crecimiento actual y prediga cuándo la línea de tendencia cruzará el umbral de advertencia (la línea discontinua amarilla).

    **c.** Siga comprobando la línea de tendencia al menos cada dos días para ver si la tendencia continúa.

#### <a name="remedies-for-scenario-two"></a>Soluciones para el escenario dos

Puede realizar los pasos siguientes para solucionar los problemas asociados con el escenario dos:

1. **Escalar verticalmente la capacidad**: el escalado vertical de la capacidad a la siguiente SKU hará que esté disponible el doble de memoria que en la SKU actual, con lo que se evita cualquier presión de memoria que experimente actualmente la capacidad.

2. **Mover los conjuntos de datos a otra capacidad**: si tiene otra capacidad con más memoria disponible, puede trasladar a esta las áreas de trabajo que contengan los conjuntos de datos más grandes.


## <a name="the-query-waits-metric"></a>Métrica de esperas de consulta

La categoría **Queries** (Consultas) indica si los usuarios pueden experimentar objetos visuales de informe con una respuesta lenta o que podrían dejar de responder. **Query waits** (Tiempos de espera de consulta) es el tiempo que tarda la consulta en iniciar la ejecución desde el momento en que se desencadenó. Este KPI mide si el 25 % o más de las consultas de la capacidad seleccionada están esperando 100 milisegundos o más para ejecutarse. Los tiempos de espera de consulta se producen cuando no hay suficiente CPU disponible para ejecutar todas las consultas pendientes. 

![Medidor de los tiempos de espera de consulta](media/service-premium-metrics-app/premium-metrics-app-09.png)

El medidor de este objeto visual muestra que en los últimos siete días desde el momento en que se actualizó el informe por última vez, el 17,32 % de las consultas esperaron más de 100 milisegundos. 

Para más información sobre el KPI de tiempos de espera de consulta, haga clic en el botón **Explore** (Explorar) para mostrar una página de informe con la visualización de las métricas pertinentes y una guía de solución de problemas en la columna derecha de la página. La guía de solución de problemas tiene dos escenarios, cada uno de los cuales proporciona explicaciones detalladas de la métrica, el estado de la capacidad y lo que se puede hacer para mitigar el problema.

A su vez, en las secciones siguientes se describe cada escenario de tiempos de espera de consulta.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Escenario uno: las consultas de larga duración consumen CPU

En el escenario uno, las consultas de larga ejecución consumen demasiada CPU. 

Puede investigar si el bajo rendimiento del informe se debe a la sobrecarga de la capacidad o al diseño deficiente del conjunto de datos o del informe. Hay varias razones por las que una consulta puede ejecutarse durante un período prolongado, es decir, tarda más de 10 segundos en terminar de ejecutarse. El tamaño y la complejidad del conjunto de datos, así como la complejidad de las consultas, son solo algunos ejemplos de lo que puede provocar una consulta de larga duración. 

En la página del informe, aparecen los siguientes objetos visuales: 

* La tabla superior titulada **A: High wait times** (Tiempos de espera elevados) muestra los conjuntos de datos con consultas que están en espera. 
* **B: Hourly high wait time distributions** (Distribuciones de tiempos de espera elevados por hora) muestra la distribución de los tiempos de espera elevados. 
* El gráfico titulado **C: Hourly long query counts** (Recuentos de consultas largas por hora) muestra el recuento de consultas de larga duración que se ejecutaron dividido entre depósitos por hora.
* El último objeto visual, la tabla **D: Long running queries** (Consultas de larga duración), enumera las consultas de larga duración y sus estadísticas.

![Página de detalles de tiempos de espera de consulta](media/service-premium-metrics-app/premium-metrics-app-10.png)

Hay pasos que puede seguir para diagnosticar y solucionar problemas con los tiempos de espera de consulta. Estos pasos se describen a continuación.

#### <a name="diagnosing-scenario-one"></a>Diagnóstico del escenario uno

En primer lugar, puede determinar si las consultas de larga duración se producen cuando las consultas están en espera. 

![Tabla de tiempos de espera elevados](media/service-premium-metrics-app/premium-metrics-app-11.png)

Observe el **gráfico B**, que muestra el recuento de consultas que están esperando más de 100 ms. Seleccione una de las columnas que muestra un número elevado de esperas.

![Distribución de tiempos de espera elevados](media/service-premium-metrics-app/premium-metrics-app-12.png)

Al hacer clic en una columna con tiempos de espera elevados, el **gráfico C** se filtra para mostrar el recuento de consultas de larga duración que se ejecutaron durante ese tiempo, que se indica en la siguiente imagen:

![Recuentos de consultas largas por hora](media/service-premium-metrics-app/premium-metrics-app-13.png)

Además, el **gráfico D** también se filtra para mostrar las consultas de larga duración durante ese período de tiempo seleccionado.

![Consultas de larga duración](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Soluciones para el escenario uno

Estos son los pasos que puede seguir para solucionar los problemas del escenario uno:

1. **Ejecutar PerfAnalyzer para optimizar los informes y los conjuntos de datos**: el analizador de rendimiento de los informes mostrará el efecto de cada interacción en una página, incluido el tiempo que tarda cada objeto visual en actualizarse y dónde se invierte el tiempo.

2. **Escalar verticalmente la capacidad**: el escalado vertical de la capacidad a la siguiente SKU hará que esté disponible dos veces la cantidad de CPU, con lo que se alivia la presión sobre la CPU que puede provocar que las consultas tarden más en ejecutarse.

3. **Mover los conjuntos de datos a otra capacidad**: si tiene otra capacidad con más CPU disponible, puede trasladar a esta las áreas de trabajo que incluyan los conjuntos de datos que contengan las consultas que están a la espera.

### <a name="scenario-two---too-many-queries"></a>Escenario dos: demasiadas consultas

En el escenario dos se ejecutan demasiadas consultas.

Cuando el número de consultas que se van a ejecutar supera los límites de la capacidad, las consultas se colocan en una cola hasta que hay recursos disponibles para ejecutarlas. Si el tamaño de la cola es demasiado grande, las consultas en esa cola pueden acabar esperando más de 100 milisegundos.

![Escenario 2](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>Diagnóstico del escenario dos

En la **tabla A**, seleccione un conjunto de datos que tenga un porcentaje elevado de tiempo de espera.

![tabla de tiempos de espera elevados](media/service-premium-metrics-app/premium-metrics-app-16.png)

Cuando haya seleccionado un conjunto de datos con un tiempo de espera elevado, el **gráfico B** se filtra para mostrar las distribuciones del tiempo de espera de las consultas de ese conjunto de datos durante los últimos siete días. A continuación, seleccione una de las columnas del **gráfico B**.

![gráfico de distribución de tiempos de espera elevados por hora](media/service-premium-metrics-app/premium-metrics-app-17.png)

Se filtra entonces el **gráfico C** para mostrar la longitud de las consultas en el tiempo seleccionado en el gráfico B.

![longitud de la cola de consultas por hora](media/service-premium-metrics-app/premium-metrics-app-18.png)

Si la longitud de la cola ha superado el umbral de 20, es probable que se retrasen las consultas del conjunto de datos seleccionado, debido a que hay demasiadas consultas que intentan ejecutarse al mismo tiempo.

![Ejecución de la tabla de consultas](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>Soluciones para el escenario dos

Puede realizar los pasos siguientes para solucionar los problemas asociados con el escenario dos:

1. **Escalar verticalmente la capacidad**: el escalado vertical de la capacidad a la siguiente SKU hará que esté disponible el doble de memoria que en la SKU actual, con lo que se evita cualquier presión de memoria que experimente actualmente la capacidad.

2. **Mover los conjuntos de datos a otra capacidad**: si tiene otra capacidad con más memoria disponible, puede trasladar a esta las áreas de trabajo que contengan los conjuntos de datos más grandes.


## <a name="the-refresh-waits-metric"></a>Métrica de tiempos de espera de actualización

La métrica de **tiempos de espera de actualización** proporciona información sobre cuándo los usuarios podrían experimentar datos antiguos u obsoletos en los informes. Los **tiempos de espera de actualización** es cuando una actualización determinada de los datos está a la espera de comenzar a ejecutarse, desde el momento en que se desencadenó a petición o se programó para ejecutarse. Este KPI mide si un 10 % o más de las solicitudes de actualización pendientes están esperando 10 minutos o más. La espera suele producirse cuando no hay suficiente memoria o CPU disponibles.

![Medidor de tiempos de espera de actualización](media/service-premium-metrics-app/premium-metrics-app-20.png)

Este medidor muestra que en los últimos siete días desde la última actualización del informe de actualización, el 3,18 % de las actualizaciones han esperado más de 10 minutos. 

Para conocer los detalles del KPI de **tiempos de espera de actualización**, haga clic en el botón **Explore** (Explorar), que presenta una página con métricas y una guía de solución de problemas en la columna derecha de la página del informe. La guía proporciona explicaciones detalladas sobre las métricas de la página y le ayuda a comprender el estado de la capacidad y lo que puede hacer para mitigar cualquier problema.

![Exploración de las métricas de tiempos de espera de actualización](media/service-premium-metrics-app/premium-metrics-app-21.png)

Se han explicado dos escenarios, que puede mostrar en la página del informe si selecciona Scenario 1 (Escenario 1) o Scenario 2 (Escenario 2) en la página. A su vez, en las secciones siguientes se describe cada escenario.

### <a name="scenario-one---not-enough-memory"></a>Escenario uno: no hay suficiente memoria

En el escenario uno, no hay suficiente memoria disponible para cargar el conjunto de datos. Hay dos situaciones que provocan la limitación de una actualización durante condiciones de memoria insuficiente:

1. No hay suficiente memoria para cargar el conjunto de datos.
2. La actualización se canceló debido a una operación de prioridad más alta. 

La prioridad para cargar conjuntos de datos es la siguiente:

1. Consulta interactiva
2. Actualización a petición
3. Actualización programada

Si no hay suficiente memoria para cargar un conjunto de datos para una consulta interactiva, las actualizaciones programadas se detienen y sus conjuntos de datos se descargan hasta que vuelve a haber suficiente memoria. Si no se libera suficiente memoria, las actualizaciones a petición se detienen y sus conjuntos de datos se descargan.

#### <a name="diagnosing-scenario-one"></a>Diagnóstico del escenario uno

Para diagnosticar el escenario uno, determine primero si la limitación se debe a memoria insuficiente. Para ello, siga estos pasos:

1.  Haga clic en el conjunto de datos que le interese de la **tabla A** para seleccionarlo: 

    ![Tabla A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Cuando se selecciona un conjunto de datos de la **tabla A**, el **gráfico B** se filtra para mostrar cuándo se produjo la espera.

    ![Gráfico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. Se filtra entonces el **gráfico C** para mostrar cualquier limitación, que se explica en el paso siguiente. 

2. Examine los resultados del **gráfico C** ahora filtrado. Si el gráfico muestra que se ha producido una limitación de memoria insuficiente en el momento en que el conjunto de datos estaba esperando, entonces la espera se debía a condiciones de memoria insuficiente.

    ![Gráfico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Por último, compruebe el **gráfico D**, que muestra los tipos de actualizaciones que se han producido, programadas frente a petición. Cualquier actualización a petición que se produzca al mismo tiempo podría ser la causa de la limitación.

    ![Gráfico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Soluciones para el escenario uno

Puede realizar los pasos siguientes para solucionar los problemas asociados con el escenario uno:

1. **Escalar verticalmente la capacidad**: el escalado vertical de la capacidad a la siguiente SKU hará que esté disponible el doble de la cantidad de memoria que tiene la SKU actual, con lo que se alivia la presión sobre la CPU y memoria que experimente actualmente la capacidad.

2. **Mover los conjuntos de datos a otra capacidad**: si los tiempos de espera se deben a la presión sobre la memoria y tiene otra capacidad con más memoria disponible, puede trasladar a esta las áreas de trabajo que contengan los conjuntos de datos que están esperando.

3. **Distribuir las actualizaciones programadas**: distribuir las actualizaciones le ayudará a evitar que demasiadas actualizaciones se intenten ejecutar a la vez.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Escenario dos: no hay suficiente CPU para la actualización

En el escenario dos, no hay suficiente CPU disponible para llevar a cabo la actualización. 

En el caso de las capacidades dedicadas, Power BI limita el número de actualizaciones que pueden producirse al mismo tiempo. Este número es igual al número de núcleos de back-end x 1,5. Por ejemplo, una capacidad dedicada P1, que tenga cuatro núcleos de back-end, puede ejecutar 6 actualizaciones a la vez. Una vez alcanzado el número máximo de actualizaciones simultáneas, otras actualizaciones esperarán hasta que finalice una actualización que se esté ejecutando.

![Escenario dos para la actualización](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>Diagnóstico del escenario dos

Para diagnosticar el escenario dos, determine primero si la limitación se debe a que se llega a la simultaneidad máxima de las actualizaciones. Para ello, siga estos pasos:

1.  Haga clic en el conjunto de datos que le interese de la **tabla A** para seleccionarlo: 

    ![Tabla A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Cuando se selecciona un conjunto de datos de la **tabla A**, el **gráfico B** se filtra para mostrar cuándo se produjo la espera.

    ![Gráfico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. Se filtra entonces el **gráfico C** para mostrar cualquier limitación, que se explica en el paso siguiente. 

2. Examine los resultados del **gráfico C** ahora filtrado. Si el gráfico muestra que la *simultaneidad máxima* se produjo en el momento en que el conjunto de datos estaba esperando, la espera se debió a que no había suficiente CPU disponible.

    ![Gráfico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Por último, compruebe el **gráfico D**, que muestra los tipos de actualizaciones que se han producido, programadas frente a petición. Cualquier actualización a petición que se produzca al mismo tiempo podría ser la causa de la limitación.

    ![Gráfico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>Soluciones para el escenario dos

1. **Escalar verticalmente la capacidad**: el escalado vertical de la capacidad a la siguiente SKU hará que esté disponible el doble de memoria que tiene la SKU actual y dos veces el número de actualizaciones simultáneas que las de la SKU actual, con lo que se alivia la presión sobre la CPU y memoria que experimente actualmente la capacidad.

2. **Mover los conjuntos de datos a otra capacidad**: si los tiempos de espera se deben a que se está alcanzando la simultaneidad máxima y tiene otra capacidad con más simultaneidad disponible, puede trasladar a esta las áreas de trabajo que contengan los conjuntos de datos que están esperando.

3. **Distribuir las actualizaciones programadas**: distribuir las actualizaciones le ayudará a evitar que demasiadas actualizaciones se intenten ejecutar a la vez.



## <a name="next-steps"></a>Pasos siguientes

* [¿Qué es Power BI Premium?](service-premium-what-is.md)
* [Notas de la versión de Power BI Premium](service-premium-release-notes.md)
* [Notas del producto de Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/pbienterprisedeploy)
* [Extended Pro Trial activation](service-extended-pro-trial.md) (Activación de la extensión del período de prueba de Power BI Pro)
* [Preguntas frecuentes sobre Power BI Embedded](developer/embedded-faq.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)