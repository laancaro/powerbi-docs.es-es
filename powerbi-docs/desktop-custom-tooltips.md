---
title: Personalización de la información sobre herramientas en Power BI Desktop
description: Crear información sobre herramientas personalizada para objetos visuales con la operación de arrastrar y soltar
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: efbae4250b7b3cab18892cf519bfac5da3a88e1b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73868666"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalización de la información sobre herramientas en Power BI Desktop
La información sobre herramientas es una forma elegante de brindar más información contextual y detalles a los puntos de datos de un objeto visual. La imagen siguiente muestra una información sobre herramientas aplicada a un gráfico de Power BI Desktop.

![Información sobre herramientas predeterminada](media/desktop-custom-tooltips/custom-tooltips-1.png)

Cuando se crea una visualización, la información sobre herramientas predeterminada muestra el valor y la categoría del punto de datos. Hay muchos casos en los que personalizar la información sobre herramientas es útil, y podría proporcionar información y contexto adicionales a los usuarios que ven el objeto visual. La información sobre herramientas personalizada le permite especificar puntos de datos adicionales que se muestran como parte de la información sobre herramientas.

## <a name="how-to-customize-tooltips"></a>Cómo personalizar la información sobre herramientas
Para crear una información sobre herramientas personalizada, en el área **Campos** del panel **Visualizaciones**, arrastre un campo al cubo **Información sobre herramientas**, como se muestra en la imagen siguiente. En la imagen siguiente, se colocaron dos campos en el cubo **Información sobre herramientas**.

![Agregar campos de información sobre herramientas](media/desktop-custom-tooltips/custom-tooltips-2.png)

Una vez que se agrega la información sobre herramientas al área de campo, mantenga el puntero sobre un punto de datos en la visualización para ver los valores de esos campos en la información sobre herramientas.

![Información sobre herramientas personalizada](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalización de sugerencia sobre herramientas con agregación o cálculos rápidos
Para personalizar aún más una información sobre herramientas, seleccione una función de agregación o un *cálculo rápido* seleccionando la flecha que aparece junto al campo en el cubo **Información sobre herramientas** y, luego, seleccionando de las opciones disponibles.

![Información sobre herramientas con Cálculo rápido](media/desktop-custom-tooltips/custom-tooltips-4.png)

Hay muchas formas de personalizar la **información sobre herramientas**, mediante cualquier campo disponible en el conjunto de datos, para transmitir información rápida y detallada a los usuarios que ven sus paneles o informes.

