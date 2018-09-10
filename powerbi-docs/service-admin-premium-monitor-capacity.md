---
title: Supervisión de las capacidades de Power BI Premium en su organización
description: Uso del Portal de administración de Power BI y la aplicación Power BI Premium Capacity Metrics
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 08/29/2018
LocalizationGroup: Premium
ms.openlocfilehash: 8e19bc596bef3862dca79ac92ffbd74954a9c756
ms.sourcegitcommit: 6be2c54f2703f307457360baef32aee16f338067
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "43300170"
---
# <a name="monitor-power-bi-premium-capacities-in-your-organization"></a>Supervisión de las capacidades de Power BI Premium en su organización

En este artículo se proporciona información general sobre la supervisión de las métricas de las capacidades de Power BI Premium. La supervisión del uso de la capacidad le permite adoptar un enfoque fundamentado para administrar sus capacidades. 

Puede supervisar la capacidad con la aplicación Premium Capacity Metrics o en el Portal de administración. Aunque en este artículo se tratan las dos opciones, se recomienda la aplicación porque proporciona muchos más detalles.

## <a name="install-the-premium-capacity-metrics-app"></a>Instalación de la aplicación Premium Capacity Metrics

Puede ir directamente a la [aplicación Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) o instalarla como hace con otras aplicaciones en Power BI.

> [!IMPORTANT]
> Para instalar y usar esta aplicación, debe ser un administrador de capacidades y administrar al menos una capacidad. No basta con ser administrador de Power BI. 

1. En Power BI, haga clic en **Aplicaciones**.

    ![Ir a Aplicaciones](media/service-admin-premium-monitor-capacity/apps.png)

2. En el lado derecho, haga clic en **Obtener aplicaciones**.

3. En la categoría **Aplicaciones**, busque **Power BI Premium Capacity Metrics**.

4. Suscríbase para instalar la aplicación.

Ahora que ha instalado la aplicación, puede ver las métricas sobre las capacidades de su organización. Echemos un vistazo a algunas de las métricas principales que están disponibles.

## <a name="use-the-metrics-app"></a>Uso de la aplicación de métricas 
Cuando se abre la aplicación, primero se muestra un panel con un resumen de todas las capacidades para las que tiene derechos de administrador.

![Información general de un informe Premium](media/service-admin-premium-monitor-capacity/app-dashboard.png)

### <a name="filtering"></a>Filtrado

La pestaña **Filters applied to all pages** (Filtros aplicados a todas las páginas) le permite seleccionar una capacidad, un conjunto de datos o un intervalo de fechas dentro de los últimos siete días. Estos filtros aplican la selección a todas las páginas e iconos pertinentes de este informe. Si no se selecciona nada, el informe muestra de forma predeterminada las métricas de la semana pasada de cada capacidad que posea.

![Información general de un informe Premium](media/service-admin-premium-monitor-capacity/premium-report-overview.png)

### <a name="summary-tab"></a>Pestaña Summary (Resumen)

La pestaña **Summary** (Resumen) muestra una vista de la capacidad basada en las entidades, el sistema y los conjuntos de datos.

![Filtros que se aplican a todas las páginas](media/service-admin-premium-monitor-capacity/premium-summary-report.png)

| **Area** (Área) | **Metrics** (Métricas) |
| --- | --- |
| **Entities** (Entidades) | * El número de capacidades que posee.<br> * El número de conjuntos de datos distintos de su capacidad.<br> * El número de áreas de trabajo distintas de su capacidad. |
| **System** (Sistema) | * El uso medio de memoria en GB durante los últimos siete días.<br> * El consumo más alto de memoria en GB en los últimos siete días y la hora local a la que se produjo.<br> * El número de veces que la CPU superó el 80 % de los umbrales en los últimos siete días, dividido en cubos de tres minutos.<br> * La mayoría de las veces que la CPU superó el 80 % en los últimos siete días, dividido en cubos de una hora, y la hora local a la que se produjo.<br> * El número de veces que las conexiones dinámicas y consultas directas superaron el 80 % de los umbrales en los últimos siete días, dividido en cubos de tres minutos.<br> * La mayoría de las veces que las conexiones dinámicas o consultas directas superaron el 80 % en los últimos siete días, dividido en cubos de una hora, y la hora local a la que se produjo. |
| **Dataset Workloads** (Cargas de trabajo de conjunto de datos) | * Número total de actualizaciones en los últimos siete días.<br> * Número total de actualizaciones correctas en los últimos siete días.<br> * Número total de actualizaciones con errores en los últimos siete días.<br> * Número total de actualizaciones con error debido a memoria insuficiente.<br> * La duración media de actualización se mide en minutos, el tiempo necesario para completar la operación.<br> * El tiempo de espera medio de actualización se mide en minutos, el retraso medio entre la hora programada y el inicio de la operación.<br> * Número total de consultas ejecutadas en los últimos siete días.<br> * Número total de consultas correctas en los últimos siete días.<br> * Número total de consultas con error en los últimos siete días.<br> * La duración media de consulta se mide en minutos, el tiempo necesario para completar la operación.<br> * Número total de modelos expulsados debido a la presión de memoria. |
|  |  |

### <a name="refreshes-tab"></a>Pestaña Refreshes (Actualizaciones)

La pestaña **Refreshes** (Actualizaciones) muestra las actualizaciones completas, las medidas de éxito, el tiempo de espera de actualización medio/máximo y la duración de actualización media/máxima fragmentados por conjuntos de datos en los últimos siete días. Los dos gráficos inferiores muestran las actualizaciones frente al consumo de memoria en GB y los tiempos de espera medios divididos en cubos de una hora, presentados en la hora local. Los gráficos de barras superiores muestran los cinco conjuntos de datos principales por el tiempo total máximo que se tardó en completar la actualización del conjunto de datos (duración de la actualización) y el tiempo de espera de actualización máximo. Varios picos elevados de tiempo de espera de actualización son indicativos de un alto uso de la capacidad.

![Informe de actualización Premium](media/service-admin-premium-monitor-capacity/premium-refresh-report.png)

### <a name="datasets-tab"></a>Pestaña Conjuntos de datos

La pestaña **Datasets** (Conjunto de datos) muestra los conjuntos de datos completos expulsados debido a la presión de memoria por la hora.

![Informe de conjuntos de datos Premium](media/service-admin-premium-monitor-capacity/premium-datasets-report.png)

### <a name="system-tab"></a>Pestaña System (Sistema)

La pestaña **System** (Sistema) muestra el uso elevado de CPU (número de veces que superó el 80 % de utilización), el uso elevado de conexiones dinámicas y consultas directas y el consumo de memoria.

![Informe del sistema Premium](media/service-admin-premium-monitor-capacity/premium-system-report.png)

## <a name="monitor-power-bi-embedded-capacity"></a>Supervisión de capacidades de Power BI Embedded

También puede usar la aplicación Power BI Premium Capacity Metrics para supervisar las capacidades de *SKU A* en Power BI Embedded. Esas capacidades se mostrarán en el informe siempre y cuando sea administrador de la capacidad. Sin embargo, la actualización del informe producirá un error si no concede determinados permisos a Power BI en sus SKU A:

1. Abra su capacidad en Azure Portal.
1. Haga clic en **Control de acceso (IAM)** y agregue la aplicación "Power BI Premium" al rol de lector. Si no puede encontrar la aplicación por el nombre, también puede agregarla por su identificador de cliente: cb4dc29f 0bf4 402a 8b30 7511498ed654.

    ![Permisos para Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Puede supervisar el uso de capacidades de Power BI Embedded en la aplicación o en Azure Portal, pero no en el Portal de administración de Power BI.

## <a name="basic-monitoring-in-the-admin-portal"></a>Supervisión básica en el Portal de administración

El área **Configuración de la capacidad** del Portal de administración proporciona cuatro medidores que indican las cargas colocadas y los recursos usados por la capacidad durante los últimos siete días. Estos cuatro iconos funcionan en una ventana de tiempo por horas que indica el número de horas en los últimos siete días que la métrica correspondiente estuvo por encima del 80 %. Esta métrica indica una posible degradación de la experiencia del usuario final.

![Uso en 7 días](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrica** | **Descripción** |
| --- | --- |
| CPU |Número de veces que la CPU ha superado el 80 % del uso. |
| Hiperpaginación de memoria |Representa la presión de memoria en los núcleos de back-end. Concretamente, se trata de una métrica que indica cuántas veces se han desalojado los modelos de la memoria debido a la presión que resulta del uso de varios conjuntos de datos. |
| Uso de memoria |Uso medio de memoria representado en gigabytes (GB). |
| DQ/s | Número de veces que el recuento de consultas de DirectQuery y conexiones dinámicas supera el 80 % del límite. <br> * Se limita el número total de consultas DirectQuery y consultas de conexión dinámica por segundo.* Los límites son 30/s para P1, 60/s para P2 y 120/s para P3. * Las consultas de DirectQuery y las de conexión dinámica son acumulativas en las limitaciones anteriores. Por ejemplo, si tiene 15 consultas DirectQuery y 15 conexiones dinámicas en un segundo, habrá alcanzado el límite.<br>* Esto se aplica igualmente a las conexiones en la nube y a las locales. |
|  |  |

Las métricas reflejan el uso durante la semana pasada.  Si quisiera obtener una vista más detallada de las métricas, no hay problema: solo tiene que hacer clic en cualquiera de los iconos de resumen.  Esto le llevará a gráficos detallados relativos a cada métrica de la capacidad Premium. El siguiente gráfico muestra los detalles de la métrica de CPU.

![Gráfico de uso detallado: CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Estos gráficos se resumen hora a hora durante la última semana, y sirven para aislar eventos concretos relacionados con el rendimiento que han tenido lugar en la capacidad Premium.

Los datos subyacentes de cualquiera de las métricas se pueden exportar también a un archivo csv.  Esta exportación le proporcionará información detallada en intervalos de tres minutos de cada día de la semana pasada.

## <a name="next-steps"></a>Pasos siguientes

Ahora que sabe cómo supervisar las capacidades de Power BI Premium, aprenda más sobre las capacidades de optimización.

> [!div class="nextstepaction"]
> [Optimización y administración de recursos con capacidad Power BI Premium](service-premium-understand-how-it-works.md)
