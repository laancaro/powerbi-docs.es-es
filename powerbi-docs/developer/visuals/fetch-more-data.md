---
title: Captura de más datos
description: Habilitación de la captura segmentada de grandes conjuntos de datos para objetos visuales de Power BI
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425077"
---
# <a name="fetch-more-data-from-power-bi"></a>Captura de más datos desde Power BI

Cargue más API de datos para superar el límite máximo de 30000 puntos de datos. Los datos se reciben en fragmentos. El tamaño del fragmento se puede configurar para mejorar el rendimiento en función del caso de uso.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Habilitación de la captura segmentada de grandes conjuntos de datos

Para el modo de segmento `dataview`, defina un valor dataReductionAlgorithm de "window" en el archivo `capabilities.json` del objeto visual para el elemento dataViewMapping necesario.
`count` determinará el tamaño de la ventana, que limita el número de las filas de datos nuevas que se anexan a `dataview` en cada actualización.

Para agregar en capabilities.json

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Los segmentos nuevos se anexan al objeto `dataview` existente y se proporcionan al objeto visual como una llamada a `update`.

## <a name="usage-in-the-custom-visual"></a>Uso en el objeto visual personalizado

La indicación de si existen datos o no puede determinarse mediante la comprobación de la existencia de `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

También se puede comprobar si se trata de la primera actualización o una posterior mediante la comprobación de `options.operationKind`.

`VisualDataChangeOperationKind.Create` significa el primer segmento y `VisualDataChangeOperationKind.Append` los segmentos posteriores.

Vea el fragmento de código siguiente para obtener una implementación de ejemplo:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

También se podría invocar el método `fetchMoreData` desde un controlador de eventos de la interfaz de usuario.

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI llamará al método `update` del objeto visual con un nuevo segmento de datos como respuesta a la llamada al método `this.host.fetchMoreData`.

> [!NOTE]
> En la actualidad, Power BI limitará el total de datos recuperados a **100 MB** para evitar restricciones de memoria del cliente. Puede detectar que se alcanza este límite cuando fetchMoreData() devuelve "false".*
