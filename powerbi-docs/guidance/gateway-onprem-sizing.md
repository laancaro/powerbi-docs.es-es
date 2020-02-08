---
title: Ajuste de tamaño de la puerta de enlace de datos local
description: Guía para trabajar con el tamaño de la puerta de enlace de datos local.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 4f289bf319bf29de8f8765d55bf3400048420af5
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76829061"
---
# <a name="on-premises-data-gateway-sizing"></a>Ajuste de tamaño de la puerta de enlace de datos local

Este artículo va dirigido a los administradores de Power BI que necesitan instalar y administrar la [puerta de enlace de datos local](../service-gateway-onprem.md).

La puerta de enlace es necesaria cuando Power BI debe acceder a los datos que no son accesibles directamente a través de Internet. Se puede instalar en un servidor local o en una infraestructura como servicio (IaaS) hospedada en la máquina virtual.

## <a name="gateway-workloads"></a>Cargas de trabajo de puerta de enlace

La puerta de enlace de datos local admite dos cargas de trabajo. Es importante que comprenda primero estas cargas de trabajo antes de pasar a las recomendaciones y el tamaño de la puerta de enlace.

### <a name="cached-data-workload"></a>Carga de trabajo de datos en caché

La carga de trabajo de _datos en caché_ recupera y transforma los datos de origen para cargarlos en conjuntos de datos de Power BI. Emplea tres pasos:

1. **Conexión**: la puerta de enlace se conecta a los datos de origen.
1. **Recuperación y transformación de datos**: los datos se recuperan y, cuando es necesario, se transforman. Siempre que sea posible, el motor de mashup de Power Query inserta pasos de transformación en el origen de datos, lo que se conoce como _[plegado de consultas](power-query-folding.md)_ . Cuando no es posible, las transformaciones deben hacerse mediante la puerta de enlace. En este caso, la puerta de enlace consumirá más recursos de CPU y memoria.
1. **Transferencia**: los datos se transfieren al servicio Power BI: se necesita una conexión a Internet confiable y rápida, en especial con grandes volúmenes de datos.

![En un diagrama se muestra la puerta de enlace de datos local que se conecta a los orígenes locales: base de datos relacional, libro de Excel y archivos CSV. La puerta de enlace recupera y transforma los datos.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Cargas de trabajo de conexión dinámica y DirectQuery

La carga de trabajo de _conexión dinámica y DirectQuery_ funciona principalmente en modo de paso a través. El servicio Power BI envía consultas y la puerta de enlace responde con los resultados de la consulta. Por lo general, los resultados de la consulta son de pequeño tamaño.

- Para más información sobre la conexión dinámica, consulte [Conjuntos de datos del servicio Power BI (modelos hospedados externamente)](../service-datasets-understand.md#external-hosted-models).
- Para más información sobre DirectQuery, consulte [Modos de conjunto de datos en el servicio Power BI (modo DirectQuery)](../service-dataset-modes-understand.md#directquery-mode).

Esta carga de trabajo requiere recursos de CPU para el enrutamiento y los resultados de las consultas. Normalmente, hay mucha menos demanda de CPU de la que precisa la carga de trabajo de datos en caché, en especial cuando es necesaria para transformar los datos para el almacenamiento en caché.

Es importante una conectividad confiable, rápida y coherente para garantizar que los usuarios de informes tengan experiencias que respondan.

![En un diagrama se muestra la puerta de enlace de datos local que se conecta a los orígenes locales: Base de datos tabular y relacional de Analysis Services. La puerta de enlace funciona principalmente en modo de paso a través.](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Consideraciones de tamaño

La determinación del tamaño correcto de la máquina de puerta de enlace puede depender de las siguientes variables:

- En el caso de cargas de trabajo de datos de caché:
  - El número de actualizaciones simultáneas del conjunto de datos
  - Los tipos de orígenes de datos (base de datos relacional, base de datos analítica, fuentes de distribución de datos o archivos)
  - El volumen de datos que se van a recuperar de los orígenes de datos
  - Las transformaciones que debe realizar el motor de mashup de Power Query
  - El volumen de datos que se va a transferir al servicio Power BI
- En el caso de las cargas de trabajo de conexión dinámica y DirectQuery:
  - El número de usuarios simultáneos del informe
  - El número de objetos visuales en las páginas del informe (cada uno de ellos envía al menos una consulta)
  - La frecuencia de las actualizaciones de la caché de consultas del panel de Power BI
  - El número de informes en tiempo real mediante la característica [Actualización automática de páginas](../desktop-automatic-page-refresh.md)
  - Si los conjuntos de datos exigen [Seguridad de nivel de fila (RLS)](../desktop-rls.md)

Por lo general, las cargas de trabajo de conexión dinámica y DirectQuery requieren una CPU suficiente, mientras que las cargas de trabajo de datos de caché requieren más CPU y memoria. Ambas cargas de trabajo dependen de una buena conectividad con el servicio Power BI y los orígenes de datos.

> [!NOTE]
> Las capacidades de Power BI imponen límites sobre el paralelismo de las actualizaciones de los modelos y sobre el rendimiento de la conexión dinámica y DirectQuery. No tiene sentido ajustar el tamaño de las puertas de enlace para que proporcionen más capacidad de la que admite el servicio Power BI. Los límites difieren en la SKU Premium (y en la SKU A de tamaño equivalente). Para más información, consulte [¿Qué es Power BI Premium? (Nodos de capacidad)](../service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Recomendaciones

Las recomendaciones de tamaño de la puerta de enlace dependen de muchas variables. En esta sección, se proporcionan recomendaciones generales que puede tener en cuenta.

### <a name="initial-sizing"></a>Tamaño inicial

Puede ser difícil calcular con precisión el tamaño correcto. Se recomienda comenzar con una máquina con al menos 8 núcleos de CPU, 8 GB de RAM y varios adaptadores de red Gigabit. Después, puede medir una carga de trabajo típica de puerta de enlace mediante el registro de los contadores del sistema de memoria y CPU. Para más información, consulte [Supervisión y optimización del rendimiento de la puerta de enlace de datos local](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Conectividad

Planee la mejor conectividad posible entre el servicio Power BI y la puerta de enlace y entre la puerta de enlace y los orígenes de datos.

- Busque confiabilidad, velocidad rápida y latencias sistemáticamente bajas
- Elimine (o reduzca) los saltos de máquina entre la puerta de enlace y los orígenes de datos.
- Quite todas las limitaciones de red impuestas por la capa de proxy del firewall. Para más información sobre los puntos de conexión de Power BI, consulte [Direcciones URL de Power BI para la inclusión en listas blancas](../power-bi-whitelist-urls.md).
- Configure [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) para establecer conexiones privadas y administradas a Power BI
- En el caso de los orígenes de datos de máquinas virtuales de Azure, asegúrese de que las máquinas virtuales estén [colocadas con el servicio Power BI](../service-admin-where-is-my-tenant-located.md)
- En el caso de cargas de trabajo de conexión dinámica a SQL Server Analysis Services (SSAS) que supongan RLS dinámico, asegúrese de que la conectividad entre la máquina de puerta de enlace y Active Directory local sea correcta.

### <a name="clustering"></a>Agrupación en clústeres

Para implementaciones a gran escala, puede crear una puerta de enlace de instalaciones de clúster. Los clústeres evitan puntos únicos de error y pueden equilibrar la carga del tráfico entre puertas de enlace. Puede:

- Instalar una o varias puertas de enlace en un clúster
- Aislar las cargas de trabajo en puertas de enlace independientes o clústeres de servidores de puerta de enlace

Para más información, consulte [Administración de clústeres de alta disponibilidad y equilibrio de carga de la puerta de enlace de datos local](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Diseño y configuración del conjunto de datos

El diseño del conjunto de datos y su configuración pueden afectar a las cargas de trabajo de puerta de enlace. Para reducir la carga de trabajo de puerta de enlace, puede considerar las siguientes acciones.

Con conjuntos de datos de importación:

- Configurar la actualización de datos menos frecuente
- Configurar la [actualización incremental](../service-premium-incremental-refresh.md) para reducir la cantidad de datos que se van a transferir
- Siempre que sea posible, asegurarse de que tiene lugar el [plegado de consultas](power-query-folding.md)
- En especial, en el caso de grandes volúmenes de datos o que haya una necesidad de resultados de baja latencia, convierta el diseño a un modelo DirectQuery o [compuesto](../service-dataset-modes-understand.md#composite-mode).

Con conjuntos de datos DirectQuery:

- Optimizar los diseños de orígenes de datos, modelos e informes. Para más información, consulte [Instrucciones del modelo de DirectQuery en Power BI Desktop](directquery-model-guidance.md).
- Crear [agregaciones](../desktop-aggregations.md) para almacenar en caché los resultados de nivel superior con el fin de reducir el número de solicitudes de DirectQuery.
- Restringir los intervalos de [actualización automática de páginas](../desktop-automatic-page-refresh.md) en diseños de informe y configuraciones de capacidad.
- En especial, cuando se aplica RLS dinámico, restringir la frecuencia de actualización de la caché de paneles.
- En especial, en el caso de volúmenes de datos más pequeños o de datos no volátiles, convertir el diseño en un modelo de importación o [compuesto](../service-dataset-modes-understand.md#composite-mode).

Con conjuntos de datos de conexión dinámica:

- En especial, cuando se aplica RLS dinámico, restringir la frecuencia de actualización de la caché de paneles.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Guía para la implementación de una puerta de enlace de datos para Power BI](../service-gateway-deployment-guidance.md)
- [Configuración de los valores del proxy para la puerta de enlace de datos local](/data-integration/gateway/service-gateway-proxy)
- [Supervisión y optimización del rendimiento de la puerta de enlace de datos local](/data-integration/gateway/service-gateway-performance)
- [Solución de problemas de puertas de enlace: Power BI](../service-gateway-onprem-tshoot.md)
- [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot)
- [La importancia del plegado de consultas](power-query-folding.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com)
