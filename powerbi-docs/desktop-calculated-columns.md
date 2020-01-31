---
title: Uso de columnas calculadas en Power BI Desktop
description: Columnas calculadas en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 425bf50ad6eb4da9b50f7d9cdc760ef71cb7bff2
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753327"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Creación de columnas calculadas en Power BI Desktop
Con las columnas calculadas, se pueden agregar nuevos datos a una tabla ya existente en el modelo. Pero en lugar de consultar y cargar los valores en la nueva columna desde un origen de datos, se crea una fórmula de expresiones de análisis de datos (DAX) que define los valores de columna. En Power BI Desktop, las columnas calculadas se crean mediante la característica nueva columna en la vista **Informes**.

A diferencia de las columnas personalizadas creadas como parte de una consulta con la opción **Agregar columnas personalizadas** en el Editor de consultas, las columnas calculadas creadas en las vistas **Informes** o **Datos** se basan en datos cargados previamente en el modelo. Por ejemplo, tal vez elija concatenar los valores de dos columnas diferentes en dos tablas diferentes pero relacionadas, hacer sumas o extraer subcadenas.

Las columnas calculadas que cree aparecerán en la lista **Campos** como cualquier otro campo, pero tendrán un icono especial para indicar que sus valores son resultado de una fórmula. Puede asignar el nombre que desee a las columnas y agregarlas a la visualización de un informe, igual que cualquier otro campo.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

Las columnas calculadas calculan los resultados usando DAX, un lenguaje de fórmulas diseñado para trabajar con datos relacionales como en Power BI Desktop. DAX incluye una biblioteca de más de 200 funciones, operadores y construcciones. Ofrece una gran flexibilidad en la creación de fórmulas para calcular los resultados ante casi cualquier necesidad de análisis de datos. Para más información acerca de DAX, consulte [Conceptos básicos de DAX en Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Las fórmulas DAX son muy similares a las fórmulas de Excel. De hecho, DAX tiene muchas de las mismas funciones que Excel. Las funciones de DAX, sin embargo, están diseñadas para trabajar con datos segmentados de forma interactiva o filtrados en un informe, como en Power BI Desktop. En Excel, puede tener una fórmula diferente para cada fila de una tabla. En Power BI, al crear una fórmula DAX para una nueva columna, calculará un resultado para cada fila de la tabla. Los valores de columna se calculan varias veces, según sea necesario, como cuando se actualizan los datos subyacentes y los valores cambian.

## <a name="lets-look-at-an-example"></a>Veamos un ejemplo
Juan es administrador de envíos en Contoso y quiere crear un informe que muestre el número de envíos a diferentes ciudades. Juan tiene una tabla **Geography** con campos independientes para las ciudades y los estados. Sin embargo, Juan quiere que en sus informes se muestren los valores de ciudad y estado como un valor único en la misma fila. En este momento la tabla **Geography** de Juan no tiene el campo que necesita.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Pero con una columna calculada, Juan puede reunir las ciudades de la columna **City** con los estados de la columna **State**.

Juan hace clic con el botón derecho en la tabla **Geography** y, después, selecciona **Nueva columna**. Después, Juan especifica la siguiente fórmula DAX en la barra de fórmulas:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Esta fórmula simplemente crea una nueva columna denominada **CityState**. Para cada fila de la tabla **Geography**, toma los valores de la columna **City**, agrega una coma y un espacio y, después, concatena los valores de la columna **State**.

Ahora Juan tiene el campo que quiere.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Puede agregarlo al lienzo de su informe junto con el número de envíos. Con el mínimo esfuerzo, Juan tiene un campo **CityState**, que puede agregar a casi cualquier tipo de visualización. Cuando Juan crea un mapa nuevo, Power BI Desktop sabe cómo leer los valores de ciudad y estado de la nueva columna.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>Pasos siguientes
Aquí hemos proporcionado únicamente una breve introducción a las columnas calculadas. Para más información, consulte los siguientes recursos:

* Para descargar un archivo de ejemplo y obtener lecciones paso a paso sobre cómo crear otras columnas, consulte [Tutorial: Creación de columnas calculadas en Power BI Desktop](desktop-tutorial-create-calculated-columns.md).

* Para más información acerca de DAX, consulte [Conceptos básicos de DAX en Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

* Para obtener más información sobre las columnas que se crean como parte de una consulta, consulte la sección **Crear columnas personalizadas** en [Realización de tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md).  

