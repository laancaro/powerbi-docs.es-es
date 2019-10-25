---
title: Orígenes de datos en Power BI Desktop
description: Orígenes de datos en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 56583c796a8f6e32bed67629dee4fe3bea677bee
ms.sourcegitcommit: 549401b0e1fad15c3603fe7f14b9494141fbb100
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72307840"
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
* Teradatos
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

* Conjuntos de datos de Power BI
* Flujos de datos de Power BI
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

## <a name="using-pbids-files-to-get-data"></a>Usar archivos PBIDS para obtener datos

Los archivos PBIDS son archivos de Power BI Desktop con una estructura específica. Tienen la extensión .PBIDS para identificarlos como archivo de origen de datos de Power BI.

Un archivo .PBIDS se puede crear para optimizar la experiencia **Obtener datos** de los creadores de informes de la organización. Se recomienda que los administradores creen estos archivos para las conexiones que se usan con frecuencia, ya que ello facilita el uso de archivos PBIDS a los nuevos autores de informes. 

Cuando un autor abre un archivo .PBIDS, Power BI Desktop se abre y pide al usuario las credenciales para autenticarse y conectarse al origen de datos especificado en el archivo. El cuadro de diálogo Navegación se abre, y el usuario debe seleccionar las tablas del origen de datos que quiera cargar en el modelo. Puede que también deba seleccionar las bases de datos si no hay ninguna especificada en el archivo .PBIDS. 

A partir de ese momento, el usuario puede empezar a crear visualizaciones o volver a visitar *Orígenes recientes para cargar un nuevo conjunto de tablas en el modelo. 

Actualmente, los archivos .PBIDS solo admiten un único origen de datos en un archivo. Si se especifica más de un origen de datos, se producirá un error. 

Para crear el archivo .PBIDS, los administradores deben especificar las entradas necesarias relativas a una sola conexión y, asimismo, especificar el modo de esa conexión, ya sea **DirectQuery** o **Importar**. Si el **modo** no existe o es nulo en el archivo, se pedirá al usuario que abre el archivo en Power BI Desktop que seleccione DirectQuery o Importar. 

### <a name="pbids-file-examples"></a>Ejemplos de archivos PBIDS

En esta sección se proporcionan algunos ejemplos de orígenes de datos de uso frecuente. El tipo de archivo .PBIDS solo admite las conexiones de datos que también se admiten en Power BI Desktop, salvo dos excepciones: las conexiones dinámicas y las consultas en blanco. 

El archivo .PBIDS *no* incluye información de autenticación ni de tablas y esquemas.  

Estos son algunos ejemplos comunes de archivos .PBIDS, pero no representan una muestra completa ni exhaustiva. En el caso de otros orígenes de datos, puede consultar el [formato de referencia de origen de datos (DSR)](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification) para obtener información sobre protocolos y direcciones.

Estos ejemplos se muestran aquí solo para su comodidad, y no están diseñados para ser integrales ni incluyen todos los conectores admitidos en formato DSR. Los administradores u organizaciones pueden crear sus propios orígenes de datos tomando estos ejemplos como guía y arrancar desde ahí para crear y admitir sus propios archivos de origen de datos. 


**Azure AS**
```
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```


 

**Carpeta**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

**OData**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```
 
**SAP BW**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```
 
**SAP Hana**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

**Lista de SharePoint**

La dirección URL debe apuntar al sitio de SharePoint en sí, y no a una lista dentro del sitio. Los usuarios obtienen un navegador que les permite seleccionar una o más listas de ese sitio, cada una de las cuales se convierte en una tabla del modelo. 
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```
 
 
**SQL Server**
```
{ 
  “version”: “0.1”, 
  “connections”: [ 
    { 
      “details”: { 
        “protocol”: “tds”, 
        “address”: { 
          “server”: “server-name-here”, 
          “database”: “db-name-here (optional)” 
        } 
      }, 
      “options”: {}, 
      “mode”: “DirectQuery” 
    } 
  ] 
} 
} 
```
 

**Archivo de texto**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```
 

**Web**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```
 



## <a name="next-steps"></a>Pasos siguientes
Se puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)    
