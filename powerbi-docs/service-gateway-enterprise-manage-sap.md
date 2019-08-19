---
title: 'Administrar el origen de datos: SAP HANA'
description: Cómo administrar la puerta de enlace de datos local y los orígenes de datos que pertenecen a esa puerta de enlace. Este artículo es específico de SAP HANA.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2458c99192779c0597c38ea9f3a3baf23f4e1dd2
ms.sourcegitcommit: 9665bdabce3bfc31f68dd8256b135bfd56f60589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68832483"
---
# <a name="manage-your-data-source---sap-hana"></a>Administrar el origen de datos: SAP HANA

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Después de [instalar la puerta de enlace de datos local](/data-integration/gateway/service-gateway-install), tendrá que [agregar orígenes de datos](service-gateway-data-sources.md#add-a-data-source) que se puedan usar con ella. En este artículo se describe cómo trabajar con puertas de enlace y orígenes de datos de SAP HANA que se usan para la actualización programada o para DirectQuery.

## <a name="add-a-data-source"></a>Elegir un origen de datos

Para más información sobre cómo agregar un origen de datos, consulte [Adición de un origen de datos](service-gateway-data-sources.md#add-a-data-source). En **Tipo de origen de datos**, seleccione **SAP HANA**.

![Adición del origen de datos SAP HANA](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

Después de seleccionar el tipo de origen de datos SAP HANA, rellene los campos **Servidor**, **Nombre de usuario** y **Contraseña** del origen de datos.

> [!NOTE]
> Todas las consultas que se realicen al origen de datos se ejecutarán con estas credenciales. Para más información sobre cómo se almacenan las credenciales, vea [Almacenamiento de credenciales cifradas en la nube](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Rellene la configuración del origen de datos](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

Después de rellenar todo, seleccione **Agregar**. A continuación, podrá usar este origen de datos para actualizaciones programadas o DirectQuery en un servidor de SAP HANA local. Si se realiza correctamente, verá el mensaje *Se conectó correctamente*.

![Representación del estado de conexión](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configuración avanzada

Opcionalmente, puede configurar el nivel de privacidad del origen de datos. Esta configuración controla cómo se pueden combinar los datos. Solo se usa para la actualización programada. La configuración del nivel de privacidad no se aplica en DirectQuery. Para más información sobre los niveles de privacidad del origen de datos, vea [Niveles de privacidad (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Establecimiento del nivel de privacidad](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Uso del origen de datos

Después de haber creado el origen de datos, estará disponible para usarse con conexiones DirectQuery, o bien a través de una actualización programada.

> [!NOTE]
> El nombre del servidor y de la base de datos deben coincidir entre Power BI Desktop y el origen de datos dentro de la puerta de enlace de datos local.

El vínculo entre el conjunto de datos y el origen de datos dentro de la puerta de enlace se basa en el nombre del servidor y en el nombre de la base de datos. Estos nombres deben coincidir. Por ejemplo, si proporciona una dirección IP para el nombre del servidor, dentro de Power BI Desktop, tendrá que usar la dirección IP del origen de datos dentro de la configuración de la puerta de enlace. Si usa *SERVER\INSTANCE* en Power BI Desktop, también tiene que usar lo mismo en el origen de datos configurado para la puerta de enlace.

Este requisito se aplica tanto en DirectQuery como en la actualización programada.

### <a name="use-the-data-source-with-directquery-connections"></a>Uso del origen de datos con conexiones de DirectQuery

Asegúrese de que el nombre del servidor y de la base de datos coincida en Power BI Desktop y en el origen de datos configurado para la puerta de enlace. También tiene que asegurarse de que el usuario aparezca en la pestaña **Usuarios** del origen de datos para publicar conjuntos de datos de DirectQuery. La selección para DirectQuery se produce dentro de Power BI Desktop al importar los datos por primera vez. Para obtener más información sobre cómo usar DirectQuery, vea [Usar DirectQuery en Power BI Desktop](desktop-use-directquery.md).

Después de publicar, ya sea desde Power BI Desktop o desde **Obtener datos**, los informes deben empezar a funcionar. La conexión puede tardar varios minutos en poderse usar después de crear el origen de datos dentro de la puerta de enlace.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Uso del origen de datos con la actualización programada

Si aparece en la pestaña **Usuarios** del origen de datos configurado dentro de la puerta de enlace y los nombres del servidor y de la base de datos coinciden, verá la puerta de enlace como una opción para usar con la actualización programada.

![Representación de los usuarios](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Pasos siguientes

* [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot)
* [Solución de problemas de puertas de enlace: Power BI](service-gateway-onprem-tshoot.md) 

¿Tiene más preguntas? Pruebe a preguntar a la [comunidad de Power BI](http://community.powerbi.com/).

