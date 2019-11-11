---
title: Sugerencias y trucos para el formato de color en Power BI
description: Sugerencias y trucos para el formato de color en Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3865647a056e28735894e40f71045305518642c6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880640"
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

![dónde encontrar el menú Editar](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-report.png)

Cuando aparezcan los paneles **Filtros** y **Visualizaciones** en el lado derecho del lienzo del informe, podrá comenzar el proceso de personalización. Si no aparece el panel, seleccione la flecha, en la esquina superior derecha, para abrirlo.

![lienzo del informe en la vista de edición](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

## <a name="change-the-color-of-a-single-data-point"></a>Cambiar el color de un solo punto de datos
En ocasiones deseará resaltar un punto de datos determinado. Tal vez sea una cifra de ventas para el lanzamiento de un producto nuevo, o el aumento de los resultados de calidad tras lanzar un nuevo programa. Con Power BI, puede resaltar un punto de datos determinado cambiándole el color.

La visualización siguiente clasifica unidades vendidas por segmento de producto. 

![Cambio de los colores de datos a gris](media/service-tips-and-tricks-for-color-formatting/power-bi-data.png)

Ahora suponga que desea destacar el segmento **Convenience** para mostrar su buen rendimiento utilizando para ello color. Estos son los pasos que debe realizar:

Expanda la sección **Colores de datos** y active el control deslizante para **Mostrar todo**. De este modo, se muestran los colores de cada elemento de datos en la visualización. Al mantener el puntero sobre los puntos de datos, se habilita el desplazamiento para permitirnos modificar cualquiera de estos.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show.png)

Establezca **Convenience** en naranja. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

Una vez seleccionado, el punto de datos de **Convenience** aparece en un bonito tono naranja que, ciertamente, consigue destacar.

Si lo desea, puede cambiar los tipos de visualización y volver después: Power BI recordará su selección y mantendrá **Convenience** en naranja.

Puede cambiar el color de un punto de datos para uno, varios o todos los elementos de datos en la visualización. Quizás desee que el objeto visual imite sus colores corporativos. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Se puede hacer de todo con los colores. En la siguiente sección, echamos un vistazo a los degradados.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Basar los colores de un gráfico en un valor numérico
Los gráficos suelen establecer dinámicamente el color en función del valor numérico de un campo. De este modo, es posible mostrar un valor diferente al que se usa para el tamaño de una barra y mostrar dos valores en un solo gráfico. También puede usar esta opción para resaltar los puntos de datos por encima (o por debajo) de un valor determinado (por ejemplo, para resaltar las áreas de baja rentabilidad).

Las secciones siguientes muestran distintos mecanismos para basar el color en un valor numérico.

## <a name="base-the-color-of-data-points-on-a-value"></a>Basar el color de los puntos de datos en un valor
Para cambiar el color según un valor, abra el panel de formato y seleccione la opción **Formato condicional**.  

![selección de la opción de formato condicional mediante un clic en los tres puntos verticales](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting.png)

En el panel de colores predeterminado, use las listas desplegables para identificar los campos que se usarán para el formato condicional. En este ejemplo, hemos seleccionado el campo **Datos de ventas** > **Total de unidades** y hemos seleccionado azul claro para el **valor más bajo** y azul oscuro para el **valor más alto**. 

![configuración del formato condicional por el color de los datos](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![gráfico de columnas con los colores predeterminados aplicados](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

También puede dar formato al color del objeto visual mediante un campo que no forma parte del objeto visual. En la siguiente imagen, se usa **%Market Share SPLY YTD**. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


Como puede ver, aunque hemos vendido más unidades de **Productivity** y **Extreme** (sus columnas son superiores), **Moderation** tiene un valor más elevado de **%Market Share SPLY YTD** (su columna tiene más de saturación de color).

## <a name="customize-the-colors-used-in-the-color-scale"></a>Personalizar los colores de la escala de colores
También puede cambiar la forma en que los valores se asignan a estos colores. En la imagen siguiente, los colores de **Mínimo** y **Máximo** están establecidos en naranja y verde, respectivamente.

En esta primera imagen, fíjese en que las barras del gráfico reflejan el degradado que se muestra en la barra. El valor más alto es verde, el más bajo es naranja y las barras del medio están coloreadas con tonos del espectro existente entre estos dos colores.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Ahora, veamos qué sucede si se proporcionan valores numéricos en los cuadros de texto **Mínimo** y **Máximo**. Establezcamos el valor **Mínimo** en 3 500 y el **Máximo**, en 6 000.

Si se establecen estos valores, el degradado ya no se aplica a los valores del gráfico que están por debajo del **Mínimo** o por encima del **Máximo**. Todas las barras con valores por encima del **Máximo** se colorean de verde, y las que tienen valores por debajo del **Mínimo** se colorean de rojo.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

## <a name="use-diverging-color-scales"></a>Usar escalas de colores divergentes
A veces los datos pueden tener una escala que diverge de forma natural. Por ejemplo, un intervalo de temperatura tiene un centro natural en el punto de congelación, y los resultados de rentabilidad tienen un punto medio natural (cero).

Para usar escalas de colores divergentes, seleccione la opción **Divergente**. Cuando se activa **Divergente**, aparece un selector de colores adicional denominado **Centro**, tal como indica la imagen siguiente.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging2.png)

Al activar el control deslizante **Divergente** , pueden establecerse los colores **Mínimo**, **Máximo** y **Centro** por separado. En la imagen siguiente, **Centro** está establecido en 0.2 para **% Market Share SPLY YTD**, por lo que las barras con valores superiores a 0.2 presentan un tono degradado verde y las barras con valores inferiores a uno presentan tonos rojos.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

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

