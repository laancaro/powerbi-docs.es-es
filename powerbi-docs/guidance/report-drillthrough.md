---
title: Obtención de detalles de la página del informe
description: Instrucciones para trabajar con la obtención de detalles de páginas de informes.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: b674c621c30491a00c529af7f2fcd9eb87f3ecfa
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74834779"
---
# <a name="report-page-drillthrough"></a>Obtención de detalles de la página del informe

Este artículo está dirigido a usted como autor de informes que diseña informes de Power BI. Proporciona sugerencias y recomendaciones a la hora de crear una [obtención de detalles de páginas de informes](../desktop-drillthrough.md).

Se recomienda diseñar el informe para que los usuarios de los informes puedan tener el siguiente flujo:

1. Ver una página de informe.
2. Identificar un elemento visual para analizarlo con mayor profundidad.
3. Hacer clic con el botón derecho en el elemento visual para efectuar la obtención de detalles.
4. Llevar a cabo un análisis gratuito.
5. Volver a la página del informe de origen.

## <a name="suggestions"></a>Sugerencias

Se recomienda tener en cuenta dos tipos de escenarios de obtención de detalles:

- [Profundidad adicional](#additional-depth)
- [Perspectiva más amplia](#broader-perspective)

### <a name="additional-depth"></a>Profundidad adicional

Cuando la página del informe muestra los resultados resumidos, una página de obtención de detalles puede dirigir a los usuarios de los informes a los detalles de nivel de transacción. Este enfoque de diseño les permite ver las transacciones auxiliares (solo cuando sea necesario).

En el ejemplo siguiente se muestra lo que sucede cuando un usuario de un informe profundiza a partir de un resumen de ventas mensuales. La página de obtención de detalles contiene una lista detallada de pedidos de un mes determinado.

![Un objeto visual de matriz titulado "Resumen de ventas" agrupa las ventas por año y por mes en las filas, y por país en las columnas. También se muestra una página de obtención de detalles.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Perspectiva más amplia

Una página de obtención de detalles puede tener el efecto contrario de la profundidad adicional. Este escenario es excelente para profundizar en una vista holística.

En el ejemplo siguiente se muestra lo que sucede cuando un usuario de un informe profundiza a partir de un código postal. En la página de obtención de detalles se muestra información general sobre ese código postal.

![Un objeto visual de tabla tiene tres columnas: Zip Code (Código postal), Average of Violation Points (Promedio de puntos de infracción) y Average of Grade Rating (Promedio de clasificación por grados). También se muestra la página de obtención de detalles.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Recomendaciones

En el momento del diseño del informe, se recomienda aplicar las siguientes prácticas:

- **Estilo:** Considere la posibilidad de diseñar la página de obtención de detalles para que use el mismo tema y estilo que el informe. De este modo, a los usuarios les parece que se encuentran en el mismo informe.
- **Filtros de obtención de detalles:** Establezca filtros de obtención de detalles para poder obtener una vista previa de un resultado realista al diseñar la página de obtención de detalles. Asegúrese de quitar estos filtros antes de publicar el informe.
- **Capacidades adicionales:** Una página de obtención de detalles es como cualquier página de informe. Incluso puede mejorarla con más capacidades interactivas, como las segmentaciones o los filtros.
- **Espacios en blanco:** Evite agregar objetos visuales que puedan mostrar valores en blanco o generar errores al aplicar filtros de obtención de detalles.
- **Visibilidad de la página:** Considere la posibilidad de ocultar las páginas de obtención de detalles. Si decide mantener visible una página de obtención de detalles, no olvide agregar un botón que permita a los usuarios borrar todos los filtros de obtención de detalles establecidos previamente. Asigne un [marcador](../desktop-bookmarks.md) al botón. El marcador se debe configurar para quitar todos los filtros.
- **Botón Atrás:** Al asignar un filtro de obtención de detalles, se agrega automáticamente un botón [Atrás](../desktop-buttons.md). Es buena idea conservarlo. De esta forma, los usuarios del informe podrán volver fácilmente a la página de origen.
- **Detección:** Ayude a promover la conciencia de una página de obtención de detalles estableciendo un texto de icono del encabezado visual o agregando instrucciones a un cuadro de texto. También puede diseñar una superposición, como se describe en [esta entrada de blog](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/).

> [!TIP]
> También se puede configurar la obtención de detalles en los informes paginados de Power BI. Puede hacerlo agregando vínculos a los informes de Power BI. Los vínculos pueden definir [parámetros de dirección URL](/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Uso de la obtención de detalles en Power BI Desktop](../desktop-drillthrough.md)
- Guy in a cube (vídeo): [Obtención de detalles en Power BI Desktop](https://www.youtube.com/watch?v=2x9lLHDbtDk)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
