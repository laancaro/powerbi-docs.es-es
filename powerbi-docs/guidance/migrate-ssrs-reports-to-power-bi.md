---
title: Migración de informes de SQL Server Reporting Services a Power BI
description: Instrucciones para ayudarle a migrar los informes de SQL Server Reporting Services (SSRS) a Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: e65dd42e8ec787d0c6edba534f79cdb06e5ba14c
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527301"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Migración de informes de SQL Server Reporting Services a Power BI

Este artículo está dirigido a los autores de informes de SQL Server Reporting Services (SSRS) y a los administradores de Power BI. Proporciona instrucciones para ayudarle a migrar los informes de [lenguaje RDL (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) a Power BI.

> [!NOTE]
> Solo se pueden migrar informes RDL. En Power BI, los informes RDL se denominan _informes paginados_.

Las instrucciones se dividen en cuatro etapas. Se recomienda leer primero el artículo completo antes de migrar los informes.

1. [Antes de comenzar](#before-you-start)
1. [Etapa previa a la migración](#pre-migration-stage)
1. [Etapa de migración](#migration-stage)
1. [Etapa posterior a la migración](#post-migration-stage)

Puede lograr la migración a los servidores de SSRS sin tiempo de inactividad ni interrupciones para los usuarios del informe. Es importante comprender que no es necesario quitar ningún dato o informe. Por lo tanto, puede mantener su entorno actual en su lugar hasta que esté a punto para su retirada.

## <a name="before-you-start"></a>Antes de comenzar

Antes de iniciar la migración, debe comprobar que el entorno cumple ciertos requisitos previos. Describiremos estos requisitos previos y también le presentaremos una herramienta de migración útil.

### <a name="preparing-for-migration"></a>Preparación de la migración

Al preparar la migración de los informes a Power BI, compruebe primero que la organización tiene una suscripción a [Power BI Premium](../service-premium-what-is.md). Esta suscripción es necesaria para hospedar y ejecutar los informes paginados de Power BI.

### <a name="supported-versions"></a>Versiones compatibles

Puede migrar instancias de SSRS que se ejecutan de forma local o en máquinas virtuales hospedadas por proveedores de nube, como Azure.

En la siguiente lista se describen las versiones de SQL Server admitidas para la migración a Power BI:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

También es posible realizar la migración desde Power BI Report Server.

### <a name="migration-tool"></a>Herramienta de migración

Se recomienda usar la [herramienta de migración de RDL](https://github.com/microsoft/RdlMigration) para ayudar a preparar y migrar los informes. Microsoft desarrolló esta herramienta para ayudar a los clientes a migrar informes RDL desde sus servidores SSRS a Power BI. Está disponible en GitHub y documenta un tutorial de un extremo a otro del escenario de migración.

La herramienta automatiza las tareas siguientes:

- Comprueba [orígenes de datos no admitidos](../paginated-reports-data-sources.md) y [características de informe no admitidas](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi).
- Convierte cualquier _recurso compartido_ en recursos _incrustados_:
  - Los **orígenes de datos** compartidos se convierten en orígenes de datos incrustados.
  - Los **conjuntos de datos** compartidos se convierten en conjuntos de datos incrustados.
- Publica los informes que superan las comprobaciones, como informes paginados en un área de trabajo de Power BI especificada (en una capacidad Premium).

No modifica ni quita los informes existentes. Al finalizar, la herramienta genera un resumen de todas las acciones completadas correcta o incorrectamente.

Con el tiempo, Microsoft puede mejorar la herramienta. También animamos a la comunidad a contribuir y ayudar a mejorarla.

## <a name="pre-migration-stage"></a>Etapa previa a la migración

Después de comprobar que la organización cumple los requisitos previos, todo está listo para iniciar la etapa _previa a la migración_. Esta etapa tiene tres partes:

1. Descubrir
1. Evaluar
1. Preparar

### <a name="discover"></a>Descubrir

El objetivo de la fase de _Detección_ es identificar las instancias existentes de SSRS. Este proceso implica el examen de la red para identificar todas las instancias de SQL Server de la organización.

Puede usar [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826). También conocida como "MAP Toolkit", esta herramienta detecta y notifica las instancias de SQL Server, las versiones y las características instaladas. Se trata de una herramienta eficaz para el inventario, la valoración y la elaboración de informes que puede simplificar el proceso de planeamiento de la migración.

### <a name="assess"></a>Evaluar

Una vez detectadas las instancias de SSRS, el objetivo de la fase de _Evaluación_ es comprender los informes de SSRS, o elementos de servidor, que no se pueden migrar.

Solo los informes RDL se pueden migrar desde los servidores SSRS a Power BI. Cada informe RDL migrado se convertirá en un informe paginado de Power BI.

Sin embargo, los siguientes tipos de elementos SSRS no se pueden migrar a Power BI:

- Orígenes de datos compartidos <sup>1</sup>
- Conjuntos de datos compartidos <sup>1</sup>
- Recursos, como archivos de imagen
- KPI (SSRS 2016 o posterior; solo Enterprise Edition)
- Informes móviles (SSRS 2016 o posterior; solo Enterprise Edition)
- Modelos de informes (en desuso)
- Partes de informes (en desuso)

<sup>1</sup> La [herramienta de migración de RDL](https://github.com/microsoft/RdlMigration) convierte automáticamente los orígenes de datos compartidos y los conjuntos de datos compartidos, lo que les permite usar orígenes de datos admitidos.

Si los informes de RDL dependen de las características [que todavía no se admiten para los informes paginados de Power BI](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), puede planear volver a desarrollarlos como [informes de Power BI](../consumer/end-user-reports.md). Aunque incluso los informes RDL se pueden migrar, se recomienda que considere modernizarlos como informes de Power BI, cuando corresponda.

Si los informes RDL necesitan recuperar datos de _orígenes de datos locales_, no pueden usar el inicio de sesión único (SSO). Actualmente, toda la recuperación de datos de estos orígenes se realizará mediante el contexto de seguridad de la _cuenta de usuario del origen de datos de puerta de enlace_. SQL Server Analysis Services (SSAS) no puede aplicar seguridad de nivel de fila (RLS) por usuario.

Por lo general, los informes paginados de Power BI están optimizados para la **impresión**o **generación de PDF**. Los informes de Power BI están optimizados para la **exploración e interactividad**. Para obtener más información, consulte [Cuándo usar informes paginados en Power BI](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Preparar

El objetivo de la fase de _Preparación_ es dejarlo todo listo. En él se describe la configuración del entorno de Power BI, la planeación de la protección y publicación de los informes, así como las ideas para volver a desarrollar elementos de SSRS que no se puedan migrar.

1. Asegúrese de que la [carga de trabajo Informes paginados](../service-admin-premium-workloads.md#paginated-reports) está habilitada para la capacidad de Power BI Premium y de que tiene suficiente memoria.
1. Compruebe la compatibilidad de los [orígenes de datos](../paginated-reports-data-sources.md) del informe y configure una [puerta de enlace de Power BI](../service-gateway-onprem.md) para permitir la conectividad con orígenes de datos locales.
1. Familiarícese con la seguridad de Power BI y planee [cómo reproducirá las carpetas y los permisos de SSRS](/sql/reporting-services/security/secure-folders) con las [áreas de trabajo y los roles de tales áreas de trabajo de Power BI](../service-new-workspaces.md).
1. Familiarícese con el uso compartido de Power BI y planee cómo va a distribuir el contenido publicando [aplicaciones de Power BI](../service-create-distribute-apps.md).
1. Considere la posibilidad de usar [conjuntos de datos compartidos de Power BI](../service-datasets-build-permissions.md) en lugar de orígenes de datos compartidos de SSRS.
1. Use [Power BI Desktop](../desktop-what-is-desktop.md) para desarrollar informes optimizados para dispositivos móviles. Para ello, puede usar el [objeto visual personalizado KPI de Power BI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview), en lugar de los informes para dispositivos móviles y KPI de SSRS.
1. Vuelva a evaluar el uso del campo integrado **UserID** en los informes. Si confía en el valor de **UserID** para proteger los datos del informe, sepa que para los informes paginados (cuando se hospedan en el servicio Power BI) devuelve el nombre principal de usuario (UPN). Por lo tanto, en lugar de devolver el nombre de cuenta de NT, por ejemplo _AW\mblythe_, el campo integrado devolverá algo como _m.bythe&commat;adventureworks.com_. Tendrá que revisar las definiciones del conjunto de datos y, posiblemente, los datos de origen. Una vez revisadas y publicadas, se recomienda probar exhaustivamente los informes para asegurarse de que los permisos de datos funcionan según lo previsto.
1. Vuelva a evaluar el uso del campo integrado **ExecutionTime** en los informes. En el caso de los informes paginados (cuando se hospedan en la servicio Power BI), el campo integrado devuelve la fecha y hora _en hora universal coordinada (o UTC)_ . Esto podría afectar a los valores predeterminados de los parámetros del informe y a las etiquetas de tiempo de ejecución del informe (normalmente se agregan a los pies de página del informe).
1. Si el origen de datos es SQL Server (local), confirme que los informes no usan visualizaciones de mapa. Las visualizaciones de mapa dependen de tipos de datos espaciales de SQL Server, y estos no son compatibles con la puerta de enlace. Para más información, vea [Guía de recuperación de datos de informes paginados (tipos de datos complejos de SQL Server)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Asegúrese de que los autores de los informes tienen instalado [Power BI Report Builder](../report-builder-power-bi.md) y que las publicaciones más recientes se pueden distribuir fácilmente en toda la organización.

## <a name="migration-stage"></a>Etapa de migración

Después de preparar el entorno y los informes de Power BI, está todo listo para la etapa de _Migración_.

Hay dos opciones de migración: _manual_ y _automatizada_. La migración manual es adecuada para un número de informes pequeño o para informes que se deban modificar antes de migrarse. La migración automatizada es adecuada para migrar un gran número de informes.

### <a name="manual-migration"></a>Migración manual

Cualquiera que tenga permiso para acceder a la instancia de SSRS y al área de trabajo de Power BI puede migrar manualmente los informes a Power BI. Estos son los pasos que debe seguir:

1. Abra el portal de SSRS que contiene los informes que quiere migrar.
1. Descargue cada definición de informe, guardando los archivos .rdl localmente.
1. Abra la _versión más reciente_ de Power BI Report Builder y conéctese al servicio Power BI con sus credenciales de Azure AD.
1. Abra cada informe en Power BI Report Builder y:
   1. Compruebe que todos los orígenes de datos y conjuntos de datos están incrustados en la definición de informe y que son [orígenes de datos admitidos](../paginated-reports-data-sources.md).
   1. Obtenga una vista previa del informe para asegurarse de que se representa correctamente.
   1. Elija la opción _Guardar como_ y seleccione _Servicio Power BI_.
   1. Seleccione el área de trabajo que contendrá el informe.
   1. Compruebe que el informe se guarda. Si aún no se admiten determinadas características del diseño del informe, se producirá un error en la acción de guardar. Se le notificará de las razones. Después deberá revisar el diseño del informe e intentar guardarlo de nuevo.

### <a name="automated-migration"></a>Migración automatizada

Existen dos formas de realizar una migración automatizada. Puede usar:

- Herramienta de migración RDL
- API disponibles públicamente para SSRS y Power BI

La [herramienta de migración RDL](#migration-tool) ya se ha descrito en este artículo.

También puede usar las API de SSRS y Power BI disponibles públicamente para automatizar la migración del contenido. Aunque la herramienta de migración de RDL ya usa estas API, puede desarrollar una herramienta personalizada que se adapte a sus requisitos exactos.

Para obtener más información sobre las API, vea:

- [Referencia de la API REST de Power BI](../developer/rest-api-reference.md)
- [API REST de SQL Server Reporting Services](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Etapa posterior a la migración

Una vez que haya completado correctamente la migración, estará a punto para la _etapa posterior a la migración_. Esta etapa implica realizar una serie de tareas posteriores a la migración para asegurarse de que todo funciona correctamente y de forma eficaz.

### <a name="configure-data-sources"></a>Configuración de orígenes de datos

Una vez que los informes se han migrado a Power BI, deberá asegurarse de que los orígenes de datos estén configurados correctamente. Puede implicar la asignación a orígenes de datos de puerta de enlace y el [almacenamiento seguro de las credenciales de origen de datos](../paginated-reports-data-sources.md#azure-sql-database-authentication). Estas acciones no se realizan mediante la herramienta de migración de RDL.

### <a name="review-report-performance"></a>Comprobación del rendimiento de los informes

Se recomienda completar las siguientes acciones para garantizar la mejor experiencia posible del usuario de informes:

1. Pruebe los informes en cada [explorador admitido para Power BI](../power-bi-browsers.md) con el fin de confirmar que el informe se representa correctamente.
1. Ejecute pruebas para comparar los tiempos de representación de los informes en SSRS y Power BI. Compruebe que los informes de Power BI se representan en un tiempo aceptable.
1. Si los informes de Power BI no se representan debido a que no hay memoria suficiente, asigne [recursos adicionales a la capacidad de Power BI Premium](../service-admin-premium-workloads.md#paginated-reports).
1. En el caso de los informes de representación prolongada, considere la posibilidad de que Power BI los entregue a los usuarios como [suscripciones de correo electrónico con datos adjuntos de informe](../consumer/paginated-reports-subscriptions.md).
1. En el caso de los informes de Power BI basados en conjuntos de datos de Power BI, revise los diseños del modelo para asegurarse de que están totalmente optimizados.

### <a name="reconcile-issues"></a>Solución de problemas

La fase posterior a la migración es fundamental para solucionar los problemas y resolver cualquier problema de rendimiento. Agregar la carga de trabajo de informes paginados a una capacidad puede atrasar el rendimiento de informes paginados _y otro contenido_ almacenado en la capacidad.

Para obtener más información sobre estos problemas, incluidos los pasos específicos para comprenderlos y mitigarlos, consulte los siguientes artículos:

- [Optimización de las capacidades Premium](../service-premium-capacity-optimize.md)
- [Supervisión de capacidades Premium en la aplicación](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [¿Qué son los informes paginados en Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- [Guía de recuperación de datos de informes paginados](report-paginated-data-retrieval.md)
- Guy in a cube (vídeo): [Presentación de los informes paginados en Power BI](https://www.youtube.com/watch?v=wfqn45XNK3M)
- [Cuándo usar informes paginados en Power BI](report-paginated-or-power-bi.md)
- [Informes paginados en Power BI: Preguntas más frecuentes](../paginated-reports-faq.md)
- [Preguntas más frecuentes sobre Power BI Premium](../service-premium-faq.md)
- [Herramienta de migración RDL](https://github.com/microsoft/RdlMigration)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Los partners de Power BI están disponibles para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
