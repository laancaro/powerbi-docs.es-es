---
title: Novedades en el servidor de informes de Power BI
description: Conozca las novedades del servidor de informes de Power BI. Se incluyen las áreas de características principales. Esta información se actualiza a medida que se publican nuevos elementos.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: 526a971817c50599bf77ae085f3d5ff07294b25b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858756"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novedades en el servidor de informes de Power BI

Obtenga información sobre las novedades de Power BI Report Server y Power BI Desktop optimizado para Power BI Report Server. En este artículo se cubren las principales áreas de características y se actualiza con cada nueva versión.

Para consultar información sobre las "novedades" de Power BI, vea:

* [Novedades en el servicio Power BI](../service-whats-new.md)
* [Novedades de Power BI Desktop](../desktop-latest-update.md)
* [Novedades en las aplicaciones móviles para Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="september-2019"></a>Septiembre de 2019

Consulte la entrada de blog [Power BI Report Server, septiembre de 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/) para obtener más información sobre todas las características nuevas.

La actualización de septiembre de 2019 de Power BI Report Server incluye muchas características de informes de Power BI. Estos son algunos de los aspectos destacados:

- **Filtros de nivel visual para las segmentaciones** Puede agregar un filtro de nivel visual a las segmentaciones. Funciona como cualquier otro filtro de nivel visual, pero simplemente filtra la propia segmentación y no otros objetos visuales. Este filtro es útil para filtrar los espacios en blanco o si quiere usar filtros de medida.
- **Conjuntos de iconos de tabla y matriz** Gracias a los iconos de KPI, se pueden configurar reglas para mostrar diferentes conjuntos de iconos en la tabla y la matriz, parecido a los conjuntos de iconos de Excel.
- **Agrupación de objetos visuales** Ahora se pueden agrupar objetos visuales, formas, cuadros de texto, imágenes y botones en una página del informe, como en PowerPoint. Al agrupar objetos, se pueden mover todos juntos y cambiar el tamaño a la vez. La agrupación hace que resulte más fácil trabajar en informes con una gran cantidad de objetos en capas en cada página.
- **Nuevos temas predeterminados** Para concordar con las nuevas opciones JSON de tema, se están actualizando los temas disponibles para los informes y se está cambiando el tema predeterminado para los nuevos informes. El nuevo tema predeterminado se adapta mejor al lenguaje de diseño de Microsoft y sigue los procedimientos recomendados de diseño para los objetos visuales. 
- **Diseño del panel actualizado** Hemos actualizado gran parte de nuestra interfaz. Hemos actualizado todos los paneles, el pie de página y el modificador de vista para que sean de un color más claro; también se ha actualizado el espaciado y se han introducido nuevos iconos. El nuevo diseño es el primer paso para actualizar toda la interfaz.

Esta es la lista completa de características. 

### <a name="reporting"></a>Informes

- Diseño del panel actualizado
- Filtros de nivel de objeto visual para las segmentaciones
- Ordenación para el panel del analizador de rendimiento
- Información en pantalla del encabezado del objeto visual
- Personalización de la etiqueta del total de tablas y matrices
- Compatibilidad de la segmentación de sincronización con la segmentación de jerarquía
- Tamaños de fuente coherentes entre objetos visuales
- Conjuntos de iconos para tabla y matriz
- Porcentaje de compatibilidad con el formato condicional por reglas
- Nuevo panel de filtro ahora disponible con carácter general
- Compatibilidad con colores de datos al usar el eje de reproducción en gráficos de dispersión
- Mejoras de rendimiento al usar segmentaciones de fecha relativas y desplegables
- Agrupación de objetos visuales
- Clases de color y texto en los temas
- Nuevos temas predeterminados

### <a name="analytics"></a>Análisis

- Cadenas de formato personalizado
- Actualizaciones del formato condicional para las opciones de formato

    - Colores de segundo plano y título del objeto visual
    - Colores de tarjeta
    - Relleno y colores del medidor
    - Texto alternativo
    - Color del borde

- Formato condicional de advertencias
- Mejora de la detectabilidad en la obtención de detalles
- Nuevas expresiones DAX: REMOVEFILTERS y CONVERT
- Nuevo operador de comparación DAX: ==

### <a name="data-preparation"></a>Preparación de datos

- Mejoras en M Intellisense
- Nueva transformación: Dividir columna por posiciones
- Copia en el Portapapeles desde la creación de perfiles de datos


## <a name="may-2019-power-bi-desktop-for-power-bi-report-server"></a>Mayo de 2019: Power BI Desktop para Power BI Report Server

Consulte la entrada de blog [Power BI Report Server, mayo de 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) para obtener más información sobre todas las características nuevas.

Estos son algunos de los aspectos destacados de la versión:

### <a name="performance-analyzer"></a>Analizador de rendimiento 

Si el informe se ejecuta más lentamente de lo esperado, pruebe el Analizador de rendimiento en Power BI Desktop. Al iniciarlo, se crea un archivo de registro con información sobre cada acción que se realiza en el informe. Obtenga más información sobre el [Analizador de rendimiento](../desktop-performance-analyzer.md).

### <a name="new-modeling-view"></a>Nueva vista de modelo

En la nueva Vista de modelo de Power BI Desktop, puede ver y trabajar con conjuntos de datos complejos que contienen muchas tablas. Los resaltados incluyen varios diseños de diagramas y edición masiva de columnas, medidas y tablas. Obtenga más información sobre [Vista de modelo](../desktop-modeling-view.md).

### <a name="accessible-visual-interaction"></a>Interacción de objetos visuales accesible

Ahora puede usar la navegación con el teclado para acceder a los puntos de datos en muchos de los objetos visuales integrados. Obtenga más información sobre [Accesibilidad en los informes de Power BI](../desktop-accessibility.md).

### <a name="conditional-formatting-titles-and-web-url-actions"></a>Títulos de formato condicional y acciones de dirección URL web

Los informes de Power BI son interactivos. Tiene sentido que los títulos de un informe sean dinámicos, a fin de reflejar el estado actual del informe. Puede usar el mismo formato enlazado a una expresión para que las direcciones URL de los botones, formas e imágenes sean dinámicas. Obtenga más información sobre los [Títulos basados en expresiones](../desktop-conditional-format-visual-titles.md).

### <a name="cross-highlight-by-axis-labels"></a>Resaltado cruzado por etiquetas de eje

Seleccione las etiquetas de la categoría del eje en un elemento visual para resaltar de forma cruzada el resto de elementos de una página, igual que seleccionaría los puntos de datos de un elemento visual. Obtenga más información sobre el [Resaltado cruzado](../power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

### <a name="all-the-new-features"></a>Todas las características nuevas

Esta es la lista de todas las características nuevas:

### <a name="reporting"></a>Informes

- Resaltado cruzado en un único punto en los gráficos de líneas 
- Ajuste automático de línea en los títulos 
- Actualización de las interacciones predeterminadas de objetos visuales para aplicar filtros cruzados ¬
- Esquinas redondeadas para los bordes de los objetos visuales 
- Segmentación de selección única  
- Compatibilidad del mapa térmico con los mapas de Bing  
- Resaltado cruzado por etiquetas de eje  
- Formato de información sobre herramientas predeterminada  
- Compatibilidad de la dirección URL web estática con botones, formas e imágenes  
- Opciones de alineación de página   
- Mejoras del panel de selección  
- Interacción de objetos visuales accesible  
- Formato condicional para títulos de objetos visuales  
- Formato condicional para acciones de direcciones URL web para botones, formas e imágenes
- Panel de Analizador de rendimiento
- Navegación mediante teclado en tablas y matrices
- Control de la posición de la etiqueta de datos de línea
- Control del tamaño de texto de un indicador visual de KPI

### <a name="analytics"></a>Análisis

- Mostrar fechas como jerarquía ahora disponible con carácter general  

### <a name="modeling"></a>Modelado

- Nueva vista de modelo ahora disponible con carácter general
- Nuevas funciones de DAX
- Actualización a la función DAX ALLSELECTED
- Deshabilitación de las tablas de fecha automática para los nuevos informes

## <a name="may-2019-power-bi-report-server"></a>Mayo de 2019: Power BI Report Server

### <a name="support-for-trusted-visuals"></a>Compatibilidad con los objetos visuales de confianza

Se ha agregado compatibilidad con objetos visuales de confianza para Power BI Report Server. Actualmente se admiten los objetos visuales de MapBox y PowerOn. ESRI, Visio y PowerApps no se admiten en esta versión.

### <a name="improved-security-features"></a>Características de seguridad mejoradas

**RestrictedResourceMimeTypeForUpload**, que los administradores pueden usar para especificar una lista separada por comas de tipos MIME prohibidos, por ejemplo, texto/html.

## <a name="january-2019"></a>Enero de 2019

Compatibilidad con estas características en los informes de Power BI:

[**Seguridad de nivel de fila**](row-level-security-report-server.md) La configuración de Seguridad de nivel de fila (RLS) en Power BI Report Server puede restringir el acceso a los datos para determinados usuarios. Los filtros restringen el acceso a los datos en el nivel de fila y se pueden definir en roles.

[**Expandir y contraer en los encabezados de fila de matriz**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Hemos agregado la capacidad de expandir y contraer los encabezados de fila de forma individual, una de las características visuales más solicitadas.

[**Copiar y pegar entre archivos .pbix**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) Los objetos visuales se pueden copiar de un archivo .pbix a otro desde el menú contextual del objeto visual o mediante métodos abreviados de teclado: Ctrl+C para copiar y CTRL+V para pegarlo en otro informe.

[**Guías de alineación inteligente**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Las guías de alineación inteligente se muestran cuando se mueven los objetos de la página del informe, al igual que en PowerPoint, para ayudarle a alinear todo el contenido. Las guías inteligentes se muestran siempre que se arrastra o se cambia de tamaño algún elemento de la página. Si coloca un objeto cerca de otro, se ajusta en una posición alineada con el otro objeto.

**Características de accesibilidad** Hay tantas características de accesibilidad que es imposible enumerarlas: por ejemplo, la [accesibilidad del panel de la lista de campos](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). El panel de la lista de campos es totalmente accesible. Puede navegar por el panel mediante el teclado y un lector de pantalla, y usar el menú contextual para agregar campos a la página del informe.

#### <a name="custom-visuals"></a>Objetos visuales personalizados

- La versión de la API incluida con esta versión es 2.3.

### <a name="administrator-settings"></a>Configuración del administrador

Los administradores pueden establecer las siguientes propiedades en las propiedades avanzadas de SSMS para la granja de servidores:

**AllowedResourceExtensionsForUpload** Defina la extensiones de los recursos que se pueden cargar en el servidor de informes. No es necesario incluir las extensiones de tipos de archivo integrados como &ast;.rdl y &ast;.pbix. El valor predeterminado es "&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx". 

**SupportedHyperlinkSchemes** Establece una lista separada por comas de los esquemas de URI que pueden definirse en las acciones de hipervínculo que pueden representarse o "&ast;" para habilitar todos los esquemas de hipervínculo. Por ejemplo, si se establece “http,https”, se permitirían hipervínculos a "https://www. contoso.com", pero quitaría hipervínculos a "mailto:bill@contoso.com" o "javascript:window.open(‘www.contoso.com’, ‘_blank’)". El valor predeterminado es "&ast;".

## <a name="august-2018"></a>Agosto de 2018

La versión de agosto de 2018 incluye muchas características nuevas incorporadas a Power BI Desktop optimizado para Power BI Report Server. Aquí están, desglosadas por área:

- [Informes](#reporting)
- [Análisis](#analytics)
- [Modelado](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Aspectos destacados de la versión de agosto de 2018

De la larga lista completa de nuevas características, estas destacan por ser especialmente interesantes. Para obtener más información, vea esta [entrada de blog](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/).

#### <a name="report-theming"></a>Temas de informe

Los temas de informe se han agregado a la versión de agosto de 2018 de Power BI Report Server y permiten colorear rápidamente todo el informe para que coincida con un tema o una marca corporativa. Al importar un tema, todos los gráficos se actualizan automáticamente para usar los colores del tema; puede acceder a los colores del tema desde la paleta de colores. Puede cargar un archivo de tema con la opción **Importar tema**, debajo del botón **Cambiar tema**.

Un archivo de tema es un archivo JSON que incluye todos los colores que quiere usar en el informe junto con cualquier formato predeterminado que quiere aplicar a los objetos visuales.
Este es un tema JSON de ejemplo sencillo que solo actualiza los colores predeterminados del informe:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Formato condicional por otro campo

La capacidad de dar formato a una columna por otro campo del modelo es una de las mejoras importantes en el formato condicional.

#### <a name="conditional-formatting-by-values"></a>Formato condicional por valores

Otro tipo nuevo de formato condicional es el valor **Formato por campo**. El valor Formato por campo permite usar una medida o columna que especifica un color, ya sea mediante un código hexadecimal o un nombre, y aplica ese color al fondo o al color de fuente.

#### <a name="report-page-tooltips"></a>Información en pantalla de la página de informes

La característica Información en pantalla de la página de informes se incluye en la actualización de agosto de 2018 de Power BI Report Server. Esta característica permite diseñar una página de informes que se va a usar como una información en pantalla personalizada para otros objetos visuales del informe.

#### <a name="log-axis-improvements"></a>Mejoras del eje de registro

Se ha mejorado considerablemente el eje de registro de los gráficos cartesianos. Ahora puede seleccionar la escala de registro del eje numérico de cualquier gráfico cartesiano, incluido el gráfico combinado, si tiene datos que son completamente positivos o completamente negativos.

#### <a name="sap-hana-sso-direct-query"></a>Direct Query de SSO de SAP HANA

Compatibilidad de Direct Query de SSO de SAP HANA con Kerberos ya disponible para informes de Power BI.

>[!Note]
>Este escenario solo se admite cuando se trata SAP HANA como un origen de datos relacional con informes creados en Power BI Desktop.  Para habilitar en Power BI Desktop, en el menú de DirectQuery, en Opciones, active "Tratar SAP HANA como origen relacional" y haga clic en Aceptar.

#### <a name="custom-visuals"></a>Objetos visuales personalizados

- La versión de la API incluida con esta versión es 1.13.0.

- Ahora, los objetos visuales personalizados pueden revertir a una versión anterior compatible con la versión actual de la API de servidor (si está disponible).

### <a name="reporting"></a>Informes 

- [Temas de informe](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Botones para desencadenar acciones](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Estilos de línea en gráficos combinados](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Ordenación predeterminada mejorada para los objetos visuales](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Segmentación numérica](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Sincronización de segmentación avanzada](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Mejoras del eje de registro](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Opciones de etiqueta de datos para gráficos de embudo](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Definir el ancho del trazo de línea en cero](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Compatibilidad con el contraste alto en los informes](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Control del radio de los gráficos de anillos](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Control de la posición de las etiquetas de detalles de los gráficos circulares y de anillos](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Dar formato a las etiquetas de datos por separado para cada medida de un gráfico combinado](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Nuevos encabezados visuales con más flexibilidad y formato](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Formato de papel tapiz](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Información en pantalla de tablas y matrices](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Desactivación de las informaciones sobre herramientas de los objetos visuales](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Accesibilidad de la segmentación](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Mejoras del panel de formato](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Compatibilidad de línea escalonada con gráficos combinados y de líneas](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Mejora en la experiencia de ordenación](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Impresión de informes a través de Exportar a PDF (en Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Creación de grupos de marcadores](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Actualización de la segmentación](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Información en pantalla de la página de informes](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Análisis

- [Nueva función de DAX: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Medida de obtención de detalles](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Formato condicional por otro campo](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Formato condicional por valores](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modelado

- [Filtrado y ordenación en la vista de datos](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Formato de configuración regional mejorado](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Categorías de datos de medidas](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Funciones DAX estadísticas](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>May. 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Configurar aplicaciones móviles de iOS de Power BI para servidores de informes de forma remota

Como administrador de TI, ya puede usar la herramienta MDM de su organización para configurar el acceso de la aplicación móvil de iOS de Power BI a un servidor de informes de forma remota. Vea [Configurar el acceso de la aplicación móvil de iOS de Power BI a un servidor de informes de forma remota](configure-powerbi-mobile-apps-remote.md) para más información.

## <a name="march-2018"></a>Marzo de 2018

La versión de marzo de 2018 incluye muchísimas características nuevas a la versión de Power BI Desktop optimizado para Power BI Report Server. Aquí están, desglosadas por área:

- [Objetos visuales](#visuals-updates)
- [Informes](#reporting)
- [Análisis](#analytics)
- [Rendimiento](#performance)
- [Servidor de informes](#report-server)
- [Otros](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Aspectos destacados de la versión de marzo de 2018

De la larga lista completa de nuevas características, estas destacan por ser especialmente interesantes.

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Rule-based conditional formatting for table and matrix](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting) (Formato condicional basado en reglas para tablas y matrices)

Permite crear reglas para cambiar el color condicionalmente del fondo o la fuente de una columna, basadas en una lógica empresarial específica en la tabla o la matriz.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Show and hide pages](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages) (Mostrar y ocultar páginas)

Quiere que los lectores tengan acceso a su informe, pero aún no ha terminado algunas de sus páginas. Ahora puede ocultarlas hasta que estén listas. O puede hacer que las páginas estén ocultas en la navegación formal y los lectores puedan acceder a ellas mediante marcadores u obtención de detalles.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Bookmarking](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking) (Colocación de marcadores)

Hablando de marcadores, puede crear marcadores para contar una historia con los datos del informe.

- [Cross-highlighting for bookmarks](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting) (Resaltado cruzado para marcadores): los marcadores mantienen y muestran el estado de resaltado cruzado de la página del informe en el momento en que creó el marcador.
- [More bookmark flexibility](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility) (Mayor flexibilidad de marcadores): los marcadores reflejan las propiedades establecidas en el informe y afectan a solo los objetos visuales que elija.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Multi-select data points across multiple charts](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight) (Selección múltiples de puntos de datos en varios gráficos)

Seleccione varios puntos de datos en varios gráficos y aplique el filtrado cruzado a toda la página.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Sync slicers across multiple pages of your report](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers) (Segmentaciones sincrónicas en varias páginas del informe)

Puede aplicar una segmentación a una, dos o más páginas de un informe.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Quick measures](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) (Medidas rápidas) 

Cree nuevas medidas en función de las medidas existentes y las columnas numéricas de una tabla.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[Drilling down filters other visuals](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals) (Filtros de detalles en otros objetos visuales)

Cuando se explora en profundidad una categoría determinada de un objeto visual, puede filtrar todos los objetos visuales de la página de filtro por esa misma categoría.

### <a name="visuals-updates"></a>Actualizaciones de objetos visuales

- [Cell alignment for table and matrix](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment) (Alineación de celdas para tablas y matrices)
- [Display units and precision control for table & matrix columns](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits) (Visualización de unidades y control de precisión para columnas de tablas y matrices)
- [Overflow data labels for bar and column charts](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow) (Etiquetas de datos de desbordamiento gráficos de barras y columnas)
- [Control data label background color for Cartesian and maps visuals](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground) (Control del color de fondo de etiquetas de datos para objetos visuales de mapas y cartesianos)
- [Bar/column padding control](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding) (Control de relleno de barras y columnas)
- [Increase area used for axis labels in charts](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize) (Aumento del área que se usa para etiquetas de ejes en gráficos)
- [Scatter visual from x- & y-axis groupings](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart) (Dispersión de un objeto visual desde agrupaciones de los ejes X e Y)
- [High density sampling for maps based on latitude and longitude](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps) (Muestreo de alta densidad para mapas en función de la latitud y longitud)
- [Responsive slicers](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive) (Segmentaciones con capacidad de respuesta)
- [Add an anchor date for relative date slicer](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate) (Agregar una fecha de anclaje de una segmentación de datos de fecha relativa)

### <a name="reporting"></a>Informes

- [Turn off the visual header in reading mode for a report](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader) (Desactivación del encabezado visual de un informe en modo de lectura)
- [Report options for slow data sources](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource) (Opciones de informe para orígenes de datos lentos)
- [Improved default visual placement](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement) (Posición visual predeterminada mejorada)
- [Control visual ordering through the selection pane](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane) (Control de la ordenación de objetos visuales a través del panel de selección)
- [Lock objects on your report](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock) (Objetos de bloqueo en el informe)
- [Search the formatting and analytics pane](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search) (Búsqueda de los paneles de formato y análisis)
- [Field properties pane and field descriptions](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane) (Panel de propiedades de campo y descripciones de los campos)

### <a name="analytics"></a>Análisis

- [UTCNOW() and UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX) [UTCNOW() y UTCTODAY()]
- [Mark custom date table](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable) (Marcado de tabla de fechas personalizada)
- [Drill filters other visuals](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals) (Filtros de obtención de detalles en otros objetos visuales)
- [Cell-level formatting for multidimensional AS models for multi-row card](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting) (Formato en el nivel de celda para modelos multidimensionales de Analysis Services (AS) para tarjetas de varias filas)

### <a name="performance"></a>Rendimiento

- [Filtering performance improvements](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering) (Mejoras de rendimiento del filtrado)
- [DirectQuery performance improvements](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf) (Mejoras de rendimiento de DirectQuery)
- [Open and save performance improvements](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf) (Mejoras de rendimiento de apertura y guardado)
- [“Show items with no data” improvements](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData) (Mejoras al mostrar elementos sin datos)

### <a name="report-server"></a>Servidor de informes

#### <a name="export-to-accessible-pdf"></a>Exportar a PDF accesible

Al exportar un informe paginado (RDL) a PDF, ya puede obtener un archivo PDF accesible o etiquetado. Ocupa más tamaño pero es más fácil de leer y navegar para los lectores en pantalla y otras tecnologías de accesibilidad. Para habilitar un PDF como accesible, defina el valor de información del dispositivo **PDF accesible** en **True**. Vea [Configuración de la información del dispositivo PDF](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) y [Cambiar la configuración de la información del dispositivo](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Otras mejoras

- [Add Column From Examples improvements](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples) (Mejoras en Agregar columna a partir de ejemplos)
- [Consulting Services quick link](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices) (Vínculo rápido de servicios de consultoría)
- [Improved error reporting](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors) (Mejoras en el informe de errores)
- [View previous errors you’ve encountered](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors) (Visualización de errores anteriores detectados)

## <a name="october-2017"></a>Octubre de 2017

### <a name="power-bi-report-data-sources"></a>Orígenes de datos de informes de Power BI

Los informes de Power BI en Power BI Report Server pueden conectarse a diversos orígenes de datos. Puede importar datos y programar la actualización de datos o realizar consultas directamente mediante DirectQuery o una conexión dinámica con SQL Server Analysis Services. Consulte la lista de orígenes de datos que admiten la actualización programada y aquellos que admiten DirectQuery en "Orígenes de datos de informes de Power BI en Power BI Report Server".

### <a name="scheduled-data-refresh-for-imported-data"></a>Actualización de datos programada para los datos importados

En Power BI Report Server, puede configurar la actualización de datos programada para mantener los datos actualizados en los informes de Power BI con un modelo insertado en lugar de una conexión dinámica o DirectQuery. Con un modelo insertado se importan los datos, ya que está desconectado del origen de datos original. Debe actualizarse para mantener los datos actualizados y la actualización programada es la manera de hacerlo. Más información sobre la "actualización programada para los informes de Power BI en Power BI Report Server".

### <a name="editing-power-bi-reports-from-the-server"></a>Edición de informes de Power BI desde el servidor

Puede abrir y editar archivos de informes (.pbix) de Power BI desde el servidor, pero obtendrá el archivo original que haya cargado.  Esto significa que **si el servidor ha actualizado los datos, los datos no estarán actualizados la primera vez que abra el archivo**. Debe actualizarlos manualmente en local para ver el cambio.

### <a name="large-file-uploaddownload"></a>Carga y descarga de archivos grandes

Puede cargar archivos de hasta 2 GB de tamaño, aunque, de forma predeterminada, este límite se establece en 1 GB en la configuración del servidor de informes en SQL Server Management Studio (SSMS).  Estos archivos se almacenan en la base de datos tal como están para SharePoint y no se requiere ninguna configuración especial para el catálogo de SQL Server.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Acceso a conjuntos de datos compartidos como fuentes de OData

Puede tener acceso a conjuntos de datos compartidos desde Power BI Desktop con una fuente de OData. Para más información, consulte [Acceso a conjuntos de datos compartidos como fuentes de OData en Power BI Report Server](access-dataset-odata.md).

### <a name="scale-out"></a>Escalado horizontal

Esta versión admite escalado horizontal. Use un equilibrador de carga y establezca la afinidad del servidor para una mejor experiencia. Tenga en cuenta que el escenario aún no se ha optimizado para el escalado horizontal, por lo que podrá ver modelos que potencialmente se replican a través de varios nodos. El escenario funcionará sin el equilibrador de carga de red y sesiones permanentes. Sin embargo, no solo verá un uso excesivo de memoria en los nodos debido a que el modelo se carga N veces, sino que el rendimiento se ralentiza entre conexiones porque el modelo se transmite cuando llega a un nuevo nodo entre solicitudes.  

### <a name="administrator-settings"></a>Configuración del administrador

Los administradores pueden establecer las siguientes propiedades en las propiedades avanzadas de SSMS para la granja de servidores:

* EnableCustomVisuals: Verdadero/Falso
* EnablePowerBIReportEmbeddedModels: Verdadero/Falso
* EnablePowerBIReportExportData: Verdadero/Falso
* MaxFileSizeMb: el valor predeterminado es 1000
* ModelCleanupCycleMinutes: frecuencia de comprobación para expulsar modelos de la memoria
* ModelExpirationMinutes: tiempo hasta que el modelo expira y se expulsa, en función de la hora de último uso
* ScheduleRefreshTimeoutMinutes: cuánto tiempo puede tardar la actualización de datos para un modelo. De forma predeterminada, es de dos horas.  No hay ningún límite superior.

**Archivo de configuración rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API para desarrolladores

La API para desarrolladores (API de REST) que se incorporó en SSRS 2017 se ha ampliado para que Power BI Report Server trabaje tanto con archivos de Excel como con archivos .pbix. Un caso de uso posible es descargar archivos mediante programación desde el servidor, actualizarlos y, a continuación, volver a publicarlos. Esta es la única manera de actualizar libros de Excel con modelos de PowerPivot, por ejemplo.

Tenga en cuenta que hay una nueva API independiente para archivos de gran tamaño, que se actualizará en la versión de Power BI Report Server de Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) y el consumo de memoria de Power BI Report Server

Power BI Report Server ahora hospeda SQL Server Analysis Services (SSAS) internamente. Esto no es específico de la actualización programada. El hospedaje de SSAS puede aumentar considerablemente el consumo de memoria del servidor de informes. El archivo de configuración AS.ini está disponible en los nodos del servidor; si está familiarizado con SSAS, puede que desee actualizar la configuración, incluido el límite de cantidad máxima de memoria, el almacenamiento en caché de disco, etc. Consulte [Propiedades del servidor en Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) para más información.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Ver libros de Excel e interactuar con ellos

Excel y Power BI disponen de una cartera de herramientas que es única en el sector. Juntas, permiten a los analistas de negocios recopilar, dar forma, analizar y explorar visualmente de una forma más sencilla los datos. Además de ver informes de Power BI en el portal web, los usuarios empresariales ahora pueden hacer lo mismo con los libros de Excel en Power BI Report Server, lo que les proporciona una única ubicación para publicar y ver su contenido de Microsoft BI en modo de autoservicio.

Hemos publicado un [tutorial sobre cómo agregar Office Online Server (OOS) al entorno de la versión preliminar de Power BI Report Server](excel-oos.md). Los clientes con una cuenta de licencias por volumen pueden descargar OOS desde el centro de servicio de licencias por volumen sin costo alguno y tendrán la funcionalidad de solo lectura. Una vez configurado, los usuarios pueden ver e interactuar con libros de Excel que:

* No tengan ninguna dependencia de origen de datos externos
* Dispongan de una conexión activa a un origen de datos externo de SQL Server Analysis Services
* Tengan un modelo de datos de PowerPivot

### <a name="support-for-new-table-and-matrix-visuals"></a>Compatibilidad con los nuevos objetos visuales de tablas y matrices

Power BI Report Server ahora admite los nuevos objetos visuales tabla y matriz de Power BI. Para crear informes con estos objetos visuales, necesitará una versión actualizada de Power BI Desktop para la versión de octubre de 2017. No se puede instalar junto con la versión de junio de 2017 de Power BI Desktop. Para la versión más reciente de Power BI Desktop, en la [página de descarga de Power BI Report Server](https://powerbi.microsoft.com/report-server/), seleccione **Opciones avanzadas de descarga**.

## <a name="june-2017"></a>Junio de 2017

* El servidor de informes de Power BI ha pasado a tener carácter general (GA).

## <a name="may-2017"></a>Mayo de 2017

* Disponibilidad de la versión preliminar del servidor de informes de Power.
* Posibilidad de publicar informes de Power BI en el entorno local.
  * Compatibilidad con objetos visuales personalizados
  * Compatibilidad con **conexiones dinámicas de Analysis Services** solo con más orígenes de datos que están por venir.
  * Actualización de la aplicación Power BI Mobile para mostrar los informes de Power BI hospedados en el servidor de informes de Power BI.
* Colaboración mejorada en los informes con comentarios.

## <a name="next-steps"></a>Pasos siguientes

Consulte estas fuentes para estar al tanto de las nuevas características de Power BI Report Server.

* [Blog de Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blog del equipo de SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* El [canal de YouTube Guy in a Cube](https://aka.ms/guyinacube)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
