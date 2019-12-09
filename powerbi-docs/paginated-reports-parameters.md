---
title: Creación de parámetros de informes paginados en el servicio Power BI
description: En este artículo, obtendrá información sobre cómo crear parámetros de informes paginados en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: 8afa43cf9d49286a1ec04f7f60aa4a4c4ca7fd16
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831178"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service"></a>Creación de parámetros de informes paginados en el servicio Power BI

En este artículo, obtendrá información sobre cómo crear parámetros de informes paginados en el servicio Power BI.  Un parámetro de informe proporciona una manera de elegir los datos de informe y variar la presentación de los informes. Puede proporcionar un valor predeterminado y una lista de valores disponibles, y los lectores del informe pueden cambiar la selección.  

La siguiente ilustración muestra la vista de diseño del Generador de informes de Power BI para un informe con los parámetros @BuyingGroup, @Customer, @FromDate y @ToDate. 
  
![Parámetros en el generador de informes](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  Los parámetros de informe en el panel Datos de informe.  
  
2.  La tabla con uno de los parámetros del conjunto de datos.  
  
3.  El panel Parámetros. Puede personalizar el diseño de parámetros en el panel de parámetros. 
  
4.  Los parámetros @FromDate y @ToDate tienen datos de tipo **Fecha y hora**. Al ver el informe, puede escribir una fecha en el cuadro de texto o elegir una fecha en el control de calendario. 

5.  Uno de los parámetros en el cuadro de diálogo **Propiedades del conjunto de datos**.  

  
## <a name="create-or-edit-a-report-parameter"></a>Creación o edición del parámetro de un informe  
  
1.  Abra el informe paginado en el Generador de informes de Power BI.

1. En el panel **Datos de informe**, haga clic con el botón derecho en el nodo **Parámetros** > **Agregar parámetro**. Se abre el cuadro de diálogo **Propiedades de parámetro de informe**.  
  
2.  En **Nombre**, escriba un nombre para el parámetro o acepte el nombre predeterminado.  
  
3.  En **Confirmación**, escriba el texto que aparece junto al cuadro de texto del parámetro cuando el usuario ejecuta el informe.  
  
4.  En **Tipo de datos**, seleccione el tipo de datos para el valor del parámetro.  
  
5.  Si el parámetro puede contener un valor en blanco, seleccione **Permitir valor en blanco**.  
  
6.  Si el parámetro puede contener un valor NULL, seleccione **Permitir valor NULL**.  
  
7.  Para permitir al usuario seleccionar más de un valor para el parámetro, seleccione **Permitir varios valores**.  
  
8.  Establezca la opción de visibilidad.  
  
    -   Para mostrar el parámetro en la barra de herramientas en la parte superior del informe, seleccione **Visible**.  
  
    -   Para ocultar el parámetro para que no se muestre en la barra de herramientas, seleccione **Oculto**.  
  
    -   Para ocultar el parámetro y evitar que pueda modificarse en el servidor de informes una vez publicado el informe, seleccione **Interno**. El parámetro de informe solo puede verse entonces en la definición de informe. Para esta opción, debe establecer un valor predeterminado o permitir que el parámetro acepte un valor NULL.  
  
9. Seleccione **Aceptar**. 
  
## <a name="next-steps"></a>Pasos siguientes

Consulte [Ver los parámetros para los informes paginados](consumer/paginated-reports-view-parameters.md) para ver el aspecto de los parámetros en el servicio Power BI.

Para obtener información detallada sobre los parámetros de los informes paginados, consulte [Parámetros del informe en el Generador de informes de Power BI](report-builder-parameters.md).
