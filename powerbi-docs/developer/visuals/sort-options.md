---
title: Ordenar
description: Comportamiento de ordenación predeterminado para objetos visuales de Power BI.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f3d913e2bce34850dfae4c9486b2e43c78521a58
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424525"
---
# <a name="sorting-options"></a>Opciones de ordenación

`Sorting` especifica el comportamiento de ordenación predeterminado para el objeto visual.
La función necesita uno de los parámetros que se describen a continuación:

## <a name="default-sorting"></a>Ordenación predeterminada

La opción `default` es la forma más simple. Permite ordenar los datos presentados en la sección “DataMappings”.
Esta opción permite clasificar los datos de “DataMappings” por el usuario y especificar la dirección de ordenación.

```json
    "sorting": {
        "default": {   }
    }
```

![Opciones de ordenación en el menú contextual](./media/sorting.png)

## <a name="implicit-sorting"></a>Ordenación implícita

`implicit` ordena con el parámetro “array” (`clauses`), que describe la ordenación para cada rol de datos.
`implicit` significa que el usuario del objeto visual no puede cambiar el criterio de ordenación.
Power BI no mostrará las opciones de ordenación en el menú del objeto visual. Pero Power BI clasificará los datos según la configuración especificada.

Los parámetros de `clauses` pueden contener varios objetos, con dos parámetros:

- `role`: determina `DataMapping` para la ordenación.

- `direction`: determina la dirección de ordenación (1 = ascendente; 2 = descendente).

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Ordenación personalizada

`custom` significa que el desarrollador administra la ordenación en el código del objeto visual.
