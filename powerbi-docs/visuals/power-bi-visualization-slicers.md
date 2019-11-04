---
title: 'Tutorial: Segmentaciones en Power BI'
description: Segmentaciones de datos en Power BI
author: v-thepet
manager: kvivek
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 10/22/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d400e2013d8f2cb8dda627cda790191fce52503b
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775885"
---
# <a name="slicers-in-power-bi"></a>Segmentaciones de datos en Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Quiere que los lectores del informe puedan buscar métricas de ventas generales, pero también resaltar el rendimiento de los administradores de distrito y los diferentes plazos de tiempo. Podría crear informes independientes o gráficos comparativos, o bien utilizar segmentaciones. Una segmentación es una forma alternativa de filtro que limita la parte del conjunto de datos que se muestra en otras visualizaciones de un informe. 

En este tutorial se usa el [ejemplo de análisis de minoristas](../sample-retail-analysis.md) gratuito para guiarlo a la hora de crear segmentaciones de plazos de tiempo, así como darles formato y crear listas de ellas. Diviértase descubriendo maneras de dar formato y usar segmentaciones. 

![segmentación](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Cuándo usar una segmentación
Las segmentaciones son una excelente opción si desea:

* Mostrar filtros importantes o que se usan con comúnmente en el lienzo de informes para facilitar el acceso.
* Facilitar la visualización del estado filtrado actual sin tener que abrir una lista desplegable. 
* Filtrar por columnas innecesarias y ocultas en las tablas de datos.
* Crear informes más enfocados colocando las segmentaciones junto a objetos visuales importantes.

Las segmentaciones de Power BI tienen las siguientes limitaciones:

- Las segmentaciones no admiten campos de entrada.
- No se admite la exploración en profundidad para las segmentaciones.


## <a name="create-slicers"></a>Creación de segmentaciones

**Creación de una nueva segmentación con el fin de filtrar los datos por administrador de distrito**

En este tutorial se usa el [archivo PBIX del Ejemplo de análisis de minoristas](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de minoristas**.

1. Abra el **archivo PBIX del Ejemplo de análisis de minoristas** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.

2. En la página Información general, sin nada seleccionado en el lienzo, elija el icono **Segmentación** ![icono Segmentación](media/power-bi-visualization-slicers/slicer-icon.png) en el panel **Visualizaciones** para crear una nueva segmentación. 
3. Con la nueva segmentación seleccionada, en el panel Campos, seleccione **Distrito** > **Administrador de distrito** para completar la segmentación. La nueva segmentación es una lista con cuadros de selección antes de los nombres. 
    
    ![nueva segmentación](media/power-bi-visualization-slicers/power-bi-new-slicer.png)
    
4. Cambie el tamaño de la segmentación y otros elementos, y arrástrelos en el lienzo para dejar espacio a la segmentación. Tenga en cuenta que los elementos de segmentación se recortan si elige un tamaño de segmentación demasiado pequeño. 
5. Seleccione los nombres en la segmentación y observe el efecto que tiene en las otras visualizaciones de la página. Seleccione los nombres de nuevo para anular la selección y mantenga presionada la tecla **Ctrl** para elegir más de un nombre. Seleccionar todos los nombres es lo mismo que no elegir ninguno. 

6. Como alternativa, seleccione el icono de rodillo de pintura para dar formato a la segmentación. Son muchas las opciones disponibles, así que no podemos explicarlas aquí todas. Experimente y cree una segmentación que le resulte adecuada. En los ejemplos siguientes, la primera segmentación utiliza una orientación horizontal y fondos en color para los elementos. La segunda segmentación se ha mantenido vertical y esta vez se aplica color al texto para darle un aspecto más estándar.

   ![nueva segmentación](media/power-bi-visualization-slicers/power-bi-filter-examples.png)
>[!TIP]
>De forma predeterminada, los elementos de la segmentación de lista se ordenan de forma ascendente. Para ordenar en orden descendente, haga clic en el botón de puntos suspensivos ( **...** ), situado en la esquina superior derecha de la segmentación, y elija **Orden descendente**.

**Para crear una nueva segmentación con el fin de filtrar datos por intervalo de fechas**

1. Sin ningún elemento seleccionado en el lienzo, despliegue **Tienda** en el panel Campos y arrastre **OpenDate** al cuadro **Valores** del panel Visualizaciones para crear una visualización.
2. Con la nueva visualización elegida, seleccione el icono de **Segmentación** en el panel Visualizaciones para convertir la nueva visualización en una segmentación. Esta segmentación es un control deslizante con el intervalo de fechas rellenado.
    
    ![nueva segmentación de intervalo](media/power-bi-visualization-slicers/power-bi-date-slicer.png)

    
4. Cambie el tamaño de la segmentación y otros elementos, y arrástrelos en el lienzo para dejar espacio a la segmentación. Tenga en cuenta que con el tamaño de segmentación se cambia el tamaño del control deslizante, pero desaparece y las fechas se recortan si elige un tamaño demasiado pequeño para la segmentación. 
4. Seleccione intervalos de fechas diferentes con el control deslizante, o bien un campo de fecha para escribir un valor o abrir una ventana emergente con un calendario para hacer una selección más precisa. Observe los efectos que tiene en las demás visualizaciones de la página.
    
    >[!NOTE]
    >Los tipos de datos numéricos y de fecha/hora generan las segmentaciones de control deslizante de intervalo de forma predeterminada. A partir de la actualización de febrero de 2018 de Power BI, las segmentaciones de intervalo de tipo de datos de número entero ahora se ajustan a los valores de número entero en lugar de mostrar las posiciones decimales. 


5. Para cambiar el tipo de segmentación, con la segmentación seleccionada, mantenga el mouse sobre el área superior derecha de la segmentación, haga clic en el acento circunflejo que aparece y elija una de las otras opciones, como **Lista** o **Antes**. Observe cómo cambian las opciones de selección y la apariencia de las segmentaciones. 
 
    ![nueva segmentación de intervalo](media/power-bi-visualization-slicers/power-bi-between-slicer.png)


Consulte [Uso de la segmentación de intervalos numéricos en Power BI Desktop](../desktop-slicer-numeric-range.md) para obtener más información sobre cómo crear y usar las segmentaciones de intervalos numérico y de fecha.
   > [!NOTE]
   > En este vídeo se usa una versión anterior de Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 

## <a name="control-which-page-visuals-are-affected-by-slicers"></a>Control de qué objetos visuales de página se ven afectados por las segmentaciones
De forma predeterminada, las segmentaciones de las páginas del informe afectan a todas las visualizaciones de la página. Cuando elija los valores en los controles deslizante de lista y fecha que acaba de crear, observe cómo afecta a las otras visualizaciones. Los datos filtrados están una intersección de los valores seleccionados en las dos segmentaciones. 

Use **Interacciones de objetos visuales** para impedir que algunas visualizaciones de página se vean afectadas. En la página **Información general**, el gráfico "Varianza total de ventas por mes fiscal y administrador del distrito" muestra datos comparativos generales de los administradores del distrito por mes, que quiere que sean visibles en todo momento. Puede usar **Interacciones de objetos visuales** para que las selecciones de segmentación sigan filtrando este gráfico. 

1. Con la segmentación del administrador de distrito seleccionada en la página **Ventas mensuales de distrito**:
    - En Power BI Desktop, haga clic en el menú **Formato** en **Visual Tools** y seleccione **Editar interacciones**.
   
   Los controles de filtro ![controles de filtro](media/power-bi-visualization-slicers/filter-controls.png) aparecen encima de los demás objetos visuales de la página. Inicialmente, todos los iconos de **Filtro** están seleccionados.
   
2. Seleccione el icono de **Ninguno** encima del gráfico **Varianza total de ventas por mes fiscal y administrador del distrito** para hacer que la segmentación deje de filtrarla. 
3. Seleccione la segmentación **Mes** y, de nuevo, elija el icono de **Ninguno** encima del gráfico **Varianza total de ventas por mes fiscal y administrador del distrito** para hacer que la segmentación deje de filtrarla. Ahora, cuando seleccione los nombres e intervalos de fechas en las segmentaciones, el gráfico Varianza total de ventas por mes fiscal y administrador del distrito no se modifica. 

Vea [Interacciones de visualización en un informe de Power BI](../service-reports-visual-interactions.md) para obtener más información sobre cómo editar las interacciones.

## <a name="sync-and-use-slicers-on-other-pages"></a>Sincronización y uso de las segmentaciones en otras páginas
A partir de la actualización de febrero de 2018 de Power BI se puede sincronizar una segmentación y usarla en una o todas las páginas de un informe. 

En el informe actual, la página **Ventas mensuales de distrito** tiene también una segmentación **Administrador de distrito**, pero ¿qué ocurriría si quisiéramos también que esa segmentación estuviera en la página de **información general**? La página **Nuevas tiendas** tiene también una segmentación, pero solo brinda información sobre el **nombre de la tienda**. Con el panel **Sincronizar segmentaciones** podemos sincronizar la segmentación **Administrador de distrito** con estas páginas, para que las selecciones de segmentación de cualquier página afecten a las visualizaciones de las tres páginas.

1. En el menú **Ver**, seleccione **Sincronizar segmentaciones** en Power BI Desktop.

    ![Segmentaciones de sincronización](media/power-bi-visualization-slicers/power-bi-slicer-view-sync.png)

1.  Aparece el panel **Sincronizar segmentaciones** entre los paneles **Filtros** y **Visualizaciones**.  

    ![Segmentaciones de sincronización](media/power-bi-visualization-slicers/power-bi-slicer-sync-pane.png)

1. En la página **Ventas mensuales de distrito**, seleccione la segmentación **Administrador del distrito**. 
    
    ![Segmentaciones de sincronización](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
3. En la columna **Sincronización**, seleccione las páginas **Nuevas tiendas** e **Información general** para sincronizar la segmentación **Ventas mensuales de distrito** con estas páginas. 
    
3. En la columna **Visible**, seleccione las páginas **Nuevas tiendas** e **Información general**. El panel **Sincronizar segmentaciones** debería tener ahora un aspecto similar a la imagen siguiente:

    ![Segmentaciones de sincronización](media/power-bi-visualization-slicers/power-bi-sync-slicer-finished.png)

1. Observe los efectos de sincronizar la segmentación y hacerla visible en las otras páginas. En la página **Ventas mensuales de distrito**, el control deslizante **Administrador de distrito** muestra ahora las mismas selecciones que en la página **Información general**. En la página **Nuevas tiendas**, las selecciones de la segmentación **Administrador de distrito** afecta a las selecciones que están disponibles en la segmentación **Nombre de la tienda**. 
    
    >[!TIP]
    >Aunque la segmentación aparece inicialmente en las páginas sincronizadas con el mismo tamaño y posición que en la página original, puede mover, cambiar el tamaño y dar formato de forma independiente a segmentaciones sincronizadas en las distintas páginas. 

>[!NOTE]
>Si sincroniza una segmentación con una página, pero no la hace visible en la página, las selecciones de segmentación realizadas en las demás páginas seguirán filtrando los datos en la página.
 
## <a name="format-slicers"></a>Segmentaciones de formato
Existen diferentes opciones de formato según el tipo de segmentación. Con la orientación **Horizontal**, el diseño **dinámico** y la posibilidad de colorear **elementos**, puede generar botones o iconos en lugar de elementos de lista estándar, y hacer que los elementos de segmentación cambien de tamaño para ajustarse a diferentes diseños y tamaños de pantalla.  

1. Con la segmentación **Administrador de distrito** seleccionada, en el panel **Visualizaciones**, seleccione el icono **Formato** ![icono Formato](media/power-bi-visualization-slicers/power-bi-paintroller.png) para mostrar los controles de formato. 
    
    ![Formato](media/power-bi-visualization-slicers/3-format.png)
    
2. Seleccione las flechas desplegables situadas junto a cada categoría para mostrar y editar las opciones. 

### <a name="general-options"></a>Opciones generales
1. Seleccione el color rojo en **Color del esquema** y cambie **Grosor del esquema** a "2". Así se establecerá el color y el grosor de los esquemas o subrayados de los encabezados y elementos, en el caso de que estén habilitados. 
2. En **Orientación**, **Vertical** es el valor predeterminado. Seleccione **Horizontal** para producir una segmentación con botones o iconos organizados horizontalmente, y flechas de desplazamiento para tener acceso a elementos que no caben en la segmentación.
    
    ![Horizontal](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Active el diseño **dinámico** para cambiar el tamaño y la disposición de los elementos de segmentación según el tamaño de la segmentación y la pantalla. Para las segmentaciones de lista, el diseño dinámico solo está disponible en orientación horizontal y evita que los elementos queden recortados en pantallas pequeñas. Para las segmentaciones de control deslizante de intervalo, el diseño dinámico cambia el estilo del control deslizante y proporciona más flexibilidad para cambiar de tamaño. Ambos tipos de segmentaciones se convierten en iconos de filtro en tamaños muy pequeños. 
    
    ![Capacidad de respuesta](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >Los cambios del diseño de capacidad de respuesta pueden invalidar un determinado formato de encabezados y elementos que establezca. 
    
4. Establezca la posición y el tamaño de la segmentación con una precisión numérica en **Posición X**, **Posición Y**, **Ancho** y **Alto**, o bien mueva y cambie el tamaño de la segmentación directamente en el lienzo. Experimente con diferentes tamaños de elementos y organizaciones, y observe cómo el diseño dinámico cambia en consecuencia.  

    ![Botones horizontales](media/power-bi-visualization-slicers/6-buttons.png)

Vea [Crear una segmentación con capacidad de respuesta que se puede cambiar de tamaño en Power BI](../power-bi-slicer-filter-responsive.md) para obtener más información sobre la orientación horizontal y el diseño dinámico.

### <a name="selection-controls-options-list-slicers-only"></a>Opciones de controles de selección (solo segmentaciones de lista)
1. La opción **Mostrar Seleccionar todo** está **desactivada** de forma predeterminada. **Actívela** para agregar un elemento **Seleccionar todo** a la segmentación que seleccione todos los elementos o anule su selección cuando esté activa la opción. Cuando se seleccionan todos los elementos, al hacer clic o tocar en uno se anula la selección, con lo que se permite un filtro de tipo "No es…". 
    
    ![Seleccionar todo](media/power-bi-visualization-slicers/7-select-all.png)
    
2. La opción **Selección única** está **activada** de forma predeterminada. Al hacer clic o tocar en un elemento se selecciona y, si se mantiene presionada la tecla **Ctrl** mientras se hace clic o se toca, se seleccionan varios elementos. **Desactive** la opción **Selección única** para poder seleccionar varios elementos sin mantener presionada la tecla **Ctrl**. Si vuelve a hacer clic o tocar en un elemento, se anulará su selección. 

### <a name="title-options"></a>Opciones de título
El **título** está **activado** de forma predeterminada y muestra el nombre del campo de datos en la parte superior de la segmentación. 
1. Dé formato al texto de título para que el **color de fuente** sea rojo, el **tamaño del texto** sea de 14 puntos, la **alineación** esté centrada y la **familia de fuentes** sea Arial Black. 


### <a name="item-options-list-slicers-only"></a>Opciones de elemento (solo segmentaciones de lista)
1. Dé formato al texto y al fondo de los elementos para que el **color de fuente** sea negro, el **fondo** sea rojo claro, el **tamaño del texto** sea de 10 puntos y la **familia de fuentes** sea Arial. 
2. En **Esquema**, elija **Marco** para dibujar un borde alrededor de cada elemento con el tamaño y el color que establezca en **Opciones generales**. 
    
    ![Con formato](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Con la **orientación horizontal**, los elementos no seleccionados muestran los colores de texto y fondo elegidos, mientras que los elementos seleccionados usan los colores predeterminados del sistema, que normalmente son el negro para los fondos con el texto de color blanco.
    >- Con la **orientación vertical**, los elementos siempre muestran los colores establecidos y los cuadros de selección siempre son de color negro cuando se seleccionan. 

### <a name="datenumeric-inputs-and-slider-options-range-slider-slicers-only"></a>Entradas numéricas y de fecha, y opciones de control deslizante (solo segmentaciones de controles deslizantes de intervalo)
- Las entradas numéricas y de fecha son las mismas que las opciones de **Elemento** de las segmentaciones de lista, pero no hay ningún **esquema** ni subrayado.
- Las opciones de control deslizante permiten establecer el color del control deslizante de intervalo o **desactivar** el control deslizante para dejar solamente las entradas numéricas.

### <a name="other-formatting-options"></a>Otras opciones de formato
Las demás opciones de formato están desactivadas de forma predeterminada. Si se **activan**: 
- **Fondo:** agrega un color de fondo a la segmentación general y establece su transparencia.
- **Bloquear relación de aspecto:** conserva la forma de la segmentación si se cambia su tamaño.
- **Borde:** agrega un borde de 1 píxel alrededor de la segmentación y establece su color. (este borde de la segmentación es independiente y no se ve afectado por la configuración general de Esquema). 

## <a name="next-steps"></a>Pasos siguientes
[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Tablas en Power BI](power-bi-visualization-tables.md)

