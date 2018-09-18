---
title: Cambio del modo de ordenar un gráfico en un informe de Power BI
description: Cambio del modo de ordenar un gráfico en un informe de Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 89891ead8eda1b8de4c7be943af2a9e9e98314c5
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2018
ms.locfileid: "44726096"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Cambio del modo de ordenar un gráfico en un informe de Power BI
En un informe de Power BI, puede ordenar la mayoría de las visualizaciones alfabéticamente por los nombres de las categorías del gráfico, o bien por los valores numéricos de cada categoría. Por ejemplo, este gráfico se ordena por nombre de tienda.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

Es fácil cambiar el criterio de ordenación y pasar de una categoría (nombre de almacén) a un valor (ventas por metro cuadrado).

1. Seleccione el botón de puntos suspensivos (…) y elija **Ordenar por Sales Per Sq Ft**.
2. Si es necesario, seleccione el icono de orden ![](media/power-bi-report-change-sort/sorticon.png) para cambiar a **Descendente**.

   ![](media/power-bi-report-change-sort/sortby.gif)

   **NOTA**: no todos los elementos visuales se pueden ordenar.  Por ejemplo, los siguientes objetos visuales no se pueden ordenar: Gráfico de rectángulos, Mapa, Mapa coroplético, Dispersión, Medidor, Tarjeta, Tarjeta de varias filas y Cascada.

## <a name="saving-changes-you-make-to-sort-order"></a>Guardar los cambios realizados en el criterio de ordenación
Los informes de Power BI conservan los filtros, las segmentaciones, la ordenación y otros cambios que se realizan en la vista de datos. Por lo que si sale de un informe y vuelve más tarde, se guardan los cambios.  Si quiere revertir los cambios a la configuración del autor del informe, seleccione **Restablecer valores predeterminados** en la barra de menús superior. 

![ordenación persistente](media/power-bi-report-change-sort/power-bi-reset-to-default.png)

Pero si el botón **Restablecer valores predeterminados** está atenuado, significa que el autor del informe ha deshabilitado la capacidad de guardar (conservar) los cambios.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordenación siguiendo otros criterios
Es posible que, a veces, quiera ordenar el objeto visual mediante un campo diferente o siguiendo otros criterios.  Por ejemplo, quizás quiera ordenarlo por mes (y no en orden alfabético) o por números enteros en lugar de dígitos (ejemplo, 0, 1, 9, 20 y no 0, 1, 20, 9).  

En algunos casos, es posible que pueda ordenar el objeto visual de la forma que quiere, por ejemplo, por mes.  Pero si no es así, puede deberse a que el conjunto de datos subyacente al informe necesita algunos ajustes. Existen varias soluciones:

* En Power BI Desktop, [use la pestaña Modelado de Herramientas de datos para ordenar por otra columna](desktop-sort-by-column.md).
* En Excel, si es propietario del conjunto de datos, agregue una nueva columna que concatene el nombre y el número del mes. A continuación, actualice vuelva a importar el conjunto de datos para ver la nueva columna en el área Campos.
* En Excel, asegúrese de que las columnas numéricas estén etiquetadas como "número entero" o "decimal" y no como "text".

## <a name="next-steps"></a>Pasos siguientes
Más información sobre [Visualizaciones en Power BI](visuals/power-bi-report-visualizations.md).

[Power BI: Conceptos básicos](service-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
