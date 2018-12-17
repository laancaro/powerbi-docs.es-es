---
title: Solución de problemas de origen de datos no admitido para la actualización
description: Solución de problemas de origen de datos no admitido para la actualización
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 08931086d05ca3fe7edba2cd195a4f6f61cfccc7
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53025930"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Solución de problemas de origen de datos no admitido para la actualización
Puede ver un error al intentar configurar un conjunto de datos para la actualización programada.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Esto sucede cuando no se admite el origen de datos que usa, en Power BI Desktop, para la actualización. Tendrá que buscar el origen de datos que está usando y compararlo con la lista de orígenes de datos compatibles en [Actualizar datos en Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Búsqueda del origen de datos
Si no está seguro de qué origen de datos se utilizó, puede encontrarlo siguiendo los siguientes pasos en Power BI Desktop.  

1. En Power BI Desktop, asegúrese de que se encuentra en el panel **Informe** .  
   ![Panel de informes de Desktop](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Seleccione **Editar consultas** en la barra de cinta.  
   ![Editar consultas](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Seleccione **Editor avanzado**.  
   ![Editor avanzado](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Tome nota del proveedor que aparece para el origen.  En este ejemplo, el proveedor es Active Directory.  
   ![Proveedor del origen de datos](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Compare el proveedor con la lista de orígenes de datos admitidos que se encuentra en [Actualizar datos en Power BI](refresh-data.md).  Encontrará que Active Directory no es un origen de datos compatible para la actualización.  

## <a name="next-steps"></a>Pasos siguientes
[Actualización de datos](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[On-premises Data Gateway (Puerta de enlace de datos local)](service-gateway-onprem.md)  
[Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md)  
[Solución de problemas de Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

