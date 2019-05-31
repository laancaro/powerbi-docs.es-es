---
title: Ver Power BI contenido como un usuario externo invitado (Azure AD B2B)
description: Usar aplicaciones móviles de Power BI para ver contenido compartido con usted de organización externa.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: mshenhav
ms.openlocfilehash: a15da4349ce97e34c8321909abc862e424b2839c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61338776"
---
# <a name="view-power-bi-content-shared-with-you-from-an-external-organization"></a>Ver el contenido de Power BI compartido con usted desde una organización externa

Power BI se integra con Azure Active Directory business-to-business (B2B de Azure AD) para permitir una distribución segura de contenido de Power BI a usuarios invitados ajenos a su organización. Y los usuarios externos invitados pueden usar la aplicación móvil de Power BI para tener acceso a ese contenido de Power BI compartido con ellos. 


Se aplica a:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Teléfono Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Tableta Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone |iPad |Teléfonos Android |Tabletas Android |

## <a name="accessing-shared-content"></a>Tener acceso al contenido compartido

**En primer lugar, se necesita a alguien de una organización externa para compartir un elemento con usted.** Cuando alguien [comparte un elemento con usted](../../service-share-dashboards.md), desde la misma organización o de una organización externa, recibirá un correo electrónico con un vínculo al elemento compartido. Siga este vínculo en el dispositivo móvil, abre la aplicación móvil de Power BI. Si la aplicación reconoce que se ha compartido el elemento de una organización externa, la aplicación vuelve a conectarse a dicha organización con su identidad. La aplicación, a continuación, carga todos los elementos que se han compartido con usted de dicha organización.

![Power BI abrir elemento compartido desde el correo electrónico ](./media/mobile-apps-b2b/mobile-b2b-open-item-email.png)

> [!NOTE]
> Si se trata del primer elemento compartido con usted como usuario externo invitado, debe reclamar la invitación de un explorador. Puede no puede reclamar la invitación de la aplicación Power BI.

Mientras está conectado a una organización externa, aparece un encabezado de color negro en la aplicación. Este encabezado indica que no están conectados a su organización principal. Para conectarse a su organización principal, salga del modo de invitado.

![Encabezado de usuario invitado de Power BI](./media/mobile-apps-b2b/mobile-b2b-exit-home.png)

Aunque debe tener un vínculo de artefacto de Power BI para conectarse a una organización externa, una vez que se activa la aplicación, puede tener acceso a todos los elementos que se hayan compartido contigo (no solo el elemento que abrió desde el correo electrónico). Para ver todos los elementos son accesibles en la organización externa, vaya al menú de aplicación y seleccione **compartido conmigo**. En **aplicaciones** buscar aplicaciones que pueden usar también.

![Menú de la aplicación Power BI como usuario externo invitado](./media/mobile-apps-b2b/mobile-b2b-menu.png)

## <a name="limitations"></a>Limitaciones

- Acceso condicional y otras directivas de Intune no se admiten en Azure AD B2B y en Power BI mobile. Esto significa que la aplicación aplica solo las directivas de la organización principal, si existen.
- Se reciben notificaciones de inserción desde el sitio de la organización principal solo (incluso cuando está conectado el usuario como invitado a una organización externa). Apertura de la notificación de volver a conecta la aplicación al sitio de la organización principal del usuario.
- Si el usuario cierra la aplicación, al volver a abrir la aplicación se conecta automáticamente a la organización principal del usuario.
- Cuando se conecta a una organización externa, algunas acciones están deshabilitadas: favorito elementos, las alertas de datos, comentarios y el uso compartido.
- Datos sin conexión no están disponibles mientras está conectado a una organización externa.
- Si tiene la aplicación de Portal de empresa instalada en el dispositivo, se debe inscribir su dispositivo.
