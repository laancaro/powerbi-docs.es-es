---
title: Cambio del modo de ordenar un gráfico en un informe
description: Cambio del modo de ordenar un gráfico en un informe de Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852383"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Cambio del modo de ordenar un gráfico en un informe de Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

En el servicio Power BI, puede cambiar el aspecto de un objeto visual al ordenar por campos de datos diferentes. Al cambiar cómo se ordena un objeto visual, puede resaltar la información que quiere transmitir y asegurarse de que el objeto visual refleja la tendencia (o énfasis).

Independientemente de si usa datos numéricos (como cifras de ventas) o datos de texto (como nombres de estado), puede ordenar sus visualizaciones de la forma que quiera y proporcionarles el aspecto que quiere que tengan. Power BI proporciona mucha flexibilidad para la ordenación y menús rápidos para su uso. En cualquier objeto visual, seleccione **Más acciones** (...) y, a continuación, seleccione el campo por el que desea ordenar.

![gráfico de barras ordenado alfabéticamente por eje X](media/end-user-change-sort/power-bi-more-actions.png)

Los objetos visuales de un panel no se pueden ordenar, pero en un informe de Power BI puede ordenar la mayoría de las visualizaciones alfabéticamente por los nombres de las categorías del gráfico o bien por los valores numéricos de cada categoría. Por ejemplo, este gráfico está ordenado alfabéticamente por la categoría **nombre de tienda**.

![gráfico de barras ordenado alfabéticamente por eje X](media/end-user-change-sort/pbi-chartsortcategory.png)

Es fácil cambiar el criterio de ordenación y pasar de una categoría (nombre de almacén) a un valor (ventas por metro cuadrado).

1. Seleccione **Más acciones** (…) y elija **Ordenar por > Ventas por metro cuadrado**.
2. Si es necesario, vuelva a seleccionar **Más acciones** (...) y elija **Orden descendente**. El campo que se usa para ordenar está en negrita y tiene una barra amarilla.

   ![vídeo que muestra la selección de ordenar por y, a continuación, ascendente, descendente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> No todos los objetos visuales se pueden ordenar. Por ejemplo, los siguientes objetos visuales no se pueden ordenar: gráfico de rectángulos, mapa, mapa coroplético, dispersión, medidor, tarjeta y cascada.

## <a name="saving-changes-you-make-to-sort-order"></a>Guardar los cambios realizados en el criterio de ordenación
Los informes de Power BI conservan los filtros, las segmentaciones, la ordenación y otros cambios que se realizan en la vista de datos. Por lo que si sale de un informe y vuelve más tarde, se guardan los cambios.  Si quiere revertir los cambios a la configuración del diseñador del informe, seleccione **Restablecer valores predeterminados** en la barra de menús superior. 

![ordenación persistente](media/end-user-change-sort/power-bi-reset.png)

Pero, si el botón **Restablecer valores predeterminados** está atenuado, significa que el diseñador del informe ha deshabilitado la capacidad de guardar (conservar) los cambios.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordenación siguiendo otros criterios
Es posible que, a veces, quiera ordenar el objeto visual mediante un campo diferente (que no está incluido en el objeto visual) o siguiendo otros criterios.  Por ejemplo, quizás quiera ordenarlo por mes (y no en orden alfabético) o por números enteros en lugar de dígitos (ejemplo, 0, 1, 9, 20 y no 0, 1, 20, 9).  El diseñador del informe podrá actualizar el conjunto de datos para habilitar este tipo de ordenación. Para encontrar la información de contacto del diseñador, seleccione el nombre del informe en la barra de encabezado.

![Elemento desplegable que muestra la información de contacto](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Pasos siguientes
Más información sobre [Visualizaciones en Power BI](end-user-visualizations.md).

[Power BI: Conceptos básicos](end-user-basic-concepts.md)
