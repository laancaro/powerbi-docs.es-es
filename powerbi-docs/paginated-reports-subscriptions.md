---
title: Suscripción a informes paginados en el servicio Power BI
description: En este artículo, obtendrá información sobre las cosas a tener en cuenta para la suscripción a informes paginados en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839567"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Suscripción personal y de otros usuarios a informes paginados en el servicio Power BI 

Ahora puede configurar suscripciones de correo electrónico para usted y otros usuarios para los informes paginados en el servicio Power BI. En general, el proceso es el mismo que para la [suscripción a informes y paneles en el servicio Power BI](service-report-subscribe.md). En este artículo se detallan las diferencias y consideraciones. 

En la configuración de las suscripciones, elija la frecuencia con la que desea recibir los correos electrónicos: diaria, semanal o cada hora. Si se elige la frecuencia diaria o semanal, se puede elegir la hora a la que le gustaría que se ejecutara la suscripción. En resumen, puede establecer hasta 24 suscripciones distintas por día para cada informe. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Consideraciones sobre las suscripciones a informes paginados 

- A diferencia de las suscripciones a paneles o informes de Power BI, la suscripción contiene datos adjuntos de la salida completa del informe.  Se admiten los siguientes tipos de datos adjuntos: PDF, presentación de PowerPoint (PPTX), libro de Excel (XLSX), documento de Word (DOCX), archivo CSV y XML.

- No hay ninguna imagen de vista previa del informe en el cuerpo del correo electrónico.  Proyectamos incluir la imagen de la primera página del informe como un elemento opcional. 

- El tamaño máximo de los datos adjuntos del informe es de 25 MB. 

- Puede suscribir a otros usuarios a los informes paginados que se conecten a los orígenes de datos admitidos actualmente, incluidos los conjuntos de datos de Azure Analysis Services o Power BI. Tenga en cuenta que los datos adjuntos del informe reflejan los datos según sus permisos, igual que hace actualmente SQL Server Reporting Services. 

- Las suscripciones a una página del informe están asociadas al nombre del informe.  

- Las suscripciones de correo electrónico se envían con los valores predeterminados de los parámetros del informe. 

- No existe la opción **Después de la actualización de datos** para la frecuencia con los informes paginados. Obtendrá siempre los valores más recientes del origen de datos subyacente. 

## <a name="next-steps"></a>Pasos siguientes

[Suscripción personal y de otros usuarios a informes y paneles en el servicio Power BI](service-report-subscribe.md)

[¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
