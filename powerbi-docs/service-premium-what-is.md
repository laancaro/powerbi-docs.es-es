---
title: ¿Qué es Microsoft Power BI Premium?
description: Power BI Premium proporciona capacidad dedicada para su organización, lo que le ofrece un rendimiento más confiable y mayores volúmenes de datos, sin tener que adquirir licencias por usuario.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/22/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e5ffa624bf69cf470aade076c80ac37028a55456
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565261"
---
# <a name="what-is-power-bi-premium"></a>¿Qué es Power BI Premium?

Power BI Premium proporciona recursos dedicados y mejorados para ejecutar el servicio Power BI para su organización. Por ejemplo:

- Mayor escalabilidad y rendimiento
- Flexibilidad de licencia por capacidad
- Unificar el autoservicio y BI empresarial
- Ampliar BI de forma local con Power BI Report Server
- Compatibilidad con la residencia de datos por región (Multigeográficas)
- Compartir datos con cualquier usuario sin tener que adquirir una licencia por usuario

En este artículo no está pensado para proporcionar información detallada sobre todas las características de Power BI Premium: de hecho, sólo toca la superficie. Si es necesario, se proporcionan vínculos a otros artículos con información más detallada.

## <a name="subscriptions-and-licensing"></a>Las suscripciones y licencias

Power BI Premium es una suscripción de Office 365 de nivel de inquilino disponible en dos familias de SKU (Stock Keeping Unit):

- **EM** SKU (EM1-EM3) para la inserción, que requieren un compromiso anual, mensualmente.
- **P** SKU (P1-P3) para insertar y las funciones empresariales, que requieren un compromiso mensual o anual, facturado mensualmente e incluye una licencia para instalar Power BI Report Server en el entorno local.

Un enfoque alternativo consiste en adquirir un **Azure Power BI Embedded** suscripción, que tiene una sola **A** solo con fines de familia SKU (A1 a A6) para insertarlo y pruebas de capacidad. Todas las SKU de entregar núcleos para crear las capacidades, pero las SKU EM están restringidas para la inserción de menor escala. EM1, EM2, A1 y A2 SKU con menos de cuatro núcleos no se ejecutan en infraestructura dedicada.

Mientras el foco de este artículo está en las SKU P, gran parte de lo que se describe también es relevante para las SKU. A diferencia de la suscripción Premium SKU, las SKU de Azure no requiere ningún compromiso de tiempo y se facturan por hora. Ofrecen elasticidad completa habilitar el escalado de, reducir verticalmente, pausar, reanudar y eliminar. 

Azure Power BI Embedded es en gran medida fuera del ámbito de este artículo, pero se describe en el [enfoques de pruebas](service-premium-capacity-optimize.md#testing-approaches) sección del artículo de las capacidades de optimización Premium como una opción práctica y económico para probar y medir las cargas de trabajo. Para obtener más información acerca de las SKU de Azure, consulte [documentación de Azure Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Compras

Las suscripciones de Power BI Premium se adquieren por administradores en el centro de administración de Microsoft 365. En concreto, sólo los administradores globales de Office 365 o administradores de facturación pueden comprar las SKU. Cuando compre, el inquilino recibe un número correspondiente de núcleos para asignar a las capacidades, conocidas como *agrupación de núcleo virtual*. Por ejemplo, la compra una SKU P3 proporciona al inquilino 32 núcleos. Para obtener más información, consulte [cómo comprar Power BI Premium](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Capacidad dedicada

Con Power BI Premium, obtendrá *dedicado capacidades*. A diferencia de una capacidad compartida donde se ejecutan cargas de trabajo en recursos informáticos compartidos con otros clientes, una capacidad dedicada es para uso exclusivo por una organización. Ha aislado con los recursos informáticos dedicados que proporcionan un rendimiento confiable y coherente para el contenido hospedado. 

Las áreas de trabajo residen dentro de las capacidades. Cada usuario de Power BI tiene un área de trabajo personal que se conoce como **mi área de trabajo**. Se pueden crear áreas de trabajo adicionales para habilitar la colaboración y la implementación, y estos se conocen como **las áreas de trabajo de aplicación**. De forma predeterminada, las áreas de trabajo, incluidas las áreas de trabajo personales, se crean en la capacidad compartida. Cuando tenga las capacidades Premium, Mis áreas de trabajo y de aplicación áreas de trabajo pueden asignarse a las capacidades Premium.

### <a name="capacity-nodes"></a>Nodos de capacidad

Como se describe en el [suscripciones y licencias](#subscriptions-and-licensing) sección, hay dos familias de SKU de Power BI Premium: **EM** y **P**. Todas las SKU Premium de Power BI están disponibles como capacidad *nodos*, que representan una cierta cantidad de recursos que consta de procesador, memoria y almacenamiento. Además de los recursos, cada SKU tiene límites operativos en el número de conexiones de DirectQuery y conexión dinámica por segundo y se actualiza el número de modelo paralelo.

El procesamiento se consigue mediante un número determinado de núcleos, dividida por igual entre el back-end y front-end.

**Núcleos de back-end** son responsables de la funcionalidad de Power BI core, incluidos el procesamiento de consultas, administración de memoria caché, ejecución de R services, actualización del modelo, el procesamiento de lenguaje natural (preguntas y respuestas) y la representación del lado servidor de informes e imágenes. Núcleos de back-end se asignan una cantidad fija de memoria que se utiliza principalmente para los modelos de host, active también conocido como conjuntos de datos.

**Núcleos de front-end** es responsable de la web informes, paneles y servicio de administración de documentos, administración de derechos de acceso, la programación, API, carga y descarga y generalmente las experiencias para todo lo relacionado con el usuario.

Storage se establece en **100 TB por nodo de capacidad**.

Los recursos y los límites de cada SKU Premium (y tamaño de forma equivalente A SKU) se describen en la tabla siguiente:

| Nodos de capacidad | Total de núcleos virtuales | Núcleos virtuales de back-end | RAM (GB) | Núcleos virtuales de front-end | Conexiones dinámicas/DirectQuery (por segundo) | Paralelismo de actualización del modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="capacity-workloads"></a>Cargas de trabajo de capacidad

Capacidad cargas de trabajo son servicios estén disponibles para usuarios. De forma predeterminada, Premium y capacidades de Azure admiten solo una carga de trabajo de conjunto de datos asociado con la ejecución de consultas de Power BI. No se puede deshabilitar la carga de trabajo del conjunto de datos. Cargas de trabajo adicionales pueden habilitarse para [AI (servicios cognitivos)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [Dataflows](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium), y [informes paginados](paginated-reports-save-to-power-bi-service.md). En las suscripciones Premium solo se admiten estas cargas de trabajo. 

Cada carga de trabajo adicional permite configurar la memoria máxima (como un porcentaje de memoria total disponible) que se puede usar la carga de trabajo. Se determinan los valores predeterminados para la memoria máxima por SKU. Puede maximizar los recursos disponibles de la capacidad habilitando sólo las cargas de trabajo adicionales cuando se usan. Y puede cambiar la configuración solo cuando haya determinado la configuración predeterminada no cumplen los requisitos de capacidad de recursos de memoria. Las cargas de trabajo pueden habilitar y configurar para un administrador de capacidad por capacidad mediante **la configuración de capacidad** en el [del portal de administración](service-admin-portal.md) o mediante el [las capacidades de las API de REST](https://docs.microsoft.com/rest/api/power-bi/capacities).  

![Habilitación de las cargas de trabajo](media/service-admin-premium-workloads/admin-portal-workloads.png)

Para obtener más información, consulte [configurar cargas de trabajo en una capacidad Premium](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>La función de las capacidades

En todo momento, el servicio Power BI hace que sea el mejor uso de recursos de capacidad, aunque no supera los límites impuestos en la capacidad.

Las operaciones de capacidad se clasifican como *interactivo* o *en segundo plano*. Operaciones interactivas incluyen las solicitudes de representación y responder a las interacciones del usuario (filtrado, preguntas y respuestas, etcetera.). Por lo general, realizar consultas de modelo de importación es memoria consume muchos recursos, mientras que consultar modelos de DirectQuery y conexión dinámica es intensiva de CPU. Operaciones en segundo plano incluyen el flujo de datos e importación las actualizaciones del modelo y almacenamiento en caché de consultas de panel.

Es importante comprender que siempre tienen mayor prioridad operaciones interactivas a través de operaciones en segundo plano para garantizar la mejor experiencia posible. Si hay recursos insuficientes, operaciones en segundo plano se agregan a una cola para procesar al liberan recursos. Operaciones en segundo plano, como las actualizaciones del conjunto de datos, pueden ser la mitad del proceso detenido por el servicio Power BI y se agregan a una cola.

Modelos de importación deben ser totalmente cargados en la memoria para que se puedan consultar o actualizar. El servicio Power BI administra la memoria, uso mediante el uso de sofisticados algoritmos para garantizar el máximo uso de memoria disponible y puede provocar la asignación excesiva de la capacidad: Aunque es posible para una capacidad almacenar la importación de muchos modelos (hasta 100 TB por capacidad Premium), cuando su almacenamiento en disco combinada supera la memoria compatible (y es necesaria para consultar y actualizar la memoria adicional), a continuación, no todos se podrán cargados en memoria a el mismo tiempo.

Modelos de importación, por tanto, se cargan en y quitar de la memoria según el uso. Un modelo de importación se carga cuando resulta consultado (operación interactiva) y todavía no en memoria, o cuando es necesario actualizar (operación en segundo plano).

La eliminación de un modelo de memoria se conoce como *expulsión*. Es una operación de que Power BI puede realizar rápidamente según el tamaño de los modelos. Si la capacidad no experimenta la presión de memoria, los modelos se simplemente se cargan en memoria y permanecerán allí. Sin embargo, cuando no hay memoria suficiente está disponible para cargar un modelo, el servicio Power BI en primer lugar deberá liberar memoria. Libera la memoria mediante la detección de los modelos que se han vuelto inactivos buscando los modelos que no se usaron en los últimos tres minutos \[ [1](#endnote-1)\]y, a continuación, expulsión de ellos. Si no hay ningún modelo para expulsar inactiva, el servicio Power BI busca expulsar los modelos de carga para las operaciones en segundo plano. Un último recurso después de 30 segundos de intentos fallidos \[ [1](#endnote-1)\], es un error en la operación interactiva. En este caso, se notifica al usuario de informe de error con una sugerencia que vuelva a intentarlo. En algunos casos, los modelos pueden descargarse de memoria debido a las operaciones de servicio.

Es importante resaltar que la expulsión del conjunto de datos es un comportamiento normal y esperado. Se esfuerza por maximizar el uso de memoria mediante la carga y descarga modelos cuyos tamaños combinados pueden superar la memoria disponible. Esto es así por diseño y completamente transparente para los usuarios de informes. Las tasas de expulsión alta no necesariamente que insuficientemente es con la capacidad de los recursos. Sin embargo, pueden, convertirse en un problema si está experimentando la capacidad de respuesta de consulta o actualización debido a las tarifas de expulsión alta.

Las actualizaciones de los modelos de importación son siempre uso intensivo de memoria como modelos deben cargarse en memoria. Memoria adicional es necesaria para el procesamiento. Una actualización completa puede utilizar aproximadamente el doble de memoria requerida por el modelo. Esto garantiza que el modelo se puede consultar incluso cuando se procesa, porque las consultas se envían al modelo existente, hasta que se ha completado la actualización y los datos del modelo nuevo están disponibles. Actualización incremental requerirá menos memoria y se complete más rápido y, por lo que puede reducir significativamente la presión sobre los recursos de capacidad. Las actualizaciones también pueden ser intensivo de CPU para los modelos, especialmente aquellos con transformaciones complejas de Power Query o tablas o columnas calculadas que son complejas o se basan en tablas grandes.

Las actualizaciones, como las consultas, requieren que el modelo se cargan en memoria. Si hay suficiente memoria, el servicio Power BI intentará expulsar modelos inactivos y, si esto no es posible (como todos los modelos están activos), el trabajo de actualización se pone en cola. Las actualizaciones son normalmente consumen mucha CPU, incluso mucho más que las consultas. Por este motivo, hay límites de capacidad en el número de actualizaciones simultáneas, que se establece en 1,5 veces el número de núcleos de virtuales back-end, redondeado al alza. Si hay demasiadas actualizaciones simultáneas, una actualización programada se pondrá en cola. Cuando se producen estas situaciones, tarda más tiempo para completar la actualización. Actualiza y a petición como los que desencadena una solicitud de usuario o una llamada de API volverá a intentar tres veces \[ [1](#endnote-1)\]. Si aún no existen suficientes recursos, a continuación, se producirá un error de la actualización.

Notas de la sección:   
<a name="endnote-1"></a>\[1\] sujeta a cambios.

### <a name="regional-support"></a>Soporte técnico regional

Al crear una nueva capacidad, los administradores globales de Office 365 y administradores del servicio Power BI puede especificar residirá una región donde las áreas de trabajo asignados a la capacidad. Esto se conoce como **Multigeográficas**. Con Multigeográficas, las organizaciones pueden cumplir los requisitos de residencia de datos mediante la implementación de contenido en los centros de datos en una región específica, incluso si es diferente de la región en la que reside la suscripción a Office 365. Para obtener más información, consulte [Multigeográficas compatibilidad con Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Administración de la capacidad

Administración de las capacidades Premium implica crear o eliminando las capacidades, asignar los administradores, asignar áreas de trabajo, la configuración de cargas de trabajo, supervisión y realizar ajustes para optimizar el rendimiento de la capacidad. 

Los administradores globales de Office 365 y administradores del servicio Power BI pueden crear las capacidades Premium de núcleos virtuales disponibles o modificar las capacidades Premium existentes. Cuando se crea una capacidad, se especifican el tamaño de la capacidad y la región geográfica y se asigna al menos un administrador. 

Cuando se crean las capacidades, la mayoría de las tareas administrativa se completa en el [del portal de administración](service-admin-portal.md).

![Portal de administración](media/service-premium-what-is/premium-admin-portal.png)

Los administradores de capacidad pueden asignar áreas de trabajo a la capacidad, administrar permisos de usuario y asignar otros administradores. Los administradores de capacidad también pueden configurar cargas de trabajo, ajustar las asignaciones de memoria y si es necesario, reinicie una capacidad, las operaciones en el caso de una sobrecarga de la capacidad de restablecer.

![Portal de administración](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Los administradores de capacidad también pueden asegurarse de que una capacidad está ejecutándose sin problemas. Puede supervisar el derecho de estado de capacidad en el portal de administración o mediante la aplicación de las métricas de capacidad Premium.

Para obtener información sobre la creación las capacidades, asignar los administradores y asignar las áreas de trabajo, consulte [las capacidades Premium administrar](service-premium-capacity-manage.md). Para más información acerca de los roles, consulte [relacionadas con roles de administrador de Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Supervisión

Supervisión de las capacidades Premium proporciona a los administradores comprender cómo funcionan las capacidades. Las capacidades se pueden supervisar mediante el portal de administración y el [métricas de capacidad de Power BI Premium app](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

Supervisión en el portal proporciona una vista rápida con métricas de alto nivel que indica la carga colocado y los recursos usados por la capacidad, calcula el promedio, en los últimos siete días. 

![Portal de administración](media/service-premium-what-is/premium-admin-portal-health.png)

El **métricas de capacidad de Power BI Premium** aplicación proporciona la información más detallada en el rendimiento de sus capacidades. La aplicación proporciona un alto nivel panel e informes más detallados.

![Panel de métricas de la aplicación](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Desde el panel de la aplicación puede hacer clic en una celda de la métrica para abrir un informe detallado. Los informes proporcionan métricas detalladas y la capacidad de filtrado para explorar en profundidad la información más importante necesitan mantener sus capacidades funcionando sin problemas.

![Recuentos de indican posible saturación de la CPU de tiempo de espera de picos periódicos de consulta](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Para obtener más información acerca de las capacidades de supervisión, consulte [supervisión en el portal de administración de Power BI](service-admin-premium-monitor-portal.md) y [supervisión con la aplicación de las métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Capacidades de optimización

Sacando el máximo partido de sus capacidades es fundamental para garantizar a los usuarios obtener el rendimiento y le esté sacando el máximo partido de su inversión en Premium. Al supervisar las métricas clave, los administradores pueden determinar cuál es la mejor solucionar los cuellos de botella y tomar las medidas necesarias. Para obtener más información, consulte [las capacidades Premium optimizar](service-premium-capacity-optimize.md) y [escenarios de capacidad Premium](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>Capacidades de las API de REST

Las API de REST de Power BI incluyen una colección de [API capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities). Con las API, los administradores pueden administrar mediante programación muchos aspectos de sus capacidades Premium, incluidas la habilitación y deshabilitación de las cargas de trabajo, la asignación de áreas de trabajo a una capacidad y mucho más.

## <a name="large-datasets"></a>Grandes conjuntos de datos

Según la SKU, Power BI Premium permite cargar archivos de modelo de Power BI Desktop (.pbix) hasta un máximo de **10 GB** de tamaño. Cuando carga, el modelo, a continuación, puede publicarse en un área de trabajo asignado a una capacidad Premium. El conjunto de datos, a continuación, se puede actualizar hasta **12 GB** de tamaño.

### <a name="size-considerations"></a>Consideraciones de tamaño

Los modelos grandes pueden consumir muchos recursos. Debe tener al menos una SKU P1 para cualquier modelo mayor de 1 GB. Aunque publicar modelos grandes en las áreas de trabajo respaldada por SKU hasta A3 podría trabajo, actualizarlos a no funcionará.

La tabla siguiente describe las SKU recomendadas para diversos tamaños de .pbix:

   |SKU  |Tamaño de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | hasta 10 GB   |

La SKU A4 de Power BI Embedded es igual a SKU P1, A5 = P2 y A6 = P3. Tenga en cuenta que la publicación de grandes modelos para A y SKU EM podría devolver errores que no son específicos del error de limitación de tamaño de modelo en la capacidad compartida. Los errores de actualización de modelos grandes en A y SKU EM es probable que apunten a errores relativos a los tiempos de espera. 

Los archivos .pbix representan datos en un *estado altamente comprimido*. Los datos probablemente se expandirán varias veces al cargarse en memoria y, a partir de ahí, podrían expandirse varias veces más durante la actualización de datos.

Actualización programada de grandes conjuntos de datos puede tardar mucho tiempo y consumir muchos recursos. Es importante no programe demasiadas actualizaciones superpuestas. Se recomienda [actualización incremental](service-premium-incremental-refresh.md) está configurado, ya que es más rápida y confiable y consume menos recursos.

La carga inicial de informes de grandes conjuntos de datos puede tardar mucho tiempo si ha pasado un tiempo desde la última vez que se usó el conjunto de datos. Una barra de carga para los informes de carga larga muestra el progreso de carga.

Mientras que las restricciones de tiempo y memoria por consulta son mucho mayores en capacidad Premium, se recomienda que usar los filtros y segmentaciones de datos para los objetos visuales muestren únicamente lo que sea necesario.

## <a name="incremental-refresh"></a>Actualización incremental

Actualización incremental proporciona una parte integral de tener y mantenimiento de grandes conjuntos de datos en Power BI Premium. Actualización incremental tiene muchas ventajas, por ejemplo, las actualizaciones son más rápidas porque solo los datos que tiene modificada debe actualizarse. Las actualizaciones son más confiables, ya no es necesario mantener las conexiones de larga ejecución con orígenes de datos volátiles. Se reduce el consumo de recursos porque menos datos para actualizar reduce el consumo total de memoria y otros recursos. Directivas de actualización incremental se definen en **Power BI Desktop**y se aplica cuando se publican en un área de trabajo en una capacidad Premium. 

![Detalles de la actualización](media/service-premium-incremental-refresh/refresh-details.png)

Para obtener más información, consulte [actualización Incremental en Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Informes paginados

Informes paginados, compatibles con P1-P3 y A4_A6 SKU, se basan en la tecnología de lenguaje RDL (Report Definition Language) de SQL Server Reporting Services. Mientras se basa en tecnología RDL, no es el mismo que el servidor de informes de Power BI, que es una plataforma de informes descargable que se puede instalar en el entorno local, que también se incluye con Power BI Premium. Informes paginados se formatean para ajustarse a una página que se puede imprimir o compartir. Datos se muestran en una tabla, incluso si la tabla abarca varias páginas. Mediante el uso de la versión gratuita [ **generador de informes de Power BI** ](https://go.microsoft.com/fwlink/?linkid=2086513) aplicación de escritorio de Windows, autor de los usuarios paginado informes y publicarlos en el servicio.

En Power BI Premium, Paginated informes son una carga de trabajo que debe habilitarse para una capacidad mediante el portal de administración. Los administradores de capacidad se pueden habilitar y, a continuación, especifique la cantidad de memoria como un porcentaje total de la capacidad recursos de memoria. A diferencia de otros tipos de cargas de trabajo, Premium ejecuta informes paginados en un espacio contenido dentro de la capacidad. La memoria máxima especificada para este espacio se utiliza si la carga de trabajo está activo. El valor predeterminado es 20%. 

Para obtener más información, consulte [informes en Power BI Premium paginados](paginated-reports-report-builder-power-bi.md). Para más información acerca de cómo habilitar la carga de trabajo de informes Paginated, consulte [configurar cargas de trabajo](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI Report Server
 
Con Power BI Premium, Power BI Report Server incluye un *local* servidor de informes con un portal web. Puede compilar a su BI entorno local y distribuya informes detrás del firewall de su organización. Servidor de informes proporciona a los usuarios acceso a enriquecidos, interactivos y capacidades de generación de informes empresariales de SQL Server Reporting Services. Los usuarios pueden explorar los datos visuales y descubran rápidamente patrones para tomar decisiones más rápidas y mejor. Servidor de informes proporciona gobierno en sus propios términos. Cuando llegue el momento, Power BI Report Server facilita la migración a la nube, donde su organización puede aprovechar al máximo toda la funcionalidad de Power BI Premium.

Para obtener más información, consulte [Power BI Report Server](report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Uso compartido de contenido ilimitado

Con Premium, cualquier usuario, ya sea dentro o fuera de su organización pueden ver el contenido de Power BI, incluidos los informes paginados e interactivos sin tener que adquirir licencias individuales. 

![Uso compartido de contenido](media/service-premium-what-is/premium-sharing.png)

Premium permite la distribución generalizada del contenido por los usuarios Pro sin necesidad de licencias de Pro para los destinatarios que ver el contenido. Licencias de Pro son necesarias para los creadores de contenido. Creadores de conexión a orígenes de datos, datos del modelo y creación paneles e informes que están empaquetados como aplicaciones de área de trabajo. 

Para obtener más información, consulte [licencias de Power BI](service-admin-licensing-organization.md).

## <a name="tool-connectivity-preview"></a>Conectividad de la herramienta (versión preliminar)

Internamente, la empresa probada Microsoft **motor Vertipaq de Analysis Services** alimenta conjuntos de datos de Power BI. Analysis Services proporciona la capacidad de programación y herramientas y la aplicación cliente se admiten a través de las bibliotecas de cliente y las API que admiten el protocolo de estándar abierto XMLA. Actualmente, los conjuntos de datos de Power BI Premium admiten *de sólo lectura* las operaciones de Microsoft y las aplicaciones cliente de terceros y las herramientas a través de **los puntos de conexión XMLA**. 

Herramientas de Microsoft, como SQL Server Management Studio y SQL Server Profiler y las aplicaciones de terceros como Studio DAX y las aplicaciones de visualización de datos, pueden conectarse y consultar conjuntos de datos Premium mediante XMLA, MDX, DAX, DMV y seguimiento de eventos. 

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)

Para obtener más información, consulte [conectarse a conjuntos de datos con herramientas y aplicaciones cliente](service-premium-connect-tools.md).

## <a name="acknowledgements"></a>Confirmaciones

Peter Myers, MVP de la plataforma de datos y experto en BI independiente con [bit a bit soluciones](https://www.bitwisesolutions.com.au/), y el Microsoft Power BI Customer Advisory Team (CAT) son los principales colaboradores a este artículo.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Administración de las capacidades Premium](service-premium-capacity-manage.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

||||||
