---
title: Publicar desde Power BI Desktop
description: Publicar desde Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3a67c36b2594696e1c576693cc5808eb0227c1c7
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709616"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>Publicar conjuntos de datos e informes desde Power BI Desktop
Al publicar un archivo de Power BI Desktop en el servicio Power BI, se publican los datos del modelo en el área de trabajo de Power BI. Lo mismo se aplica a los informes creados en la vista **Informes**. Verá un nuevo conjunto de datos con el mismo nombre y los informes en el Explorador de área de trabajo.

La publicación desde Power BI Desktop tiene el mismo efecto que usar **Obtener datos** en Power BI para conectarse y cargar un archivo de Power BI Desktop.

> [!NOTE]
> Los cambios que realice en el informe en Power BI no se volverán a guardar en el archivo de Power BI Desktop original. Esto incluye la adición, eliminación o cambio de visualizaciones en los informes.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Para publicar informes y conjuntos de datos de Power BI Desktop
1. En Power BI Desktop, elija **Archivo** \> **Publicar** \> **Publicar en Power BI**, o bien seleccione **Publicar** en la cinta de opciones.  

   ![Botón Publicar](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Inicie sesión en Power BI.
3. Seleccione el destino.

   ![Seleccionar destino de publicación](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Cuando se haya completado la publicación, recibirá un vínculo al informe. Seleccione el vínculo para abrir el informe en el sitio de Power BI.

![Cuadro de diálogo Publicación correcta](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Republicación o reemplazo de un conjunto de datos publicado desde Power BI Desktop
El conjunto de datos y los informes creados en Power BI Desktop se cargarán en el sitio de Power BI al publicar un archivo de Power BI Desktop. Cuando vuelva a publicar el archivo de Power BI Desktop, el conjunto de datos del sitio de Power BI se reemplazará por el conjunto de datos actualizado desde el archivo de Power BI Desktop.

Este proceso es sencillo, pero hay algunas cosas que debe saber:

* Dos o más conjuntos de datos en Power BI con el mismo nombre que el archivo de Power BI Desktop podrían provocar un error en la publicación. Asegúrese de que tiene un único conjunto de datos en Power BI con el mismo nombre. También puede cambiar el nombre del archivo y publicar, creando un nuevo conjunto de datos con el mismo nombre que el archivo.
* Si cambia el nombre o elimina una columna o medida, las visualizaciones que ya tenga en Power BI con ese campo podrían interrumpirse. 
* Power BI omite los cambios de formato de las columnas existentes. Por ejemplo, si cambia el formato de una columna de 0,25 % a 25 %.
* Supongamos que tiene una programación de actualización que está configurada para el conjunto de datos existente en Power BI. Al agregar nuevos orígenes de datos al archivo y, después, volverlo a publicar, tendrá que iniciar sesión en estos antes de la siguiente actualización programada.
* Cuando se vuelve a publicar un conjunto de datos publicado desde Power BI Desktop y se define una programación de actualización, se inicia una actualización del conjunto de datos en cuanto se vuelve a publicar. 

