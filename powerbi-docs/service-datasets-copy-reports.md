---
title: 'Copia de informes desde otras áreas de trabajo (versión preliminar): Power BI'
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
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461474"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Copia de informes desde otras áreas de trabajo (versión preliminar)

Obtenga información sobre cómo puede copiar un informe de un área de trabajo y guardarlo en otra. Después, puede modificar ese informe mediante la adición o eliminación de objetos visuales y otros elementos.

Cuando encuentre un informe que le guste en un área de trabajo o una aplicación, puede realizar una copia y después modificarlo para ajustarlo a sus necesidades. No tiene que preocuparse de crear el modelo de datos. Ya se ha creado de forma automática. Y resulta mucho más fácil modificar un informe existente que empezar desde cero.

## <a name="save-a-copy-of-a-report"></a>Guardado de una copia de un informe

1. En una aplicación o un área de trabajo, vaya a la vista de lista Informes.

1. En **Acciones**, seleccione **Guardar una copia**.

    ![Guardado de una copia de un informe](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Solo verá el icono **Guardar una copia** si el informe está en una nueva experiencia de área de trabajo y tiene [permisos de compilación](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Incluso si tiene acceso al área de trabajo, necesita tener permisos de compilación para el conjunto de datos.

3. En **Guardar una copia de este informe**, asigne un nombre del informe y seleccione el área de trabajo de destino.

    ![Cuadro de diálogo Guardar una copia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Puede guardar el informe en el área de trabajo actual o en otra diferente en el servicio Power BI. Solo verá las áreas de trabajo que sean de la nueva experiencia, de las que sea miembro.
  
4. Seleccione **Guardar**.

    Al guardar una copia del informe, se crea una conexión dinámica al conjunto de datos, y puede abrir la experiencia de creación de informes con el conjunto completo de datos disponible. No ha realizado una copia del conjunto de datos. El conjunto de datos aún reside en su ubicación original. Puede usar todas las tablas y medidas del conjunto de datos en el informe propio. Las restricciones de seguridad de nivel de fila (RLS) en el conjunto de datos están en vigor, por lo que solo verá los datos para los que tenga permiso, según su rol de RLS.

    Power BI crea de forma automática una entrada en la lista de conjuntos de datos si el informe se basa en un conjunto de datos fuera del área de trabajo. El icono para este conjunto de datos es diferente del de los conjuntos de datos del área de trabajo: ![Icono de conjunto de datos compartido](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    De este modo, los miembros del área de trabajo pueden saber en qué paneles e informes se usan conjuntos de datos que están fuera del área de trabajo. En la entrada se muestra información sobre el conjunto de datos y algunas acciones concretas.

    ![Acciones del conjunto de datos](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Visualización de conjuntos de datos relacionados

Cuando tiene un informe en el área de trabajo, es posible que necesite saber en qué conjunto de datos se basa.

1. En la vista de lista Informes, seleccione **Ver relacionados**.

    ![icono de Ver relacionados](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. En el cuadro de diálogo **Contenido relacionado** se muestran todos los elementos relacionados. En esta lista, el conjunto de datos es similar a cualquier otro. No puede saber que se encuentra en otra área de trabajo. Es un problema conocido.
 
    ![Cuadro de diálogo Contenido relacionado](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>Pasos siguientes

- [Uso de conjuntos de datos entre áreas de trabajo (versión preliminar)](service-datasets-across-workspaces.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
