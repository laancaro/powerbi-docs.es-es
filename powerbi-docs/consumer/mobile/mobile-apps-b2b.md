---
title: Visualización del contenido de Power BI como usuario invitado externo (Azure AD B2B)
description: Use aplicaciones móviles de Power BI para ver el contenido compartido con usted desde la organización externa.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: mshenhav
ms.openlocfilehash: 900c7b57c2b6283c44e4a1923dd223d7dfd40ef7
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/16/2019
ms.locfileid: "69490364"
---
# <a name="view-power-bi-content-shared-with-you-from-an-external-organization"></a>Visualización del contenido de Power BI compartido con usted desde una organización externa

Power BI se integra con Azure Active Directory business-to-business (Azure AD B2B) para permitir una distribución segura del contenido de Power BI a los usuarios invitados de fuera de la organización. Los usuarios invitados externos pueden usar la aplicación móvil de Power BI para acceder a ese contenido de Power BI compartido con ellos. 


Se aplica a:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Teléfono Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Tableta Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone |iPad |Teléfonos Android |Tabletas Android |

## <a name="accessing-shared-content"></a>Acceder al contenido compartido

**En primer lugar, necesita que un usuario de una organización externa comparta un elemento con usted.** Cuando alguien [comparte un elemento con usted](../../service-share-dashboards.md), ya sea desde la misma organización o desde una organización externa, recibe un correo electrónico con un vínculo a ese elemento compartido. Al seguir ese vínculo en el dispositivo móvil, se abre la aplicación móvil de Power BI. Si la aplicación reconoce que el elemento se ha compartido desde una organización externa, la aplicación se vuelve a conectar a esa organización con su identidad. Luego la aplicación carga todos los elementos que se han compartido con usted desde esa organización.

![Power BI abre un elemento compartido desde el correo electrónico ](./media/mobile-apps-b2b/mobile-b2b-open-item-email.png)

> [!NOTE]
> Si este es el primer elemento que se comparte con usted como usuario invitado externo, debe reclamar la invitación en un explorador. No se puede reclamar la invitación en la aplicación de Power BI.

Siempre que esté conectado a una organización externa, aparece un encabezado negro en la aplicación. Este encabezado indica que no está conectado a la organización principal. Para volver a conectarse a la organización principal, salga del modo invitado.

![Encabezado de usuario invitado de Power BI](./media/mobile-apps-b2b/mobile-b2b-exit-home.png)

Aunque necesite tener un vínculo de artefacto de Power BI para conectarse a una organización externa, una vez que la aplicación cambie, puede acceder a todos los elementos compartidos con usted (no solo el elemento abierto desde el correo electrónico). Para ver todos los elementos a los que puede acceder en la organización externa, vaya al menú de la aplicación y seleccione **Compartido conmigo**. En **Aplicaciones**, también se encuentran las aplicaciones que puede usar.

![Menú de aplicación de Power BI como usuario externo invitado](./media/mobile-apps-b2b/mobile-b2b-menu.png)

## <a name="limitations"></a>Limitaciones

- Los usuarios deben tener una cuenta de Power BI activa y un inquilino principal.
- Los usuarios deben iniciar sesión en su inquilino principal de Power BI para poder acceder al contenido compartido con ellos desde un inquilino externo.
- En Azure AD B2B y Power BI Mobile no se admiten las directivas de acceso condicional ni otras de Intune. Esto significa que la aplicación solo aplica las directivas de la organización principal, si las hubiera.
- Las notificaciones de inserción solo se reciben desde el sitio de la organización principal (aunque el usuario esté conectado como invitado a una organización externa). Al abrir la notificación se vuelve a conectar la aplicación al sitio de la organización principal del usuario.
- Si el usuario cierra la aplicación, cuando se vuelve a abrir, se conecta automáticamente a la organización principal del usuario.
- Al conectarse a una organización externa, algunas acciones están deshabilitadas: elementos favoritos, alertas de datos, comentarios y uso compartido.
- Los datos sin conexión no están disponibles mientras se está conectado a una organización externa.
- Si tiene la aplicación Portal de empresa instalada en el dispositivo, el dispositivo debe estar inscrito.
