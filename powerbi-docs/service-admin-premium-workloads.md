---
title: Procedimientos para configurar las cargas de trabajo en Power BI Premium
description: Descubra cómo configurar las cargas de trabajo en una capacidad Premium de Power BI.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: e22b598b81f34e80431d0def93d52f7301c500d4
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964649"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configuración de cargas de trabajo en una capacidad Premium

En este artículo se describe cómo habilitar y configurar las cargas de trabajo para capacidades Premium de Power BI. De forma predeterminada, las capacidades solo admiten la carga de trabajo asociada con la ejecución de consultas de Power BI. También puede habilitar y configurar cargas de trabajo adicionales para **[AI (Cognitive Services)](service-cognitive-services.md)**, **[Flujos de datos](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Informes paginados](paginated-reports-save-to-power-bi-service.md)**.

## <a name="default-memory-settings"></a>Configuración de memoria predeterminada

Las cargas de trabajo de consulta están optimizadas y limitadas en función de los recursos determinados por la SKU de la capacidad Premium. Las capacidades Premium también admiten cargas de trabajo adicionales que pueden usar recursos de su capacidad. Los valores de memoria predeterminados para estas cargas de trabajo se basan en los nodos de capacidad disponibles para su SKU. Estos valores de memoria máxima no son acumulativos. La memoria, hasta el valor máximo especificado, se asigna dinámicamente para AI y flujos de datos, pero estáticamente para informes paginados. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKU de Microsoft Office para los escenarios de software como servicio (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI (Cognitive Services) | 20 % predeterminado; TBD mín.| 20 % predeterminado; TBD mín. | 20 % predeterminado; TBD mín. | 20 % predeterminado; TBD mín. | 20 % predeterminado; TBD mín. |
| Flujos de datos | N/D |20 % predeterminado; 12 % mínimo  | 20 % predeterminado; 5 % mínimo  | 20 % predeterminado; 3 % mínimo | 20 % predeterminado; 2 % mínimo  |
| Informes paginados | N/D |N/D | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo | 20 % predeterminado; 2,5 % mínimo |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKU de Microsoft Azure para los escenarios de plataforma como servicio (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI (Cognitive Services) | N/D                      | 20 % predeterminado; TBD mín.                      | 20 % predeterminado; TBD mín.                     | 20 % predeterminado; TBD mín. | 20 % predeterminado; TBD mín. | 20 % predeterminado; TBD mín. |
| Flujos de datos         | 40 % predeterminado; 40 % mínimo | 24 % predeterminado; 24 % mínimo | 20 % predeterminado; 12 % mínimo | 20 % predeterminado; 5 % mínimo  | 20 % predeterminado; 3 % mínimo | 20 % predeterminado; 2 % mínimo   |
| Informes paginados | N/D                      | N/D                      | N/D                     | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo | 20 % predeterminado; 2,5 % mínimo |
| | | | | | |

## <a name="configure-workloads"></a>Configuración de las cargas de trabajo

Maximice los recursos disponibles de su capacidad habilitando las cargas de trabajo solo si se van a usar. Cambie la configuración de la memoria solo cuando disponga de una configuración predeterminada específica que no cumpla sus requisitos en relación con los recursos de capacidad.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar las cargas de trabajo en el portal de administración de Power BI

1. En **Configuración de la capacidad** > **CAPACIDADES PREMIUM**, seleccione una capacidad.

1. En **MÁS OPCIONES**, expanda **Cargas de trabajo**.

1. Habilite una o varias cargas de trabajo y establezca un valor para **Memoria máxima**.   

    
    ![Habilitación de las cargas de trabajo](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Haga clic en **Aplicar**.

> [!NOTE]
> Si habilita la carga de trabajo de los informes paginados, tenga en cuenta que dichos informes permiten ejecutar su propio código al representar un informe (por ejemplo, para cambiar de forma dinámica el color del texto en función del contenido). Power BI Premium ejecuta informes paginados en un espacio contenido dentro de la capacidad. Se usa la memoria máxima especificada para este espacio, independientemente de si la carga de trabajo está o no activa. Si usa informes o flujos de datos de Power BI en la misma capacidad, asegúrese de establecer una cantidad de memoria lo suficientemente baja para los informes paginados, de tal forma que no afecte negativamente a las otras cargas de trabajo. en circunstancias excepcionales, la carga de trabajo de informes paginados deja de estar disponible. En este caso, la carga de trabajo muestra un estado de error en el portal de administración y los usuarios ven los tiempos de expiración para la representación de informes. Para mitigar este problema, deshabilite la carga de trabajo y luego vuelva a habilitarla.

### <a name="rest-api"></a>API de REST

Las cargas de trabajo se pueden habilitar y asignar a una capacidad mediante las API de REST [Capacities](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Supervisión de cargas de trabajo

La aplicación [Métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md) proporciona métricas de conjuntos de datos, flujos de datos e informes paginados para supervisar las cargas de trabajo habilitadas para sus capacidades. 

## <a name="next-steps"></a>Pasos siguientes

[Optimización y administración de recursos con capacidad Power BI Premium](service-premium-understand-how-it-works.md)   
[Preparación de datos de autoservicio en Power BI en Power BI con flujos de datos](service-dataflows-overview.md)   
[¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

¿Tiene más preguntas? [Pregunte a la comunidad de Power BI](http://community.powerbi.com/)