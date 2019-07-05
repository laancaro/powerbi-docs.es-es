---
title: Conexión a conjuntos de datos de Power BI Premium con herramientas y aplicaciones cliente (versión preliminar)
description: Se describe cómo conectarse a conjuntos de datos en Power BI Premium desde herramientas y aplicaciones cliente.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/18/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 48513ea163847ee3bf1df07151e9985c5bce9656
ms.sourcegitcommit: 5f22dcda8885d840b7da344d38e89329d02b14fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67235076"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Conexión a conjuntos de datos con herramientas y aplicaciones cliente (versión preliminar)

Las áreas de trabajo y los conjuntos de datos de Power BI Premium admiten conexiones *de solo lectura* desde herramientas y aplicaciones cliente de Microsoft y de terceros. 

> [!NOTE]
> En este artículo está pensado solo para presentar la conectividad de solo lectura a áreas de trabajo y conjuntos de datos de Power BI Premium. *No* está pensado para proporcionar información detallada sobre programación, herramientas y aplicaciones específicas, arquitectura y administración de áreas de trabajo y conjuntos de datos. Los temas que se describen aquí requieren un conocimiento sólido de la administración y arquitectura de base de datos de modelos tabulares de Analysis Services.

## <a name="protocol"></a>Protocolo

En Power BI Premium se usa el protocolo [XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) (XMLA) para las comunicaciones entre las aplicaciones cliente y el motor que administra las áreas de trabajo y los conjuntos de datos. Estas comunicaciones se realizan a través de lo que normalmente se denominan puntos de conexión XMLA. XMLA es el mismo protocolo de comunicación que usa el motor de Microsoft Analysis Services, que internamente, ejecuta el modelado semántico, el gobierno, el ciclo de vida y la administración de datos de Power BI. 

La gran mayoría de las aplicaciones cliente y las herramientas no se comunican de forma explícita con el motor mediante puntos de conexión XMLA. En su lugar, usan bibliotecas de cliente como MSOLAP, ADOMD y AMO como intermediarias entre la aplicación cliente y el motor, que se comunica de forma exclusiva mediante XMLA.


## <a name="supported-tools"></a>Herramientas admitidas

Estas herramientas admiten el acceso de solo lectura a las áreas de trabajo y los conjuntos de datos de Power BI Premium:

**SQL Server Management Studio (SSMS)** : admite consultas MDX, XMLA, DAX y TraceEvent. Requiere la versión 18.0. Se puede descargar [aquí](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**SQL Server Profiler**: incluida con SSMS 18.0 (versión preliminar), esta herramienta proporciona seguimiento y depuración de eventos de servidor. Puede capturar y guardar datos sobre cada evento en un archivo o una tabla para analizarlos después. Aunque oficialmente en desuso para SQL Server, Profiler se sigue incluyendo en SSMS y todavía se admite para Analysis Services y, ahora, para Power BI Premium. Para más información, vea [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**DAX Studio**: herramienta de la comunidad de código abierto para ejecutar y analizar consultas DAX en Analysis Services. Requiere la versión 2.8.2 o superior. Para más información, vea [daxstudio.org](https://daxstudio.org/).

**Tablas dinámicas de Excel**: se requiere la versión de Hacer clic y ejecutar de Office 16.0.11326.10000 o superior.

**Terceros**: se incluyen aplicaciones y herramientas de visualización de datos de cliente que se pueden conectar, consultar y consumir conjuntos de datos en Power BI Premium. La mayoría de las herramientas requiere las versiones más recientes de las bibliotecas de cliente MSOLAP, pero algunas pueden usar ADOMD.

## <a name="client-libraries"></a>Bibliotecas de cliente

Las aplicaciones y las herramientas cliente necesitan bibliotecas de cliente para conectarse a las áreas de trabajo de Power BI Premium. Las mismas bibliotecas de cliente que se usan para la conexión a Analysis Services también se admiten en Power BI Premium. Las aplicaciones cliente de Microsoft, como Excel, SQL Server Management Studio (SSMS) y SQL Server Data Tools (SSDT) instalan las tres bibliotecas de cliente y las actualizan junto con las actualizaciones de aplicación convencionales. En algunos casos, en especial con las aplicaciones y herramientas de terceros, es posible que tenga que instalar versiones más recientes de las bibliotecas de cliente. Las bibliotecas de cliente se actualizan mensualmente. Para más información, vea [Bibliotecas de cliente para la conexión a Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>Conexión a un área de trabajo Premium

Se puede conectar a las áreas de trabajo asignadas a capacidades Premium dedicadas. Las áreas de trabajo asignadas a una capacidad dedicada tienen una cadena de conexión con formato de dirección URL. 

Para obtener la cadena de conexión del área de trabajo en Power BI, en **Configuración del área de trabajo**, en la pestaña **Premium**, en **Conexión del área de trabajo**, haga clic en **Copiar**.

![Cadena de conexión del área de trabajo](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

En las conexiones del área de trabajo se usa el formato de dirección URL siguiente para dirigirse a un área de trabajo como si fuese un nombre de servidor de Analysis Services:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Por ejemplo, `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`.

### <a name="to-connect-in-ssms"></a>Para conectarse en SSMS

En **Conectarse al servidor** > **Tipo de servidor**, seleccione **Analysis Services**. En **Nombre del servidor**, escriba la dirección URL. En **Autenticación**, seleccione **Active Directory - Universal compatible con MFA** y, después, en **Nombre de usuario**, escriba el identificador de usuario de la organización. 

Cuando se haya conectado, el área de trabajo se muestra como un servidor de Analysis Services, y los conjuntos de datos del área de trabajo se muestran como bases de datos.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Catálogo inicial

En algunas herramientas, como SQL Server Profiler, es posible que tenga que especificar un *Catálogo inicial*. Especifique un conjunto de datos (base de datos) en el área de trabajo. En **Conectarse al servidor**, haga clic en **Opciones**. En el cuadro de diálogo **Conectarse al servidor**, en **Conectar a base de datos** en la pestaña **Propiedades de conexión**, escriba el nombre del conjunto de datos.

### <a name="duplicate-workspace-name"></a>Nombre del área de trabajo duplicado

Al conectarse a un área de trabajo con el mismo nombre que otra, es posible que obtenga el error siguiente: **No se puede conectar con powerbi://api.powerbi.com/v1.0/[nombre del inquilino]/[nombre del área de trabajo].**

Para solucionar este error, además del nombre del área de trabajo, especifique el valor ObjectIDGuid, que se puede copiar desde el valor objectID del área de trabajo en la dirección URL. Anexe el valor de objectID a la dirección URL de conexión. Por ejemplo, "powerbi://api.powerbi.com/v1.0/myorg/Contoso Sales - 9d83d204-82a9-4b36-98f2-a40099093830"

### <a name="duplicate-dataset-name"></a>Nombre del conjunto de datos duplicado

Al conectarse a un conjunto de datos con el mismo nombre que otro en la misma área de trabajo, anexe el GUID del conjunto de datos al nombre del conjunto de datos. Puede obtener el nombre del conjunto de datos *y* el GUID cuando se conecta al área de trabajo en SSMS. 

### <a name="delay-in-datasets-shown"></a>Retraso en los conjuntos de datos mostrados

Al conectarse a un área de trabajo, los cambios de los conjuntos de datos nuevos, eliminados y cuyo nombre ha cambiado pueden tardar hasta 5 minutos en aparecer. 

### <a name="unsupported-datasets"></a>Conjuntos de datos no admitidos

Los conjuntos de datos siguientes no son accesibles mediante puntos de conexión XMLA. Estos conjuntos de datos *no* aparecerán en el área de trabajo en SSMS o en otras herramientas: 

- Conjuntos de datos con una conexión dinámica a modelos de Analysis Services. 
- Conjuntos de datos con datos de inserción mediante la API REST.
- Conjuntos de datos de libros de Excel. 

Los conjuntos de datos siguientes no se admiten en el servicio Power BI:   

- Conjuntos de datos con una conexión dinámica a un conjunto de datos de Power BI.

### <a name="roles-and-role-memberships"></a>Roles y pertenencias a roles

Actualmente, los roles de modelo y las pertenencias a roles no son detectables ni se muestran mediante el uso de puntos de conexión XMLA.

## <a name="audit-logs"></a>Registros de auditoría 

Cuando las herramientas y aplicaciones cliente se conectan a un área de trabajo, el acceso a través de puntos de conexión XMLA se registra en los registros de auditoría de Power BI bajo la operación **GetWorkspaces**. Para más información, vea [Auditoría de Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Vea también

[Referencias de Analysis Services](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[Protocolo tabular de SQL Server Analysis Services](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[Vistas de administración dinámica (DMV)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
