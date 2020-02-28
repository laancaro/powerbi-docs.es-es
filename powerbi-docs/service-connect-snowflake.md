---
title: Conexión a Snowflake en Power BI
description: Snowflake con SSO para Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 03e6e8efae5cd4a5f61e3d07bc0b3c524b3b0a46
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2020
ms.locfileid: "77429358"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Conexión a Snowflake en el servicio Power BI

## <a name="introduction"></a>Introducción

La conexión a Snowflake en el servicio Power BI solo difiere de otros conectores en un sentido: se ofrece una funcionalidad adicional para AAD (con una opción para SSO). Diferentes elementos de la integración requieren roles administrativos distintos a través de Snowflake, Power BI y Azure. También puede optar por habilitar la autenticación de AAD sin usar SSO. La autenticación básica funciona de forma similar a otros conectores en el servicio.

Si le interesa configurar la integración de AAD, así como habilitar SSO opcionalmente:
* Si es el administrador de Snowflake, lea el artículo [SSO de Power BI para Snowflake: Introducción](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) de la documentación de Snowflake.
* (SSO) Si es un administrador de Power BI, consulte la sección "Configuración del servicio Power BI: portal de administración"
* (SSO) Si es un creador de conjuntos de datos de Power BI, consulte la sección "Configuración del servicio Power BI: habilitación de un conjunto de datos"

## <a name="power-bi-service-configuration"></a>Configuración del servicio Power BI

### <a name="admin-portal"></a>Portal de administración

Si quiere habilitar el inicio de sesión único, es necesario que el administrador de inquilinos vaya al portal de administración y apruebe el envío de las credenciales de AAD de Power BI a Snowflake.

![Configuración del administrador de inquilinos para el SSO de Snowflake](media/service-connect-snowflake/snowflakessotenant.png)

Vaya a "Portal de administración", seleccione el elemento de la barra lateral "Configuración del inquilino", desplácese hacia abajo hasta "Configuración de integración" y verá una opción para "SSO de Snowflake".

Como se ha advertido, tiene que habilitarlo de forma manual para dar su consentimiento al envío del token de AAD a los servidores de Snowflake. Para habilitarlo, haga clic en el comando de alternancia "Deshabilitado", pulse Aplicar y espere a que el cambio de configuración surta efecto. El servicio puede tardar hasta una hora en propagar la configuración.

Una vez hecho esto, podrá usar informes con SSO.

### <a name="configuring-a-dataset-with-aad"></a>Configuración de un conjunto de datos con AAD

Una vez que se haya publicado en la web un informe basado en el conector Snowflake, en el servicio web Power BI, el creador del conjunto de datos debe navegar hasta el área de trabajo adecuada, seleccionar "Conjuntos de datos" y luego "Configuración" (en el menú "..." de acciones adicionales situado junto al conjunto de datos pertinente).

Debido al funcionamiento de Power BI, SSO solo funcionará cuando no se ejecute ningún origen de datos a través de la puerta de enlace de datos local.

* Si solo va a usar un origen de Snowflake en el modelo de datos, puede utilizar el inicio de sesión único si decide no usar la puerta de enlace de datos local
* Si va a usar un origen de Snowflake junto a otro origen, puede utilizar el inicio de sesión único si ninguno de los orígenes usa la puerta de enlace de datos local
* Si va a usar un origen de Snowflake a través de la puerta de enlace de datos local, puede usar las credenciales de AAD pero no SSO. Esto puede ser importante en caso de que intente acceder a una red virtual desde una única dirección IP con la puerta de enlace instalada en ella, en lugar de hacerlo desde el intervalo de direcciones IP completo de Power BI.
* Si va a usar un origen de Snowflake junto a otro que requiera una puerta de enlace, se le pedirá que también use Snowflake a través de la puerta de enlace de datos local y no podrá usar SSO.

Para más información sobre cómo usar la puerta de enlace de datos local, vea el artículo [¿Qué es una puerta de enlace de datos local?](https://docs.microsoft.com/power-bi/service-gateway-onprem)

Si no va a usar la puerta de enlace, todo está listo. Si tiene credenciales de Snowflake configuradas en la puerta de enlace de datos local, pero solo usa ese origen de datos en el modelo, puede hacer clic en el control de la página Configuración del conjunto de datos para desactivar la puerta de enlace para ese modelo de datos.

![Configuración del conjunto de datos para desactivar la puerta de enlace](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

El creador del conjunto de datos debe seleccionar "Credenciales de origen de datos" e iniciar sesión. Se puede iniciar sesión en el conjunto de datos en Snowflake con credenciales básicas o de OAuth2 (AAD). Si decide usar AAD, el conjunto de datos se puede habilitar para usar SSO. Cuando este primer usuario inicie sesión en Snowflake para el conjunto de datos, tendrá que seleccionar la opción de que se utilicen las credenciales de Oauth2 de otros usuarios para recuperar los datos. Esto habilitará el inicio de sesión único de AAD. Con independencia de que el usuario inicial inicie sesión con la autenticación básica o la de OAuth2 (AAD), las credenciales de AAD serán las que se enviarán para SSO. 

![Configuración del conjunto de datos para el SSO de Snowflake](media/service-connect-snowflake/snowflakessocredui.png)

Una vez hecho esto, los usuarios adicionales deben usar automáticamente su autenticación de AAD para conectarse a los datos de ese conjunto de datos de Snowflake.

Si decide no habilitar el inicio de sesión único, los usuarios que actualicen el informe utilizarán las credenciales del usuario que haya iniciado sesión, como la mayoría de otros informes de Power BI.

### <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas con la integración, consulte la [guía de solución de problemas](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting) de Snowflake.

