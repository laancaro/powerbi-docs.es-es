---
title: Inicio de sesión único en la aplicación Windows de Power BI Mobile
description: Lea sobre el inicio de sesión único (SSO) en la aplicación Windows de Power BI Mobile. El inicio de sesión único significa acceder a todas las aplicaciones y recursos necesarios para hacer negocios, iniciando sesión una sola vez, con una única cuenta de usuario.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: mshenhav
ms.openlocfilehash: fdbdebacc2ae41cdfa8296eb6b0c06e52f149cac
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290967"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Inicio de sesión único en la aplicación Windows de Power BI Mobile

Lea sobre el inicio de sesión único (SSO) en la aplicación Windows de Power BI Mobile. El inicio de sesión único significa acceder a todas las aplicaciones y recursos necesarios para hacer negocios, iniciando sesión una sola vez, con una única cuenta de usuario. Una vez que inicie sesión, puede acceder a todas esas aplicaciones sin tener que volver a autenticarse. 

Como la aplicación de Power BI para Windows se integra en Azure Active Directory, puede usar la cuenta de la organización principal no solo para iniciar sesión en los dispositivos unidos a un dominio, sino también para iniciar sesión en el servicio Power BI. Si está viendo Power BI en teléfonos Windows, asegúrese de que la cuenta que use para Power BI está configurada como una cuenta profesional o educativa en la configuración del dispositivo.  

El inicio de sesión único solo se habilita para dispositivos Windows administrados por Windows Azure Active Directory. 

## <a name="sign-in-with-sso"></a>Inicio de sesión con SSO

Para simplificar el proceso de inicio de sesión, al instalar la aplicación por primera vez, esta intenta autenticarse de forma automática en el servicio Power BI mediante el inicio de sesión único. La aplicación le pedirá que proporcione las credenciales de Power BI solo si este proceso no se realiza correctamente.  

Si ya usa la aplicación de Power BI Mobile para Windows, al actualizar a la versión nueva de la aplicación también puede usar el inicio de sesión único. Cierre sesión en la aplicación, ciérrela y vuelva a abrirla. Cuando la aplicación se vuelve a abrir, intenta usar de forma automática las credenciales actuales de Windows para autenticarse en el servicio Power BI. 

Si no quiere usar las credenciales actuales de la sesión activa de Windows para iniciar sesión en Power BI, vaya a **Configuración**, cierre la sesión e inicie sesión con otras credenciales. 
 
## <a name="next-steps"></a>Pasos siguientes

- [Introducción a la aplicación móvil de Power BI para Windows 10](mobile-windows-10-phone-app-get-started.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

