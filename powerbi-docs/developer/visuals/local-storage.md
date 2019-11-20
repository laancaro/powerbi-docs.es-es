---
title: API de almacenamiento local en objetos visuales de Power BI
description: En el artículo se describe cómo usar la API de objetos visuales de Power BI para obtener acceso al almacenamiento local del explorador
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879883"
---
# <a name="local-storage-api"></a>API de almacenamiento local

La API de almacenamiento local es una API que cualquier objeto visual personalizado puede usar para solicitar al host que guarde o cargue datos desde el almacenamiento del dispositivo. Está aislado en el sentido de que hay una separación del almacenamiento entre los distintos tipos de objetos visuales.

## <a name="sample"></a>Ejemplo

Si el objeto visual personalizado debe aumentar un contador cada vez que se llama al método de actualización, pero el valor del contador también debe conservarse y no restablecerse cada vez que se inicia un objeto visual:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Problemas y limitaciones conocidos

La API de almacenamiento local no está activada de forma predeterminada para los objetos visuales personalizados. Si desea activarla para un visual personalizado, envíe una solicitud al equipo de soporte técnico de objetos visuales personalizados de Power BI `pbicvsupport@microsoft.com`
