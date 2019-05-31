---
title: Sugerencias y trucos para el formato de color en Power BI
description: Sugerencias y trucos para el formato de color en Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d3fba99c5b6b639d851b62d5624331b0bef1567d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61390898"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Sugerencias y trucos para el formato de color en Power BI
Power BI permite personalizar los paneles y los informes de muchas formas. En este artículo se detallan una serie de sugerencias para que las visualizaciones de Power BI resulten más atractivas, interesantes y personalizadas según sus necesidades.

A continuación se proporcionan varias sugerencias. ¿Tiene alguna otra? Magnífico. Envíenosla para que estudiemos si puede agregarse a esta lista.

* Cambiar el color de un solo punto de datos
* Basar los colores de un gráfico en un valor numérico
* Basar el color de los puntos de datos en un valor de campo
* Personalizar los colores de la escala de colores
* Usar escalas de colores divergentes
* Cómo deshacer acciones en Power BI

Para realizar cambios, debe modificar un informe. Abra el informe y seleccione **Editar informe** en el área del menú superior, como se muestra en la siguiente imagen.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

Cuando aparezca el panel **Visualizaciones** en el lado derecho del lienzo **Informe** , podrá comenzar el proceso de personalización. Si no aparece el panel, seleccione la flecha, en la esquina superior derecha, para abrirlo.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-formatting-pane.png)

## <a name="change-the-color-of-a-single-data-point"></a>Cambiar el color de un solo punto de datos
En ocasiones deseará resaltar un punto de datos determinado. Tal vez sea una cifra de ventas para el lanzamiento de un producto nuevo, o el aumento de los resultados de calidad tras lanzar un nuevo programa. Con Power BI, puede resaltar un punto de datos determinado cambiándole el color.

La visualización siguiente clasifica unidades vendidas por segmento de producto. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-grey.png)

Ahora suponga que desea destacar el segmento **Convenience** para mostrar su buen rendimiento utilizando para ello color. Estos son los pasos que debe realizar:

Expanda la sección **Colores de datos** y active el control deslizante para **Mostrar todo**. De este modo, se muestran los colores de cada elemento de datos en la visualización. Al mantener el puntero sobre los puntos de datos, se habilita el desplazamiento para permitirnos modificar cualquiera de estos.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Establezca **Convenience** en naranja. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-orange.png)

Una vez seleccionado, el punto de datos de **Convenience** aparece en un bonito tono naranja que, ciertamente, consigue destacar.

Si lo desea, puede cambiar los tipos de visualización y volver después: Power BI recordará su selección y mantendrá **Convenience** en naranja.

Puede cambiar el color de un punto de datos para uno, varios o todos los elementos de datos en la visualización. Quizás desee que el objeto visual imite sus colores corporativos. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Se puede hacer de todo con los colores. En la siguiente sección, echamos un vistazo a los degradados.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Basar los colores de un gráfico en un valor numérico
Los gráficos suelen establecer dinámicamente el color en función del valor numérico de un campo. De este modo, es posible mostrar un valor diferente al que se usa para el tamaño de una barra y mostrar dos valores en un solo gráfico. También puede usar esta opción para resaltar los puntos de datos por encima (o por debajo) de un valor determinado (por ejemplo, para resaltar las áreas de baja rentabilidad).

Las secciones siguientes muestran distintos mecanismos para basar el color en un valor numérico.

## <a name="base-the-color-of-data-points-on-a-value"></a>Basar el color de los puntos de datos en un valor
Para cambiar el color en función de un valor, arrastre el campo en el que desea basar el color al área **Saturación de color**, en el panel **Campo**. En la imagen siguiente, se arrastró **%Market Share SPLY YTD** a **Saturación de color**. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-color-saturation.png)

Y en el panel de formato, en **Colores de datos**, determine cómo modificará el color y el sombreado el valor de **%Market Share SPLY YTD** en el gráfico de columnas. En este ejemplo, un valor bajo de %Market Share será azul claro y los valores más altos serán azul oscuro.


![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Como puede ver, aunque hemos vendido más unidades de **Productivity** y **Extreme** (sus columnas son superiores), **Moderation** tiene un valor más elevado de **%Market Share SPLY YTD** (su columna tiene más de saturación de color).

![](media/service-tips-and-tricks-for-color-formatting/power-bi-saturation.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>Personalizar los colores de la escala de colores
También puede personalizar los colores de la escala de colores De forma predeterminada, se asigna el valor inferior de los datos al color menos saturado, y el valor más alto al más saturado. En la imagen anterior, se usa un degradado de color azul. 

Expanda la sección **Colores de datos** y verá un degradado de colores que se usan para visualizar los datos. El rango de colores se muestra en la barra de degradado, que muestra el espectro entre los valores de color **Mínimo** y **Máximo** , con el valor de color **Mínimo** a la izquierda y **Máximo** a la derecha.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Si desea cambiar la escala para usar otro rango de colores, seleccione la lista desplegable de colores situada junto a **Mínimo** o **Máximo**y seleccione un color. En la imagen siguiente se muestra el color **Máximo** cambiado a negro y la barra de degradado con el espectro del color nuevo entre el **Mínimo** y el **Máximo**.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

También puede cambiar la forma en que los valores se asignan a estos colores. En la imagen siguiente, los colores de **Mínimo** y **Máximo** están establecidos en naranja y verde, respectivamente.

En esta primera imagen, fíjese en que las barras del gráfico reflejan el degradado que se muestra en la barra. El valor más alto es verde, el más bajo es naranja y las barras del medio están coloreadas con tonos del espectro existente entre estos dos colores.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Ahora veamos qué sucede si se proporcionan valores numéricos en los cuadros de valor **Mínimo** y **Máximo** , que se encuentran debajo de los selectores de colores **Mínimo** y **Máximo** (mostrados en la imagen siguiente). Establezcamos el valor **Mínimo** en 20 000 000 y el **Máximo**, en 20 000 001.

Si se establecen estos valores, el degradado ya no se aplica a los valores del gráfico que están por debajo del **Mínimo** o por encima del **Máximo**. Todas las barras con valores por encima del **Máximo** se colorean de verde, y las que tienen valores por debajo del **Mínimo** se colorean de rojo.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Usar escalas de colores divergentes
A veces los datos pueden tener una escala que diverge de forma natural. Por ejemplo, un intervalo de temperatura tiene un centro natural en el punto de congelación, y los resultados de rentabilidad tienen un punto medio natural (cero).

Para usar escalas de colores divergentes, deslice el control **Divergente** a **Activado**. Cuando se activa **Divergente** , aparecen un selector de colores y un cuadro de valores adicionales, ambos denominados **Centro**, tal como indica la imagen siguiente.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

Al activar el control deslizante **Divergente** , pueden establecerse los colores **Mínimo**, **Máximo** y **Centro** por separado. En la imagen siguiente, **Centro** está establecido en uno, por lo que las barras con valores superiores a uno presentan un tono degradado verde, y las barras con valores inferiores a uno presentan tonos rojos.

## <a name="how-to-undo-in-power-bi"></a>Cómo deshacer acciones en Power BI
Al igual que muchos otros servicios y software de Microsoft, Power BI permite deshacer el último comando fácilmente. Por ejemplo, pongamos que cambia el color de un punto de datos o de una serie de puntos de datos y no le gusta el color cuando aparece en la visualización. No recuerda exactamente qué color tenía antes, pero sabe que desea recuperar ese color.

Para **deshacer** la última acción, o las últimas acciones, lo único que debe hacer es:

- Escribir CTRL+Z.

## <a name="feedback"></a>Comentarios
¿Tiene una sugerencia que le gustaría compartir? Envíenosla para que estudiemos si puede agregarse a esta lista.

>[!NOTE]
>Estas personalizaciones del color, de los ejes y otras relacionadas, disponibles cuando se selecciona el icono **Formato**, también están disponibles en Power BI Desktop.

## <a name="next-steps"></a>Pasos siguientes
[Introducción a las propiedades de eje y formato de color](service-getting-started-with-color-formatting-and-axis-properties.md)

