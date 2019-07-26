---
title: Suscripción a informes paginados en el servicio Power BI
description: En este artículo, obtendrá información sobre los aspectos que tener en cuenta para la suscripción a informes paginados en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 07/15/2019
ms.openlocfilehash: 2d48892450bbf6ab09a4bc88cd2be9a58bbdc863
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307084"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Suscripción personal y de otros usuarios a informes paginados en el servicio Power BI 

Ahora puede configurar suscripciones de correo electrónico para usted y otros usuarios para los informes paginados en el servicio Power BI. En general, el proceso es el mismo que para la [suscripción a informes y paneles en el servicio Power BI](service-report-subscribe.md). En este artículo se detallan las diferencias y consideraciones. 

En la configuración de las suscripciones, elija la frecuencia con la que desea recibir los correos electrónicos: diaria, semanal o cada hora. Si se elige la frecuencia diaria o semanal, se puede elegir la hora a la que le gustaría que se ejecutara la suscripción. En resumen, puede establecer hasta 24 suscripciones distintas por día para cada informe. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Consideraciones sobre las suscripciones a informes paginados 

- A diferencia de las suscripciones a paneles o informes de Power BI, la suscripción contiene datos adjuntos de la salida completa del informe.  Se admiten los siguientes tipos de datos adjuntos: PDF, presentación de PowerPoint (PPTX), libro de Excel (XLSX), documento de Word (DOCX), archivo CSV y XML.

- Puede incluir una imagen de vista previa del informe en el cuerpo del correo electrónico.  Esto es opcional y puede diferir ligeramente de la primera página del documento de informe adjunto, en función del formato de datos adjuntos seleccionado. 

- El tamaño máximo de los datos adjuntos del informe es de 25 MB. 

- Puede suscribir a otros usuarios a los informes paginados que se conecten a los orígenes de datos admitidos actualmente, incluidos los conjuntos de datos de Azure Analysis Services o Power BI. Tenga en cuenta que los datos adjuntos del informe reflejan los datos según sus permisos, igual que hace actualmente SQL Server Reporting Services. 

- Las suscripciones de correo electrónico se pueden enviar con los parámetros predeterminados del informe o los seleccionados actualmente.  Puede establecer otros valores de parámetro para cada suscripción que cree para el informe. 

- Si el autor del informe ha establecido parámetros basados en expresiones (por ejemplo, el valor predeterminado es la fecha actual), se usarán en la suscripción como valor predeterminado. Puede cambiar otros valores de parámetro y elegir usar valores actuales, pero a menos que también cambie de forma explícita ese valor, en la suscripción se usa el parámetro basado en expresiones.

- No existe la opción **Después de la actualización de datos** para la frecuencia con los informes paginados. Obtendrá siempre los valores más recientes del origen de datos subyacente. 

## <a name="next-steps"></a>Pasos siguientes

[Suscripción personal y de otros usuarios a informes y paneles en el servicio Power BI](service-report-subscribe.md)

[¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
