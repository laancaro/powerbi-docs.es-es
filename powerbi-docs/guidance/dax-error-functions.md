---
title: 'DAX: Uso adecuado de las funciones de error'
description: Instrucciones sobre cuándo usar las funciones de error de DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: ae4e9081930b0f6934a557ba45afd99dd8dfc05d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875637"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Uso adecuado de las funciones de error

Este artículo va dirigido a los modeladores de datos que definen expresiones DAX.

## <a name="background"></a>Fondo

Al escribir una expresión DAX que podría generar un error en tiempo de evaluación, puede considerar el uso de dos funciones de DAX útiles.

- La función [ISERROR](/dax/iserror-function-dax), que toma una sola expresión y devuelve TRUE si se produce un error.
- La función [IFERROR](/dax/iferror-function-dax), que toma dos expresiones. Si la primera expresión genera un error, se devuelve el valor de la segunda expresión. En realidad, es una implementación más optimizada del anidamiento de la función ISERROR dentro de una función [IF](/dax/if-function-dax).

Sin embargo, aunque estas funciones pueden ser útiles y pueden contribuir a escribir expresiones fáciles de entender, también pueden degradar significativamente el rendimiento de los cálculos. Esto se debe a que estas funciones aumentan el número de exámenes del motor de almacenamiento necesarios.

Tenga en cuenta que la mayoría de los errores en tiempo de evaluación se deben a valores BLANK o cero inesperados, o a una conversión de tipo de datos no válida.

## <a name="recommendations"></a>Recomendaciones

Es mejor evitar el uso de las funciones ISERROR e IFERROR. En su lugar, aplique estrategias defensivas al desarrollar el modelo y escribir expresiones. Estas pueden incluir:

- **Garantizar que se cargan datos de calidad en el modelo:** Utilice transformaciones de Power Query para quitar o sustituir valores no válidos o ausentes, y para establecer los tipos de datos correctos. También se puede utilizar una transformación de Power Query para filtrar las filas cuando se producen errores, como la conversión de datos no válida.

    También se puede controlar la calidad de los datos si se establece la propiedad **Is Nullable** de la columna del modelo en Off, lo que producirá un error en la actualización de los datos en caso de que se encuentren valores BLANK. Tenga en cuenta que, si se produce este error, los datos cargados como resultado de una actualización correcta permanecerán en las tablas.
- **Uso de la función IF:** La expresión de la prueba lógica de la función IF se puede usar para determinar si se produciría un resultado de error. Tenga en cuenta que, al igual que las funciones ISERROR e IFERROR, esta función puede producir exámenes adicionales del motor de almacenamiento, pero es probable que funcione mejor que estos ya que no es necesario generar ningún error.
- **Usar funciones tolerantes a errores:** Algunas funciones de DAX probarán y compensarán las condiciones de error. Estas funciones permiten especificar un resultado alternativo que se devolvería en su lugar. La función[DIVIDE](/dax/divide-function-dax) es un ejemplo de este tipo. Para obtener más información sobre esta función, lea el artículo [DAX: función DIVIDE frente al operador de división (/)](dax-divide-function-operator.md).

## <a name="example"></a>Ejemplo

La expresión de medida siguiente comprueba si se produciría un error. Devuelve BLANK en esta instancia (que es el caso cuando no se proporciona la función IF con una expresión de valor por si es falso).
```dax
= IF(ISERROR([Profit] / [Sales]))
```
La siguiente versión de la expresión de medida se ha mejorado mediante el uso de la función IFERROR en lugar de las funciones IF e ISERROR.
```dax
= IFERROR([Profit] / [Sales], BLANK())
```
Sin embargo, esta versión final de la expresión de medición consigue el mismo resultado, pero de forma más eficaz y elegante.
```dax
= DIVIDE([Profit], [Sales])
```