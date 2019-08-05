---
title: Habilitación de segmentaciones de sincronización
description: Cómo agregar la característica Segmentaciones de sincronización para objetos visuales de Power BI
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425031"
---
# <a name="sync-slicers"></a>Segmentaciones de sincronización

Para admitir [Segmentaciones de sincronización](https://docs.microsoft.com/power-bi/desktop-slicers), el objeto visual de segmentación de datos personalizado debe usar la API 1.13 o una versión posterior.

El segundo aspecto necesario es la opción habilitada en `capabilities.json` (vea un ejemplo a continuación).

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Después de los cambios en `capabilities.json`, puede ver el panel de opciones de Segmentaciones de sincronización al hacer clic en el objeto visual de segmentación de datos personalizado.

> [!NOTE]
> Si la segmentación de datos tiene más de un campo (categoría o medida), se deshabilitará la característica porque las segmentaciones de sincronización no admiten varios campos.

![Panel de segmentaciones de sincronización](./media/sync-slicers-panel.png)

En el panel, puede ver que la visibilidad de la segmentación de datos y su filtración se pueden aplicar en varias páginas del informe.
