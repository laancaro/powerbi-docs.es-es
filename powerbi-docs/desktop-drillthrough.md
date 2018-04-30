---
title: Uso de la obtención de detalles en Power BI Desktop
description: Obtenga información sobre cómo explorar en profundidad datos en una nueva página del informe en Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 4/10/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b5da2bf43f2d38e0828571e2b9d404feb615ac69
ms.sourcegitcommit: 312390f18b99de1123bf7a7674c6dffa8088529f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Uso de la obtención de detalles en Power BI Desktop
Con la **obtención de detalles** en **Power BI Desktop**, puede crear una página en el informe que se centra en una entidad específica, como un proveedor, un cliente o un fabricante. Con el foco en esa página del informe, los usuarios pueden hacer clic con el botón derecho en un punto de datos en otras páginas del informe y obtener detalles de la página que tiene el foco, filtrados en ese contexto.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Uso de la obtención de detalles
1. Para usar la **obtención de detalles**, cree una página del informe que contenga los objetos visuales que le gustaría ver para el tipo de entidad en la que proporciona obtención de detalles. 

    Por ejemplo, si está interesado en proporcionar obtención de detalles para fabricantes, podría crear una página de obtención de detalles con objetos visuales que muestren las ventas totales, el total de unidades enviadas, las ventas por categoría y por región, y así sucesivamente. De este modo, cuando se realiza la obtención de detalles mediante esa página, los objetos visuales serán específicos para el fabricante que haya seleccionado.

2. A continuación, en esa página de obtención de detalles, en la sección **Campos** del panel **Visualizaciones**, arrastre el campo sobre el que desea obtener detalles al área **Filtros de obtención de detalles**.

    ![](media/desktop-drillthrough/drillthrough_02.png)

    Cuando se agrega un campo al área **Filtros de obtención de detalles**, **Power BI Desktop** crea automáticamente un objeto visual de botón *Volver*. Ese objeto visual se convierte en un botón en los informes publicados y permite que los usuarios que están consumiendo el informe en el **servicio Power BI** puedan volver fácilmente a la página del informe de la que venían (la página en la que se ha seleccionado la obtención de detalles).

    ![](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Uso de su propia imagen para un botón Atrás    
 Puesto que el botón Atrás es una imagen, puede reemplazar la imagen de ese objeto visual por cualquier imagen que desee y seguirá funcionando como botón Atrás para que los consumidores del informe puedan volver a la página original.

1. Para usar su propia imagen para un botón Atrás, coloque un objeto visual de imagen en la página de obtención de detalles.
2. Seleccione el objeto visual y establezca el control deslizante **Botón Atrás** en Activado. Ahora su imagen funciona como botón Atrás.

    ![](media/desktop-drillthrough/drillthrough_05.png)

    Al completarse la página de **obtención de detalles** y hacer clic con el botón derecho los usuarios en un punto de datos del informe que usa el campo que colocó en el área **Filtros de obtención de detalles**, aparece un menú contextual que admite la obtención de detalles mediante esa página.

    ![](media/desktop-drillthrough/drillthrough_04.png)

    Cuando los consumidores del informe eligen la obtención de detalles, la página se filtra para mostrar información acerca del punto de datos en el que se hizo clic con el botón derecho. Por ejemplo, si los usuarios hacen clic con el botón derecho en un punto de datos de Contoso (un fabricante) y seleccionan obtener detalles, la página de obtención de detalles que se les muestra está filtrada para Contoso.

    > [!NOTE]
    > Solo el campo que se encuentra en el área **Filtros de obtención de detalles** lleva a la página de obtención de detalles del informe. No se pasa ninguna otra información contextual.
    > 
    > 

Y eso es todo lo necesario para usar la **obtención de detalles** en los informes. Es una excelente manera de obtener una vista expandida de la información de la entidad que se seleccione para el filtro de obtención de detalles.

