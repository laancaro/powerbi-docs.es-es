---
title: Conexión a Office365Mon con Power BI
description: Office365Mon para Power BI
author: teddybercovitz
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 8/29/2019
ms.author: tebercov
LocalizationGroup: Connect to services
ms.openlocfilehash: 5d31eccd52164bb4d1ff37532d89dc7e147693d3
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060827"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Conexión a Office365Mon con Power BI
Analizar los datos de rendimiento de estado e interrupciones de Office 365 es fácil con Power BI y la plantilla de aplicación Office365Mon. Power BI recupera los datos (incluidos los de sondeo de estado e interrupciones) y, a continuación, crea un panel integrado e informes basados en esos datos.

Conéctese a la [aplicación de plantilla Office365Mon](https://app.powerbi.com/groups/me/getdata/services/office365mon) para Power BI.

>[!NOTE]
>Se necesita una cuenta de administrador de Office365Mon para conectarse a la aplicación de plantilla de Power BI y cargarla.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Seleccione **Office365Mon** \> **Obtener**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. En Método de autenticación, seleccione **oAuth2** \> **Iniciar sesión**.
   
   Cuando se le solicite, escriba sus credenciales de administrador de Office365Mon y siga el proceso de autenticación.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Una vez que Power BI importe los datos, verá un nuevo panel, el informe y el conjunto de datos en el panel de navegación izquierdo. Los nuevos elementos están marcados con un asterisco amarillo \*. Seleccione la entrada de Office365Mon.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](consumer/end-user-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

## <a name="troubleshooting"></a>Solución de problemas
Si recibe el mensaje **"Error de inicio de sesión"** después de usar las credenciales de la suscripción a Office365Mon para iniciar sesión, la cuenta que está usando no tiene permisos para recuperar los datos de Office365Mon de su cuenta. Compruebe que se trata de una cuenta de administrador y vuelva a intentarlo.

## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](fundamentals/power-bi-overview.md)

[Obtener datos para Power BI](service-get-data.md)

