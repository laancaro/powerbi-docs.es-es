---
title: Orígenes de datos en Power BI Desktop
description: Orígenes de datos en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ead5c8f45e102aaeebeed492ecf4646342747fe1
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71142281"
---
# <a name="data-sources-in-power-bi-desktop"></a>Orígenes de datos en Power BI Desktop
Power BI Desktop permite conectarse a datos de muchos orígenes diferentes. En la parte inferior de esta página puede consultar una lista completa de los orígenes de datos disponibles.

Para conectarse a datos, seleccione **Obtener datos** desde la cinta de opciones **Inicio** . Al seleccionar la flecha abajo o el texto **Obtener datos** en el botón, se muestra el menú de tipos de datos **Más comunes** en la siguiente imagen:

![Obtener datos en Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Al seleccionar **Más…** en el menú **Más comunes**, se muestra la ventana **Obtener datos**. También puede abrir la ventana **Obtener datos** (y omitir el menú **Más comunes** ) seleccionando el icono **Obtener datos** **directamente** .

![Botón Obtener datos](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> El equipo de Power BI está ampliando continuamente los orígenes de datos disponibles en **Power BI Desktop** y **servicio Power BI**. Por lo tanto, a menudo verá las versiones anteriores de orígenes de datos en proceso de desarrollo marcados como *Beta* o *Versión preliminar*. Cualquier origen de datos marcada como *Beta* o *Versión preliminar* tiene una compatibilidad y funcionalidades limitadas y, no debe usarse en entornos de producción. 

> Además, es posible que los orígenes de datos marcados como *Beta* o *Versión preliminar* para **Power BI Desktop** no estén disponibles para su uso en el **servicio Power BI** u otros servicios de Microsoft hasta que el origen de datos esté disponible con carácter general (GA).

## <a name="data-sources"></a>Orígenes de datos
Los tipos de datos se organizan en las categorías siguientes:

* Todos
* Archivo
* Base de datos
* Power BI
* Azure
* Online Services
* Otros

La categoría **Todos** incluye todos los tipos de conexión de datos de todas las categorías.

La categoría **Archivo** proporciona las siguientes conexiones de datos:

* Excel
* Texto o CSV
* XML
* JSON
* Carpeta
* PDF
* Carpeta de SharePoint

La siguiente imagen muestra la ventana **Obtener datos** para **Archivo**.

![Obtener datos > Archivo](media/desktop-data-sources/data-sources-03.png)

La categoría **Base de datos** proporciona las siguientes conexiones de datos:

* Base de datos de SQL Server
* Base de datos de Access
* Base de datos de SQL Server Analysis Services
* Base de datos de Oracle
* Base de datos IBM DB2
* Base de datos Informix de IBM (beta)
* IBM Netezza
* Base de datos de MySQL
* Base de datos de PostgreSQL
* Base de datos de Sybase
* Base de datos de Teradata
* Base de datos SAP HANA
* Servidor de aplicaciones de SAP Business Warehouse
* Servidor de mensajería de SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* Cubos AtScale (Beta)
* Conector de BI
* Dremio
* Exasol
* Indexima (Beta)
* InterSystems IRIS (Beta)
* Jethro (beta)
* Kyligence Enterprise (Beta)
* MarkLogic (Beta)

> [!NOTE]
> Para habilitar algunos conectores de bases de datos, debe seleccionar primero **Archivo > Opciones y configuración > Opciones** y, después, **Características en vista previa**. Si no ve algunos de los conectores mencionados anteriormente y quiere usarlos, compruebe la configuración de **Características en vista previa**. Tenga también en cuenta que cualquier origen de datos marcada como *Beta* o *Versión preliminar* tiene una compatibilidad y funcionalidades limitadas, y no debe usarse en entornos de producción.

La siguiente imagen muestra la ventana **Obtener datos** para **Base de datos**.

![Obtener datos > Bases de datos](media/desktop-data-sources/data-sources-04.png)

La categoría **Power Platform** proporciona las conexiones de datos siguientes:

* Conjuntos de datos de Power BI
* Flujos de datos de Power BI
* Common Data Service
* Flujos de entrada de Power Platform (Beta)

En la imagen siguiente se muestra la ventana **Obtener datos** para **Power Platform**.

![Obtener datos > Power BI](media/desktop-data-sources/data-sources-05.png)

La categoría **Azure** proporciona las siguientes conexiones de datos:

* Azure SQL Database
* Azure SQL Data Warehouse
* Base de datos de Azure Analysis Services
* Azure Blob Storage
* Azure Table Storage
* Azure Cosmos DB
* Azure Data Lake Storage Gen2 (Beta)
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Azure Data Explorer (Kusto)
* Azure Cost Management (Beta)

La siguiente imagen muestra la ventana **Obtener datos** para **Azure**.

![Obtener datos > Azure](media/desktop-data-sources/data-sources-06.png)

La categoría **Online Services** proporciona las siguientes conexiones de datos:

* Lista de SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (en línea)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (local)
* Microsoft Azure Consumption Insights (Beta)
* Azure DevOps (Beta)
* Azure DevOps Server (Beta)
* Objetos de Salesforce
* Informes de Salesforce
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* Data.World - Obtener un conjunto de datos (Beta)
* Facebook
* GitHub (Beta)
* MailChimp (Beta)
* Marketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One - PRM (Beta)
* PlanView Projectplace (Beta)
* QuickBooks Online (Beta)
* Smartsheet
* SparkPost (Beta)
* Stripe (Beta)
* SweetIQ (Beta)
* PlanView Enterprise One - CMT (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* Zendesk (Beta)
* Dynamics 365 Customer Insights (Beta)
* Origen de datos de Emigo (Beta)
* Entersoft Business Suite (Beta)
* Industrial App Store
* Intune Data Warehouse (Beta)
* Microsoft Graph Security (Beta)
* Quick Base
* TeamDesk (Beta)


La imagen siguiente muestra la ventana **Obtener datos** para **Online Services**

![Obtener datos > Online Services](media/desktop-data-sources/data-sources-07.png)

La categoría **Otros** proporciona las siguientes conexiones de datos:

* Web
* Lista de SharePoint
* Fuente de OData
* Active Directory
* Microsoft Exchange
* Archivo Hadoop (HDFS)
* Spark
* Script R
* Script de Python
* ODBC
* OLE DB
* BI360: informes presupuestarios y financieros (Beta)
* Denodo
* Information Grid (Beta)
* Paxata 
* QubolePresto (Beta)
* Roamler (Beta)
* SurveyMonkey (Beta)
* Tenforce (Smart)List (Beta)
* Dimensiones de Workforce (Beta)
* Consulta en blanco

La siguiente imagen muestra la ventana **Obtener datos** para **Otros**.

![Obtener datos > Otros](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> En este momento, no es posible conectarse a orígenes de datos personalizados que se protegen mediante Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Conectarse a un origen de datos
Para conectarse a un origen de datos, seleccione el origen de datos en la ventana **Obtener datos** y seleccione **Conectar**. En la siguiente imagen, la opción **Web** está seleccionada en la categoría de conexión de datos **Otros** .

![Conectar a Web](media/desktop-data-sources/data-sources-08.png)

Se muestra una ventana de conexión, específica al tipo de conexión de datos. Si se necesitan credenciales, se le pedirá que las proporcione. La siguiente imagen muestra una dirección URL que se escribió para conectarse a un origen de datos web.

![Entrada de dirección URL web](media/desktop-data-sources/datasources-fromwebbox.png)

Cuando se escribe la información de conexión de recurso o la dirección URL, seleccione **Aceptar**. Power BI Desktop realiza la conexión al origen de datos y presenta los orígenes de datos disponibles en el **Navegador**.

![Pantalla de navegador](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Puede cargar los datos seleccionando el botón **Cargar** situado en la parte inferior del panel **Navegador** , o bien editar la consulta antes de cargar datos seleccionando el botón **Editar** .

Eso es todo lo que se necesita para conectarse a orígenes de datos en Power BI Desktop. Intente conectarse a datos de nuestra lista de orígenes de datos en crecimiento y vuelva a consultarla con frecuencia, debido a que siempre agregamos elementos a esta lista.

## <a name="next-steps"></a>Pasos siguientes
Se puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)    
