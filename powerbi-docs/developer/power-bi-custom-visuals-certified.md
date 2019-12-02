---
title: Objetos visuales de Power BI certificados
description: Requisitos y procedimiento para enviar un objeto visual personalizado para su certificación. Y una lista de objetos visuales de Power BI ya certificados.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 05/9/2019
ms.openlocfilehash: 373d57b871953f1afe02212ff0a1bbdb633cac4d
ms.sourcegitcommit: a21f7f9de32203e3a4057292a24ef9b5ac6ce94b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74565252"
---
# <a name="get-a-power-bi-visual-certified"></a>Obtención de un objeto visual de Power BI certificado

## <a name="what-are-_certified_-power-bi-visuals"></a>¿Qué son los objetos visuales de Power BI **_certificados_** ?

Los objetos visuales de Power BI certificados son objetos visuales en **Marketplace** que cumplen con determinados requisitos de **código especificado** que el **equipo de Microsoft Power BI** ha probado y aprobado. Una vez que un objeto visual personalizado está certificado, ofrece más características. Por ejemplo, puede [exportar a PowerPoint](../consumer/end-user-powerpoint.md) y mostrar el objeto visual en los correos electrónicos recibidos cuando un usuario [se suscribe a páginas del informe](../consumer/end-user-subscribe.md).

**Los objetos visuales de Power BI certificados** se usan como [objetos visuales de Power BI estándar](power-bi-custom-visuals.md). Los objetos visuales de Power BI certificados se pueden agregar al **servicio Power BI** o a un **informe de Power BI Desktop**, y se pueden ver con **Power BI Mobile** y **Power BI Embedded**.

Las pruebas realizadas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos. **Microsoft** *no* es el autor de los objetos visuales de Power BI de terceros y recomendamos a los clientes que se pongan en contacto directamente con el autor para comprobar la funcionalidad de cada objeto visual.

El proceso de certificación es opcional y son los desarrolladores quienes deciden si quieren que su objeto visual se certifique en Marketplace.  

**Los objetos visuales de Power BI sin certificar** no tienen por qué ser inseguros. Algunos objetos visuales no están certificados porque no cumplen con uno o varios de los [requisitos de certificación](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por ejemplo, conectarse a un servicio externo, como los objetos visuales de mapa o los objetos visuales que usan bibliotecas comerciales.

¿Es un desarrollador web interesado en crear sus propias visualizaciones y agregarlas a  **[Microsoft AppSource](https://appsource.microsoft.com)** ? Vea  **[Desarrollo de objetos visuales personalizados de Power BI](visuals/custom-visual-develop-tutorial.md)** para ver cómo hacerlo.

## <a name="removal-of-power-bi-certified-power-bi-visuals"></a>Eliminación de objetos visuales de Power BI certificados en Power BI

Microsoft puede quitar un objeto visual de la [lista de objetos visuales certificados](#list-of-power-bi-visuals-that-have-been-certified) a su criterio exclusivo.

## <a name="getting-a-custom-visualcertified"></a>Obtención de un objeto visual personalizado certificado

### <a name="certification-requirements"></a>Requisitos de certificación

Para obtener un objeto visual personalizado [certificado](#get-a-power-bi-visual-certified), asegúrese de que el objeto visual personalizado cumple con los siguientes requisitos:  

* Está aprobado por Microsoft AppSource. El objeto visual personalizado debe estar en nuestro [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* El objeto visual personalizado se escribe con la **API v2.5** o superior con control de versiones.
* El repositorio de código está disponible para su revisión por el equipo de Power BI (por ejemplo, código fuente [JavaScript o TypeScript] en un formato natural que se pueda leer, a través de GitHub).

    >[!Note]
    > No tiene que compartir públicamente el código en Github.
* Requisitos del repositorio de código:
   * Debe incluir el conjunto mínimo de archivos necesario:
      * .gitignore
      * capabilities.json
      * pbiviz.json
      * package.json
      * package-lock.json
      * tsconfig.json
   * No debe incluir la carpeta node_modules (agregue node_modules al archivo .gitingore).
   * El comando **npm install** no debe devolver ningún error.
   * El comando **npm audit** no debe devolver ninguna advertencia con nivel alto o moderado.
   * El comando **pbiviz package** no debe devolver errores.
   * Debe incluir [TSlint de Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sin configuración invalidada, y este comando no debe devolver ningún error de lint.
   * El paquete compilado del objeto visual personalizado debe coincidir con el paquete enviado (el hash md5 de ambos archivos debe ser igual).
* Requisitos del código fuente:
   * El objeto visual debe admitir la [API de representación de eventos](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Asegúrese de que no se ejecuta ningún código arbitrario o dinámico (incorrecto: eval(), no es seguro usar settimeout(), requestAnimationFrame(), setinterval [alguna función con entrada de usuario], ejecución de datos/entrada de usuario).
   * Asegúrese de que DOM se manipule de forma segura (incorrecto: innerHTML, D3.html(<alguna entrada de datos/usuario>), y use saneamiento para los datos o la entrada de usuario antes de agregarlos a DOM.
   * Asegúrese de que no haya errores o excepciones de JavaScript en la consola del explorador para ningún dato de entrada. Los usuarios pueden usar el objeto visual con un intervalo diferente de datos inesperados, por lo que el objeto visual no debe producir un error. Puede usar [este informe de ejemplo](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) como conjunto de datos de prueba.

* Si se cambia alguna propiedad de capabilities.json, asegúrese de que no interrumpe los informes del usuario existentes.

* Asegúrese de que el objeto visual cumple las [directrices de los objetos visuales de Power BI](./guidelines-powerbi-visuals.md). **No se permiten marcas de agua**.

* Solo usa componentes OSS revisables públicos (bibliotecas JS o TypeScript que son públicos. El código fuente está disponible para su revisión y no tiene vulnerabilidades conocidas). No podemos comprobar un objeto visual personalizado que use un componente comercial.

* No accede a servicios o recursos externos, incluidos, entre otros, ninguna solicitud HTTP/S o WebSocket sale de Power BI para dirigirse a otro servicio. 

> [!TIP]
> Le recomendamos que use EsLint con un conjunto de reglas de seguridad predeterminadas para validar previamente el código antes de su envío.

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Proceso para enviar un objeto visual personalizado para su certificación

Para enviar un objeto visual personalizado para su certificación:

1. Envíe un correo al equipo de soporte técnico de objetos visuales de Power BI (pbicvsupport@microsoft.com). En el correo electrónico, incluya la siguiente información:
    * Título: Solicitud de certificación visual
    * Vínculo al repositorio de GitHub donde se hospeda el código fuente en un lenguaje natural
    * [Cumplimiento de los requisitos](#certification-requirements)
    * Pase la revisión del código

2. El equipo de objetos visuales de Power BI de Microsoft le notificará cuando el objeto visual personalizado se haya certificado y agregado a la [lista certificada](#list-of-power-bi-visuals-that-have-been-certified), o bien se haya rechazado, e incluirá un informe de las incidencias que deben corregirse. Es responsabilidad del desarrollador mantener una línea abierta de comunicación con Microsoft y actualizar sus objetos visuales certificados según sea necesario.

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Lista de objetos visuales de Power BI que se han certificado

| Vínculo a AppSource | Vincular al vídeo |
| --- | --- |
| [3AG Systems - Bar Chart With Relative Variance](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) (Sistemas 3AG: Gráfico de barras con la varianza relativa) | |
| [3AG Systems - Column Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) (Sistemas 3AG: Gráfico de columnas con la varianza relativa) | |
| [Objeto visual de anillo avanzado](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [Visualización de red avanzada](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [Objeto visual de serie temporal avanzada](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [Objeto visual combinado avanzado](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [Aster Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [Vídeo](https://youtu.be/So5xKMSpVJI) |
| [Gráfico de cajas y bigotes](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [Gráfico de cajas y bigotes de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [Vídeo](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [Vídeo](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendar de Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [Candlestick by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [Vídeo](https://youtu.be/nT_18gyRxPo) |
| [Card with States de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [Vídeo](https://youtu.be/9NHXALkBXuY) |
| [Cluster Map](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [Cylindrical Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [Vídeo](https://youtu.be/DgdoWi7Gcxo) |
| [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Dot Plot de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [Vídeo](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [Drill-down column chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [Vídeo](https://youtu.be/lBy2gQQ5YsQ) |
| [Drill-down column chart for time based data](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [Vídeo](https://youtu.be/T_mRou18vx0) |
| [Drill-down donut chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [Vídeo](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) (Dynamic Tooltip de MAQ Software) | [Vídeo](https://youtu.be/Z-tl97BpEr0) |
| [Enhanced Scatter](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [Vídeo](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Filtrar por lista de Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [Vídeo](https://youtu.be/RetEWGwBu0I) |
| [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [Vídeo](https://youtu.be/YsTa7uyJ4sg) |
| [Funnel with Source by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [Vídeo](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [Vídeo](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [Vídeo](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [Vídeo](https://youtu.be/0ZGzJaq_KT4) |
| [Histogram Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [Gráfico de histograma con puntos de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [Vídeo](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [Vídeo](https://youtu.be/SudZei68PPo) |
| [Image by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [Gráfico KPI de Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [Columna de KPI de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [Vídeo](https://youtu.be/rU0xoOlIq1U) |
| [KPI Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [Vídeo](https://youtu.be/dM4PvZh71V0) |
| [KPI Indicator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [Vídeo](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [Vídeo](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [Vídeo](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [Información general de CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [Vídeo](https://youtu.be/1enze8pcGzY) |
| [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [Vídeo](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant Chart de MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [Vídeo](https://youtu.be/ppBnyhqWNC0) |
| [Radar Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [Vídeo](https://youtu.be/d5xBCMmb3hU) |
| [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Gráfico de dispersión de Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [Scroller](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [Panel sinóptico de OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [Table Heatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [Vídeo](https://youtu.be/C3OXdETbS9o) |
| [Filtro de texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [Vídeo](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [Vídeo](https://youtu.be/szNi9YgXFJc) |
| [Gráfico de tornado](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [Vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [Vídeo](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [Vídeo](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [Vídeo](https://youtu.be/0BZsVCQdEkc) |
| [User List by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [Vídeo](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES

Para obtener más información sobre los objetos visuales, vea las [preguntas más frecuentes sobre objetos visuales certificados](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Pasos siguientes

* [Desarrollo de objetos visuales personalizados de Power BI](../developer/custom-visual-develop-tutorial.md)
* [Lista de reproducción sobre objetos visuales de Microsoft en YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizaciones en Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualizaciones personalizadas en Power BI](power-bi-custom-visuals.md)  
* [Publicación de objetos visuales de Power BI en Microsoft AppSource](../developer/office-store.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
