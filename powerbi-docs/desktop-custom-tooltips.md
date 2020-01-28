---
title: Personalización de la información sobre herramientas en Power BI Desktop
description: Crear información sobre herramientas personalizada para objetos visuales con la operación de arrastrar y soltar
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 93177ac56bc2d8ecfe4b85f4ab66daef6bf0f0f3
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161042"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Personalización de la información sobre herramientas en Power BI Desktop

La información sobre herramientas es una forma elegante de brindar más información contextual y detalles a los puntos de datos de un objeto visual. La imagen siguiente muestra una información sobre herramientas aplicada a un gráfico de Power BI Desktop.

![Información sobre herramientas predeterminada](media/desktop-custom-tooltips/custom-tooltips-1.png)

Cuando se crea una visualización, la información sobre herramientas predeterminada muestra el valor y la categoría del punto de datos. Hay muchas instancias en las que personalizar la información sobre herramientas resulta útil. Personalizar la información sobre herramientas proporciona contexto e información adicionales a los usuarios que ven el objeto visual. La información sobre herramientas personalizada le permite especificar puntos de datos adicionales que se muestran como parte de la información sobre herramientas.

## <a name="how-to-customize-tooltips"></a>Cómo personalizar la información sobre herramientas

Para crear una información sobre herramientas personalizada, en el área **Campos** del panel **Visualizaciones**, arrastre un campo al cubo **Información sobre herramientas**, como se muestra en la imagen siguiente. En la imagen siguiente, se colocaron tres campos en el cubo **Información sobre herramientas**.

![Agregar campos de información sobre herramientas](media/desktop-custom-tooltips/custom-tooltips-2.png)

Una vez que se agrega la información sobre herramientas a **Información sobre herramientas**, mantenga el puntero sobre un punto de datos en la visualización para ver los valores de esos campos.

![Información sobre herramientas personalizada](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>Personalización de la información sobre herramientas con agregación o medidas rápidas

Puede personalizar más una información sobre herramientas seleccionando una función de agregación o una *medida rápida*. Seleccione la flecha situada junto al campo en el cubo **Información sobre herramientas**. A continuación, seleccione entre las opciones disponibles.

![Información sobre herramientas con medida rápida](media/desktop-custom-tooltips/custom-tooltips-4.png)

Hay muchas formas de personalizar la información sobre herramientas, mediante cualquier campo disponible en el conjunto de datos, para transmitir información rápida y detallada a los usuarios que ven sus paneles o informes.
