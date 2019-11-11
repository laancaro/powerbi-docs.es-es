---
title: Suscripción a informes paginados en el servicio Power BI
description: En este artículo, obtendrá información sobre los aspectos que tener en cuenta para la suscripción a informes paginados en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 08/29/2019
ms.openlocfilehash: dfdacef52ea601e26121dfcaa59ba2b66bb90182
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874626"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Suscripción personal y de otros usuarios a informes paginados en el servicio Power BI 

Ahora puede configurar suscripciones de correo electrónico para usted y otros usuarios para los informes paginados en el servicio Power BI. En general, el proceso es el mismo que para la [suscripción a informes y paneles en el servicio Power BI](service-report-subscribe.md). En este artículo se detallan las diferencias y consideraciones. 

En la configuración de las suscripciones, elija la frecuencia con la que quiere recibir los correos electrónicos: diaria, semanal, mensual o cada hora. También puede elegir las horas a las que quiere que se ejecute la suscripción. En resumen, puede establecer hasta 24 suscripciones distintas para cada informe. 

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
