---
title: Interacciones de objetos visuales
description: Procedimientos para comprobar que los objetos visuales de Power BI deben permitir interacciones de objetos visuales
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424502"
---
# <a name="visuals-interactions"></a>Interacciones de objetos visuales

Los objetos visuales pueden consultar el valor de la marca "allowInteractions", que indica si el objeto visual debe permitir interacciones de objetos visuales.
Por ejemplo, los objetos visuales son interactivos durante la visualización o edición de informes, pero no cuando se ven en un panel.
Estas interacciones son las de clic, desplazamiento lateral, zoom, selección y otras.
Tenga en cuenta que las informaciones sobre herramientas se deben habilitar en todos los escenarios, con independencia del valor de esta marca.

La marca "allowInteractions" se pasa como un valor booleano durante la inicialización del elemento visual, como miembro de la interfaz IVisualHost.

En cualquier escenario de Power BI en el que se requiera que los objetos visuales no sean interactivos (por ejemplo, iconos de panel), la marca "allowInteractions" se establecerá en false.
En caso contrario (por ejemplo, para informes), "allowInteractions" se establecerá en true.

Para más información, vea el [repositorio del objeto visual SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
