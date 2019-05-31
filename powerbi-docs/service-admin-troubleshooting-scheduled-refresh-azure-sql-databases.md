---
title: Solución de problemas de actualización programada de bases de datos SQL de Azure
description: Solución de problemas de actualización programada de bases de datos SQL de Azure en Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 0c22d005044c0ebddc242eb35908e26689fee597
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61186915"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Solución de problemas de actualización programada de bases de datos SQL de Azure en Power BI
Para obtener pasos detallados acerca de cómo configurar la actualización programada, asegúrese de ver [Actualizar datos en Power BI](refresh-data.md).

Al configurar la actualización programada de Azure SQL Database, si se produce un error con el código de error 400 durante la edición de las credenciales, intente lo siguiente para configurar la regla de firewall apropiada:

1. Inicie sesión en el Portal de administración de Azure.
2. Vaya al servidor SQL de Azure para el que está configurando la actualización.
3. Active "Servicios de Microsoft Azure" en la sección de servicios permitidos.

![Servicios permitidos de Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

