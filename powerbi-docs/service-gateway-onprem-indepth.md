---
title: Detalles sobre la puerta de enlace de datos local
description: En este artículo se examina la puerta de enlace global en profundidad. Describe cómo funciona el servicio con Azure Active Directory y Active Directory local cuando se trabaja con Analysis Services
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: e8807feeccccebab8837ac571ae4340c5c0c9b1a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881591"
---
# <a name="on-premises-data-gateway-in-depth"></a>Detalles sobre la puerta de enlace de datos local

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

La información de este artículo se ha migrado a varios artículos de la documentación de Power BI y general. Siga los vínculos de cada encabezado para buscar el contenido pertinente.

## <a name="how-the-gateway-works"></a>Cómo funciona la puerta de enlace

Vea [Arquitectura de puerta de enlace de datos local](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Lista de tipos de orígenes de datos disponibles

Vea [Administración de orígenes de datos](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Autenticación para orígenes de datos locales

Vea [Autenticación para orígenes de datos locales](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticación a un origen de datos de Analysis Services activo

Vea [Autenticación a un origen de datos de Analysis Services activo](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Seguridad basada en roles

Vea [Seguridad basada en roles](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Seguridad de nivel de fila

Vea [Seguridad de nivel de fila](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>¿Qué pasa con Azure Active Directory?

Vea [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>¿Cómo sé cuál es mi UPN?

Vea [¿Cómo sé cuál es mi UPN?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Asignación de nombres de usuario a orígenes de datos de Analysis Services

Vea [Asignación de nombres de usuario a orígenes de datos de Analysis Services](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizar un servidor de Active Directory local con Azure Active Directory

Vea [Sincronización de un servidor de Active Directory local con Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>¿Qué hacer a continuación?

Vea los artículos sobre orígenes de datos:

[Administración de orígenes de datos](service-gateway-data-sources.md)
[Administrar el origen de datos: Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Administrar el origen de datos: SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Administrar el origen de datos: SQL Server](service-gateway-enterprise-manage-sql.md)  
[Administrar el origen de datos: Oracle](service-gateway-onprem-manage-oracle.md)  
[Administrar el origen de datos: importación o actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Posibles problemas

Vea [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot) y [Solución de problemas de puertas de enlace: Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Cuenta de inicio de sesión

Vea [Cuenta de inicio de sesión](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Cuenta de servicio de Windows

Vea [Cambio de la cuenta de servicio de puerta de enlace de datos local](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Puertos

Vea [Puertos](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forzar la comunicación HTTPS con Azure Service Bus

Vea [Aplicación forzosa de comunicación HTTPS con Azure Service Bus](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Compatibilidad con TLS 1.2

Vea [TLS 1.2 para el tráfico de puerta de enlace](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Cómo reiniciar la puerta de enlace

Vea [Reinicio de una puerta de enlace](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Pasos siguientes

[¿Qué es la puerta de enlace de datos local?](service-gateway-onprem.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)