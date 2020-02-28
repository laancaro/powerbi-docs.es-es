---
title: Inserción de un informe con la pestaña Power BI de Microsoft Teams
description: Con la pestaña Power BI de Microsoft Teams, puede insertar fácilmente informes interactivos en canales y chats.
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 01/31/2020
ms.openlocfilehash: fb4846a777dda4787e1ed0be7de869367a616ea5
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530496"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>Inserción de un informe con la pestaña Power BI de Microsoft Teams

Con la pestaña Power BI actualizada de Microsoft Teams, puede insertar fácilmente informes interactivos en canales y chats de Microsoft Teams.

Use la pestaña Power BI de Microsoft Teams para que sus compañeros encuentren fácilmente los datos que el equipo usa, así como para analizar los datos de los canales del equipo.

## <a name="requirements"></a>Requisitos

Para que la **pestaña Power BI de Microsoft Teams** funcione, se necesita lo siguiente:

- Una licencia de Power BI Pro, o que el informe esté incluido en una [capacidad Power BI Premium (SKU EM o P)](service-premium-what-is.md) con una licencia de Power BI.
- La pestaña Power BI de Microsoft Teams.
- El usuario debe iniciar sesión en el servicio Power BI para activar su licencia de Power BI y consumir el informe.
- El usuario debe tener permiso para ver el informe.

## <a name="embed-your-report"></a>Insertar un informe
Para insertar el informe en un canal o un chat de Microsoft Teams, agréguelo como se describe a continuación.

1. Abra el canal o el chat que quiera en Microsoft Teams y seleccione el icono **+** .

    ![Adición de una pestaña a un canal o un chat](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. Seleccione la pestaña Power BI.

    ![Lista de pestañas de Microsoft Teams con la pestaña Power BI](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. Use las opciones suministradas para elegir un informe, ya sea de un área de trabajo, uno compartido con usted o una aplicación de Power BI.

    ![Configuración de la pestaña Power BI de Microsoft Teams](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. El nombre de la pestaña se actualiza automáticamente para que coincida con el nombre del informe, pero puede cambiarlo. 

5. Presione **Save**(Guardar).

## <a name="supported-reports"></a>Informes admitidos

La pestaña permite insertar los siguientes informes:

- Informes paginados e interactivos
- Informes de Mi área de trabajo, de una nueva experiencia de área de trabajo y de áreas de trabajo clásicas
- Informes de aplicaciones de Power BI


## <a name="grant-access-to-reports"></a>Concesión de acceso a los informes

Insertar un informe en Microsoft Teams no concede permiso a los usuarios para ver el informe de forma automática: hay que [permitir que los usuarios vean los informes en Power BI](service-share-dashboards.md). Para que esto sea más fácil, puede usar un grupo de Office 365 en el equipo. 

> [!IMPORTANT]
> Asegúrese de revisar quién puede ver el informe en el servicio Power BI y de conceder acceso a los usuarios que no están en la lista.

Una forma de garantizar que todos los miembros del equipo van a tener acceso a los informes que se insertan es incluir a esos miembros en una misma área de trabajo en Power BI, y dar acceso a ese grupo de Office 365 del equipo al área de trabajo en cuestión.

## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

- Power BI no admite los mismos idiomas localizados que Microsoft Teams. En consecuencia, es posible que no vea una localización correcta en el informe insertado.
- En la pestaña Power BI de Microsoft Teams no se pueden insertar paneles de Power BI.
- Un usuario que no tenga una licencia de Power BI o permiso en el informe verá el mensaje "El contenido no está disponible".
- Si utiliza Internet Explorer 10, pueden surgir problemas. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- La pestaña Power BI de Microsoft Teams no admite [filtros de URL](service-url-filters.md).
- En las nubes nacionales, la nueva pestaña Power BI no está disponible; es posible que haya una versión anterior disponible que no sea compatible con la nueva experiencia de área de trabajo o con los informes de aplicaciones de Power BI. 
- Una vez guardada la pestaña, su nombre no se podrá cambiar a través de la configuración de la pestaña. Para cambiarlo, use la opción Cambiar nombre.

## <a name="next-steps"></a>Pasos siguientes
- [Compartir un panel con compañeros y otros usuarios](service-share-dashboards.md)  
- [Creación y distribución de una aplicación en Power BI](service-create-distribute-apps.md)  
- [¿Qué es Power BI Premium?](service-premium-what-is.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
