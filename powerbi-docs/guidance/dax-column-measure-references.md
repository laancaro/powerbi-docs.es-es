---
title: 'DAX: Referencias de columnas y medidas'
description: Instrucciones para hacer referencia a columnas en las medidas en expresiones DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 3ca49008639f7e3e084c8d045bc911aff57b7b21
ms.sourcegitcommit: 0da17de80c9651f9f4474d1abb1bdaaade8808fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2019
ms.locfileid: "75498746"
---
# <a name="dax-column-and-measure-references"></a>DAX: Referencias de columnas y medidas

Como modelador de datos, las expresiones DAX harán referencia a las columnas y medidas del modelo. Las columnas y las medidas siempre están asociadas a las tablas del modelo, pero estas asociaciones son diferentes. Por tanto, hay distintas recomendaciones sobre cómo hará referencia a ellas en las expresiones.

## <a name="columns"></a>Columnas

Una columna es un objeto de nivel de tabla y los nombres de columna deben ser únicos en una tabla. Por tanto, se puede usar el mismo nombre de columna varias veces en el modelo, siempre que pertenezca a tablas diferentes. Hay una regla más: un nombre de columna no puede ser el mismo que el de una medida o una jerarquía de la misma tabla.

Por lo general, DAX no forzará el uso de una referencia _completa_ a una columna. Una referencia completa significa que el nombre de la tabla precede al nombre de la columna.

Este es un ejemplo de una definición de columna calculada en la que solo se usan referencias de nombre de columna. Las columnas **Sales** y **Cost** pertenecen a una tabla denominada **Orders**.

```dax
Profit = [Sales] - [Cost]
```

Se puede volver a escribir la misma definición con referencias de columna completas.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Pero, en ocasiones, se le pedirá que use referencias de columna completas cuando Power BI detecte ambigüedades. Al escribir una fórmula, se le avisará mediante un mensaje de error con una línea ondulada de color rojo. Además, algunas funciones DAX, como [LOOKUPVALUE](/dax/lookupvalue-function-dax), requieren el uso de columnas completas.

Se recomienda usar siempre nombres completos para las referencias de columna. Los motivos se proporcionan en la sección [Recomendaciones](#recommendations).

## <a name="measures"></a>Medidas

Una medida es un objeto de nivel de modelo. Por esta razón, los nombres de medida deben ser únicos en el modelo. Pero en el panel **Campos**, los autores del informe verán cada medida asociada a una sola tabla de modelo. Esta asociación se establece por motivos cosméticos y puede configurarla si establece la propiedad **Tabla inicial** de la medida. Para obtener más información, vea [Medidas en Power BI Desktop (organización de las medidas)](../desktop-measures.md#organizing-your-measures).

Es posible usar una medida completa en las expresiones. IntelliSense para DAX ofrecerá incluso la sugerencia. Pero no es necesario y no es un procedimiento recomendado. Si cambia la tabla inicial de una medida, se interrumpirán todas las expresiones en las que se use una referencia de medida completa. Después, tendrá que editar cada fórmula interrumpida para quitar (o actualizar) la referencia de la medida.

Se recomienda que nunca califique las referencias de medidas. Los motivos se proporcionan en la sección [Recomendaciones](#recommendations).

## <a name="recommendations"></a>Recomendaciones

Nuestras recomendaciones son sencillas y fáciles de recordar:

- Usar siempre nombres completos de referencias de columna
- No usar nunca nombres completos de referencias de medida

Aquí se detallan los motivos:

- **Entrada de fórmula**: se aceptarán expresiones, ya que no habrá ninguna referencia ambigua que resolver. Además, cumplirá los requisitos para las funciones DAX que requieren referencias de columna completas.
- **Solidez**: las expresiones seguirán funcionando, incluso cuando cambie una propiedad de la tabla inicial de la medida.
- **Legibilidad**: las expresiones serán rápidas y fáciles de entender: determinará rápidamente que es una columna o medida, en función de si está completa o no.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Referencia de expresiones de análisis de datos (DAX)](/dax/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
