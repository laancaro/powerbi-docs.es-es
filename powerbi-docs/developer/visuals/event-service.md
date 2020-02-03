---
title: Representación de eventos en objetos visuales de Power BI
description: Los objetos visuales de Power BI pueden notificar a Power BI que están listos para la exportación a PowerPoint o PDF.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 873968a89a230171d8fecba81a7d528767ee7077
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819155"
---
# <a name="render-events-in-power-bi-visuals"></a>Representación de eventos en objetos visuales de Power BI

La nueva API consta de tres métodos (`started`, `finished` o `failed`) a los que se debe llamar durante la representación.

Cuando se inicia la representación, el código del objeto visual de Power BI llama al método `renderingStarted` para indicar que se ha iniciado el proceso de representación.

Si la representación se completa correctamente, el código del objeto visual de Power BI llama inmediatamente al método `renderingFinished` para notificar a los clientes de escucha (principalmente *Exportar a PDF* y *Exportar a PowerPoint*) que la imagen del objeto visual está lista para exportarse.

Si se produce un problema durante el proceso, se impide que el objeto visual de Power BI se represente correctamente. Para notificar a los clientes de escucha que el proceso de representación no se ha completado, el código del objeto visual de Power BI debe llamar al método `renderingFailed`. Este método también proporciona una cadena opcional para proporcionar un motivo del error.

## <a name="usage"></a>Uso

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Ejemplo: El objeto visual no muestra animaciones

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Ejemplo: El objeto visual muestra animaciones

Si el objeto visual tiene animaciones o funciones asincrónicas para la representación, se debe llamar al método `renderingFinished` después de la animación o dentro de la función asincrónica.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Representación de eventos para la certificación de objetos visuales

Un requisito de certificación de objetos visuales es la compatibilidad del objeto visual con la representación de eventos. Para obtener más información, consulte [Requisitos de certificación](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements).
