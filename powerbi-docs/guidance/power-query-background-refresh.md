---
title: Deshabilitación de la actualización en segundo plano de Power Query
description: Instrucciones sobre cuándo deshabilitar la actualización en segundo plano de Power Query.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: ef9ab7c0d84b926094c33e8aa2765cd43b844314
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623070"
---
# <a name="disable-power-query-background-refresh"></a>Deshabilitación de la actualización en segundo plano de Power Query

Este artículo está dirigido a modeladores de datos de importación que trabajan con Power BI Desktop.

De forma predeterminada, cuando Power Query importa datos, también almacena en caché hasta 1000 filas de datos de vista previa para cada consulta. Los datos de vista previa facilitan la presentación de una vista previa rápida de los datos de origen y los resultados de transformación de cada paso de las consultas. Se almacenan por separado en el disco y no dentro del archivo de Power BI Desktop.

Pero cuando el archivo de Power BI Desktop contiene muchas consultas, la recuperación y el almacenamiento de datos de vista previa pueden ampliar el tiempo necesario para completar una actualización.

## <a name="recommendation"></a>Recomendación

Para lograr una actualización más rápida, establezca el archivo de Power BI Desktop para actualizar la caché de vista previa _en segundo plano_. Para habilitarlo En Power BI Desktop, seleccione _Archivo > Opciones y configuración > Opciones_ y, después, seleccione la página _Carga de datos_. Después, puede activar la opción **Permitir que se descargue la vista previa de datos en segundo plano**. Tenga en cuenta que esta opción solo se puede establecer para el archivo actual.

![Opciones de datos en segundo plano de Power BI Desktop](media/power-query-background-refresh/power-query-options-background-data.png)

La habilitación de la actualización en segundo plano puede dar lugar a que los datos de vista previa estén desactualizados. En ese caso, el Editor de Power Query le notificará la siguiente advertencia:

![Advertencia del Editor de Power Query sobre datos de vista previa antiguos](media/power-query-background-refresh/power-query-preview-data-old.png)

Siempre se puede actualizar la caché de vista previa. Puede actualizarla para una sola consulta o para todas mediante el comando **Actualizar vista previa**. Lo encontrará en la cinta **Inicio** de la ventana del Editor de Power Query.

![Comandos del Editor de Power Query para actualizar los datos de vista previa](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Documentación de Power Query](/power-query/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
