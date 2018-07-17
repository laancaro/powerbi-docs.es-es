---
title: Consulta y edición de la configuración de parámetros de conjunto de datos en el servicio Power BI
description: Los parámetros de consulta se crean en Power BI Desktop, pero se pueden revisar y actualizar en el servicio Power BI.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: ac271e8013bce5824931153351a651644a716a2f
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965168"
---
# <a name="what-is-a-query-parameter"></a>¿Qué es un parámetro de consulta?
Los parámetros de consulta son parámetros que los creadores de informes incorporan a Power BI Desktop. Estos parámetros permiten establecer porciones de los informes como dependientes de uno o varios *valores* de parámetro. Por ejemplo, un creador de informes puede crear un parámetro que restrinja los datos a una única región de un país, o un parámetro que defina qué formatos son aceptables en campos como los relativos a fechas, hora y texto.

![Pestaña Inicio con la opción Administrar parámetros en Desktop](media/service-parameters/power-bi-manage-parameters.png)


## <a name="review-and-edit-parameters-in-power-bi-service"></a>Revisión y edición de parámetros en el servicio Power BI

Una vez definidos los parámetros en Desktop, cuando ese [informe se publique en el servicio Power BI](desktop-upload-desktop-files.md), tanto la configuración de los parámetros como las selecciones realizadas aparecerán reflejadas en dicho informe. Algunos valores de parámetro se pueden revisar y editar en el servicio Power BI: no los parámetros que restringen los datos disponibles, pero sí aquellos que definen y describen los valores aceptables.

1. En el servicio Power BI, seleccione el icono de engranaje ![Icono de engranaje](media/service-parameters/power-bi-cog.png) y elija **Configuración**.

2. Seleccione la pestaña **Conjuntos de datos** y resalte un conjunto de datos de la lista. 
    
    ![Ventana Configuración con la pestaña Conjuntos de datos seleccionada](media/service-parameters/power-bi-select-dataset2.png)

3. Expanda **Parámetros**.  Si el conjunto de datos seleccionado no tiene parámetros, verá un mensaje con un vínculo que lleva a más información sobre los parámetros de consulta. Pero si el conjunto de datos sí tiene parámetros, podrá verlos expandiendo el encabezado **Parámetros**. 

    ![Ventana Configuración con Parámetros expandido](media/service-parameters/power-bi-settings.png)

    Revise la configuración de los parámetros y realice los cambios que considere necesarios. Los campos atenuados no son editables. 


## <a name="next-steps"></a>Pasos siguientes
Una manera directa de agregar parámetros simples es [modificar la dirección URL](service-url-filters.md).