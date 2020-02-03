---
title: Funcionalidades y propiedades de objetos visuales de Power BI
description: En este artículo se describen las funcionalidades y propiedades de los objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819201"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Incorporar un menú contextual a un objeto visual de Power BI

Puede usar `selectionManager.showContextMenu()` con parámetros `selectionId` y una posición (como un objeto `{x:, y:}`) para que Power BI muestre un menú contextual para el objeto visual.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` se presentó en Visuals API 2.2.0.

Por lo general, se agrega como un evento de clic con el botón derecho (o un evento que se mantiene presionado en los dispositivos táctiles). El menú contextual se agregó al BarChart de ejemplo como referencia:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
