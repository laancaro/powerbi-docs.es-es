---
title: Dos maneras de compartir un informe de Power BI filtrado
description: Aprenda dos maneras de filtrar un informe de Power BI y compartirlo con los compañeros de la organización.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 79f09b5018efcdae88d74ae26f099ff095fb161a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871443"
---
# <a name="two-ways-to-share-a-filtered-power-bi-report"></a>Dos maneras de compartir un informe de Power BI filtrado
*Compartir* es una buena manera de permitir que otros usuarios tengan acceso a sus paneles e informes. ¿Qué sucede si quiere compartir una versión filtrada de un informe? Quizás un informe que muestra solamente los datos de una ciudad, vendedor o año determinados. Intente filtrar un informe y compartirlo, o crear una dirección URL personalizada. El informe se filtra cuando los destinatarios lo abren por primera vez. Pueden quitar el filtro modificando la dirección URL. 

![Informe filtrado](media/service-share-reports/power-bi-share-filter-pane-report.png)

Power BI ofrece también [otras maneras de colaborar y distribuir sus informes](service-how-to-collaborate-distribute-dashboards-reports.md). Con el uso compartido, usted y sus destinatarios necesitarán una [licencia de Power BI Pro](service-features-license-type.md) o que el contenido esté en una [capacidad premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Dos formas de filtrar un informe

Con ambas técnicas de filtrado, usamos la aplicación de plantilla de ejemplo de marketing y ventas. ¿Quiere probarlo? También puede instalar la aplicación de plantilla [Ejemplo de marketing y ventas](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).

### <a name="set-a-filter"></a>Establecimiento de un filtro

Abra un informe en [Vista de edición](consumer/end-user-reading-view.md) y aplique un filtro.

En este ejemplo, vamos a filtrar la página YTD Category (Categoría hasta la fecha) de la aplicación de plantilla Ejemplo de marketing y ventas para mostrar solo los valores donde **Región** es igual a **Central**. 
 
![Panel de filtro de informe](media/service-share-reports/power-bi-share-report-filter.png)

Guarde el informe.

### <a name="create-a-filter-in-the-url"></a>Creación de un filtro en la dirección URL

Al agregar el filtro al final de la dirección URL de la página del informe, el comportamiento es ligeramente diferente. La página filtrada tiene el mismo aspecto. Sin embargo, Power BI agrega el filtro a todo el informe y quita los demás valores del panel de filtro.  

Agregue lo siguiente al final de la dirección URL de la página del informe:
   
    ?filter=*tablename*/*fieldname* eq *value*
   
El campo debe ser de tipo número, fecha y hora o cadena. Los valores de *tablename* o *fieldname* no pueden contener espacios.
   
En nuestro ejemplo, el nombre de la tabla es **Geo**, el nombre del campo es **Región** y el valor por el que quiere filtrar es **Central**:
   
    ?filter=Geo/Region eq 'Central'

El explorador agrega caracteres especiales para representar espacios, apóstrofos y barras diagonales, así que el resultado es:
   
    app.powerbi.com/groups/xxxx/reports/xxxx/ReportSection4d00c3887644123e310e?filter=Geo~2FRegion%20eq%20'Central'

![Informe con filtro de dirección URL](media/service-share-reports/power-bi-share-report-filter-url.png)

Guarde el informe.

Consulte el artículo [Filtro de un informe con parámetros de cadena de consulta en la URL](service-url-filters.md) para información mucho más detallada.

## <a name="share-the-filtered-report"></a>Compartir el informe filtrado

1. Cuando [comparta el informe](service-share-dashboards.md), desactive la casilla **Enviar notificación por correo electrónico a los destinatarios**.

    ![Cuadro de diálogo Compartir informe](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envíe el vínculo con el filtro que creó anteriormente.

## <a name="next-steps"></a>Pasos siguientes
* [Formas de compartir el trabajo en Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartir un panel](service-share-dashboards.md)
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/).
* ¿Quiere hacer algún comentario? Vaya al [sitio de la comunidad de Power BI](https://community.powerbi.com/) para efectuar sus sugerencias.

