---
title: Uso de conectores de datos personalizados con la puerta de enlace de datos local
description: Puede usar conectores de datos personalizados con la puerta de enlace de datos local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 074a8dd876e0612f87c220f9fb077b60b2b85c88
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271804"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Uso de conectores de datos personalizados con la puerta de enlace de datos local

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Los conectores de datos de Power BI le permiten conectarse y tener acceso a datos desde un origen de datos, servicio o aplicación. Puede desarrollar conectores de datos personalizados y usarlos en Power BI Desktop.

Para más información sobre cómo desarrollar conectores de datos personalizados para Power BI, consulte la [página del SDK de conector de datos en GitHub](http://aka.ms/dataconnectors). En este sitio se incluye información de introducción y ejemplos para Power BI y Power Query.

Al compilar informes en Power BI Desktop en los que se usan conectores de datos personalizados, puede utilizar la puerta de enlace de datos local para actualizar esos informes desde el servicio Power BI.

## <a name="how-to-enable-and-use-this-capability"></a>Procedimientos para habilitar y usar esta funcionalidad

Al instalar la versión de julio de 2018 de la puerta de enlace de datos local o una versión posterior, puede ver una pestaña **Conectores** en la aplicación de puerta de enlace de datos local, con una opción para elegir una carpeta desde la que cargar los conectores personalizados. Asegúrese de seleccionar una carpeta a la que pueda acceder el usuario que ejecuta el servicio de puerta de enlace (que es *NT SERVICE\PBIEgwService* de forma predeterminada). La puerta de enlace carga de forma automática los archivos de conector personalizados que se encuentran en esa carpeta y podrá verlos en la lista de conectores de datos.

![Conector personalizado 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Si usa la puerta de enlace de datos local (modo personal), en este momento podrá cargar el informe de Power BI en el servicio Power BI y usar la puerta de enlace para actualizarlo.

Para la puerta de enlace de datos, todavía tendrá que crear un origen de datos para el conector personalizado. En la página de configuración de la puerta de enlace en el servicio Power BI, debería ver una nueva opción al seleccionar el clúster de puerta de enlace para permitir el uso de conectores personalizados con este clúster. Asegúrese de que todas las puertas de enlace del clúster tienen la versión de actualización de julio de 2018 o una posterior para que esta opción esté disponible. Ahora, seleccione esa opción para habilitar el uso de conectores personalizados con este clúster.

![Conector personalizado 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Cuando esta opción esté habilitada, verá los conectores personalizados como orígenes de datos disponibles que se pueden crear en este clúster de puerta de enlace. Una vez que cree un origen de datos con el nuevo conector personalizado, podrá actualizar los informes de Power BI mediante ese conector personalizado en el servicio Power BI.

![Conector personalizado 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* Asegúrese de que el servicio de la puerta de enlace en segundo plano puede acceder a la carpeta que cree. Normalmente, no se puede acceder a las carpetas que hay en la carpeta de Windows o del sistema de los usuarios. En la aplicación de puerta de enlace de datos local se muestra un mensaje si no se puede acceder a la carpeta (esto no se aplica a la versión personal de la puerta de enlace).
* Para que los conectores personalizados funcionen con la puerta de enlace de datos local, tienen que implementar una sección "TestConnection" en el código del conector personalizado. Esto no es necesario al usar conectores personalizados con Power BI Desktop. Puede tener uno que funciona con la versión Desktop, pero no con la puerta de enlace por este motivo. Vea [esta documentación](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) sobre cómo implementar una sección TestConnection.

## <a name="next-steps"></a>Pasos siguientes

* [Administrar el origen de datos: Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Administrar el origen de datos: SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Administrar el origen de datos: SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Administrar el origen de datos: Oracle](service-gateway-onprem-manage-oracle.md)  
* [Administrar el origen de datos: importación o actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md)  

* [Configuración de los valores del proxy para la puerta de enlace de datos local](/data-integration/gateway/service-gateway-proxy)  
* [Uso de Kerberos para el SSO (inicio de sesión único) de Power BI en orígenes de datos locales](service-gateway-sso-kerberos.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
