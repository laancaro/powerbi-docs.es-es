---
title: Orígenes de datos en Power BI Desktop
description: Orígenes de datos en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0cf9d6acd4fe5f729dafb575a2ab736b9e8db7bb
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76039777"
---
# <a name="data-sources-in-power-bi-desktop"></a>Orígenes de datos en Power BI Desktop

Power BI Desktop permite conectarse a datos de muchos orígenes diferentes. Para obtener una lista completa de los orígenes de datos disponibles, vea [Orígenes de datos de Power BI](power-bi-data-sources.md).

Use la cinta de opciones **Inicio** para conectarse a los datos. Para mostrar el menú de los tipos de datos **Más comunes**, seleccione la etiqueta del botón **Obtener datos** o la flecha abajo.

![Menú de los tipos de datos Más comunes, Obtener datos en Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Para ir al cuadro de diálogo **Obtener datos**, muestre el menú de los tipos de datos **Más comunes** y seleccione **Más**. Puede abrir el cuadro de diálogo **Obtener datos** (y omitir el menú **Más comunes**) si selecciona directamente el icono **Obtener datos**.

![Botón Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> El equipo de Power BI está ampliando continuamente los orígenes de datos disponibles en Power BI Desktop y en el servicio Power BI. Por lo tanto, a menudo verá las versiones anteriores de orígenes de datos en proceso de desarrollo marcados como **Beta** o **Versión preliminar**. Cualquier origen de datos marcada como **Beta** o **Versión preliminar** tiene una compatibilidad y funcionalidades limitadas y no se debe usar en entornos de producción. Además, es posible que los orígenes de datos marcados como **Beta** o **Versión preliminar** para Power BI Desktop no estén disponibles para su uso en el servicio Power BI u otros servicios de Microsoft hasta que el origen de datos esté disponible con carácter general (GA).

> [!NOTE]
> Hay muchos conectores de datos para Power BI Desktop que requieren Internet Explorer 10 (o posterior) para la autenticación. 


## <a name="data-sources"></a>Orígenes de datos

En el cuadro de diálogo **Obtener datos** se organizan los tipos de datos en las categorías siguientes:

* Todo
* Archivo
* Base de datos
* Power Platform
* Azure
* Servicios en línea
* Otros

La categoría **Todos** incluye todos los tipos de conexión de datos de todas las categorías.

### <a name="file-data-sources"></a>Orígenes de datos de archivo

La categoría **Archivo** proporciona las siguientes conexiones de datos:

* Excel
* Texto o CSV
* XML
* JSON
* Carpeta
* PDF
* Carpeta de SharePoint

La siguiente imagen muestra la ventana **Obtener datos** para **Archivo**.

![Orígenes de datos de archivo, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>Orígenes de datos de base de datos

La categoría **Base de datos** proporciona las siguientes conexiones de datos:

* Base de datos SQL Server
* Base de datos Access
* Base de datos SQL Server Analysis Services
* Base de datos Oracle
* Base de datos IBM DB2
* Base de datos Informix de IBM (beta)
* IBM Netezza
* Base de datos MySQL
* Base de datos PostgreSQL
* Base de datos Sybase
* Base de datos Teradata
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
* Denodo
* Dremio
* Exasol
* Indexima (Beta)
* InterSystems IRIS (Beta)
* Jethro (beta)
* Kyligence
* MarkLogic

> [!NOTE]
> Para habilitar algunos conectores de bases de datos, debe seleccionar primero **Archivo > Opciones y configuración > Opciones** y, después, **Características en vista previa**. Si no ve algunos de los conectores mencionados anteriormente y quiere usarlos, compruebe la configuración de **Características en vista previa**. Tenga también en cuenta que cualquier origen de datos marcada como *Beta* o *Versión preliminar* tiene una compatibilidad y funcionalidades limitadas, y no debe usarse en entornos de producción.

La siguiente imagen muestra la ventana **Obtener datos** para **Base de datos**.

![Orígenes de datos de base de datos, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Orígenes de datos de Power Platform

La categoría **Power Platform** proporciona las conexiones de datos siguientes:

* Conjuntos de datos de Power BI
* Flujos de datos de Power BI
* Common Data Service
* Flujos de datos de Power Platform

En la imagen siguiente se muestra la ventana **Obtener datos** para **Power Platform**.

![Orígenes de datos de Power Platform, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Orígenes de datos de Azure

La categoría **Azure** proporciona las siguientes conexiones de datos:

* Base de datos de Azure SQL
* Azure SQL Data Warehouse
* Base de datos de Azure Analysis Services
* Azure Blob Storage
* Azure Table Storage
* Azure Cosmos DB
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Azure Data Explorer (Kusto)
* Azure Cost Management
* Azure Time Series Insights (Beta)

La siguiente imagen muestra la ventana **Obtener datos** para **Azure**.

![Orígenes de datos de Azure, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Orígenes de datos de Online Services

La categoría **Online Services** proporciona las siguientes conexiones de datos:

* Lista de SharePoint Online
* Microsoft Exchange Online
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
* LinkedIn Sales Navigator (Beta)
* MailChimp (Beta)
* Marketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One - PRM (Beta)
* PlanView Projectplace (Beta)
* QuickBooks Online (Beta)
* Smartsheet
* SparkPost (Beta)
* SweetIQ (Beta)
* Planview Enterprise One - CTM (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* Zendesk (Beta)
* Dynamics 365 Customer Insights (Beta)
* Origen de datos de Emigo
* Entersoft Business Suite (Beta)
* Industrial App Store
* Intune Data Warehouse (Beta)
* Microsoft Graph Security (Beta)
* Product Insights (Beta)
* Quick Base
* TeamDesk (Beta)
* Workplace Analytics (Beta)

La imagen siguiente muestra la ventana **Obtener datos** para **Online Services**

![Orígenes de datos de Online Services, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>Otros orígenes de datos

La categoría **Otros** proporciona las siguientes conexiones de datos:

* Web
* Lista de SharePoint
* Fuente de OData
* Active Directory
* Microsoft Exchange
* Archivo Hadoop (HDFS)
* Spark
* Script de R
* Script de Python
* ODBC
* OLE DB
* BI360: informes presupuestarios y financieros (Beta)
* Information Grid (Beta)
* Paxata
* QubolePresto (Beta)
* Roamler (Beta)
* Siteimprove (Beta)
* SurveyMonkey (Beta)
* Tenforce (Smart)List (Beta)
* Vena (Beta)
* Dimensiones de Workforce (Beta)
* Consulta en blanco

La siguiente imagen muestra la ventana **Obtener datos** para **Otros**.

![Otros orígenes de datos, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> En este momento, no es posible conectarse a orígenes de datos personalizados que se protegen mediante Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Conectarse a un origen de datos

Para conectarse a un origen de datos, seleccione el origen de datos en la ventana **Obtener datos** y seleccione **Conectar**. En la siguiente imagen, la opción **Web** está seleccionada en la categoría de conexión de datos **Otros** .

![Conectar a la Web, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

Se muestra una ventana de conexión, específica al tipo de conexión de datos. Si se necesitan credenciales, se le pedirá que las proporcione. La siguiente imagen muestra una dirección URL que se escribió para conectarse a un origen de datos web.

![Dirección URL de entrada, cuadro de diálogo Desde la Web, Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

Escriba la dirección URL o la información de conexión de recurso y, luego, seleccione **Aceptar**. Power BI Desktop realiza la conexión al origen de datos y presenta los orígenes de datos disponibles en el **Navegador**.

![Cuadro de diálogo Navegador, Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Para cargar los datos, seleccione el botón **Cargar** en la parte inferior del panel **Navegador**. Para transformar o editar la consulta en el Editor de Power Query antes de cargar los datos, seleccione el botón **Transformar datos**.

Eso es todo lo que se necesita para conectarse a orígenes de datos en Power BI Desktop. Intente conectarse a datos de nuestra lista de orígenes de datos en crecimiento y vuelva a consultarla con frecuencia, debido a que siempre agregamos elementos a esta lista.

## <a name="using-pbids-files-to-get-data"></a>Usar archivos PBIDS para obtener datos

Los archivos PBIDS son archivos de Power BI Desktop con una estructura específica y tienen la extensión .PBIDS para identificarlos como archivo de origen de datos de Power BI.

Un archivo .PBIDS se puede crear para optimizar la experiencia **Obtener datos** de los creadores de informes de la organización. Para facilitar que el autor de un informe nuevo use los archivos PBIDS, lo recomendable es que un administrador cree estos archivos para las conexiones de uso frecuente.

Cuando un autor abre un archivo .PBIDS, Power BI Desktop se abre y pide al usuario las credenciales para autenticarse y conectarse al origen de datos especificado en el archivo. El cuadro de diálogo **Navegación** se abre y el usuario debe seleccionar las tablas del origen de datos que quiera cargar en el modelo. Puede que también deba seleccionar las bases de datos si no hay ninguna especificada en el archivo .PBIDS.

A partir de ese momento, el usuario puede empezar a crear visualizaciones o seleccionar **Orígenes recientes** para cargar un conjunto de tablas nuevo en el modelo.

Actualmente, los archivos .PBIDS solo admiten un único origen de datos en un archivo. Si se especifica más de un origen de datos, se producirá un error.

Para crear el archivo PBIDS, un administrador debe especificar las entradas necesarias para una única conexión. También pueden especificar el modo de conexión como DirectQuery o Importar. Si el **modo** no existe o es nulo en el archivo, se pedirá al usuario que abre el archivo en Power BI Desktop que seleccione **DirectQuery** o **Importar**.

### <a name="pbids-file-examples"></a>Ejemplos de archivos PBIDS

En esta sección se proporcionan algunos ejemplos de orígenes de datos de uso frecuente. El tipo de archivo .PBIDS solo admite las conexiones de datos que también se admiten en Power BI Desktop, salvo dos excepciones: Live Connect y las Consultas en blanco.

El archivo .PBIDS *no* incluye información de autenticación ni de tablas y esquemas.  

En los fragmentos de código siguientes se muestran varios ejemplos comunes de archivos PBIDS, pero no son completos. En el caso de otros orígenes de datos, puede consultar el [Formato de referencia de origen de datos (DSR)](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification) para obtener información sobre protocolos y direcciones.

Le presentamos estos ejemplos por su carácter práctico, pero no están diseñados para ser exhaustivos ni incluyen todos los conectores admitidos en formato DSR. Un administrador o una organización pueden crear sus propios orígenes de datos tomando estos ejemplos como guía y utilizarlos para crear y respaldar sus propios archivos de origen de datos.

#### <a name="azure-as"></a>Azure AS

```json
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

#### <a name="folder"></a>Carpeta

```json
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

#### <a name="odata"></a>OData

```json
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

#### <a name="sap-bw"></a>SAP BW

```json
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

#### <a name="sap-hana"></a>SAP HANA

```json
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

#### <a name="sharepoint-list"></a>Lista de SharePoint

La dirección URL debe llevar al sitio de SharePoint en sí y no a una lista dentro del sitio. Los usuarios obtienen un navegador que les permite seleccionar una o más listas de ese sitio, cada una de las cuales se convierte en una tabla del modelo.

```json
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

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>Archivo de texto

```json
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

#### <a name="web"></a>Web

```json
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

#### <a name="dataflow"></a>Flujo de datos

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>Pasos siguientes

Puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)
