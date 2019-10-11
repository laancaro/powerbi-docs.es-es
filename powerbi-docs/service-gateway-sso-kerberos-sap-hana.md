---
title: Uso de Kerberos para el inicio de sesión único (SSO) en SAP HANA
description: Configuración del servidor de SAP HANA para habilitar el SSO del servicio Power BI
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9e7bdb0ae2f1e512e3e431cf69395d601cbc7b3f
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968527"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Uso de Kerberos para el inicio de sesión único (SSO) en SAP HANA

En este artículo se describe cómo configurar el origen de datos SAP HANA para habilitar el SSO del servicio Power BI.

> [!NOTE]
> Complete los pasos de este artículo junto con los pasos de [configuración del SSO de Kerberos](service-gateway-sso-kerberos.md) antes de intentar actualizar un informe basado en SAP HANA que use el SSO de Kerberos.

## <a name="enable-sso-for-sap-hana"></a>Habilitación del SSO para SAP HANA

Para habilitar el SSO para SAP HANA, siga estos pasos:

* Asegúrese de que el servidor de SAP HANA ejecuta la versión mínima requerida, que depende del nivel de plataforma de su servidor de SAP HANA:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* En el equipo de puerta de enlace, instale el controlador ODBC de HANA más reciente de SAP.  La versión mínima es HANA ODBC versión 2.00.020.00, de agosto de 2017.

Asegúrese de que el servidor de SAP HANA se haya configurado para el SSO basado en Kerberos. Para obtener más información sobre cómo configurar SSO para SAP HANA mediante Kerberos, vea [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Inicio de sesión único con Kerberos) en la Guía de seguridad de SAP HANA. Consulte también los vínculos de esa página, en particular SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

También se recomienda seguir estos pasos adicionales, que pueden comportar una pequeña mejora de rendimiento.

1. En el directorio de instalación de la puerta de enlace, busque y abra este archivo de configuración: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

2. Busque la propiedad *FullDomainResolutionEnabled* y cambie su valor a *True*.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Ahora, [ejecute un informe de Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Pasos siguientes

Para más información acerca de la **puerta de enlace de datos local** y **DirectQuery**, consulte los recursos siguientes:

* [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
