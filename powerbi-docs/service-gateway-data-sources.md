---
title: Administración de orígenes de datos
description: Obtenga información sobre cómo administrar orígenes de datos en Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 3a4b343894f23d6f5720d95eb6c92436259befaa
ms.sourcegitcommit: a58461fe7dfa65c751490b52de5fc73f8e69a17f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68352199"
---
# <a name="manage-data-sources"></a>Administración de orígenes de datos

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Power BI admite muchos orígenes de datos locales, y cada uno tiene sus propios requisitos. Una puerta de enlace se puede usar para un único origen de datos, o bien para varios. En este ejemplo, vamos a mostrarle cómo agregar SQL Server como un origen de datos, pero los pasos son similares para otros orígenes de datos.

>[!NOTE]
>La mayoría de las operaciones de administración de orígenes de datos también se pueden realizar mediante API. Para más información, vea [API REST (puertas de enlace)](/rest/api/power-bi/gateways).

## <a name="add-a-data-source"></a>Elegir un origen de datos

>[!NOTE]
>No se pueden agregar grupos sin un correo electrónico.

1. En la esquina superior derecha del servicio Power BI, seleccione el icono del engranaje ![Icono de engranaje de configuración](media/service-gateway-data-sources/icon-gear.png) > **Administrar puertas de enlace**.

    ![Administrar puertas de enlace](media/service-gateway-data-sources/manage-gateways.png)

2. Seleccione una puerta de enlace > **Agregar origen de datos** o vaya a Puertas de enlace > **Agregar origen de datos**.

    ![Agregar origen de datos](media/service-gateway-data-sources/add-data-source.png)

3. Seleccione el **tipo de origen de datos**.

    ![Seleccionar SQL Server](media/service-gateway-data-sources/select-sql-server.png)

4. Escriba la información del origen de datos. En este ejemplo, es **Servidor**, **Base de datos** y otra información.  

    ![Configuración del origen de datos](media/service-gateway-data-sources/data-source-settings.png)

5. Para SQL Server, elegiría un **Método de autenticación** de **Windows** o **Básico** (Autenticación de SQL). Si elige **Básico**, escriba las credenciales del origen de datos.

6. En **Configuración avanzada**, si quiere puede configurar el [nivel de privacidad](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) del origen de datos (no se aplica a [DirectQuery](desktop-directquery-about.md)).

    ![Configuración avanzada](media/service-gateway-data-sources/advanced-settings.png)

7. Seleccione **Agregar**. Si el proceso se completa correctamente, verá el mensaje *Conexión correcta*.

    ![Conexión correcta](media/service-gateway-data-sources/connection-successful.png)

Ahora puede usar este origen de datos para incluir los datos de SQL Server en los informes y paneles de Power BI.

## <a name="remove-a-data-source"></a>Quitar un origen de datos

Puede quitar un origen de datos si ya no lo usa. Tenga en cuenta que, si quita un origen de datos, se interrumpirá cualquier panel e informe que se base en dicho origen.

Para quitar un origen de datos, vaya al origen de datos y luego seleccione **Quitar**.

![Quitar un origen de datos](media/service-gateway-data-sources/remove-data-source.png)

## <a name="using-the-data-source-for-scheduled-refresh-or-directquery"></a>Uso del origen de datos para actualización programada o DirectQuery

Después de haber creado el origen de datos, estará disponible para usarse con conexiones DirectQuery, o bien a través de una actualización programada.

> [!NOTE]
>El nombre del servidor y de la base de datos deben coincidir entre Power BI Desktop y el origen de datos dentro de la puerta de enlace de datos local.

El vínculo entre el conjunto de datos y el origen de datos de la puerta de enlace se basa en el nombre del servidor y el de la base de datos. Estos nombres deben coincidir. Por ejemplo, si proporciona una dirección IP para el nombre del servidor, en Power BI Desktop, tendrá que usar la dirección IP del origen de datos de la configuración de la puerta de enlace. Si usa *SERVIDOR\INSTANCIA* en Power BI Desktop, tendrá que usar lo mismo en el origen de datos configurado para la puerta de enlace.

Si aparece en la pestaña **Usuarios** del origen de datos configurado en la puerta de enlace y los nombres del servidor y de la base de datos coinciden, verá la puerta de enlace como una opción para usar con la actualización programada.

![Conexión de puerta de enlace](media/service-gateway-data-sources/gateway-connection.png)

> [!WARNING]
> Si el conjunto de datos contiene varios orígenes de datos, deberá agregar cada uno en la puerta de enlace. Si no agrega uno de los orígenes de datos (o más) a la puerta de enlace, no verá la puerta de enlace como disponible para la actualización programada.

### <a name="limitations"></a>Limitaciones

OAuth es un esquema de autenticación compatible solo para conectores personalizados con la puerta de enlace de datos local. No puede agregar otros orígenes de datos que requieran OAuth. Si el conjunto de datos tiene un origen de datos que requiere OAuth y no es un conector personalizado, no podrá usar la puerta de enlace para la actualización programada.

## <a name="manage-users"></a>Administrar usuarios

Después de agregar un origen de datos a una puerta de enlace, conceda acceso a los usuarios y grupos de seguridad habilitados para correo electrónico al origen de datos específico (no a toda la puerta de enlace). La lista de usuarios del origen de datos controla solo a quién se le permite publicar informes que incluyen datos del origen de datos. Los propietarios de informes pueden crear paneles, paquetes de contenido y aplicaciones y compartirlos con otros usuarios.

También puede conceder acceso administrativo a los usuarios y grupos de seguridad a la puerta de enlace.

### <a name="add-users-to-a-data-source"></a>Adición de usuarios a un origen de datos

1. En la esquina superior derecha del servicio Power BI, seleccione el icono del engranaje ![Icono de engranaje de configuración](media/service-gateway-data-sources/icon-gear.png) > **Administrar puertas de enlace**.

2. Seleccione el origen de datos en el que desea agregar usuarios.

3. Seleccione **Usuarios** y especifique un usuario de su organización a quien desea conceder acceso al origen de datos seleccionado. Por ejemplo, en la pantalla siguiente se agrega a Maggie y a Adam.

    ![Pestaña Usuarios](media/service-gateway-data-sources/users-tab.png)

4. Seleccione **Agregar**, y el miembro agregado se muestra en el cuadro.

    ![Agregar usuario](media/service-gateway-data-sources/add-user.png)

Y eso es todo. Recuerde que debe agregar usuarios a cada origen de datos al que quiera conceder acceso. Cada origen de datos tiene una lista separada de usuarios y debe agregar los usuarios por separado para cada origen de datos.

### <a name="remove-users-from-a-data-source"></a>Eliminación de usuarios de un origen de datos

En la pestaña **Usuarios** del origen de datos, puede quitar usuarios y grupos de seguridad que usan este origen de datos.

![Quitar usuario](media/service-gateway-data-sources/remove-user.png)

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Almacenar credenciales cifradas en la nube

Cuando agrega un origen de datos a la puerta de enlace, debe proporcionar las credenciales de ese origen de datos. Todas las consultas que se realicen al origen de datos se ejecutarán con estas credenciales. Las credenciales se cifran de forma segura mediante el cifrado simétrico, para que no se puedan descifrar en la nube, antes de almacenarse en ella. Las credenciales se envían al equipo en el que se ejecuta la puerta de enlace, de forma local, donde se descifran cuando se accede a los orígenes de datos.

## <a name="list-of-available-data-source-types"></a>Lista de tipos de orígenes de datos disponibles

La puerta de enlace de datos local admite los siguientes orígenes de datos para Power BI. Además de los orígenes de datos locales, los orígenes detrás de un firewall, VPN o red virtual también podrían necesitar una puerta de enlace de datos.

| **Origen de datos** | **Dinámica/DirectQuery** | **Actualización programada o manual configurada por el usuario** |
| --- | --- | --- |
| Active Directory |No |Sí |
| Amazon Redshift |Sí |Sí |
| Analysis Services |Sí |Sí |
| Cubos de AtScale |Sí |Sí |
| Azure Blob Storage |No |Sí |
| Azure DevOps Server |No |Sí |
| Azure Table Storage |No |Sí |
| Conector de BI |Sí |Sí |
| Denodo |Sí |Sí |
| Dremio |Sí |Sí |
| EmigoDataSourceConnector |No |Sí |
| Essbase |Sí |Sí |
| Exasol |Sí |Sí |
| Archivo |No |Sí |
| Carpeta |No |Sí |
| Paxata |No |Sí |
| IBM DB2 |Sí |Sí |
| Base de datos Informix de IBM |No |Sí |
| IBM Netezza |Sí |Sí |
| Impala |Sí |Sí |
| Jethro ODBC |Sí |Sí |
| Kyligence Enterprise |Sí |Sí |
| MarkLogic ODBC |Sí |Sí |
| Microsoft Graph Security |No |Sí |
| MySQL |No |Sí |
| ODBC |No |Sí |
| OData |No |Sí |
| OleDb |No |Sí |
| Oracle |Sí |Sí |
| PostgreSQL |No |Sí |
| QubolePresto |Sí |Sí |
| Conector Quick Base |No |Sí |
| Servidor de mensajería de SAP Business Warehouse |Sí |Sí |
| Servidor de SAP Business Warehouse |Sí |Sí |
| SAP HANA |Sí |Sí |
| SQL Server |Sí |Sí |
| SharePoint |No |Sí |
| Snowflake |Sí |Sí |
| Spark |Sí |Sí |
| SurveyMonkey |No |Sí |
| Sybase |No |Sí |
| TeamDesk.Database |No |Sí |
| Teradata |Sí |Sí |
| Vertica |Sí |Sí |
| Web |No |Sí |
| Dimensiones de Workforce |No |Sí |

## <a name="next-steps"></a>Pasos siguientes

* [Administrar el origen de datos: Analysis Services](service-gateway-enterprise-manage-ssas.md)
* [Administrar el origen de datos: SAP HANA](service-gateway-enterprise-manage-sap.md)
* [Administrar el origen de datos: SQL Server](service-gateway-enterprise-manage-sql.md)
* [Administrar el origen de datos: Oracle](service-gateway-onprem-manage-oracle.md)
* [Administrar el origen de datos: importación o actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Instrucciones para implementar una puerta de enlace de datos](service-gateway-deployment-guidance.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
