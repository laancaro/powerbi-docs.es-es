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
ms.date: 03/11/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0baab138ee98d2ec96bc9f47e6e727525a57ed3e
ms.sourcegitcommit: f176ba9d52d50d93f264eca21bb3fd987dbf934b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57757255"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configuración de cargas de trabajo en una capacidad Premium

En este artículo se describe cómo habilitar y configurar las cargas de trabajo para capacidades Premium de Power BI. De forma predeterminada, las capacidades solo admiten la carga de trabajo asociada con la ejecución de consultas de Power BI. Las cargas de trabajo de consulta están optimizadas y limitadas en función de los recursos determinados por la SKU de la capacidad Premium. Las capacidades Premium también admiten cargas de trabajo adicionales que pueden usar recursos de capacidad.

## <a name="configure-workloads"></a>Configuración de las cargas de trabajo

Puede habilitar y configurar cargas de trabajo adicionales para AI, [Flujos de datos](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) e [Informes paginados](paginated-reports-save-to-power-bi-service.md). Los valores de memoria predeterminados para estas cargas de trabajo se basan en los nodos de capacidad disponibles para su SKU. Estos valores de memoria máxima no son acumulativos. La memoria, hasta el valor máximo especificado, se asigna dinámicamente para AI y flujos de datos, pero estáticamente para informes paginados. 

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


## <a name="next-steps"></a>Pasos siguientes

[Optimización y administración de recursos con capacidad Power BI Premium](service-premium-understand-how-it-works.md)   
[Preparación de datos de autoservicio en Power BI en Power BI con flujos de datos](service-dataflows-overview.md)   
[¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

¿Tiene más preguntas? [Pregunte a la comunidad de Power BI](http://community.powerbi.com/)