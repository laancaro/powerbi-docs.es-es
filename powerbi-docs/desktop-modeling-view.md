---
title: Uso del modelado de vistas en Power BI Desktop
description: Uso de Vista de modelo para ver conjuntos de datos complejos en un formato visual en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 6869430e3fece78210d538c9886234c7728b667a
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "73866544"
---
# <a name="modeling-view-in-power-bi-desktop"></a>Modelado de vistas en Power BI Desktop

Con la característica **Vista de modelo** de **Power BI Desktop**, puede ver y trabajar con conjuntos de datos complejos que contienen muchas tablas.


## <a name="using-modeling-view"></a>Uso de Vista de modelo

Para acceder a Vista de modelo, seleccione el icono correspondiente que se encuentra a la izquierda de **Power BI Desktop**, como se muestra en la imagen siguiente.

![El icono Vista de modelo de Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Creación de diagramas independientes

Con Vista de modelo, puede crear diagramas de su modelo que contengan solo un subconjunto de las tablas del modelo. Esto puede ayudar a proporcionar una visión más clara de las tablas con las que desea trabajar y a facilitar el trabajo con conjuntos de datos complejos. Para crear un diagrama con solo un subconjunto de las tablas, haga clic en el signo **+** junto a la pestaña **Todas las tablas** en la parte inferior de la ventana de Power BI Desktop.

![Crear un diagrama al hacer clic en el signo + en la sección de pestañas](media/desktop-modeling-view/modeling-view_03.png)

A continuación, puede arrastrar una tabla desde la lista **Campos** hasta la superficie del diagrama. Haga clic con el botón derecho en la tabla y, luego, seleccione **Agregar tablas relacionadas** en el menú que aparece.

![Hacer clic con el botón derecho en una tabla y seleccionar Agregar tablas relacionadas](media/desktop-modeling-view/modeling-view_04.png)

Al hacerlo, las tablas que están relacionadas con la tabla original se muestran en el nuevo diagrama. En la imagen siguiente se ilustra cómo se muestran las tablas relacionadas tras seleccionar la opción de menú **Agregar tablas relacionadas**.

![Presentación de las tablas relacionadas](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Definición de las propiedades comunes

Puede seleccionar varios objetos a la vez en Vista de modelo; para ello, mantenga presionada la tecla **CTRL** y haga clic en varias tablas. Al seleccionar varias tablas, se resaltan en esta vista. Cuando varias tablas están resaltadas, los cambios aplicados en el panel **Propiedades** se aplican a todas las tablas seleccionadas.

Por ejemplo, podría cambiar el [modo de almacenamiento](desktop-storage-mode.md) para varias tablas en la vista de diagrama; para ello, mantendría presionada la tecla **CTRL**, seleccionaría las tablas y, luego, cambiaría la opción de modo de almacenamiento en el panel  **Propiedades**.

![Seleccionar varias tablas manteniendo presionada la tecla CTRL y, luego, establecer las propiedades comunes en todas las tablas seleccionadas](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Pasos siguientes

En los artículos siguientes se proporciona más información sobre los modelos de datos y también se describe DirectQuery de forma detallada.

* [Agregaciones en Power BI Desktop (versión preliminar)](desktop-aggregations.md)
* [Modelos compuestos en Power BI Desktop](desktop-composite-models.md)
* [Modo de almacenamiento en Power BI Desktop (versión preliminar)](desktop-storage-mode.md)
* [Relaciones de varios a varios en Power BI Desktop](desktop-many-to-many-relationships.md)


Artículos sobre DirectQuery:

* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos admitidos por DirectQuery en Power BI](desktop-directquery-data-sources.md)
