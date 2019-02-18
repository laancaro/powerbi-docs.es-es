---
title: Uso Vista de modelo en Power BI Desktop (versión preliminar)
description: Uso de Vista de modelo para ver conjuntos de datos complejos en un formato visual en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/13/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ccb78c8d22fdb7b9fecbb202dca488c44d36a15d
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216318"
---
# <a name="modeling-view-in-power-bi-desktop-preview"></a>Vista de modelo en Power BI Desktop (versión preliminar)

Con la característica **Vista de modelo** de **Power BI Desktop**, puede ver y trabajar con conjuntos de datos complejos que contienen muchas tablas. Con Vista de modelo, puede hacer lo siguiente:


## <a name="enabling-the-modeling-view-preview-feature"></a>Habilitación de la característica Vista de modelo en versión preliminar

La característica Vista de modelo se encuentra en versión preliminar y debe estar habilitada en **Power BI Desktop**. Para habilitar Vista de modelo, seleccione **Archivo > Opciones y configuración > Opciones > Características de versión preliminar** y, luego, active la casilla **Vista de modelo**, como se muestra en la imagen siguiente.

![Habilitar la característica Vista de modelo en versión preliminar de Power BI Desktop](media/desktop-modeling-view/modeling-view_01.png)

Se le indicará que es necesario reiniciar **Power BI Desktop** para habilitar la característica en versión preliminar. 

![Reiniciar Power BI Desktop para habilitar características en versión preliminar](media/desktop-modeling-view/modeling-view_01b.png)

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
* [Modelos compuestos en Power BI Desktop (versión preliminar)](desktop-composite-models.md)
* [Modo de almacenamiento en Power BI Desktop (versión preliminar)](desktop-storage-mode.md)
* [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md)


Artículos sobre DirectQuery:

* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos admitidos por DirectQuery en Power BI](desktop-directquery-data-sources.md)
