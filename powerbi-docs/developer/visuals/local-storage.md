---
title: API de almacenamiento local en objetos visuales de Power BI
description: En el artículo se describe cómo usar la API de objetos visuales de Power BI para obtener acceso al almacenamiento local del explorador
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 7665f0c8e3c909263f194a0fd54a54ed2a752c8c
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819109"
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

La API de almacenamiento local no está activada de forma predeterminada para los objetos visuales personalizados. Si quiere activarla para un objeto visual personalizado, envíe una solicitud al equipo de soporte técnico de objetos visuales personalizados de Power BI `pbicvsupport@microsoft.com`.  
**Tenga en cuenta que el objeto visual debe estar disponible en [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) y estar [certificado](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
