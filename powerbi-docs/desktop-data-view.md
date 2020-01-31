---
title: Vista de datos en Power BI Desktop
description: Vista de datos en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a82465adb5b0c7fe8be0e6e724c5eda1bfcf7ec0
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538684"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Trabajo con Vista de datos en Power BI Desktop

La *vista Datos* permite inspeccionar, explorar y analizar los datos de su modelo de *Power BI Desktop*. Es distinto de cómo se visualizan las tablas, las columnas y los datos en el *Editor de Power Query*. Con la vista Datos, se ven los datos *después* de que se hayan cargado en el modelo.

Cuando se están modelando los datos, a veces quiere ver lo que hay realmente en una tabla o columna sin crear un objeto visual en el lienzo del informe. Es posible que quiera ver hasta el nivel de fila. Esta capacidad es útil sobre todo cuando crea columnas calculadas y medidas o cuando tiene que identificar un tipo de datos o una categoría de datos.

Eche un vistazo más de cerca a algunos de los elementos de la vista Datos.

![Vista de datos en Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Icono de la vista Datos**. Seleccione este icono para entrar en la vista Datos.

2. **Cuadrícula de datos**. Esta área muestra la tabla seleccionada y todas las columnas y filas que hay en ella. Las columnas ocultas de la vista *Informes* están atenuadas. Puede hacer clic con el botón derecho en una columna para ver las opciones.

3. **Cinta de opciones de modelado**. Aquí se pueden administrar relaciones, crear cálculos y cambiar el tipo de datos, el formato y la categoría de datos de una columna.

4. **Barra de fórmulas**. Introduzca fórmulas de expresiones de análisis de datos (DAX) para las columnas calculadas y las medidas.

5. **Búsqueda**. Busque una tabla o una columna en el modelo.

6. **Lista de campos**. Seleccione una tabla o una columna para verla en la cuadrícula de datos.

## <a name="filtering-in-data-view"></a>Filtrado en la vista Datos

También se pueden filtrar y ordenar datos en la vista Datos. En cada columna se muestra un icono que identifica la dirección de ordenación, si procede.

![Ordenar y filtrar en la vista Datos en Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Puede filtrar valores concretos o puede usar el filtrado avanzado en función de los datos de la columna.

> [!NOTE]
> Al crear un modelo de Power BI en una referencia cultural diferente con respecto a la interfaz de usuario actual, el cuadro de búsqueda solo aparecerá en la interfaz de usuario de la vista Datos para los campos de texto. Por ejemplo, esto se aplicaría para un modelo creado en inglés de EE. UU. que se ve en español.
