---
title: Almacenamiento en caché de consultas en Power BI Premium
description: Almacenamiento en caché de consultas en Power BI Premium
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: c981a3e2a05129a470c8d26675226bfb42c1bb68
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769538"
---
# <a name="query-caching-in-power-bi-premium"></a>Almacenamiento en caché de consultas en Power BI Premium

Las organizaciones con Power BI Premium pueden sacar partido del *almacenamiento en caché de consultas* para acelerar los informes asociados a un conjunto de datos. El almacenamiento en caché de consultas indica a la capacidad Premium que use su servicio de almacenamiento en caché local para mantener los resultados de la consulta, lo que evita que el origen de datos subyacente tenga que calcular esos resultados.

> [!IMPORTANT]
> El almacenamiento en caché de consultas solo está disponible en Power BI Premium. No es aplicable a los conjuntos de datos de LiveConnect que aprovechan Azure Analysis Services o SQL Server Analysis Services.

Los resultados de las consultas almacenadas en caché son específicos del usuario y el contexto del conjunto de datos, y siempre respetan las reglas de seguridad. En este momento, el servicio solo realiza el almacenamiento de consultas de la página inicial en la que se entra. En otras palabras, las consultas no se almacenan en caché cuando se interactúa con el informe. La caché refleja los marcadores personales y los filtros persistentes. Los [iconos de panel](service-dashboard-tiles.md) que funcionan con las mismas consultas también aprovechan las consultas una vez almacenadas en caché. El rendimiento mejora especialmente cuando se accede con frecuencia a un conjunto de datos que no es necesario actualizar a menudo. El almacenamiento en caché de consultas puede además reducir la carga sobre la capacidad Premium al reducir el número total de consultas.

El comportamiento del almacenamiento en caché se controla en la página **Configuración** del conjunto de datos del servicio Power BI. Tiene dos configuraciones posibles:

- **Desactivado**: No se usa el almacenamiento en caché de consultas para este conjunto de datos.

- **Activado**: Se usa el almacenamiento en caché de consultas para este conjunto de datos.

![Cuadro de diálogo Caché de consultas](media/power-bi-query-caching/power-bi-query-caching.png)

> [!NOTE]
> Al cambiar la configuración de almacenamiento en caché de **Activado** a **Desactivado**, todos los resultados de la consulta del conjunto de datos guardados se quitan de la caché de capacidad. Puede desactivar el almacenamiento en caché ya sea explícitamente o revirtiendo a la configuración predeterminada de capacidad que un administrador haya establecido en **Desactivado**. La desactivación de esta opción puede introducir un pequeño retraso la próxima vez que un informe ejecute consultas en este conjunto de datos. El retraso se debe a que las consultas de informes se ejecutan a petición y no aprovechan los resultados guardados. Además, es posible que primero haya que cargar en memoria el conjunto de datos necesario para que pueda atender consultas.


