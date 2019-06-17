---
title: 'Creación de informes basados en conjuntos de datos de diferentes áreas de trabajo (versión preliminar): Power BI'
description: Obtenga información sobre cómo se puede compartir un conjunto de datos con usuarios en toda la organización. Después, podrán crear informes basados en el conjunto de datos en sus propias áreas de trabajo.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 99769b78060756c557223dd366da550ad3e11056
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461290"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces-preview"></a>Creación de informes basados en conjuntos de datos de diferentes áreas de trabajo (versión preliminar)

Obtenga información sobre cómo puede crear informes en áreas de trabajo propias basados en conjuntos de datos de otras. Para generar un informe sobre un conjunto de datos existente, puede empezar desde Power BI Desktop o desde el servicio Power BI, en Mi área de trabajo o en una [nueva experiencia de área de trabajo](service-create-the-new-workspaces.md).

- En el servicio Power BI: **Obtener datos** > **Conjuntos de datos publicados**.
- En Power BI Desktop: **Obtener datos** > **Conjuntos de datos de Power BI**.

    ![Conexión a un conjunto de datos existente](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
En ambos casos, la experiencia de detección del conjunto de datos se inicia en este cuadro de diálogo **Selección de un conjunto de datos para crear un informe**. Verá todos los conjuntos de datos a los que tiene acceso, con independencia de dónde se encuentren:

![Selección de un conjunto de datos](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

Observe que el primero tiene la etiqueta **Promocionado**. Se describirá más adelante en este artículo, en la sección [Búsqueda de un conjunto de datos promocionado](#find-an-endorsed-dataset).

Los conjuntos de datos que se ven en esta lista cumplen al menos una de las condiciones siguientes:

- El conjunto de datos está en una de las áreas de trabajo de la nueva experiencia de áreas de trabajo, y es miembro de esa área de trabajo. Vea [Consideraciones y limitaciones](service-datasets-across-workspaces.md#considerations-and-limitations).
- Tiene permiso de compilación para el conjunto de datos, que se encuentra en un área de trabajo de la nueva experiencia de áreas de trabajo.
- El conjunto de datos está en Mi área de trabajo.

> [!NOTE]
> Si es un usuario gratuito, solo verá los conjuntos de datos de Mi área de trabajo, o bien los conjuntos de datos para los que tiene permiso de compilación que se encuentran en áreas de trabajo de la capacidad Premium.

Al hacer clic en **Crear**, se crea una conexión dinámica al conjunto de datos y la experiencia de creación de informes se abre con el conjunto completo de datos disponible. No ha realizado una copia del conjunto de datos. El conjunto de datos aún reside en su ubicación original. Puede usar todas las tablas y medidas del conjunto de datos para crear informes propios. Las restricciones de seguridad de nivel de fila (RLS) en el conjunto de datos están en vigor, por lo que solo verá los datos para los que tenga permiso, según su rol de RLS.

Puede guardar el informe en el área de trabajo actual en el servicio Power BI, o bien publicarlo en un área de trabajo de Power BI Desktop. Power BI crea de forma automática una entrada en la lista de conjuntos de datos si el informe se basa en un conjunto de datos fuera del área de trabajo. El icono para este conjunto de datos es diferente del de los conjuntos de datos del área de trabajo: ![Icono de conjunto de datos compartido](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

De este modo, los miembros del área de trabajo pueden saber en qué paneles e informes se usan conjuntos de datos que están fuera del área de trabajo. En la entrada se muestra información sobre el conjunto de datos y algunas acciones concretas.

![Acciones del conjunto de datos](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>Búsqueda un conjunto de datos aprobado

Hay dos tipos diferentes de conjuntos de datos aprobados. Los propietarios del conjunto de datos pueden *promocionar* un conjunto de datos que le recomienden. El administrador de inquilinos de Power BI puede designar expertos en la organización que pueden *certificar* conjuntos de datos para todos los usuarios. En los conjuntos de datos promocionados y certificados se muestran *distintivos* que puede ver tanto al buscar un conjunto de datos como en la lista de conjuntos de datos de un área de trabajo. 

- En el servicio Power BI: **Obtener datos** > **Conjuntos de datos publicados**.
- En Power BI Desktop: **Obtener datos** > **Conjuntos de datos de Power BI**.

    En el cuadro de diálogo **Seleccionar un conjunto de datos**, los conjuntos de datos aprobados aparecen al principio de la lista de forma predeterminada. 

    ![Conjunto de datos promocionado](media/service-datasets-certify-promote/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>Pasos siguientes

- [Uso de conjuntos de datos entre áreas de trabajo (versión preliminar)](service-datasets-across-workspaces.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
