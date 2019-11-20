---
title: Administración de las capacidades de Microsoft Power BI Premium
description: En este artículo se describen las tareas de administración para las capacidades de Power BI Premium.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 5e8becd877165f456793d99951544156a9314290
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881192"
---
# <a name="managing-premium-capacities"></a>Administración de las capacidades Premium

La administración de Power BI Premium implica la creación, administración y supervisión de las capacidades Premium. En este artículo se proporciona información general sobre las capacidades; consulte [Configuración y administración de capacidades](service-admin-premium-manage.md) para instrucciones detalladas.

## <a name="creating-and-managing-capacities"></a>Creación y administración de capacidades

En la página **Configuración de la capacidad** del portal de administración de Power BI se muestra la cantidad de núcleos virtuales comprados y las capacidades Premium disponibles. La página permita que los administradores globales de Office 365 y los administradores del servicio Power BI puedan crear capacidades Premium a partir de los núcleos virtuales disponibles, o bien modificar capacidades Premium existentes.

Al crear una capacidad Premium, los administradores deben definir:

- El nombre de la capacidad (que debe ser único dentro del inquilino).
- Los administradores de la capacidad.
- El tamaño de la capacidad.
- La región de residencia de los datos.

Se debe asignar al menos un administrador de capacidad. Los usuarios asignados como administradores de capacidad pueden:

- Asignar áreas de trabajo a la capacidad.
- Asignar los permisos de usuarios, para agregar administradores de capacidad o usuarios con permisos de asignación (a fin de permitirles asignar áreas de trabajo a la capacidad).
- Administrar cargas de trabajo para configurar el uso máximo de memoria para las cargas de trabajo de flujos de datos e informes paginados.
- Reiniciar la capacidad para restablecer todas las operaciones debido a una sobrecarga del sistema.

Los administradores de capacidad no pueden acceder al contenido del área de trabajo a menos que se los asigne explícitamente en permisos del área de trabajo. Tampoco tienen acceso a todas las áreas de administración de Power BI (a menos que se asignen de manera explícita), como métricas de uso, registros de auditoría o configuración del inquilino. Lo importante es que los administradores de capacidad no tienen permisos para crear capacidades nuevas ni para escalar las existentes. Los administradores se asignan por capacidad, lo que garantiza que solo podrán ver y administrar las capacidades a las que están asignados.

El tamaño de la capacidad se selecciona en una lista de las opciones de SKU disponible, que se ve restringida por el número de núcleos virtuales disponibles en el grupo. Es posible crear varias capacidades desde el grupo, cuyo origen puede ser una o varias SKU compradas. Por ejemplo, una SKU P3 (32 núcleos virtuales) se podría usar para crear tres capacidades: una P2 (16 núcleos virtuales) y dos P1 (2 x 8 núcleos virtuales). Es posible mejorar el rendimiento y la escala mediante la creación de capacidades de menor tamaño, tal como se describe en el artículo [Optimización de las capacidades Premium](service-premium-capacity-optimize.md). En la imagen siguiente se muestra una configuración de ejemplo para la organización ficticia Contoso, que consta de cinco capacidades Premium (3 x P1 y 2 x P3), donde cada una contiene áreas de trabajo y varias áreas de trabajo en la capacidad compartida.

![Una configuración de ejemplo para la organización ficticia Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Se puede asignar una capacidad Premium a una región distinta de la región de inicio del inquilino de Power BI, una característica que se conoce como Multi-Geo. Multi-Geo brinda control administrativo sobre los centros de datos dentro de regiones geográficas definidas donde reside el contenido de Power BI. Por lo general, la lógica de una implementación multigeográfica es para cumplimiento corporativo o gubernamental, en lugar del rendimiento y la escala. La carga de informes y paneles sigue implicando solicitudes de metadatos a la región principal. Para más información, vea [Compatibilidad de Multi-Geo con Power BI Premium](service-admin-premium-multi-geo.md).

Los administradores del servicio Power BI y los administradores globales de Office 365 pueden modificar la capacidades Premium. En concreto, pueden:

- Cambiar el tamaño de la capacidad para escalar o reducir verticalmente los recursos.
- Agregar o quitar administradores de capacidad.
- Agregar o quitar usuarios con permisos de asignación.
- Agregar o quitar cargas de trabajo adicionales.
- Cambiar las regiones.

Los permisos de asignación son necesarios para asignar un área de trabajo a una capacidad Premium específica. Los permisos se pueden conceder a toda la organización, a usuarios específicos o a grupos.

De manera predeterminada, las capacidades Premium admiten cargas de trabajo asociadas con la ejecución de consultas de Power BI. Las capacidades Premium también admiten otras cargas de trabajo: **IA (Cognitive Services)** , **Informes paginados** y **Flujos de datos**. Cada carga de trabajo requiere configurar la memoria máxima (como un porcentaje de la memoria total disponible) que puede usar la carga de trabajo. Es importante comprender que el aumento de las asignaciones de memoria máxima puede afectar el número de modelos activos que se pueden hospedar y el rendimiento de las actualizaciones. 

La memoria se asigna de manera dinámica a los flujos de datos, pero de forma estática a los informes paginados. La razón para asignar estáticamente la memoria máxima es que los informes paginados se ejecutan dentro de un espacio contenido protegido de la capacidad. Se debe tener cuidado al establecer la memoria de los informes paginados, ya que se reduce la memoria disponible para cargar los modelos. Para más información, consulte la [configuración de memoria predeterminada](service-admin-premium-workloads.md#default-memory-settings).

Es posible eliminar una capacidad Premium, lo que no eliminará las áreas de trabajo ni el contenido. En lugar de eso, todas las áreas de trabajo asignadas se mueven a la capacidad compartida. Cuando se creó la capacidad Premium en otra región, el área de trabajo se mueve a la capacidad compartida de la región de inicio.

### <a name="assigning-workspaces-to-capacities"></a>Asignación de áreas de trabajo a las capacidades

Las áreas de trabajo se pueden asignar a una capacidad Premium en el portal de administración de Power BI o, en el caso de un área de trabajo, en el panel **Área de trabajo**.

Los administradores de capacidad, así como los administradores globales de Office 365 o los administradores del servicio Power BI, pueden asignar áreas de trabajo en masa en el portal de administración de Power BI. La asignación masiva se puede aplicar a:

- **Áreas de trabajo por usuarios**: todas las áreas de trabajo que pertenecen a esos usuarios, incluidas las áreas de trabajo personales, se asignan a la capacidad Premium. Esto incluirá la reasignación de las áreas de trabajo cuando ya estén asignadas a una capacidad Premium diferente. Además, a los usuarios también se les asignan permisos de asignación de área de trabajo.

- **Áreas de trabajo específicas**
- **Áreas de trabajo de toda la organización**: todas las áreas de trabajo, incluidas las áreas de trabajo personales, se asignan a la capacidad Premium. A todos los usuarios actuales y futuros se les asignan permisos de asignación de área de trabajo. No se recomienda este enfoque. Se prefiere un enfoque más dirigido.

Para agregar un área de trabajo a una capacidad Premium, puede usar el panel **Área de trabajo**, siempre que el usuario sea administrador de un área de trabajo y tenga permisos de asignación.

![Uso del panel Área de trabajo para asignar un área de trabajo a una capacidad Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Los administradores del área de trabajo pueden quitar un área de trabajo de una capacidad (en una capacidad compartida) sin requerir el permiso de asignación. Al quitar áreas de trabajo de capacidades dedicadas, se reubica de manera eficaz el área de trabajo en una capacidad compartida. Tenga en cuenta que quitar un área de trabajo de una capacidad Premium puede tener consecuencias negativas como, por ejemplo que el contenido compartido no esté disponible para los usuarios con licencias gratuitas de Power BI o la suspensión de una actualización programada cuando se excedan las provisiones que admiten las capacidades compartidas.

En el servicio Power BI, un área de trabajo asignada a una capacidad Premium se identifica fácilmente con el icono de diamante que aparece en el nombre del área de trabajo.

![Identificación de un área de trabajo asignada a una capacidad Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Supervisión de las capacidades

La supervisión de las capacidades Premium proporciona a los administradores una descripción del funcionamiento de las capacidades. Las capacidades se pueden supervisar mediante el portal de administración de Power BI o con la aplicación **Métricas de capacidad de Power BI Premium** (Power BI).

### <a name="power-bi-admin-portal"></a>Portal de administración de Power BI

En el portal de administración, para cada capacidad, la pestaña **Health** (Estado) proporciona un resumen de las métricas correspondientes a la capacidad y cada carga de trabajo habilitada. Las métricas muestran un promedio de los últimos siete días.  

En el nivel de capacidad, las métricas son acumulativas de todas las cargas de trabajo habilitadas. Se proporcionan las métricas siguientes:

- **USO DE CPU**: proporciona el uso de CPU promedio como porcentaje de la CPU disponible total para la capacidad.  
- **USO DE MEMORIA**: proporciona el uso de memoria promedio (en GB) como un total de la memoria disponible para la capacidad. 

Para cada carga de trabajo habilitada, se proporciona el uso de CPU y memoria, así como varias métricas específicas de la carga de trabajo. Por ejemplo, para la carga de trabajo Flujo de datos, **Total Count** (Recuento total) muestra el total de actualizaciones de cada flujo de datos, mientras que **Average Duration** (Duración promedio) muestra la duración promedio de actualización para el flujo de datos.

![Pestaña Health (Estado) de la capacidad en el portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Para más información sobre todas las métricas disponibles para cada carga de trabajo, consulte [Supervisión de capacidades en el portal de administración](service-admin-premium-monitor-portal.md).

Las funcionalidades de supervisión en el portal de administración de Power BI están diseñadas para brindar un resumen rápido de las métricas de capacidad clave. Para una supervisión más detallada, se recomienda usar la aplicación **Métricas de capacidad de Power BI Premium**.

### <a name="power-bi-premium-capacity-metrics-app"></a>Aplicación Métricas de capacidad de Power BI Premium

La aplicación [Métricas de capacidad de Power BI Premium](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) es una aplicación de Power BI que está disponible para los administradores de capacidad y se instala como cualquier otra aplicación de Power BI. Contiene un panel y un informe.

![Aplicación Métricas de capacidad de Power BI Premium](media/service-premium-capacity-manage/capacity-metrics-app.png)

Cuando se abre la aplicación, se carga el panel para presentar numerosos iconos que expresan una vista agregada de todas las capacidades de las que el usuario es un administrador de la capacidad. El diseño del panel incluye cinco secciones principales:

- **Información general**: versión de la aplicación, cantidad de capacidades y áreas de trabajo.
- **Resumen del sistema**: métricas de memoria y CPU.
- **Resumen de conjuntos de datos**: métricas de consultas, actualizaciones, DQ/LC y número de conjuntos de datos.
- **Resumen de flujos de datos**: métricas de conjuntos de datos y número de flujos de datos.
- **Resumen de informes paginados**: métricas de actualizaciones y visualizaciones.

Es posible acceder al informe subyacente, desde donde se anclaron los iconos del panel, si se hace clic en cualquiera de los iconos del panel. Proporciona una perspectiva más detallada de cada una de las secciones del panel y admite el filtrado interactivo. 

Para lograr el filtrado, puede establecer segmentaciones por intervalo de fechas, capacidad, área de trabajo y carga de trabajo (informe, conjunto de datos, flujo de datos) y seleccionar elementos dentro de objetos visuales de informes para aplicar un filtro cruzado en la página de informe. El filtrado cruzado es una técnica eficaz para limitar a períodos de tiempo, capacidades, áreas de trabajo, conjuntos de datos específicos, entre otros, y puede ser muy útil al realizar un análisis de la causa principal.

Para información más detallada sobre las métricas de panel e informe en la aplicación, consulte [Supervisión de capacidades Premium con la aplicación](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretación de las métricas

Las métricas se deben supervisar para entender detalladamente el uso de los recursos y la actividad de las cargas de trabajo. Si la capacidad se ralentiza, es importante entender cuáles son las métricas que se deben supervisar y las conclusiones que puede sacar.

Idealmente, las consultas se deben completar en un segundo para brindar experiencias con capacidad de respuesta a los usuarios de los informes y permitir un mayor rendimiento de las consultas. Por lo general, es menos preocupante cuando los procesos en segundo plano (incluidas las actualizaciones) tardan más tiempo en completarse.

Por lo general, los informes lentos pueden ser indicio de una capacidad sobrecalentada. Cuando no se cargan los informes, es señal de que se sobrecalentó una capacidad. En cualquier caso, la causa principal se podría atribuir a muchos factores, entre los que se incluyen:

- Las **consultas con error** que, ciertamente, indican la presión de memoria y que un modelo no se podría cargar en la memoria. El servicio Power BI intentará cargar un modelo durante 30 segundos antes de que se produzca un error.

- Los **tiempos de espera de consulta excesivos** se pueden deber a distintos motivos:
  - La necesidad de que el servicio Power BI expulse primero los modelos y luego cargue los modelos que se van a consultar (recuerde que tasas más altas de expulsión de los conjuntos de datos por sí mismas no son señal de una presión de capacidad, a menos que vayan acompañadas de tiempos de espera de consulta prolongados que indiquen la hiperpaginación de memoria).
  - Tiempos de carga de modelo (especialmente la espera para cargar en memoria un modelo de gran tamaño).
  - Consultas de larga duración.
  - Demasiadas conexiones LC\DQ (que superan los límites de la capacidad).
  - Saturación de la CPU.
  - Diseños de informes complejos con una cantidad excesiva de objetos visuales en una página (recuerde que cada objeto visual es una consulta).

- Las **consultas de larga duración** pueden indicar que los diseños de modelos no están optimizados, especialmente cuando hay varios conjuntos de datos activos en una capacidad y solo un conjunto de datos genera que las consultas sean de larga duración. Esto sugiere que la capacidad tiene los recursos suficientes y que el conjunto de datos en cuestión no es óptimo o es simplemente lento. Las consultas de larga duración pueden ser problemáticas porque pueden bloquear el acceso a los recursos que otros procesos requieren.
- Los **tiempos de espera de actualización prolongados** indican que no hay memoria suficiente debido a que son muchos los modelos activos que consumen memoria, o bien que hay una actualización problemática bloqueando otras actualizaciones (superando los límites de actualizaciones en paralelo).

Puede encontrar una explicación más detallada sobre cómo usar las métricas en el artículo [Optimización de las capacidades Premium](service-premium-capacity-optimize.md).

## <a name="acknowledgements"></a>Agradecimientos

Este artículo es obra de Peter Myers, MVP de plataforma de datos y experto independiente de BI con [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Optimización de las capacidades Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configuración de cargas de trabajo en una capacidad Premium](service-admin-premium-workloads.md)   

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

