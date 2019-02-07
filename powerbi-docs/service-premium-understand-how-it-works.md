---
title: Optimización y uso de la memoria con capacidad Power BI Premium
description: Obtenga información sobre la optimización y la administración de memoria con capacidad Power BI Premium.
ms.date: 02/05/2019
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-admin
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e31f67d978471f4dcc6472860fc5f8315212e563
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794868"
---
# <a name="microsoft-power-bi-premium-capacity-resource-management-and-optimization"></a>Optimización y administración de recursos de capacidad de Microsoft Power BI Premium

Este artículo describe cómo Power BI Premium administra los recursos; el artículo también proporciona ejemplos y sugerencias para solucionar problemas. Para leer una introducción, consulte [¿Qué es Power BI Premium?](service-premium.md).

## <a name="premium-capacity-memory-management"></a>Administración de memoria con capacidad Premium

 La memoria con capacidad Premium se usa de la siguiente forma:

* Los conjuntos de datos que se cargan en memoria
* Actualización del conjunto de datos (programada y a petición)
* Cargas de trabajo que admite la capacidad
* Consultas de informe

Cuando se emite una solicitud en un conjunto de datos publicado en la capacidad, ese conjunto de datos se carga en memoria desde el almacenamiento persistente (esto se denomina carga de la imagen). Mantener el conjunto de datos cargado en la memoria ayuda a responder con rapidez a las consultas futuras a este conjunto de datos. Además de la memoria necesaria para mantener el conjunto de datos cargado en la memoria, las consultas de informes y las actualizaciones del conjunto de datos consumen memoria adicional.

### <a name="dataset-memory-estimation"></a>Estimación de la memoria del conjunto de datos

Al intentar cargar un conjunto de datos en la memoria, Power BI calcula la cantidad de memoria que el conjunto de datos necesitará para completar el comando solicitado. Los conjuntos de datos en memoria tienden a tener un tamaño más grande que cuando se almacenan en un disco. Durante la actualización de un conjunto de datos, Power BI requiere al menos el doble de la cantidad de memoria que resulta necesaria cuando el conjunto de datos está inactivo.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Sobreutilización de capacidad, expulsión y recarga de conjuntos de datos

Power BI Premium ofrece la ventaja de poder *sobreutilizar* la capacidad. Por ejemplo, puede publicar más conjuntos de datos de los que acepta la capacidad. Si los conjuntos de datos publicados necesitan más memoria de la que está disponible en la capacidad, algunos de los conjuntos de datos se almacenan por separado en un almacenamiento persistente. El almacenamiento persistente forma parte del almacenamiento de 100 TB asociado a cada una de sus capacidades.

En este caso, ¿qué conjuntos de datos permanecen en la memoria y qué ocurre al resto de conjuntos de datos? Como se describió anteriormente, cuando se emite una solicitud en un conjunto de datos, se carga en memoria (carga de la imagen). La solicitud podría ser una operación de actualización o una consulta de informe. Pero, dado que puede sobreutilizar su capacidad, la capacidad también podría sufrir la presión de la memoria. Cuando una capacidad sufre la presión de la memoria, el nodo *expulsa* uno o varios conjuntos de datos de la memoria. Los conjuntos de datos que están inactivos (sin ninguna operación de consulta o actualización ejecutándose actualmente) se expulsan primero. A continuación, el orden de expulsión se basa en una medida de tipo LRU (el menos usado recientemente). Si se emiten comandos nuevos en el conjunto de datos expulsado, el servicio intenta volver a cargar el conjunto de datos en la memoria, con la posible expulsión de otros conjuntos de datos. Este comportamiento permite un uso más eficaz, al permitir que la capacidad admita muchos más conjuntos de datos de los que la memoria puede contener.

Cargar un conjunto de datos en memoria es una operación bastante costosa. Dependiendo del tamaño del conjunto de datos, esta operación puede durar desde un par de segundos para los conjuntos de datos pequeños hasta decenas de segundos o incluso minutos para conjuntos de datos grandes, como conjuntos de datos de 10 GB aproximadamente. La capacidad Premium intenta minimizar el número de veces que será necesario cargar la capacidad al mantener los conjuntos de datos menos usados recientemente en la memoria durante el máximo tiempo posible. Si se necesita memoria adicional, será necesario expulsar algunos conjuntos de datos, y el sistema intentará elegir el que menos repercuta en la experiencia del usuario. Si se necesita memoria adicional, será necesario expulsar algunos conjuntos de datos, y el sistema intentará elegir el que menos repercuta en la experiencia del usuario. Por ejemplo, el sistema evitará expulsar los conjuntos de datos que se han usado activamente dentro de los últimos minutos. Estos conjuntos de datos suelen consultarse muy pronto.

El proceso de expulsión en sí es una operación rápida. Si el conjunto de datos no se usa de forma activa en el momento de la expulsión, el usuario no podrá determinar con precisión la repercusión de la expulsión. Sin embargo, si hay demasiados conjuntos de datos activos al mismo tiempo y no hay suficiente memoria para almacenarlos, se pueden producir muchas expulsiones. Un exceso de conjuntos de datos activos puede ocasionar una situación de "hiperpaginación", en la que los conjuntos de datos se expulsan constantemente y se vuelven a cargar, y los usuarios podrían observar una caída importante de los tiempos de respuesta y del rendimiento.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Competición entre el requisito de memoria para actualizaciones de conjuntos de datos y el requisito de memoria para conjuntos de datos activos

Los conjuntos de datos se pueden actualizar de forma programada o a petición de los usuarios. Tal como se ha descrito anteriormente, la memoria necesaria para las actualizaciones completas ocupa al menos el doble de la memoria que los conjuntos de datos cargados e inactivos. Antes de que se inicie la actualización, se estima el requisito de memoria para la actualización. Si el requisito de memoria total es mayor que la memoria disponible en la capacidad, se expulsan algunos conjuntos de datos. Nuevamente, la expulsión se basa en LRU.

Si la memoria necesaria no está disponible a pesar de la expulsión, la actualización se pone en cola para reintentos posteriores. El servicio ejecuta los reintentos hasta conseguirlo y, después, se inicia una nueva acción de actualización.

Si se emite una consulta interactiva a cualquier conjunto de datos en la capacidad y no hay suficiente memoria disponible debido a una actualización en curso, dicha solicitud genera un error y el usuario debe volver a intentarla.

### <a name="workloads"></a>Cargas de trabajo

De forma predeterminada, las funcionalidades de **Power BI Premium** y **Power BI Embedded** admiten solo la carga de trabajo asociada con la ejecución de consultas de Power BI en la nube. Ahora ofrecemos compatibilidad con versiones preliminares para dos cargas de trabajo adicionales: **Informes paginados** y **flujos de datos**. Si está habilitada, estas cargas de trabajo pueden afectar al uso de memoria en la capacidad. Para más información, vea [Configuración de cargas de trabajo](service-admin-premium-manage.md#configure-workloads).

## <a name="cpu-resource-management-in-premium-capacity"></a>Administración de recursos de CPU en la capacidad Premium

Hay dos consumidores principales de recursos de CPU:

* Consultas de informes
* Actualización (procesamiento)

### <a name="queries-from-reports"></a>Consultas de informes

Las consultas de informes consumen recursos de CPU de su capacidad. Los informes con consultas ineficaces o demasiados usuarios simultáneos pueden consumir una gran cantidad de recursos de CPU. La capacidad existente puede no ser suficiente para controlar la carga.

### <a name="refresh-parallelization-policy"></a>Actualización de la directiva de paralelización

La memoria no es el único recurso que puede restringir la actualización de los conjuntos de datos. El número de núcleos virtuales de un servidor también puede ser un factor. Dado que cada operación de actualización requiere un número determinado de núcleos virtuales, hay un límite en cuanto a cuántas actualizaciones se pueden ejecutar en paralelo. En la tabla siguiente se detalla el límite por SKU. Las actualizaciones adicionales que van más allá de estos límites se ponen en cola.

 | SKU | Núcleos virtuales de back-end | Paralelismo de actualización de modelo |
 | --- | --- | --- |
 | A1  | 0,5  | 1  |
 | A2  | 1  | 2  |
 | A3  | 2  | 3  |
 | A4  | 4  | 6  |
 | A5  | 8  | 12  |
 | A6  | 16  | 24  |
 | EM1  | 0,5  | 1  |
 | EM2  | 1  | 2  |
 | EM3  | 2  | 3  |
 | P1  | 4  | 6  |
 | P2  | 8  | 12  |
 | P3  | 16  | 24  |
 | P4  | 32  | 48  |
 | P5  | 64  | 96  |

 > [!TIP]
> Si las actualizaciones sufren retrasos, compruebe el número de actualizaciones paralelas que la capacidad admite.

## <a name="example-scenarios"></a>Escenarios de ejemplo

A continuación se describen algunos escenarios comunes y las acciones realizadas por el servicio:

**Veinte actualizaciones programadas que se envían todas al mismo tiempo**. Power BI intenta iniciar las primeras *x* actualizaciones al mismo tiempo. El valor de *x* lo determina la directiva de paralelización de actualizaciones de dicha SKU. Si Power BI no logra obtener la suficiente memoria al expulsar conjuntos de datos inactivos (conjuntos de datos no usados recientemente), no todas las *x* actualizaciones se podrán iniciar al mismo tiempo. Todas las actualizaciones que no se puedan iniciar, se pondrán en cola hasta que sea posible.

**Dos actualizaciones en ejecución al mismo tiempo pero solo hay suficiente memoria para completar una**. Se inicia solo la que se puede completar. La otra se vuelve a intentar más tarde.

**Un gran número de conjuntos de datos consultados mientras se está actualizando varios conjuntos de datos**. Si no hay suficiente memoria disponible, Power BI intenta detener las actualizaciones activas para dar prioridad a las consultas interactivas. Esto reduce el rendimiento de la actualización.

**El conjunto de datos necesita mucha más memoria para actualizarse en el tamaño de capacidad actual**. La actualización generará un error. No se realiza ningún intento para obtener más memoria mediante expulsiones.

**Actualización de un único conjunto de datos que tiene un pico elevado en memoria**. Si el pico es más alto que la cantidad de memoria que se puede obtener con la expulsión de los conjuntos de datos inactivos, la actualización se vuelve a intentar más tarde hasta que haya suficiente memoria para controlar el pico.

**La consulta se ejecuta en un conjunto de datos que no puede obtener suficiente memoria con la expulsión de todas las actualizaciones y los conjuntos de datos inactivos**. Dichas consultas generan errores. Para estos tipos de requisitos de carga de trabajo, se debe adquirir más capacidad.

## <a name="troubleshooting-and-testing"></a>Solución de problemas y pruebas

Si los informes son lentos o no responden, empiece por probar solo un usuario en el informe. Después, empiece a aumentar la carga de usuarios simultáneos para conocer el límite. En muchos casos, la optimización de las consultas DAX puede cambiar drásticamente el rendimiento de los informes. La optimización de las consultas también aumenta el número de usuarios simultáneos admitidos por la capacidad. [Supervise la capacidad](service-admin-premium-monitor-capacity.md) para identificar posibles problemas de rendimiento.

Use la capacidad de Power BI Embedded en Azure para probar diferentes SKU y determinar la mejor SKU Premium para la carga de trabajo esperada. La SKU A4 de Power BI Embedded es igual a P1, A5 = P2 y A6 = P3. En Azure, puede cambiar fácilmente de SKU mediante el escalado y la reducción verticales en Azure Portal. Cuando encuentre la SKU que se adapte mejor a su carga de trabajo y realice las pruebas pertinentes, puede eliminar la SKU.

En algunos casos, abrir un archivo de Power BI Desktop (.pbix) del modelo en el equipo y comprobar la memoria y el consumo de CPU dice mucho sobre el problema. Esto no es útil para los modelos muy grandes, pero para algunos modelos más pequeños, pruebe a abrir, actualizar y consultar el modelo del equipo. Compruebe el tamaño del modelo, la memoria y la CPU que se consumen al abrir el modelo. Intente actualizar y consultar. Use el administrador de tareas para comprobar el consumo de CPU y memoria del archivo local. A veces, esas métricas en el propio equipo pueden indicar una capacidad Premium menor como P1/P2 puede no ser suficiente para su solución.

## <a name="next-steps"></a>Pasos siguientes

[Administración de la capacidad en Power BI Premium y Power BI Embedded](service-admin-premium-manage.md)