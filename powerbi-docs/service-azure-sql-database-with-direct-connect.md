---
title: Azure SQL Database con DirectQuery
description: Azure SQL Database con DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/20/2018
LocalizationGroup: Data from databases
ms.openlocfilehash: f03f4933566a8c18510ef0ce07b71db61ecfa8fd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770599"
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

> [!Important]
> Hemos mejorado la conectividad con Azure SQL Database.  Use Power BI Desktop para disfrutar de la mejor experiencia de conexión al origen de datos de Azure SQL Database.  Una vez creados el modelo y el informe, puede publicarlos en el servicio Power BI.  El conector directo de Azure SQL Database en el servicio Power BI se encuentra en desuso.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop y DirectQuery

Para conectarse a Azure SQL Database mediante DirectQuery, debe usar Power BI Desktop. Este enfoque proporciona más flexibilidad y capacidades. Los informes creados mediante Power BI Desktop se pueden publicar en el servicio Power BI. Puede obtener más información sobre cómo conectarse a [Azure SQL Database mediante DirectQuery](desktop-use-directquery.md) en Power BI Desktop.

## <a name="single-sign-on"></a>Inicio de sesión único

Después de publicar un conjunto de datos DirectQuery de Azure SQL en el servicio, puede habilitar el inicio de sesión único (SSO) a través de OAuth2 de Azure Active Directory (Azure AD) para los usuarios finales.

Para habilitar el inicio de sesión único, vaya a la configuración del conjunto de datos, abra la pestaña **Orígenes de datos** y active la casilla SSO.

![Configuración del cuadro de diálogo de Azure SQL con DirectQuery](media/service-azure-sql-database-with-direct-connect/sso-dialog.png)

Cuando se habilita la opción SSO y los usuarios pueden acceder a los informes creados sobre el origen de datos, Power BI envía sus credenciales autenticadas de Azure AD en las consultas a la instancia de Azure SQL Database. Esto permite a Power BI respetar la configuración de seguridad establecida en el nivel de origen de datos.

La opción SSO surte efecto en todos los conjuntos de datos que usan este origen de datos. No afecta el método de autenticación utilizado para los escenarios de importación.

> [!Note]
> No se admite Azure Multi-Factor Authentication (MFA). Los usuarios que quieran usar SSO con Azure SQL DirectQuery deben excluirse de MFA.

## <a name="finding-parameter-values"></a>Buscar valores de parámetro

El nombre completo del servidor y el nombre de la base de datos pueden encontrarse en Azure Portal.

![Nueva actualización de puerto de Azure](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Actualización del portal Azure](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Pasos siguientes

* [Usar DirectQuery en Power BI Desktop](desktop-use-directquery.md)  
* [¿Qué es Power BI?](power-bi-overview.md)  
* [Obtener datos para Power BI](service-get-data.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
