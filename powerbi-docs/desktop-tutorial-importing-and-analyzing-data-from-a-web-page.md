---
title: 'Tutorial: Importación y análisis de datos de una página web'
description: 'Tutorial: Importación y análisis de datos desde una página web con Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 5497c56f358470d0d24f69f0d67865dbbd7839a3
ms.sourcegitcommit: 75300b3f53f438ed7d3bd4edc93b9eb5925bf3af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2020
ms.locfileid: "77026747"
---
# <a name="tutorial-analyze-webpage-data-by-using-power-bi-desktop"></a>Tutorial: Análisis de datos de páginas web con Power BI Desktop

Como antiguo fanático del fútbol, desea crear un informe de los ganadores de Campeonato Europeo de la UEFA (Eurocopa) a lo largo de los años. Con Power BI Desktop, puede importar estos datos desde una página web en un informe y crear visualizaciones que muestren los datos. En este tutorial, aprenderá a usar Power BI Desktop para:

- Conectarse a un origen de datos web y navegar por las tablas disponibles.
- Dar forma a los datos y transformarlos en el Editor de Power Query.
- Asignar un nombre a una consulta e importarla en un informe de Power BI Desktop.
- Crear y personalizar un mapa y una visualización de gráfico circular

## <a name="connect-to-a-web-data-source"></a>Conexión a un origen de datos de web

Puede obtener los datos de los ganadores de la UEFA de la tabla Historial de la página de Wikipedia sobre el Campeonato Europeo de fútbol de la UEFA (Eurocopa), en https://en.wikipedia.org/wiki/UEFA_European_Football_Championship. 

![Tabla de resultados de Wikipedia](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

Las conexiones web solo se establecen con la autenticación básica. Los sitios web que requieren autenticación podrían no funcionar correctamente con el conector web.

Para importar los datos:

1. En la pestaña de la cinta de opciones **Inicio** de Power BI Desktop, despliegue la flecha que está junto a **Obtener datos** y luego seleccione **Web**.

   ![Cinta de opciones Obtener datos de](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 

   >[!NOTE]
   >También puede seleccionar el elemento **Obtener datos** mismo o seleccionar **Obtener datos** en el cuadro de diálogo Introducción de Power BI Desktop, seleccionar después **Web** en la sección **Todo** u **Otros** del cuadro de diálogo **Obtener datos** y, luego, seleccionar **Conectar**.

1. En el cuadro de diálogo **Desde la Web**, pegue la dirección URL `https://en.wikipedia.org/wiki/UEFA_European_Football_Championship` en el cuadro de texto **URL** y luego seleccione **Aceptar**.

    ![Obtener datos en el cuadro de diálogo](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)

   Después de conectarse a la página web de Wikipedia, el cuadro de diálogo **Navegador** muestra una lista de las tablas disponibles en la página. Puede seleccionar cualquiera de los nombres de tabla para obtener una vista previa de sus datos. La tabla **Results [edit]** contiene los datos que desea, pero no presenta exactamente la forma esperada. Podrá cambiar la forma de los datos y limpiarlos antes de cargarlos en el informe.

   ![Cuadro de diálogo Navegador](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)

   >[!NOTE]
   >En el panel **Vista previa** se muestra la tabla seleccionada más recientemente, pero todas las tablas seleccionadas se cargarán en el Editor de Power Query si selecciona **Transformar datos** o **Cargar**.

1. Seleccione la tabla **Results [edit]** en la lista **Navegador** y después seleccione **Transformar datos**.

   Se abre una vista previa de la tabla en el **Editor de Power Query**, donde puede aplicar transformaciones para limpiar los datos.

   ![Editor de Power Query](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)

## <a name="shape-data-in-power-query-editor"></a>Dar forma a los datos en el Editor de Power Query

Desea facilitar el análisis de los datos mostrando solo los años y los países ganadores. Puede usar el Editor de Power Query para realizar estos pasos necesarios para dar forma a los datos y limpiarlos.

En primer lugar, quite todas las columnas excepto dos de la tabla. Cambie el nombre de estas columnas a *Year* y *Country* más adelante en el proceso.

1. En la cuadrícula **Editor de Power Query**, seleccione las columnas. Seleccione Ctrl para seleccionar varios elementos.

1. Haga clic con el botón derecho y seleccione **Quitar otras columnas** o seleccione **Quitar columnas** > **Quitar otras columnas** en el grupo **Administrar columnas** de la pestaña de la cinta de opciones **Inicio** para eliminar todas las demás columnas de la tabla.

   ![Menú desplegable Quitar otras columnas](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png)

   o bien

   ![Cinta de opciones Quitar otras columnas](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

A continuación, quite la palabra adicional *Details* de las celdas de la primera columna.

1. Seleccione la primera columna.

1. Haga clic con el botón derecho y seleccione **Reemplazar valores** o seleccione **Reemplazar los valores** del grupo **Transformar** en la pestaña **Inicio** de la cinta de opciones. Esta opción también se encuentra en el grupo **Cualquier columna** de la pestaña **Transformar**.

   ![Menú desplegable Reemplazar los valores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) 

   o bien

   ![Cinta de opciones Reemplazar los valores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)

1. En el cuadro de diálogo **Reemplazar los valores**, escriba **Details** en el cuadro de texto **Valor que buscar**, deje el cuadro de texto **Reemplazar por** vacío y luego seleccione **Aceptar** para borrar la palabra *Details* de esta columna.

   ![Quitar una palabra de la columna](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

Algunas celdas contienen solo la palabra "Year" en lugar de valores de año. Puede filtrar la columna para que solo se muestren las filas que no contienen la palabra "Year".

1. Seleccione la flecha desplegable del filtro de la columna.

1. En el menú desplegable, desplácese hacia abajo y desactive la casilla junto a la opción **Year** y, luego, seleccione **Aceptar**.

   ![Filtrar datos](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

Como solo va a examinar la lista de campeones, puede cambiar el nombre de esta columna a **Country**. Para cambiar el nombre de la columna:

1. Haga doble clic en el encabezado de la segunda columna y manténgalo presionado.
   - O bien, haga clic en el encabezado de la columna y seleccione **Cambiar el nombre**.
   - Otra opción es seleccionar la *columna y seleccionar **Cambiar el nombre** en el grupo **Cualquier columna** de la pestaña **Transformar** de la cinta de opciones.

   ![Menú desplegable Cambiar el nombre](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) 
  
   o bien

   ![Cinta de opciones Cambiar nombre](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)

1. Escriba **Country** en el encabezad y presione **ENTRAR** para cambiar el nombre de la columna.

También puede filtrar las filas como "2020" que tengan valores null en la columna **Country**. Podría usar el menú de filtro como en el caso de los valores **Year**, o bien puede hacer lo siguiente:

1. Haga clic con el botón derecho en la celda **Country** en la fila **2020**, que tiene el valor *null*.

1. Seleccione **Filtros de texto** > **No es igual a** en el menú contextual para quitar todas las filas que contienen ese valor de celda.

   ![Filtro de texto](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)

## <a name="import-the-query-into-report-view"></a>Importación de la consulta en la vista de informe

Ahora que ya ha dado forma a los datos de la manera deseada, puede asignar el nombre "Euro Cup Winners" a su consulta e importarla en el informe.

1. En el panel **Configuración de consultas** , en el cuadro de texto **Nombre** , escriba **Campeones de la Eurocopa**.

   ![Asignación de nombre a la consulta](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

1. Seleccione **Cerrar y aplicar** > **Cerrar y aplicar** en la pestaña **Inicio** de la cinta de opciones.

   ![Cerrar y aplicar](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)

La consulta se carga en la *Vista de informe* de Power BI Desktop, donde puede verla en el panel **Campos**.

   ![Panel Campos](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)

>[!TIP]
>Puede volver siempre al Editor de Power Query para editar y refinar la consulta; para ello, haga lo siguiente:
>- Seleccione los puntos suspensivos **Más opciones** ( **...** ) junto a **Euro Cup Winners** en el panel **Campos** y seleccione **Editar consulta**.
>- Seleccione **Editar consultas** > **Editar consultas** en el grupo **Datos externos** de la pestaña **Inicio** de la cinta de opciones en la vista de informe. 

## <a name="create-a-visualization"></a>Creación de una visualización

Para crear una visualización basada en los datos:

1. Seleccione el campo **Country** en el panel **Campos** o arrástrelo al lienzo del informe. Power BI Desktop reconoce los datos como nombres de países y crea automáticamente una visualización de **mapa**.

   ![Visualización de mapa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)

1. Amplíe el mapa arrastrando los controladores de las esquinas para que todos los nombres de los países ganadores estén visibles.  

   ![Ampliar el mapa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)

1. En el mapa se muestran puntos de datos idénticos para cada país ganador del campeonato de la Eurocopa. Para que el tamaño de cada punto de datos refleje cuántas veces ha ganado el país, arrastre el campo **Year** a **Arrastrar campos de datos aquí** en **Tamaño** en la parte inferior del panel **Visualizaciones**. El campo cambia automáticamente a una medida de **Número de años** y en la visualización del mapa se muestran ahora los puntos de datos más altos para los países que ganaron más campeonatos.

   ![Arrastre el Número de años para ajustar el tamaño](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)

## <a name="customize-the-visualization"></a>Personalización de la visualización

Como puede ver, es muy fácil crear visualizaciones basadas en los datos. También es fácil personalizar las visualizaciones para presentar mejor los datos de las formas que desee.

### <a name="format-the-map"></a>Dar formato al mapa

Puede cambiar la apariencia de una visualización; para ello, selecciónela y luego seleccione el icono **Formato** (rodillo) en el panel **Visualizaciones**. Por ejemplo, los puntos de datos de "Alemania" podrían ser erróneos en su visualización, ya que Alemania Occidental ganó dos campeonatos y Alemania, uno, y en el mapa se superponen los dos puntos en lugar de separarlos o agregarlos juntos. Puede dar color diferentes a estos dos puntos para resaltar este hecho. También puede dar al mapa un título más descriptivo y atractivo.

1. Con la visualización seleccionada, seleccione el icono **Formato** y luego seleccione **Colores de datos** para expandir las opciones de color de los datos.

   ![Dar formato a los datos con colores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)

1. Cambie el estado de **Mostrar todo** a **Activado** y luego seleccione el menú desplegable junto a **Alemania Occidental** y elija el color amarillo.

   ![Cambiar el color](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)

1. Seleccione **Título** para expandir las opciones de título y, en el campo **Texto del título**, escriba **Euro Cup Winners** en lugar del título actual.

1. Cambie el **Color de fuente** a rojo, el **Tamaño del texto** a **12** y la **Familia de fuentes** a **Segoe (Negrita)** .

   ![Dar formato a los datos con colores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)

La visualización de mapa ahora tiene el siguiente aspecto:

![Visualización de mapa con formato](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)

### <a name="change-the-visualization-type"></a>Cambiar el tipo de visualización

Puede cambiar el tipo de una visualización si la selecciona y, a continuación, selecciona un icono diferente en la parte superior del panel **Visualizaciones**. Por ejemplo, en la visualización de mapa faltan los datos de la Unión Soviética y de la República Checa, porque esos países ya no existen en el mapa del mundo. Otro tipo de visualización, como un gráfico de rectángulos o un gráfico circular, puede ser más precisa, porque muestra todos los valores.

Para cambiar el mapa a un gráfico circular, selecciónelo y luego seleccione el icono de **Gráfico circular** en el panel **Visualizaciones**.

![Cambie la visualización a un gráfico circular](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- Puede usar las opciones de formato de **Colores de datos** para resaltar "Alemania" y "Alemania Occidental" en el mismo color. 
>- Para agrupar los países con más campeonatos ganados en el gráfico circular, seleccione los puntos suspensivos ( **…** ) en la parte superior derecha de la visualización y luego seleccione **Ordenar por número de año**.

Power BI Desktop ofrece una experiencia perfectamente integrada que va desde la obtención de datos procedentes de una amplia gama de orígenes hasta su manipulación para adaptarlos a cualquier necesidad de análisis y su visualización de forma enriquecida e interactiva. Cuando el informe esté listo, podrá [cargarlo en Power BI](desktop-upload-desktop-files.md) y crear paneles basados en él, paneles que podrá compartir con otros usuarios de Power BI.

## <a name="see-also"></a>Vea también

* [Lea otros tutoriales de Power BI Desktop](/power-bi/guided-learning/)
* [Vea vídeos de Power BI Desktop](desktop-videos.md)
* [Visite el foro de Power BI](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Lea el blog de Power BI](https://go.microsoft.com/fwlink/?LinkID=519327)

