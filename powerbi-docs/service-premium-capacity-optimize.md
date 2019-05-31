---
title: Optimizar las capacidades de Microsoft Power BI Premium
description: Describe las estrategias de optimización de las capacidades de Power BI Premium.
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
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565325"
---
# <a name="optimizing-premium-capacities"></a>Optimizar las capacidades Premium

Cuando surgen problemas de rendimiento de capacidad Premium, un primer enfoque común es optimizar o ajustar sus soluciones para restaurar los tiempos de respuesta aceptables. El razonamiento que se va a evitar comprar una capacidad Premium adicional a menos que justifica.

Cuando se requiere más capacidad Premium, hay dos opciones descritas en este artículo:

- Escalar verticalmente una capacidad Premium existente
- Agregar una nueva capacidad Premium

Por último, las pruebas enfoques y dimensionar la capacidad Premium concluyen este artículo.

## <a name="best-practices"></a>Procedimientos recomendados

Al intentar obtener el mejor rendimiento y el uso, existen algunos procedimientos recomendados, incluidos:

- Uso de las áreas de trabajo de la aplicación en lugar de áreas de trabajo personales.
- Separar crítico para la empresa y BI de autoservicio (SSBI) en las diferentes capacidades.

  ![Separar crítico para la empresa y BI de autoservicio en las diferentes capacidades](media/service-premium-capacity-optimize/separate-capacities.png)

- Si comparte contenido solo con usuarios de Power BI Pro, no puede haber ninguna necesidad de almacenar el contenido en una capacidad dedicada.
- Usar capacidades dedicadas al intentar para lograr un tiempo de actualización específico o cuando se requieren funciones específicas. Por ejemplo, con grandes conjuntos de datos o informes paginados.

### <a name="addressing-common-questions"></a>Direccionamiento de las preguntas más frecuentes

Optimizar las implementaciones de Power BI Premium es un tema complejo que implica una comprensión de los requisitos de carga de trabajo, los recursos disponibles y su uso real.

Este artículo aborda las siete preguntas comunes de soporte técnico, que describe los posibles problemas y explicaciones y obtener información sobre cómo identificar y solucionarlos problemas.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>¿Por qué es la capacidad lenta y lo puedo hacer?

Hay muchas razones que pueden contribuir a una capacidad Premium lento. Esta pregunta requiere más información para comprender qué se entiende por lento. ¿Son informes tarda en cargarse? ¿O bien, son errores en la carga? ¿Son objetos visuales de informe tarda en cargar o actualizar cuando los usuarios interactúan con el informe? ¿Son actualizados toma más tiempo en completarse de lo esperado, o que haya tenido?

Tras conseguir una descripción del motivo, a continuación, puede empezar a investigar. Las respuestas a las preguntas siguientes seis le ayudará a solucionar más problemas específicos.

### <a name="what-content-is-using-up-my-capacity"></a>¿El contenido que está usando mi capacidad?

Puede usar el **métricas de capacidad de Power BI Premium** aplicación para filtrar por la capacidad y revisar las métricas de rendimiento para el contenido del área de trabajo. Es posible revisar el uso de recursos y las métricas de rendimiento por hora durante los últimos siete días para todo el contenido almacenado en una capacidad Premium. Supervisión suele ser el primer paso para tomar para solucionar el problema una duda general sobre el rendimiento de capacidad Premium.

Las métricas claves para supervisar incluyen:

- Promedio de CPU y el recuento de uso elevado.
- Promedio de memoria y recuento de alta utilización y uso de memoria para los informes paginados, flujos de datos y conjuntos de datos específicos.
- Conjuntos de datos activos cargan en memoria.
- Duración promedio y máximo de consulta.
- Tiempos de espera de la media de las consultas.
- Flujo de datos y el conjunto de datos promedio actualizan veces.

En la aplicación de las métricas de capacidad de Power BI Premium, la memoria activa muestra la cantidad total de memoria que se asigna a un informe que no se puede expulsar porque ha sido en uso en los últimos tres minutos. Un pico alta en el tiempo de espera de actualización podría estar correlacionado con un conjunto de datos grande o activa.

El **Top 5 por promedio de duración** gráfico resalta los cinco primeros conjuntos de datos, informes paginados y flujos de datos consume recursos de capacidad. Contenido en los primeros cinco listas es candidatas para la optimización de investigación y posibles.

### <a name="why-are-reports-slow"></a>¿Por qué informes lenta?

Las siguientes tablas muestran los posibles problemas y maneras de identificar y controlarlos.

#### <a name="insufficient-capacity-resources"></a>Recursos de capacidad suficiente

| Obtener posibles explicaciones | Cómo identificar | Cómo resolver |
| --- | --- | --- |
| Memoria alta totales (modelo no se puede expulsar porque está en uso en los últimos tres minutos).<br><br> Tiempos de espera de los picos alta varias en la consulta.<br><br> Los picos alta varias en la actualización de los tiempos de espera. | Supervisar las métricas de memoria \[ [1](#endnote-1)\]y los recuentos de expulsión \[ [2](#endnote-2)\]. | Reducir el tamaño del modelo, o convertir en el modo DirectQuery. Consulte la [optimización de los modelos](#optimizing-models) sección en este artículo.<br><br> La capacidad de escalado.<br><br> Asignar el contenido a una capacidad diferente. |

#### <a name="inefficient-report-designs"></a>Diseños de informe ineficaz

| Obtener posibles explicaciones | Cómo identificar | Cómo resolver |
| --- | --- | --- |
| Las páginas de informe contienen demasiados objetos visuales (filtrado interactivo puede desencadenar una al menos una consulta por objeto visual).<br><br> Los objetos visuales recuperan más datos que es necesario. | Revise los diseños de informe.<br><br> Entrevistar a los usuarios de informes para entender cómo interactúan con los informes.<br><br> Supervisar las métricas de consulta de conjunto de datos \[ [3](#endnote-3)\]. | Nuevo diseño de informes con menos elementos visuales por página. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Conjunto de datos es lento, especialmente cuando los informes previamente se han realizado correctamente

| Obtener posibles explicaciones | Cómo identificar | Cómo resolver |
| --- | --- | --- |
| Cada vez más grandes volúmenes de datos de importación.<br><br> Lógica de cálculo complejo o ineficiente, incluidos los roles de RLS.<br><br> Modelo no totalmente optimizada.<br><br> (DQ/LC) Latencia de la puerta de enlace.<br><br> Calidad de datos origen consulta tiempos de respuesta bajos. | Revise los diseños de modelo.<br><br> Supervisar los contadores de rendimiento de puerta de enlace. | Consulte la [optimización de los modelos](#optimizing-models) sección en este artículo. |

#### <a name="high-concurrent-report-usage"></a>Uso de informes simultáneas alta

| Obtener posibles explicaciones | Cómo identificar | Cómo resolver |
| --- | --- | --- |
| Tiempos de espera de consulta alta.<br><br> Saturación de la CPU.<br><br> Límites de conexiones de calidad de datos/LC superados. | Supervisar la utilización de CPU \[ [4](#endnote-4)\], tiempos de espera de consulta y la utilización de calidad de datos/LC \[ [5](#endnote-5) \] métricas + duración de las consulta. Si fluctúa, puede indicar problemas de simultaneidad. | La capacidad de escalado vertical, o asignar el contenido a una capacidad diferente.<br><br> Nuevo diseño de informes con menos elementos visuales por página. |

**Notas:**    
<a name="endnote-1"></a>\[1\] promedio de uso de memoria (GB) y el consumo de memoria máximo (GB).   
<a name="endnote-2"></a>\[2\] expulsiones de conjunto de datos.   
<a name="endnote-3"></a>\[3\] las consultas de conjunto de datos, duración de la consulta de conjunto de datos promedio (ms), conjunto de datos esperan recuento y el tiempo de espera promedio del conjunto de datos (ms).   
<a name="endnote-4"></a>\[4\] recuento alto de utilización de CPU y el tiempo de CPU de mayor uso (últimos siete días).   
<a name="endnote-5"></a>\[5\] recuento alto de utilización de calidad de datos/LC y la hora de calidad de datos/LC de utilización más alta (últimos siete días).   

### <a name="why-are-reports-not-loading"></a>¿Por qué son los informes no está cargando?

Cuando no se pudo cargar informes, es un inicio de sesión está seguro de la capacidad no tiene suficiente memoria y es excesiva calentada. Esto puede ocurrir cuando se consultan activamente de todos los modelos cargados y por lo que no se puede expulsar, y cualquier operación de actualización se han pausado o retrasado. El servicio Power BI intentará cargar el conjunto de datos durante 30 segundos y se notifica correctamente al usuario del error con una sugerencia que vuelva a intentarlo.

Actualmente no hay ninguna métrica para supervisar para informe de errores de carga. Puede identificar el potencial para resolver este problema mediante la memoria del sistema de supervisión, específicamente mayor uso y tiempo de utilización más alta. Expulsiones de conjunto de datos alta y tiempo de espera de actualización a largo conjunto de datos podrían sugerir que se está produciendo este problema.

Si esto ocurre muy en ocasiones, esto es posible que no se considera un problema de prioridad. Los usuarios de informes le informa de que el servicio está ocupado y que debe reintentar después de un breve tiempo. Si esto sucede con demasiada frecuencia, el problema puede solucionarse al escalar verticalmente la capacidad Premium o al asignar el contenido a una capacidad diferente.

Los administradores de capacidad (y los administradores de servicios de Power BI) puede supervisar el **errores de consulta** métrica para determinar cuando esto ocurra. También puede reiniciar la capacidad de restablecer todas las operaciones en el caso de sobrecarga del sistema.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>¿Por qué las actualizaciones no se está iniciando en programación?

No se garantiza que las horas de inicio de la actualización programada. Recuerde que el servicio Power BI siempre priorizará operaciones interactivas a través de operaciones en segundo plano. La actualización es una operación en segundo plano que puede producirse cuando se cumplen las dos condiciones:

- No hay memoria suficiente
- No se supera el número de actualizaciones simultáneas admitidas por la capacidad Premium

Cuando no se cumplen las condiciones, la actualización se pone en cola hasta que las condiciones son favorables.

Para una actualización completa, recuerde que se requiere al menos el doble el tamaño de memoria del conjunto de datos actual. Si no hay suficiente memoria disponible, a continuación, la actualización no puede comenzar hasta la expulsión del modelo que se libere memoria; Esto significa retrasos hasta que uno o varios conjuntos de datos pasa a estar inactiva y se pueden expulsar.

Recuerde que el número admitido de las actualizaciones simultáneas máximos se establece en 1,5 veces el back-end núcleos, redondeado hacia arriba.

Una actualización programada se producirá un error cuando no puede comenzar antes del vencimiento comenzar la siguiente actualización programada. Una actualización a petición desencadenada manualmente desde la interfaz de usuario se intentará ejecutar hasta tres veces antes de desistir.

Los administradores de capacidad (y los administradores de servicios de Power BI) puede supervisar el **tiempo promedio de actualización de espera (minutos)** métrica para determinar el intervalo promedio entre la hora programada y el inicio de la operación.

Aunque normalmente no se actualiza una prioridad administrativa, para influir en los datos a la hora, asegúrese de que hay suficiente memoria disponible. Esto puede implicar el aislamiento de conjuntos de datos de las capacidades con suficientes recursos conocidos. También es posible que podrían coordinar los administradores con los propietarios del conjunto de datos para ayudar a fin de escalonar o reducir los tiempos de actualización de datos programada se minimizan los conflictos. Tenga en cuenta que no es posible que un administrador para ver la cola de actualización, o para recuperar las programaciones del conjunto de datos.

### <a name="why-are-refreshes-slow"></a>¿Por qué son las actualizaciones de baja velocidad?

Las actualizaciones pueden ser lento - o percibido lenta (como las direcciones de pregunta común anterior).

Cuando la actualización de hecho es lenta, puede deberse a varias razones:

- Una CPU insuficiente (actualización puede ser muy intensivo de CPU).
- Memoria insuficiente, lo que resulta en pausa la actualización (que requiere la actualización para volver a empezar cuando las condiciones son favorables para reanudarse).
- Capacidad de que no son razones, incluida la capacidad de respuesta del sistema de origen de datos, latencia de red, permisos no válidos o el rendimiento de puerta de enlace.
- Volumen de datos: una buena razón para configurar incremental actualizar, tal como se describe a continuación.

Los administradores de capacidad (y los administradores de servicios de Power BI) puede supervisar el **promedio actualizar duración (minutos)** métrica para determinar un banco de pruebas para la comparación con el tiempo y el **tiempo promedio de actualización de espera (minutos)** las métricas para determinar el intervalo promedio entre promedio de retardo entre la hora programada y el inicio de la operación.

Actualización incremental puede reducir considerablemente la duración de la actualización de datos, especialmente para las tablas del modelo de gran tamaño. Hay cuatro beneficios asociados con la actualización incremental:

- **Las actualizaciones son más rápidas** : solo un subconjunto de una tabla necesita el uso de CPU y memoria de carga, lo que disminuye y el paralelismo puede ser superior al actualizar varias particiones.
- **Las actualizaciones se producen solo cuando sea necesario** -se pueden configurar directivas de actualización Incremental para cargar solo cuando los datos han cambiado.
- **Las actualizaciones son más confiables** -son menos susceptibles a la desconexión de las conexiones de ejecución más cortas a sistemas de origen de datos volátiles.
- **Modelos permanecen recorte** -directivas de actualización Incremental pueden configurarse para quitar automáticamente historial más allá de una ventana deslizante de tiempo.

Para obtener más información, consulte [actualización Incremental en Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>¿Por qué datos actualiza no completan?

Cuando comienza la actualización de datos, pero no se puede completar, puede deberse a varias razones:

- Memoria insuficiente, incluso si hay un único modelo la capacidad Premium, es decir, el tamaño del modelo es muy grande.
- Motivos de capacidad no, incluidos la desconexión del origen de datos del sistema, los permisos no válidos o error de puerta de enlace.

Los administradores de capacidad (y los administradores de servicios de Power BI) puede supervisar el **actualizar errores debido a memoria insuficiente** métrica.

## <a name="optimizing-models"></a>Optimización de los modelos

Diseño del modelo óptimo es crucial para ofrecer una solución eficaz y escalable. Sin embargo, resulta más allá del ámbito de este artículo para proporcionar una explicación completa. En su lugar, esta sección proporciona áreas clave deben tener en cuenta al optimizar los modelos.

### <a name="optimizing-power-bi-hosted-models"></a>Optimización de Power BI hospedados modelos

Optimizar modelos hospedados en una capacidad Premium se puede lograr en las capas de orígenes de datos y el modelo.

Tenga en cuenta las posibilidades de optimización de un modelo de importación:

![Posibilidades de optimización para un modelo de importación](media/service-premium-capacity-optimize/import-model-optimizations.png)

En la capa de origen de datos:

- Orígenes de datos relacionales se pueden optimizar para garantizar la actualización más rápida posible previamente integración de datos, aplicar los índices apropiados, definir las particiones de tabla que se ajusten a los puntos de actualización incremental y materializar los cálculos (en lugar de calcular modelo de tablas y columnas) o agregar lógica de cálculo a las vistas.
- Orígenes de datos no relacionales pueden ser integrados previamente con almacenes relacionales.
- Asegúrese de que las puertas de enlace tienen suficientes recursos, preferiblemente en máquinas dedicadas, con suficiente ancho de banda de red y cerca de los orígenes de datos.

En el nivel de modelo:

- Los diseños de consulta de Power Query pueden minimizar o eliminar transformaciones complejas y especialmente los que la combinación de distintos orígenes de datos (almacenes de datos lograrlo durante su fase de extracción, transformación y carga). Además, se establecen garantizar niveles de privacidad de ese origen de datos adecuado, esto puede evitar la necesidad de Power BI cargar los resultados completos para generar un resultado combinado en todas las consultas.
- La estructura del modelo determina los datos que se va a cargar y tiene un impacto directo en el tamaño del modelo. Se pueden diseñarse para evitar la carga de datos innecesarios mediante la eliminación de columnas, quitar filas (especialmente datos históricos) o mediante la carga de datos resumidos (a costa de la carga de datos detallados). Reducción de tamaño considerable puede lograrse mediante la eliminación de columnas de una cardinalidad alta (especialmente las columnas de texto) que no almacenar o comprimir de forma muy eficaz.
- Rendimiento de consultas de modelo se puede mejorar mediante la configuración de las relaciones de una dirección única a menos que haya un motivo convincente para permitir el filtrado bidireccional. Considere la posibilidad de usar también el [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) función en lugar de filtrado bidireccional.
- Tablas de agregación pueden lograr consultas rápido respuestas mediante la carga previamente los datos resumen de, sin embargo, Esto aumentará el tamaño del modelo y resultado tiempos más largos de actualización. Por lo general, las tablas de agregación se deben reservar para modelos muy grandes o diseños de modelo compuesto.
- Tablas y columnas calculadas, aumentar el tamaño del modelo y dar lugar a tiempos de actualización. Por lo general, se pueden lograr un tamaño menor de almacenamiento y la hora de actualización más rápida cuando los datos se materializan o calculados en el origen de datos. Si esto no es posible, utilizan columnas personalizadas de Power Query puede ofrecer la compresión de almacenamiento mejorado.
- Puede haber oportunidad para optimizar las expresiones de DAX para medidas y las reglas RLS, quizás volver a escribir la lógica para evitar el costosas fórmulas
- Actualización incremental drásticamente puede reducir el tiempo de actualización y conservar memoria y CPU. La actualización incremental también puede configurarse para quitar datos históricos mantener recorte tamaños de modelo.
- Un modelo podría ser rediseñado como dos modelos cuando hay patrones de consulta diferentes y en conflicto. Por ejemplo, algunos informes presentes agregados de alto nivel a través de todos los historial y puede toleran la latencia de 24 horas. Otros informes preocupados por los datos de hoy en día y necesitan acceso granular a las transacciones individuales. En lugar de un único modelo de diseño para satisfacer todos los informes, crear dos modelos optimizados para cada requisito.

Tenga en cuenta las posibilidades de optimización para un modelo DirectQuery. Como el modelo emite las solicitudes de consulta al origen de datos subyacente, optimización del origen de datos es fundamental para la entrega de las consultas de modelo con capacidad de respuesta.

 ![Posibilidades de optimización para un modelo DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

En la capa de origen de datos:

- El origen de datos se puede optimizar para asegurarse de que las consultas más rápido posible integrando previamente los datos (lo cual no es posibles en el nivel de modelo), aplicar los índices apropiados, definir las particiones de tabla, materializar los datos resumidos (con vistas indizadas), y minimizar la cantidad de cálculo. La mejor experiencia se logra al paso a través de consultas necesitan filtrar únicamente y realizar combinaciones internas entre las tablas indizadas o las vistas.
- Asegúrese de que las puertas de enlace tienen suficientes recursos, preferiblemente en máquinas dedicadas, con suficiente ancho de banda de red y cerca del origen de datos.

En el nivel de modelo:

- Consulta de Power Query diseños, preferiblemente, no deben aplicar ninguna transformación - en caso contrario, intenta mantener las transformaciones de absoluta mínimo.
- Rendimiento de consultas de modelo se puede mejorar mediante la configuración de las relaciones de una dirección única a menos que haya un motivo convincente para permitir el filtrado bidireccional. También, las relaciones de modelo deben estar configuradas para que asuman se exige integridad referencial (si este es el caso) y consultas de origen de datos mediante combinaciones internas más eficaces (en lugar de las combinaciones externas) dará como resultado.
- Evite crear columnas personalizadas de consulta de Power Query o una columna calculada de modelo: materializar estas opciones en el origen de datos, siempre que sea posible.
- Puede haber una oportunidad para optimizar las expresiones de DAX para medidas y las reglas RLS, quizás volver a escribir la lógica para evitar el costosas fórmulas

Tenga en cuenta las posibilidades de optimización de un modelo compuesto. Recuerde que un modelo compuesto permite una combinación de importación y DirectQuery tablas.

![Posibilidades de optimización para un modelo compuesto](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Por lo general, la optimización para los modelos de importación y DirectQuery se aplican a las tablas de modelo compuesto que usan estos modos de almacenamiento.
- Normalmente, se esfuerzan por lograr un diseño equilibrado mediante la configuración de las tablas de tipo de dimensión (que representan las entidades empresariales) como tablas de modo y el tipo de hechos de almacenamiento Dual (a menudo las tablas grandes, que representa los hechos operativos) como el modo de almacenamiento DirectQuery. Modo de almacenamiento dual significa que ambos importación y DirectQuery y modos de almacenamiento, esto permite que el servicio Power BI determinar el modo de almacenamiento más eficaz que se utilizará al generar una consulta nativa de paso a través.
- Asegúrese de que las puertas de enlace tengan suficientes recursos, preferiblemente en máquinas dedicadas, con suficiente ancho de banda de red y cerca de los orígenes de datos
- Configurar las tablas de agregaciones como modo de almacenamiento de importación puede ofrecer mejoras de rendimiento de consulta considerable cuando se usa para resumir las tablas de hechos de tipo de modo de almacenamiento DirectQuery. En este caso, aumentará el tamaño del modelo y aumentar el tiempo de actualización de las tablas de agregación y a menudo esto es una exigencia asumible para consultas más rápidas.

### <a name="optimizing-externally-hosted-models"></a>Optimizar externamente hospedado modelos

Muchas de las posibilidades de optimización que se describen en el [optimizar Power BI hospedados modelos](#optimizing-power-bi-hosted-models) sección también se aplica a modelos desarrollados con Azure Analysis Services y SQL Server Analysis Services. Borrar excepciones son ciertas características que no se admiten actualmente, incluidos modelos compuestos y las tablas de agregación.

Una consideración adicional para los conjuntos de datos hospedado externamente es la base de datos de hospedaje en relación con el servicio Power BI. Azure Analysis Services, esto significa crear el recurso de Azure en la misma región que el inquilino de Power BI (región principal). Para SQL Server Analysis Services de la IaaS, esto significa que hospeda la máquina virtual en la misma región y en local, significa garantizar una configuración eficaz de la puerta de enlace.

Por otro lado, puede ser de interés para que tenga en cuenta que las bases de datos de Azure Analysis Services y bases de datos tabulares de SQL Server Analysis Services requieren que sus modelos de cargarse totalmente en memoria y que permanecen allí en todo momento para admitir la consulta. Al igual que el servicio Power BI, debe haber suficiente memoria para la actualización si el modelo debe permanecer en línea durante la actualización. A diferencia del servicio Power BI, no hay ningún concepto modelos vencen automáticamente dentro y fuera de memoria según el uso. Power BI Premium, por lo tanto, ofrece un enfoque más eficaz para maximizar el modelo consultando con menor uso de memoria.

## <a name="capacity-planning"></a>Planificación de capacidad

El tamaño de una capacidad Premium determina su memoria disponible y los recursos del procesador y límites impuestos en la capacidad. El número de las capacidades Premium también es una consideración, como crear Premium varias capacidades pueden ayudar a aislar las cargas de trabajo entre sí. Tenga en cuenta que storage es 100 TB por nodo de capacidad, y esto es probable que sea más que suficiente para cualquier carga de trabajo.

Determinar el tamaño y el número de las capacidades Premium puede resultar complicado, especialmente para la capacidad inicial que cree. El primer paso al ajuste de tamaño de capacidad es comprender la carga de trabajo promedio que representa el uso diario esperado. Es importante entender que no todas las cargas de trabajo son iguales. Por ejemplo, en un extremo de un espectro - 100 usuarios simultáneos tienen acceso a una única página del informe que contiene un solo objeto visual es puede realizar fácilmente. Aún - en el otro extremo del espectro - 100 usuarios simultáneos que tienen acceso a 100 informes diferentes, cada uno con 100 objetos visuales de la página del informe, va a hacer muy distintas demandas de recursos de capacidad.

Los administradores de capacidad, por tanto, debe tener en cuenta muchos factores específicos de su entorno, el contenido y el uso esperado. El objetivo reemplazo es maximizar la utilización de capacidad al tiempo que ofrece tiempos de consultas coherentes, tiempos de espera aceptable y tasas de expulsión. Pueden incluir factores deben tener en cuenta:

- **Las características de datos y del tamaño del modelo** : modelos de importación deben ser totalmente cargados en la memoria para permitir que la consulta o actualización. LC/DQ conjuntos de datos pueden requerir tiempo de procesador significativo y posiblemente importantes de memoria para evaluar medidas complejas o las reglas RLS. Memoria y procesador, rendimiento y tamaño LC/DQ consulta están limitados por el tamaño de la capacidad.
- **Modelos activos simultáneos** -la realización de consultas simultáneas de importación diferentes modelos ofrecerá mejor la capacidad de respuesta y el rendimiento cuando queden en memoria. Debe haber suficiente memoria para hospedar todos los modelos que se consultan con mucha frecuencia, con memoria adicional para permitir su actualización.
- **Actualización del modelo de importación** -el tipo de actualización (completo o incremental), la duración y la complejidad de las consultas de Power Query y la lógica de la tabla o columna calculada pueden afectar en memoria y uso del procesador especialmente. Las actualizaciones simultáneas están limitadas por el tamaño de la capacidad (1,5 x backend núcleos, redondeado al alza).
- **Consultas simultáneas** -pueden dar lugar a muchas consultas simultáneas en informes no responde al procesador o LC/DQ conexiones supera el límite de capacidad. Esto sucede especialmente para las páginas de informes que incluyen muchos objetos visuales.
- **Flujos de datos e informes paginados** -la capacidad puede configurarse para admitir flujos de datos e informes paginados, que requiere un porcentaje máximo configurable de capacidad de memoria. Memoria se asigna dinámicamente a los flujos de datos, pero está asignada estáticamente a los informes paginados.

Además de estos factores, los administradores de capacidad puede crear varias capacidades. Varias capacidades permiten para el aislamiento de las cargas de trabajo y pueden configurarse para asegurarse de que las cargas de trabajo de prioridad tienen garantizados los recursos. Por ejemplo, se pueden crear dos capacidades para separar las cargas de trabajo empresariales críticas de las cargas de trabajo (SSBI) de BI de autoservicio. La capacidad crítico para la empresa puede utilizarse para aislar los modelos corporativos grandes proporcionarles recursos garantizados, con acceso concedido sólo al departamento de TI de creación. La capacidad SSBI puede usarse para hospedar un número creciente de los modelos más pequeños, con acceso concedido a los analistas de negocios. La capacidad SSBI a veces puede experimentar esperas de consulta o actualización tolerables.

Con el tiempo, los administradores de capacidad puede equilibrar las áreas de trabajo en las capacidades de mover contenido entre las áreas de trabajo, o áreas de trabajo entre las capacidades y las capacidades de ajuste de escala hacia arriba o hacia abajo. Por lo general, para una mayor simultaneidad modelos más grandes de host puede escalar verticalmente y escalar horizontalmente.

Recuerde que comprar una licencia proporciona al inquilino con núcleos. La compra de un **P3** suscripción puede utilizarse para crear uno, o hasta cuatro capacidades Premium, es decir, 1 x P3, o 2 x P2 o 4 x P1. Además, antes de la conversión de una capacidad de P2 a una capacidad de P3, se puede prestar atención a dividir los núcleos virtuales para crear dos capacidades de P1.

## <a name="testing-approaches"></a>Enfoques de pruebas

Una vez que se decide el tamaño de la capacidad, las pruebas pueden realizarse mediante la creación de un entorno controlado. Es una opción práctica y económica crear una capacidad de Azure (SKU), teniendo en cuenta que una capacidad de P1 es el mismo tamaño que una capacidad A4, con el P2 y P3 capacidades del mismo tamaño que las capacidades A5 y A6, respectivamente. Capacidades de Azure se pueden crear rápidamente y se facturan por hora. Por lo tanto, una vez completada la prueba, se puede eliminar fácilmente para dejar de acumular los costos.

El contenido de la prueba se puede agregar a las áreas de trabajo creados en la capacidad de Azure y, a continuación, como un único usuario puede ejecutar informes para generar una carga de trabajo realista y representativo de las consultas. Si no hay modelos de importación, también debe realizarse una actualización para cada modelo. Herramientas de supervisión, a continuación, pueden utilizarse para revisar todas las métricas para comprender el uso de recursos.

Es importante que las pruebas son repetibles. Se deben ejecutar las pruebas varias veces y que deben proporcionar aproximadamente el mismo resultado cada vez. Un promedio de estos resultados puede utilizarse para extrapolar y calcular una carga de trabajo en condiciones de producción es true.

Para generar una prueba de esfuerzo, considere la posibilidad de desarrollar una aplicación para simular una carga de trabajo realista de prueba de carga. Los detalles de cómo lograr esto están fuera del ámbito de este artículo. Para obtener información adicional incluido un ejemplo de código, consulte el [carga probar las aplicaciones de Power BI con la prueba de carga de Visual Studio](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) seminario Web.

## <a name="acknowledgements"></a>Confirmaciones

En este artículo se escribió por Peter Myers, MVP de la plataforma de datos y experto en BI independiente con [bit a bit soluciones](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Escenarios de capacidad Premium](service-premium-capacity-scenarios.md)   
  
¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

||||||