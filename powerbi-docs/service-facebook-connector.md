---
title: 'Servicio de terceros: Conector de Facebook para Power BI Desktop'
description: 'Servicio de terceros: Conector de Facebook para Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 644e68ec827915c5457e22e1c1486a8f6f3299f6
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "73877038"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Conector de Facebook para Power BI Desktop
El conector de Facebook en **Power BI Desktop** se basa en la API Graph de Facebook. Por lo tanto, las características y la disponibilidad pueden variar con el tiempo.

Puede ver un [tutorial acerca del conector de Facebook para Power BI Desktop](desktop-tutorial-facebook-analytics.md).

El 30 de abril de 2015 caducó la versión v1.0 de Graph API en Facebook. Power BI usa la API Graph en segundo plano para el conector de Facebook, lo que le permite conectarse a los datos y analizarlos.

Es posible que las consultas que se crearon antes del 30 de abril de 2015 ya no funcionen o que devuelvan menos datos. A partir del 30 de abril de 2015, Power BI usa v2.8 en todas las llamadas a la API de Facebook. Si la consulta se creó antes del 30 de abril de 2015 y no la ha usado desde entonces, probablemente tendrá que volver a autenticarse para aprobar el nuevo conjunto de permisos que se pedirá.

Aunque intentamos sacar actualizaciones para cualquier cambio, la API puede cambiar de manera que afectE a los resultados de las consultas que generamos. En algunos casos, puede que ya no se admitan determinadas consultas. Debido a esta dependencia, no podemos garantizar los resultados de las consultas cuando se usa este conector.

Para más detalles sobre el cambio en la API de Facebook acuda [aquí](https://developers.facebook.com/docs/apps/changelog#v2_0).

