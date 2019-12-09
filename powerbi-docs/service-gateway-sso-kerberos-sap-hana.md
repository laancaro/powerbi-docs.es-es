---
title: Uso de Kerberos para el inicio de sesión único (SSO) en SAP HANA
description: Configuración del servidor de SAP HANA para habilitar el SSO del servicio Power BI
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9c2eb554a4e3b3ec90d3fe17145e0ec277298e1b
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74697506"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Uso de Kerberos para el inicio de sesión único (SSO) en SAP HANA

En este artículo se describe cómo configurar el origen de datos SAP HANA para habilitar el SSO del servicio Power BI.

> [!NOTE]
> Antes de intentar actualizar un informe basado en SAP HANA que usa el inicio de sesión único de Kerberos, complete los dos pasos de este artículo y los de [Configuración del inicio de sesión único de Kerberos](service-gateway-sso-kerberos.md).

## <a name="enable-sso-for-sap-hana"></a>Habilitación del SSO para SAP HANA

Para habilitar el SSO para SAP HANA, siga estos pasos:

1. Asegúrese de que el servidor de SAP HANA ejecuta la versión mínima requerida, que depende del nivel de plataforma de su servidor de SAP HANA:
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. En la máquina de puerta de enlace, instale el controlador ODBC de SAP HANA más reciente. La versión mínima es HANA ODBC versión 2.00.020.00, de agosto de 2017.

3. Asegúrese de que el servidor de SAP HANA se haya configurado para el SSO basado en Kerberos. Para obtener más información sobre cómo configurar SSO para SAP HANA mediante Kerberos, vea [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Inicio de sesión único con Kerberos) en la Guía de seguridad de SAP HANA. Consulte también los vínculos de esa página, en particular SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

También se recomienda seguir estos pasos adicionales, que pueden comportar una pequeña mejora de rendimiento:

1. En el directorio de instalación de la puerta de enlace, busque y abra este archivo de configuración: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Busque la propiedad `FullDomainResolutionEnabled` y cambie su valor a `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Ahora, [ejecute un informe de Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la puerta de enlace de datos local y DirectQuery, consulte los recursos siguientes:

* [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
