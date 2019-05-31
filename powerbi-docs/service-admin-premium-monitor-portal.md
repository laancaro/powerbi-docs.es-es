---
title: Supervisión de las capacidades de Power BI Premium mediante el portal de administración
description: Use el portal de administración de Power BI para supervisar las capacidades Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564888"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Supervisión de capacidades en el portal de administración

El **mantenimiento** pestaña en el **la configuración de capacidad** área en el portal de administración proporciona un resumen acerca de las cargas de trabajo habilitados y la capacidad de métricas.  

![Ficha de estado de capacidad en el portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Si tiene métricas más completas, use la [métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md) app. La aplicación proporciona exploración en profundidad y filtrado, y las métricas más detalladas de casi todos los aspectos que afectan al rendimiento de capacidad. Para obtener más información, consulte [las capacidades de supervisión Premium con la aplicación](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Métricas del sistema

En el **mantenimiento** pestaña, en el nivel más alto, uso de CPU y uso de memoria proporcionan una vista rápida de las métricas más importantes de la capacidad. Estas métricas son acumulativas, incluidos todos habilitados de cargas de trabajo para la capacidad.

| **Métrica** | **Descripción** |
| --- | --- |
| USO DE CPU | Uso promedio de CPU, como un porcentaje del total de CPU disponible. |
| USO DE MEMORIA | Promedio de uso de memoria en gigabytes (GB).|

## <a name="workload-metrics"></a>Métricas de carga de trabajo

Para cada carga de trabajo habilitada para la capacidad. Se muestran el uso de CPU y uso de memoria.

| **Métrica** | **Descripción** |
| --- | --- |
| USO DE CPU | Uso promedio de CPU, como un porcentaje del total de CPU disponible. |
| USO DE MEMORIA | Promedio de uso de memoria en gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Métricas de carga de trabajo detallado

Cada carga de trabajo tiene métricas adicionales. El tipo de métricas que se muestran dependen de la carga de trabajo. Para ver métricas detalladas de las cargas de trabajo, haga clic en la expansión (flecha hacia abajo).

![Expanda el estado de carga de trabajo](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Flujos de datos

##### <a name="dataflow-operations"></a>Operaciones de flujo de datos

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento total | número total de actualizaciones de cada flujo de datos. |
| Recuento de casos completados correctamente | Actualizaciones correctas totales para cada flujo de datos.|
| Duración promedio (min) | duración media de la actualización del flujo de datos, en minutos. |
| Duración máxima (min) | duración de la actualización de ejecución más larga del flujo de datos, en minutos. |
| Tiempo promedio de espera (min) | retraso medio entre la hora programada y el inicio de una actualización del flujo de datos, en minutos. |
| Tiempo de espera máximo (minutos) | tiempo de espera máximo del flujo de datos, en minutos.  |

#### <a name="datasets"></a>Conjuntos de datos

##### <a name="refresh"></a>Actualizar

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento total | actualizaciones totales de cada conjunto de datos. |
| Recuento de casos completados correctamente | Actualizaciones correctas totales para cada conjunto de datos. |
| Recuento de errores | Total de actualizaciones con error para cada conjunto de datos. |
| Tasa de éxito  | Número de actualizaciones correcta dividido entre las actualizaciones total para medir. Confiabilidad. |
| Duración promedio (min) | duración media de la actualización del conjunto de datos, en minutos.  |
| Duración máxima (min) | duración de la actualización de ejecución más larga del conjunto de datos, en minutos. |
| Tiempo promedio de espera (min) | el retraso medio entre la hora programada y el inicio de una actualización del conjunto de datos, en minutos. |
| Tiempo de espera máximo (minutos) | tiempo de espera máximo del conjunto de datos, en minutos. |

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
| Número de modelo | El número total de expulsiones de conjunto de datos para esta capacidad. Cuando una funcionalidad sufre la presión de la memoria, el nodo expulsa uno o varios conjuntos de datos de la memoria. Los conjuntos de datos que están inactivos (sin ninguna operación de consulta o actualización ejecutándose actualmente) se expulsan primero. A continuación, el orden de expulsión se basa en una medida de tipo LRU (el menos usado recientemente). |

#### <a name="paginated-reports"></a>Informes paginados

##### <a name="report-execution"></a>Ejecución de informes

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento de ejecuciones  | El número de veces que se ejecutó el informe y ver los usuarios.|

##### <a name="report-usage"></a>Uso de informes

| **Métrica** | **Descripción** |
| --- | --- |
| Recuento de casos completados correctamente | El número de veces que se visualiza el informe por un usuario. |
| Recuento de errores |El número de veces que se visualiza el informe por un usuario.|
| Recuento de filas |número de filas de datos que hay en el informe. |
| Duración de recuperación de datos (ms) |cantidad media de tiempo que se tarda en recuperar los datos del informe, en milisegundos. Las duraciones largas pueden indicar consultas lentas u otros problemas del origen de datos.  |
| Duración del procesamiento (ms) |cantidad media de tiempo que se tarda en procesar los datos de un informe, en milisegundos. |
| Duración de representación (ms) |cantidad media de tiempo que se tarda en representar un informe en el explorador, en milisegundos. |

> [!NOTE]
> Métricas detalladas para la **AI** carga de trabajo no están disponibles.

## <a name="next-steps"></a>Pasos siguientes

Ahora que sabe cómo supervisar las capacidades de Power BI Premium, aprenda más sobre las capacidades de optimización.

> [!div class="nextstepaction"]
> [Optimizar las capacidades de Power BI Premium](service-premium-capacity-optimize.md)
