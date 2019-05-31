---
title: Descripción de la seguridad de nivel de fila (RLS) con Power BI Desktop
description: Cómo configurar la seguridad de nivel de fila para conjuntos de datos importados, y DirectQuery, en Power BI Desktop.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 05/03/2018
LocalizationGroup: Create reports
ms.openlocfilehash: e53805c8aa76fd2fe80246eb0974ec73bedd4d4f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769552"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Seguridad de nivel de fila (RLS) con Power BI Desktop

La Seguridad de nivel de fila (RLS) con Power BI Desktop restringe el acceso a los datos a determinados usuarios. Los filtros restringen los datos en el nivel de fila. Puede definir filtros en roles.

Ahora puede configurar RLS para los modelos de datos que se han importado en Power BI con Power BI Desktop. También puede configurar RLS en conjuntos de datos que utilizan DirectQuery, como SQL Server. Anteriormente, solo podía implementar RLS en modelos locales de Analysis Services fuera de Power BI. Para las conexiones activas de Analysis Services, la seguridad de nivel de fila se configura en el modelo local. La opción de seguridad no se muestra para conjuntos de datos de conexión dinámica.

> [!IMPORTANT]
> Si ha definido roles y reglas dentro del servicio Power BI, tendrá que volver a crear esos roles dentro de Power BI Desktop y publicar el informe en el servicio.

Obtenga más información sobre las opciones de [RLS dentro del servicio Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Pasos siguientes

[Seguridad de nivel de fila (RLS) con el servicio Power BI](service-admin-rls.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)