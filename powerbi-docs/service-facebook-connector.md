---
title: 'Servicio de terceros: Conector de Facebook para Power BI Desktop'
description: 'Servicio de terceros: Conector de Facebook para Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527711"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Uso del conector de Facebook para Power BI Desktop
El conector de Facebook en **Power BI Desktop** se basa en la API Graph de Facebook. Por lo tanto, las características y la disponibilidad pueden variar con el tiempo.

Puede ver un [tutorial acerca del conector de Facebook para Power BI Desktop](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Aviso de desuso del conector de datos de Facebook:** la importación y actualización de datos desde Facebook en Excel dejará de funcionar correctamente en abril de 2020. Hasta entonces, puede usar el conector de Facebook *Obtener y transformar (Power Query)* . Después de esa fecha, no podrá conectarse a Facebook y recibirá un mensaje de error. Se recomienda revisar o quitar las consultas *Obtener y transformar (Power Query)* existentes que usan el conector de Facebook lo antes posible para evitar resultados inesperados.


El 30 de abril de 2015 caducó la versión v1.0 de Graph API en Facebook. Power BI usa la API Graph en segundo plano para el conector de Facebook, lo que le permite conectarse a los datos y analizarlos.

Es posible que las consultas que se crearon antes del 30 de abril de 2015 ya no funcionen o que devuelvan menos datos. A partir del 30 de abril de 2015, Power BI usa v2.8 en todas las llamadas a la API de Facebook. Si la consulta se creó antes del 30 de abril de 2015 y no la ha usado desde entonces, probablemente tendrá que volver a autenticarse para aprobar el nuevo conjunto de permisos que se pedirá.

Aunque intentamos sacar actualizaciones para cualquier cambio, la API puede cambiar de manera que afectE a los resultados de las consultas que generamos. En algunos casos, puede que ya no se admitan determinadas consultas. Debido a esta dependencia, no podemos garantizar los resultados de las consultas cuando se usa este conector.

Para más detalles sobre el cambio en la API de Facebook acuda [aquí](https://developers.facebook.com/docs/apps/changelog#v2_0).

