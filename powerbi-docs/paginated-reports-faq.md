---
title: 'Informes paginados en Power BI: Preguntas frecuentes (versión preliminar)'
description: En este artículo se responden las preguntas más frecuentes sobre los informes paginados. Estos informes son el resultado de píxel perfecto con formato de alta calidad optimizado para impresión o generación en PDF.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.openlocfilehash: cedf72585d7aa4f2ece39739dc0bdba33ca66e21
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "60987794"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Informes paginados en Power BI: Preguntas frecuentes (versión preliminar)

En este artículo se responden las preguntas más frecuentes sobre los informes paginados. Estos informes son el resultado de píxel perfecto con formato de alta calidad optimizado para impresión o generación en PDF. Se denominan "paginados" porque presentan un formato apto para abarcar varias páginas. Los informes paginados se basan en la tecnología de informe RDL de SQL Server Reporting Services. 

En este artículo se responden muchas preguntas comunes que los usuarios se plantean sobre los informes paginados en Power BI Premium y sobre el generador de informes, la herramienta independiente para crear informes paginados. Necesita una licencia de Power BI Pro para publicar un informe en el servicio. Puede publicar y compartir informes paginados en Mi área de trabajo o en las áreas de trabajo de la aplicación, siempre que el área de trabajo tenga una capacidad Premium de Power BI. 

## <a name="administration"></a>Administración

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>¿Qué tamaño de capacidad Premium se necesita para los informes paginados?

La carga de trabajo de los informes paginados está disponible en las SKU P1 – P3 para la versión preliminar pública.  También puede usarla para escenario de desarrollo y pruebas con las SKU A4 – A6.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>¿Cuál es el umbral de memoria máxima que puedo asignar para los informes paginados en mi capacidad?

Actualmente, solo puede reservar el 50 % de la memoria para esta carga de trabajo. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>¿Cómo funciona el acceso de usuario en los informes paginados?

El acceso de usuario en los informes paginados funciona de la misma forma que el acceso de usuario al resto del contenido del servicio Power BI. 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>¿Cómo se puede activar o desactivar la carga de trabajo de los informes paginados?

El administrador puede habilitar o deshabilitar la carga de trabajo de los informes paginados en la página del portal de administración de capacidad.  

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

Sí. No se pueden cargar informes en el área de trabajo sin una licencia Pro. Le recomendamos que descargue y use el generador de informes de Power BI incluso sin la licencia de Pro, pero no se puede publicar los informes paginados creados sin él. 

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

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>La documentación indica que el generador de informes de Power BI es la herramienta de creación preferida. ¿Puedo crear informes paginados de SQL Server Data Tools para Power BI?

Sí, pero el servicio Power BI solo permite cargar un solo elemento a la vez, por lo que muchos de los escenarios que los autores usan con SQL Server Data Tools (SSDT) aún no son compatibles. Consulte la [lista de características compatibles](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) completa disponible más adelante en este artículo de preguntas frecuentes.  

### <a name="what-versions-of-report-builder-do-you-support"></a>¿Qué versiones del generador de informes se admiten?

Recientemente, publicamos el generador de informes de Power BI como la principal herramienta de creación para los informes paginados en el servicio Power BI. Instalar [Power generador de informes de BI desde el centro de descarga de Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>¿Cómo se pueden mover a Power BI los informes existentes guardados en SQL Server Reporting Services?

Debe descargar el informe del servidor y luego cargarlo en Power BI mediante el portal.  Actualmente no existe ninguna herramienta de migración disponible, pero estamos pensando en crear una vez finalizada la versión preliminar pública y tras obtener el nivel adecuado de paridad de características entre los productos.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>¿Puedo abrir informes y publicarlos directamente en el servicio?

En este momento, no. Estamos agregando compatibilidad para abrir informes y publicarlos directamente al servicio Power BI del generador de informes antes de GA, igual que con Power BI Desktop.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>¿Qué características de los informes paginados de SSRS no son compatibles aún en Power BI?

Actualmente, los informes paginados no admiten los siguientes elementos:

- Orígenes de datos compartidos
- Conjuntos de datos compartidos
- Subinformes
- Acciones de clic y obtención de detalles
- Informes vinculados
- Marcadores
- Capas de mapa de Bing
- Fuentes personalizadas

Obtiene un mensaje si intenta cargar un archivo que tiene una característica incompatible en el servicio Power BI, que no sea alternar u ordenar.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>¿Qué orígenes de datos se admiten actualmente para los informes paginados?

Se admite el origen de datos siguientes: 

- Conjuntos de datos de Power BI Premium
- Azure Analysis Services (a través de inicio de sesión único (SSO))
- Azure SQL Database
- SQL Server*
- SQL Server Analysis Services (SSAS) tabular (DAX) y los modelos multidimensionales (MDX) * 
- Oracle* 
- Teradata* 

* requiere la puerta de enlace local.

Al acceder a SSAS a través de la puerta de enlace, el usuario cuyas credenciales están almacenadas necesita permisos elevados en SSAS para trabajar a través de la puerta de enlace.

### <a name="what-authentication-methods-do-you-support"></a>¿Qué métodos de autenticación se admiten?

Admitimos el inicio de sesión único para los orígenes de datos de Azure Analysis Services y Power BI Premium.  Para los demás orígenes de datos, actualmente debe almacenar un nombre de usuario y una contraseña con el origen de datos en el portal o la puerta de enlace.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>¿Puedo usar un conjunto de datos de Power BI como origen de datos de mi informe paginado?

Sí, ahora se admiten conjuntos de datos de Power BI Premium como orígenes de datos para los informes paginados.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>¿Se pueden usar procedimientos almacenados a través de la puerta de enlace?

Puede usar un procedimiento almacenado a través de la puerta de enlace, pero es posible que haya problemas en determinados escenarios si el procedimiento almacenado incluye parámetros.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>¿Qué formatos de exportación están disponibles para el informe en el servicio Power BI?

Puede exportar a Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, MHTML, XML y CSV.

### <a name="can-i-print-paginated-reports"></a>¿Puedo imprimir informes paginados?

Sí, la impresión está disponible para los informes paginados, incluida una experiencia de vista previa de impresión nuevas y mejoradas. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>¿Ya están disponibles las suscripciones de correo electrónico para los informes paginados?

No, las suscripciones de correo electrónico se incorporarán próximamente.

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>¿Qué características de SSRS se admitirán en el servicio Power BI?

Nuestro plan es proporcionar paridad de características para la mayoría de los escenarios, pero hay determinados elementos de SSRS y Power BI que quizá no tenga sentido cambiar para ajustarse a los patrones existentes de SSRS.  Por ejemplo, los modelos de permisos diferentes de Power BI no pueden asignarse a SSRS.  Tomaremos ese tipo de decisiones en base a los comentarios de los clientes y los partners.

### <a name="can-i-run-custom-code-in-my-report"></a>¿Puedo ejecutar código personalizado en mi informe?

Sí, se admite la capacidad de ejecutar código en los informes de la misma forma que en SSRS.

### <a name="does-this-mean-ssrs-is-going-away"></a>¿Eso significa que SSRS va a desaparecer?

En absoluto.  Esta nueva oferta proporciona a los clientes una opción basada en la nube para sus informes paginados.  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>¿Puedo usar Power BI Embedded para insertar los informes paginados en una aplicación que estoy hospedando?

Tenemos previsto admitir este escenario con las API de Power BI existentes, pero aún no contamos con un período de tiempo para saber cuándo estará disponible este escenario.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>¿Puedo extraer los detalles de un informe de Power BI en un informe paginado?

Todavía no, pero planeamos admitir este escenario sin duda alguna.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>¿Puedo compartir el contenido de un informe paginado mediante una aplicación de Power BI?

Sí, se admiten informes paginados para implementarse con las aplicaciones de las áreas de trabajo v1 y v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>¿Otras características específicas de informes de Power BI, como el anclaje de los iconos de informes en los paneles, funcionan con los informes paginados?

Planeamos que los informes admitan lo máximo posible los mismos escenarios importantes en el servicio.  Lo ideal es que, aunque la herramienta de creación es diferente, desde la perspectiva del consumidor, es simplemente otro informe en su lista en el portal. No les preocupa cómo se creó, ya que pueden hacer lo que necesitan.  Un buen ejemplo de esta paridad de características es la compatibilidad planeada con los comentarios. Aunque la propia característica puede funcionar de forma ligeramente diferente para cada tipo de informe, podrá utilizar comentarios para ambos.

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>¿Se prevé alguna herramienta de migración para que los clientes de SSRS puedan mover los informes y recursos existentes a Power BI?

Estamos evaluando distintas opciones para permitir mover el contenido a Power BI de forma automática, pero esto no estará disponible hasta después de la disponibilidad general.

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>¿Alguna vez será posible crear tanto los informes paginados como los informes de Power BI en una única herramienta de creación?

Posiblemente.  Actualmente estamos estudiando la forma de permitir este escenario; puede que simplemente distribuyamos las herramientas de creación todas juntas como un único conjunto de BI o que ofrezcamos descargas individuales o personalización de marcas.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>¿Existe un control del visor de informes para los informes paginados en el servicio Power BI?

No, actualmente no se encuentra disponible ningún control del visor de informes.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>¿Se pueden buscar informes paginados con la nueva experiencia de inicio del servicio Power BI?

No, actualmente no puede buscar los informes paginados desde la sección de inicio.  Sin embargo, los verá en otras partes de la nueva experiencia de inicio.

## <a name="next-steps"></a>Pasos siguientes

- [Instalar al generador de informes de BI energía desde el centro de descarga de Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Crear un informe paginado](paginated-reports-quickstart-aw.md)
