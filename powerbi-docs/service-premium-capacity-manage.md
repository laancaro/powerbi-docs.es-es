---
title: Administrar las capacidades de Microsoft Power BI Premium
description: Describe las tareas de administración para las capacidades de Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565241"
---
# <a name="managing-premium-capacities"></a>Administración de las capacidades Premium

Administración de Power BI Premium implica la creación, administración y supervisión de las capacidades Premium.

## <a name="creating-and-managing-capacities"></a>Crear y administrar las capacidades

El **la configuración de capacidad** página del portal de administración de Power BI muestra el número de núcleos adquiridos y las capacidades Premium disponibles. La página permite a los administradores globales de Office 365 o los administradores de servicios de Power BI para crear las capacidades Premium de núcleos virtuales disponibles, o para modificar las capacidades Premium existentes.

Al crear una capacidad Premium, los administradores deben definir:

- Nombre de la capacidad (es único dentro del inquilino).
- Administradores de capacidad.
- Tamaño de capacidad.
- Región de residencia de datos.

Debe asignarse al menos un administrador de capacidad. Los usuarios asignados como administradores de capacidad de hacer lo siguiente:

- Asignar áreas de trabajo a la capacidad.
- Administrar permisos de usuario, para agregar los usuarios con permisos de asignación (que les permite asignar áreas de trabajo a la capacidad) o los administradores de capacidad adicionales.
- Administrar las cargas de trabajo, para configurar el uso de memoria máximo para los informes paginados y cargas de trabajo de flujos de datos.
- Reinicie la capacidad para restablecer todas las operaciones debido a una sobrecarga del sistema.

Los administradores de capacidad no pueden tener acceso a contenido del área de trabajo a menos que se asigne explícitamente en los permisos del área de trabajo. También no tienen acceso a todas las áreas de administración de Power BI (a menos que se asigne explícitamente) como las métricas de uso, los registros de auditoría o configuración de inquilinos. Lo que es importante, los administradores de capacidad no tiene permisos para crear nuevas capacidades o ampliar las capacidades existentes. Los administradores se asignan de forma por capacidad, asegurándose de que se pueden solo ver y administrar las capacidades a los que están asignadas.

Tamaño de capacidad se selecciona de una lista de las opciones de SKU disponible que está restringida por el número de núcleos virtuales disponibles en el grupo. Es posible crear varias capacidades de la agrupación, que podría proceder de uno o más adquirir la SKU. Por ejemplo, una SKU P3 (32 núcleos) podrían usarse para crear tres capacidades: uno P2 (16 núcleos) y P1 dos (2 x 8 núcleos). Mejorar el rendimiento y la escala se pueden lograr mediante la creación de menores tamaño capacidades, como se describe en el [optimizar capacidades Premium](service-premium-capacity-optimize.md) artículo. La siguiente imagen muestra una configuración de ejemplo para la organización ficticia de Contoso que consta de cinco de las capacidades Premium (3 x P1 y 2 x P3) con cada contenedor áreas de trabajo de aplicación y varias áreas de trabajo en capacidad compartida.

![Una configuración de ejemplo para la organización ficticia de Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Una capacidad Premium puede asignarse a una región distinta de la región principal del inquilino de Power BI, conocido como multigeográfica. Multigeográficas proporciona control administrativo sobre qué centros de datos de regiones geográficas definidas que reside el contenido de Power BI. La lógica para una implementación multigeográficas normalmente es para corporativa o cumplimiento de normas gubernamentales, en lugar de rendimiento y escalabilidad. Informes y la carga del panel todavía supone las solicitudes a la región principal para los metadatos. Para obtener más información, consulte [Multigeográficas compatibilidad con Power BI Premium](service-admin-premium-multi-geo.md).

Los administradores de servicios de Power BI y los administradores globales de Office 365 pueden modificar las capacidades Premium. En concreto, puede:

- Cambiar el tamaño de la capacidad para escalar verticalmente o reducir verticalmente los recursos.
- Agregar o quitar administradores de capacidad.
- Agregar o quitar usuarios que tengan permisos de asignación.
- Agregar o quitar las cargas de trabajo adicionales.
- Cambiar las regiones.

Se requieren permisos de asignación para asignar un área de trabajo a una capacidad Premium específica. Los permisos pueden concederse a la toda la organización, usuarios específicos o grupos.

De forma predeterminada, las capacidades Premium admiten cargas de trabajo asociados con la ejecución de consultas de Power BI. Las capacidades Premium también admiten cargas de trabajo adicionales: **Inteligencia artificial (servicios cognitivos)** , **informes paginados**, y **flujos de datos**. Cada carga de trabajo requiere la configuración de la memoria máxima (como un porcentaje de memoria total disponible) que se puede usar la carga de trabajo. Es importante entender que puede afectar a aumentar las asignaciones de memoria máxima del número de modelos activos que se puede hospedar y el rendimiento de las actualizaciones. 

Memoria se asigna dinámicamente a los flujos de datos, pero está asignada estáticamente a los informes paginados. La razón para asignar estáticamente la memoria máxima es que se ejecutan los informes paginados dentro de un espacio protegido independiente de la capacidad. Debe tener cuidado al valor paginado informes memoria, ya que reduce la memoria disponible para cargar los modelos. Para obtener más información, consulte el [configuración de memoria predeterminada](service-admin-premium-workloads.md#default-memory-settings).

Eliminando una capacidad Premium, es posible y no como resultado la eliminación de sus áreas de trabajo y el contenido. En su lugar, se mueve las áreas de trabajo asignados a la capacidad compartida. Cuando se creó la capacidad Premium en una región distinta, el área de trabajo se mueve a una capacidad compartida de la región principal.

### <a name="assigning-workspaces-to-capacities"></a>Asignar áreas de trabajo a las capacidades

Las áreas de trabajo se pueden asignar a una capacidad Premium en el portal de administración de Power BI o, para un área de trabajo de aplicación, en el **área de trabajo** panel.

Los administradores de capacidad, así como los administradores globales de Office 365 o los administradores de servicios de Power BI, pueden realizar masiva asignar áreas de trabajo en el portal de administración de Power BI. Puede aplicar masiva asignado a:

- **Áreas de trabajo de usuarios** -todas las áreas de trabajo que pertenecen a esos usuarios, incluidas las áreas de trabajo personales, se asignan a la capacidad Premium. Esto incluirá la reasignación de áreas de trabajo cuando ya está asignadas a una capacidad Premium diferentes. Además, los usuarios también se asignan permisos de asignación de área de trabajo.

- **Áreas de trabajo específicas**
- **Las áreas de trabajo de toda la organización** -todas las áreas de trabajo, incluidas las áreas de trabajo personales, se asignan a la capacidad Premium. Todos los usuarios actuales y futuros se asignan permisos de asignación de área de trabajo. No se recomienda este enfoque. Se prefiere un enfoque más realista.

Un área de trabajo se puede agregar a una capacidad Premium mediante el uso de la **área de trabajo** panel que proporciona el usuario sea administrador del área de trabajo y tiene permisos de asignación.

![Uso del panel de área de trabajo para asignar un área de trabajo a una capacidad Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Los administradores del área de trabajo pueden quitar un área de trabajo de una capacidad (a la capacidad compartida) sin necesidad de un permiso de asignación. Quitar las áreas de trabajo de capacidades dedicadas efectivamente vuelve a colocar en el área de trabajo en capacidad compartida. Tenga en cuenta que al quitar un área de trabajo de una capacidad Premium puede tener consecuencias negativas resultante, por ejemplo, en el contenido compartido no esté disponible para la versión gratuita de Power BI con licencia a los usuarios o la suspensión de la actualización programada cuando se superen las provisiones de compatibles comparte las capacidades.

En el servicio Power BI, un área de trabajo asignado a una capacidad Premium se identifica fácilmente mediante el icono de rombo que adorna el nombre del área de trabajo.

![Que identifica un área de trabajo asignado a una capacidad Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Capacidades de supervisión

Supervisión de las capacidades Premium proporciona a los administradores comprender cómo funcionan las capacidades. Las capacidades se pueden supervisar mediante el portal de administración de Power BI o **métricas de capacidad de Power BI Premium** app (Power BI).

### <a name="power-bi-admin-portal"></a>Portal de administración de Power BI

En el portal de administración, para cada capacidad, el **mantenimiento** ficha proporciona métricas de resumen para cada carga de trabajo habilitado y la capacidad. Las métricas muestran un promedio durante los últimos siete días.  

En el nivel de capacidad, las métricas son acumulativas de todas las cargas de trabajo habilitados. se proporcionan las siguientes métricas:

- **USO de CPU** -proporciona el uso de CPU promedio como porcentaje del total de CPU disponible para la capacidad.  
- **USO de memoria** -proporciona promedio de uso de memoria (en GB) como un total de memoria disponible para la capacidad. 

Para cada carga de trabajo habilitado, se proporcionan de la CPU y uso de memoria, así como un número de métricas de carga de trabajo específicas. Por ejemplo, para la carga de trabajo de flujo de datos, **recuento Total de** muestra totales para cada flujo de datos, las actualizaciones y **promedio de duración** muestra la duración promedio de actualización para el flujo de datos.

![Ficha de estado de capacidad en el portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Para obtener más información acerca de todas las métricas disponibles para cada carga de trabajo, vea [supervisar las capacidades en el portal de administración](service-admin-premium-monitor-portal.md).

Las funcionalidades de supervisión en el portal de administración de Power BI están diseñadas para proporcionar un resumen rápido de las métricas de capacidad de clave. Para obtener más supervisión, se recomienda usar la **métricas de capacidad de Power BI Premium** app.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium app las métricas de capacidad

El [métricas de capacidad de Power BI Premium app](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) es una aplicación de Power BI disponible para los administradores de capacidad y se instala como cualquier otra aplicación de Power BI. Contiene un panel e informes.

![Power BI Premium app las métricas de capacidad](media/service-premium-capacity-manage/capacity-metrics-app.png)

Cuando se abre la aplicación, se carga el panel para presentar varios iconos expresar una vista agregada a través de todas las capacidades de los cuales el usuario es un administrador de capacidad. El diseño del panel incluye cinco secciones principales:

- **Información general sobre** -versión de la aplicación, el número de áreas de trabajo y las capacidades
- **Resumen del sistema** -las métricas de memoria y CPU
- **Resumen del conjunto de datos** : número de conjuntos de datos, calidad de datos/LC, actualización y las métricas de consulta
- **Resumen de flujo de datos** : número de flujos de datos y las métricas del conjunto de datos
- **Pagina el resumen del informe** : actualizar y ver las métricas

El informe subyacente, desde el que se han anclado los iconos del panel, puede obtenerse haciendo clic en cualquier icono de panel. Proporciona una perspectiva más detallada de cada una de las secciones del panel y admite el filtrado interactivo. 

El filtrado puede lograrse mediante el establecimiento de las segmentaciones de datos por intervalo de fechas, capacidad, área de trabajo y carga de trabajo (informe, conjunto de datos, flujo de datos) y seleccionando elementos de informe de los objetos visuales cruzar filtrar la página del informe. Filtrado cruzado es una técnica eficaz para reducir a determinados períodos de tiempo, las capacidades, las áreas de trabajo, los conjuntos de datos, etc. y puede ser muy útil al realizar análisis de causa raíz.

Para obtener información detallada acerca de las métricas de paneles e informes en la aplicación, consulte [las capacidades de supervisión Premium con la aplicación](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretación de las métricas

Las métricas deben supervisarse para establecer una comprensión de la línea de base de actividad de carga de trabajo y el uso de recursos. Si la capacidad se convierte en lenta, es importante comprender las métricas que desea supervisar y las conclusiones puede realizar.

Idealmente, las consultas se completará en un segundo para ofrecer experiencias con capacidad de respuesta a los usuarios de informes y habilitar un mayor rendimiento de consulta. Suele ser de menor importancia cuando los procesos en segundo plano (incluidos las actualizaciones) toman tiempos más largos en completarse.

En general, informes lentos pueden ser una indicación de una capacidad de sobrecalentamiento. Cuando no se pudo cargar informes, esto es una indicación de una capacidad exceso calentada. En cualquier caso, la causa podría ser atribuible a muchos factores, como:

- **Consultas erróneas** ciertamente indican la presión de memoria, y que no se pudo cargar un modelo en memoria. El servicio Power BI intentará cargar un modelo de 30 segundos antes de desistir.

- **Tiempos de espera de consulta excesivo** puede deberse a varias razones:
  - La necesidad de que el servicio Power BI primero a expulsar modelos y, a continuación, cargar el modelo se va a consultar (Recuerde que mayores tasas de expulsión de conjunto de datos por sí solo no son una indicación de esfuerzo de capacidad, a menos acompañado por largos tiempos de espera de consulta que indican hiperpaginación de memoria).
  - Carga de modelos veces (especialmente la espera para cargar un modelo de gran tamaño en memoria).
  - Consultas de larga ejecución.
  - Demasiadas conexiones LC\DQ (si se supera los límites de capacidad).
  - Saturación de la CPU.
  - Diseños de informe complejos con un número excesivo de objetos visuales en una página (Recuerde que cada objeto visual es una consulta).

- **Consulta de larga duración** puede indicar que no se optimizan los diseños de modelo, sobre todo cuando están activos en una capacidad de varios conjuntos de datos, y solo un conjunto de datos está produciendo una larga duración de las consulta. Esto sugiere que la capacidad se ha extraído suficientemente y que el conjunto de datos en la pregunta es simplemente lentas o poco óptimo. Consultas de larga ejecución pueden ser problemática, ya puede bloquear el acceso a los recursos requeridos por otros procesos.
- **Tiempos de espera de actualización largo** indican una memoria insuficiente debido a muchos modelos activos que consumen memoria o que una actualización problemática esté bloqueando otras actualiza (que superan los límites de actualización paralela).

Se trata una explicación más detallada de cómo usar las métricas en el [las capacidades Premium optimizar](service-premium-capacity-optimize.md) artículo.

## <a name="acknowledgements"></a>Confirmaciones

En este artículo se escribió por Peter Myers, MVP de la plataforma de datos y experto en BI independiente con [bit a bit soluciones](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Optimizar las capacidades Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurar las cargas de trabajo en una capacidad Premium](service-admin-premium-workloads.md)   

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

||||||
