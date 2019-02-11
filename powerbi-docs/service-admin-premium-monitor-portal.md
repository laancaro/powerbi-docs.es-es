---
title: Supervisión de las capacidades de Power BI Premium mediante el portal de administración
description: Use el portal de administración de Power BI para supervisar las capacidades Premium.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 59097c07719e4bb8db188e8a86db377076aea7a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794121"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Supervisión de capacidades en el portal de administración

En este artículo se describe cómo puede usar el área de configuración Capacidad del portal de administración para obtener una vista rápida del rendimiento de la capacidad.  Para obtener las métricas más detalladas sobre la capacidad, se recomienda usar la aplicación [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md).

## <a name="capacity-metrics"></a>Métricas de capacidad

El área **Configuración de la capacidad** del Portal de administración proporciona cuatro medidores que indican las cargas colocadas y los recursos usados por la capacidad durante los últimos siete días. Estos cuatro iconos funcionan en una ventana de tiempo por horas que indica el número de horas en los últimos siete días que la métrica correspondiente estuvo por encima del 80 %. Esta métrica indica una posible degradación de la experiencia del usuario final.

![Uso en 7 días](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrica** | **Descripción** |
| --- | --- |
| CPU |Número de veces que la CPU ha superado el 80 % del uso. |
| Hiperpaginación de memoria |Representa la presión de memoria en los núcleos de back-end. Concretamente, se trata de una métrica que indica cuántas veces se han desalojado los modelos de la memoria debido a la presión que resulta del uso de varios conjuntos de datos. |
| Uso de memoria |Uso medio de memoria representado en gigabytes (GB). |
| DQ/s | Número de veces que el recuento de consultas de DirectQuery y conexiones dinámicas supera el 80 % del límite. <br>  El número total de consultas de DirectQuery y de conexión dinámica por segundo es limitado. Los límites son 30/s para P1, 60/s para P2 y 120/s para P3.  Las consultas de DirectQuery y las de conexión dinámica son acumulativas en las limitaciones anteriores. Por ejemplo, si tiene 15 consultas DirectQuery y 15 conexiones dinámicas en un segundo, habrá alcanzado el límite.<br> Esto se aplica igualmente a las conexiones en la nube y a las locales. |
|  |  |

Las métricas reflejan el uso durante la semana pasada.  Si quisiera obtener una vista más detallada de las métricas, no hay problema: solo tiene que hacer clic en cualquiera de los iconos de resumen.  Esto le llevará a gráficos detallados relativos a cada métrica de la capacidad Premium. El siguiente gráfico muestra los detalles de la métrica de CPU.

![Gráfico de uso detallado: CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Estos gráficos se resumen hora a hora durante la última semana, y sirven para aislar eventos concretos relacionados con el rendimiento que han tenido lugar en la capacidad Premium.

Los datos subyacentes de cualquiera de las métricas se pueden exportar también a un archivo csv.  Esta exportación le proporcionará información detallada en intervalos de tres minutos de cada día de la semana pasada.

## <a name="next-steps"></a>Pasos siguientes

Ahora que sabe cómo supervisar las capacidades de Power BI Premium, aprenda más sobre las capacidades de optimización.

> [!div class="nextstepaction"]
> [Optimización y administración de recursos con capacidad Power BI Premium](service-premium-understand-how-it-works.md)
