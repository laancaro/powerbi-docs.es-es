---
title: Power BI y ExpressRoute
description: Power BI y ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 62289c974e25207f3a991e7f17a0ee965c729b8a
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900138"
---
# <a name="power-bi-and-expressroute"></a>Power BI y ExpressRoute

**ExpressRoute** es un servicio de Azure que le permite crear conexiones privadas entre centros de datos de Azure (donde reside Power BI) y la infraestructura local o entre centros de datos de Azure y su entorno de colocación.

Con **Power BI** y **ExpressRoute**, puede crear una conexión de red privada entre su organización y Power BI (o mediante una instalación de colocación del ISP), omitiendo Internet para proteger mejor las conexiones y los datos confidenciales de Power BI.

Para más información, consulte [Información general sobre ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI es compatible con ExpressRoute, con algunas excepciones en las que Power BI obtiene o envía datos a través de la red pública de Internet. Para ver una lista de las direcciones URL que Power BI usa, consulte [URL de Power BI](power-bi-whitelist-urls.md).

![Diagrama de ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)