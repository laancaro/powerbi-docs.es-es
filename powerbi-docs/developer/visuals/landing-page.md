---
title: Adición de una página de aterrizaje a los objetos visuales de Power BI
description: En este artículo se describe cómo agregar una página de aterrizaje a objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: fdf9496c564372e385879b3e0a3feb392d10ff90
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879976"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Adición de una página de aterrizaje a los objetos visuales de Power BI

Con la API 2.3.0, puede agregar una página de aterrizaje a los objetos visuales de Power BI. Para ello, agregue `supportsLandingPage` a las funcionalidades y establézcalo en true. Esta acción inicializa y actualiza el objeto visual antes de agregarle datos. Dado que el objeto visual ya no muestra una marca de agua, puede diseñar su propia página de aterrizaje para que se muestre en el objeto visual siempre que no tenga datos.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

En la imagen siguiente se muestra una página de aterrizaje de ejemplo:

![captura de pantalla de la página de aterrizaje](./media/landing-page.png)
