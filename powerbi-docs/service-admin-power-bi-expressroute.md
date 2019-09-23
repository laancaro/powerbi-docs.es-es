---
title: Power BI y ExpressRoute
description: Power BI y ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c7d12bf6a1a2a02c988f8351a1844be1080ad2b8
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074794"
---
# <a name="power-bi-and-expressroute"></a>Power BI y ExpressRoute

**ExpressRoute** es un servicio de Azure que le permite crear conexiones privadas entre centros de datos de Azure (donde reside Power BI) y la infraestructura local o entre centros de datos de Azure y su entorno de colocación.

Con **Power BI** y **ExpressRoute**, puede crear una conexión de red privada entre su organización y Power BI (o mediante una instalación de colocación del ISP), omitiendo Internet para proteger mejor las conexiones y los datos confidenciales de Power BI.

Para más información, consulte [Información general sobre ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI es compatible con ExpressRoute, con algunas excepciones en las que Power BI obtiene o envía datos a través de la red pública de Internet. Para ver una lista de las direcciones URL que Power BI usa, consulte [URL de Power BI](power-bi-whitelist-urls.md).

![Diagrama de ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)