---
title: Procedimientos para configurar las cargas de trabajo en Power BI Premium
description: Descubra cómo configurar las cargas de trabajo en una capacidad Premium de Power BI.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564878"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configuración de cargas de trabajo en una capacidad Premium

En este artículo se describe cómo habilitar y configurar las cargas de trabajo para capacidades Premium de Power BI. De forma predeterminada, las capacidades solo admiten la carga de trabajo asociada con la ejecución de consultas de Power BI. También puede habilitar y configurar cargas de trabajo adicionales para **[AI (Cognitive Services)](service-cognitive-services.md)** , **[Flujos de datos](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Informes paginados](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Configuración de memoria predeterminada

Las cargas de trabajo de consulta están optimizadas y limitadas en función de los recursos determinados por la SKU de la capacidad Premium. Las capacidades Premium también admiten cargas de trabajo adicionales que pueden usar recursos de su capacidad. Los valores de memoria predeterminados para estas cargas de trabajo se basan en los nodos de capacidad disponibles para su SKU. Estos valores de memoria máxima no son acumulativos. La memoria, hasta el valor máximo especificado, se asigna dinámicamente para AI y flujos de datos, pero estáticamente para informes paginados. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKU de Microsoft Office para los escenarios de software como servicio (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N/D | N/D | valor predeterminado de 20%; mínimo de 20% | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo |
| Flujos de datos | N/D |20 % predeterminado; 12 % mínimo  | 20 % predeterminado; 5 % mínimo  | 20 % predeterminado; 3 % mínimo | 20 % predeterminado; 2 % mínimo  |
| Informes paginados | N/D |N/D | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo | 20 % predeterminado; 2,5 % mínimo |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKU de Microsoft Azure para los escenarios de plataforma como servicio (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N/D                      | valor predeterminado de 20%; mínimo de 100%                     | valor predeterminado de 20%; mínimo de 50%                     | valor predeterminado de 20%; mínimo de 20% | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo |
| Flujos de datos         | 40 % predeterminado; 40 % mínimo | 24 % predeterminado; 24 % mínimo | 20 % predeterminado; 12 % mínimo | 20 % predeterminado; 5 % mínimo  | 20 % predeterminado; 3 % mínimo | 20 % predeterminado; 2 % mínimo   |
| Informes paginados | N/D                      | N/D                      | N/D                     | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo | 20 % predeterminado; 2,5 % mínimo |
| | | | | | |

## <a name="workload-settings"></a>Configuración de la carga de trabajo

### <a name="ai-preview"></a>AI (versión preliminar)

Además el **Max Memory** establecimiento, la carga de trabajo de inteligencia artificial tiene una configuración adicional, **permitir el uso de Power BI Desktop**. El valor predeterminado es **desactivar**. Esta configuración está reservada para uso futuro y no puede aparecer en todos los inquilinos.

### <a name="datasets-preview"></a>Conjuntos de datos (versión preliminar)

De forma predeterminada, la carga de trabajo de los conjuntos de datos está habilitada y no se puede deshabilitar. Esta carga de trabajo contiene una configuración adicional, **extremo XMLA**. El valor predeterminado es **1**, significado habilitado. Esta configuración especifica las conexiones desde aplicaciones cliente respetan la pertenencia al grupo de seguridad establecidos en los niveles de aplicación y el área de trabajo. Para obtener más información, consulte [conectarse a conjuntos de datos con herramientas y aplicaciones cliente](service-premium-connect-tools.md).

### <a name="dataflows"></a>Flujos de datos

Además el **Max Memory** establecimiento, la carga de trabajo de flujos de datos tiene una configuración adicional, **tamaño del contenedor**. Esta configuración le permite optimizar el rendimiento de la carga de trabajo de flujo de datos para el procesamiento de flujos de datos más complejos y de proceso intensivo.

Al actualizar un flujo de datos, la carga de trabajo de flujo de datos genera un contenedor para cada entidad en el flujo de datos. Cada contenedor puede tardar memoria hasta el volumen en especificado en la configuración de tamaño del contenedor. El valor predeterminado para todos los SKU es **700 MB**. Es posible que desee cambiar esta configuración si:

- Flujos de datos tardan demasiados en actualizar, o se produce un error de actualización de flujo de datos en un tiempo de espera.
- Las entidades de flujo de datos incluyen los pasos de cálculo, por ejemplo, una combinación.  

Recomienda usar de la la [métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md) aplicación para analizar el rendimiento de la carga de trabajo de flujo de datos. 

En algunos casos, aumenta el tamaño del contenedor no puede mejorar rendimiento. Por ejemplo, si el flujo de datos está obteniendo datos solo desde un origen sin necesidad de realizar cálculos significativos, cambiar el tamaño del contenedor probablemente no ayuda. Aumentar el tamaño del contenedor podría ser útil si permitirá la carga de trabajo de flujo de datos asignar más memoria para la entidad de las operaciones de actualización. Al tener más memoria asignada, puede reducir el tiempo necesario para actualizar entidades de gran medida calculadas. 

El valor de tamaño del contenedor no puede superar la memoria máxima para la carga de trabajo de flujos de datos. Por ejemplo, una capacidad de P1 tiene 25GB de memoria. Si la carga de trabajo de flujo de datos Max Memory (%) se establece en 20%, contenedor de tamaño (MB) no puede superar los 5000. En todos los casos, el tamaño del contenedor no puede superar Max Memory, incluso si establece un valor mayor. 

### <a name="paginated-reports-preview"></a>Informes paginados (versión preliminar)

Informes paginados permiten código personalizado que se ejecutan al representar un informe. Por ejemplo, cambiar dinámicamente el color del texto en función del contenido, que puede adoptar memoria adicional. Power BI Premium ejecuta informes paginados en un espacio contenido dentro de la capacidad. Especifica, se usa la Max Memory *si* la carga de trabajo está activo. Si cambiar la configuración de memoria máxima de forma predeterminada, asegúrese de que se establece bajo suficientemente que TI no afectar negativamente a otras cargas de trabajo.

En algunos casos, la carga de trabajo de informes paginados puede estar disponible. En este caso, la carga de trabajo muestra un estado de error en el portal de administración y los usuarios ven los tiempos de espera para la representación de informes. Para mitigar este problema, deshabilite la carga de trabajo y, a continuación, vuelva a habilitarla.

## <a name="configure-workloads"></a>Configuración de las cargas de trabajo

Maximice los recursos disponibles de su capacidad habilitando las cargas de trabajo solo si se van a usar. Cambie la configuración de la memoria solo cuando disponga de una configuración predeterminada específica que no cumpla sus requisitos en relación con los recursos de capacidad.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar las cargas de trabajo en el portal de administración de Power BI

1. En **Configuración de la capacidad** > **CAPACIDADES PREMIUM**, seleccione una capacidad.

1. En **MÁS OPCIONES**, expanda **Cargas de trabajo**.

1. Habilite una o varias cargas de trabajo y establezca un valor para **Memoria máxima**.   

    
    ![Habilitación de las cargas de trabajo](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Haga clic en **Aplicar**.

### <a name="rest-api"></a>API de REST

Las cargas de trabajo se pueden habilitar y asignar a una capacidad mediante las API de REST [Capacities](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Supervisión de cargas de trabajo

La aplicación [Métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md) proporciona métricas de conjuntos de datos, flujos de datos e informes paginados para supervisar las cargas de trabajo habilitadas para sus capacidades. 

## <a name="next-steps"></a>Pasos siguientes

[Optimizar las capacidades de Power BI Premium](service-premium-capacity-optimize.md)     
[Preparación de datos de autoservicio en Power BI en Power BI con flujos de datos](service-dataflows-overview.md)   
[¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

¿Tiene más preguntas? [Pregunte a la comunidad de Power BI](http://community.powerbi.com/)