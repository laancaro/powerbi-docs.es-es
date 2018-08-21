---
title: Uso de conectores de datos personalizados con la puerta de enlace de datos local
description: Puede usar conectores de datos personalizados con la puerta de enlace de datos local.
author: mgblythe
ms.author: mblyth
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 08/08/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 8230a1df7db7758c34bf45c5a33e991ddf08dde5
ms.sourcegitcommit: cce10e14c111e8a19f282ad6c032d802ebfec943
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39713131"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Uso de conectores de datos personalizados con la puerta de enlace de datos local

Los conectores de datos de Power BI le permiten conectarse y tener acceso a datos desde un origen de datos, servicio o aplicación. Puede desarrollar conectores de datos personalizados y usarlos en Power BI Desktop.

Para obtener más información sobre cómo desarrollar conectores de datos personalizadas para Power BI, vea nuestra documentación [aquí](http://aka.ms/dataconnectors).

Al compilar informes en Power BI Desktop que usan conectores de datos personalizados, puede usar la puerta de enlace de datos local para actualizar estos informes desde el servicio Power BI.

## <a name="here-is-a-guide-on-how-to-enable-and-use-this-capability"></a>Aquí tiene una guía sobre cómo habilitar y usar esta funcionalidad

Al instalar la versión de julio de 2018 de la puerta de enlace de datos local o una versión posterior, puede ver la pestaña "Conectores" en el configurador con una opción para elegir una carpeta desde la que cargar los conectores personalizados. Asegúrese de que selecciona una carpeta a la que pueda acceder el usuario que ejecuta el servicio de puerta de enlace (que es "NT SERVICE\PBIEgwService" de forma predeterminada). La puerta de enlace carga automáticamente los archivos del conector personalizado que se encuentran en esa carpeta y debería verlos en la lista de los conectores de datos.

![Conector personalizado 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Si usa la versión Personal de la puerta de enlace de datos local, en este momento debería poder cargar el informe de Power BI en el servicio Power BI y usar la puerta de enlace para actualizarlo.

Para la versión Enterprise de la puerta de enlace, deberá crear un origen de datos para el conector personalizado. En la página de configuración de la puerta de enlace en el servicio Power BI, debería ver una nueva opción al seleccionar el clúster de puerta de enlace para permitir el uso de conectores personalizados con este clúster. Asegúrese de que todas las puertas de enlace del clúster tienen la versión de actualización de julio de 2018 o una posterior para que esta opción esté disponible. Ahora, seleccione esa opción para habilitar el uso de conectores personalizados con este clúster.

![Conector personalizado 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Cuando esta opción esté habilitada, verá los conectores personalizados como orígenes de datos disponibles que se pueden crear en este clúster de puerta de enlace. Una vez que cree un origen de datos con el nuevo conector personalizado, podrá actualizar los informes de Power BI mediante ese conector personalizado en el servicio Power BI.

![Conector personalizado 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* Asegúrese de que el servicio de la puerta de enlace en segundo plano puede acceder a la carpeta que cree. Normalmente, no se puede acceder a las carpetas que hay en la carpeta de Windows o del sistema de los usuarios. El configurador de la puerta de enlace muestra un mensaje si no se puede acceder a la carpeta (esto no se aplica a la versión Personal de la puerta de enlace).
* Para que los conectores personalizados funcionen con la puerta de enlace de datos local, se debe implementar una sección "TestConnection" en el código del conector personalizado. Esto no es necesario al usar conectores personalizados con Power BI Desktop. Puede tener uno que funciona con la versión Desktop, pero no con la puerta de enlace por este motivo. Vea [esta documentación](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) sobre cómo implementar una sección TestConnection.
* No se admiten los conectores personalizados con la autenticación OAuth.
* No se admiten los conectores personalizados con DirectQuery.

## <a name="next-steps"></a>Pasos siguientes

* [Administrar el origen de datos: Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Administrar el origen de datos: SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Administrar el origen de datos: SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Administrar el origen de datos: Oracle](service-gateway-onprem-manage-oracle.md)  
* [Administrar el origen de datos: importación o actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md)  
* [Detalles sobre la puerta de enlace de datos local](service-gateway-onprem-indepth.md)  
* [Puerta de enlace de datos local (modo personal)](service-gateway-personal-mode.md)
* [Configuración de los valores del proxy para la puerta de enlace de datos local](service-gateway-proxy.md)  
* [Uso de Kerberos para el SSO (inicio de sesión único) de Power BI en orígenes de datos locales](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
