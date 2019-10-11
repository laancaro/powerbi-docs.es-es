---
title: Creación de mapas de ArcGIS de ESRI en Power BI
description: 'Creación de mapas de ArcGIS de ESRI en Power BI '
author: mihart
manager: kvivek
ms.reviewer: lukaszp
featuredvideoid: EKVvOZmxg9s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 87a8333c89f2682640649e757984c6b02e10c3a8
ms.sourcegitcommit: 0687908938e4c3b68401fd511ec1c28fb54ddeb3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71691282"
---
# <a name="arcgis-maps-in-power-bi-desktop-by-esri"></a>Mapas de ArcGIS de Esri en Power BI Desktop

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Este tutorial se ha escrito desde el punto de vista de la persona que está creando un mapa de ArcGIS. Si un creador comparte un mapa de ArcGIS con un compañero, este podrá ver e interactuar con el mapa pero no guardar los cambios. Para más información acerca de cómo ver un mapa de ArcGIS, consulte [Interactuación con mapas de ArcGIS](power-bi-visualizations-arcgis.md).

Con la combinación de ArcGIS Maps y Power BI, los mapas no se limitan a ser una representación de puntos, sino que alcanzan un nivel completamente nuevo. Elija entre mapas base, tipos de ubicación, temas, estilos de símbolos y capas de referencia para crear magníficas visualizaciones informativas de mapas. La combinación de capas de datos relevantes en un mapa con el análisis espacial transmite una comprensión más profunda de los datos en la visualización.

 Aunque no puede crear mapas de ArcGIS en dispositivos móviles, puede verlos e interactuar con ellos. Consulte [Interactuación con mapas de ArcGIS](power-bi-visualizations-arcgis.md).

> [!TIP]
> GIS son las siglas en inglés para sistemas de información geográfica.


En el ejemplo siguiente, se usa un lienzo de color gris oscuro para mostrar las ventas regionales como mapa térmico contra una capa demográfica de la mediana de renta disponible en 2016. Como verá más adelante, ArcGIS Maps ofrece una funcionalidad de creación de mapas mejorada prácticamente ilimitada, datos demográficos y visualizaciones de mapas aún más atractivas, para que pueda contar mejor su historia.

![Imagen de introducción de ArcGIS](media/power-bi-visualization-arcgis/power-bi-intro-arcgis.png)

> [!TIP]
> Visite la [página de Esri en Power BI](https://www.esri.com/powerbi) para ver numerosos ejemplos y leer recomendaciones. Y después consulte la [página de introducción a ArcGIS Maps para Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) de Esri.

## <a name="user-consent"></a>Consentimiento del usuario
Esri (www.esri.com) proporciona ArcGIS Maps for Power BI. Su uso de ArcGIS Maps para Power BI está sujeto a los términos y a la directiva de privacidad de Esri. Los usuarios de Power BI que quieran usar objetos visuales de ArcGIS Maps para Power BI tienen que aceptar el cuadro de diálogo de consentimiento.

**Recursos**

[Términos](https://go.microsoft.com/fwlink/?LinkID=826322)

[Directiva de privacidad](https://go.microsoft.com/fwlink/?LinkID=826323)

[Página del producto ArcGIS Maps para Power BI](https://www.esri.com/powerbi)

<br/>


### <a name="enable-the-arcgis-map-in-power-bi-desktop-apppowerbicom"></a>Habilitación de mapas de ArcGIS ***en Power BI Desktop (app.powerbi.com)***
En este tutorial se usa el [archivo .PBIX del Ejemplo de análisis de minoristas](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix
). Para habilitar **ArcGIS Maps para Power BI**:

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** \> **Abrir**.
   
2. Busque el **archivo PBIX del Ejemplo de análisis de minoristas** guardado en la máquina local.

1. Abra **Ejemplo de análisis de minoristas**  en la vista de informe ![Captura de pantalla del icono de vista de informe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.

   
3. Seleccione el icono de ArcGIS Maps for Power BI en el panel Visualizaciones.
   
    ![Panel de visualización de mapas de ArcGIS](media/power-bi-visualization-arcgis/power-bi-viz-pane.png)
4. Power BI agrega una plantilla de mapa de ArcGIS vacía al lienzo del informe.
   
   ![Marcador de posición de visualización de ArcGIS](media/power-bi-visualization-arcgis/power-bi-esri-placeholder2new.png)

<br/>

## <a name="create-an-arcgis-map-visual"></a>Creación de un objeto visual de mapa de ArcGIS
Observe cómo se crean distintas visualizaciones de mapas de ArcGIS y, después, siga los pasos que se indican a continuación para probar a hacerlo por su cuenta con el [archivo .PBIX del Ejemplo de análisis de minoristas](../sample-datasets.md).
   > [!NOTE]
   > En este vídeo se usa una versión anterior de Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/EKVvOZmxg9s" frameborder="0" allowfullscreen></iframe>

1. En el panel **Campos**, arrastre un campo de datos a los depósitos **Location** (Ubicación) o **Latitude** (Latitud) y/o **Longitude** (Longitud). En este ejemplo, usamos **Store > City** (Tienda > Ciudad).
   
   > [!NOTE]
   > ArcGIS para Power BI detectará de forma automática si los campos que ha seleccionado se ven mejor como una forma o un punto en un mapa. Puede ajustar el valor predeterminado en la configuración (véalo a continuación).
   > 
   > 
   
    ![Panel Campos de ArcGIS](media/power-bi-visualization-arcgis/power-bi-fields-pane3new.png)

3. En el panel **Campos**, arrastre una medida al depósito **Tamaño** para ajustar cómo se muestran los datos. En este ejemplo, usamos **Sales > Last Year Sales** (Ventas > Ventas del último año).
   
    ![Visualización de mapa de puntos de Esri](media/power-bi-visualization-arcgis/power-bi-esri-point-map-size2new.png)

## <a name="settings-and-formatting-for-arcgis-maps"></a>Configuración y formato de mapas de ArcGIS
Para acceder a las características de formato de **ArcGIS Maps para Power BI**:

1. Para acceder a más características, seleccione el botón de puntos suspensivos en la esquina superior derecha de la visualización y haga clic en **Editar**.
   
   ![Panel de edición de ArcGIS](media/power-bi-visualization-arcgis/power-bi-edit2.png)
   
   Las características disponibles se muestran en la parte superior de la visualización. Al seleccionar cada característica, se abre un panel de tareas que proporciona opciones detalladas.<br/>
   
   ![Panel de características de Esri](media/power-bi-visualization-arcgis/power-bi-esri-features-new.png)
   
   > [!NOTE]
   > Para obtener más información sobre las características y la configuración, consulte **Documentación detallada** a continuación.
   > 
   > 


<br/>

## <a name="detailed-documentation"></a>Documentación detallada
**Esri** ofrece [documentación exhaustiva](https://go.microsoft.com/fwlink/?LinkID=828772) sobre el conjunto de características de **ArcGIS Maps para Power BI**.

## <a name="features-overview"></a>Información general de las características
### <a name="base-maps"></a>Mapas base
Se proporcionan cuatro mapas base: Dark Gray Canvas, Light Gray Canvas, OpenStreetMap y Streets.  Streets es el mapa base estándar de ArcGIS.

Para aplicar un mapa base, selecciónelo en el panel de tareas.

![Objeto visual de mapas base Esri](media/power-bi-visualization-arcgis/power-bi-esri-base-maps-new.png)

### <a name="location-type"></a>Tipo de ubicación
ArcGIS Maps para Power BI detecta de forma automática la mejor manera de mostrar datos en el mapa. Se selecciona entre Points o Boundaries. Las opciones del tipo de ubicación le permiten ajustar estas selecciones.

![Ejemplo de tipos de ubicación Esri](media/power-bi-visualization-arcgis/power-bi-esri-location-types-new.png)

**Boundaries** solo funcionará si los datos contienen valores geográficos estándar. Esri determina de forma automática la forma que se va a mostrar en el mapa. Los valores geográficos estándar incluyen, entre otros, países, provincias y códigos postales. En cambio, al igual que con la geocodificación, Power BI puede no detectar que el campo debe ser un límite de manera predeterminada, o puede que no tenga un límite para los datos.  

### <a name="map-theme"></a>Tema del mapa
Se proporcionan cuatro temas de mapa. Los temas Location only (Solo ubicación) y Size (Tamaño) se eligen de forma automática según los campos que se enlacen a la ubicación y se agregan al depósito **Size** en el panel Campos de Power BI. Actualmente estamos usando **Tamaño**, por lo que vamos a cambiar a **Mapa térmico**. Simplemente recuerde deshabilitar **Mapa térmico** antes de pasar al paso siguiente.  

![Ejemplo de tema de mapa Esri](media/power-bi-visualization-arcgis/power-bi-esri-map-theme-new.png)

<table>
<tr><th>Tema</th><th>Descripción</th>
<tr>
<td>Location Only</td>
<td>Traza puntos de datos o límites coropléticos según la configuración del tipo de ubicación.</td>
</tr>
<tr>
<td>Heat Map</td>
<td>Traza un trazado de intensidad de los datos en el mapa.</td>
</tr>
<tr>
<td>Tamaño</td>
<td>Traza puntos de datos en el mapa según el tamaño y en función del valor del depósito de tamaño en el panel de campos.</td>
</tr>
<tr>
<td>Clustering</td>
<td>Traza el recuento de puntos de datos en regiones en el mapa. </td>
</tr>
</table>


### <a name="symbol-style"></a>Estilo de los símbolos
Los estilos de los símbolos le permiten ajustar con precisión cómo se presentan los datos en el mapa. Los estilos de los símbolos dependen del contexto según el tipo de ubicación seleccionado y el tema del mapa. En el ejemplo siguiente se muestra el tipo de mapa establecido en **Tamaño** y varios ajustes de transparencia, estilo y tamaño. 

![Ejemplo de estilo de los símbolos Esri](media/power-bi-visualization-arcgis/power-bi-esri-symbol-style-new.png)

### <a name="pins"></a>Marcas
Llame la atención sobre puntos en el mapa mediante las marcas.  

1. Seleccione la pestaña **Pins** (Marcas).
2. Escriba palabras clave (como direcciones, lugares y puntos de interés) en el cuadro de búsqueda y seleccione en la lista desplegable. Aparece un símbolo en el mapa, que se amplía automáticamente a la ubicación. Los resultados de la búsqueda se guardan como tarjetas de ubicación en el panel Pins (Marcas). Puede guardar hasta 10 tarjetas de ubicación.
   
   ![Ejemplo de anclaje de mapa de ArcGIS](media/power-bi-visualization-arcgis/power-bi-pin-arcgis-newer.png)
3. Power BI agrega en esa ubicación una marca, cuyo color puede cambiar.
   
   ![Ejemplo de color de anclaje](media/power-bi-visualization-arcgis/power-bi-pin-color-new.png)
4. Agregue y elimine marcas.
   
   ![Ejemplo de adición y eliminación de anclaje](media/power-bi-visualization-arcgis/power-bi-pin3.png)

### <a name="drive-time"></a>Tiempo de conducción
El panel Drive time (Tiempo de conducción) le permite seleccionar una ubicación y determinar luego qué otras características del mapa están dentro de un radio o tiempo de conducción específico.  
    ![Ejemplo de tiempo de conducción](media/power-bi-visualization-arcgis/power-bi-esri-drive-time.png)

1. Seleccione la pestaña **Drive time** (Tiempo de conducción) y elija la herramienta de selección única o múltiple. Seleccione únicamente la marca para Washington D.C.

   ![Ejemplo de selección de un solo anclaje](media/power-bi-visualization-arcgis/power-bi-esri-single-select.png)
   
   > [!TIP]
   > Es más fácil seleccionar una ubicación si amplía el mapa (mediante el icono +).
   > 
   > 
2. Supongamos que vuela a Washington D.C. para unos días y desea averiguar qué tiendas hay a una distancia de conducción razonable. Cambie el área Search (Búsqueda) a **Radius** (Radio) y Distance (Distancia) a **50** millas, y seleccione OK (Aceptar).    
   
    ![Radio de tiempo de conducción](media/power-bi-visualization-arcgis/power-bi-esri-drive-time-radius.png)

3. El radio se muestra en color púrpura. Seleccione cualquier ubicación para mostrar sus detalles. También puede dar formato al radio cambiando el color y el contorno.
   
    ![Ejemplo de formato de radio con color y contorno](media/power-bi-visualization-arcgis/power-bi-esri-drive-time.png)

### <a name="reference-layer"></a>Capa de referencia
#### <a name="reference-layer---demographics"></a>Capa de referencia: datos demográficos
ArcGIS Maps para Power BI proporciona una selección de capas demográficas que ayudan a contextualizar los datos de Power BI.

1. Seleccione la pestaña **Capa de referencia** y elija **Datos demográficos**.
2. Cada capa que aparece tiene una casilla. Agregue una marca de verificación para agregar esa capa al mapa.  En este ejemplo, hemos agregado Average Household Income.<br/>
   
    ![Ejemplo demográfico de capa de referencia](media/power-bi-visualization-arcgis/power-bi-esri-reference-layer-demographic.png)
3. Asimismo, todas las capas son interactivas. Así como puede mantener el puntero sobre una burbuja para ver los detalles, puede hacer clic en un área sombreada en el mapa para ver los detalles.<br/>
   
    ![Ejemplo de detalles de capa de referencia](media/power-bi-visualization-arcgis/power-bi-esri-reference-layer-details.png)

#### <a name="reference-layer---arcgis"></a>Capa de referencia: ArcGIS
ArcGIS Online proporciona a las organizaciones la capacidad de publicar mapas web públicos. Además, Esri proporciona un conjunto elaborado de mapas web a través de Living Atlas. En la pestaña de ArcGIS, puede buscar todos los mapas web públicos o de Living Atlas y agregarlos al mapa como capas de referencia.

1. Seleccione la pestaña **Capa de referencia** y elija **ArcGIS**.
2. Escriba los términos de búsqueda y después seleccione una capa de mapa. En este ejemplo, hemos elegido USA Congressional Districts.
   
    ![Ejemplo de datos demográficos de Esri](media/power-bi-visualization-arcgis/power-bi-reference-details.png)
3. Para ver los detalles, seleccione un área sombreada para abrir *Select from reference layer* (Seleccionar a partir de la capa de referencia): use la herramienta de selección de capas de referencia para seleccionar límites u objetos en la capa de referencia.

<br/>

## <a name="selecting-data-points"></a>Seleccionar puntos de datos
ArcGIS Maps for Power BI permite que cinco modos de selección le ayuden a seleccionar los datos con precisión y rapidez.

Para cambiar el modo de selección, mantenga el cursor sobre el icono de la herramienta de selección única que se muestra en la imagen siguiente. También se expandirá la barra oculta para mostrar herramientas adicionales:

![Herramienta de selección de Esri](media/power-bi-visualization-arcgis/power-bi-esri-selection-tools2.png)

Cada herramienta tiene un rol único que permite seleccionar los datos: 

![Selección única de Esri](media/power-bi-visualization-arcgis/power-bi-esri-selection-single2.png) Seleccione puntos de datos individuales.

![Marquesina de selección de Esri](media/power-bi-visualization-arcgis/power-bi-esri-selection-marquee2.png) Dibuja un rectángulo en el mapa y selecciona los puntos de datos contenidos.

![Capa de referencia de selección de Esri](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-layer2.png) Permite usar los límites o polígonos en las capas de referencia para seleccionar puntos de datos contenidos.

![Capa de búfer de selección de Esri](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-buffer.png) Permite seleccionar datos mediante una capa de búfer.

![Selección similar de selección de Esri](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-similar.png) Permite seleccionar puntos de datos similares entre sí.

> [!NOTE]
> Se puede seleccionar un máximo de 250 puntos de datos a la vez.
> 
> 

<br/>

## <a name="getting-help"></a>Obtener ayuda
**Esri** ofrece [documentación exhaustiva](https://go.microsoft.com/fwlink/?LinkID=828772) sobre el conjunto de características de **ArcGIS Maps para Power BI**.

Puede formular preguntas, buscar la información más reciente, notificar problemas y encontrar respuestas en el [hilo de la comunidad de Power BI relacionado con **ArcGIS Maps para Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).

Si tiene alguna sugerencia para una mejora, envíela a la [lista de ideas de Power BI](https://ideas.powerbi.com).

<br/>

## <a name="managing-use-of-arcgis-maps-for-power-bi-within-your-organization"></a>Administrar el uso de ArcGIS Maps para Power BI en la organización
Power BI proporciona a los usuarios, administradores de inquilinos y administradores de TI la capacidad de decidir si usar ArcGIS Maps para Power BI. Debajo encontrará los pasos que puede llevar a cabo cada rol para administrar el uso de ArcGis Maps. 

### <a name="user-options"></a>Opciones de usuario
En Power BI Desktop, los usuarios pueden dejar de usar ArcGIS Maps for Power BI si lo deshabilitan en la pestaña Seguridad en **Archivo** > **Opciones y configuración** y luego seleccionan **Opciones** > **Seguridad**. Si se deshabilita, ArcGIS Maps no cargará de manera predeterminada.

![Ejemplo de cuadro de diálogo de seguridad de escritorio](media/power-bi-visualization-arcgis/power-bi-desktop-security-dialog2.png)

### <a name="tenant-admin-options"></a>Opciones de administrador de inquilinos
En PowerBI.com, los administradores de inquilinos pueden evitar que todos los usuarios del inquilino usen ArcGIS Maps for Power BI si deshabilitan la opción en **Configuración** > **Portal de administración** > **Configuración de inquilinos**. Si esto sucede, Power BI ya no mostrará el icono de ArcGIS Maps para Power BI en el panel de visualizaciones.

![Ejemplo del portal de administración de ArcGIS](media/power-bi-visualization-arcgis/power-bi-arcgis-admin-portal2.png)

### <a name="it-administrator-options"></a>Opciones del administrador de TI
Power BI Desktop admite el uso de la **Directiva de grupo** para deshabilitar ArcGIS Maps for Power BI en los equipos implementados de una organización.

<table>
<tr><th>Atributo</th><th>Valor</th>
</tr>
<tr>
<td>key</td>
<td>Software\Policies\Microsoft\Power BI Desktop&lt;/td&gt;
</tr>
<tr>
<td>valueName</td>
<td>EnableArcGISMaps</td>
</tr>
</table>

Un valor de 1 (decimal) habilita ArcGIS Maps para Power BI.

Un valor de 0 (decimal) deshabilita ArcGIS Maps para Power BI.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones
ArcGIS Maps para Power BI está disponible en los siguientes servicios y aplicaciones:

<table>
<tr><th>Servicio/aplicación</th><th>Disponibilidad</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Sí</td>
</tr>
<tr>
<td>Servicio Power BI (powerbi.com)</td>
<td>Sí</td>
</tr>
<tr>
<td>Aplicaciones móviles de Power BI</td>
<td>Sí</td>
</tr>
<tr>
<td>Publicar en Web de Power BI</td>
<td>No</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>No</td>
</tr>
<tr>
<td>Inserción del servicio Power BI (PowerBI.com)</td>
<td>No</td>
</tr>
</table>

En los servicios o aplicaciones donde ArcGIS Maps para Power BI no está disponible, la visualización mostrará un objeto visual vacío con el logotipo de Power BI.

En la geocodificación de direcciones postales, solo se geocodifican las primeras 1500 direcciones. La geocodificación de nombres de lugares o países no está sujeto al límite de 1500 direcciones.

<br/>

**¿Cómo funciona ArcGIS Maps for Power BI?**
Esri (www.esri.com) proporciona ArcGIS Maps for Power BI. Su uso de ArcGIS Maps for Power BI está sujeto a los [términos](https://go.microsoft.com/fwlink/?LinkID=8263222) y a la [directiva de privacidad](https://go.microsoft.com/fwlink/?LinkID=826323) de Esri. Los usuarios de Power BI que quieran usar objetos visuales de ArcGIS Maps for Power BI tienen que aceptar el cuadro de diálogo de consentimiento (vea Consentimiento del usuario para más detalles).  El uso de ArcGIS Maps for Power BI de Esri está sujeto a los términos y a la directiva de privacidad de Esri, a los que puede acceder desde el vínculo del cuadro de diálogo de consentimiento. Cada usuario debe dar su consentimiento antes de usar ArcGIS Maps for Power BI por primera vez. Una vez que el usuario acepta el consentimiento, los datos enlazados al objeto visual se envían a los servicios de Esri al menos para su geocodificación, lo que implica transformar la información de ubicación en información de latitud y longitud que se pueda representar en un mapa. Debe tener en cuenta que los datos enlazados a la visualización de datos pueden enviarse a los servicios de Esri. Esri proporciona servicios como mapas base, análisis espacial, geocodificación, etc. El objeto visual de ArcGIS Maps for Power BI interactúa con estos servicios mediante una conexión SSL protegida por un certificado proporcionado y mantenido por Esri. Puede obtener más información sobre ArcGIS Maps for Power BI en la [Página del producto ArcGIS Maps for Power BI](https://www.esri.com/powerbi) de Esri.

Cuando un usuario se suscribe a una suscripción Plus ofrecida por Esri a través de ArcGIS Maps for Power BI, está entablando una relación directa con Esri. Power BI no envía información personal sobre el usuario a Esri. El usuario inicia sesión en una aplicación AAD proporcionada por Esri, y confía en ella, mediante su propia identidad AAD. Al hacerlo, el usuario comparte su información personal directamente con Esri. Una vez que el usuario agrega contenido Plus a un objeto visual de ArcGIS Maps for Power BI, otros usuarios de Power BI también necesitan una suscripción Plus de Esri para ver o editar ese contenido. 

Para realizar preguntas técnicas detalladas sobre el funcionamiento de ArcGIS Maps for Power BI de Esri, póngase en contacto con Esri a través de su sitio de soporte técnico.

**¿Qué datos se envían a Esri?**
Puede leer sobre los datos que se transfieren a Esri en su [documentación](https://doc.arcgis.com/en/maps-for-powerbi/get-started/data-transfer.htm).

**¿Hay algún cargo por usar ArcGIS Maps para Power BI?**

ArcGIS Maps para Power está disponible para todos los usuarios de Power BI sin costo adicional. Es un componente que proporciona **Esri** y su uso está sujeto a los términos y a la directiva de privacidad que proporciona **Esri**, como se ha indicado anteriormente en este artículo.

**Recibo un mensaje de error en Power BI Desktop sobre el hecho de que la caché está llena**

Se trata de un error que están solucionando.  Mientras tanto, para borrar la memoria caché, intente eliminar archivos en esta ubicación: C:\Users\\AppData\Local\Microsoft\Power BI Desktop\CEF y, luego, reinicie Power BI.

**¿ArcGIS Maps para Power BI admite archivos de forma de Esri?**

ArcGIS Maps para Power BI detecta de forma automática los límites estándar, como países o regiones, estados o provincias y códigos postales. Si necesita proporcionar sus propias formas, puede hacerlo mediante [Mapas de formas en Power BI Desktop (versión preliminar)](desktop-shape-map.md).

**¿Puedo ver mi mapas de ArcGIS sin conexión?**

No, Power BI necesita conectividad de red para mostrar los mapas.

**¿Puedo conectarme a mi cuenta de ArcGIS Online desde Power BI?**

Aún no. [Vote por esta idea](https://ideas.powerbi.com/forums/265200-power-bi-ideas/suggestions/9154765-arcgis-geodatabases) y le enviaremos un correo electrónico cuando comencemos a trabajar en esta característica.  

## <a name="next-steps"></a>Pasos siguientes
[Interactuación con un mapa de ArcGIS compartido con usted](power-bi-visualizations-arcgis.md)

[Entrada de blog con el anuncio de la disponibilidad de ArcGIS Maps para Power BI](https://powerbi.microsoft.com/blog/announcing-arcgis-maps-for-power-bi-by-esri-preview/)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

