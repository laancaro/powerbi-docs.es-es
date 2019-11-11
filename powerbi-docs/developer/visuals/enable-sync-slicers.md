---
title: Habilitación de la característica Segmentaciones de sincronización en objetos visuales de Power BI
description: En este artículo se describe cómo agregar la característica Segmentaciones de sincronización a objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 055878988a197b80a8e4842a6567966f75af2ce5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880139"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Segmentaciones de sincronización en objetos visuales de Power BI

Para admitir la característica [Segmentaciones de sincronización](https://docs.microsoft.com/power-bi/desktop-slicers), el objeto visual de segmentación personalizado debe usar la versión de API 1.13 o posterior.

Además, debe habilitar la opción en el archivo *capabilities.json*, tal y como se muestra en el código siguiente:

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

Después de actualizar el archivo *capabilities.json*, puede ver el panel de opciones **Segmentaciones de sincronización** al seleccionar el objeto visual de segmentación personalizado.

> [!NOTE]
> La característica Segmentaciones de sincronización no admite más de un campo. Si su segmentación tiene más de un campo (**Categoría** o **Medida**), la característica se deshabilita.

![Panel "Segmentaciones de sincronización"](./media/sync-slicers-panel.png)

En el panel **Segmentaciones de sincronización**, puede ver que la visibilidad de la segmentación y su filtración se pueden aplicar en varias páginas del informe.
