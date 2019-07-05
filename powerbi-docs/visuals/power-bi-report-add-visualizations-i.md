---
title: 'Parte 1: Incorporación de visualizaciones a un informe de Power BI'
description: 'Parte 1: Incorporación de visualizaciones a un informe de Power BI'
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299197"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Parte 1: Incorporación de visualizaciones a un informe de Power BI

En este artículo, se ofrece una introducción rápida a la creación de una visualización en un informe. Se aplica al servicio Power BI y a Power BI Desktop. Para obtener contenido más avanzado, [vea la parte 2](power-bi-report-add-visualizations-ii.md) de esta serie. Vea cómo Amanda demuestra algunas maneras de crear, editar y dar formato a objetos visuales en el lienzo del informe. A continuación, inténtelo usted usando el [ejemplo de marketing y ventas](../sample-datasets.md) para crear su propio informe.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Abrir un informe y agregar una nueva página

1. Abra un [informe en la Vista de edición](../service-interact-with-a-report-in-editing-view.md).

    En este tutorial, se usa el [ejemplo de ventas y marketing](../sample-datasets.md).

1. Si el panel **Campos** no está visible, seleccione el icono de flecha para abrirlo.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Agregue una página en blanco al informe.

## <a name="add-visualizations-to-the-report"></a>Agregar visualizaciones al informe

1. Cree una visualización seleccionando un campo en el panel **Campos** .

    Comience con un campo numérico como **SalesFact** > **Ventas en USD**. Power BI crea un gráfico de columnas con una sola columna.

    ![Captura de pantalla de un gráfico de columnas con una sola columna.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    O bien, comience con un campo de categoría, como **Nombre** o **Producto**. Power BI crea una tabla y agrega ese campo también a **Valores**.

    ![GIF de una persona que selecciona un producto y luego una categoría para crear una tabla.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    O bien, comience con un campo de geografía, como **Geografía** > **Ciudad**. Power BI y mapas de Bing crean una visualización de mapa.

    ![Captura de pantalla de una visualización de mapa.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Cree una visualización y, a continuación, cambie su tipo. Seleccione **Producto** > **Categoría** y después **Producto** > **Recuento de productos** para agregarlos al área **Valores**.

   ![Captura de pantalla del panel Campos con los valores resaltados.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Cambie la visualización a un gráfico de columnas mediante la selección del icono **Gráfico de columnas apiladas**.

   ![Captura de pantalla del panel Visualizaciones con el icono Gráfico de columnas apiladas resaltado.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. Cuando cree visualizaciones en el informe, puede [anclarlas al panel](../service-dashboard-pin-tile-from-report.md). Para anclar la visualización, seleccione el icono de anclaje ![Captura de pantalla del icono de anclaje.](media/power-bi-report-add-visualizations-i/pinnooutline.png).

   ![Captura de pantalla de una visualización de gráfico de columnas con el icono de anclaje resaltado.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Pasos siguientes

 Continúe con:

* [Parte 2: Incorporación de visualizaciones a un informe de Power BI](power-bi-report-add-visualizations-ii.md)

* [Interactuar con las visualizaciones](../consumer/end-user-reading-view.md) en el informe.

* [Hacer más cosas incluso con visualizaciones](power-bi-report-visualizations.md).

* [Guardar el informe](../service-report-save.md).
