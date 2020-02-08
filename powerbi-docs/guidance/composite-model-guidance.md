---
title: Guía de modelos compuestos de Power BI Desktop
description: Guía para el desarrollo de modelos compuestos.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/24/2019
ms.author: v-pemyer
ms.openlocfilehash: fa9ecd66d30839e169252065f7f736189b71b6ce
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2020
ms.locfileid: "76889489"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Guía de modelos compuestos de Power BI Desktop

Este artículo va dirigido a los modeladores de datos que desarrollan modelos compuestos de Power BI. En él se describen los casos de uso de modelos compuestos y se proporcionan instrucciones de diseño. En concreto, la guía es para ayudarle a determinar si un modelo compuesto es adecuado para su solución. En caso afirmativo, este artículo también le ayudará a diseñar un modelo óptimo.

> [!NOTE]
> En este artículo no se incluye una introducción a los modelos compuestos. Si no está totalmente familiarizado con los modelos compuestos, le recomendamos que primero lea el artículo [Usar modelos compuestos en Power BI Desktop](../desktop-composite-models.md).
>
> Dado que los modelos compuestos constan de al menos un origen de DirectQuery, también es importante comprender perfectamente las [relaciones del modelo](../desktop-relationships-understand.md), los [modelos de DirectQuery](../desktop-directquery-about.md) y la [guía de diseño del modelo DirectQuery](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Casos de uso del modelo compuesto

Siempre que sea posible, es mejor desarrollar un modelo en modo de importación. Este modo proporciona la mayor flexibilidad de diseño y el mejor rendimiento.

Sin embargo, los modelos de importación no pueden resolver los desafíos relacionados con grandes volúmenes de datos o con la generación de informes sobre datos casi en tiempo real. En cualquiera de estos casos, puede considerar un modelo DirectQuery, siempre y cuando los datos se almacenen en un único origen de datos que sea [compatible con el modo DirectQuery](../power-bi-data-sources.md).

Además, puede considerar el desarrollo de un modelo compuesto en las siguientes situaciones.

- El modelo podría ser un modelo DirectQuery, pero desea mejorar el rendimiento. En un modelo compuesto, el rendimiento se puede mejorar configurando el almacenamiento adecuado para cada tabla. También puede agregar [agregaciones](../desktop-aggregations.md). Estas dos optimizaciones se describen más adelante en este artículo.
- Quiere combinar un modelo DirectQuery con datos adicionales, que se deben importar en el modelo. Los datos importados se pueden cargar desde un origen de datos diferente o desde tablas calculadas.
- Desea combinar dos o más orígenes de datos DirectQuery en un único modelo.

> [!NOTE]
> Los modelos compuestos no pueden combinar orígenes de conexión dinámica u orígenes de base de datos analíticos de DirectQuery. Los orígenes de conexión dinámica incluyen [modelos con hospedaje externo](../service-datasets-understand.md#external-hosted-models) y conjuntos de datos de Power BI. Los orígenes de base de datos analíticos de DirectQuery incluyen SAP Business Warehouse y SAP HANA.

## <a name="optimize-model-design"></a>Optimización del diseño del modelo

Un modelo compuesto puede optimizarse mediante la configuración de [modos de almacenamiento](../desktop-storage-mode.md) de tabla y la adición de [agregaciones](../desktop-aggregations.md).

### <a name="table-storage-mode"></a>Modo Table Storage

En un modelo compuesto, puede configurar el modo de almacenamiento de cada tabla (excepto las tablas calculadas):

- **DirectQuery**: se recomienda establecer este modo para las tablas que representan grandes volúmenes de datos o que deben proporcionar resultados casi en tiempo real. Los datos nunca se importarán en estas tablas. Normalmente, estas tablas serán tablas de tipo de hechos (tablas usadas para el resumen).
- **Importación**: se recomienda establecer este modo para las tablas de tipo dimensión: tablas que se usan para filtrar y agrupar. De hecho, es la única opción para las tablas basadas en orígenes que no son compatibles con el modo DirectQuery. Las tablas calculadas siempre son tablas de importación.
- **Dual**: se recomienda establecer este modo para las tablas de tipo dimensión, cuando exista la posibilidad de que se realicen consultas en ellas junto con las tablas de tipo de hechos DirectQuery del mismo origen.

Hay varios escenarios posibles cuando Power BI consulta un modelo compuesto:

- **Consultas solo de tablas de importación o duales**: todos los datos se recuperan de la caché de modelos. Este escenario proporcionará el rendimiento más rápido posible. Es común para las tablas de tipo dimensión consultadas mediante filtros u objetos visuales de segmentación de datos.
- **Consultas de tablas duales o DirectQuery desde el mismo origen**: todos los datos se recuperan mediante el envío de una o varias consultas nativas al origen de DirectQuery. Este escenario proporcionará el rendimiento más rápido posible, especialmente cuando existan índices adecuados en las tablas de origen. Es común para las consultas que relacionan tablas duales de tipo dimensión y tablas DirectQuery de tipo de hechos. Estas consultas son _intrainsulares_, y así todas las relaciones de uno a uno o de uno a varios se evalúan como [relaciones fuertes](../desktop-relationships-understand.md#strong-relationships).
- **Todas las demás consultas**: estas consultas implican relaciones entre islas. O bien porque una tabla de importación se relaciona con una tabla DirectQuery o una tabla dual se relaciona con una tabla DirectQuery de un origen diferente, en cuyo caso se comporta como una tabla de importación. Todas las relaciones se evalúan como [relaciones débiles](../desktop-relationships-understand.md#weak-relationships). También significa que las agrupaciones aplicadas a tablas que no son DirectQuery deben enviarse al origen de DirectQuery como una tabla virtual. En este caso, la consulta nativa puede ser ineficaz, en especial con conjuntos de agrupamiento grandes. Además, tiene la posibilidad de exponer datos confidenciales en la consulta nativa.

En resumen, se recomienda que:

- Considere detenidamente que un modelo compuesto sea la solución correcta: si bien permite la integración de nivel de modelo de distintos orígenes de datos, también presenta complejidades de diseño con posibles consecuencias.
- Establezca el modo de almacenamiento en **DirectQuery** cuando una tabla sea una tabla de tipo de hechos que almacene grandes volúmenes de datos o necesite ofrecer resultados casi en tiempo real.
- Establezca el modo de almacenamiento en **Dual** cuando una tabla sea una tabla de tipo dimensión, que se consultará junto con tablas **DirectQuery** de tipos de hechos basadas en el mismo origen.
- Configure las frecuencias de actualización adecuadas para mantener sincronizada la caché de modelos de las tablas duales (y las tablas calculadas dependientes) con las bases de datos de origen.
- Intente garantizar la integridad de los datos entre orígenes de datos (incluida la caché de modelos): las relaciones débiles eliminarán filas cuando los valores de columna relacionados no coincidan.
- Optimice los orígenes de datos de DirectQuery con los índices adecuados para conseguir combinaciones, filtrados y agrupaciones eficaces.
- No cargue datos confidenciales en tablas de importación o duales si hay riesgo de que se intercepten consultas nativas. para más información, consulte [Uso de modelos compuestos en Power BI Desktop (implicaciones para la seguridad)](../desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>Agregaciones

Puede agregar agregaciones a tablas DirectQuery en el modelo compuesto. Las agregaciones se almacenan en caché en el modelo, por lo que se comportan como tablas de importación (aunque no se pueden usar como una tabla de modelo). Su finalidad es mejorar el rendimiento de las consultas de más alto nivel de detalle. Para más información, vea [Agregaciones en Power BI Desktop](../desktop-aggregations.md).

Se recomienda que las tablas de agregación sigan una regla básica: su recuento de filas debe ser al menos un factor de 10 inferior a la tabla subyacente. Por ejemplo, si la tabla subyacente almacena mil millones de filas, la tabla de agregación no debe superar los 100 millones de filas. Esta regla garantiza una ganancia de rendimiento adecuada en relación con el costo de la creación y el mantenimiento de la tabla de agregación.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Usar modelos compuestos en Power BI Desktop](../desktop-composite-models.md)
- [Relaciones de modelos en Power BI Desktop](../desktop-relationships-understand.md)
- [Modelos de DirectQuery en Power BI Desktop](../desktop-directquery-about.md)
- [Usar DirectQuery en Power BI Desktop](../desktop-use-directquery.md)
- [Solución de problemas del modelo de DirectQuery en Power BI Desktop](../desktop-directquery-troubleshoot.md)
- [Orígenes de datos de Power BI](../power-bi-data-sources.md)
- [Modo de almacenamiento en Power BI Desktop](../desktop-storage-mode.md)
- [Agregaciones en Power BI Desktop](../desktop-aggregations.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com)
