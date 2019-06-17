---
title: Archivo de inclusión
description: Archivo de inclusión
services: powerbi
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: mblythe
ms.openlocfilehash: 94b6959b6bcbf250e54a353e8b725b6c9e5a2e30
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448364"
---
## <a name="single-sign-on"></a>Inicio de sesión único

Después de publicar un conjunto de datos DirectQuery de Azure SQL en el servicio, puede habilitar el inicio de sesión único (SSO) a través de OAuth2 de Azure Active Directory (Azure AD) para los usuarios finales.

Para habilitar el inicio de sesión único, vaya a la configuración del conjunto de datos, abra la pestaña **Orígenes de datos** y active la casilla SSO.

![Configuración del cuadro de diálogo de Azure SQL con DirectQuery](media/direct-query-sso/sso-dialog.png)

Cuando se habilita la opción SSO y los usuarios acceden a informes creados sobre el origen de datos, Power BI envía sus credenciales autenticadas de Azure AD en las consultas a la base de datos o el almacenamiento de datos de Azure SQL. Esto permite a Power BI respetar la configuración de seguridad establecida en el nivel de origen de datos.

La opción SSO surte efecto en todos los conjuntos de datos que usan este origen de datos. No afecta el método de autenticación utilizado para los escenarios de importación.

> [!Note]
> No se admite Azure Multi-Factor Authentication (MFA). Los usuarios que quieran usar SSO con Azure SQL DirectQuery deben excluirse de MFA.