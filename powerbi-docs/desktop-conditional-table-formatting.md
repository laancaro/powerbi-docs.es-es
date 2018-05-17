---
title: Formato de tabla condicional en Power BI Desktop
description: Aplicar formato personalizado a las tablas
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
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1626c2af5906004b6b4f79f4830f003b96e241fc
ms.sourcegitcommit: 509be8852ba7595b9441c9479224f9dca298b26d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2018
---
# <a name="conditional-formatting-in-tables"></a>Formato condicional en tablas
Con el formato condicional de tablas, se pueden especificar colores de fondo personalizados de las celdas en función de los valores de esas celdas o de otros valores o campos. También se pueden usar colores de degradado. Para acceder al formato condicional, en el área **Campos** del panel **Visualizaciones** de Power BI Desktop, seleccione la flecha hacia abajo que está situada junto al valor del área **Valores** que desea formatear (o haga clic con el botón derecho en el campo). El formato condicional solo se puede administrar en el área **Valores** de **Campos**.

![Formato condicional de tabla](media/desktop-conditional-table-formatting/table-formatting_1.png)

En el cuadro de diálogo que aparece, puede configurar el color, así como los valores de *Mínimo* y *Máximo*. Si selecciona el cuadro **Diverging**, puede configurar un valor *Centro* opcional.

![Colores divergentes](media/desktop-conditional-table-formatting/table-formatting_2.png)

También se puede basar el degradado de color en un campo del modelo de datos. Además, se puede especificar el tipo de agregación del campo seleccionado (el campo seleccionado se especifica en el campo **Aplicar color a**, con lo que se puede llevar un seguimiento).

![Basar colores en un campo](media/desktop-conditional-table-formatting/table-formatting_2b.png)

Cuando se aplica a una tabla, el formato personalizado que se aplica con los pasos ya descritos reemplaza cualquier estilo de tabla personalizada aplicado a las celdas con formato condicional.

![Formato de tabla](media/desktop-conditional-table-formatting/table-formatting_3.png)

También se puede aplicar formato condicional a los campos de texto y de fecha, siempre y cuando se elija un valor numérico como base del formato. 

Para quitar el formato condicional de una visualización, simplemente vuelva a hacer clic con el botón derecho en el campo y seleccione **Quitar formato condicional**.

![Quitar formato de tabla](media/desktop-conditional-table-formatting/table-formatting_4.png)

