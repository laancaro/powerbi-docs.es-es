---
title: Procedimientos recomendados de rendimiento de Power BI Embedded
description: En este artículo se proporcionan instrucciones sobre los procedimientos recomendados de análisis integrado.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: d2e4a29b3dd7e36081458ff6ca51b0006a10466f
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750941"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Procedimientos recomendados de rendimiento de Power BI Embedded

En este artículo se proporcionan recomendaciones para un procesamiento más rápido de los informes, paneles e iconos de la aplicación.

## <a name="embed-parameters"></a>Insertar parámetros

El método Powerbi.embed() recibe pocos parámetros para insertar un informe, un panel o un icono. Estos parámetros tienen implicaciones en el rendimiento.

### <a name="embed-url"></a>Insertar URL

Evite generar usted mismo la dirección URL que se va a insertar. En su lugar, asegúrese de obtener la dirección URL de inserción mediante una llamada a las API [Obtener informes](/rest/api/power-bi/reports/getreportsingroup), [Obtener paneles](/rest/api/power-bi/dashboards/getdashboardsingroup) u [Obtener iconos](/rest/api/power-bi/dashboards/gettilesingroup). Hemos agregado un parámetro nuevo a la dirección URL denominado  **_config_** , que se usa para mejorar el rendimiento.

### <a name="permissions"></a>Permisos

Proporcione permisos de **visualización** si no tiene previsto insertar un informe en el **modo de edición**. De este modo, el código para insertar no inicializa los componentes que se usan para el modo de edición.

### <a name="filters-bookmarks-and-slicers"></a>Filtros, marcadores y segmentaciones

Por lo general, los objetos visuales de los informes se guardan con los datos almacenados en caché. Los datos en caché se usan para dar la percepción de rendimiento. Los informes representan los datos en caché mientras se ejecutan las consultas. Si se proporcionan filtros, marcadores o segmentaciones, los datos en caché no son pertinentes. Por tanto, los objetos visuales solo se representan después de ejecutar la consulta del objeto visual.

Si inserta los informes con los mismos filtros para evitar pasar una lista de filtros en la configuración de carga, guarde el informe con los filtros ya aplicados.

## <a name="preload"></a>Carga previa

Use la API *preload* de JavaScript para mejorar el rendimiento del usuario final.
Powerbi.preload() descarga JavaScript, archivos CSS y otros artefactos que se usan posteriormente para su inserción en un informe.

Llame a preload si no va a insertar el informe inmediatamente. Por ejemplo, si inserta un informe en un clic de botón, es mejor llamar a preload cuando se carga la página anterior. De este modo, cuando el usuario de la aplicación hace clic en el botón, el procesamiento es más rápido.

## <a name="measure-performance"></a>Medir el rendimiento

Para medir el rendimiento, use:

1. Cargado: tiempo hasta que se inicializa el informe (el usuario no ve la rueda de espera).
2. Representado: tiempo hasta que representa por completo el informe con datos reales. El evento representado se desencadena cada vez que se vuelve a representar el informe (es decir, después aplicar filtros). Para medir primero un informe, asegúrese de que realiza los cálculos en el primer evento generado.

Los datos en caché se representan cuando están disponibles, pero aún no tenemos un evento para estos datos.

## <a name="update-tools-and-sdk-packages"></a>Actualizar herramientas y paquetes SDK

Mantenga actualizadas las herramientas y los paquetes SDK.

* Use siempre la versión más reciente de [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Instale la versión más reciente del [SDK de cliente de Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Seguimos publicando más mejoras, así que asegúrese de hacer un seguimiento de vez en cuando.

* Paquetes que hay que instalar:
    * Paquete Npm: powerbi-client
    * Paquete NuGet: Microsoft.PowerBI.JavaScript

> [!Note]
> Recuerde que el tiempo de carga depende principalmente de los elementos pertinentes para el informe y los propios datos. Por ejemplo, el número de objetos visuales, el tamaño de los datos y la complejidad de las consultas y las medidas calculadas. Siga los [procedimientos recomendados](../power-bi-reports-performance.md) para mejorar el tiempo de carga del informe.

## <a name="next-steps"></a>Pasos siguientes

* [Procedimientos recomendados de rendimiento de Power BI](../power-bi-reports-performance.md)
* [Cómo solucionar problemas de Power BI Embedded](embedded-troubleshoot.md)
* [Preguntas frecuentes sobre Power BI Embedded](embedded-faq.md)
