---
title: Objetos visuales de Power BI certificados
description: Requisitos y procedimiento para enviar un objeto visual personalizado para su certificación. Y una lista de objetos visuales de Power BI certificados.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: c39b96122016746905ea09c0983adf50356f0c77
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "75221974"
---
# <a name="get-a-power-bi-visual-certified"></a>Obtención de un objeto visual de Power BI certificado

Los objetos visuales de Power BI certificados son objetos visuales en *Marketplace* que cumplen con determinados requisitos de *código especificado* que el *equipo de Microsoft Power BI* ha probado y aprobado. Las pruebas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos.

Los objetos visuales de Power BI certificados y los [objetos visuales de Power BI estándar](power-bi-custom-visuals.md) se usan de la misma manera. Se pueden agregar a [Power BI Desktop](../desktop-what-is-desktop.md) y al [servicio Power BI](../power-bi-service-overview.md) y ver con [Power BI Mobile](../consumer/mobile/mobile-apps-for-mobile-devices.md) y [Power BI Embedded](embedding.md).

El proceso de certificación es un proceso opcional. Son los desarrolladores los que deciden si quieren certificar el objeto visual de Power BI en el Marketplace. Una vez que un objeto visual de Power BI está certificado, ofrece más características. Por ejemplo, puede [exportar el objeto visual a PowerPoint](../consumer/end-user-powerpoint.md) o mostrarlo en los correos electrónicos recibidos, cuando un usuario [se suscribe a páginas del informe](../consumer/end-user-subscribe.md).

Los objetos visuales de Power BI sin certificar no tienen por qué ser inseguros. Algunos objetos visuales no están certificados porque no cumplen con uno o varios de los [requisitos de certificación](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por ejemplo, conectarse a un servicio externo, como los objetos visuales de mapa o los objetos visuales que usan bibliotecas comerciales.

Si es desarrollador web y está interesado en crear sus propios objetos visuales de Power BI y agregarlos a  [Microsoft AppSource](https://appsource.microsoft.com), empiece con el tutorial  [Desarrollar un objeto visual de Power BI](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> **Microsoft***no* es autor de los objetos visuales de Power BI de terceros. Para comprobar la funcionalidad de los objetos visuales de terceros, recomendamos a los clientes que se pongan en contacto directamente con el autor.

> [!IMPORTANT]
> Microsoft puede quitar un objeto visual de Power BI de la [lista de objetos visuales certificados de Power BI](#certified-power-bi-visuals) a su criterio exclusivo.

## <a name="certification-requirements"></a>Requisitos de certificación

Para [certificar](#get-a-power-bi-visual-certified) un objeto visual de Power BI, asegúrese de que este cumple con los requisitos que aparecen en esta sección. 

> [!TIP]
> Le recomendamos que use EsLint con el conjunto de reglas de seguridad predeterminadas para validar previamente el código antes de su envío.

* Aprobación por el Centro de partners o el Panel de vendedores de Microsoft. El objeto visual de Power BI debe estar en nuestro [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* El objeto visual de Power BI está escrito con *API v2.5* o una versión superior.
* El repositorio de código está disponible para que lo revise el equipo de Power BI. Por ejemplo, un formato legible del código fuente (JavaScript o TypeScript) está disponible para nosotros a través de GitHub.

    >[!NOTE]
    > No tiene que compartir públicamente el código en Github.

* Requisitos del repositorio de código:
  * Debe incluir estos archivos:
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * No debe incluir la carpeta *node_modules* (agregue *node_modules* al archivo .gitingore*).
  * El comando *npm install* no debe devolver ningún error.
  * El comando *npm audit* no debe devolver ninguna advertencia con nivel alto o moderado.
  * El comando *pbiviz package* no debe devolver ningún error.
  * Debe incluir [TSlint de Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sin ninguna configuración invalidada. Este comando no debe devolver ningún error de lint.
   * El paquete compilado del objeto visual de Power BI debe coincidir con el paquete enviado.
* Requisitos del código fuente:
   * El objeto visual de Power BI deba admitir la [API de representación de eventos](./visuals/event-service.md).
   * Asegúrese de que no se ejecuta ningún código arbitrario o dinámico (incorrecto: eval(), no es seguro usar settimeout(), requestAnimationFrame(), setinterval [alguna función con entrada de usuario], ejecución de datos/entrada de usuario).
   * Asegúrese de que DOM se manipule de forma segura (incorrecto: innerHTML, D3.html(<alguna entrada de datos/usuario>), y use saneamiento para los datos o la entrada de usuario antes de agregarlos a DOM.
   * Asegúrese de que no haya errores ni excepciones de JavaScript en la consola del explorador para ningún dato de entrada. Los usuarios pueden usar el objeto visual de Power BI con un intervalo diferente de datos inesperados, por lo que el objeto visual no debe producir un error. Puede usar este [informe de ejemplo](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) como conjunto de datos de prueba.

* Si se cambia alguna propiedad del archivo *capabilities.json*, asegúrese de que no interrumpe los informes del usuario existentes.

* Asegúrese de que el objeto visual de Power BI cumple las [directrices de los objetos visuales de Power BI](./guidelines-powerbi-visuals.md).
    
* El código solo puede usar componentes de OSS que se pueden revisar de manera pública, como bibliotecas públicas de JavaScript o TypeScript. El código fuente debe estar disponible para su revisión y no tiene vulnerabilidades conocidas. No podemos comprobar un objeto visual personalizado que use un componente comercial.

* El objeto visual de Power BI no debe acceder a recursos ni servicios externos. Por ejemplo, ninguna solicitud HTTP/S ni WebSocket puede salir de Power BI a ningún servicio. 

## <a name="submitting-a-power-bi-visual-for-certification"></a>Envío de un objeto visual de Power BI para certificación

Puede solicitar que el equipo de Power BI certifique su objeto visual de Power BI mediante el Centro de partners.

>[!TIP]
>El proceso de certificación de Power BI puede tardar un tiempo. Si va a crear un objeto visual de Power BI, se recomienda publicarlo a través del Centro de partners antes de solicitar la certificación de Power BI. Esto garantiza que la publicación del objeto visual no se retrase.

Para solicitar la certificación de Power BI:

1. Inicie sesión en el Centro de datos.
2. En la página **Información general**, elija su objeto visual de Power BI y vaya a la página de configuración del **producto**.
3. Active la casilla **Request Power BI certification** (Solicitar la certificación de Power BI).
4. En la página **Revisar y publicar**, en el cuadro de texto **Notas para la certificación**, proporcione un vínculo al código fuente y las credenciales necesarias para acceder a él.

>[!NOTE]
> Si está en medio de un proceso de envío de un objeto visual de Power BI y debe usar el [Panel de vendedores](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (la herramienta de administración anterior), revise las instrucciones para el [proceso de envío de una certificación del Panel de vendedores](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="certified-power-bi-visuals"></a>Objetos visuales de Power BI certificados

A continuación se enumeran los objetos visuales certificados de Power BI. Haga clic en el vínculo para abrir el objeto visual de Power BI en AppSource. Si hay un vídeo disponible, puede hacer clic en el vínculo de vídeo para verlo.

* [3AG Systems - Bar Chart With Absolute Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802) (Sistemas 3AG: Gráfico de barras con varianza absoluta)
*  [3AG Systems - Bar Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912) (Sistemas 3AG: Gráfico de barras con la varianza relativa)
*  [3AG Systems - Column Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) (Sistemas 3AG: Gráfico de columnas con la varianza relativa)
*  [3AG Systems - Column Chart With Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724) (Sistemas 3AG: Gráfico de columnas con varianza)
* [Advanced Donut Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) [Objeto visual de anillo avanzado (Edición completa)]
*  [Advanced Donut Visual (Light Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) [Objeto visual de anillo avanzado (Edición ligera)]
*  [Advanced Graph Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086) (Objeto visual de gráfico avanzado)
*  [Visualización de red avanzada](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Advanced TimeSeries Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) [Objeto visual de serie temporal avanzada (Edición completa)]
*  [Aster Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Gráfico de cajas y bigotes](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Gráfico de cajas y bigotes de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Brick Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Bubble Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755),  **[vínculo de vídeo](https://youtu.be/AOlsFYkfkcw)**
* [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[vínculo de vídeo](https://youtu.be/mtvUNl9bMjA)**
* [Calendar de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Calendar de Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Candlestick de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[vínculo de vídeo](https://youtu.be/nT_18gyRxPo)**
*  [Card with States de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[vínculo de vídeo](https://youtu.be/AQvd2FhRyCI)**
*  [Circular Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Cluster Map](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Custom Calendar de Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Cylindrical Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Dot Plot de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[vínculo de vídeo](https://youtu.be/By16pX9KT40)**
*  [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Gráfico de columnas de exploración en profundidad](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[vínculo de vídeo](https://youtu.be/lBy2gQQ5YsQ)**
*  [Gráfico de columnas de exploración en profundidad para datos temporales](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[vínculo de vídeo](https://youtu.be/T_mRou18vx0)**
*  [Gráfico de anillos de exploración en profundidad](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[vínculo de vídeo](https://youtu.be/AUVFrSHmPeo)**
*  [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) (Dynamic Tooltip de MAQ Software)
*  [Gráfico de dispersión mejorado](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[vínculo de vídeo](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filter by List de Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[vínculo de vídeo](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[vínculo de vídeo](https://youtu.be/YsTa7uyJ4sg)**
*  [Funnel with Source by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[vínculo de vídeo](https://youtu.be/qJ7s_KrGiUU)**
* [Gantt Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarchy Chart de Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[vínculo de vídeo](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogram Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Gráfico de histograma con puntos de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Gráfico de barras horizontal](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Image by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [Gráfico KPI de Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [Columna de KPI de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [KPI Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI Indicator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI Ticker by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Linear Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[vínculo de vídeo](https://youtu.be/90FLCKpgicA)**
*  [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Información general de CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [vínculo de vídeo](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[vínculo de vídeo](https://youtu.be/1enze8pcGzY)**
*  [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[vínculo de vídeo](https://youtu.be/DQWdcQtjDVw)**
*  [Quadrant Chart de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Radar Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Rotating Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[vínculo de vídeo](https://youtu.be/WWP9wVUHGaA)**
*  [Gráfico de dispersión de Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Scroller](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[vínculo de vídeo](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[vínculo de vídeo](https://youtu.be/0m3Vnvso9tY)**
*  [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Panel sinóptico de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Table Heatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[vínculo de vídeo](https://youtu.be/C3OXdETbS9o)**
*  [Filtro de texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Text Wrapper by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[vínculo de vídeo](https://youtu.be/ozMtZ4_NZ10)**
*  [Timeline de CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [vínculo de vídeo](https://youtu.be/szNi9YgXFJc)
*  [Tornado chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[vínculo de vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Trading Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI Card](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[vínculo de vídeo](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[vínculo de vídeo](https://youtu.be/0BZsVCQdEkc)**
*  [User List by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Venn Diagram by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Violin Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[vínculo de vídeo](https://youtu.be/1vRqYUsm3Vk)**
*  [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[vínculo de vídeo](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>Preguntas frecuentes

Para obtener más información sobre los objetos visuales, vea las [preguntas más frecuentes sobre objetos visuales certificados](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Pasos siguientes

* [Desarrollo de objetos visuales personalizados de Power BI](../developer/custom-visual-develop-tutorial.md)
* [Lista de reproducción sobre objetos visuales de Microsoft en YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizaciones en Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualizaciones personalizadas en Power BI](power-bi-custom-visuals.md)  
* [Publicación de objetos visuales de Power BI en Microsoft AppSource](../developer/office-store.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
