---
title: Power BI y ExpressRoute
description: Power BI y ExpressRoute
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 59ddddcf1b02f07b850294fa314b7508f7f9fcdc
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856946"
---
# <a name="power-bi-and-expressroute"></a>Power BI y ExpressRoute

**ExpressRoute** es un servicio de Azure que le permite crear conexiones privadas entre centros de datos de Azure (donde reside Power BI) y la infraestructura local o entre centros de datos de Azure y su entorno de colocación.

Con **Power BI** y **ExpressRoute**, puede crear una conexión de red privada entre su organización y Power BI (o mediante una instalación de colocación del ISP), omitiendo Internet para proteger mejor las conexiones y los datos confidenciales de Power BI.

Para más información, consulte [Información general sobre ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI es compatible con ExpressRoute, con algunas excepciones en las que Power BI obtiene o envía datos a través de la red pública de Internet. Para ver una lista de las direcciones URL que Power BI usa, consulte [URL de Power BI](power-bi-whitelist-urls.md).

![Diagrama de ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)