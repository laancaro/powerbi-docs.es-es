---
title: Tipos de filtros en informes de Power BI
description: Adición de un filtro de página, un filtro de visualización o un filtro de informe a un informe en Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c96b4ebae574a3b6a6fa54c5f5dc99b5bc948a90
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874424"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Tipos de filtros en informes de Power BI

No todos los filtros se comportan de la misma forma, ya que no se crean de la misma manera. La forma de crearlos influye en cómo se comportan en el nuevo panel de filtros en modo de edición. En este artículo se describen los diferentes tipos de filtros: las diversas formas de crearlos y las diferentes cosas para las que son buenos. Obtenga información sobre cómo [agregar filtros a los informes](power-bi-report-add-filter.md). 

![Panel de filtros](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Comencemos con los dos tipos de filtro más habituales: manuales y automáticos.

## <a name="manual-filters"></a>Filtros manuales 

Los filtros manuales son los filtros que los creadores de informes arrastran y colocan en cualquier parte del nuevo panel de filtros. Los usuarios con permiso de edición para el informe pueden editar, eliminar, ocultar, bloquear, ordenar o cambiar el nombre de este filtro en el nuevo panel.

## <a name="automatic-filters"></a>Filtros automáticos 

Los filtros automáticos son los filtros que se agregan automáticamente al nivel visual del panel de filtros al crear un objeto visual. Estos filtros se basan en los campos que componen su objeto visual. Los usuarios con permiso de edición para el informe pueden editar, borrar, ocultar, bloquear, ordenar o cambiar el nombre de este filtro en el nuevo panel. No pueden eliminar los filtros automáticos, ya que el objeto visual hace referencia a esos campos.

## <a name="more-advanced-filters"></a>Filtros más avanzados

Estos tipos de filtro mostrados a continuación son menos habituales, pero sigue siendo importante conocerlos si aparecen en el informe. Además, puede que le resulten útiles a la hora de crear el filtro adecuado para el informe.

## <a name="include-and-exclude-filters"></a>Filtros de inclusión y exclusión

Los filtros de inclusión y exclusión se agregan automáticamente al panel de filtros al usar la funcionalidad de inclusión o exclusión para un objeto visual. Los usuarios con permiso de edición para el informe pueden eliminar, bloquear, ocultar u ordenar este filtro en el nuevo panel. No pueden editar, borrar o cambiar el nombre de un filtro de inclusión o exclusión, ya que se asocia con la funcionalidad de inclusión y exclusión de los objetos visuales.

![Filtro de exclusión](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Filtros de exploración en profundidad

Los filtros de exploración en profundidad se agregan automáticamente al panel de filtros al usar la funcionalidad de exploración en profundidad para un objeto visual en el informe. Los usuarios con permiso de edición para el informe pueden editar o borrar el filtro en el nuevo panel. No pueden eliminar, ocultar, bloquear, ordenar o cambiar el nombre de este filtro, ya que se asocia a la funcionalidad de exploración en profundidad de los objetos visuales. Para quitar el filtro de exploración en profundidad, debe hacer clic en el botón de rastreo agrupando datos del objeto visual.

![Filtro de exploración en profundidad](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Filtros de exploración cruzada

Los filtros de exploración cruzada se agregan automáticamente al nuevo panel al pasarse un filtro de exploración en profundidad a otro objeto visual en la página del informe a través de la característica de filtro cruzado o resaltado cruzado. Los usuarios con permiso de edición para el informe no pueden eliminar, borrar, ocultar, bloquear, ordenar o cambiar el nombre de este filtro, ya que se asocia a la funcionalidad de exploración en profundidad de los objetos visuales. Tampoco pueden editar este filtro porque deriva de la exploración en profundidad en otro objeto visual. Para quitar el filtro de exploración en profundidad, debe hacer clic en el botón de rastreo agrupando datos del objeto visual que pasa el filtro.

## <a name="drillthrough-filters"></a>Filtros de obtención de detalles

Los filtros de obtención de detalles se pasan de una página a otra a través de la característica de obtención de detalles. Aparecen en el panel de obtención de detalles. Existen dos tipos de filtros de obtención de detalles. El primer tipo es el que invoca la obtención de detalles. Los editores de informes pueden editar, eliminar, borrar, ocultar o bloquear este tipo de filtro. El segundo tipo es el filtro de obtención de detalles que se pasa al destino, en función de los filtros de nivel de página de la página de origen. Los editores de informes pueden editar, eliminar o borrar este tipo transitorio de filtro de obtención de detalles. No pueden bloquear ni ocultar este filtro para los usuarios finales.

## <a name="url-filters"></a>Filtros de direcciones URL

Los filtros de direcciones URL se agregan al nuevo panel agregando un parámetro de consulta de dirección URL. Los usuarios con permiso de edición para el informe pueden editar, eliminar o borrar el filtro en el nuevo panel. No pueden ocultar, bloquear, ordenar o cambiar el nombre de este filtro, ya que se asocia al parámetro de dirección URL. Para quitar el filtro, debe quitar el parámetro de la dirección URL. Esta es una dirección URL de ejemplo con un parámetro:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![Filtro de URL](media/power-bi-report-filter-types/power-bi-filter-url.png)

Obtenga más información sobre los [filtros de direcciones URL](service-url-filters.md).

## <a name="pass-through-filters"></a>Filtros de paso a través

Los filtros de paso a través son filtros de nivel de objeto visual creados a través de Preguntas y respuestas. Los autores pueden eliminar, ocultar u ordenar estos filtros en el nuevo panel. Sin embargo, no pueden editar, borrar, bloquear ni cambiar el nombre de estos filtros.

![Filtro de paso a través con Preguntas y respuestas](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Comparación de tipos de filtro

En esta tabla se compara lo que pueden hacer los autores con los diversos tipos de filtros.

| Tipo de filtro | Editar | Borrar | Eliminar | Ocultar | Bloquear | Ordenar | Cambiar nombre |
|----|----|----|----|----|----|----|----|
| Filtros manuales | Y | Y | Y | Y | Y | Y | Y |
| Filtros automáticos | Y | Y | N | Y | Y | Y | Y |
| Filtros de inclusión o exclusión | N | N | Y | Y | Y | Y | N |
| Filtros de exploración en profundidad | Y | Y | N | N | N | N | N |
| Filtros de exploración cruzada | N | N | N | N | N | N | N |
| Filtros de obtención de detalles (invocan la obtención de detalles) | Y | Y | Y | Y | Y | N | N |
| Filtros de obtención de detalles (transitorios) | Y | Y | Y | N | N | N | N |
| Filtros de direcciones URL: transitorios | Y | Y | Y | N | N | N | N |
| Filtros de paso a través | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>Pasos siguientes

[Incorporación de un filtro a un informe en la vista Editar](power-bi-report-add-filter.md)

[Ver el panel Filtros del informe](consumer/end-user-report-filter.md)

[Filtrado y resaltado en informes](power-bi-reports-filters-and-highlighting.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

