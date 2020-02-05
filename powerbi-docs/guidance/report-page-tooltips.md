---
title: Extensión de objetos visuales con la información en pantalla de la página del informe
description: Instrucciones para trabajar con la información sobre herramientas de páginas de informes.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 826af7b224b901b6dc9f3926260b1d920836a792
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76040362"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>Extensión de objetos visuales con la información en pantalla de la página del informe

Este artículo está dirigido a usted como autor de informes que diseña informes de Power BI. Proporciona sugerencias y recomendaciones a la hora de crear [información sobre herramientas de páginas de informes](../desktop-tooltips.md).

## <a name="suggestions"></a>Sugerencias

La información sobre herramientas de páginas de informes puede mejorar la experiencia de los usuarios de los informes. La información sobre herramientas de páginas permite a los usuarios de los informes obtener información más detallada de un objeto visual de forma rápida y eficaz. Pueden asociarse a diferentes objetos de informe:

- **Objetos visuales:** Para cada objeto visual, puede configurar los objetos visuales que mostrarán la información sobre herramientas de página. En cada objeto visual se puede hacer que no muestre información sobre herramientas, que tenga como valor predeterminado la información sobre herramientas del objeto visual (configurada en el panel de campos de objetos visuales) o que use cierta información sobre herramientas de página.
- **Encabezados visuales:** Puede configurar objetos visuales específicos para mostrar cierta información sobre herramientas de página. Los usuarios de los informes pueden mostrar la información sobre herramientas de una página cuando sitúan el cursor sobre el icono del encabezado visual; cerciórese de educar a los usuarios sobre este icono.

> [!NOTE]
> Un objeto visual de informe solo puede mostrar cierta información sobre herramientas de página si los filtros de página de información sobre herramientas son compatibles con el diseño del objeto visual. Por ejemplo, un objeto visual que agrupa por _producto_ será compatible con una página de información sobre herramientas que filtre por _producto_.
>
> La información sobre herramientas de página no admite la interactividad. Si quiere que los usuarios de los informes interactúen, deberá crear una [página de obtención de detalles](../desktop-drillthrough.md).
>
> Los objetos visuales personalizados no admiten la información sobre herramientas de página.

Estos son algunos escenarios de diseño propuestos:

- [Perspectiva diferente](#different-perspective)
- [Agregar detalle](#add-detail)
- [Agregar ayuda](#add-help)

### <a name="different-perspective"></a>Perspectiva diferente

La información sobre herramientas de página puede visualizar los mismos datos que el objeto visual de origen. Para ello, se deben usar los mismos grupos dinámicos y de objetos visuales, o bien distintos tipos de objetos visuales. La información sobre herramientas de página también puede aplicar distintos filtros que los que se aplican al objeto visual de origen.

En el ejemplo siguiente se muestra lo que sucede cuando el usuario de un informe mantiene el cursor sobre el valor **EnabledUsers**. El contexto de filtro del valor es Yammer en noviembre de 2018.

![Un objeto visual de matriz muestra una cuadrícula de valores agrupados por año y mes en las filas. El usuario del informe ha situado el cursor sobre un valor único. Aparece la información sobre herramientas de una página.](media/report-page-tooltips/suggestion-different-perspective.png)

Se muestra la información sobre herramientas de una página. Presenta un objeto visual de datos diferente (gráfico de líneas y columnas agrupadas) y aplica un filtro de tiempo de contraste. Observe que el contexto de filtro del punto de datos es el mes de noviembre de 2018, pero la información sobre herramientas de la página muestra la tendencia sobre _un año completo de meses_.

### <a name="add-detail"></a>Agregar detalle

La información sobre herramientas de página puede mostrar más datos y agregar contexto.

En el ejemplo siguiente se muestra lo que sucede cuando el usuario de un informe mantiene el cursor sobre el valor **Average of Violation Points** (Promedio de puntos de infracción) para el código postal 98022.

![Un objeto visual de tabla muestra una cuadrícula de valores; la tabla contiene tres columnas. Aparece la información sobre herramientas de una página.](media/report-page-tooltips/suggestion-add-details.png)

Se muestra la información sobre herramientas de una página. Presenta atributos y estadísticas específicos para el código postal 98022.

### <a name="add-help"></a>Agregar ayuda

Los encabezados visuales se pueden configurar para mostrar la información sobre herramientas de página en los encabezados visuales. Puede agregar documentación de ayuda a la información sobre herramientas de una página mediante cuadros de texto con formato enriquecido. También es posible agregar imágenes y formas.

Curiosamente, los botones, imágenes, cuadros de texto y formas también pueden mostrar información sobre herramientas de página de un encabezado visual.

En el ejemplo siguiente se muestra lo que sucede cuando el usuario de un informe mantiene el cursor sobre el [icono de encabezado visual](../desktop-visual-elements-for-reports.md).

![Un usuario de un informe ha situado el cursor sobre el icono de encabezado visual (icono de signo de interrogación). Ha aparecido información sobre herramientas con formato enriquecido.](media/report-page-tooltips/suggestion-add-help.png)

Se muestra la información sobre herramientas de una página. Muestra texto con formato enriquecido en cuatro cuadros de texto y una forma (línea). La información sobre herramientas de la página transmite ayuda mediante la descripción de los acrónimos que se muestran en el objeto visual.

## <a name="recommendations"></a>Recomendaciones

En el momento del diseño del informe, se recomienda aplicar las siguientes prácticas:

- **Tamaño de página:** Configure la información sobre herramientas de página para que sea pequeña. Puede usar la opción integrada **Información sobre herramientas** (320 píxeles de ancho y 240 píxeles de alto). También puede establecer dimensiones personalizadas. Tenga cuidado de no usar un tamaño de página demasiado grande: podría ocultar los objetos visuales de la página de origen.
- **Vista de página:** En el diseñador de informes, establezca la vista de página en **Tamaño real** (el valor predeterminado de la vista de página es **Ajustar a la página**). De esta forma, puede ver el tamaño real de la información sobre herramientas de la página a medida que la diseña.
- **Estilo:** Considere la posibilidad de diseñar la información sobre herramientas de página para usar el mismo tema y estilo que el informe. De este modo, a los usuarios les parece que se encuentran en el mismo informe. También puede diseñar un estilo gratuito para la información sobre herramientas. No olvide aplicar este estilo a toda la información sobre herramientas de página.
- **Filtros de información sobre herramientas:** Asigne filtros a la información sobre herramientas de página para poder obtener una vista previa de un resultado realista a medida que la diseña. Asegúrese de quitar estos filtros antes de publicar el informe.
- **Visibilidad de la página:** Oculte siempre las páginas de información sobre herramientas: los usuarios no deben acceder directamente a ellas.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Creación de información sobre herramientas basada en páginas de informes en Power BI Desktop](../desktop-tooltips.md)
- [Personalización de la información sobre herramientas en Power BI Desktop](../desktop-custom-tooltips.md)
- [Uso de elementos visuales para mejorar los informes de Power BI](../desktop-visual-elements-for-reports.md)
- Guy in a cube (vídeo): [Información sobre herramientas de páginas de informes de Power BI: Cómo crearla en Power BI Desktop](https://www.youtube.com/watch?v=URTA7JZsAtw)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
