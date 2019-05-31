---
title: Power BI y ExpressRoute
description: Power BI y ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0c4618150094a4eabb0dc9745e9ac93e4f342ff1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187897"
---
# <a name="power-bi-and-expressroute"></a>Power BI y ExpressRoute

**ExpressRoute** es un servicio de Azure que le permite crear conexiones privadas entre centros de datos de Azure (donde reside Power BI) y la infraestructura local o entre centros de datos de Azure y su entorno de colocación.

Con **Power BI** y **ExpressRoute**, puede crear una conexión de red privada entre su organización y Power BI (o mediante una instalación de colocación del ISP), omitiendo Internet para proteger mejor las conexiones y los datos confidenciales de Power BI.

Para más información, consulte [Información general sobre ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI es compatible con ExpressRoute, con algunas excepciones en las que Power BI obtiene o envía datos a través de la red pública de Internet. Para ver una lista de las direcciones URL que Power BI usa, consulte [URL de Power BI](power-bi-whitelist-urls.md).

![Diagrama de ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)