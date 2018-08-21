---
title: URL de Power BI
description: Los clientes que usen Power BI deben poder acceder a los puntos de conexión
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 8e29fa0c9471bb865619102247f38776208c3d87
ms.sourcegitcommit: 8990028a348b642ba5c96f001fe3a4280f0166ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "40101148"
---
# <a name="power-bi-urls"></a>URL de Power BI

**El servicio Power BI en línea**, también conocido como la aplicación de SaaS (software como servicio) de Power BI, requiere conectividad a Internet. Los clientes que usen el servicio Power BI en línea deben poder acceder a los puntos de conexión siguientes.

Para usar el servicio Power BI en línea, debe tener acceso para conectarse a los puntos de conexión marcados como **Obligatorio** en las tablas siguientes y los puntos de conexión marcados como **Obligatorio** en los sitios vinculados. Si el vínculo a un sitio externo hace referencia a una sección concreta, solo tiene que revisar los puntos de conexión de esa sección.

Los puntos de conexión marcados como **Opcional** también se pueden incluir en la **lista de permitidos** para que funcionen funcionalidades específicas.

El servicio Power BI en línea solo requiere que el puerto TCP 443 esté abierto para los puntos de conexión enumerados.

Los caracteres comodín (*) representan todos los niveles bajo el dominio raíz y usamos N/D cuando la información no está disponible. En la columna **Destinos**, se incluye una lista con FQDN, dominios y vínculos a sitios externos, que contienen más información sobre el punto de conexión.

>[!Important]
>La información de las tablas siguientes no representa la **nube del gobierno estadounidense**, **la nube de Alemania** ni **la nube de China**.

## <a name="authentication"></a>Autenticación

Power BI depende de los puntos de conexión requeridos en las secciones de identidad y autenticación de Office 365. Para usar Power BI, debe poder conectarse a los puntos de conexión en el sitio vinculado a continuación.

| Fila | Propósito | Destinos | Puertos |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatorio:** autenticación e identidad | Vea la sección [Autenticación e identidad de Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_identity) del sitio de la lista de permitidos de Office 365 | N/D |

## <a name="general-site-usage"></a>Uso del sitio general

Para usar Power BI de forma general, debe poder conectarse a los puntos de conexión de la tabla y los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatorio:** API de back-end | *.analysis.windows.net | TCP 443 |
| 2 | **Obligatorio:** integración de Office 365 | Vea la sección [Portal e infraestructura compartida de Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) en el sitio de la lista de permitidos de Office 365 | N/D |
| 3 | **Obligatorio:** portal | app.powerbi.com | TCP 443 |
| 4 | **Obligatorio:** telemetría de servicio | dc.services.visualstudio.com | TCP 443 |
| 5 | **Opcional:** mensajes informativos | dynmsg.modpim.com | TCP 443 |
| 6 | **Opcional:** encuestas NPS | nps.onyx.azure.net | TCP 443 |

## <a name="administration"></a>Administración

Para realizar funciones administrativas en Power BI, debe poder conectarse a los puntos de conexión en los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatorio:** para administrar usuarios y ver los registros de auditoría | Vea la sección [Portal e infraestructura compartida de Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) en el sitio de la lista de permitidos de Office 365 | N/D |

## <a name="get-data"></a>Obtener datos

Para poder obtener datos de orígenes de datos específicos, como OneDrive, debe poder conectarse a los puntos de conexión de la tabla siguiente.

| Fila | Propósito | Destinos | Puertos |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatorio:** AppSource (aplicaciones internas o externas en Power BI) | appsource.microsoft.com | TCP 443 |
| 2 | **Opcional:** importar archivos desde OneDrive personal | Vea el sitio [Required URLs and ports for OneDrive](https://support.office.com/en-ie/article/required-urls-and-ports-for-onedrive-ce15d2cc-52ef-42cd-b738-d9c6f9b03f3a) (Direcciones y puertos requeridos para OneDrive) | N/D |
| 3 | **Opcional:** vídeo del tutorial de Power BI en 60 segundos | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 4 | **Opcional:** orígenes de datos de streaming de PubNub | Vea la [documentación de PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |

## <a name="dashboard-and-report-integration"></a>Integración de paneles e informes 

Power BI depende de determinados puntos de conexión para poder admitir los paneles e informes. Debe poder conectarse a los puntos de conexión de la tabla y los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatorio:** integración de Excel | Vea la sección [Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) en el sitio de la lista de permitidos de Office 365 | N/D |

## <a name="custom-visuals"></a>Objetos visuales personalizados

Power BI depende de determinados puntos de conexión para poder ver y acceder a los objetos visuales personalizados. Debe poder conectarse a los puntos de conexión de la tabla y los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatorio:** importar un objeto visual personalizado desde la interfaz de Marketplace y un archivo | *.microsoft.com </br> *.bing.com </br> *.msecnd.net </br> *.osi.office.net </br> *.azureedge.net </br> ajax.aspnetcdn.com </br> nexus.ensighten.com </br> store.office.com | TCP 443 |
| 2 | **Opcional:** mapas de Bing | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Vea la sección [Servicios requeridos](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) del sitio de requisitos del sistema de PowerApps | N/D |
| 4 | **Opcional:** Visio | Vea la sección [Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) en el sitio de la lista de permitidos de Office 365 | N/D |