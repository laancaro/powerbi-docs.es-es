---
title: Supervisión de las capacidades de Power BI Premium mediante el portal de administración
description: Use el portal de administración de Power BI para supervisar las capacidades Premium.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0d1e0da498a7a2c78e86b643b8a86cb87d6d095a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856863"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Supervisión de capacidades en el portal de administración

La pestaña **Estado** del área **Configuración de la capacidad** del portal de administración ofrece un resumen de las métricas sobre la capacidad y las cargas de trabajo habilitadas.  

![Pestaña Health (Estado) de la capacidad en el portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Si necesita métricas más completas, use la aplicación de [métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md). Esta aplicación proporciona exploración en profundidad y filtrado, y las métricas más detalladas para casi todos los aspectos que afectan al rendimiento de la capacidad. Para más información, consulte [Supervisión de capacidades Premium con la aplicación](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Métricas de sistema

En la pestaña **Estado**, en el nivel más alto, el uso de la CPU y el uso de memoria proporcionan una vista rápida de las métricas más importantes de la capacidad. Estas métricas son acumulativas e incluyen todas las cargas de trabajo habilitadas para la capacidad.

| **Métrica** | **Descripción** |
| --- | --- |
| USO DE CPU | Uso promedio de la CPU, como porcentaje del total de CPU disponible. |
| USO DE MEMORIA | Uso promedio de memoria en gigabytes (GB).|

## <a name="workload-metrics"></a>Métricas de carga de trabajo

Para cada carga de trabajo habilitada para la capacidad. Se muestran el uso de la CPU y de la memoria.

| **Métrica** | **Descripción** |
| --- | --- |
| USO DE CPU | Uso promedio de la CPU, como porcentaje del total de CPU disponible. |
| USO DE MEMORIA | Uso promedio de memoria en gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Métricas de carga de trabajo detalladas

Cada carga de trabajo tiene métricas adicionales. El tipo de métricas que se muestra depende de la carga de trabajo. Para ver las métricas detalladas de una carga de trabajo, haga clic en la flecha hacia abajo para expandir.

![Expansión del estado de la carga de trabajo](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Flujos de datos

##### <a name="dataflow-operations"></a>Operaciones de flujo de datos

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento total | número total de actualizaciones de cada flujo de datos. |
| Recuento de casos completados correctamente | Número total de actualizaciones correctas de cada flujo de datos.|
| Duración promedio (min) | duración media de la actualización del flujo de datos, en minutos. |
| Duración máxima (min) | duración de la actualización de ejecución más larga del flujo de datos, en minutos. |
| Tiempo medio de espera (min) | retraso medio entre la hora programada y el inicio de una actualización del flujo de datos, en minutos. |
| Tiempo de espera máximo (min) | tiempo de espera máximo del flujo de datos, en minutos.  |

#### <a name="datasets"></a>Conjuntos de datos

##### <a name="refresh"></a>Actualizar

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento total | actualizaciones totales de cada conjunto de datos. |
| Recuento de casos completados correctamente | Número total de actualizaciones correctas de cada conjunto de datos. |
| Recuento de errores | Número total de actualizaciones con errores de cada conjunto de datos. |
| Tasa de éxito  | Número de actualizaciones correctas dividido entre el número total de actualizaciones a medir. Confiabilidad. |
| Duración promedio (min) | duración media de la actualización del conjunto de datos, en minutos.  |
| Duración máxima (min) | duración de la actualización de ejecución más larga del conjunto de datos, en minutos. |
| Tiempo medio de espera (min) | el retraso medio entre la hora programada y el inicio de una actualización del conjunto de datos, en minutos. |
| Tiempo de espera máximo (min) | tiempo de espera máximo del conjunto de datos, en minutos. |

##### <a name="query"></a>Consulta

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento total | número total de consultas ejecutadas para el conjunto de datos. |
| Duración promedio (ms) |duración media de consulta del conjunto de datos, en milisegundos.|
| Duración máxima (ms) |duración de la consulta de ejecución más larga del conjunto de datos, en milisegundos. |
| Tiempo promedio de espera (ms) |tiempo de espera de consulta promedio del conjunto de datos, en milisegundos. |
| Tiempo de espera máximo (ms) |duración de la consulta con un tiempo de espera más largo en el conjunto de datos, en milisegundos. |

##### <a name="eviction"></a>Expulsión

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento de modelos | El número total de expulsiones del conjunto de datos para esta capacidad. Cuando una funcionalidad sufre la presión de la memoria, el nodo expulsa uno o varios conjuntos de datos de la memoria. Los conjuntos de datos que están inactivos (sin ninguna operación de consulta o actualización ejecutándose actualmente) se expulsan primero. A continuación, el orden de expulsión se basa en una medida de tipo LRU (el menos usado recientemente). |

#### <a name="paginated-reports"></a>Informes paginados

##### <a name="report-execution"></a>Ejecución de informes

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento de ejecuciones  | El número de veces que los usuarios han ejecutado y visualizado el informe.|

##### <a name="report-usage"></a>Uso de informes

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento de casos completados correctamente | El número de veces que un usuario ha visualizado el informe. |
| Recuento de errores |El número de veces que un usuario ha visualizado el informe.|
| Recuento de filas |número de filas de datos que hay en el informe. |
| Duración de la recuperación de datos (ms) |cantidad media de tiempo que se tarda en recuperar los datos del informe, en milisegundos. Las duraciones largas pueden indicar consultas lentas u otros problemas del origen de datos.  |
| Duración del procesamiento (ms) |cantidad media de tiempo que se tarda en procesar los datos de un informe, en milisegundos. |
| Duración de la representación (ms) |cantidad media de tiempo que se tarda en representar un informe en el explorador, en milisegundos. |

> [!NOTE]
> Todavía no están disponibles las métricas detalladas de la carga de trabajo de **IA**.

## <a name="next-steps"></a>Pasos siguientes

Ahora que sabe cómo supervisar las capacidades de Power BI Premium, aprenda más sobre las capacidades de optimización.

> [!div class="nextstepaction"]
> [Optimización de las capacidades de Power BI Premium](service-premium-capacity-optimize.md)
