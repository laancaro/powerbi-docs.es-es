---
title: 'Copia de informes desde otras áreas de trabajo (versión preliminar): Power BI'
description: Obtenga información sobre cómo se puede compartir un conjunto de datos con usuarios en toda la organización. Después, podrán crear informes basados en el conjunto de datos en sus propias áreas de trabajo.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 2fc33c8adcaed35dab8fc9d81ab28fa314f42e3b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881936"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Copia de informes desde otras áreas de trabajo (versión preliminar)

Si encuentra un informe que le gusta en un área de trabajo o una aplicación, puede realizar una copia y guardarlo en otra área de trabajo. Luego puede modificar la copia del informe mediante la incorporación o eliminación de objetos visuales y otros elementos. No tiene que preocuparse de crear el modelo de datos. Ya se ha creado de forma automática. Y resulta mucho más fácil modificar un informe existente que empezar desde cero. Pero si se crea una aplicación desde la nueva área de trabajo, a veces no es posible publicar la copia del informe en la aplicación. Vea [Consideraciones y limitaciones en el artículo "Uso de conjuntos de datos entre áreas de trabajo"](service-datasets-across-workspaces.md#considerations-and-limitations) para obtener detalles.

> [!NOTE]
> Para realizar una copia se necesita una licencia Pro, aunque el informe original se encuentre en un área de trabajo de una capacidad Premium.

## <a name="save-a-copy-of-a-report"></a>Guardado de una copia de un informe

1. En una aplicación o un área de trabajo, vaya a la vista de lista Informes.

1. En **Acciones**, seleccione **Guardar una copia**.

    ![Guardado de una copia de un informe](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Solo verá el icono **Guardar una copia** si el informe está en una nueva experiencia de área de trabajo y tiene [permiso de compilación](service-datasets-build-permissions.md). Incluso si tiene acceso al área de trabajo, necesita tener permiso de compilación para el conjunto de datos.

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

## <a name="delete-a-report-and-its-shared-dataset"></a>Eliminación de un informe y su conjunto de datos compartido

Puede decidir que ya no quiere ni el informe ni su conjunto de datos compartido asociado en el área de trabajo.

1. Elimine el informe. En la lista de informes del área de trabajo, seleccione el icono de **Eliminar**.

    ![Icono de eliminación de informe](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. En la lista de conjuntos de datos, observará que los conjuntos de datos compartidos no tienen iconos de **Eliminar**. Actualice la página o vaya a otra página y regrese. El conjunto de datos se habrá eliminado. Si no, compruebe **Ver relacionados**. Puede estar relacionadas con otra tabla del área de trabajo.

    ![icono de Ver relacionados](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > La eliminación del conjunto de datos compartido en esta área de trabajo no elimina el conjunto de datos, tan solo la referencia a él.


## <a name="next-steps"></a>Pasos siguientes

- [Uso de conjuntos de datos entre áreas de trabajo (versión preliminar)](service-datasets-across-workspaces.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
