---
title: Introducción a los paneles para los diseñadores de Power BI
description: Los paneles son una característica clave del servicio Power BI. Incluyen una única página, que se suele denominar lienzo, que cuenta una historia mediante visualizaciones.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/17/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 7ee083de9800b55c4f7d998a113c1a63df112b7b
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68624023"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Introducción a los paneles para los diseñadores de Power BI

Un *panel* de Power BI incluye una única página, que se suele denominar lienzo, que cuenta una historia mediante visualizaciones. Dado que se limita a una sola página, un panel bien diseñado contiene únicamente los elementos destacados de esa historia. Los lectores pueden ver informes relacionados para conocer los detalles.

![Panel](media/service-dashboards/power-bi-dashboard2.png)

Los paneles son una característica exclusiva del servicio Power BI. y no están disponibles en Power BI Desktop. Aunque no se pueden crear paneles en dispositivos móviles, puede [verlos y compartirlos](mobile-apps-view-dashboard.md) desde allí.

## <a name="dashboard-basics"></a>Conceptos básicos de los paneles 

Las visualizaciones que se ven en el panel se denominan *iconos*. Puede *anclar* iconos a un panel desde informes. Si no está familiarizado con Power BI, puede obtener una buena base si lee [Basic concepts for designers in the Power BI service](service-basic-concepts.md) (Conceptos básicos para diseñadores del servicio Power BI).

> [!IMPORTANT]
> Necesita una licencia de [Power BI Pro](service-free-vs-pro.md) para crear paneles.

Las visualizaciones de un panel proceden de informes y cada informe se basa en un conjunto de datos. Una manera de pensar en un panel es como vía de entrada a los informes y conjuntos de datos subyacentes. Si selecciona una visualización, se le dirige al informe (y al conjunto de datos) en el que se basa.

![Diagrama que muestra la relación entre paneles, informes y conjuntos de datos](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Ventajas de los paneles
Los paneles son una magnífica manera de supervisar su empresa y ver las métricas más importantes de un vistazo. Las visualizaciones de un panel pueden proceder de un conjunto de datos subyacente o de varios, y de un informe subyacente o de varios. Un panel combina datos locales y en la nube, lo que proporciona una vista consolidada, independientemente de dónde residen los datos.

Un panel no es simplemente una foto bonita. Es muy interactivo y los iconos se actualizan según cambian los datos subyacentes.

## <a name="dashboards-versus-reports"></a>Paneles frente a informes
Los [informes](service-reports.md) y los paneles parecen similares, porque ambos son lienzos con visualizaciones, Pero hay diferencias importantes, como puede ver en la tabla siguiente.

| **Funcionalidad** | **Paneles** | **Informes** |
| --- | --- | --- |
| Páginas |Una página |Una o varias páginas |
| Orígenes de datos |Uno o varios informes y uno o varios conjuntos de datos por cada panel |Un único conjunto de datos por informe |
| Disponible en Power BI Desktop |No | Sí. Pueden generar y ver informes en Power BI Desktop |
| Suscribirse |Sí. Es posible suscribirse a un panel |Sí. Es posible suscribirse a una página del informe |
| Filtrado |No. No es posible filtrar ni segmentar |Sí. Numerosas formas de filtrar, resaltar y segmentar |
| Destacado |Sí. Se puede definir un panel como *destacado* |No |
| Favorito | Sí. Se pueden definir varios paneles como *favoritos* | Sí. Se pueden definir varios informes como *favoritos*
| Establecimiento de alertas |Sí. Disponible para iconos de panel en determinadas circunstancias |No |
| Consultas en lenguaje natural |Sí | Sí, siempre que tenga permisos de edición para el informe y el conjunto de datos subyacente |
| Se pueden ver campos y tablas del conjunto de datos subyacentes |No. Se pueden exportar datos, pero no se pueden ver tablas ni campos en el propio panel |Sí |


## <a name="next-steps"></a>Pasos siguientes
* Familiarícese con los paneles viendo uno de nuestros [paneles de ejemplo](sample-tutorial-connect-to-the-samples.md).
* Obtenga información sobre los [iconos del panel](service-dashboard-tiles.md).
* ¿Desea realizar un seguimiento de un icono de panel individual y recibir un mensaje de correo electrónico al alcanzar un umbral determinado? [Cree una alerta en un icono](service-set-data-alerts.md).
* Aprenda a utilizar [Preguntas y respuestas de Power BI](power-bi-tutorial-q-and-a.md) para formular una pregunta sobre los datos y recibir una respuesta en forma de visualización.
