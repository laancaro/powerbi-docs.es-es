---
title: Orígenes de datos admitidos por DirectQuery en Power BI
description: Obtener una lista de los orígenes de datos que pueden usar DirectQuery.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/04/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 59c55d2e9322b0b7d76a35f4eec0863efe4959e0
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302656"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Orígenes de datos admitidos por DirectQuery en Power BI

**Power BI Desktop** y el **servicio Power BI** dispone de muchos orígenes de datos a la que puede conectarse y obtener acceso a datos. En este artículo se describe qué orígenes de datos de Power BI son compatibles con el método de conexión que se conoce como **DirectQuery**. Para más información acerca de DirectQuery, consulte [**DirectQuery en Power BI**](desktop-directquery-about.md).

Los siguientes orígenes de datos admiten DirectQuery en Power BI:

* Amazon Redshift
* AtScale (Beta)
* Azure Data Explorer
* Azure HDInsight Spark
* [Azure SQL Database](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Denodo
* Google BigQuery
* HDInsight Interactive Query
* IBM DB2 (proveedor de Microsoft)
* IBM Netezza
* Impala (versión 2.x)
* MarkLogic
* Base de datos de Oracle (versión 12 y versiones posteriores)
* Oracle Essbase
* PostgreSQL
* Servidor de aplicaciones de SAP Business Warehouse
* Servidor de mensajería de SAP Business Warehouse
* SAP HANA
* Snowflake
* Spark (versión 0.9 y posteriores)
* SQL Server
* Base de datos de Teradata
* Vertica

Los orígenes de datos en los que aparece **(Beta)** o **(Versión preliminar)** después del nombre están sujetos a cambios y no se pueden usar en entornos de producción. Es posible que tampoco se admitan después de publicar un informe en el **servicio Power BI**, lo que implica que se puede producir un error al abrir un informe publicado o explorar el conjunto de datos.

La única diferencia entre los orígenes de datos **(beta)** y **(versión preliminar)** es que los segundos deben habilitarse como una característica de **versión preliminar** para poder usarse. Para habilitar un conector de datos **(versión preliminar)** , vaya a **Power BI Desktop**, vaya a **Archivo > Opciones y configuración > Opciones** y, después, seleccione **Características de versión preliminar**.

> [!NOTE]
> Las consultas de DirectQuery para SQL Server necesitan autenticación mediante las credenciales de autenticación de Windows actuales o las credenciales de la base de datos para establecer el acceso. No se admiten credenciales alternativas.
>

## <a name="on-premises-gateway-requirements"></a>Requisitos de puerta de enlace local
La tabla siguiente especifica si se requiere una **puerta de enlace de datos local** para conectarse al origen de datos especificado, después de publicar un informe en el **servicio Power BI**.

| Origen | ¿Se requiere puerta de enlace? |
| --- | --- |
| Amazon Redshift |No |
| Azure HDInsight Spark (Beta) |No |
| Azure SQL Database |No |
| Azure SQL Data Warehouse |No |
| Google BigQuery |No |
| IBM Netezza |Sí |
| IBM DB2 (proveedor de IBM) |Sí |
| IBM DB2 (proveedor de Microsoft) |No |
| Base de datos Informix de IBM |No |
| Impala (versión 2.x) |Sí |
| MySQL |Sí |
| ODBC |Sí |
| Base de datos de Oracle |Sí |
| PostgreSQL |Sí |
| Servidor de aplicaciones de SAP Business Warehouse |Sí |
| Servidor de mensajería de SAP Business Warehouse |Aún no se admite en el **servicio Power BI** |
| SAP HANA |Sí |
| Snowflake |Sí |
| Spark (Beta), versiones 0.9 y posteriores |Sí |
| SQL Server |Sí |
| Sybase |Sí |
| Base de datos de Teradata |Sí |
| Vertica |Sí |


## <a name="single-sign-on-sso-for-directquery-sources"></a>Inicio de sesión único (SSO) para orígenes de DirectQuery

Cuando se habilita la opción SSO y los usuarios acceden a informes creados sobre el origen de datos, Power BI envía sus credenciales autenticadas de Azure AD en las consultas al origen de datos subyacente. Esto permite a Power BI respetar la configuración de seguridad establecida en el nivel de origen de datos.

La opción SSO surte efecto en todos los conjuntos de datos que usan este origen de datos. No afecta el método de autenticación utilizado para los escenarios de importación. Los orígenes de datos siguientes admiten el inicio de sesión único para las conexiones a través de DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradatos

> [!Note]
> No se admite Azure Multi-Factor Authentication (MFA). Los usuarios que quieran usar SSO con DirectQuery se deben excluir de MFA.

## <a name="next-steps"></a>Pasos siguientes
Para más información acerca de DirectQuery, revise los siguientes recursos:

* [DirectQuery en Power BI](desktop-directquery-about.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [On-premises Data Gateway (Puerta de enlace de datos local)](service-gateway-onprem.md)

