---
title: Panel de análisis
description: Crea líneas de referencia dinámicas en objetos visuales de Power BI
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425537"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Panel de análisis en objetos visuales de Power BI

El **panel de análisis** se [introdujo para objetos visuales nativos](https://docs.microsoft.com/power-bi/desktop-analytics-pane) en noviembre de 2018.
Los objetos visuales personalizados con la API v2.5.0 pueden presentar y administrar sus propiedades en el panel **Análisis**.

![Panel de análisis](./media/visualization-pane-analytics-tab.png)

Se controla de forma similar a la [administración de propiedades en el panel Formato](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options), mediante la definición de un objeto en el archivo capabilities.json del objeto visual. 

Estas son las diferencias:

1. En la definición de `object`, agregue un campo de `objectCategory` con un valor de 2.

    > [!NOTE]
    > El campo `objectCategory` es un campo opcional introducido en la API 2.5.0. Define el aspecto del objeto visual que controla el objeto (1 = formato, 2 = análisis). El “Formato” se usa para la apariencia, los colores, los ejes, las etiquetas, etc. El “Análisis” se usa para las previsiones, las líneas de tendencia, las líneas de referencia, las formas, etc.
    >
    > Si se omite el valor de `objectCategory`, se usará “Formato” como el valor predeterminado.

2. El objeto necesita estas dos propiedades:
    1. `show` de tipo booleano, con “falso” como valor predeterminado.
    2. `displayName` de tipo texto. El valor predeterminado que seleccione se convertirá en el nombre para mostrar inicial de la instancia.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Pueden definirse otras propiedades de la misma forma que para los objetos de formato. La enumeración de objetos se realiza exactamente igual que en el **panel Formato**.

***Problemas y limitaciones conocidos***

  1. Aún no se admite el uso de varias instancias. Los objetos no pueden tener un [selector](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) que no sea estático (es decir, “selector”: nulo), y los objetos visuales personalizados no pueden tener varias instancias de una tarjeta definidas por el usuario.
  2. Las propiedades del tipo `integer` no se muestran correctamente. Como solución alternativa, use el tipo `numeric` en su lugar.

> [!NOTE]
> Use el panel Análisis solo para los objetos que agreguen nueva información o proporcionen nuevas perspectivas sobre la información presentada. Por ejemplo, líneas de referencia dinámicas que muestren tendencias importantes.
> Cualquier opción que controle la apariencia del objeto visual (es decir, el formato) tiene que mantenerse en el panel Formato.
