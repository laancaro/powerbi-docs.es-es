---
title: Vista de datos en Power BI Desktop
description: Vista de datos en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 567beb29ecdcaf8a07023c8c8c9b32995623534c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454477"
---
# <a name="data-view-in-power-bi-desktop"></a>Vista de datos en Power BI Desktop
La **vista de datos** le permite inspeccionar, explorar y analizar los datos de su modelo de **Power BI Desktop**. Es diferente de cómo ve las tablas, columnas y datos en el **Editor de consultas**. Con la vista de datos, ve los datos *después* de que se hayan cargado en el modelo.

Cuando se están modelando los datos, a veces desea ver lo que hay realmente en una tabla o columna sin crear un elemento visual en el lienzo del informe, normalmente justo debajo del nivel de fila. Es útil sobre todo cuando crea columnas calculadas y medidas o cuando tiene que identificar un tipo de datos o una categoría de datos.

Eche un vistazo más de cerca a algunos de los elementos de la **vista de datos**.

![Vista de datos en Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Icono de vista de datos**: seleccione este icono para entrar en la vista de datos.

2. **Cuadrícula de datos**: se muestra la tabla seleccionada y todas las columnas y filas que contiene. Las columnas ocultas de la **vista de informe** están atenuadas. Puede hacer clic en una columna de opciones.

3. **Cinta de opciones de modelado**: aquí puede administrar relaciones, crear cálculos y cambiar el tipo de datos, el formato y la categoría de datos de una columna.

4. **Barra de fórmulas**: indique fórmulas DAX para las columnas calculadas y las medidas.

5. **Búsqueda**: busque una tabla o una columna en el modelo.

6. **Lista de campos**: seleccione una tabla o una columna para verla en la cuadrícula de datos.

## <a name="filtering-in-data-view"></a>Filtrado en la vista de datos

También puede filtrar y ordenar datos en la **vista de datos**. En cada columna se muestra un icono que identifica la dirección de ordenación (si procede).

![Ordenar y filtrar en la vista Datos en Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Puede filtrar valores concretos o puede usar el filtrado avanzado en función de los datos de la columna. 

> [!NOTE]
> Cuando se crea un modelo de Power BI en una referencia cultural diferente con respecto a la interfaz de usuario actual (por ejemplo, el modelo se ha creado en inglés de Estados Unidos y lo está viendo en español), el cuadro de búsqueda solo aparecerá en la interfaz de usuario de la vista de datos para los campos de texto.
