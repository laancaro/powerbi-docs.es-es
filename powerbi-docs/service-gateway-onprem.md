---
title: Puerta de enlace de datos local
description: Esta es información general acerca de la puerta de enlace de datos local para Power BI. Puede usar esta puerta de enlace para trabajar con orígenes de datos DirectQuery. También puede usar esta puerta de enlace para actualizar conjuntos de datos en la nube con datos locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 57c4292913a2056ab285716de1e1b83e2313f723
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307096"
---
# <a name="what-is-an-on-premises-data-gateway"></a>¿Qué es una puerta de enlace de datos local?

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

La puerta de enlace de datos local actúa como un puente, para proporcionar una transferencia de datos rápida y segura entre los datos locales (los que no están en la nube) y varios servicios en la nube de Microsoft, incluidos Power BI, PowerApps, Microsoft Flow, Azure Analysis Services y Logic Apps. Al usar una puerta de enlace, las organizaciones pueden mantener bases de datos y otros orígenes de datos en sus redes locales, pero usar de forma segura esos datos locales en servicios en la nube.

## <a name="how-the-gateway-works"></a>Cómo funciona la puerta de enlace

![Información general de la puerta de enlace](media/service-gateway-onprem/on-premises-data-gateway.png)

Para obtener información detallada sobre cómo funciona la puerta de enlace, vea [Arquitectura de puerta de enlace de datos local](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Tipos de puertas de enlace

Hay dos tipos de puertas de enlace diferentes, cada una para un escenario distinto:

* **Puerta de enlace de datos local**: permite que varios usuarios se conecten a varios orígenes de datos locales. Puede usar una puerta de enlace de datos local con todos los servicios admitidos, con una sola instalación de puerta de enlace. Esta puerta de enlace está diseñada especialmente para escenarios complejos en los que varios usuarios acceden a varios orígenes de datos.

* **Puerta de enlace de datos local (modo personal)** : permite que un usuario se conecte a los orígenes y no pueda compartirlos con otros usuarios. Una puerta de enlace de datos local (modo personal) solo se puede usar con Power BI. Esta puerta de enlace está diseñada especialmente para los escenarios en los que usted es el único que crea informes y no necesita compartir ningún origen de datos con otros usuarios.

## <a name="using-a-gateway"></a>Uso de una puerta de enlace

Hay cuatro pasos principales para usar una puerta de enlace:

1. [Descargar e instalar la puerta de enlace](/data-integration/gateway/service-gateway-install) en un equipo local.
2. [Configurar](/data-integration/gateway/service-gateway-app) la puerta de enlace según el firewall y otros requisitos de red.
3. [Agregar administradores de puerta de enlace](/data-integration/gateway/service-gateway-manage) que también pueden otros requisitos de red.
4. [Solucionar los problemas](service-gateway-onprem-tshoot.md) de la puerta de enlace en caso de errores.

## <a name="next-steps"></a>Pasos siguientes

* [Instalación de la puerta de enlace de datos local](/data-integration/gateway/service-gateway-install)


¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
