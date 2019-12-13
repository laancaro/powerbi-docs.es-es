---
title: Mapas coropléticos en Power BI
description: Documentación sobre cómo crear mapas coropléticos en Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/05/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e7fa98be039093015e1b19ba8bf20f1368658a43
ms.sourcegitcommit: 212fb4a46af3e434a230331f18456c6a49a408fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907856"
---
# <a name="filled-maps-choropleth-in-power-bi"></a>Mapas coropléticos en Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Los mapas coropléticos usan sombreado, tintes o patrones para mostrar las diferencias de un valor en proporción en una ubicación geográfica o región.  Muestre rápidamente estas diferencias relativas con sombreados que va del claro (valores menos frecuentes o inferiores) a oscuro (más frecuentes o superiores).    

![Mapa de EE. UU.](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>Qué se envía a Bing
Power BI se integra con Bing para proporcionar coordenadas de mapas predeterminadas (un proceso denominado geocodificación). Cuando se crea una visualización de mapa en el servicio Power BI o en Power BI Desktop, se envían a Bing los datos en los cubos **Ubicación**, **Latitud** y **Longitud** (que se usan para crear la visualización).

Puede que usted o su administrador tengan que actualizar el firewall para permitir el acceso a las direcciones URL que utiliza Bing para geocodificación.  Estas direcciones URL son:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Para más información sobre los datos que se envían a Bing, así como sugerencias para lograr mejores resultados con la geocodificación, consulte [Sugerencias y trucos para visualizaciones de mapa](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Cuándo usar un mapa coroplético
Los mapas coropléticos son una excelente opción:

* Para mostrar información cuantitativa en un mapa.
* Para mostrar las relaciones y patrones espaciales.
* Cuando los datos están normalizados.
* Cuando se trabaja con datos socioeconómicos.
* Cuando las regiones definidas son importantes.
* Para obtener una visión general de la distribución en las ubicaciones geográficas.

### <a name="prerequisites"></a>Requisitos previos
En este tutorial se usa el [archivo .PBIX del ejemplo de ventas y marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).
1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**
   
2. Busque su copia del **archivo .PBIX del ejemplo de ventas y marketing**.

1. Abra el **archivo PBIX de Ventas y marketing** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.


## <a name="create-a-basic-filled-map"></a>Crear un mapa coroplético básico
En este video, Kim crea un mapa básico y lo convierte en un mapa coroplético.
   > [!NOTE]
   > En este vídeo se usa una versión anterior de Power BI Desktop.
   > 
   > 

[VÍDEO https://www.youtube.com/embed/ajTPGNpthcg ]

### <a name="create-a-filled-map"></a>Creación de un mapa coroplético
1. En el panel Campos, seleccione el campo **Zona geográfica** \> **Estado**.    

   ![Marca de verificación amarilla junto a Estado](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
2. [Convierta el gráfico](power-bi-report-change-visualization-type.md) en un mapa coroplético. Observe que **Estado** está ahora en el área **Ubicación**. Bing Maps usa el campo del área **Ubicación** para crear el mapa.  La ubicación puede ser una gran variedad de ubicaciones válidas: países, estados, provincias, ciudades, códigos postales, etc. Bing Maps proporciona mapas coropléticos para ubicaciones en todo el mundo. Sin una entrada válida en el área Ubicación, Power BI no puede crear el mapa coroplético.  

   ![Plantillas con el icono de mapa coroplético resaltado](media/power-bi-visualization-filled-maps-choropleths/img003.png)
3. Filtre el mapa para mostrar solo el territorio continental de Estados Unidos.

   a.  En la parte izquierda del panel Visualizaciones, busque el panel **Filtros**. Expándalo si está minimizado.

   b.  Mantenga el puntero sobre **Estado** y seleccione el botón de contenido adicional.  
   ![Filtros de nivel de objeto visual que muestran Estado (Todos)](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Coloque una marca de verificación junto a **Todos** y quite la marca de verificación junto a **AK**.

   ![Lista desplegable de estados con (Todos) y AK sin seleccionar](media/power-bi-visualization-filled-maps-choropleths/img005.png)
4. Seleccione el icono del rodillo de pintura para abrir el panel de formato y elija **Colores de datos**.

    ![Panel de formato en el que se muestra la opción Colores de datos](media/power-bi-visualization-filled-maps-choropleths/power-bi-colors-data.png)

5. Seleccione los tres puntos verticales y elija **Formato condicional**.

    ![Botón de formato condicional de Colores de datos](media/power-bi-visualization-filled-maps-choropleths/power-bi-conditional.png)

6. Utilice la pantalla **Color predeterminado: Colores de datos** para determinar los tonos de su mapa coroplético. Las opciones disponibles incluyen en qué campo se basarán los tonos y cómo se aplicarán. En este ejemplo se usa el campo **SalesFact** > **Sentiment**; se establece el valor inferior de opinión como naranja, mientras que el superior es azul. Los valores que se encuentren entre el valor superior y el mínimo se representarán con tonalidades de naranja y azul. En la ilustración de la parte inferior de la pantalla se muestra la gama de colores que se usará. 

    ![Panel de color predeterminado con una opinión seleccionada](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-field.png)

7. El mapa coroplético se sombrea en color verde y rojo; el rojo representa los números de opinión más bajos y el verde la opinión más alta y más positiva.  Para mostrar detalles adicionales, arrastre un campo al área de información sobre herramientas.  Aquí hemos agregado **SalesFact** > **Hueco de opinión**. Al resaltar el estado de Idaho (ID), se muestra que el hueco de opinión es bajo (6).
   ![Mapa coroplético en el que se muestra información sobre herramientas de Idaho](media/power-bi-visualization-filled-maps-choropleths/power-bi-idaho-filled-map.png)

10. [Guarde el informe](../service-report-save.md).

Power BI le proporciona mucho control sobre la apariencia del mapa coroplético. Practique con estos controles de color de datos hasta que obtenga el aspecto que quiera. 

## <a name="highlighting-and-cross-filtering"></a>Resaltado y filtrado cruzado
Para más información acerca de cómo usar el panel Filtros, consulte [Agregar un filtro a un informe](../power-bi-report-add-filter.md).

Al resaltar una ubicación en un mapa coroplético, se realiza un filtrado cruzado de las demás visualizaciones en la página del informe, y viceversa.

1. Para poder continuar, primero debe guardar este informe seleccionando **Archivo > Guardar**. 

2. Presione CTRL-C para copiar el mapa coroplético.

3. En la parte inferior del lienzo del informe, haga clic en la pestaña **Opiniones** para abrir la página del informe Opinión.

    ![Pestaña Opiniones seleccionada](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Mueva y cambie el tamaño de las visualizaciones de la página para hacer espacio, y después presione CTRL-V para pegar el mapa coroplético del informe anterior. (Vea las siguientes imágenes)

   ![Mapa coroplético agregado a la página Opinión](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. En el mapa coroplético, seleccione un estado.  Esto realiza un resaltado y un filtro cruzados de las demás visualizaciones de la página. Al seleccionar **Texas**, por ejemplo, se aplica un filtro cruzado a las tarjetas y un resaltado cruzado al gráfico de barras. A partir de este, sabemos que la opinión es 75 y que Texas está en el distrito central n.º 23.   
   ![Texas seleccionado](media/power-bi-visualization-filled-maps-choropleths/power-bi-filter.png)
2. Seleccione un punto de datos en el gráfico de líneas VanArsdel - Opinión por mes. Al hacerlo, se filtra el mapa coroplético para mostrar los datos de opinión de VanArsdel y no de la competencia.  
   ![Nuevo sombreado](media/power-bi-visualization-filled-maps-choropleths/power-bi-vanarsdel.png)

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
Los datos de mapas pueden ser ambiguos.  Por ejemplo, hay un París, Francia, pero también hay un París, Texas. Los datos geográficos probablemente se almacenan en columnas diferentes: una columna para los nombres de ciudades, una columna para los nombres de estado o provincia, etc., por lo que Bing no podrá decir qué Paris es cual. Si el conjunto de datos ya contiene datos de latitud y longitud, Power BI tiene campos especiales para ayudar a que los datos de mapas no sean ambiguos. Simplemente arrastre el campo que contiene los datos de latitud al área Visualizaciones \> Latitud.  Y haga lo mismo para los datos de longitud.    

![Paneles Visualizaciones y Filtros](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Si tiene permisos para editar el conjunto de datos en Power BI Desktop, vea este vídeo para saber cómo abordar la ambigüedad de los mapas.

[VÍDEO https://www.youtube.com/embed/Co2z9b-s_yM ]

Si no tiene acceso a los datos de latitud y longitud pero tiene acceso de edición al conjunto de datos, [siga estas instrucciones para actualizar el conjunto de datos](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Para más ayuda con las visualizaciones de mapa, consulte [Sugerencias y trucos para visualizaciones de mapa](../power-bi-map-tips-and-tricks.md).

## <a name="next-steps"></a>Pasos siguientes

[Mapa de formas](desktop-shape-map.md)

[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)