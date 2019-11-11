---
title: Procedimientos recomendados para los flujos de datos de Power BI
description: Procedimientos recomendados para los flujos de datos de Power BI
author: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 4bbc8b71455d01405854304dd4b889f664ce8575
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877285"
---
# <a name="dataflows-best-practice"></a>Procedimientos recomendados de los flujos de datos

En este artículo se describen los procedimientos recomendados para diseñar flujos de datos en Power BI. Puede usar esta guía para aprender a crear flujos de datos y aplicar estos procedimientos a sus propios flujos de datos.

> [!NOTE]
> Las recomendaciones que se realizan en este artículo son directrices. Todos los procedimientos recomendados de este artículo pueden tener motivos legítimos para desviarse de esta guía. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Dividir la ingesta y la transformación para usar el motor de proceso mejorado

Al crear flujos de datos, es posible que se sienta tentado a crear un único flujo de entrada con todas las entidades, transformaciones, combinaciones y mejoras en un solo lugar. En el caso de conjuntos de valores más pequeños, un único flujo de datos puede ser efectivo. Sin embargo, cuando se trabaja con volúmenes de datos más grandes, la realización de combinaciones o de determinadas transformaciones puede dar lugar en ocasiones a restricciones o límites de memoria. Para solucionar estos problemas, se ha lanzado el motor mejorado para usuarios de Power BI Premium que se escala a volúmenes de datos mucho mayores. El motor de proceso mejorado solo funciona con entidades vinculadas o calculadas, así que la creación de un flujo de datos para la ingesta y un flujo de datos vinculado para realizar todas las combinaciones y transformaciones complejas puede beneficiarse de las ventajas de este motor.

La división de los flujos de datos también resulta beneficioso para el diagnóstico y la depuración de problemas de actualización, especialmente cuando se trabaja con orígenes que tienen limitaciones.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Realizar acciones que puedan usar el motor de proceso mejorado

Para tener la seguridad de usar el motor de proceso mejorado, confirme que primero se realizan las combinaciones y las transformaciones de filtros en una entidad calculada antes de llevar a cabo otros tipos de transformaciones.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Dividir los flujos de datos al conectarse a SharePoint

Al trabajar con SharePoint y conectarse a varios archivos, es posible que observe errores esporádicos. SharePoint limita las solicitudes para garantizar su confiabilidad y capacidad de respuesta. Como consecuencia, al conectarse a archivos de Excel desde SharePoint, puede que tienda a descargar todos los archivos en un único flujo de datos. Si va a descargar muchos archivos, más de 20, cree dos o más flujos de datos para dividir la carga de actualización y superar la limitación de SharePoint.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Evitar programar la actualización de entidades vinculadas dentro de la misma área de trabajo

Si normalmente se bloquean los flujos de datos que contienen entidades vinculadas, puede ser debido a que el correspondiente flujo de datos dependiente dentro del mismo área de trabajo se bloquea cuando se actualiza. Este bloqueo proporciona precisión transaccional y, si bien garantiza que ambos flujos de datos se actualizan correctamente, puede impedir que se editen. 

Si configura una programación independiente para el flujo de datos vinculado, los flujos de datos pueden actualizarse innecesariamente e impedirle que pueda editarlos. Para evitar este problema, siga estas dos recomendaciones: 

* Evite establecer una programación de actualización para un flujo de trabajo vinculado del mismo área de trabajo que el flujo de datos de origen.
* Si quiere configurar una programación de actualización por separado y desea evitar el comportamiento de bloqueo, separe el flujo de datos en un área de trabajo aparte.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Crear un área de trabajo independiente para la ingesta y la transformación

Para proporcionar acceso a los datos del flujo de datos subyacente para muchos usuarios sin permitir el acceso a los datos sin procesar del sistema de origen subyacente, cree un área de trabajo independiente que contenga todos los datos que necesite compartir y asigne permisos. Actualmente no se admiten permisos para flujo de datos individuales.

### <a name="ensure-capacity-is-in-the-same-region"></a>Asegurarse de que la capacidad esté en la misma región

Los flujos de datos no admiten actualmente varias regiones geográficas. La capacidad Premium debe estar en la misma región que el inquilino de Power BI.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Separar orígenes locales de los orígenes de nube

Además de los procedimientos recomendados descritos anteriormente, puede crear un flujo de datos independiente para cada tipo de origen: local, nube, SQL Server, Spark, Dynamics, etc. Se recomienda completamente dividir el flujo de datos por tipo de origen de datos. Esta separación por tipo de origen facilita la solución de problemas rápida y evita los límites internos al actualizar los flujos de datos.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Separar los flujos de datos en una capacidad aparte

Si experimenta limitaciones o percibe errores habituales en los flujos de datos debido a límites de memoria en su capacidad, tiene la posibilidad de separar los flujos de datos o de escalar verticalmente la capacidad Premium para obtener memoria adicional.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporciona información sobre los procedimientos recomendados para los flujos de datos. Para más información sobre los flujos de datos, los siguientes artículos pueden resultar útiles:

* [Preparación de datos de autoservicio con flujos de datos](service-dataflows-overview.md)
* [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
* [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso de flujos de datos con orígenes de datos locales](service-dataflows-on-premises-gateways.md)

Para información sobre el desarrollo de CDS y los recursos del tutorial, consulte los siguientes artículos:
* [Introducción a Common Data Service](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Carpetas de CDS](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definición del archivo de modelo de CDS](https://go.microsoft.com/fwlink/?linkid=2045521)


Para obtener más información sobre Power Query y la actualización programada, puede leer estos artículos:
* [Información general sobre consultas en Power BI Desktop](desktop-query-overview.md)
* [Configuración de la actualización programada](refresh-scheduled-refresh.md)
