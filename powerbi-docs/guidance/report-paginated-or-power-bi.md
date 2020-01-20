---
title: Cuándo usar informes paginados en Power BI
description: Guía de uso de los informes paginados de Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 2e048c3aa2ebc6e51388be652234c2ccf2348663
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886145"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Cuándo usar informes paginados en Power BI

Este artículo está dirigido a los diseñadores de informes para Power BI. Proporciona sugerencias para ayudarle a decidir cuándo desarrollar [informes paginados de Power BI](../paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> Publicar informes paginados de Power BI requiere una suscripción a Power BI Premium. Los informes solo se representarán si están en un área de trabajo en una capacidad dedicada que tiene [habilitada el área de trabajo de informes paginados](../service-admin-premium-workloads.md#paginated-reports).

Los informes paginados de Power BI están optimizados para la **impresión**o **generación de PDF**. También permiten producir diseños de gran formato con una pixelación perfecta. Por lo tanto, los informes paginados son ideales para los informes operativos, como las facturas de ventas.

Por otra parte, los informes de Power BI están optimizados para la **exploración e interactividad**. Además, pueden presentar los datos mediante una amplia gama de objetos visuales muy modernos. Los informes de Power BI, por lo tanto, son ideales para informes analíticos, lo que permite a los usuarios de los informes explorar los datos y detectar relaciones y patrones.

Se recomienda que considere la posibilidad de usar un informe paginado de Power BI en los siguientes casos:

* Sabe que el informe debe imprimirse o mostrarse como un documento PDF.
* Los diseños de cuadrícula de datos pueden expandirse y desbordarse. Tenga en cuenta que una tabla o una matriz en un informe de Power BI no se puede cambiar de tamaño dinámicamente para mostrar todos los datos; en su lugar, se proporcionarán barras de desplazamiento. Sin embargo, si se imprimen, no será posible desplazarse para mostrar los datos que no estén a la vista.
* Las características y capacidades paginadas de Power BI son una gran ventaja. Muchos de estos escenarios de informes se describen más adelante en este artículo.

## <a name="legacy-reports"></a>Informes heredados

Si ya tiene informes de [Report Definition Language (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) de SQL Server Reporting Services (SSRS), puede volver a desarrollarlos como [informes de Power BI](../consumer/end-user-reports.md) o migrarlos como informes paginados a Power BI. Para obtener más información, consulte [Migración de informes de SQL Server Reporting Services a Power BI](migrate-ssrs-reports-to-power-bi.md).

Una vez publicados en un área de trabajo de Power BI, los informes paginados están disponibles en paralelo con los de Power BI. A continuación, se pueden distribuir fácilmente mediante las [aplicaciones de Power BI](../service-create-distribute-apps.md).

Podría valorar la posibilidad de volver a desarrollar informes de SSRS, en lugar de migrarlos. Es especialmente útil para los informes que están diseñados para ofrecer experiencias analíticas. En estos casos, los informes de Power BI probablemente ofrezcan mejores experiencias de usuario.

## <a name="paginated-report-scenarios"></a>Escenarios de informes paginados

Hay muchos escenarios atractivos en los que puede preferir el desarrollo de un informe paginado de Power BI. Muchas son características o capacidades que no se admiten en los informes de Power BI.

* **Listos para imprimir**: Los informes paginados están optimizados para la impresión o generación de PDF. Cuando sea necesario, las regiones de datos se pueden expandir y desbordar en varias páginas de una manera controlada. Los diseños de los informes pueden definir los márgenes, los encabezados y los pies de página.
* **Formatos de representación**: Power BI puede representar informes paginados en formatos diferentes. Los formatos incluyen Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML y MHTML. (El servicio Power BI usa el formato MHTML para representar los informes). Los usuarios del informe pueden decidir exportarlo en el formato que prefieran.
* **Diseño de precisión**: Puede realizar diseños de gran formato y con una pixelación perfecta, con el tamaño y la ubicación exactos, configurados en fracciones de pulgadas o centímetros.
* **Diseño dinámico**: Puede generar diseños con gran capacidad de respuesta estableciendo muchas propiedades de informe para usar expresiones VB.NET. Las expresiones tienen acceso a muchas de las principales bibliotecas de .NET Framework.
* **Diseño específico para representación**: Puede usar expresiones para modificar el diseño del informe en función del formato de representación aplicado. Por ejemplo, puede diseñar el informe para deshabilitar la visibilidad de alternancia (para lograr la exploración en profundidad y la obtención de detalles) al representarlo con un formato no interactivo, como PDF.
* **Consultas nativas**: No es necesario que desarrolle primero un conjunto de datos de Power BI. Es posible crear consultas nativas del autor (o usar procedimientos almacenados) para cualquier [origen de datos admitido](../paginated-reports-data-sources.md). Las consultas pueden incluir parametrización.
* **Diseñadores gráficos de consultas**: Power BI Report Builder incluye diseñadores gráficos de consultas para ayudarle a escribir y probar sus consultas de conjuntos de datos.
* **Conjuntos de datos estáticos**: Puede definir un conjunto de datos y escribir los datos directamente en la definición del informe. Esta funcionalidad es especialmente útil para respaldar una demostración o para ofrecer una prueba de concepto (POC).
* **Integración de datos**: Puede combinar datos de distintos orígenes de datos o con conjuntos de datos estáticos. Para ello, se crean campos personalizados mediante expresiones VB.NET.
* **Parametrización**: Puede diseñar experiencias de parametrización muy personalizadas, incluidos parámetros basados en datos y en cascada. También es posible definir los valores predeterminados de los parámetros. Estas experiencias pueden diseñarse para ayudar a los usuarios de los informes a establecer rápidamente los filtros adecuados. Además, no es necesario que los parámetros filtren los datos del informe; se pueden usar para admitir escenarios de tipo "y si", filtrado o estilo dinámico.
* **Datos de imagen**: El informe puede representar imágenes cuando se almacenan en formato binario en un origen de datos.
* **Código personalizado**: Puede desarrollar bloques de código de las funciones de VB.NET en el informe y usarlos en cualquier expresión de informe.
* **Subinformes**: Puede incrustar otros informes paginados de Power BI (desde la misma área de trabajo) en el informe.
* **Cuadrículas de datos flexibles**: Tiene un control exhaustivo de los diseños de cuadrícula mediante el uso de la región de datos Tablix. También admite diseños complejos, incluidos los grupos anidados y adyacentes. Además, se puede configurar para repetir los encabezados cuando se imprimen en varias páginas. También puede insertar un subinforme u otras visualizaciones, incluidas barras de datos, minigráficos e indicadores.
* **Tipos de datos espaciales**: La región de datos de mapa puede visualizar [tipos de datos espaciales de SQL Server](/sql/relational-databases/spatial/spatial-data-sql-server). Por lo tanto, los tipos de datos GEOGRAPHY y GEOMETRY se pueden usar para visualizar puntos, líneas o polígonos. También es posible visualizar polígonos definidos en archivos de forma ESRI.
* **Medidores modernos**: Los medidores radiales y lineales se pueden usar para mostrar valores de KPI y estado. Incluso se pueden incrustar en regiones de datos de cuadrícula, que se repiten dentro de grupos.
* **Representación en HTML**: Puede mostrar texto con formato enriquecido cuando se almacena como HTML.
* **Combinar correspondencia**: Puede usar los marcadores de posición de cuadro de texto para insertar valores de datos en el texto. De este modo, puede generar un informe de combinación de correspondencia.
* **Características de interactividad**: Entre las características interactivas se incluyen la alternancia de la visibilidad (para lograr exploración en profundidad y obtención de detalles), vínculos, organización interactiva e información sobre herramientas. También puede agregar vínculos que permitan obtener detalles sobre los informes de Power BI u otros informes paginados de Power BI. Los vínculos pueden incluso saltar a otra ubicación dentro del mismo informe.
* **Suscripciones**: Power BI puede proporcionar informes paginados según una programación como correos electrónicos con datos adjuntos de informe en cualquier formato admitido.
* **Diseños por usuario**: Puede crear diseños de informe con gran capacidad de respuesta basados en el usuario autenticado que abre el informe. Puede diseñar el informe para filtrar los datos de manera diferente, ocultar las regiones de datos o visualizaciones, aplicar formatos diferentes o establecer valores predeterminados de parámetros específicos del usuario.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

* [¿Qué son los informes paginados en Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
* Guy in a cube (vídeo): [Presentación de los informes paginados en Power BI](https://www.youtube.com/watch?v=wfqn45XNK3M)
* [Migración de informes de SQL Server Reporting Services a Power BI](migrate-ssrs-reports-to-power-bi.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
* ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com)
