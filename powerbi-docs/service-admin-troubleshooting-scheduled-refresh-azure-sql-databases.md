---
title: Solución de problemas de actualización programada de bases de datos SQL de Azure
description: Solución de problemas de actualización programada de bases de datos SQL de Azure en Power BI
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 292f80b4fec7da9ff6ce42e3611bf4d6353bae2d
ms.sourcegitcommit: 90bd747b7c460d17b74cd386d3f5714234b1f6c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74791954"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Solución de problemas de actualización programada de bases de datos SQL de Azure en Power BI

Para obtener información detallada sobre la actualización, consulte [Actualizar datos en Power BI](refresh-data.md) y [Configuración de actualización programada](refresh-scheduled-refresh.md).

Al configurar la actualización programada de una base de datos de Azure SQL, si se produce un error con el código de error 400 al editar las credenciales, intente lo siguiente para configurar la regla de firewall apropiada:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

1. Vaya a la base de datos de Azure SQL para la que está configurando la actualización.

1. En la parte superior de la hoja **Información general**, seleccione **Establecer el firewall del servidor**.

1. En la hoja **Configuración del firewall**, asegúrese de que la opción **Permitir el acceso a servicios de Azure** esté establecida en **Activar**.

    ![Servicios permitidos de Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
