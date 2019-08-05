---
title: Representación de eventos
description: Los objetos visuales de Power BI pueden notificar a Power BI que están listos para la exportación a Power Point o PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425100"
---
# <a name="event-service"></a>Servicio de eventos

La nueva API consta de tres métodos (iniciado, finalizado o con error) que se deben llamar durante la representación.

Cuando se inicia la representación, el código del objeto visual personalizado llama al método renderingStarted para indicar que se ha iniciado el proceso de representación.

Si la representación se ha completado de forma correcta, el código del objeto visual personalizado llamará inmediatamente al método `renderingFinished` para notificar a los agentes de escucha (**principalmente "Exportar a PDF" y "Exportar a PowerPoint"** ) que la imagen del objeto visual está lista.

En caso de que se produzca un problema durante el proceso de representación, que impida que el objeto visual personalizado se complete correctamente, el código del objeto visual personalizado debe llamar al método `renderingFailed` para notificar al agente de escucha que el proceso de representación no se ha completado. Este método también proporciona una cadena opcional para la causa del error.

## <a name="usage"></a>Usage (Uso)

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Ejemplo sencillo. El objeto visual no tiene ninguna animación durante la representación

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

### <a name="sample-the-visual-with-animation"></a>Ejemplo. El objeto visual con animación

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
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Representación de eventos para la certificación de objetos visuales

La compatibilidad del objeto visual con la representación de eventos es uno de los requisitos de certificación de objetos visuales. Más información sobre [requisitos de certificación](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
