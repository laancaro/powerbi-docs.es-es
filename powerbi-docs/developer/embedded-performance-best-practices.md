---
title: Procedimientos recomendados de rendimiento de Power BI Embedded
description: En este artículo se proporcionan instrucciones sobre los procedimientos recomendados de análisis integrado.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: e28801a15cf50351d737af63bc48f655ca85d28f
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008175"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Procedimientos recomendados de rendimiento de Power BI Embedded

En este artículo se proporcionan recomendaciones para un procesamiento más rápido de los informes, paneles e iconos de la aplicación.

## <a name="embed-parameters"></a>Insertar parámetros

El método Powerbi.embed() recibe pocos parámetros para insertar un informe, un panel o un icono. Estos parámetros tienen implicaciones en el rendimiento.

### <a name="embed-url"></a>Insertar URL

Evite generar usted mismo la dirección URL que se va a insertar. En su lugar, asegúrese de obtener la dirección URL de inserción mediante una llamada a las API [Obtener informes](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Freports%2Fgetreportsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=22lkqRM2w1MQfrM8dooedaPqqIU8PufTq9TT4VDzRo0%3D&reserved=0), [Obtener paneles](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgetdashboardsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=nfWRgbSoXVF42Rg%2Ba9491u19uksXp%2FAyz%2Fa%2Ba7%2FCtdA%3D&reserved=0) u [Obtener iconos](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgettilesingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256178318&sdata=LgZ27TynNpqQJDrb3aHWGQXIS%2FzichAO9De5M2uhF1Q%3D&reserved=0). Hemos agregado un parámetro nuevo a la dirección URL denominado  **_config_**, que se usa para mejorar el rendimiento.

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

* Use siempre la versión más reciente de [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

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
