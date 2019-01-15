---
title: Objetos visuales personalizados certificados de Power BI
description: Requisitos y procedimiento para enviar un objeto visual personalizado para su certificación. Y una lista de objetos visuales personalizados ya certificados.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/21/2018
ms.openlocfilehash: bfe3421b2c2328ee65cb8f34b43b34de8fe98723
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280226"
---
# <a name="certified-custom-visuals"></a>Objetos visuales personalizados certificados

## <a name="what-are-certified-custom-visuals"></a>¿Qué son los objetos visuales personalizados **_certificados_**?

Los objetos visuales personalizados certificados son objetos visuales en **Marketplace** que cumplen con determinados requisitos de **código especificado** que el **equipo de Microsoft Power BI** ha probado y aprobado. Una vez que un objeto visual personalizado está certificado, ofrece más características. Por ejemplo, puede [exportar a PowerPoint](consumer/end-user-powerpoint.md) y mostrar el objeto visual en los correos electrónicos recibidos cuando un usuario [se suscribe a páginas del informe](consumer/end-user-subscribe.md).

Los **objetos visuales personalizados certificados** se usan como los [objetos visuales personalizados estándar](power-bi-custom-visuals.md). Los objetos visuales personalizados certificados se pueden agregar al **servicio Power BI** o a un **informe de Power BI Desktop**, y se pueden ver con **Power BI Mobile** y **Power BI Embedded**.

Las pruebas realizadas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos. **Microsoft** *no* es el autor de los objetos visuales personalizados de terceros y recomendamos a los clientes que se pongan en contacto directamente con el autor para comprobar la funcionalidad de cada objeto visual.

El proceso de certificación es opcional y son los desarrolladores quienes deciden si quieren que su objeto visual se certifique en Marketplace.  

Los **objetos visuales personalizados sin certificar** no tienen por qué ser inseguros. Algunos objetos visuales no están certificados porque no cumplen con uno o varios de los [requisitos de certificación](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por ejemplo, conectarse a un servicio externo, como los objetos visuales de mapa o los objetos visuales que usan bibliotecas comerciales.

¿Es un desarrollador web interesado en crear sus propias visualizaciones y agregarlas a  **[Microsoft AppSource](https://appsource.microsoft.com)**? Vea  **[Desarrollo de objetos visuales personalizados de Power BI](developer/custom-visual-develop-tutorial.md)** para ver cómo hacerlo.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Eliminación de objetos visuales personalizados certificados de Power BI

Microsoft puede quitar un objeto visual de la [lista de objetos visuales certificados](#list-of-custom-visuals-that-have-been-certified) a su criterio exclusivo.

## <a name="getting-a-custom-visualcertified"></a>Obtención de un objeto visual personalizado certificado

### <a name="certification-requirements"></a>Requisitos de certificación

Para obtener un objeto visual personalizado [certificado](#certified-custom-visuals), asegúrese de que el objeto visual personalizado cumple con los siguientes requisitos:  

* Está aprobado por Microsoft AppSource. El objeto visual personalizado debe estar en nuestro [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* El objeto visual personalizado se escribe con la API 1.2 o superior con control de versiones.
* El repositorio de código está disponible para que lo revise el equipo de Power BI; por ejemplo, el código fuente (archivos JavaScript o TypeScript) está en un formato natural que podamos leer, a través de GitHub.

    >[!Note]
    > No tiene que compartir públicamente el código en Github.

* Solo usa componentes OSS revisables públicos (bibliotecas JS o TypeScript que son públicos. El código fuente está disponible para su revisión y no tiene vulnerabilidades conocidas). No podemos comprobar un objeto visual personalizado que use un componente comercial.

* No accede a servicios o recursos externos, incluidos, entre otros, ninguna solicitud HTTP/S o WebSocket sale de Power BI para dirigirse a otro servicio. 

> [!TIP]
> Le recomendamos que use EsLint con un conjunto de reglas de seguridad predeterminadas para validar previamente el código antes de su envío.

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Proceso para enviar un objeto visual personalizado para su certificación

Para enviar un objeto visual personalizado para su certificación:

1. Envíe un correo electrónico al equipo de soporte técnico de objetos visuales personalizados de Power BI (pbicvsupport@microsoft.com). En el correo electrónico, incluya la siguiente información:
    * Título: Solicitud de certificación visual
    * Vínculo al repositorio de GitHub donde se hospeda el código fuente en un lenguaje natural
    * [Cumplimiento de los requisitos](#certification-requirements)
    * Pase la revisión del código

2. El equipo de objetos visuales personalizados de Microsoft le notificará cuando el objeto visual personalizado se haya certificado y agregado a la [lista de objetos visuales certificados](#list-of-custom-visuals-that-have-been-certified), o bien se haya rechazado, e incluirá un informe de los problemas que deben corregirse. Es responsabilidad del desarrollador mantener una línea abierta de comunicación con Microsoft y actualizar sus objetos visuales certificados según sea necesario.

## <a name="list-of-custom-visuals-that-have-been-certified"></a>Lista de objetos visuales personalizados que se han certificado

| Vínculo a AppSource | Vincular al vídeo |
| --- | --- |
| [3AG Systems - Column Chart With Relative Variance](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381803) (Sistemas 3AG: Gráfico de columnas con la varianza relativa) | |
| [Aster Plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft Calendar](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) | |
| [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) | [Vídeo](https://youtu.be/So5xKMSpVJI) |
| [Gráfico de cajas y bigotes](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) | |
| [Gráfico de cajas y bigotes de MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) | [Vídeo](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | [Vídeo](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) | |
| [Bullet Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) | [Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendar de Tallan](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) | |
| [Candlestick by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | [Vídeo](https://youtu.be/nT_18gyRxPo) |
| [Card with States de OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) | [Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) | [Vídeo](https://youtu.be/9NHXALkBXuY) |
| [Cluster Map](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) | |
| [Cylindrical Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | [Vídeo](https://youtu.be/DgdoWi7Gcxo) |
| [Dial Gauge](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) | |
| [Dot Plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) | |
| [Dot Plot de OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) | [Vídeo](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) | |
| [Drill-down column chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) | [Vídeo](https://youtu.be/lBy2gQQ5YsQ) |
| [Drill-down column chart for time based data](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | [Vídeo](https://youtu.be/T_mRou18vx0) |
| [Drill-down donut chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | [Vídeo](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380983) (Dynamic Tooltip de MAQ Software) | [Vídeo](https://youtu.be/Z-tl97BpEr0) |
| [Enhanced Scatter](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | [Vídeo](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Filtrar por lista de Devscope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381413) | [Vídeo](https://youtu.be/RetEWGwBu0I) |
| [Force-Directed Graph](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) | [Vídeo](https://youtu.be/YsTa7uyJ4sg) |
| [Funnel with Source by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) | [Vídeo](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) | [Vídeo](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) | |
| [Grid by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380825) | [Vídeo](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) | [Vídeo](https://youtu.be/0ZGzJaq_KT4) |
| [Histogram Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) | |
| [Gráfico de histograma con puntos de MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) | [Vídeo](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) | [Vídeo](https://youtu.be/SudZei68PPo) |
| [Image by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) | |
| [Image Grid](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) | |
| [Gráfico KPI de Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) | |
| [Columna de KPI de MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380996) | [Vídeo](https://youtu.be/rU0xoOlIq1U) |
| [KPI Grid by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380947) | [Vídeo](https://youtu.be/dM4PvZh71V0) |
| [KPI Indicator](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | [Vídeo](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) | [Vídeo](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) | |
| [Mekko Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) | [Vídeo](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381763) | |
| [Información general de CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381477) | |
| [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI Matrix](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) | [Vídeo](https://youtu.be/1enze8pcGzY) |
| [Pulse Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) | [Vídeo](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant Chart de MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) | [Vídeo](https://youtu.be/ppBnyhqWNC0) |
| [Radar Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) | |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) | [Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) | [Vídeo](https://youtu.be/d5xBCMmb3hU) |
| [Sankey Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) | [Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Gráfico de dispersión de Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381703) | |
| [Scroller](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) | [Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) | [Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Stream Graph](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) | |
| [Panel sinóptico de OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380873) | |
| [Table Heatmap](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) | |
| [Tachometer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [Vídeo](https://youtu.be/C3OXdETbS9o) |
| [Filtro de texto](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [Thermometer by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380847) | [Vídeo](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380798) | |
| [Timeline Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) | [Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381427) | [Vídeo](https://youtu.be/szNi9YgXFJc) |
| [Gráfico de tornado](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [Vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) | [Vídeo](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) | [Vídeo](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | [Vídeo](https://youtu.be/0BZsVCQdEkc) |
| [User List by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) | |
| [Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) | [Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Word Cloud](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [Vídeo](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>Pasos siguientes

* [Desarrollo de objetos visuales personalizados de Power BI](developer/custom-visual-develop-tutorial.md)
* [Lista de reproducción sobre objetos visuales de Microsoft en YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizaciones en Power BI](visuals/power-bi-report-visualizations.md)  
* [Visualizaciones personalizadas en Power BI](power-bi-custom-visuals.md)  
* [Publicar objetos visuales personalizados en Microsoft AppSource](developer/office-store.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
