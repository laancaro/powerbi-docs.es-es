---
title: Uso del inicio de sesión único (SSO) en orígenes de datos locales
description: Configure la puerta de enlace para habilitar el inicio de sesión único (SSO) desde Power BI a orígenes de datos locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/15/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 9e91c162c9b748fd0ef122aed8fc7ffee6dba5fc
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448287"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Introducción al inicio de sesión único (SSO) para puertas de enlace de Power BI

Puede lograr una conectividad de inicio de sesión único directa con la habilitación de la actualización de los informes y paneles de Power BI con datos locales, mediante la configuración de la puerta de enlace de datos local con la delegación restringida de Kerberos o con SAML (Lenguaje de marcado de aserción de seguridad). La puerta de enlace de datos local facilita el inicio de sesión único (SSO) mediante DirectQuery, que es lo que utiliza para conectarse a los orígenes de datos locales.

Actualmente se admiten estos orígenes de datos:

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) y [SAML](service-gateway-sso-saml.md))
* SAP BW ([Kerberos](service-gateway-sso-kerberos.md))
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))
* También es posible que el inicio de sesión único [otros orígenes de datos](desktop-directquery-data-sources.md#single-sign-on-sso-for-directquery-sources) sin usar una puerta de enlace de datos

Cuando un usuario interactúa con un informe de DirectQuery en el servicio Power BI, cada operación de filtro cruzado, división, ordenación y edición de informes puede dar lugar a consultas que se ejecutan en vivo en el origen de datos local subyacente.  Cuando se configura SSO para el origen de datos, las consultas se ejecutan bajo la identidad del usuario que interactúa con Power BI (es decir, a través de la experiencia web o aplicaciones móviles de Power BI). Por lo tanto, cada usuario ve los datos para los que tiene permisos en el origen de datos subyacente: con el inicio de sesión único configurado, no hay ningún almacenamiento en caché de datos compartido entre distintos usuarios.

## <a name="query-steps-when-running-sso"></a>Pasos de consulta cuando se ejecuta SSO

Una consulta que se ejecuta con SSO consta de tres pasos, tal como se muestra en el diagrama siguiente.

![Pasos de consulta de SSO](media/service-gateway-sso-overview/sso-query-steps.png)

> [!NOTE]
> SSO para Oracle aún no está habilitado, pero está en fase de desarrollo y estará disponible próximamente.

Estos son los detalles adicionales sobre estos pasos:

1. Para cada consulta, el **servicio Power BI** incluye el *nombre principal de usuario* (UPN) al enviar una solicitud de consulta a la puerta de enlace configurada.

2. La puerta de enlace debe asignar el UPN de Azure Active Directory a una identidad de Active Directory local.

   a.  Si Azure AD DirSync (también conocido como *Azure AD Connect*) está configurado, la asignación funciona automáticamente en la puerta de enlace.

   b.  En caso contrario, la puerta de enlace puede buscar y asignar el UPN de Azure AD a un usuario local mediante la realización de una búsqueda en el dominio local de Active Directory.

3. El proceso del servicio de puerta de enlace suplanta al usuario local asignado, abre la conexión a la base de datos subyacente y envía la consulta. No es necesario que la puerta de enlace esté instalada en el mismo equipo que la base de datos.

## <a name="next-steps"></a>Pasos siguientes

Ahora que ya entiende los conceptos básicos de SSO, obtenga información más detallada acerca de Kerberos y SAML:

* [Inicio de sesión único (SSO): Kerberos](service-gateway-sso-kerberos.md)
* [Inicio de sesión único (SSO): SAML](service-gateway-sso-saml.md)
