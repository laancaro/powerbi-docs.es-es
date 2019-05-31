---
title: Ver datos y registros en objetos visuales de Power BI Desktop
description: Usar las características Ver datos y Ver registros de Power BI Desktop para profundizar en la información
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 6e425f146228d0139b9eec914a44ed5dc732fe98
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514767"
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Usar Ver datos y Ver registros en Power BI Desktop
En **Power BI Desktop**, puede profundizar en los detalles de una visualización y ver representaciones textuales de los datos subyacentes o de los registros de datos individuales del objeto visual seleccionado. Estas características se conocen a veces como *click-through*, o *drill-through* u *obtención de detalles*.

Puede usar **Ver datos** para ver una versión textual de los valores usados por la visualización seleccionada, o usar **Ver registros** para ver todos los datos de un registro o punto de datos seleccionado. 

![Ver datos y Ver registros](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>**Ver datos** y **Ver registros** admiten solo los siguientes tipos de visualización:
>  - Gráfico de barras
>  - Gráfico de columnas
>  - Gráfico de anillos
>  - Mapa coroplético
>  - Embudo
>  - Mapa
>  - Gráfico circular
>  - Gráfico de rectángulos

## <a name="use-see-data-in-power-bi-desktop"></a>Uso de Ver datos en Power BI Desktop

**Ver datos** muestra los datos que subyacen a una visualización. **Ver datos** aparece en la pestaña **Datos y rastreo** en la sección **Visual Tools** de la cinta al seleccionarse una visualización.

![Ver Datos en la cinta](media/desktop-see-data-see-records/see-data1.png)

También puede ver los datos haciendo clic con el botón derecho en una visualización y, a continuación, seleccionando **Mostrar datos** en el menú que aparece, o bien seleccionando los puntos suspensivos (...) **Más opciones** en la esquina superior derecha de una visualización y, después, seleccionando **Mostrar datos**.

![Mostrar datos clic con el botón derecho](media/desktop-see-data-see-records/see-data2.png)&nbsp;&nbsp;![Mostrar datos Más opciones](media/desktop-see-data-see-records/see-data3.png)

> [!NOTE]
> Debe mantener el puntero sobre un punto de datos del objeto visual para que el menú contextual esté disponible.

Al seleccionar **Ver datos** o **Mostrar datos**, el lienzo de Power BI Desktop muestra tanto la representación visual como la representación textual de los datos. En la *vista horizontal*, el objeto visual se muestra en la mitad superior del lienzo, mientras que los datos aparecen en la mitad inferior. 

![vista horizontal](media/desktop-see-data-see-records/see-data4a.png)

Puede alternar entre la vista horizontal y una *vista vertical* si selecciona el icono en la esquina superior derecha del lienzo.

![alternar vista vertical](media/desktop-see-data-see-records/see-data4.png)

Para volver al informe, seleccione **< Volver al informe** en la esquina superior izquierda del lienzo.

![Volver al informe](media/desktop-see-data-see-records/see-data5.png)

## <a name="use-see-records-in-power-bi-desktop"></a>Uso de Ver registros en Power BI Desktop

También puede centrarse en un registro de datos de una visualización y profundizar en los datos que contiene. Para usar **Ver registros**, seleccione una visualización y, a continuación, **Ver registros** en la pestaña **Datos y detalles** en la sección **Herramientas visuales** de la cinta. Después, seleccione una fila o punto de datos en la visualización. 

![Ver Registros en la cinta](media/desktop-see-data-see-records/see-record1.png)

> [!NOTE]
> Si el botón **Ver registros** de la cinta está deshabilitado y en gris, significa que la visualización seleccionada no admite **Ver registros**.

También puede hacer clic con el botón derecho en un elemento de datos y seleccionar **Ver registros** en el menú que aparece.

![Ver registros haciendo clic con el botón derecho](media/desktop-see-data-see-records/see-record2.png)

Al seleccionar **Ver registros** para un elemento de datos, el lienzo de Power BI Desktop muestra todos los datos asociados al elemento seleccionado. 

![](media/desktop-see-data-see-records/see-record3.png)

Para volver al informe, seleccione **< Volver al informe** en la esquina superior izquierda del lienzo.

![](media/desktop-see-data-see-records/see-record4.png)

> [!NOTE]
>**Ver registros** tiene las siguientes limitaciones:
> - No puede cambiar los datos en la vista **Ver registros** y guardarlos de nuevo en el informe.
> - No se puede usar **Ver registros** cuando el objeto visual utiliza una medida calculada.
> - No se puede usar **Ver registros** al conectarse a un modelo multidimensional (MD) activo.

## <a name="next-steps"></a>Pasos siguientes
**Power BI Desktop** incluye todo tipo de características de administración de datos y formato de informes. Para ver algunos ejemplos, consulte los siguientes recursos:

* [Usar la agrupación y la discretización en Power BI Desktop](desktop-grouping-and-binning.md)
* [Usar líneas de cuadrícula, ajustar a la cuadrícula, orden Z, alineación y distribución en los informes de Power BI Desktop](desktop-gridlines-snap-to-grid.md)

