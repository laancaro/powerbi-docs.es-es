---
title: 'Informes paginados en Power BI: Preguntas frecuentes'
description: En este artículo se responden las preguntas más frecuentes sobre los informes paginados. Estos informes son el resultado de píxel perfecto con formato de alta calidad optimizado para impresión o generación en PDF.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: c1f8a274a17d85cf8f86d2e33ff63f3e9b686742
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "74831230"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Informes paginados en Power BI: Preguntas frecuentes 

En este artículo se responden las preguntas más frecuentes sobre los informes paginados. Estos informes son el resultado de píxel perfecto con formato de alta calidad optimizado para impresión o generación en PDF. Se denominan "paginados" porque presentan un formato apto para abarcar varias páginas. Los informes paginados se basan en la tecnología de informe RDL de SQL Server Reporting Services. 

En este artículo se responden muchas preguntas comunes que los usuarios se plantean sobre los informes paginados en Power BI Premium y sobre el generador de informes, la herramienta independiente para crear informes paginados. Necesita una licencia de Power BI Pro para publicar un informe en el servicio. Puede publicar y compartir informes paginados en Mi área de trabajo o en las áreas de trabajo, siempre que el área de trabajo tenga una capacidad Power BI Premium. 

## <a name="administration"></a>Administración

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>¿Qué tamaño de capacidad Premium se necesita para los informes paginados?

La carga de trabajo de los informes paginados está disponible en las SKU P1 – P3.  También puede usarla con las SKU A4 – A6 para escenarios de inserción o de desarrollo y pruebas.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>¿Cuál es el umbral de memoria máxima que puedo asignar para los informes paginados en mi capacidad?

Puede usar hasta el 100 % de la memoria en esta carga de trabajo.

### <a name="how-does-user-access-work-for-paginated-reports"></a>¿Cómo funciona el acceso de usuario en los informes paginados?

El acceso de usuario en los informes paginados funciona de la misma forma que el acceso de usuario al resto del contenido del servicio Power BI. 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>¿Cómo se puede activar o desactivar la carga de trabajo de los informes paginados?

El administrador puede habilitar o deshabilitar la carga de trabajo de los informes paginados en la página del portal de administración de capacidad.  De forma predeterminada, la carga de trabajo estará activada en las nuevas capacidades que cree.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>¿Cómo se puede supervisar el uso de los informes paginados en mi inquilino?

En los registro de auditoría de Office 365 se detalla el uso de este tipo de informe en los siguientes eventos: 

- Visualización del informe de Power BI
- Eliminación del informe de Power BI
- Creación del informe de Power BI
- Informe de Power BI descargado

El campo ReportType tiene el valor "PaginatedReport" para identificar los informes paginados en lugar de los informes de Power BI.

Además, los registros de auditoría proporcionan los siguientes eventos para los informes paginados:

- Conjunto de datos de Power BI enlazado a la puerta de enlace
- Detección del origen de datos de Power BI
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>¿Puedo supervisar esta carga de trabajo con la aplicación de supervisión de capacidad Premium?

Sí, la supervisión está disponible como una nueva pestaña con los mismos detalles pertinentes que los conjuntos de datos de Power BI.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>¿Necesito una licencia Pro para crear y publicar informes paginados?

Puede cargar informes paginados en Mi área de trabajo sin una licencia Pro, siempre que sea en una capacidad premium.  En el caso de otras áreas de trabajo, debe tener una licencia Pro para crear y publicar contenido en ellas. Le recomendamos que descargue y use el Generador de informes de Power BI incluso sin la licencia Pro, aunque sin ella no podrá publicar los informes paginados. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>¿Qué ocurre si tengo un informe paginado en un área de trabajo y se desactiva la carga de trabajo del informe paginado?

Recibe un mensaje de error y no se puede ver el informe hasta que la carga de trabajo se vuelve a activar. Todavía puede eliminar el informe del área de trabajo.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>¿Cuál es la memoria predeterminada para cada una de las SKU Premium que se admite en los informes paginados?

Memoria predeterminada de cada SKU Premium en los informes paginados:

- **P1/A4**: 20 % predeterminado; 10 % mínimo
- **P2/A5**: 20 % predeterminado; 5 % mínimo
- **P3/A6**: 20 % predeterminado; 2,5 % mínimo

## <a name="general"></a>General

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>¿Cuándo debo usar un informe paginado en lugar de un informe de Power BI?

Los informes paginados son los más convenientes para escenarios que requieren un resultado de píxel perfecto con formato de alta calidad optimizado para impresión o generación en PDF.  Un estado de ganancias y pérdidas es un buen ejemplo del tipo de informe que probablemente desea crear como un informe paginado.  

Los informes de Power BI están optimizados para la exploración e interactividad.  Un informe de ventas donde diferentes vendedores desean segmentar los datos en el mismo informe por región, sector y cliente específicos y ver cómo cambian las cifras se representaría mejor como un informe de Power BI.

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>En esta documentación se indica que el Generador de informes de Power BI es la herramienta de creación preferida. ¿Puedo crear informes paginados de SQL Server Data Tools para Power BI?

Sí, pero el servicio Power BI solo permite cargar un solo elemento a la vez, por lo que muchos de los escenarios que los autores usan con SQL Server Data Tools (SSDT) aún no son compatibles. Consulte la [lista de características compatibles](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) completa disponible más adelante en este artículo de preguntas frecuentes.  

### <a name="what-versions-of-report-builder-do-you-support"></a>¿Qué versiones del generador de informes se admiten?

Recientemente, publicamos el Generador de informes de Power BI como la principal herramienta de creación de informes paginados en el servicio Power BI. Instale el [Generador de informes de Power BI desde el Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>¿Cómo se pueden mover a Power BI los informes existentes guardados en SQL Server Reporting Services?

Debe descargar el informe del servidor y luego cargarlo en Power BI mediante el portal.  Actualmente no existe ninguna herramienta de migración disponible, pero estamos pensando en crear una vez finalizada la versión preliminar pública y tras obtener el nivel adecuado de paridad de características entre los productos.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>¿Puedo abrir informes y publicarlos directamente en el servicio?

Sí. Recientemente hemos agregado compatibilidad para abrir informes y publicarlos directamente en el servicio desde el Generador de informes de Power BI.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>¿Qué características de los informes paginados de SSRS no son compatibles aún en Power BI?

Actualmente, los informes paginados no admiten los siguientes elementos:

- Orígenes de datos compartidos
- Conjuntos de datos compartidos
- Subinformes
- Obtención de detalles y acciones de clic a otros informes
- Informes vinculados
- Capas de mapa de Bing
- Fuentes personalizadas

Obtiene un mensaje si intenta cargar un archivo que tiene una característica incompatible en el servicio Power BI, que no sea alternar u ordenar.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>¿Qué orígenes de datos se admiten actualmente para los informes paginados?

Consulte el artículo [Orígenes de datos admitidos para informes paginados de Power BI](paginated-reports-data-sources.md) para obtener una lista de orígenes de datos. 

### <a name="what-authentication-methods-do-you-support"></a>¿Qué métodos de autenticación se admiten?

Se admite SSO para los orígenes de datos de Azure Analysis Services, Azure SQL Database y Power BI.  También se admite OAuth para Azure SQL Database y Azure Analysis Services.  Con otros orígenes de datos, actualmente debe almacenar un nombre de usuario y una contraseña con el origen de datos en el portal o la puerta de enlace.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>¿Puedo usar un conjunto de datos de Power BI como origen de datos de mi informe paginado?

Sí, se admiten conjuntos de datos de Power BI como orígenes de datos para los informes paginados.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>¿Se pueden usar procedimientos almacenados a través de la puerta de enlace?

Puede usar un procedimiento almacenado a través de la puerta de enlace, pero es posible que haya problemas en determinados escenarios si el procedimiento almacenado incluye parámetros.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>¿Qué formatos de exportación están disponibles para el informe en el servicio Power BI?

Puede exportar a Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, MHTML, XML y CSV.

### <a name="can-i-print-paginated-reports"></a>¿Puedo imprimir informes paginados?

Sí, la impresión está disponible para los informes paginados e incluye una experiencia de vista previa de impresión nueva y mejorada. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>¿Las suscripciones de correo electrónico están disponibles para los informes paginados?

Sí, las suscripciones por correo electrónico se admiten completamente para los informes paginados e incluyen compatibilidad con seis formatos de archivo y valores de parámetro diferentes.

### <a name="can-i-run-custom-code-in-my-report"></a>¿Puedo ejecutar código personalizado en mi informe?

Sí, se admite la capacidad de ejecutar código en los informes de la misma forma que en SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>¿Puedo usar Power BI Embedded para insertar los informes paginados en una aplicación que estoy hospedando?

Ya está disponible la inserción de SaaS, incluida la compatibilidad con la inserción segura.  La compatibilidad con la inserción de PaaS está planeada para más adelante este año.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>¿Puedo extraer los detalles de un informe de Power BI en un informe paginado?

Sí, puede hacerlo mediante parámetros URL con los informes paginados.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>¿Puedo compartir el contenido de un informe paginado mediante una aplicación de Power BI?

Sí, se pueden implementar informes paginados con aplicaciones de las áreas de trabajo v1 y v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>¿Otras características específicas de informes de Power BI, como el anclaje de los iconos de informes en los paneles, funcionan con los informes paginados?

Planeamos que los informes admitan lo máximo posible los mismos escenarios importantes en el servicio.  Lo ideal es que, aunque la herramienta de creación es diferente, desde la perspectiva del consumidor, es simplemente otro informe en su lista en el portal. No les preocupa cómo se creó, ya que pueden hacer lo que necesitan.  Un buen ejemplo de esta paridad de características es la compatibilidad planeada con los comentarios. Aunque la propia característica puede funcionar de forma ligeramente diferente para cada tipo de informe, podrá utilizar comentarios para ambos.

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>¿Se prevé alguna herramienta de migración para que los clientes de SSRS puedan mover los informes y recursos existentes a Power BI?

Los proyectos de GitHub admiten ahora la migración de contenido de SQL Server Reporting Services a Power BI.  Vea los detalles y descargue aquí la herramienta: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>¿Existe un control del visor de informes para los informes paginados en el servicio Power BI?

No, actualmente no se encuentra disponible ningún control del visor de informes.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>¿Se pueden buscar informes paginados con la nueva experiencia de inicio del servicio Power BI?

Sí, ahora puede buscar los informes paginados desde la sección de inicio.  También podrá verlos en otras partes de la nueva experiencia de inicio.

## <a name="next-steps"></a>Pasos siguientes

- [Instalación del Generador de informes de Power BI desde el Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Crear un informe paginado](paginated-reports-quickstart-aw.md)
