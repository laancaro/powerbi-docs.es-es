---
title: Descripción de la seguridad de nivel de fila (RLS) con Power BI Desktop
description: Cómo configurar la seguridad de nivel de fila para conjuntos de datos importados, y DirectQuery, en Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 12/05/2019
LocalizationGroup: Create reports
ms.openlocfilehash: abbd8f34f42bdcfdca6e65df58c78bf394f00d91
ms.sourcegitcommit: 9a265d8117cc202f5f700286b5ff42a631aacdb4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "74882811"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Seguridad de nivel de fila (RLS) con Power BI Desktop

Puede usar la seguridad de nivel de fila (RLS) con Power BI Desktop para restringir el acceso a los datos a determinados usuarios. Los filtros restringen los datos en el nivel de fila. Puede definir filtros en roles.

Ahora puede configurar RLS para los modelos de datos que se han importado en Power BI con Power BI Desktop. También puede configurar RLS en conjuntos de datos en los que se usa [DirectQuery](desktop-use-directquery.md), como SQL Server. Anteriormente, solo podía implementar RLS en modelos locales de Analysis Services fuera de Power BI. Para las conexiones activas de Analysis Services, la seguridad de nivel de fila se configura en el modelo local. La opción de seguridad no se muestra para conjuntos de datos de conexión dinámica.

> [!IMPORTANT]
> Si ha definido roles y reglas dentro del servicio Power BI, tiene que volver a crear esos roles dentro de Power BI Desktop y publicar el informe en el servicio.

Obtenga más información sobre las opciones de [RLS dentro del servicio Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Pasos siguientes

[Seguridad de nivel de fila (RLS) con el servicio Power BI](service-admin-rls.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)