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
ms.openlocfilehash: 5365c076b75d0989df8db15c1dc16f4e11bc3f09
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448400"
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

## <a name="finding-parameter-values"></a>Buscar valores de parámetro

El nombre completo del servidor y el nombre de la base de datos pueden encontrarse en Azure Portal.

![Nueva actualización de puerto de Azure](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Actualización de Azure Portal](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>Pasos siguientes

* [Usar DirectQuery en Power BI Desktop](desktop-use-directquery.md)  
* [¿Qué es Power BI?](power-bi-overview.md)  
* [Obtener datos para Power BI](service-get-data.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
