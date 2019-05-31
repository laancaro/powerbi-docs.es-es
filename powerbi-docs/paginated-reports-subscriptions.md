---
title: Suscribirse a informes paginados en el servicio Power BI
description: En este artículo, obtendrá información sobre las cosas a tener en cuenta sobre la suscripción a informes paginados en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222193"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Suscribirse usted mismo y a otros usuarios a los informes paginados en el servicio Power BI 

Ahora puede configurar suscripciones de correo electrónico para usted y otros usuarios para los informes paginados en el servicio Power BI. En general, el proceso es el mismo que [suscribirse a informes y paneles en el servicio Power BI](service-report-subscribe.md). En este artículo se detalla las diferencias y consideraciones. 

En la configuración de las suscripciones, elija la frecuencia con la desea recibir los correos electrónicos: diaria, semanal o cada hora. Si elige diariamente o semanalmente, puede elegir la hora desea que ejecute la suscripción. En resumen, puede establecer hasta 24 distintas suscripciones al día para cada informe. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Consideraciones para las suscripciones de informe paginado 

- A diferencia de las suscripciones a los paneles o informes de Power BI, la suscripción contiene datos adjuntos de la salida de informe completo.  Se admiten los siguientes tipos de datos adjuntos: Presentación de PowerPoint (PPTX), PDF, libro de Excel (XLSX), documento de Word (doc), CSV y XML.

- No hay ninguna imagen de vista previa del informe en el cuerpo del correo electrónico.  Estamos planeando tener la imagen de la primera página del informe como un elemento opcional. 

- El tamaño de los datos adjuntos de informes máximo es 25 MB. 

- Se pueden suscribir a otros usuarios para los informes paginados que se conectan a los orígenes de datos admitidos actualmente, incluidos los conjuntos de datos de Azure Analysis Services o Power BI. Tenga en cuenta que los datos adjuntos de informes reflejan los datos según sus permisos, igual que SQL Server Reporting Services lo hace hoy en día. 

- Suscripciones de la página de informe están vinculadas al nombre del informe.  

- Suscripciones de correo electrónico se envían con los valores predeterminados de parámetros del informe. 

- No hay ningún **después de la actualización de datos** opción para la frecuencia con informes paginados. Obtendrá siempre los valores más recientes del origen de datos subyacente. 

## <a name="next-steps"></a>Pasos siguientes

[Suscribirse a usted y a otros a informes y paneles en el servicio Power BI](service-report-subscribe.md)

[¿Qué son los informes paginados en Power BI Premium? (versión preliminar)](paginated-reports-report-builder-power-bi.md)
