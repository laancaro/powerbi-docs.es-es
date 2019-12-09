---
title: 'Administrar el origen de datos: SQL'
description: Cómo administrar la puerta de enlace de datos local y los orígenes de datos que pertenecen a esa puerta de enlace.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: c0dc3b9eeb7932ca0cb6784fd6a46857821d1b12
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698127"
---
# <a name="manage-your-data-source---sql-server"></a>Administrar el origen de datos: SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Después de [instalar la puerta de enlace de datos local](/data-integration/gateway/service-gateway-install), tendrá que [agregar orígenes de datos](service-gateway-data-sources.md#add-a-data-source) que puedan usarse con esta. En este artículo se describe cómo trabajar con puertas de enlace y orígenes de datos de SQL Server que se usan para la actualización programada o para DirectQuery.

## <a name="add-a-data-source"></a>Elegir un origen de datos

Para más información sobre cómo agregar un origen de datos, consulte [Adición de un origen de datos](service-gateway-data-sources.md#add-a-data-source). En **Tipo de origen de datos**, seleccione **SQL Server**.

![Selección del origen de datos de SQL Server](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Al usar DirectQuery, la puerta de enlace solo es compatible con **SQL Server 2012 SP1** y versiones posteriores.

Rellene la información del origen de datos, incluidos el **Servidor** y la **Base de datos**. 

En **Método de autenticación**, seleccione **Windows** o **Básico**. Seleccione **Básico** si tiene previsto usar la autenticación de SQL en lugar de la autenticación de Windows. A continuación, escriba las credenciales que se usarán para este origen de datos.

> [!NOTE]
> Todas las consultas al origen de datos se ejecutarán con estas credenciales, excepto si se ha configurado el inicio de sesión único (SSO) de Kerberos y se ha habilitado para el origen de datos. Con el inicio de sesión único, los conjuntos de datos de importación usan las credenciales almacenadas, pero los conjuntos de datos de DirectQuery utilizan el usuario actual de Power BI para ejecutar las consultas mediante inicio de sesión único. Para más información sobre cómo se almacenan las credenciales, vea [Almacenamiento de credenciales cifradas en la nube](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud). También puede ver el artículo donde se describe cómo [usar Kerberos para el inicio de sesión único (SSO) de Power BI a orígenes de datos locales](service-gateway-sso-kerberos.md).

![Rellene la configuración del origen de datos](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Después de rellenar todo, seleccione **Agregar**. Ahora, ya puede usar este origen de datos para actualizaciones programadas o DirectQuery en una instancia de SQL Server local. Si se realiza correctamente, verá el mensaje *Se conectó correctamente*.

![Representación del estado de conexión](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configuración avanzada

Opcionalmente, puede configurar el nivel de privacidad del origen de datos. Esta configuración controla cómo se pueden combinar los datos. Solo se usa para la actualización programada. La configuración del nivel de privacidad no se aplica a DirectQuery. Para más información sobre los niveles de privacidad del origen de datos, vea [Niveles de privacidad (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Establecimiento del nivel de privacidad](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Uso del origen de datos

Después de haber creado el origen de datos, estará disponible para usarse con conexiones DirectQuery, o bien a través de una actualización programada.

> [!NOTE]
> El nombre del servidor y de la base de datos deben coincidir entre Power BI Desktop y el origen de datos dentro de la puerta de enlace de datos local.

El vínculo entre el conjunto de datos y el origen de datos dentro de la puerta de enlace se basa en el nombre del servidor y en el nombre de la base de datos. Estos nombres deben coincidir. Por ejemplo, si proporciona una dirección IP para el nombre del servidor, dentro de Power BI Desktop, tendrá que usar la dirección IP del origen de datos dentro de la configuración de la puerta de enlace. Si usa *SERVIDOR\INSTANCIA* en Power BI Desktop, tendrá que usarlo también en el origen de datos configurado para la puerta de enlace.

Este requisito se aplica tanto en DirectQuery como en la actualización programada.

### <a name="use-the-data-source-with-directquery-connections"></a>Uso del origen de datos con conexiones de DirectQuery

Asegúrese de que el nombre del servidor y de la base de datos coinciden entre Power BI Desktop y el origen de datos configurado para la puerta de enlace. También tiene que asegurarse de que el usuario aparece en la pestaña **Usuarios** del origen de datos para publicar conjuntos de datos de DirectQuery. La selección para DirectQuery se produce dentro de Power BI Desktop al importar los datos por primera vez. Para obtener más información sobre cómo usar DirectQuery, vea el artículo sobre el [uso de DirectQuery en Power BI Desktop](desktop-use-directquery.md).

Después de publicar, ya sea desde Power BI Desktop o desde **Obtener datos**, los informes deben empezar a funcionar. La conexión puede tardar varios minutos en poderse usar después de crear el origen de datos dentro de la puerta de enlace.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Uso del origen de datos con la actualización programada

Si aparece en la pestaña **Usuarios** del origen de datos configurado dentro de la puerta de enlace y los nombres del servidor y de la base de datos coinciden, verá la puerta de enlace como una opción para usar con la actualización programada.

![Representación de los usuarios](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Pasos siguientes

* [Conexión a datos locales en SQL Server](service-gateway-sql-tutorial.md)
* [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot)
* [Solución de problemas de puertas de enlace: Power BI](service-gateway-onprem-tshoot.md)
* [Uso de Kerberos para el inicio de sesión único (SSO) de Power BI a orígenes de datos locales](service-gateway-sso-kerberos.md)

¿Tiene más preguntas? Pruebe a preguntar a la [comunidad de Power BI](https://community.powerbi.com/).

