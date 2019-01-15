---
title: Solución de problemas de actualización programada de bases de datos SQL de Azure
description: Solución de problemas de actualización programada de bases de datos SQL de Azure en Power BI
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 17ee932bf0331940c7b30b020ab8fc43cdc9fdf5
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54274688"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Solución de problemas de actualización programada de bases de datos SQL de Azure en Power BI
Para obtener pasos detallados acerca de cómo configurar la actualización programada, asegúrese de ver [Actualizar datos en Power BI](refresh-data.md).

Al configurar la actualización programada de Azure SQL Database, si se produce un error con el código de error 400 durante la edición de las credenciales, intente lo siguiente para configurar la regla de firewall apropiada:

1. Inicie sesión en el Portal de administración de Azure.
2. Vaya al servidor SQL de Azure para el que está configurando la actualización.
3. Active "Servicios de Microsoft Azure" en la sección de servicios permitidos.

![Servicios permitidos de Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

