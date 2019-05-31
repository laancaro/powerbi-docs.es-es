---
title: Direcciones URL de Power BI para la inclusión en listas blancas
description: En este artículo se describen los puntos de conexión a los cuales deben poder acceder los clientes que usan Power BI.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/22/2018
ms.custom: seodec18
ms.openlocfilehash: 07441bd0446e37353984efe97e435ac83d2c355d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "60978382"
---
# <a name="power-bi-urls-for-whitelisting"></a>Direcciones URL de Power BI para la inclusión en listas blancas

**El servicio Power BI en línea**, también conocido como la aplicación de SaaS (software como servicio) de Power BI, requiere conectividad a internet. Los clientes que usen el servicio Power BI en línea deben poder acceder a los puntos de conexión siguientes.

Para usar el servicio Power BI en línea, debe tener acceso para conectarse a los puntos de conexión marcados como **Obligatorio** en las tablas siguientes y los puntos de conexión marcados como **Obligatorio** en los sitios vinculados. Si el vínculo a un sitio externo hace referencia a una sección concreta, solo tiene que revisar los puntos de conexión de esa sección.

Los puntos de conexión marcados como **Opcional** también se pueden incluir en la **lista de permitidos** para que funcionen funcionalidades específicas.

El servicio Power BI en línea solo requiere que el puerto TCP 443 esté abierto para los puntos de conexión enumerados.

Los caracteres comodín (*) representan todos los niveles bajo el dominio raíz y usamos N/D cuando la información no está disponible. En la columna **Destinos**, se incluye una lista con FQDN, dominios y vínculos a sitios externos, que contienen más información sobre el punto de conexión.

>[!Important]
>La información de las tablas siguientes no representa la **nube del gobierno estadounidense**, **la nube de Alemania** ni **la nube de China**.

## <a name="authentication"></a>Autenticación

Power BI depende de los puntos de conexión requeridos en las secciones de identidad y autenticación de Office 365. Para usar Power BI, debe poder conectarse a los puntos de conexión en el sitio vinculado a continuación.

| Fila | Propósito | Destinos | Puertos |
| --- | --- | --- | --- |
| 1 | **Obligatorio:** autenticación e identidad | Consulte la documentación de Office 365 para [Office Online y las URL comunes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N/D |

## <a name="general-site-usage"></a>Uso del sitio general

Para usar Power BI de forma general, debe poder conectarse a los puntos de conexión de la tabla y los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
| --- | --- | --- | --- |
| 1 | **Obligatorio:** API de back-end | *.analysis.windows.net | TCP 443 |
| 2 | **Obligatorio:** integración de Office 365 | Consulte la documentación de Office 365 para [Office Online y las URL comunes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| 3 | **Obligatorio:** Portal | app.powerbi.com | TCP 443 |
| 4 | **Obligatorio:** telemetría de servicio | dc.services.visualstudio.com | TCP 443 |
| 5 | **Opcional:** mensajes informativos | dynmsg.modpim.com | TCP 443 |
| 6 | **Opcional:** encuestas de NPS | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administración

Para realizar funciones administrativas en Power BI, debe poder conectarse a los puntos de conexión en los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
| --- | --- | --- | --- |
| 1 | **Obligatorio:** para administrar usuarios y ver los registros de auditoría | Consulte la documentación de Office 365 para [Office Online y las URL comunes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="getting-data"></a>Obtención de datos

Para obtener datos de orígenes de datos específicos, como OneDrive, debe poder conectarse a los puntos de conexión de la tabla siguiente. Puede ser necesario tener acceso a dominios de internet y URL adicionales para orígenes de datos específicos utilizados en su organización.

| Fila | Propósito | Destinos | Puertos |
| --- | --- | --- | --- |
| 1 | **Obligatorio:** AppSource (aplicaciones internas o externas en Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Opcional:** iniciar sesión y obtener datos para los paquetes de contenido | En función de los paquetes de contenido utilizados | En función de los paquetes de contenido utilizados |
| 3 | **Opcional:** importar archivos desde OneDrive Personal | Vea el sitio [Required URLs and ports for OneDrive](https://docs.microsoft.com/onedrive/required-urls-and-ports) (Direcciones y puertos requeridos para OneDrive) | N/D |
| 4 | **Opcional:** vídeo tutorial de Power BI en 60 segundos | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Opcional:** orígenes de datos de streaming de PubNub | Vea la [documentación de PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |
| | | |

## <a name="dashboard-and-report-integration"></a>Integración de paneles e informes

Power BI depende de determinados puntos de conexión para poder admitir los paneles e informes. Debe poder conectarse a los puntos de conexión de la tabla y los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
| --- | --- | --- | --- |
| 1 | **Obligatorio:** integración de Excel | Consulte la documentación de Office 365 para [Office Online y las URL comunes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="custom-visuals"></a>Objetos visuales personalizados

Power BI depende de determinados puntos de conexión para poder ver y acceder a los objetos visuales personalizados. Debe poder conectarse a los puntos de conexión de la tabla y los sitios vinculados a continuación.

| Fila | Propósito | Destinos | Puertos |
| --- | --- | --- | --- |
| 1 | **Obligatorio:** importar un objeto visual personalizado desde la interfaz de Marketplace o desde un archivo | *.azureedge.net <br> *.blob.core.windows.net <br> store.office.com | TCP 443 |
| 2 | **Opcional:** Mapas de Bing | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Vea la sección [Servicios requeridos](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) del sitio de requisitos del sistema de PowerApps | N/D |
| 4 | **Opcional:** Visio | Consulte la documentación de Office 365 para [Office Online y URL comunes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), así como [SharePoint Online y OneDrive para la Empresa](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N/D |
| | | |

## <a name="related-external-sites"></a>Sitios externos relacionados

Vínculos de Power BI a otros sitios relacionados. Estos sitios incluyen los de documentación, soporte técnico, solicitudes de nuevas funciones, etc. Estos sitios no afectarán a la funcionalidad de Power BI, por lo que, si quiere, puede ponerlos en la lista de permitidos.

| Fila | Propósito | Destinos | Puertos |
| --- | --- | --- | --- |
| 1 | **Opcional:** sitio de la Comunidad | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Opcional:** Sitio de documentación | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Opcional:** sitio de descarga (para Power BI Desktop, etc.) | download.microsoft.com | TCP 443 |
| 4 | **Opcional:** redirecciones externas | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Opcional:** sitio de comentarios de ideas| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Opcional:** sitio de Power BI: página de inicio, vínculos de más información, sitio de soporte técnico, vínculos de descarga, presentación de asociados, etc. | powerbi.microsoft.com | TCP 443 |
| 7 | **Opcional:** Centro para desarrolladores de Power BI | dev.powerbi.com | TCP 443 |
| 8 | **Opcional:** sitio de soporte técnico | support.powerbi.com <br> s3.amazonaws.com <br> *. olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |