---
title: Resaltado
description: Resaltado de selecciones de puntos de datos en objetos visuales de Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424824"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Resaltado de puntos de datos en objetos visuales de Power BI

De forma predeterminada, cada vez que se selecciona un elemento, la matriz `values` del objeto `dataView` se filtra solo por los valores seleccionados. Hará que todos los demás objetos visuales de la página muestren solo los datos seleccionados.

![Comportamiento predeterminado del resaltado de "DataView"](./media/highlight-dataview.png)

Si establece la propiedad `supportsHighlight` de `capabilities.json` en `true`, recibirá la matriz `values` completa sin filtrar junto con una matriz `highlights`. La matriz `highlights` tendrá la misma longitud que la matriz de valores y todos los valores no seleccionados se establecerán en `null`. Con esta propiedad habilitada, el objeto visual es el responsable de resaltar los datos adecuados mediante la comparación de la matriz `values` con la matriz `highlights`.

![Compatibilidad con el resaltado en la vista de datos](./media/highlight-dataview-supports.png)

En el ejemplo, observará que la barra 1 está seleccionada. Y es el único valor de la matriz highlights. También es importante tener en cuenta que puede haber varias selecciones y resaltado parcial. Existe el valor numérico correspondiente en los valores y las matrices highlights estarán presentes pero serán distintas.
