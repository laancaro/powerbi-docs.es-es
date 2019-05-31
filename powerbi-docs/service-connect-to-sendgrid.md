---
title: Conexión a SendGrid con Power BI
description: SendGrid para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 2e9da4bc46a741af42a214d4e70fd46bfaa4a541
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61152043"
---
# <a name="connect-to-sendgrid-with-power-bi"></a>Conexión a SendGrid con Power BI
El paquete de contenido de Power BI para SendGrid permite extraer información y estadísticas de una cuenta de SendGrid. Con el paquete de contenido de SendGrid puede visualizar las estadísticas de SendGrid en un panel.

Conéctese al [paquete de contenido de SendGrid](https://app.powerbi.com/getdata/services/sendgrid) para Power BI.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. Seleccione el paquete de contenido de **SendGrid** y haga clic en **Conectar**.
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. Cuando se le solicite, proporcione su nombre de usuario y contraseña de SendGrid. Seleccione **Iniciar sesión**.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. Después de que Power BI importe los datos, verá un nuevo panel, el informe y el conjunto de datos en el panel de navegación izquierdo, rellenado con las estadísticas de correo electrónico de los últimos 90 días. Los nuevos elementos se marcan con un asterisco amarillo \*.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](consumer/end-user-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

## <a name="whats-included"></a>Qué se incluye
Las siguientes métricas están disponibles en el panel de SendGrid:

* Estadísticas generales de correo electrónico: solicitudes, entregado, devuelto, correo no deseado bloqueado, informe de correo no deseado, etc.
* Estadísticas de correo electrónico por categoría
* Estadísticas de correo electrónico por geografía
* Estadísticas de correo electrónico por ISP
* Estadísticas de correo electrónico por dispositivo, cliente, explorador

## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](power-bi-overview.md)

[Obtener datos](service-get-data.md)

