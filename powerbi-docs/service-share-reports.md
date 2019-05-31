---
title: Filtrar un informe y compartirlo con compañeros de trabajo - Power BI
description: Aprenda a filtrar un informe de Power BI y a compartirlo con los compañeros de la organización.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770678"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>Filtrar un informe de Power BI y compartirlo con compañeros de trabajo
*Compartir* es una buena manera de permitir que otros usuarios tengan acceso a sus paneles e informes. ¿Qué sucede si quiere compartir una versión filtrada de un informe? Quizás un informe que muestra solamente los datos de una ciudad, vendedor o año determinados. Intente filtrar un informe y compartirlo o crear una dirección URL personalizada. El informe se filtrará cuando los destinatarios lo abran por primera vez. Pueden quitar el filtro modificando la dirección URL. 

Power BI ofrece también [varias maneras de colaborar y distribuir sus informes](service-how-to-collaborate-distribute-dashboards-reports.md). Con el uso compartido, usted y sus destinatarios necesitarán una [licencia de Power BI Pro](service-features-license-type.md) o que el contenido esté en una [capacidad premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Dos maneras de filtrar un informe

### <a name="set-a-filter"></a>Establecer un filtro

Abra el informe en [vista de edición](consumer/end-user-reading-view.md), aplique el filtro y guarde el informe.
   
En este ejemplo, vamos a filtrar el [ejemplo de Análisis de venta directa](sample-tutorial-connect-to-the-samples.md) para mostrar solo los valores donde **Territory** sea igual a **NC**.
   
![Panel de filtro de informe](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>Crear un filtro en la dirección URL

Agregue lo siguiente al final de la dirección URL de la página del informe:
   
?filter=*tablename*/*fieldname* eq *value*
   
El campo debe ser de tipo número, fecha y hora o cadena. Los valores de *tablename* o *fieldname* no pueden contener espacios.
   
En nuestro ejemplo, el nombre de la tabla es **Almacén**, el nombre del campo es **Territorio** y el valor por el que quiere filtrar es **NC**:
   
?filter=Tienda/Territorio eq 'NC'
   
![Dirección URL de informe filtrado](media/service-share-reports/power-bi-filter-url3.png)
   
El explorador agrega caracteres especiales para representar espacios, apóstrofos y barras diagonales, así que es resultado es:
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

Consulte el artículo [filtrar un informe con parámetros de cadena de consulta en la dirección URL](service-url-filters.md) para mucho más detalle.

## <a name="share-the-filtered-report"></a>Compartir el informe filtrado

1. Cuando se [compartir el informe](service-share-dashboards.md), desactive la **envíe una notificación por correo electrónico a los destinatarios** casilla de verificación.

    ![Cuadro de diálogo Compartir informe](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envíe el vínculo con el filtro que creó anteriormente.

## <a name="next-steps"></a>Pasos siguientes
* ¿Quiere hacer algún comentario? Vaya al [sitio de la comunidad de Power BI](https://community.powerbi.com/) para efectuar sus sugerencias.
* [¿Cómo debo compartir paneles e informes y colaborar en ellos?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartir un panel](service-share-dashboards.md)
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/).

