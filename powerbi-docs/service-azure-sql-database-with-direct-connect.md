---
title: Azure SQL Database con DirectQuery
description: Azure SQL Database con DirectQuery
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/18/2017
ms.author: maghan
LocalizationGroup: Data from databases
ms.openlocfilehash: 27b2eb90a07d3112b771fd3ee23cc86353a46991
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34242258"
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL Database con DirectQuery
Obtenga información sobre cómo puede conectarse directamente a Azure SQL Database y crear informes que usan datos activos. Puede mantener los datos en el origen y no en Power BI.

Con DirectQuery, las consultas se envían a Azure SQL Database a medida que explora los datos en la vista de informe. Se sugiere esta experiencia para los usuarios que están familiarizados con las bases de datos y entidades a las que se conectan.

**Notas:**

* Especifique el nombre completo del servidor cuando se conecte (consulte más abajo para obtener más detalles)
* Asegúrese de que las reglas de firewall para la base de datos están configuradas en "[Permitir el acceso a los servicios de Azure](https://msdn.microsoft.com/library/azure/ee621782.aspx)"
* Cada acción, como seleccionar una columna o agregar un filtro, enviará una consulta a la base de datos
* Los iconos se actualizan cada hora (no es necesario programar la actualización). Se puede ajustar en la configuración avanzada al conectarse.
* Preguntas y respuestas no está disponible para conjuntos de datos de DirectQuery.
* Los cambios de esquema no se recogen automáticamente

Estas restricciones y notas pueden cambiar mientras seguimos mejorando las experiencias. A continuación, se detallan los pasos para conectarse. 

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop y DirectQuery
Para conectarse a Azure SQL Database mediante DirectQuery, debe usar Power BI Desktop. Este enfoque proporciona más flexibilidad y capacidades. Los informes creados mediante Power BI Desktop se pueden publicar en el servicio Power BI. Puede obtener más información sobre cómo conectarse a [Azure SQL Database mediante DirectQuery](desktop-use-directquery.md) en Power BI Desktop. 

## <a name="single-sign-on"></a>Inicio de sesión único

Después de publicar un conjunto de datos DirectQuery de Azure SQL en el servicio, puede habilitar el inicio de sesión único (SSO) a través de OAuth2 de Azure Active Directory (Azure AD) para los usuarios finales. 

Para habilitar el inicio de sesión único, vaya a la configuración del conjunto de datos, abra la pestaña **Orígenes de datos** y active la casilla SSO.

![Configuración del cuadro de diálogo de Azure SQL con DirectQuery](media/service-azure-sql-database-with-direct-connect/sso-dialog.png)

Cuando se habilita la opción SSO y los usuarios pueden acceder a los informes creados sobre el origen de datos, Power BI envía sus credenciales autenticadas de Azure AD en las consultas a la instancia de Azure SQL Database. Esto permite a Power BI respetar la configuración de seguridad establecida en el nivel de origen de datos.

La opción SSO surte efecto en todos los conjuntos de datos que usan este origen de datos. No afecta el método de autenticación utilizado para los escenarios de importación.

## <a name="finding-parameter-values"></a>Buscar valores de parámetro
El nombre completo del servidor y el nombre de la base de datos pueden encontrarse en Azure Portal.

![](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Pasos siguientes
[Usar DirectQuery en Power BI Desktop](desktop-use-directquery.md)  
[Introducción a Power BI](service-get-started.md)  
[Obtener datos para Power BI](service-get-data.md)  
¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
