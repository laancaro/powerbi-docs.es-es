---
title: Rastreo agrupando y desagrupando datos en una visualización
description: Este artículo muestra cómo explorar en profundidad una visualización del servicio Microsoft Power BI y Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 6/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 29823a2f1ca7f1448df54282e0ce081310974eb3
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "67265265"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Modo detallado en una visualización de Power BI

Este artículo muestra cómo explorar en profundidad una visualización del servicio Microsoft Power BI y Power BI Desktop. Los informes de Power BI presentan diferentes jerarquías de datos con el fin de ofrecerle la mayor cantidad de información posible sobre ellos. El uso del rastreo agrupando y desagrupando puntos de datos le permite explorar en profundidad sus detalles. Puede incluso disfrutar de sus ventajas en el factor de forma pequeño de sus dispositivos móviles.

## <a name="drill-requires-a-hierarchy"></a>El modo detallado necesita una jerarquía

Cuando una visualización tiene una jerarquía, se puede explorar en profundidad para mostrar detalles adicionales. Por ejemplo, puede tener una visualización que examine el número de medallas olímpicas mediante una jerarquía formada por deporte, disciplina y evento. De forma predeterminada, la visualización muestra el número de medallas por deporte, como gimnasia, esquí, deportes acuáticos, etc. Pero, como tiene una jerarquía, la selección de uno de los elementos de la visualización (por ejemplo, una barra, línea o burbuja) puede mostrar una imagen cada vez más detallada. Seleccione el elemento **aquatics** para ver los datos de natación, buceo y waterpolo.  Seleccione el elemento **diving** para ver los detalles de springboard, plataforma y eventos de buceo sincronizado.

Puede agregar jerarquías a los informes de su propiedad, pero no a los que se hayan compartido con usted.
¿No está seguro de qué visualizaciones de Power BI contienen una jerarquía? Mantenga el cursor sobre una visualización. Si ve estos controles de exploración en las esquinas superiores, la visualización tiene una jerarquía.

![Captura de pantalla del icono para explorar en profundidad un nivel.](./media/end-user-drill/power-bi-drill-icon4.png)  ![Captura de pantalla del icono para activar y desactivar la opción de explorar en profundidad.](./media/end-user-drill/power-bi-drill-icon2.png)  ![Captura de pantalla del icono para explorar en profundidad todos los campos a la vez.](./media/end-user-drill/power-bi-drill-icon3.png)
![icono de rastrear agrupando datos](./media/end-user-drill/power-bi-drill-icon5.png) ![Captura de pantalla del icono de expansión.](./media/end-user-drill/power-bi-drill-icon6.png)  

Las fechas son un tipo único de jerarquía. Cuando agrega un campo de fechas a una visualización, Power BI agrega automáticamente una jerarquía de tiempo que contiene valores para el año, trimestre, mes y día. Para más información, consulte [Jerarquías visuales y exploración en profundidad](../guided-learning/visualizations.yml?tutorial-step=18) o vea el vídeo siguiente.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Para obtener información sobre cómo crear jerarquías con Power BI Desktop, vea el vídeo [How to create and add hierarchies](https://youtu.be/q8WDUAiTGeU) (Cómo generar y agregar jerarquías).

## <a name="prerequisites"></a>Requisitos previos

1. En el servicio Power BI o en Desktop, para el modo detallado se necesita una visualización con una jerarquía.

1. Para continuar, abra el [ejemplo de análisis de venta directa](../sample-datasets.md). Cree una visualización de **gráfico de rectángulos** que se fije en:

    | Área | Campo |
    | ---- | ----- |
    | Valor |Ventas<br>\|\_ Unidades totales de este año |
    | Agrupar | Tienda<br>\|\_ Territorio<br>\|\_ Ciudad<br>\|\_ Código postal<br>\|\_ Nombre

    El treemap tiene una jerarquía formada por el territorio, la ciudad, el código postal y el nombre de la ciudad. Cada territorio tiene una o varias ciudades, cada ciudad tiene uno o más códigos postales, etc. De forma predeterminada, la visualización muestra solo los datos de territorio, porque *Territory* (Territorio) aparece en primer lugar en la lista.

    ![Captura de pantalla del panel de visualizaciones con el icono de territorio resaltado.](media/end-user-drill/power-bi-hierarcy-list.png)

1. El aprendizaje del funcionamiento de los diferentes iconos de exploración puede resultar confuso. Vamos a filtrar el gráfico de rectángulos para mostrar solo dos de los territorios más pequeños: **KY** y **TN**. Seleccione el treemap y, en **Filtros de nivel visual** expanda **Territory** (Territorio) y seleccione **KY** y **TN**.

    ![Captura de pantalla del panel visualizaciones con el filtro para KY y TN.](./media/end-user-drill/power-bi-filter.png)

    Ahora solo se muestran dos territorios en el treemap.

    ![Captura de pantalla del objeto visual con KY y TN resaltados.](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-use-the-drill-features"></a>Tres maneras de usar las características de exploración en detalle

Tiene varias opciones para acceder a las características de rastrear desagrupando datos, rastrear agrupando datos y expandir para las visualizaciones que tienen jerarquías. En este artículo se explica cómo usar la primera opción. Una vez que aprenda los aspectos básicos del rastreo desagrupando datos y la expansión, sabrá como utilizar las tres. Todas realizan las mismas funciones. Pruébelas y quédese con la que más le guste.

- Mantenga el mouse sobre una visualización para ver y usar los iconos.  

    ![Captura de pantalla del ejemplo al mantener el puntero.](./media/end-user-drill/power-bi-hover.png)

- Haga clic con el botón derecho en una visualización para mostrar el menú y usarlo.

    ![Captura de pantalla del ejemplo al hacer clic con el botón derecho.](./media/end-user-drill/power-bi-drill-menu.png)

- En la barra de menús de Power BI, seleccione el botón **Explorar**.

   ![Captura de pantalla de la selección de la opción de exploración que muestra los iconos y opciones que contiene.](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>Rutas de exploración

### <a name="drill-down"></a>Rastrear desagrupando datos

Existen varias formas de explorar en profundidad la visualización. **Rastrear desagrupando datos** le lleva al siguiente nivel en la jerarquía. Si está mirando el nivel **Territory** (Territorio), puede rastrear desagrupando datos al nivel City (Ciudad), luego al nivel Postal Code (Código postal) y, por último, al nivel Name (Nombre). Cada paso de la ruta muestra información nueva.

![Diagrama que muestra la ruta de exploración](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Expandir

**Expandir** agrega un nivel de jerarquía adicional a la vista actual. Por tanto, si está mirando el nivel **Territory** (Territorio), puede expandir y agregar City (Ciudad), Postal Code (Código postal) y Name (Nombre) al gráfico de rectángulos. Cada paso de la ruta muestra la misma información y agrega un nivel de información nueva.

![Diagrama que muestra la ruta de expansión](./media/end-user-drill/power-bi-expand-path.png)

También puede elegir si quiere rastrear desagrupando datos o expandir solo un campo o todos los campos a la vez.

## <a name="drill-down-all-fields-at-once"></a>Rastreo desagrupando datos de todos los campos a la vez

1. Empiece en el nivel superior del treemap, que muestra datos de KY y TN. Amplíe el treemap seleccionando uno de los controladores y arrastrándolo a la derecha.

    ![Captura de pantalla del objeto visual del gráfico de rectángulos que muestra KY y TN](./media/end-user-drill/power-bi-drill-down.png)

1. Para rastrear desagrupando datos de *todos los campos a la vez*, seleccione la flecha doble de la esquina superior izquierda de la visualización ![icono doble del rastreo desagrupando datos](./media/end-user-drill/power-bi-drill-icon3.png). El treemap muestra ahora los datos de ciudad de Kentucky y Tennessee.

    ![Captura de pantalla del objeto visual del gráfico de rectángulos que muestra la exploración en profundidad hacia las ciudades.](./media/end-user-drill/power-bi-drill-down1.png)

1. Rastree desagrupando datos una vez más en el nivel Postal Code (Código postal) de la jerarquía.

    ![Captura de pantalla del objeto visual del gráfico de rectángulos que muestra la exploración en profundidad hacia el código postal.](./media/end-user-drill/power-bi-drill-down2.png)

1. Para volver a rastrear agrupando datos, seleccione la flecha ascendente situada en la esquina superior izquierda de la visualización ![Captura de pantalla del icono para rastrear agrupando datos un nivel.](./media/end-user-drill/power-bi-drill-icon5.png).

## <a name="drill-down-one-field-at-a-time"></a>Rastrear desagrupando datos un solo campo a la vez

Este método usa los iconos del modo detallado que aparecen en la esquina superior derecha de la propia visualización.

1. Seleccione el icono de rastrear desagrupando datos para activar esta opción ![Captura de pantalla del icono para activar/desactivar la opción de rastrear desagrupando datos en modo activado.](./media/end-user-drill/power-bi-drill-icon2.png).

    Ahora tiene la opción de rastrear desagrupando datos de **un solo campo a la vez**.

    ![Captura de pantalla del objeto visual con flecha que apunta al icono de activación o desactivación de rastrear desagrupando datos en modo activado.](media/end-user-drill/power-bi-drill-icon-new.png)

    Si no activa el rastreo desagrupando datos, la selección de un elemento de visualización (como una barra, burbuja u hoja) no explorará en profundidad, sino que aplicará un filtro cruzado a los otros gráficos de la página del informe.

1. Seleccione el nodo hoja para **TN**. El gráfico de rectángulos muestra ahora todas las ciudades de Tennessee que tienen una tienda.

    ![Captura de pantalla del gráfico de rectángulos que muestra datos solo de TN.](media/end-user-drill/power-bi-drill-down-one1.png)

1. En este momento, puede hacer lo siguiente:

    1. Seguir profundizando para Tennessee.

    1. Explorar en profundidad para una ciudad determinada de Tennessee.

    1. Optar por expandir (consulte **Expandir todo** a continuación).

    Sigamos rastreando desagrupando datos de un solo campo a la vez.  Seleccione **Knoxville, TN**. El gráfico de rectángulos muestra ahora el código postal de la tienda en Knoxville.

    ![Captura de pantalla del gráfico de rectángulos que muestra datos solo del código postal 37919.](media/end-user-drill/power-bi-drill-down-one2.png)

    Observe que el título cambia a medida que realiza la exploración en profundidad y vuelve a agruparlos de nuevo.

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandir todo y expandir un campo a la vez

Tener un gráfico de rectángulos que nos muestra solo un código postal no es muy informativo.  Así que vamos a expandir un nivel en la jerarquía.  

1. Con el gráfico de rectángulos activo, seleccione el icono de *expandir* ![Captura de pantalla del icono de expandir](./media/end-user-drill/power-bi-drill-icon6.png). El gráfico de rectángulos muestra ahora dos niveles de la jerarquía: código postal y nombre de la tienda.

    ![Captura de pantalla del gráfico de rectángulos que muestra el código postal y el nombre de la tienda](./media/end-user-drill/power-bi-expand1.png)

1. Para ver los cuatro niveles de jerarquía de datos para Tennessee, haga clic en la flecha arriba de exploración hasta llegar al segundo nivel **Total units this year by territory and city** (Unidades totales este año por territorio y ciudad) del gráfico de rectángulos.

    ![Captura de pantalla del gráfico de rectángulos que muestra todos los datos de TN.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Asegúrese de que el rastreo desagrupando datos sigue activado, ![Captura de pantalla del icono para activar/desactivar la opción de rastrear desagrupando datos en modo activado.](./media/end-user-drill/power-bi-drill-icon2.png) y seleccione el icono de *expandir* ![Captura de pantalla del icono de expandir](./media/end-user-drill/power-bi-drill-icon6.png). Ahora, el gráfico de rectángulos muestra algunos detalles adicionales. En lugar de mostrar solo la ciudad y el estado, también muestra el código postal.

    ![Captura de pantalla del gráfico visual que muestra la ciudad, el estado y el código postal.](./media/end-user-drill/power-bi-expand-one3.png)

1. Haga clic en el icono de *expandir* una vez más para mostrar los cuatro niveles de jerarquía de detalle para Tennessee en el gráfico de rectángulos. Mantenga el mouse sobre un nodo hoja para ver más detalles.

    ![Captura de pantalla del gráfico de rectángulos que muestra información sobre herramientas con datos específicos de la hoja.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>Filtros de detalles en otros objetos visuales

Cuando se trabaja en el modo detallado, tiene que decidir en qué medida afecta el rastreo desagrupando datos y la expansión a otras visualizaciones de la página.

De forma predeterminada, el modo detallado no filtrará otros objetos visuales en un informe. Puede habilitar esta característica en el servicio Power BI y en Power BI Desktop.

1. En Desktop, seleccione la pestaña **Formato** y active la casilla para **Filtros de detalles en otros objetos visuales**.

    ![Captura de pantalla que muestra el ajuste Filtros de detalles en otros objetos visuales en Power BI Desktop](./media/end-user-drill/power-bi-drill-filters-desktop.png)

1. Ahora, cuando rastree desagrupando o agrupando datos o con la opción de expansión en una visualización con una jerarquía, esa acción filtrará los otros objetos visuales de la página.

    ![Captura de pantalla del resultado en Desktop.](./media/end-user-drill/power-bi-drill-filters.png)

    ![Captura de pantalla del otro resultado en Desktop.](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> Para habilitar esta opción en el servicio Power BI, en la barra de menús superior, seleccione **Interacciones de objetos visuales** > **Filtros de detalles en otros objetos visuales**.
>
> ![Captura de pantalla del ajuste Filtros de detalles en otros objetos visuales en el servicio Power BI](./media/end-user-drill/power-bi-drill-filters-service.png)

## <a name="learn-about-the-hierarchy-axis-and-hierarchy-group"></a>Información sobre el eje de jerarquías y el grupo de jerarquías

Puede pensar en el eje de jerarquías y el grupo de jerarquías como los mecanismos que puede usar para aumentar y reducir la granularidad de los datos que quiere ver. Los datos que puede organizar en categorías y subcategorías pueden tener una jerarquía, incluidas fechas y horas.

En Power BI puede crear una visualización que tenga una jerarquía si selecciona uno o más campos de datos y los agrega al área **Eje** o **Grupo**. A continuación, agregue los datos que quiere examinar como campos de datos en el área **Valores**. Sabrá que los datos son jerárquicos si aparecen los iconos del *modo de exploración* en las esquinas superior izquierda y derecha de la visualización.

Básicamente, resulta práctico considerarlo como dos tipos de datos jerárquicos:

- Datos de fecha y hora: si tiene un campo de datos con un tipo de datos DateTime, ya tiene datos jerárquicos. Power BI crea automáticamente una jerarquía para cualquier campo de datos. Puede analizar los valores en una estructura [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx). Solo tiene que agregar un campo DateTime al área **Eje** o **Grupo**.

- Datos de categorías: si Power BI deriva los datos de colecciones que contienen subcolecciones o tienen filas de datos que comparten valores comunes, tiene datos jerárquicos.

Power BI le permite expandir por uno o por todos los subconjuntos. Puede rastrear desagrupando datos para ver un único subconjunto en cada nivel o para ver todos los subconjuntos de forma simultánea en cada nivel. Por ejemplo, puede explorar en profundidad un año determinado o ver todos los resultados de cada año a medida que baja por la jerarquía.

A la inversa, puede rastrear agrupando datos de la misma manera.

En las secciones siguientes se describe la exploración en profundidad desde la vista superior, la media y la inferior.

### <a name="hierarchical-data-and-time-data"></a>Datos jerárquicos y datos de hora

En este ejemplo:

1. Siga con el [ejemplo de análisis de venta directa](../sample-datasets.md) y cree una visualización de gráfico de columnas apiladas que examine:

    | Área | Campo |
    | ---- | ----- |
    | Eje | Hora<br>\|\_ Mes |
    | Valores | Ventas<br>\|\_ Total de ventas |

    Aunque el campo de datos Axis es **Month**, sigue creando una categoría **Year** en el área **Axis**. Esto es debido a que Power BI proporciona la estructura DateTime completa para todos los valores que lee. La parte superior de la jerarquía muestra los datos del año.

    ![Captura de pantalla de barra que muestra los datos agrupados por año](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

1. Con el modo de rastrear desagrupando datos activado, seleccione la barra del gráfico para bajar un nivel de la jerarquía. Verá tres barras para los datos de los trimestres disponibles.

1. Luego, en los iconos izquierdos superiores, elija **Expand all down one level of the hierarchy** (Expandir hacia abajo un nivel de la jerarquía).

1. Hágalo una vez más para ir al nivel inferior de la jerarquía, que muestra resultados de cada mes.

    ![Captura de pantalla del gráfico de barras para ver la barra por mes](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

Además de la visualización, se puede ver la jerarquía reflejada en los datos representados para cada informe. En la esquina superior derecha, seleccione los puntos suspensivos y, a continuación, **Mostrar datos**. La siguiente tabla muestra los resultados del rastreo desagrupando datos de un solo mes o todos los meses:

|Modo expandido|Año|Trimestre|Mes|Día|
| --- |:---:|:---:|:---:|---|
|Único|![un solo año](./media/end-user-drill/power-bi-hierarchical-year.png)|![un solo trimestre](media/end-user-drill/power-bi-hierarchical-quarter.png)|![un solo mes](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![un solo día](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Todo|![todos los años](./media/end-user-drill/power-bi-hierarchical-year.png)|![todos los trimestres](media/end-user-drill/power-bi-hierarchical-quarter.png)|![todos los meses](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![todos los días](media/end-user-drill/power-bi-hierarchical-all-day.png)|

Tenga en cuenta que los datos son los mismos para los informes de **trimestre** y **año**. Después de explorar en profundidad al nivel de detalle especificado para **Valores**, puede ver cómo el informe único se vuelve más específico y el informe "todos los meses" tiene más datos.

### <a name="hierarchical-category-data"></a>Datos de categoría jerárquicos

Los datos modelados a partir de colecciones y subcolecciones son jerárquicos.

Un buen ejemplo son los datos de ubicación. Imagine una tabla de un origen de datos cuyas columnas son País, Estado, Ciudad y Código postal. Los datos que comparten el mismo País, Estado y Ciudad son jerárquicos.

En este ejemplo:

1. Para este ejemplo, continúe con el [ejemplo de análisis de venta directa](../sample-datasets.md). Creación de una visualización de gráfico de columnas apiladas que se fije en:

    | Área | Campo |
    | ---- | ----- |
    | Valor |Ventas<br>\|\_ Unidades totales de este año |
    | Eje | Tienda<br>\|\_ Territorio<br>\|\_ Ciudad: es posible que deba arrastrar Ciudad desde el área **Leyenda** al área **Eje**.<br>\|\_ Código postal<br>\|\_ Nombre |

    ![Captura de pantalla del gráfico de barras que muestra las unidades totales de este año por territorio.](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

1. Con el modo de rastrear desagrupando datos activado, en los iconos izquierdos superiores, elija **Expand all down one level of the hierarchy** (Expandir hacia abajo un nivel de la jerarquía) tres veces.

    Debería encontrarse en el nivel inferior de la jerarquía, que muestra los resultados de territorio, ciudad y código postal.

    ![Captura de pantalla del gráfico de barras que muestra el nivel más bajo de la jerarquía, nivel más detallado.](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

Además de la visualización, se puede ver la jerarquía reflejada en los datos representados para cada informe. En la esquina superior derecha, seleccione los puntos suspensivos y, a continuación, **Mostrar datos**. La siguiente tabla muestra los resultados de explorar en profundidad un solo territorio o todos los territorios.

| Modo expandido|Territorio|Ciudad|Postal|Nombre|
| ---|:---:|:---:|:---:|---|
|Único|![un solo territorio](./media/end-user-drill/power-bi-hierarchical-territory.png)|![una sola ciudad](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![un solo código postal](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![un solo nombre](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Todo|![todos los territorios](./media/end-user-drill/power-bi-hierarchical-territory.png)|![todas las ciudades](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![todos los códigos postales](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![todos los nombres](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|

 Al explorar en profundidad, puede ver cómo el informe **único** se vuelve más específico y que el informe de **todos los territorios** tiene más datos.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Si al agregar un campo de fecha a una visualización no se crea una jerarquía, es posible el campo de fecha no se guarde realmente como una fecha. Si es el propietario del conjunto de datos:

1. Abra la vista *Datos* en Power BI Desktop.

1. Seleccione la columna que tiene la fecha.

1. En la pestaña **Modelado**, cambie el **Tipo de datos** a **Fecha** o **Fecha y hora**.

![Captura de pantalla de la selección de la vista de datos y, en la esquina superior derecha, puede ver el tipo de fecha.](media/end-user-drill/power-bi-change-data-type2.png)

Si el informe se ha compartido con usted, póngase en contacto con el propietario para solicitar el cambio.

## <a name="next-steps"></a>Pasos siguientes

[Visualizaciones en informes de Power BI](../visuals/power-bi-report-visualizations.md)

[Informes de Power BI](end-user-reports.md)

[Power BI: Conceptos básicos](end-user-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
