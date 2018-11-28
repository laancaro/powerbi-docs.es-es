---
title: Orígenes de datos admitidos por DirectQuery en Power BI
description: Obtener una lista de los orígenes de datos que pueden usar DirectQuery.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 098447f4d0c0b1dc9534c91e84827c4cefb8850c
ms.sourcegitcommit: fdb54145f9bc93b312409c15c603749f3a4a876e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2018
ms.locfileid: "52452554"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Orígenes de datos admitidos por DirectQuery en Power BI
**Power BI Desktop** y el **servicio Power BI** dispone de muchos orígenes de datos a la que puede conectarse y obtener acceso a datos. En este artículo se describe qué orígenes de datos de Power BI son compatibles con el método de conexión que se conoce como **DirectQuery**. Para más información acerca de DirectQuery, consulte [**DirectQuery en Power BI**](desktop-directquery-about.md).

Los siguientes orígenes de datos admiten DirectQuery en Power BI:

* Amazon Redshift
* Azure HDInsight Spark (Beta)
* Azure SQL Database
* Azure SQL Data Warehouse
* Google BigQuery (beta)
* Base de datos IBM DB2
* IBM Netezza (Beta)
* Impala (versión 2.x)
* Base de datos de Oracle (versión 12 y versiones posteriores)
* Servidor de aplicaciones de SAP Business Warehouse
* Servidor de mensajería de SAP Business Warehouse (Beta)
* SAP HANA
* Snowflake
* Spark (Beta) (versión 0.9 y versiones posteriores)
* SQL Server
* Base de datos de Teradata
* Vertica (Beta)

Los orígenes de datos en los que aparece **(Beta)** o **(Versión preliminar)** después del nombre están sujetos a cambios y no se pueden usar en entornos de producción. Es posible que tampoco se admitan después de publicar un informe en el **servicio Power BI**, lo que implica que se puede producir un error al abrir un informe publicado o explorar el conjunto de datos.

La única diferencia entre los orígenes de datos **(beta)** y **(versión preliminar)** es que los segundos deben habilitarse como una característica de versión preliminar para poder usarse. Para habilitar un conector de datos **(versión preliminar)**, vaya a **Power BI Desktop**, vaya a **Archivo > Opciones y configuración > Opciones** y, después, seleccione **Características de versión preliminar**.

> [!NOTE]
> Las consultas de DirectQuery para SQL Server necesitan autenticación mediante las credenciales de autenticación de Windows actuales o las credenciales de la base de datos para establecer el acceso. No se admiten credenciales alternativas.
>

## <a name="on-premises-gateway-requirements"></a>Requisitos de puerta de enlace local
La tabla siguiente especifica si se requiere una **puerta de enlace de datos local** para conectarse al origen de datos especificado, después de publicar un informe en el **servicio Power BI**.

| Origen | ¿Se requiere puerta de enlace? |
| --- | --- |
| SQL Server |Sí |
| Azure SQL Database |No |
| Azure SQL Data Warehouse |No |
| SAP HANA |Sí |
| Base de datos de Oracle |Sí |
| Base de datos de Teradata |Sí |
| Amazon Redshift |No |
| Impala (versión 2.x) |Sí |
| Snowflake |Sí |
| Spark (Beta), versiones 0.9 y posteriores |Sí |
| Azure HDInsight Spark (Beta) |No |
| IBM Netezza |Sí |
| Servidor de aplicaciones de SAP Business Warehouse |Sí |
| Servidor de mensajería de SAP Business Warehouse |Aún no se admite en el **servicio Power BI** |
| Google BigQuery |No |


## <a name="next-steps"></a>Pasos siguientes
Para más información acerca de DirectQuery, revise los siguientes recursos:

* [DirectQuery en Power BI](desktop-directquery-about.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [On-premises Data Gateway (Puerta de enlace de datos local)](service-gateway-onprem.md)

