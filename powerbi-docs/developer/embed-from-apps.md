---
title: Insertar informes o paneles desde aplicaciones
description: Obtenga información para integrar o insertar un informe o un panel desde una aplicación de Power BI y no desde un área de trabajo de aplicación.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2817ccb25fc9aa6d3e8150c776558366dcf0ccb6
ms.sourcegitcommit: 0c870a006e525447497e678484874a2f137b9abd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088848"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Insertar informes o paneles desde aplicaciones

En **Power BI**, puede crear aplicaciones para reunir **paneles** e **informes** relacionados en un solo lugar y publicarlos posteriormente para grandes grupos de usuarios de la organización. El uso de esas aplicaciones es pertinente cuando todos los usuarios son usuarios de Power BI, para poder compartir contenido con ellos mediante aplicaciones de Power BI. Nos gustaría compartir unos cuantos pasos rápidos sobre cómo realizar la inserción de contenido de una aplicación de Power BI publicada en una aplicación de terceros.

## <a name="how-to-grab-report-embed-url-for-embedding"></a>Cómo obtener la dirección URL del informe para la inserción

1. Cree una instancia de la aplicación en un área de trabajo de usuario ("Mi área de trabajo") al compartir con usted mismo o guiar a otro usuario a lo largo de este flujo.

2. Abra el informe que quiera en el servicio Power BI.

3. Vaya a Archivo -> Insertar en SharePoint Online y tome de ahí la dirección URL para insertar del informe (la puede ver en la siguiente instantánea) o llame a la API de REST GetReports/GetReport y extraiga el campo embedURL correspondiente del informe de la respuesta (tenga en cuenta que la llamada a REST no debe tener un identificador de área de trabajo como parte de la dirección URL, ya que la instancia de la aplicación se ha creado en el área de trabajo del usuario).

4. Use la dirección URL para insertar recuperada en el paso 3 para usarla con el SDK de JS.

    ![Insertar desde aplicaciones](media/embed-from-apps/embed-from-app.png)

## <a name="how-to-grab-dashboard-embed-url-for-embedding"></a>Cómo obtener la dirección URL del panel para la inserción

1. Cree una instancia de la aplicación en un área de trabajo de usuario ("Mi área de trabajo") al compartir con usted mismo o guiar a otro usuario a lo largo de este flujo.

2. Llame a la API de REST GetDashboards y extraiga el campo de inserción embedURL correspondiente del panel de la respuesta (tenga en cuenta que la llamada a REST no debe tener un identificador de área de trabajo como parte de la dirección URL, ya que la instancia de la aplicación se ha creado en el área de trabajo del usuario).

3. Use la dirección URL para insertar recuperada en el paso 4 para usarla con el SDK de JS.

## <a name="next-steps"></a>Pasos siguientes

Además, vea cómo insertar desde áreas de trabajo de aplicación para los clientes ajenos y la organización.

> [!div class="nextstepaction"]
>[Insertar para clientes ajenos](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insertar para la organización](embed-sample-for-your-organization.md)