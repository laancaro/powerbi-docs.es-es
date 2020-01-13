---
title: Instrucciones de plegado de consultas en Power BI Desktop
description: Instrucciones para lograr el plegado de consultas de Power Query en Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: e8123bba9f68305e1944dbfb280b5255e4fb9b48
ms.sourcegitcommit: ef9ab7c0d84b926094c33e8aa2765cd43b844314
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2020
ms.locfileid: "75622157"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Instrucciones de plegado de consultas en Power BI Desktop

Este artículo se dirige a los modeladores de datos que desarrollan modelos en Power BI Desktop. Proporciona instrucciones de procedimientos recomendados sobre cuándo y cómo lograr el plegado de consultas de Power Query.

El _plegado de consultas_ es la capacidad de una consulta de Power Query de generar una instrucción de consulta única que recupera y transforma los datos de origen. Para obtener más información, vea [Plegado de consultas de Power Query](/power-query/power-query-folding).

## <a name="guidance"></a>Instrucciones

Las instrucciones sobre plegado de consultas difieren en función del modo de modelo.

Para una tabla del modo de almacenamiento **DirectQuery** o **Dual**, la consulta de Power Query debe lograr el plegado de consultas.

En el caso de una tabla de **Importación**, es posible que se pueda conseguir el plegado de consultas. Cuando la consulta se basa en un origen relacional, y si se puede construir una sola instrucción SELECT, el _mejor rendimiento de la actualización de datos_ se consigue asegurándose de que se produce el plegado de consultas. Si todavía es necesario que el motor de mashup de Power Query procese las transformaciones, debe procurar minimizar el trabajo que tiene que hacer, en especial para los conjuntos de datos grandes.

En la siguiente lista con viñetas se proporcionan instrucciones concretas.

- **Delegar todo el procesamiento que sea posible en el origen de datos:** cuando no se pueden plegar todos los pasos de una consulta de Power Query, descubra qué paso impide el plegado de consultas. Cuando sea posible, adelante los pasos finales en la secuencia, para que se puedan factorizar en el plegado de consultas. Tenga en cuenta que el motor de mashup de Power Query puede ser lo suficientemente inteligente como para reordenar los pasos de la consulta al generar la consulta de origen.

    En el caso de un origen de datos relacional, si el paso que impide el plegado de consultas se puede lograr con una sola instrucción SELECT, o bien dentro de la lógica de procedimiento de un procedimiento almacenado, considere la posibilidad de usar una consulta SQL nativa, como se describe a continuación.

- **Uso de una consulta SQL nativa**: cuando una consulta de Power Query recupera datos de un origen relacional, algunos orígenes pueden usar una consulta SQL nativa. En realidad, la consulta puede ser cualquier instrucción válida, incluida la ejecución de un procedimiento almacenado. Si la instrucción genera varios conjuntos de resultados, solo se devolverá el primero. Los parámetros se pueden declarar en la instrucción y se recomienda usar la función de M [Value.NativeQuery](/powerquery-m/value-nativequery). Esta función se ha diseñado para pasar valores de parámetro de manera segura y cómoda. Es importante comprender que el motor de mashup de Power Query no puede plegar pasos de consulta posteriores, por lo que debe incluir toda la lógica de transformación (o la mayor parte posible) en la instrucción de consulta nativa.

    Existen dos consideraciones importantes que se deben tener en cuenta al usar consultas SQL nativas:

    - En el caso de una tabla del modelo de DirectQuery, la consulta debe ser una instrucción SELECT y no puede usar expresiones de tabla comunes (CTE) ni un procedimiento almacenado.
    - La actualización incremental no puede usar una consulta SQL nativa. Por tanto, obligaría al motor de mashup de Power Query a recuperar todas las filas de origen y, después, aplicar filtros para determinar los cambios incrementales.

    > [!IMPORTANT]
    > Una consulta SQL nativa puede hacer más que recuperar datos. Se puede ejecutar cualquier instrucción válida (y posiblemente varias veces), incluida una que modifica o elimina datos. Es importante aplicar el principio de privilegios mínimos para asegurarse de que la cuenta usada para acceder a la base de datos solo tiene permiso de lectura en los datos necesarios.

- **Preparación y transformación de los datos en el origen**: al identificar que determinados pasos de la consulta de Power Query no se pueden plegar, es posible aplicar las transformaciones en el origen de datos. Las transformaciones se podrían lograr si se escribe una vista de base de datos que transforme de forma lógica los datos de origen. O bien, mediante la preparación física y la materialización de los datos, antes de que Power BI los consulte. Un almacenamiento de datos relacional es un excelente ejemplo de datos preparados, normalmente compuesto por orígenes de datos de la organización integrados previamente.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- Artículo de concepto [Plegado de consultas](/power-query/power-query-folding) de Power Query
- [Actualizaciones incrementales en Power BI Premium](../service-premium-incremental-refresh.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
