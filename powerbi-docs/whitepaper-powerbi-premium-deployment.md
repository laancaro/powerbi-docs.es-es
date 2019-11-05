---
title: Implementación y administración de capacidades de Power BI Premium
description: Comprenda el potencial de Power BI Premium y aprenda a diseñar, implementar, supervisar y solucionar problemas de soluciones escalables.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/06/2019
LocalizationGroup: Premium
ms.openlocfilehash: eecbc43f26cebc12884ae6c5143a815f6e310ce5
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432369"
---
# <a name="deploying-and-managing-power-bi-premium-capacities"></a>Implementación y administración de capacidades de Power BI Premium

**Resumen:** Power BI Premium proporciona un rendimiento más coherente, compatibilidad con grandes volúmenes de datos y la flexibilidad de una plataforma empresarial de autoservicio unificada para todos los usuarios de su organización. Este documento técnico de nivel 300 se ha escrito específicamente para los administradores de Power BI y los autores y editores de contenido. Pretende ayudarles a comprender el potencial de Power BI Premium y a explicar cómo diseñar, implementar, supervisar y solucionar problemas de soluciones escalables.

**Autor:** [Peter Myers](https://www.linkedin.com/in/peterjsmyers) (MVP de plataforma de datos y experto de BI independiente con soluciones bit a bit)

**Revisores técnicos:** Adam Saxton, Akshai Mirchandani, Bhavik Merchant, David Magar, Josh Caplan, Michael Blythe, Nimrod Shalit, de Matrat a Swati Gupta

**Se aplica a:** Capacidades de servicio Power BI, Power BI Premium y Azure Power BI Embedded

> [!NOTE]
> Para guardar o imprimir estas notas del producto, haga clic en **Imprimir** en el explorador y después en **Guardar como PDF**.

## <a name="introducing-power-bi"></a>Presentación de Power BI

Power BI es un servicio de análisis de negocios diseñado para ofrecer información que permite tomar decisiones rápidas y fundamentadas. Desde su lanzamiento en 2015, se ha convertido rápidamente en un servicio popular que se usa para ofrecer soluciones para el menor de las organizaciones a la mayor cantidad de empresas.

Está disponible de dos maneras: como un servicio en la nube y como una solución de informes local denominada **Power BI Report Server**. \[[1](#endnote-01)\]

Power BI como servicio en la nube es software como servicio (SaaS) \[[2](#endnote-02)\]. Representa un conjunto de servicios y aplicaciones que permiten a las organizaciones desarrollar, implementar, administrar y compartir soluciones para supervisar su negocio.

No es la intención de estas notas del producto proporcionar una descripción completa del servicio Power BI. En su lugar, se centra en temas relevantes para el asunto de Power BI Premium. Para obtener información general sobre Power BI, consulte la [documentación de Power BI](service-admin-premium-multi-geo.md)completa. Para obtener una explicación más detallada de la servicio Power BI centrada en la realización de implementaciones de empresa con el buen rendimiento, consulte la documentación de [planeamiento de una implementación de Power BI Enterprise](https://aka.ms/pbienterprisedeploy) .

En el contexto del asunto de este documento, en esta sección se presentan y describen las capacidades, los tipos de contenido de Power BI, los modos de almacenamiento de modelos y las licencias. La comprensión de estos temas es esencial para implementar y administrar correctamente Power BI Premium.

### <a name="capacities"></a>Capacidades

Las **capacidades** son un concepto de Power BI básico que representa un conjunto de recursos (almacenamiento, procesador y memoria) que se usan para hospedar y proporcionar contenido de Power BI. Las capacidades son compartidas o dedicadas. Una **capacidad compartida** es la que se comparte con otros clientes de Microsoft, mientras que una **dedicada** está confirmada plenamente para un solo cliente. Las capacidades dedicadas se presentan en el tema [capacidades Premium](#premium-capacities) .

En la capacidad compartida, las cargas de trabajo se ejecutan en recursos informáticos compartidos con otros clientes. Dado que la capacidad debe compartir recursos, se imponen limitaciones para garantizar la "reproducción justa", como el tamaño máximo del modelo (1 GB) y la frecuencia máxima de actualización diaria (ocho veces al día).

### <a name="workspaces"></a>Áreas de trabajo

Power BI áreas de trabajo residen dentro de las capacidades y representan contenedores de seguridad, colaboración e implementación. Cada usuario de Power BI tiene un área de trabajo personal que se conoce como **Mi área de trabajo**. Se pueden crear áreas de trabajo adicionales para habilitar la colaboración y la implementación, y se conocen como **áreas de trabajo**. De forma predeterminada, las áreas de trabajo, incluidas las áreas de trabajo personales, se crean en la capacidad compartida.

### <a name="power-bi-content-types"></a>Tipos de contenido de Power BI

Para introducir temas Power BI Premium, es importante comenzar con una explicación detallada de la arquitectura de Power BI, incluidos los tipos de contenido fundamentales.

Todos los Power BI contenido se almacenan y administran en áreas de trabajo que son contenedores de contenido de Power BI. Cada usuario Power BI tiene su propia área de trabajo personal, pero el procedimiento recomendado general es crear áreas de trabajo. Las áreas de trabajo permiten la copropiedad del contenido y la capacidad de colaborar en el contenido. También proporcionan la capacidad de organizar y distribuir contenido a audiencias anchas como aplicaciones.

El siguiente contenido de Power BI se almacena en áreas de trabajo:

- Flujos de datos
- Conjuntos de datos
- Libros
- Informes
- Paneles

#### <a name="dataflows"></a>Flujos de datos

Power BI flujos de datos ayudan a las organizaciones a unificar los datos de orígenes dispares. Pueden considerarse como datos preparados y almacenados provisionalmente para su uso en modelos; sin embargo, no se pueden usar directamente como origen para la creación de informes. Aprovechan la amplia colección de conectores de datos de Microsoft, lo que permite la ingesta de datos de orígenes de datos locales y basados en la nube.

Los flujos de datos solo se pueden crear y administrar en áreas de trabajo, y se almacenan como entidades en Common Data Model (CDM) en Azure Data Lake Storage Gen2. Normalmente, están programados para actualizarse de forma periódica para almacenar datos actualizados.

Para obtener más información, consulte el documento sobre la [preparación de datos de autoservicio en Power BI (versión preliminar)](service-dataflows-overview.md) .

#### <a name="datasets"></a>Conjuntos de datos

Power BI conjuntos de datos representan un origen de datos preparado para la creación de informes y visualización. Hay muchos tipos de conjuntos de valores, creados por:

- Conexión a un modelo de datos existente que no está hospedado en una Power BI capacidad
- Cargar un archivo Power BI Desktop que contiene un modelo
- Cargar un libro de Excel (que contiene una o más tablas de Excel o un modelo de datos de libro) o cargar un archivo de valores separados por comas (CSV)
- Uso del servicio Power BI para crear un conjunto de un conjunto de flujo de streaming híbrido o de transmisión por secuencias

Excepto en el caso de los conjuntos de datos de streaming \[[3](#endnote-03)\], el conjunto de datos representa un modelo de datos que aprovecha las tecnologías de modelado consolidadas de Analysis Services.

Tenga en cuenta que en la documentación, a veces los conjuntos de información y los modelos de terminología son intercambiables. Por lo general, desde una perspectiva servicio Power BI se hace referencia a él como un **conjunto de DataSet** y, desde una perspectiva de desarrollo, se denomina **modelo**. En el contexto de estas notas del producto, esto significa prácticamente lo mismo.

##### <a name="externally-hosted-models"></a>Modelos hospedados externamente

La conexión a un modelo hospedado externamente implica la instalación de la [puerta de enlace de datos local](service-gateway-onprem.md) para conectarse a SQL Server Analysis Services, tanto si es local como si es una infraestructura como servicio (IaaS) hospedada en la máquina virtual. Azure Analysis Services no requiere una puerta de enlace. A menudo, este escenario tiene sentido cuando existen inversiones existentes en el modelo, que normalmente forman parte del almacenamiento de datos empresariales (EDW). Permite a Power BI realizar una **conexión dinámica** (LC) a Analysis Services y lo hace mediante la aplicación de los permisos de datos mediante la identidad del usuario del informe de Power BI. Por SQL Server Analysis Services, se admiten tanto modelos multidimensionales (cubos) como modelos tabulares. Como se muestra en la siguiente imagen, un conjunto de elementos de conexión dinámica pasa las consultas a los modelos hospedados externamente.

![Un conjunto de conexiones de conexión dinámica pasa las consultas a los modelos hospedados externamente](media/whitepaper-premium-deployment/live-connection-dataset.png)

##### <a name="power-bi-desktop-developed-models"></a>Modelos desarrollados por Power BI Desktop

Power BI Desktop: una aplicación cliente diseñada para Power BI desarrollo: puede usarse para desarrollar un modelo que es realmente un modelo tabular Analysis Services. Los modelos se pueden desarrollar mediante la importación de datos de flujos de datos, que luego se pueden integrar con otros orígenes de datos. Aunque los detalles sobre cómo se puede lograr el modelado se encuentran fuera del ámbito de este documento, es importante comprender que hay tres tipos o modos de modelos que se pueden desarrollar mediante Power BI Desktop. Estos modos determinan si los datos se importan en el modelo o si permanecen en el origen de datos. Los tres modos son: Import, DirectQuery y composite. En el tema [modos de almacenamiento de modelos](#model-storage-modes) se explicará una discusión completa de cada modo.

Los modelos y modelos hospedados externamente desarrollados en Power BI Desktop pueden aplicar seguridad de nivel de fila (RLS) para limitar los datos que se pueden recuperar para un usuario determinado. Por ejemplo, los usuarios asignados al grupo de seguridad vendedores solo pueden ver los datos del informe para las regiones de ventas a las que están asignados. Los roles RLS pueden ser dinámicos o estáticos. Los **Roles dinámicos** los filtra el usuario del informe, mientras que los **roles estáticos** aplican los mismos filtros a todos los usuarios asignados al rol.

##### <a name="excel-workbook-models"></a>Modelos de libros de Excel

La creación de conjuntos de valores basados en libros de Excel o en archivos CSV producirá la creación automática de un modelo. Las tablas de Excel y los datos CSV se importarán para crear tablas de modelo, mientras que un modelo de datos del libro de Excel se transpondrá para crear un modelo de Power BI. En todos los casos, los datos de archivo se importan en un modelo.

A continuación, se pueden realizar distinciones sobre Power BI conjuntos de valores que representan modelos:

- Se hospedan en el servicio Power BI o se hospedan externamente en Analysis Services
- Pueden almacenar datos importados o pueden emitir solicitudes de consulta de paso a través a los orígenes de datos subyacentes, o bien una combinación de ambos.

A continuación se muestra un resumen de los datos importantes sobre Power BI conjuntos de datos que representan modelos:

- SQL Server Analysis Services modelos hospedados requieren una puerta de enlace para realizar consultas de LC
- Modelos hospedados en Power BI que importan datos
  - Se debe cargar por completo en la memoria para que se puedan consultar
  - Requerir actualización para mantener los datos actualizados y debe incluir puertas de enlace cuando no se pueda acceder a los datos de origen directamente a través de Internet
- Los modelos hospedados en Power BI que usan el modo de almacenamiento DirectQuery (DQ) requieren conectividad con los datos de origen. Cuando se consulta el modelo, Power BI emite consultas a los datos de origen para recuperar los datos actuales. Este modo debe implicar puertas de enlace cuando no se puede tener acceso a los datos de origen directamente a través de Internet.
- Los modelos pueden aplicar reglas RLS y aplicar filtros para limitar el acceso a los datos a determinados usuarios.

Para implementar y administrar correctamente Power BI Premium, es importante comprender dónde se hospedan los modelos, el modo de almacenamiento, las dependencias de las puertas de enlace, el tamaño de los datos importados y el tipo y la frecuencia de actualización. Esto puede tener un impacto significativo en los recursos de Power BI Premium. Además, el diseño del modelo, incluidos sus consultas y cálculos de preparación de datos, puede agregarse a la combinación de consideraciones.

También es importante comprender que los modelos de importación hospedados en Power BI se pueden actualizar de acuerdo con la programación o ser desencadenados a petición por un usuario en el servicio Power BI.

El diseño de modelos optimizados se describe más adelante en este documento técnico en el tema [optimización de modelos](#optimizing-models) .

#### <a name="workbooks"></a>Libros

Power BI los libros son un tipo de contenido de Power BI \[[4](#endnote-04)\]. Son libros de Excel que se han cargado en el servicio Power BI y no se deben confundir con libros de Excel cargados que crean conjuntos de valores (modelos). El tipo de contenido del libro representa una conexión a un libro, que puede cargarse en el servicio Power BI o permanecer en el almacenamiento en nube en OneDrive o SharePoint Online.

Es importante comprender que este tipo de contenido no está disponible como origen de datos para Power BI visualizaciones de datos. En su lugar, se puede abrir como un libro en el servicio Power BI mediante Excel online. La intención principal de este tipo de contenido es permitir el acceso a los informes de libros de Excel heredados desde el servicio Power BI y permitir que las visualizaciones de datos se anclen en Power BI paneles.

Para obtener más información, consulte el documento [obtener datos de archivos de libro de Excel](service-excel-workbook-files.md) .

#### <a name="reports"></a>Informes

Hay dos tipos de informes: Power BI informes y los informes paginados.

**Power BI informes** proporcionan experiencias de visualización de datos interactivas que se conectan a un único conjunto de datos. A menudo, los informes se diseñan para favorecer la participación de los usuarios, lo que les permite interactuar con una gran variedad de funcionalidades, como el filtrado, la segmentación, el filtrado cruzado y el resaltado, la obtención de detalles, el análisis, la obtención de detalles, la & un Preguntas sobre el lenguaje, enfoque, navegación de páginas, Spotlight, visualización de marcadores, etc.

En el contexto de estas notas del producto, es importante comprender cómo la arquitectura de Power BI, Power BI el diseño de informes y las interacciones de usuario pueden afectar a los recursos de servicio Power BI:

- Para cargar informes e interactuar con ellos en función de los modelos de importación, el modelo se debe cargar por completo en la memoria (ya sea hospedado en el servicio Power BI u hospedado externamente).
- Cada informe visual emite una consulta para recuperar datos consultando el modelo
- Por lo general, las interacciones de filtro y segmentación implican la consulta del modelo. Por ejemplo, si se cambia una selección de segmentación, de forma predeterminada, será necesario volver a cargar cada uno de los objetos visuales de la página \[[5](#endnote-05)\]
- Power BI informes no garantizan la visualización de los datos actuales y puede requerir que el usuario actualice el informe para volver a cargar la página del informe y sus objetos visuales
- Los usuarios pueden interactuar con la función Q & una característica de lenguaje natural para formular preguntas, y proporcionar el Power BI diseño del informe permite y el conjunto de datos representa un modelo de importación de datos hospedado en Power BI o un conjunto de datos de LC configurado para habilitar Q & a

**Informes paginados** que permiten la publicación y representación de informes de SQL Server Reporting Services (SSRs) (formato\*. rdl). Como sugiere su nombre, los informes paginados suelen usarse cuando los requisitos exigen una necesidad de impresión en un tamaño de página fijo, o cuando hay listas de variables de datos que deben expandirse por completo. Por ejemplo, una factura diseñada para la representación de varias páginas (en lugar de desplazarse dentro de un visual) e imprimir.

Los dos tipos de informes admitidos proporcionan la opción para los autores de informes, permitiéndoles seleccionar el tipo en función de los requisitos y el uso previsto. Por lo general, los informes de Power BI son ideales para experiencias interactivas que permiten al usuario explorar y descubrir información de los datos, mientras que los informes paginados son más adecuados para los diseños de página controlados por parámetros.

Independientemente del tipo de informe, lograr una carga de informes y actualizaciones de datos que respondan (cuando se cambian los filtros o los parámetros) es fundamental para ofrecer una experiencia de usuario confiable y con un rendimiento óptimo.

#### <a name="dashboards"></a>Paneles

Power BI paneles están diseñados para ofrecer experiencias de supervisión y son conceptualmente diferentes de Power BI informes. Los paneles están diseñados para mostrarse en un único panel de cristal para expresar valores y visualizaciones de datos en mosaicos. Por lo general, los paneles ofrecen menos experiencias de interacción que Power BI informes, con algunos diseños de paneles que no esperan ninguna interacción. Por ejemplo, un panel desatendido se presenta en una pantalla no táctil en una sala de servidores. Otra diferencia importante es que los paneles pueden presentar mosaicos que incluyen datos de origen de varios conjuntos de datos, mientras que un informe de Power BI solo puede basarse en un único conjunto de datos.

Es importante comprender que un panel está diseñado para cargarse rápidamente y expresar en todo momento los datos más actuales (conocidos por el servicio Power BI). Consigue esto mediante el almacenamiento en caché de los resultados de la consulta de mosaico y lo hace para cada panel. De hecho, debe hacerlo para cada usuario que tenga acceso a un panel basado en modelos que apliquen RLS dinámico.

El servicio Power BI actualiza automáticamente las cachés de consultas del panel inmediatamente después de que se actualicen los modelos de importación hospedados en Power BI. En el caso de los modelos LC y DQ, el propietario del conjunto de los mismos tiene un grado de control sobre la frecuencia con que el servicio Power BI actualiza la memoria caché, que se puede configurar con la frecuencia que sea cada 15 minutos o con una frecuencia de una vez por semana. Tenga en cuenta que las actualizaciones de la caché de consultas de LC primero consultarán los metadatos del modelo para determinar si se ha llevado a cabo una actualización del modelo desde la última actualización de la memoria caché y no continuarán con la actualización de la memoria caché cuando no se haya producido una actualización. Esta comprobación no es posible para los modelos de DQ y, por tanto, se producirán actualizaciones de caché si los datos de origen han cambiado o no.

Las actualizaciones de la caché de consultas de panel basadas en los modelos DQ y LC pueden afectar significativamente a los recursos de servicio Power BI y los orígenes de datos externos. Considere la posibilidad de usar un panel con 20 iconos, todo ello basado en un modelo de Azure Analysis Services que aplique RLS dinámico y que se actualice cada hora, y que este panel se comparta con 100 usuarios. Si el conjunto de resultados está configurado para actualizarse cada hora, se generarán al menos 2000 (20 x 100) consultas LC. Esto podría suponer una carga enorme en el servicio Power BI y los orígenes de datos externos, y también podría superar los límites impuestos en los recursos disponibles. Los recursos de capacidad y los límites se describen en el tema [capacidad nodos](#capacity-nodes) .

Los usuarios pueden interactuar con un panel de varias maneras, que requieren servicio Power BI recursos. En concreto, pueden:

- Desencadenar una actualización de los iconos de paneles, lo que puede dar lugar a una actualización a petición de todos los modelos de importación de datos hospedados en Power BI relacionados
- Póngase en contacto con el & de preguntas más frecuentes sobre el lenguaje natural para formular preguntas (el diseño del panel lo permite y el conjunto de datos es un modelo de importación de datos hospedado en Power BI o un conjunto de datos de LC configurado para habilitar Q & A).
- Use la característica Conclusiones rápidas para tener Power BI detectar información a partir de un conjunto de datos subyacente y responder con objetos visuales que los muestran y describen (siempre que el mosaico se base en un conjunto de datos hospedado Power BI modelo de importación de datos).
- Configure alertas en los iconos del panel, lo que requiere que el servicio Power BI Compare los umbrales con los valores de mosaico, posiblemente con la misma frecuencia que cada hora, y para notificar a los usuarios cuando se superan los umbrales (siempre que el icono muestre un único valor numérico y se base en un conjunto de datos que se Power BI modelo de importación de datos hospedado)

### <a name="model-storage-modes"></a>Modos de almacenamiento de modelos

Recuerde que Power BI Desktop permite desarrollar un modelo en uno de tres modos. Es importante comprender la lógica de cada modo de almacenamiento del modelo de datos y los posibles impactos en los recursos de servicio Power BI. En esta sección se presentan los tres modos. Estos se tratarán con más detalle más adelante en esta nota del producto en el tema optimización de modelos.

#### <a name="import-mode"></a>Modo de importación

El modo de importación es el modo más común que se usa para desarrollar modelos debido al rendimiento extremadamente rápido asociado a las consultas en memoria, la flexibilidad de diseño disponible para los modeladores y la compatibilidad con capacidades de servicio Power BI específicas (Q & A, Conclusiones rápidas , etc.). Es el modo predeterminado al crear una nueva solución de Power BI Desktop.

Es importante comprender que los datos importados siempre se almacenan en el disco y deben estar totalmente cargados en la memoria para ser consultados o actualizados. Una vez en la memoria, los modelos de importación alcanzan resultados de consultas increíblemente rápidos. También es importante entender que no hay ningún concepto de un modelo de importación que se cargue parcialmente en la memoria.

Cuando se actualizan, los datos se comprimen y optimizan y luego se almacenan en el disco mediante el motor de almacenamiento de VertiPaq. Cuando se carga desde el disco en la memoria, es posible ver la compresión 10x y, por lo tanto, es razonable esperar que 10 GB de datos de origen se puedan comprimir a aproximadamente 1 GB de tamaño. El tamaño de almacenamiento en disco puede lograr una reducción del 20% sobre esto. \[[6](#endnote-06)\]

La flexibilidad de diseño se puede lograr de tres maneras. Los modeladores de datos pueden:

- Integración de datos mediante el almacenamiento en caché de datos de varios orígenes de datos, independientemente del tipo de origen de datos y el formato
- Aproveche el conjunto completo de funciones del lenguaje de fórmulas de Power Query (informadamente conocido como M) al crear consultas de preparación de datos.
- Aprovechar todo el conjunto de funciones de expresiones de análisis de datos (DAX) al mejorar el modelo con lógica de negocios, así como columnas calculadas, tablas calculadas y medidas

Como se muestra en la siguiente imagen, un modelo de importación puede integrar datos de cualquier número de tipos de orígenes de datos admitidos.

![Un modelo de importación puede integrar datos de cualquier número de tipos de orígenes de datos admitidos.](media/whitepaper-premium-deployment/import-model.png)

Sin embargo, aunque hay ventajas interesantes asociadas con los modelos de importación, también hay desventajas:

- El modelo completo se debe cargar en la memoria antes de que Power BI pueda consultar el modelo, lo que puede poner presión sobre los recursos disponibles a medida que aumentan el número y el tamaño de los modelos.
- Los datos del modelo solo son tan actuales como la actualización más reciente, por lo que es necesario actualizar los modelos de importación, preferiblemente de forma programada.
- Una actualización completa quitará todos los datos de todas las tablas y los volverá a cargar desde el origen de datos. Esto puede resultar muy caro en cuanto a tiempo y recursos para el servicio Power BI y los orígenes de datos. Power BI es compatible con la actualización incremental, lo que puede evitar truncar y volver a cargar tablas enteras, y esto se trata en el tema [optimización de modelos hospedados Power BI](#optimizing-power-bi-hosted-models) .

Desde una perspectiva de recursos servicio Power BI, los modelos de importación requieren:

- Memoria suficiente para cargar el modelo cuando se consulta o se actualiza
- Procesamiento de recursos y recursos de memoria adicionales para actualizar datos

#### <a name="directquery-mode"></a>Modo DirectQuery

Los modelos desarrollados en el modo DirectQuery (DQ) no importan datos. En su lugar, solo se componen de metadatos que, cuando se consultan, emite consultas nativas al origen de datos subyacente.

![Un modelo DirectQuery emite consultas nativas al origen de datos subyacente.](media/whitepaper-premium-deployment/direct-query-model.png)

Hay dos razones principales para considerar el desarrollo de un modelo DQ. La primera razón es que los volúmenes de datos son demasiado grandes, incluso cuando se aplican métodos de reducción de datos, para cargarlos en un modelo o actualizarse prácticamente. La segunda razón es que los informes y los paneles deben proporcionar datos "casi en tiempo real", más allá de lo que se puede lograr dentro de los límites de actualización programados (48 veces al día para una capacidad dedicada).

Hay varias ventajas asociadas a los modelos DQ:

- No se aplican los límites de tamaño del modelo de importación
- No es necesario actualizar los modelos
- Los usuarios de informes verán los datos más recientes al interactuar con filtros y segmentaciones de informes, y pueden actualizar todo el informe para recuperar los datos actuales.
- Los iconos del panel, cuando se basan en los modelos DQ, pueden actualizarse automáticamente con la frecuencia que sea cada 15 minutos.

Sin embargo, hay numerosas desventajas y limitaciones asociadas a los modelos de DQ:

- El modelo debe basarse en un único origen de datos compatible y, por lo tanto, la integración de datos ya debe realizarse en el origen de datos. Los orígenes de datos admitidos son sistemas relacionales y de análisis, con compatibilidad para muchos almacenes de datos populares \[[7](#endnote-07)\].
- El rendimiento puede ser lento, podría afectar negativamente en el servicio Power BI (las consultas pueden tener un uso intensivo de la CPU) y en el origen de datos (que puede no estar optimizado para las consultas de análisis).
- Power Query consultas no pueden ser demasiado complejas y están limitadas a M expresiones y funciones que se pueden transponer en consultas nativas entendidas por el origen de datos
- Las funciones DAX se limitan a las que se pueden transponer en consultas nativas entendidas por el origen de datos y no son compatibles con las tablas calculadas o las capacidades integradas de inteligencia de tiempo.
- De forma predeterminada, se producirá un error en las consultas de modelo que requieren recuperación de más de 1 millón filas
- Los informes y paneles con varios objetos visuales pueden mostrar resultados incoherentes, especialmente cuando el origen de datos es volátil
- P & A y Conclusiones rápidas no se admiten

Desde una perspectiva de recursos servicio Power BI, los modelos DQ requieren:

- Memoria mínima para cargar el modelo (solo metadatos) cuando se consulta
- A veces, recursos de procesador significativos para generar y procesar consultas enviadas al origen de datos

Para obtener más información, consulte el documento [uso de la consulta directa en Power BI Desktop](desktop-use-directquery.md) .

#### <a name="composite-mode"></a>Modo compuesto

Los modelos desarrollados en modo compuesto permiten configurar el modo de almacenamiento para tablas de modelo individuales. Por lo tanto, admite una combinación de tablas de importación y DQ. También admite tablas calculadas (definidas con DAX) y varios orígenes de datos DQ.

El modo de almacenamiento de tabla se puede configurar como Import, DirectQuery o dual. Una tabla configurada como modo de almacenamiento dual es Import y DirectQuery, y esto permite a la servicio Power BI determinar el modo más eficaz que se va a usar en una consulta por consulta.

![Un modelo compuesto es una combinación de modos de almacenamiento de importación y DQ, configurado en el nivel de tabla](media/whitepaper-premium-deployment/composite-model.png)

Los modelos compuestos se esfuerzan por ofrecer lo mejor de los modos de importación y DirectQuery. Cuando se configuran correctamente, pueden combinar el alto rendimiento de las consultas de los modelos en memoria con la capacidad de recuperar datos casi en tiempo real de los orígenes de datos.

Es probable que los modelos de datos que desarrollan modelos compuestos configuren tablas de tipo dimensión en el modo de importación o de almacenamiento dual y en las tablas de tipo de hecho en el modo DirectQuery. Por ejemplo, considere un modelo con una tabla de tipo dimensión de producto en modo dual y una tabla de tipo de hecho de ventas en el modo DirectQuery. La tabla de productos se puede consultar eficaz y rápidamente desde en memoria para representar una segmentación de informes. A continuación, la tabla sales se puede consultar en el modo DirectQuery, unida a la tabla Product relacionada. Esta última consulta podría permitir la generación de una única consulta nativa eficaz para combinar las tablas Product y sales y filtrar por los valores de la segmentación.

En general, se pueden considerar las ventajas y desventajas asociadas a cada modo de modelo para que se apliquen al modo de almacenamiento de tabla en los modelos compuestos.

Para obtener más información, consulte el documento [uso de modelos compuestos en Power BI Desktop](desktop-composite-models.md) .

### <a name="licensing"></a>Administración de licencias

Power BI tiene tres licencias:

- Power BI gratuito
- Power BI Pro
- Power BI Premium

La licencia **gratuita de Power BI** permite que una persona inicie sesión en el servicio Power BI y trabaje dentro de su área de trabajo personal publicando modelos e informes. Es importante entender que no es posible compartir el contenido de Power BI mediante esta licencia. Esta licencia, como sugiere su nombre, es gratuita.

La licencia de **Power Bi Pro** permite a un individuo crear y colaborar en áreas de trabajo y compartir y distribuir contenido de Power BI. También pueden configurar la actualización de los conjuntos de datos para mantener los datos actualizados automáticamente, incluidos los orígenes de datos locales. Además, pueden auditar y controlar cómo se obtiene acceso a los datos y cómo se usan. Esta licencia es necesaria para recibir contenido compartido de otros usuarios a menos que el usuario esté asociado a una Power BI Premium capacidad dedicada.

La licencia **Power BI Premium** es una licencia de nivel de inquilino y se describe en la sección [Introducción a Power BI Premium](#introducing-power-bi-premium) .

Para obtener más información acerca de las licencias de Power BI, consulte la página de [precios de Power BI](https://powerbi.microsoft.com/pricing/) .

## <a name="introducing-power-bi-premium"></a>Presentación de Power BI Premium

Power BI Premium ofrece una plataforma de BI empresarial y de autoservicio unificada con escalado, rendimiento confiable y costos predecibles. Esto lo consigue principalmente proporcionando recursos dedicados para ejecutar el servicio Power BI para su organización.

Además, Power BI Premium ofrece muchas características empresariales:

- Distribución de contenido rentable, que permite compartir contenido de Power BI con usuarios gratuitos Power BI gratis, incluidos los usuarios externos
- Compatibilidad con tamaños de conjunto de DataSet mayores \[[8](#endnote-08)\]
- Mayores tasas de actualización de flujos de entrada y conjuntos de valores (hasta 48 veces al día)
- Actualización incremental de flujos de entrada y conjuntos de valores
- Entidades vinculadas de flujo de entrada y ejecución en paralelo de transformaciones
- Informes paginados
- Power BI Report Server, para informes locales
- Capacidad para insertar contenido en aplicaciones en nombre de usuarios de la aplicación (PaaS)

Muchas de estas características se pueden aprovechar para ofrecer soluciones empresariales eficientes y escalables y se describen en la sección optimización de las [capacidades Premium](#optimizing-premium-capacities) .

### <a name="subscriptions-and-licensing"></a>Suscripciones y licencias

Power BI Premium es una suscripción de Office 365 de nivel de inquilino disponible en dos familias de SKU (referencia de almacén):

- **Em** SKU (EM1-EM3) para la inserción, que requiere un compromiso anual, facturado mensualmente
- SKU **P** (P1-P3) para la inserción y las características empresariales, que requieren un compromiso mensual o anual, facturado mensualmente e incluye una licencia para instalar Power BI Report Server de forma local

Un enfoque alternativo es adquirir una suscripción de Azure Power BI Embedded que tenga una sola familia de SKU: **una** SKU (a1-A6) para la inserción y pruebas de capacidad únicamente.

Todas las SKU ofrecen núcleos virtuales para crear capacidades \[[9](#endnote-09)\], pero las SKU EM están restringidas para la incrustación a menor escala. Aunque este documento se centra en las SKU P, gran parte de lo que se trata también es pertinente para las SKU.

A diferencia de las SKU de suscripción Premium, las de Azure no requieren ningún compromiso de tiempo y se facturan por hora. Ofrecen elasticidad completa que permite escalar y reducir verticalmente, pausar, reanudar y eliminar.

En gran medida, Azure Power BI Embedded está fuera del ámbito de este documento, pero se describe en el tema sobre los enfoques de pruebas como una opción práctica y económica para probar y medir cargas de trabajo.

Para más información sobre las SKU de Azure, consulte la [documentación de azure Power BI Embedded](/azure/power-bi-embedded/).

Los administradores compran las suscripciones de Power BI Premium en el Centro de administración de Microsoft 365. En concreto, solo los administradores globales de Office 365 o los administradores de facturación pueden comprar SKU.

Una vez comprada, el inquilino recibe un número correspondiente de núcleos virtuales para asignar a las capacidades; esto se conoce como **agrupación de núcleos de v**. Por ejemplo, la compra de una SKU P3 proporciona al inquilino 32 núcleos virtuales.

Para obtener más información, consulte la [compra de Power BI Premium](service-admin-premium-purchase.md) documento.

### <a name="premium-capacities"></a>Capacidades Premium

A diferencia de una capacidad compartida en la que las cargas de trabajo se ejecutan en recursos computacionales compartidos con otros clientes, una **capacidad dedicada** es para uso exclusivo de una organización. Está aislado con recursos informáticos dedicados que proporcionan un rendimiento confiable y coherente para el contenido hospedado.

Este documento se centra en la **capacidad Premium** , lo que significa que está asociada con cualquiera de las SKU em o P.

#### <a name="capacity-nodes"></a>Nodos de capacidad

Tal y como se describe en el tema suscripciones y licencias, hay dos familias Power BI Premium SKU: EM y P. Todas las SKU de Power BI Premium están disponibles como nodos de capacidad, cada uno de los cuales representa una cantidad establecida de recursos que se componen del procesador, la memoria y el almacenamiento. Además de los recursos, cada SKU tiene límites operativos sobre el número de conexiones de DirectQuery (DQ) y conexión dinámica (LC) por segundo y el número de actualizaciones de modelos en paralelo.

El procesamiento se consigue mediante un número determinado de núcleos virtuales, que se divide por igual entre el back-end y el front-end.

Los **núcleos virtuales de back-end** son responsables de funciones básicas de Power BI, como el procesamiento de consultas, la administración de caché, la ejecución de servicios R, la actualización del modelo, el procesamiento de lenguaje natural (Preguntas y respuestas) y la representación de informes e imágenes en el lado servidor. Los núcleos virtuales de back-end tienen asignada una cantidad de memoria fija que es la principal que se usa para hospedar modelos que también se conocen como conjuntos de valores activos.

Los **núcleos** virtuales de front-end son responsables del servicio Web, la administración de documentos de panel y de informes, la administración de derechos de acceso, la programación, las API, las cargas y descargas y, por lo general, de todo lo relacionado con las experiencias de usuario.

Storage se establece en 100 TB por nodo de capacidad.

En la tabla siguiente se describen los recursos y los límites de cada SKU Premium (y con un tamaño equivalente A una SKU).

| Nodos de capacidad | Total de núcleos virtuales | Núcleos virtuales de back-end | RAM (GB) | Núcleos virtuales de front-end | DQ/LC (por segundo) | Paralelismo de actualización de modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 3 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

#### <a name="capacity-workloads"></a>Cargas de trabajo de capacidad

Las cargas de trabajo de capacidad son servicios disponibles para los usuarios. De forma predeterminada, las capacidades Premium y Azure solo admiten una carga de trabajo asociada a la ejecución de consultas Power BI que no se pueden deshabilitar.

Se pueden habilitar cargas de trabajo adicionales para informes paginados, flujos de trabajo e AI. Cada carga de trabajo adicional requiere la configuración de la memoria máxima (como porcentaje de la memoria total disponible) que puede usar la carga de trabajo.

#### <a name="how-capacities-function"></a>Cómo funcionan las capacidades

En todo momento, el servicio Power BI se esfuerza por hacer el mejor uso de los recursos de capacidad y no superar los límites impuestos en la capacidad.

Las operaciones de capacidad se clasifican como interactivas o en segundo plano. Las operaciones interactivas incluyen la representación de solicitudes y la respuesta a interacciones del usuario (filtrado, preguntas y respuestas, etc.). Por lo general, la consulta de modelos de importación tiene un uso intensivo de recursos de memoria, mientras que la consulta de modelos LC/DQ requiere una gran cantidad de CPU. Las operaciones en segundo plano incluyen las actualizaciones de flujos de datos y del modelo de importación, y el almacenamiento en caché de consultas de panel.

Es importante comprender que las operaciones interactivas siempre tienen prioridad sobre las operaciones en segundo plano para garantizar la mejor experiencia posible del usuario. Si no hay recursos suficientes, las operaciones en segundo plano se agregan a una cola para su procesamiento cuando se liberen los recursos. Las operaciones en segundo plano, como las actualizaciones del conjunto de los conjuntos de información y las funciones de AI, pueden detenerse en proceso intermedio por el servicio Power BI y agregarse a una cola.

Los modelos de importación deben estar totalmente cargados en la memoria para que se puedan consultar o actualizar. El servicio Power BI administra el uso de memoria mediante algoritmos sofisticados para garantizar el uso máximo de la memoria disponible y puede conseguir sobrecargar la capacidad: aunque es posible que una capacidad almacene muchos modelos de importación (hasta 100 TB por capacidad Premium), cuando su almacenamiento en disco combinado supera la memoria admitida (y se requiere memoria adicional para las consultas y la actualización), no se pueden cargar en la memoria al mismo tiempo.

Por tanto, los modelos de importación se cargan y se quitan de la memoria según el uso. Un modelo de importación se carga cuando se consulta (operación interactiva) y aún no se encuentra en memoria, o cuando se va a actualizar (operación en segundo plano).

La eliminación de un modelo de la memoria se conoce como **expulsión** y es una operación que Power BI puede realizar rápidamente en función del tamaño de los modelos. Si la capacidad no experimenta presión de memoria, los modelos simplemente se cargan en memoria y permanecerán allí. No obstante, \[[10](#endnote-10)\], cuando no haya suficiente memoria disponible para cargar un modelo, la servicio Power BI primero deberá liberar memoria. Libera memoria al detectar modelos que se han vuelto inactivos mediante la búsqueda de modelos que no se han usado en los últimos tres minutos \[[11](#endnote-11)\]y, después, expulsarlos. Si no hay ningún modelo inactivo para expulsar, el servicio Power BI busca los que se han cargado para las operaciones en segundo plano. Esto puede incluir la expulsión de cargas de trabajo en segundo plano, como la carga de trabajo de inteligencia artificial. Un último recurso, después de 30 segundos de intentos fallidos \[[11](#endnote-11)\], es que se produzca un error en la operación interactiva. En este caso, el usuario del informe recibe una notificación correcta del error con una sugerencia para intentarlo de nuevo en breve.

Es importante resaltar que la expulsión del conjunto de DataSet es un comportamiento normal y esperado. El objetivo es maximizar el uso de memoria mediante la carga y descarga de modelos cuyos tamaños combinados pueden superar la memoria disponible. Esto es así por diseño y es completamente transparente para los usuarios del informe. Las tasas de expulsión altas no significan necesariamente que la capacidad no tenga los recursos suficientes. Pero pueden convertirse en un problema si la capacidad de respuesta de la consulta o la actualización se ve afectada debido a las altas tasas de expulsión.

Las actualizaciones de los modelos de importación siempre hacen un uso intensivo de la memoria, ya que los modelos se deben cargar en la memoria y se necesita memoria adicional para el procesamiento. Una actualización completa puede usar aproximadamente el doble de memoria requerida por el modelo. Esto garantiza que el modelo se puede consultar incluso cuando se procesa (las consultas se envían al modelo existente, hasta que la actualización se ha completado y los nuevos datos del modelo están disponibles). Tenga en cuenta que la actualización incremental requerirá menos memoria y podría completarse más rápido, por lo que puede reducir considerablemente la presión de los recursos de capacidad. Las actualizaciones también pueden hacer un uso intensivo de la CPU para los modelos, especialmente aquellos con transformaciones complejas de Power Query, o bien tablas o columnas calculadas que son complejas o se basan en tablas de gran tamaño.

Actualizaciones similares a: requiere que el modelo se cargue en la memoria. Si no hay suficiente memoria, el servicio Power BI intentará expulsar los modelos inactivos, y si esto no es posible (porque todos los modelos estén activos), el trabajo de actualización se pone en cola. Las actualizaciones suelen ser muy intensivas en la CPU, incluso más que las consultas. Por este motivo, hay límites de capacidad en cuanto al número de actualizaciones simultáneas, que se establece en 1,5 veces el número de núcleos de virtuales de back-end, redondeado al alza. Si hay demasiadas actualizaciones simultáneas, una actualización programada se pondrá en cola. Cuando se producen estas situaciones, la actualización tarda más tiempo en completarse. Tenga en cuenta que las actualizaciones a petición (desencadenadas por una solicitud de usuario o una llamada API) se reintentarán tres veces \[[11](#endnote-11)\]y, después, producirán un error si aún no hay suficientes recursos.

## <a name="managing-power-bi-premium"></a>Administrar Power BI Premium

La administración de Power BI Premium implica adquirir suscripciones y crear, administrar y supervisar capacidades Premium.

### <a name="creating-and-managing-capacities"></a>Crear y administrar capacidades

La página Configuración de la **capacidad** del portal de **Administración de Power BI** muestra el número de núcleos virtuales adquiridos y disponibles (es decir, que todavía se asignan a una capacidad) y enumera las capacidades Premium. La página permite a los administradores globales de Office 365 o a los administradores de servicio Power BI crear capacidades Premium a partir de núcleos virtuales disponibles o modificar las capacidades Premium existentes.

Al crear una capacidad Premium, el administrador debe definir:

- Nombre de capacidad (único en el inquilino)
- Administradores de capacidad
- Tamaño de capacidad
- Región para la residencia de datos \[[12](#endnote-12)\]

Se debe asignar al menos un administrador de capacidad. Los usuarios asignados como administradores de capacidad pueden:

- Asignar áreas de trabajo a la capacidad
- Administrar permisos de usuario para agregar administradores de capacidad adicionales o usuarios con permisos de asignación (para permitirles asignar áreas de trabajo a la capacidad)
- Administrar cargas de trabajo, para configurar el uso máximo de memoria para los informes paginados y las cargas de trabajo de flujos de trabajo
- Reinicie la capacidad para restablecer todas las operaciones en caso de sobrecarga del sistema \[[13](#endnote-13)\]

Los administradores de capacidad no pueden tener acceso al contenido del área de trabajo (a menos que se les asigne explícitamente permisos de área de trabajo) y no tienen acceso a todas Power BI áreas de administración (a menos que se asignen explícitamente) como métricas de uso, registros de auditoría o configuración de inquilino Lo importante es que los administradores de capacidad no tienen permisos para crear capacidades nuevas ni para escalar las existentes. Además, se asignan por cada capacidad, asegurándose de que solo pueden ver y administrar las capacidades a las que están asignadas.

El tamaño de la capacidad debe seleccionarse en una lista disponible de opciones de SKU que está restringida por el número de núcleos virtuales disponibles en el grupo. Es posible crear varias capacidades a partir del grupo, que podría ser origen de una o varias SKU adquiridas. Por ejemplo, una SKU P3 (32 núcleos virtuales) se podría usar para crear tres capacidades: una P2 (16 núcleos virtuales) y dos P1 (2 x 8 núcleos virtuales). Se puede lograr un mayor rendimiento y escalado mediante la creación de capacidades de menor tamaño y este tema se describe en la sección optimización de las [capacidades Premium](#optimizing-premium-capacities) . En la imagen siguiente se muestra una configuración de ejemplo para la organización ficticia de Contoso que consta de cinco capacidades Premium (3 x P1 y 2 x P3) con cada una de las áreas de trabajo que contiene y varias áreas de trabajo en capacidad compartida.

![Una configuración de ejemplo para la organización ficticia Contoso](media/whitepaper-premium-deployment/contoso-organization-example.png)

Se puede asignar una capacidad Premium a una región distinta de la región de inicio del inquilino de Power BI, lo que proporciona control administrativo sobre qué centros de usuarios (dentro de las regiones geográficas definidas) reside Power BI contenido. \[[12](#endnote-12)\]

Los administradores del servicio Power BI y los administradores globales de Office 365 pueden modificar la capacidades Premium. En concreto, pueden:

- Cambie el tamaño de la capacidad para escalar verticalmente o reducir verticalmente los recursos. Sin embargo, no es posible degradar una SKU P a una SKU EM o actualizar a la inversa.
- Adición o eliminación de administradores de capacidad
- Agregar o quitar usuarios que tienen permisos de asignación
- Adición o eliminación de cargas de trabajo adicionales
- Cambiar regiones

Los permisos de asignación son necesarios para asignar un área de trabajo a una capacidad Premium específica. Los permisos se pueden conceder a toda la organización, a usuarios o grupos específicos.

De manera predeterminada, las capacidades Premium admiten cargas de trabajo asociadas con la ejecución de consultas de Power BI. También admite tres cargas de trabajo adicionales: **informes paginados**, **flujos**de trabajo e **AI**. Cada carga de trabajo requiere configurar la memoria máxima (como un porcentaje de la memoria total disponible) que puede usar la carga de trabajo. Es importante comprender que el aumento de las asignaciones de memoria máximas puede afectar al número de modelos activos que se pueden hospedar y al rendimiento de las actualizaciones.

La memoria se asigna de manera dinámica a los flujos de datos, pero se asigna de forma estática a los informes paginados. La razón para asignar estáticamente la memoria máxima es que los informes paginados se ejecutan dentro de un espacio contenido protegido de la capacidad. Se debe tener cuidado al establecer la memoria de los informes paginados, ya que se reduce la memoria disponible para cargar los modelos.

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Informes paginados | N/D | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo | 20 % predeterminado; 2,5 % mínimo |
| Flujos de datos | 20 % predeterminado; 8 % mínimo  | 20 % predeterminado; 4 % mínimo  | 20 % predeterminado; 2 % mínimo | 20 % predeterminado; 1 % mínimo  |
| INTELIGENCIA ARTIFICIAL | N/D | 20 % predeterminado; 20 % mínimo  | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo  |
| | | | | |

Es posible eliminar una capacidad Premium y no se eliminarán las áreas de trabajo y el contenido. En su lugar, se moverán las áreas de trabajo asignadas a la capacidad compartida. Cuando se crea la capacidad Premium en otra región, el área de trabajo se mueve a la capacidad compartida de la región de inicio.

### <a name="assigning-workspaces-to-capacities"></a>Asignación de áreas de trabajo a capacidades

Las áreas de trabajo pueden asignarse a una capacidad Premium en el**portal** de **Administración de Power BI**o-para un área de trabajo, en el panel del **área de trabajo** .

Los administradores de capacidad, así como los administradores globales de Office 365 o los administradores de servicio Power BI, pueden asignar áreas de trabajo en masa en el**portal**de **Administración de Power BI**. La asignación masiva se puede aplicar a:

- **Áreas de trabajo por usuarios** : todas las áreas de trabajo que pertenecen a esos usuarios, incluidas las áreas de trabajo personales, se asignan a la capacidad Premium. Esto incluirá la reasignación de áreas de trabajo cuando ya estén asignadas a una capacidad Premium diferente. Además, a los usuarios también se les asignan permisos de asignación de área de trabajo.

- **Áreas de trabajo específicas**
- **Las áreas de trabajo de toda la organización** : todas las áreas de trabajo, incluidas las áreas de trabajo personales, se asignan a la capacidad Premium. Además, todos los usuarios actuales y futuros tienen asignados permisos de asignación de área de trabajo. \[[14](#endnote-14)\]

Para agregar un área de trabajo a una capacidad Premium, puede usar el panel **Área de trabajo**, siempre que el usuario sea administrador de un área de trabajo y tenga permisos de asignación.

![Uso del panel Área de trabajo para asignar un área de trabajo a una capacidad Premium](media/whitepaper-premium-deployment/assign-workspace-capacity.png)

Los administradores del área de trabajo pueden quitar un área de trabajo de una capacidad (en una capacidad compartida) sin requerir el permiso de asignación. Al quitar áreas de trabajo de capacidades dedicadas, se reubica de manera eficaz el área de trabajo en una capacidad compartida. Tenga en cuenta que quitar un área de trabajo de una capacidad Premium puede tener consecuencias negativas como, por ejemplo que el contenido compartido no esté disponible para los usuarios con licencias gratuitas de Power BI o la suspensión de una actualización programada cuando se excedan las provisiones que admiten las capacidades compartidas.

En el servicio Power BI, un área de trabajo asignada a una capacidad Premium se identifica fácilmente con el icono de diamante que aparece en el nombre del área de trabajo.

![Identificación de un área de trabajo asignada a una capacidad Premium](media/whitepaper-premium-deployment/premium-diamond-icon.png)

### <a name="monitoring-capacities"></a>Capacidades de supervisión

La supervisión de las capacidades Premium proporciona a los administradores una descripción del funcionamiento de las capacidades. Las capacidades se pueden supervisar mediante el [Power BI Premium aplicación de métricas de capacidad](service-admin-premium-monitor-capacity.md) o el [portal de administración de Power BI](service-admin-premium-monitor-portal.md).

#### <a name="interpreting-metrics"></a>Interpretar métricas

Las métricas se deben supervisar para entender detalladamente el uso de los recursos y la actividad de las cargas de trabajo. Si la capacidad se ralentiza, es importante entender cuáles son las métricas que se deben supervisar y las conclusiones que puede sacar.

Idealmente, las consultas se deben completar en un segundo para brindar experiencias con capacidad de respuesta a los usuarios de los informes y permitir un mayor rendimiento de las consultas. Por lo general, es menos preocupante cuando los procesos en segundo plano (incluidas las actualizaciones) tardan más tiempo en completarse.

Por lo general, los informes lentos pueden ser indicio de una capacidad sobrecalentada. Cuando no se cargan los informes, es señal de que se sobrecalentó una capacidad. En cualquier caso, la causa principal se podría atribuir a muchos factores, entre los que se incluyen:

- Las **consultas con error** que, ciertamente, indican la presión de memoria y que un modelo no se podría cargar en la memoria. El servicio Power BI intentará cargar un modelo durante 30 segundos antes de que se produzca un error.

- Los **tiempos de espera de consulta excesivos** se pueden deber a distintos motivos:
  - La necesidad de que la servicio Power BI deshaga primero los modelos y, a continuación, cargue el modelo de consulta que se va a consultar (Recuerde que las tasas de expulsión de conjunto de elementos más altas por sí mismas no son una indicación de la tensión de la capacidad, a menos que vayan acompañados de tiempos de espera de consulta largos que indiquen hiperpaginación)
  - Tiempos de carga del modelo (especialmente la espera para cargar un modelo grande en la memoria)
  - Consultas de ejecución prolongada
  - Demasiadas conexiones LC\DQ (que superen los límites de capacidad)
  - Saturación de CPU
  - Diseños de informes complejos con un número excesivo de objetos visuales en una página (Recuerde que cada visual es una consulta)
- Las **consultas de larga duración** pueden indicar que los diseños de modelos no están optimizados, especialmente cuando hay varios conjuntos de datos activos en una capacidad y solo un conjunto de datos genera que las consultas sean de larga duración. Esto sugiere que la capacidad tiene los recursos suficientes y que el conjunto de datos en cuestión no es óptimo o es simplemente lento. Las consultas de larga duración pueden ser problemáticas porque pueden bloquear el acceso a los recursos que otros procesos requieren.
- Los tiempos de espera de **actualización prolongada o los tiempos de espera** de la llamada de AI indican memoria insuficiente debido a muchos modelos activos que consumen memoria, o que una actualización problemática está bloqueando otras actualizaciones (que superen los límites de actualización en paralelo).

A continuación se incluye una explicación más detallada de cómo usar las métricas en la sección optimización de las [capacidades Premium](#optimizing-premium-capacities) .

## <a name="optimizing-premium-capacities"></a>Optimizar las capacidades Premium

Cuando surgen problemas de rendimiento de la capacidad Premium, un primer enfoque común es optimizar o optimizar las soluciones ya implementadas para restaurar los tiempos de respuesta aceptables. La lógica de reemplazo consiste en evitar la compra de capacidad Premium adicional, a menos que se pueda justificar.

Cuando se necesita más capacidad Premium, hay dos opciones que se tratarán más adelante en esta sección:

- Escale verticalmente la capacidad Premium
- Adición de una capacidad Premium nueva

Por último, la evaluación de los enfoques y el tamaño de la capacidad Premium concluyerán esta sección.

### <a name="general-best-practices"></a>Procedimientos recomendados generales

A la hora de lograr un mejor uso y rendimiento, hay algunas prácticas recomendadas que se pueden tomar en el panel como recomendaciones generales. Estas incluyen:

- Usar áreas de trabajo en lugar de áreas de trabajo personales
- Separación de inteligencia empresarial crítica y de autoservicio (SSBI) en capacidades diferentes

  ![Separación de inteligencia empresarial de autoservicio y crítica para la empresa en diferentes capacidades](media/whitepaper-premium-deployment/separate-capacities.png)

- Si comparte contenido solo con usuarios de Power BI Pro, puede que no sea necesario almacenar el contenido en una capacidad dedicada.
- Utilice capacidades dedicadas al buscar un tiempo de actualización específico o cuando se requieran características específicas, como grandes conjuntos de información o informes paginados.

### <a name="addressing-common-questions"></a>Solucionar preguntas comunes

La optimización de las implementaciones de Power BI Premium es un tema complejo que implica una comprensión de los requisitos de carga de trabajo, los recursos disponibles y su uso eficaz.

En este tema se abordan siete preguntas de soporte técnico comunes, en las que se describen posibles problemas y explicaciones, así como información sobre cómo identificarlos y resolverlos.

#### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>¿Por qué la capacidad es lenta y qué puedo hacer?

Hay muchas razones que pueden contribuir a la lentitud de una capacidad Premium. Esta pregunta requiere más información para comprender lo que se entiende por lentitud. ¿Los informes tardan en cargarse? ¿O bien no se pueden cargar? ¿Los objetos visuales de informes tardan en cargarse o actualizarse cuando los usuarios interactúan con el informe? ¿Las actualizaciones tardan más en completarse de lo esperado o antes?

Una vez que se entiende el motivo, puede empezar a investigar. Las respuestas a las seis preguntas siguientes le ayudarán a abordar problemas más específicos.

#### <a name="what-content-is-using-up-my-capacity"></a>¿Qué contenido está usando mi capacidad?

Puede usar la aplicación **Métricas de capacidad de Power BI Premium** para filtrar por capacidad y revisar las métricas de rendimiento del contenido del área de trabajo. Es posible revisar las métricas de rendimiento y el uso de recursos por hora durante los últimos siete días para todo el contenido almacenado dentro de una capacidad Premium. Este suele ser el primer paso a la hora de solucionar problemas generales relacionados con el rendimiento de la capacidad Premium.

Entre las métricas clave que se deben supervisar se incluyen las siguientes:

- Promedio de CPU y recuento de uso elevado
- Promedio de memoria y recuento de uso elevado, y uso de memoria para conjuntos de información, flujos de DataFlow e informes paginados específicos
- Conjuntos de valores activos cargados en memoria
- Duración media y máxima de la consulta
- Promedio de tiempos de espera de consulta
- Tiempo medio de actualización de los conjuntos de
- Tiempos promedio de llamadas y tiempos de espera de AI

Además, en la aplicación Power BI Premium de métricas de capacidad, la memoria activa muestra la cantidad total de memoria asignada a un informe que no se puede desalojar porque está en uso en los últimos tres minutos. Un pico elevado en el tiempo de espera de actualización podría estar relacionado con un conjunto de datos grande o activo.

En el gráfico "5 principales por duración media" se resaltan los cinco conjuntos de elementos principales, los informes paginados, los flujos de entrada y las llamadas a AI que consumen recursos de capacidad. El contenido de las cinco primeras listas son candidatos para la investigación y la posible optimización.

#### <a name="why-are-reports-slow"></a>¿Por qué son lentos los informes?

En las tablas siguientes se muestran los posibles problemas y maneras de identificarlos y administrarlos.

##### <a name="insufficient-capacity-resources"></a>Recursos de capacidad insuficientes

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Gran cantidad de memoria activa total (el modelo no se puede desalojar porque está en uso en los últimos tres minutos)<br><br> Varios picos altos en los tiempos de espera de consulta<br><br> Varios picos altos en los tiempos de espera de actualización | Supervise las métricas de memoria \[[18](#endnote-18)\]y recuentos de expulsiones \[[19](#endnote-19)\] | Reducir el tamaño del modelo o convertirlo en el modo DirectQuery; consulte el tema sobre los [modelos de optimización](#optimizing-models) en esta sección.<br><br> Escalar verticalmente la capacidad<br><br> Asignar el contenido a una capacidad diferente |

##### <a name="inefficient-report-designs"></a>Diseños de informe ineficaces

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Las páginas de informe contienen numerosos objetos visuales (el filtrado interactivo puede desencadenar al menos una consulta por visual)<br><br> Los objetos visuales recuperan más datos de los necesarios | Revisar los diseños de informe<br><br> Entrevistar a los usuarios de informes para entender cómo interactúan con los informes<br><br> Supervisión de las métricas de consulta del conjunto de los \[[20](#endnote-20)\] | Rediseñar informes con menos objetos visuales por página |

##### <a name="dataset-slow-especially-when-reports-have-previously-performed-well"></a>Conjunto de informes lento (especialmente cuando los informes se han realizado correctamente)

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Volúmenes cada vez mayores de datos de importación<br><br> Lógica de cálculo compleja o ineficaz, incluidos los roles RLS<br><br> Modelo no totalmente optimizado<br><br> (DQ/LC) Latencia de puerta de enlace<br><br> Tiempos de respuesta de la consulta de origen DQ lenta | Revisar diseños de modelos<br><br> Supervisar contadores de rendimiento de puerta de enlace | Consulte el tema sobre los [modelos de optimización](#optimizing-models) en esta sección. |

##### <a name="high-concurrent-report-usage"></a>Uso elevado de informes simultáneos

| Explicaciones posibles | Cómo identificarlo | Cómo resolverlo |
| --- | --- | --- |
| Tiempos de espera de consulta elevados<br><br> Saturación de CPU<br><br> Se han superado los límites de conexión de DQ/LC | Supervisar el uso de CPU \[[21](#endnote-21)\], tiempos de espera de consulta y uso de DQ/LC \[[22](#endnote-22) métricas de\] y duraciones de consultas: Si la fluctuación puede indicar problemas de simultaneidad | Escalar verticalmente la capacidad o asignar el contenido a una capacidad diferente<br><br> Rediseñar informes con menos objetos visuales por página |

#### <a name="why-are-reports-not-loading"></a>¿Por qué no se cargan los informes?

Cuando los informes no se cargan, es un escenario en el peor de los casos, y se asegura de que la capacidad no tiene suficiente memoria y está sobrecalentada. Esto puede ocurrir cuando todos los modelos cargados se consultan de forma activa, por lo que no se pueden expulsar, y las operaciones de actualización se han pausado o retrasado. El servicio Power BI intentará cargar el conjunto de datos durante 30 segundos y el error se notificará al usuario de forma correcta con una sugerencia para que lo intente de nuevo en breve.

En la actualidad no existe ninguna métrica para supervisar los errores de carga de informes. Puede identificar la posibilidad de este problema si supervisa la memoria del sistema, en concreto el uso más alto y la hora de uso más alto. Los valores elevados de expulsiones de conjunto de datos y tiempo de espera promedio de actualización del conjunto de datos podrían sugerir que se está produciendo este problema.

Si esto solo sucede de forma ocasional, es posible que no se considere un problema prioritario. Se informa a los usuarios del informe de que el servicio está ocupado y que deben volver a intentarlo después de un breve período de tiempo. Si esto ocurre con demasiada frecuencia, el problema se puede resolver mediante el escalado vertical de la capacidad Premium o la asignación del contenido a otra capacidad.

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica **Errores de consulta** para determinar cuándo sucede esto. También pueden reiniciar la capacidad, y restablecer todas las operaciones en caso de sobrecarga del sistema.

#### <a name="why-are-refreshes-not-starting-on-schedule"></a>¿Por qué no se inician las actualizaciones según la programación?

Las horas de inicio de la actualización programada no están garantizadas. Recuerde que el servicio Power BI siempre dará prioridad a las operaciones interactivas sobre las operaciones en segundo plano. La actualización es una operación en segundo plano que se puede producir cuando se cumplen dos condiciones:

- Hay memoria suficiente
- No se supera el número de actualizaciones simultáneas admitidas para la capacidad Premium

Cuando no se cumplen las condiciones, la actualización se pone en cola hasta que las condiciones sean favorables.

Para una actualización completa, recuerde que al menos se requiere el doble del tamaño de la memoria del conjunto de datos actual. Si no hay suficiente memoria disponible, la actualización no se puede iniciar hasta que la expulsión del modelo libere memoria, lo que supone retrasos hasta que uno o varios conjuntos de datos queden inactivos y se puedan expulsar.

Recuerde que el número de actualizaciones simultáneas máximas que se admite se establece en 1,5 veces los núcleos virtuales de back-end, redondeado hacia arriba.

Se producirá un error en una actualización programada cuando no se pueda iniciar antes de que se inicie la siguiente actualización programada. Una actualización a petición desencadenada de forma manual desde la interfaz de usuario intentará ejecutarse hasta tres veces antes de que se produzca un error.

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica de **tiempo de espera promedio de actualización (minutos)** para determinar el retraso medio entre la hora programada y el inicio de la operación.

Aunque no suele ser una prioridad administrativa, para influir en las actualizaciones de datos puntuales, asegúrese de que haya suficiente memoria disponible. Esto puede implicar el aislamiento de los conjuntos de datos en capacidades con recursos suficientes conocidos. También es posible que los administradores se coordinen con los propietarios del conjunto de datos para ayudar a escalonar o reducir los tiempos de actualización de datos programados para minimizar las colisiones. Tenga en cuenta que un administrador no puede ver la cola de actualización ni recuperar las programaciones de conjunto de los conjuntos de programas.

#### <a name="why-are-refreshes-slow"></a>¿Por qué son lentas las actualizaciones?

Las actualizaciones pueden ser lentas o percibirse como tales (como se aborda en la pregunta común anterior).

Cuando la actualización es realmente lenta, puede deberse a varios motivos:

- CPU insuficiente (la actualización puede consumir mucha CPU)
- Memoria insuficiente, lo que produce una pausa de actualización (que requiere que la actualización se inicie de nuevo cuando las condiciones son favorables para reiniciarse)
- Razones que no son de capacidad, como la capacidad de respuesta del sistema de origen de datos, la latencia de red, permisos no válidos
- Volumen de datos: una buena razón para configurar la actualización incremental, como se describe a continuación

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica **Duración promedio de la actualización (minutos)** para determinar un banco de pruebas para la comparación en el tiempo, y la métrica **Tiempo de espera promedio de actualización (minutos)** para determinar el retraso medio entre la hora programada y el inicio de la operación.

La actualización incremental puede reducir significativamente la duración de la actualización de datos, especialmente en el caso de tablas de modelos grandes. Hay cuatro ventajas asociadas con la actualización incremental:

- Las **actualizaciones son más rápidas** : solo es necesario cargar un subconjunto de una tabla, reducir el uso de la CPU y la memoria, y el paralelismo puede ser mayor al actualizar varias particiones.
- Las **actualizaciones solo se producen cuando es necesario** : las directivas de actualización incremental se pueden configurar para que se carguen solo cuando los datos han cambiado.
- Las **actualizaciones son más confiables** : las conexiones en ejecución más cortas a sistemas de origen de datos volátiles son menos susceptibles de desconexión.
- Los **modelos siguen siendo Trim** : las directivas de actualización incremental se pueden configurar para quitar automáticamente el historial más allá de un período de tiempo deslizante.

Para obtener más información, consulte la [actualización incremental en Power BI Premium](service-premium-incremental-refresh.md) documento.

#### <a name="why-are-data-refreshes-not-completing"></a>¿Por qué no se completan las actualizaciones de datos?

Cuando la actualización de datos comienza pero no se completa, puede deberse a varios motivos:

- Memoria insuficiente, incluso si solo hay un modelo en la capacidad Premium, es decir, el tamaño del modelo es muy grande.
- Razones que no son de capacidad, incluida la desconexión del sistema de origen de datos, permisos no válidos o error de puerta de enlace

Los administradores de capacidad (y los del servicio Power BI) pueden supervisar la métrica **Refresh Failures due to out of Memory** (Errores de consulta debido a memoria insuficiente).

#### <a name="why-are-ai-calls-failing"></a>¿Por qué se producen errores en las llamadas a AI?

Las llamadas a AI pueden producir errores por varias razones. La memoria mínima necesaria para iniciar la carga de trabajo de AI es de 5 GB, pero puede que no sea suficiente para algunos conjuntos de datos de entrada. Por ejemplo, el entrenamiento automatizado del modelo de aprendizaje automático requiere, al menos, dos veces y, en ocasiones, el tamaño del conjunto de datos de entrada. Además, una llamada a AI se termina si tarda más de dos horas en completarse. En el caso de las llamadas automáticas de entrenamiento del modelo de aprendizaje automático que no se completan en dos horas, se devuelve el mejor modelo que se encuentra en esas dos horas.  Las llamadas a AI también se pueden interrumpir mediante solicitudes interactivas, que tienen prioridad.

Los administradores deben supervisar los tiempos de espera de AI para los síntomas de otras solicitudes que tengan prioridad. Los administradores también pueden asegurarse de que haya suficiente memoria disponible para la carga de trabajo de inteligencia artificial en relación con los tamaños de datos de entrada. Esto puede implicar aislar las cargas de trabajo de inteligencia artificial a las capacidades conocidas para tener suficientes recursos. También es posible que los administradores se coordinen con los propietarios de flujos de DataFlow para ayudar a escalonar o reducir los tiempos de actualización del flujo de entrada para minimizar las colisiones. Tenga en cuenta que un administrador no puede ver la cola de llamadas de AI.

### <a name="optimizing-models"></a>Optimizar modelos

El diseño de modelos óptimos es fundamental para ofrecer una solución eficaz y escalable. Sin embargo, queda fuera del ámbito de este documento para proporcionar una descripción completa. En su lugar, en esta sección se proporcionarán las áreas clave que se deben tener en cuenta al optimizar los modelos.

#### <a name="optimizing-power-bi-hosted-models"></a>Optimización de modelos hospedados en Power BI

La optimización de los modelos hospedados en una capacidad Premium se puede lograr en los orígenes de datos y en las capas de modelo.

Tenga en cuenta las posibilidades de optimización de un modelo de importación:

![Posibilidades de optimización de un modelo de importación](media/whitepaper-premium-deployment/import-model-optimizations.png)

En la capa de origen de datos:

- Los orígenes de datos relacionales se pueden optimizar para garantizar la actualización más rápida posible mediante la integración previa de datos, la aplicación de índices adecuados, la definición de particiones de tabla que se alinean con los períodos de actualización incremental y la materialización de cálculos (en lugar de los calculados). tablas y columnas de modelo) o agregar lógica de cálculo a las vistas
- Los orígenes de datos no relacionales se pueden integrar previamente con almacenes relacionales
- Asegúrese de que las puertas de enlace tienen recursos suficientes, preferiblemente en equipos dedicados, con suficiente ancho de banda de red y que están cerca de los orígenes de datos

En el nivel de modelo:

- Los diseños de consulta de Power Query pueden minimizar o quitar transformaciones complejas, especialmente las que combinan distintos orígenes de datos (los almacenes de datos lo logran durante su fase de extracción, transformación y carga). Además, asegurarse de que se establezcan los niveles de privacidad del origen de datos adecuados, esto puede evitar la necesidad de Power BI para cargar los resultados completos con el fin de generar un resultado combinado en las consultas.
- La estructura del modelo determina los datos que se van a cargar y tiene un impacto directo en el tamaño del modelo. Se puede diseñar para evitar la carga de datos innecesarios mediante la eliminación de columnas y filas (especialmente datos históricos), o la carga de datos resumidos (a costa de cargar datos detallados). Se puede lograr una reducción drástica del tamaño si se quitan las columnas de cardinalidad (especialmente las columnas de texto) que no se almacenan ni comprimen de manera muy eficaz.
- El rendimiento de la consulta del modelo se puede mejorar mediante la configuración de relaciones de dirección única, a menos que haya una buena razón para permitir el filtrado bidireccional. Considere también el uso de la función CROSSFILTER en lugar del filtrado bidireccional.
- Las tablas de agregación pueden obtener respuestas de consulta rápidas mediante la carga de datos resumidos previamente, pero esto aumentará el tamaño del modelo y dará lugar a tiempos de actualización más largos. Por lo general, las tablas de agregación se deben reservar para modelos muy grandes o diseños de modelos compuestos.
- Las tablas y columnas calculadas aumentan el tamaño del modelo y dan lugar a tiempos de actualización más largos. Por lo general, se puede lograr un tamaño de almacenamiento más pequeño y un tiempo de actualización más rápido cuando los datos se materializan o calculan en el origen de datos. Si esto no es posible, el uso de columnas personalizadas de Power Query puede ofrecer una compresión de almacenamiento mejorada.
- Es posible que se puedan ajustar expresiones DAX para medidas y reglas de RLS, y reescribir la lógica para evitar fórmulas costosas
- La actualización incremental puede reducir drásticamente el tiempo de actualización y conservar la memoria y la CPU. La actualización incremental también se puede configurar para quitar datos históricos y mantener el recorte de los tamaños de modelo.
- Un modelo se podría rediseñar como dos cuando existen patrones de consulta diferentes y en conflicto. Por ejemplo, algunos informes presentan agregados generales de todo el historial y pueden tolerar una latencia de 24 horas. Otros informes se limitan a los datos actuales y necesitan acceso pormenorizado a transacciones individuales. En lugar de diseñar un único modelo para satisfacer todos los informes, cree dos modelos optimizados para cada requisito.

Tenga en cuenta las posibilidades de optimización de un modelo de DirectQuery. A medida que el modelo emite solicitudes de consulta al origen de datos subyacente, la optimización de orígenes de datos es fundamental para entregar consultas de modelo que responden.

 ![Posibilidades de optimización de un modelo de DirectQuery](media/whitepaper-premium-deployment/direct-query-model-optimizations.png)

En la capa de origen de datos:

- El origen de datos se puede optimizar para garantizar la consulta más rápida posible mediante la integración previa de datos (que no es posible en el nivel de modelo), la aplicación de índices adecuados, la definición de particiones de tabla, la materialización de datos resumidos (con vistas indizadas) y minimizar la cantidad de cálculos. La mejor experiencia se consigue cuando las consultas de paso a través solo necesitan filtrar y realizar combinaciones internas entre tablas o vistas indizadas.
- Asegúrese de que las puertas de enlace tienen suficientes recursos, preferiblemente en máquinas dedicadas, con suficiente ancho de banda de red y cerca del origen de datos.

En el nivel de modelo:

- Power Query diseños de consulta deberían aplicar preferiblemente no transformaciones; de lo contrario, intenta mantener las transformaciones en un mínimo absoluto.
- El rendimiento de la consulta del modelo se puede mejorar mediante la configuración de relaciones de dirección única, a menos que haya una buena razón para permitir el filtrado bidireccional. Además, las relaciones de modelos deben configurarse para asumir que se aplica la integridad referencial (cuando este es el caso) y dará como resultado consultas de origen de datos con combinaciones internas más eficaces (en lugar de combinaciones externas).
- Evite la creación de Power Query columna calculada de la consulta o las columnas calculadas del modelo: materializarlas en el origen de datos, siempre que sea posible.
- Es posible que se puedan ajustar expresiones DAX para medidas y reglas de RLS, y reescribir la lógica para evitar fórmulas costosas

Tenga en cuenta las posibilidades de optimización de un modelo compuesto. Recuerde que un modelo compuesto permite una combinación de tablas de importación y de DirectQuery.

![Posibilidades de optimización para un modelo compuesto](media/whitepaper-premium-deployment/composite-model-optimizations.png)

- Por lo general, los temas de optimización de los modelos de importación y DirectQuery se aplican a las tablas de modelo compuesto que usan estos modos de almacenamiento.
- Es habitual intentar lograr un diseño equilibrado mediante la configuración de tablas de tipo de dimensión (que representan entidades empresariales) en modo de almacenamiento dual, y las tablas de tipo de hechos (a menudo tablas grandes que representan hechos operativos) en modo de almacenamiento de DirectQuery. El modo de almacenamiento dual significa tanto el modo de almacenamiento de DirectQuery como el de importación y esto permite a los servicio Power BI determinar el modo de almacenamiento más eficaz que se usará al generar una consulta nativa para el acceso directo.
- Asegúrese de que las puertas de enlace tienen recursos suficientes, preferiblemente en equipos dedicados, con suficiente ancho de banda de red y que están cerca de los orígenes de datos
- Las tablas de agregaciones configuradas como modo de almacenamiento de importación pueden mejorar de forma considerable el rendimiento de las consultas cuando se usan para resumir tablas de tipo de hechos en modo de almacenamiento de DirectQuery. En este caso, las tablas de agregación aumentarán el tamaño del modelo y el tiempo de actualización, lo que a menudo resulta aceptable y compensa para obtener consultas más rápidas.

#### <a name="optimizing-externally-hosted-models"></a>Optimizar modelos hospedados externamente

Muchas de las posibilidades de optimización descritas en el tema [optimización de modelos hospedados Power BI](#optimizing-power-bi-hosted-models) también se aplican a los modelos desarrollados con Azure Analysis Services y SQL Server Analysis Services. Las excepciones evidentes son ciertas características que no se admiten en la actualidad, incluidos los modelos compuestos y las tablas de agregación.

Una consideración adicional para los conjuntos de datos hospedados externamente es el hospedaje de la base de datos en relación con el servicio Power BI. Para Azure Analysis Services, esto significa crear el recurso de Azure en la misma región que el inquilino de Power BI (la región principal). Para SQL Server Analysis Services, en el caso de IaaS, esto significa hospedar la máquina virtual en la misma región y, para el entorno local, garantizar una configuración de puerta de enlace eficaz.

Por otra parte, puede ser de interés destacar que en las bases de datos de Azure Analysis Services y las bases de datos tabulares de SQL Server Analysis Services es necesario que los modelos se carguen completamente en memoria y que permanezcan allí de forma continua para admitir las consultas. Como sucede en el servicio Power BI, debe haber memoria suficiente para la actualización si el modelo debe permanecer en línea durante la actualización. A diferencia de lo que ocurre en el servicio Power BI, no hay ningún concepto de que la memoria de los modelos aumente o disminuya de forma automática en función del uso. Por tanto, Power BI Premium ofrece un enfoque más eficaz para maximizar las consultas de modelos con un menor uso de memoria.

### <a name="capacity-planning"></a>Planeamiento de capacidad

El tamaño de una capacidad Premium determina la memoria disponible y los recursos del procesador y los límites impuestos en la capacidad. También se debe tener en cuenta el número de capacidades Premium, ya que la creación de varias capacidades Premium puede facilitar el aislamiento de las cargas de trabajo entre sí. Recuerde que el almacenamiento es de 100 TB por nodo de capacidad, lo que probablemente sea más que suficiente para cualquier carga de trabajo.

Determinar el tamaño y el número de capacidades Premium puede ser un reto, especialmente para las capacidades iniciales que cree. Al ajustar el tamaño de la capacidad, el primer paso consiste es comprender el promedio de carga de trabajo que representa el uso cotidiano esperado. Es importante entender que no todas las cargas de trabajo son iguales. Por ejemplo, en un extremo de un espectro, 100 usuarios simultáneos que acceden a una sola página de un informe que contiene un solo objeto visual se puede conseguir fácilmente. Pero, en el otro extremo del espectro, 100 usuarios simultáneos que acceden a 100 informes distintos, cada uno con 100 objetos visuales en la página del informe, supondrá una demanda muy distinta de los recursos de la capacidad.

Por tanto, los administradores de capacidad deberán tener en cuenta muchos factores específicos del entorno, el contenido y el uso esperado. El objetivo de invalidación es maximizar la utilización de la capacidad, a la vez que se proporcionan tiempos de consulta coherentes, tiempos de espera aceptables y tasas de expulsión. Algunos factores que se deben tener en cuenta son los siguientes:

- **Tamaño del modelo y características** de los datos: los modelos de importación deben estar totalmente cargados en la memoria para permitir la consulta o la actualización. Los conjuntos de datos de LC/DQ pueden requerir mucho tiempo de procesador y posiblemente mucha memoria para evaluar medidas complejas o reglas RLS. El tamaño de la memoria y del procesador, y el rendimiento de las consultas LC/DQ están restringidos por el tamaño de la capacidad.
- **Modelos activos simultáneos** : las consultas simultáneas de diferentes modelos de importación proporcionarán una mejor capacidad de respuesta y rendimiento cuando permanezcan en la memoria. Debe haber memoria suficiente para hospedar todos los modelos que se consultan de manera intensiva, con memoria adicional para permitir su actualización.
- **Importar actualización del modelo** : el tipo de actualización (completa o incremental), la duración y la complejidad de las consultas de Power Query y la lógica de tabla o columna calculada pueden afectar a la memoria y, en especial, al uso del procesador. Las actualizaciones simultáneas están limitadas por el tamaño de la capacidad (1,5 x núcleos virtuales de back-end, redondeado hacia arriba).
- **Consultas simultáneas** : muchas consultas simultáneas pueden dar lugar a informes que no responden cuando las conexiones procesador o LC/DQ superan el límite de capacidad. Esto sucede especialmente con las páginas de informe que incluyen muchos objetos visuales.
- **Flujos de DataFlow, informes paginados y funciones de AI** : la capacidad puede configurarse para admitir flujos de DataFlow, informes paginados y funciones de AI, y cada uno de ellos requiere un porcentaje máximo configurable de memoria de la capacidad. La memoria se asigna dinámicamente a los flujos de entrada, pero se asigna estáticamente a los informes paginados y a la carga de trabajo de AI.

Además de estos factores, los administradores de capacidad pueden considerar la posibilidad de crear varias capacidades. Varias capacidades permiten el aislamiento de las cargas de trabajo y se pueden configurar para garantizar que las cargas de trabajo prioritarias tengan recursos garantizados. Por ejemplo, se pueden crear dos capacidades para separar las cargas de trabajo críticas para la empresa de las cargas de trabajo de inteligencia empresarial con características de autoservicio (SSBI). La capacidad crítica para la empresa se puede usar para aislar modelos corporativos de gran tamaño proporcionándoles recursos garantizados, y conceder el acceso de creación solo al departamento de TI. La capacidad de SSBI se puede usar para hospedar un número creciente de modelos más pequeños, y conceder el acceso a los analistas de negocios. La capacidad de SSBI puede experimentar ocasionalmente esperas de consulta o actualización tolerables.

Con el tiempo, los administradores de capacidad pueden equilibrar las áreas de trabajo entre las capacidades si mueven contenido entre las áreas de trabajo, o bien las áreas de trabajo entre las capacidades, y si escalan las capacidades vertical u horizontalmente. Por lo general, para hospedar modelos más grandes, escale verticalmente y para una mayor simultaneidad que escala horizontalmente.

Recuerde que la compra de una licencia proporciona núcleos virtuales al inquilino. La compra de una suscripción **P3** se puede usar para crear una o hasta cuatro capacidades Premium, es decir, 1 x P3, 2 x P2 o 4 x P1. Además, antes de convertir una capacidad P2 a una capacidad P3, se puede considerar la posibilidad de dividir los núcleos virtuales para crear dos capacidades P1.

### <a name="testing-approaches"></a>Métodos de prueba

Una vez que se ha decidido el tamaño de la capacidad, se pueden realizar pruebas mediante la creación de un entorno controlado. Una opción práctica y económica consiste en crear una capacidad de Azure (SKU), sin olvidar que una capacidad P1 tiene el mismo tamaño que una capacidad A4, y que las capacidades P2 y P3 tienen el mismo tamaño que las capacidades A5 y A6, respectivamente. Las capacidades de Azure se pueden crear de forma rápida y se facturan por hora. Por tanto, una vez completadas las pruebas, se pueden eliminar fácilmente para dejar de acumular costos.

El contenido de las pruebas se puede agregar a las áreas de trabajo creadas en la capacidad de Azure y, después, como un solo usuario que puede ejecutar informes para generar una carga de trabajo realista y representativa de las consultas. Si hay modelos de importación, también se debe realizar una actualización de cada uno. Se pueden usar herramientas de supervisión para revisar todas las métricas y comprender el uso de los recursos.

Es importante que las pruebas sean repetibles: las pruebas se deben ejecutar varias veces y deben proporcionar aproximadamente el mismo resultado cada vez. Se puede usar un promedio de estos resultados para extrapolar y calcular una carga de trabajo en condiciones reales de producción.

Si ya tiene una capacidad y los informes para los que quiere realizar pruebas de carga, use la [herramienta de generación de cargas de PowerShell](https://aka.ms/PowerBILoadTestingTool) para generar rápidamente una prueba de carga. La herramienta permite calcular el número de instancias de cada informe que la capacidad puede ejecutar en una hora. Puede usar la herramienta para evaluar si la capacidad puede representar informes individuales o varios informes diferentes en paralelo. Para obtener más información, vea el vídeo [Microsoft Power BI: capacidad Premium](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Para generar una prueba más compleja, considere la posibilidad de desarrollar una aplicación de prueba de carga que simule una carga de trabajo realista. Para más información, vea el seminario web [Load Testing Power BI Applications with Visual Studio Load Test](https://www.youtube.com/watch?v=UFbCh5TaR4w) (Pruebas de carga de aplicaciones de Power BI con la prueba de carga de Visual Studio).

## <a name="exploring-real-world-scenarios"></a>Explorar escenarios del mundo real

En esta sección, se presentarán varios escenarios del mundo real para describir problemas comunes o desafíos, cómo identificarlos y cómo resolverlos:

- [Mantener actualizados los conjuntos de datos](#keeping-datasets-up-to-date)
- [Identificar conjuntos de valores de respuesta lenta](#identifying-slow-responding-datasets)
- [Identificación de las causas de los conjuntos de valores de respuesta esporádicamente lentos](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinar si hay suficiente memoria](#determining-whether-there-is-enough-memory)
- [Determinar si hay suficiente CPU](#determining-whether-there-is-enough-cpu)

Los pasos, junto con los ejemplos de gráficos y tablas, proceden de la **aplicación Power BI Premium de métricas de capacidad** (APP) a la que un administrador de Power BI tendrá acceso.

### <a name="keeping-datasets-up-to-date"></a>Mantener actualizados los conjuntos de datos

En este escenario, se desencadenó una investigación cuando los usuarios se quejan de que los datos del informe parecían a veces antiguos o "obsoletos".

En la aplicación, el administrador interactúa con el objeto visual de **actualizaciones** , ordenando los conjuntos de objetos por las estadísticas de **tiempo de espera máximo** en orden descendente. Esto les ayuda a revelar los conjuntos de valores que tienen tiempos de espera más largos, agrupados por nombre de área de trabajo.

![El conjunto de los conjuntos de caracteres se actualiza por tiempo de espera máximo descendente, agrupado por área de trabajo](media/whitepaper-premium-deployment/dataset-refreshes.png)

Además, en los **tiempos de espera de actualización promedio por hora** , observan que el pico de tiempo de espera de actualización se alcanza constantemente aproximadamente a las 16:00 cada día.

![El pico de espera de actualización se actualiza periódicamente a las 16:00](media/whitepaper-premium-deployment/peak-refresh-waits.png)

Hay varias explicaciones posibles para estos resultados:

- Se pueden tener demasiados intentos de actualización al mismo tiempo, superando los límites impuestos por el nodo de capacidad (seis actualizaciones simultáneas en P1 con asignación de memoria predeterminada)

- Los conjuntos de valores que se van a actualizar pueden ser demasiado grandes para caber en la memoria disponible (lo que requiere al menos el doble de memoria necesaria para la actualización completa)
- Una lógica de Power Query ineficaz puede ser el resultado de un pico de uso de memoria durante la actualización del conjunto de resultados. En una capacidad ocupada, en ocasiones, esto puede alcanzar el límite físico, con lo que se producirá un error en la actualización y posiblemente afecte a otras operaciones de vista de informe sobre la capacidad.
- Los conjuntos de valores de consulta frecuente que necesitan permanecer en la memoria pueden afectar a la capacidad de actualización de otros conjuntos de valores, debido a la memoria disponible limitada.

Para ayudar a investigar esto, el administrador de Power BI puede buscar:

- Poca memoria disponible en el momento de la actualización de datos, cuando la memoria disponible es menor que el doble del tamaño del conjunto de datos que se va a actualizar.
- Conjuntos de valores que no se actualizaron y que no estaban en la memoria antes de una actualización, pero que empezaron a mostrar tráfico interactivo durante grandes tiempos de actualización. Para ver los conjuntos de valores que se cargaron en la memoria en un momento dado, un administrador de Power BI puede examinar el área conjuntos de valores de la pestaña **conjuntos de valores** de la aplicación y el filtro cruzado a un momento dado haciendo clic en una de las barras del conjunto de conjuntos por hora que se **recuento**. Un pico local (que se muestra en la imagen siguiente) indica una hora en la que se cargaron varios conjuntos de información en la memoria, lo que puede retrasar el inicio de las actualizaciones programadas.
- Aumento de las expulsiones de los conjuntos de datos que tienen lugar cuando las actualizaciones de datos están programadas para iniciarse, lo que indica que se ha producido una presión de memoria elevada al servir demasiados informes interactivos antes del momento de la actualización. El objeto visual de **expulsiones y consumo de memoria del conjunto** de elementos por hora puede indicar claramente picos en las expulsiones.

En la siguiente imagen se muestra un pico local en los conjuntos de valores cargados, que sugiere consultas interactivas sobre el Inicio retrasado de las actualizaciones. Al seleccionar un período de tiempo en el conjunto de objetos **cargado por hora** , el objeto visual realizará un filtro cruzado del objeto visual **tamaños de conjunto** de elementos.

![Un pico local en los conjuntos de valores cargados sugiere consultas interactivas en el Inicio retrasado de las actualizaciones](media/whitepaper-premium-deployment/hourly-loaded-dataset-counts.png)

El administrador de Power BI puede intentar resolver el problema realizando pasos para asegurarse de que hay suficiente memoria disponible para que las actualizaciones de datos se inicien de la manera siguiente:

- Ponerse en contacto con los propietarios del conjunto de datos y pedirles que escalonen y destaquen la programación de actualización de datos
- Reducir la carga de la consulta del conjunto de filas quitando paneles innecesarios o iconos del panel, especialmente aquellos que aplican seguridad de nivel de fila
- Acelerar las actualizaciones de datos mediante la optimización de la lógica de Power Query, el modelo de tablas o columnas calculadas, la reducción de los tamaños de los conjuntos de datos o la configuración de conjuntos de datos mayores para realizar la actualización incremental de datos

### <a name="identifying-slow-responding-datasets"></a>Identificar conjuntos de valores de respuesta lenta

En este escenario, se desencadenó una investigación cuando los usuarios produjeron que determinados informes tardaron mucho tiempo en abrirse y, en ocasiones, se bloquearía.

En la aplicación, el administrador de Power BI puede usar el visual de duración de la **consulta** para determinar los conjuntos de valores de peor rendimiento mediante la ordenación de los conjuntos de objetos por **duración media**descendente. Este objeto visual también muestra los recuentos de consultas del conjunto de elementos, por lo que puede ver la frecuencia con que se consultan los conjuntos de objetos.

![Revelar los conjuntos de valores de peor rendimiento](media/whitepaper-premium-deployment/worst-performing-datasets.png)

El administrador de Power BI puede hacer referencia al visual de distribución de la duración de la **consulta** , que muestra una distribución general del rendimiento de las consultas en depósito (< = 30ms, 0-100 MS, etc.) para el período de tiempo filtrado. Por lo general, la mayoría de los usuarios consideran que las consultas que tardan un segundo o menos responden. las consultas que tardan más tiempo tienden a crear una percepción de un rendimiento incorrecto.

El visual de distribución de la duración de las **consultas por hora** permite al administrador de Power BI identificar los períodos de una hora en que el rendimiento de la capacidad podría haberse percibido como deficiente. Cuanto más grandes sean los segmentos de la barra que representan la duración de la consulta en un segundo, mayor será el riesgo de que los usuarios perciban un rendimiento deficiente.

El visual es interactivo y, cuando se selecciona un segmento de la barra, el visual de la tabla **duraciones** de la consulta correspondiente en la página del informe se filtra de forma cruzada para mostrar los conjuntos de los mismos que representa. Este filtrado cruzado permite al administrador de Power BI identificar fácilmente qué conjuntos de valores responden lentamente.

En la imagen siguiente se muestra un visual filtrado por las **distribuciones de duración**de las consultas por hora, centrándose en los conjuntos de valores de peor rendimiento en cubos de una hora. 

![Distribuciones de duración de consulta por hora filtradas visual muestra los conjuntos de objetos de peor rendimiento](media/whitepaper-premium-deployment/hourly-query-duration-distributions.png)

Una vez que se identifica el conjunto de resultados de rendimiento deficiente en un intervalo de tiempo de 1 hora específico, el administrador de Power BI puede investigar si el bajo rendimiento está causado por una capacidad sobrecargada o debido a un conjunto de información o informe mal diseñado. Para ello, pueden hacer referencia al visual de los **tiempos de espera** de la consulta y ordenar los conjuntos de valores por tiempo medio de espera de consulta. Si hay un gran porcentaje de consultas en espera, es probable que la causa de muchas esperas de consultas sea una gran demanda del conjunto de los mismos. Si el tiempo promedio de espera de consulta es considerable (> 100 ms), puede que merezca la pena revisar el conjunto de información y el informe para ver si se pueden realizar optimizaciones. Por ejemplo, quizás menos objetos visuales en determinadas páginas del informe o en una optimización de expresión DAX.

![El visual de tiempo de espera de la consulta ayuda a revelar conjuntos de valores de rendimiento deficiente](media/whitepaper-premium-deployment/query-wait-times.png)

Hay varias razones posibles por las que el tiempo de espera de la consulta se genera en conjuntos de valores:

- Un diseño de modelo poco óptimo, expresiones de medida o incluso un diseño de informe, todas las circunstancias que pueden contribuir a consultas de larga ejecución que consumen altos niveles de CPU. Esto obliga a que las nuevas consultas esperen hasta que los subprocesos de CPU estén disponibles y puedan crear un efecto de convoy (pensar en el atasco de tráfico), que normalmente se percibe durante el horario comercial. La página **esperas de consulta** será el recurso principal para determinar si los conjuntos de valores tienen tiempos de espera de consulta promedio elevados.
- Un gran número de usuarios de capacidad simultánea (de cientos a miles) que consumen el mismo informe o conjunto de los mismos. Incluso los conjuntos de valores bien diseñados pueden llevar un tiempo superior al umbral de simultaneidad. Normalmente, esto se indica mediante un único conjunto de valores que muestra un valor drásticamente superior para los recuentos de consultas que otros conjuntos de valores (es decir, las consultas de 300 000 para un < conjunto de los conjuntos de los conjuntos de valores). En algún momento, la consulta espera a que este conjunto de elementos se inicie en etapas y esto se verá en el objeto visual de duración de la **consulta** .
- Muchos conjuntos de información dispares se consultan simultáneamente, lo que provoca la paginación excesiva, ya que los conjuntos de valores se recorren con frecuencia dentro y fuera de la memoria. Esto hace que los usuarios experimenten un rendimiento lento cuando el conjunto de resultados se carga en la memoria. Para confirmarlo, el administrador de Power BI puede hacer referencia al objeto visual de **expulsiones y consumo de memoria del conjunto** de elementos por hora, lo que puede indicar que un gran número de conjuntos de objetos cargados en la memoria se expulsan repetidamente.

### <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificación de las causas de los conjuntos de valores de respuesta esporádicamente lentos

En este escenario, se desencadenó una investigación cuando los usuarios describen que los objetos visuales de los informes a veces tardan en responder o podrían dejar de responder, pero en otros momentos eran aceptablemente receptivos.

Dentro de la aplicación, se usó la sección **duraciones** de la consulta para encontrar el conjunto de elementos de causa de la siguiente manera:

- En el objeto visual de duración de la **consulta** , el conjunto de DataSet filtrado por el conjunto de elementos (a partir de los primeros conjuntos de elementos consultados) y examinó las barras filtradas entre horas en el objeto visual de **distribuciones de consultas por hora** .
- Cuando una sola barra de una hora muestra cambios significativos en la relación entre todos los grupos de duración de la consulta y otras barras de una hora para ese conjunto de bits (es decir, las proporciones entre los cambios de los colores se modifican drásticamente), significa que este conjunto de DataSet demuestra un cambio esporádico en rendimiento.
- Las barras de una hora que muestran una parte irregular de las consultas con un rendimiento deficiente, indicaban un intervalo de tiempo en el que el conjunto de resultados se ha visto afectado por un efecto vecino ruidoso, causado por otras actividades de conjuntos de información.

En la imagen siguiente se muestra una hora el 30 de enero, donde se produjo un setback significativo en el rendimiento de un conjunto de resultados, indicado por el tamaño del cubo de duración de ejecución "(3, decenas]"). Al hacer clic en esa barra de una hora, se muestran todos los conjuntos de valores que se cargan en la memoria durante ese tiempo, con lo que se muestran los conjuntos de valores del culpable del candidato que causan el efecto vecino ruidoso.

![Barra que muestra el peor rendimiento en una gran parte](media/whitepaper-premium-deployment/worst-performing-queries.png)

Una vez que se identifica un intervalo de tiempo problemático (es decir, durante el 30 de enero de la imagen anterior), el administrador de Power BI puede quitar todos los filtros de conjunto de los conjuntos de valores y, a continuación, filtrar solo por ese intervalo de tiempo para determinar qué conjuntos de valores se consultaron activamente El conjunto de valores de causa del efecto vecino ruidoso es normalmente el conjunto de los principales consultado superior o el que tiene la duración media más larga de la consulta.

Una solución a este problema podría ser distribuir los conjuntos de datos de causa a través de diferentes áreas de trabajo en distintas capacidades Premium, o en capacidad compartida si se admiten el tamaño del conjunto de datos, los requisitos de consumo y los patrones de actualización de datos.

La inversión también puede ser verdadera. El administrador de Power BI puede identificar los momentos en los que el rendimiento de una consulta de conjunto de elementos mejora drásticamente y, a continuación, busca lo que ha desaparecido. Si falta cierta información en ese momento, esto puede ayudar a señalar el problema que causa.

### <a name="determining-whether-there-is-enough-memory"></a>Determinar si hay suficiente memoria

Para determinar si hay suficiente memoria para que la capacidad pueda completar sus cargas de trabajo, el administrador de Power BI puede hacer referencia al visual de **porcentaje de memoria consumida** en la pestaña **conjuntos de valores** de la aplicación. **Toda** la memoria (total) representa la memoria consumida por los conjuntos de valores cargados en la memoria, independientemente de si se consultan o procesan activamente. La memoria **activa** representa la memoria consumida por los conjuntos de valores que se están procesando activamente.

En una capacidad correcta, el aspecto visual será similar al siguiente, mostrando un intervalo entre todo (total) y la memoria activa:

![Una capacidad correcta mostrará un intervalo entre todo (total) y la memoria activa](media/whitepaper-premium-deployment/memory-healthy-capacity.png)

En una capacidad que experimenta la presión de memoria, el mismo visual muestra claramente la memoria activa y el total de la memoria, lo que significa que no es posible cargar conjuntos de caracteres adicionales en la memoria en ese momento dado. En este caso, el administrador de Power BI puede hacer clic en **reinicio de capacidad** (en **Opciones avanzadas** del área Configuración de capacidad del portal de administración). Al reiniciar la capacidad, se vacían todos los conjuntos de datos de la memoria y se les permite volver a cargarlos en la memoria según sea necesario (mediante consultas o actualización de datos).

![\* * Memoria activa * * que converge con * * All * * Memory](media/whitepaper-premium-deployment/memory-unhealthy-capacity.png)

### <a name="determining-whether-there-is-enough-cpu"></a>Determinar si hay suficiente CPU

En general, el uso promedio de la CPU de la capacidad debe permanecer por debajo del 80%. Si se supera este valor, la capacidad se aproxima a la saturación de la CPU.

Los efectos de la saturación de la CPU se expresan mediante operaciones que tardan más tiempo de lo que deberían debido a la capacidad que realiza muchos cambios de contexto de CPU cuando intenta procesar todas las operaciones. En una capacidad Premium con un gran número de consultas simultáneas, esto se indica mediante altos tiempos de espera de consulta. Una consecuencia de tiempos de espera de consulta elevados es una capacidad de respuesta más lenta de lo habitual. El administrador de Power BI puede identificar fácilmente si la CPU está saturada viendo el visual de **distribuciones de tiempo de espera de consulta por hora** . Los picos periódicos de los recuentos de tiempo de espera de consulta indican una posible saturación de la CPU.

![Los recuentos de picos periódicos de tiempo de espera de consultas indican la posible saturación de la CPU.](media/whitepaper-premium-deployment/peak-query-wait-times.png)

A veces se puede detectar un patrón similar en las operaciones en segundo plano si contribuyen a la saturación de la CPU. Un administrador de Power BI puede buscar un pico periódico en los tiempos de actualización de un conjunto de información específico, lo que puede indicar una saturación de la CPU en el momento (probablemente debido a otras actualizaciones de conjunto de los conjuntos de información en curso o a consultas interactivas). En esta instancia, es posible que la referencia a la vista **del sistema** de la aplicación no revele necesariamente que la CPU está en el 100%. La vista **del sistema** muestra los promedios por hora, pero la CPU puede saturarse durante varios minutos de operaciones pesadas, que se muestran como picos en los tiempos de espera.

Hay más matices para ver el efecto de la saturación de la CPU. Aunque el número de consultas que esperan es importante, el tiempo de espera de la consulta siempre se producirá en cierta medida sin producir una degradación del rendimiento apreciable. Algunos conjuntos de usuarios (con un tiempo medio de consulta de más larga, que indica la complejidad o el tamaño) son más propensos a los efectos de la saturación de la CPU que otros. Para identificar fácilmente estos conjuntos de objetos, el administrador de Power BI puede buscar cambios en la composición de color de las barras del visual de **distribución por hora de tiempo de espera** . Después de detectar una barra de valores atípicos, pueden buscar los conjuntos de valores que tenían consultas en espera durante ese tiempo y observar también el tiempo promedio de espera de consulta en comparación con la duración media de la consulta. Cuando estas dos métricas son de la misma magnitud y la carga de trabajo de la consulta para el conjunto de resultados no es trivial, es probable que el conjunto de resultados se vea afectado por una CPU insuficiente.

Este efecto puede ser especialmente aparente cuando un conjunto de resultados se utiliza en ráfagas cortas de consultas de alta frecuencia por parte de varios usuarios (es decir, en una sesión de entrenamiento), lo que produce una saturación de la CPU durante cada ráfaga. En este caso, los tiempos de espera de consulta significativos de este conjunto de resultados se pueden experimentar, así como afectar a otros conjuntos de valores de la capacidad (efecto vecino ruidoso).

En algunos casos, los administradores de Power BI pueden solicitar que los propietarios de conjuntos de registros creen una carga de trabajo de consultas menos volátil mediante la creación de un panel (que realiza consultas periódicas con cualquier actualización del conjunto de registros para los mosaicos en caché) en lugar de un informe. Esto puede ayudar a evitar picos cuando se carga el panel. Es posible que esta solución no siempre sea posible para los requisitos empresariales determinados, pero puede ser una manera eficaz de evitar la saturación de la CPU, sin realizar cambios en el conjunto de información.

## <a name="conclusion"></a>Conclusión

Power BI Premium proporciona un rendimiento más coherente, compatibilidad con grandes volúmenes de datos y la flexibilidad de una plataforma empresarial de autoservicio unificada para todos los usuarios de su organización. Este documento técnico de nivel 300 se ha escrito específicamente para los administradores de Power BI y los autores y editores de contenido. Pretende ayudarles a comprender el potencial de Power BI Premium y a explicar cómo diseñar, implementar, supervisar y solucionar problemas de soluciones escalables.

Para implementar y administrar las capacidades de Power BI Premium, los administradores y los desarrolladores de modelos necesitarán una buena comprensión de cómo funcionan las capacidades, cómo se pueden administrar y supervisar, y cómo se pueden optimizar los modelos, con el fin de responder adecuadamente a problemas de rendimiento y cuellos de botella que surjan.

## <a name="end-notes"></a>Notas finales

<a name="endnote-01"></a>\[1\] este documento técnico está relacionado con Power BI Premium que solo es compatible con el servicio en la nube Power BI, por lo que Power BI Report Server no está en el ámbito, excepto en el caso de que la licencia necesaria para instalar Power BI Report Server esté incluida en algunos Power BI Premium SKU.

<a name="endnote-02"></a>\[2\] Power BI como servicio en la nube cuando se usa para insertar contenido en nombre de los usuarios de la aplicación es plataforma como servicio (PaaS). Este tipo de incrustación se puede lograr con dos productos diferentes, uno de los cuales es Power BI Premium.

<a name="endnote-03"></a>\[3\] los conjuntos de inserciones, streaming e híbridos no se almacenan en capacidades Premium y, por tanto, no se tienen en cuenta al implementar, administrar y supervisar las capacidades Premium.

<a name="endnote-04"></a>\[4\] libros de Excel como un tipo de contenido de Power BI no se almacenan en capacidades Premium y, por tanto, no son una consideración al implementar, administrar o supervisar las capacidades Premium.

<a name="endnote-05"></a>\[5\] los objetos visuales se pueden configurar para omitir las interacciones de la segmentación. Para obtener más información, consulte las [interacciones de visualización en un documento de informe de Power BI](service-reports-visual-interactions.md) .

<a name="endnote-06"></a>\[6\] la diferencia de tamaño se puede determinar comparando el tamaño del archivo Power BI Desktop con la memoria del administrador de tareas mediante para el archivo.

<a name="endnote-07"></a>\[7\] compatibilidad con orígenes de datos de Microsoft incluyen SQL Server, bricks de datos de Azure Azure HDInsight Spark (beta), Azure SQL Database y Azure SQL Data Warehouse. Para obtener información sobre otros orígenes, consulte los [orígenes de datos compatibles con Direct Query en Power BI](desktop-directquery-data-sources.md) documento.

<a name="endnote-08"></a>\[8\] Power BI Premium admiten la carga de un archivo Power BI Desktop (. pbix) hasta un máximo de 10 GB de tamaño. Una vez cargado, un conjunto de resultados puede aumentar hasta 12 GB de tamaño como resultado de la actualización. El tamaño máximo de carga varía según la SKU. Para obtener más información, consulte el documento [compatibilidad de Power BI Premium con conjuntos de datos grandes](service-premium-large-datasets.md) .

<a name="endnote-09"></a>\[9\] SKU con menos de cuatro núcleos virtuales no se ejecutan en una infraestructura dedicada. Esto incluye las SKU EM1, EM2, a1 y a2.

<a name="endnote-10"></a>\[10\], aunque es poco frecuente, los modelos se pueden descargar de la memoria debido a las operaciones del servicio.

<a name="endnote-11"></a>\[11\] estos tiempos están sujetos a cambios en cualquier momento.

<a name="endnote-12"></a>\[12\] esto se conoce como multigeo, actualmente en versión preliminar. Por lo general, la lógica de una implementación multigeográfica es para cumplimiento corporativo o gubernamental, en lugar del rendimiento y la escala. La carga de informes y paneles sigue implicando solicitudes de metadatos a la región principal. Para obtener más información, consulte el documento [compatibilidad con múltiples geografías para Power BI Premium (versión preliminar)](service-admin-premium-multi-geo.md) .

<a name="endnote-13"></a>\[13\] es posible que los usuarios puedan causar problemas de rendimiento sobrecargando el servicio Power BI con trabajos, escribiendo consultas demasiado complejas, creando referencias circulares, etc.

<a name="endnote-14"></a>\[14\] la opción para asignar las áreas de trabajo de toda la organización no se recomienda, y se prefiere un enfoque más dirigido. Por lo general, no es recomendable usar áreas de trabajo personales para el contenido de producción.

<a name="endnote-15"></a>\[15\] es posible supervisar una SKU en la aplicación o en el Azure Portal, pero no en el portal de administración de Power BI. Para supervisar una SKU, se producirá un error en la actualización del informe si no se ha agregado la aplicación al rol lector del recurso. Para obtener más información, consulte el documento [supervisión Power BI Premium y capacidades de Power BI Embedded](service-admin-premium-monitor-capacity.md) .

<a name="endnote-16"></a>\[16 actualizaciones de\] pueden esperar cuando no haya suficiente CPU o memoria para iniciarse.

<a name="endnote-17"></a>\[17\] el tamaño del conjunto de la memoria puede ser mayor que el tamaño en disco hasta un 20%.

<a name="endnote-18"></a>\[18\] promedio de uso de memoria (GB) y el mayor consumo de memoria (GB)

<a name="endnote-19"></a>expulsiones de \[19\] DataSet

<a name="endnote-20"></a>\[20\] consultas de conjunto de los conjuntos de DataSet, duración media de la consulta (MS), recuento de espera de conjunto de DataSet y tiempo promedio de espera (MS)

<a name="endnote-21"></a>\[21\] recuento de uso elevado de CPU y tiempo de CPU de uso más alto (últimos siete días)

<a name="endnote-22"></a>\[22\] recuento de uso elevado de DQ/LC y hora de DQ/LC de uso más alto (últimos siete días)
