---
title: 'Clientes dedicados de Office 365: problemas conocidos'
description: 'Compatibilidad con clientes dedicados de Office 365: problemas conocidos. En este tema se describen los problemas específicos de un cliente dedicado de Office 365. Esto incluye las limitaciones de la función de grupo, así como la aplicación de iPhone con dominios personales.'
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 8f9ab0a9a4beddf9be3fc933174f92ac4ae96a6b
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026509"
---
# <a name="office-365-dedicated-customers---known-issues"></a>Clientes dedicados de Office 365: problemas conocidos
Power BI es ahora compatible con los clientes dedicados de Office 365.  Si usted es un cliente dedicado de O365, puede iniciar sesión con una cuenta de ese inquilino y usar Power BI. Actualmente existen dos problemas conocidos.

## <a name="groups"></a>Grupos
Al seleccionar **Miembros** o **Calendario** en el menú contextual del grupo, se le redirigirá a la aplicación de correo.  **Archivos** y **Conversaciones** funcionan según lo previsto.

![Grupo de Power BI](media/service-admin-office-365-dedicated-known-issues/group-menu.png)

## <a name="iphone-app---sign-in-with-vanity-domain-leads-to-error"></a>Aplicación para iPhone: el inicio de sesión con el dominio personal provoca un error
Al iniciar sesión, en la aplicación para iPhone, mediante un inicio de sesión con un dominio personal, puede producirse un error.

*Error de inicio de sesión*  
*Error interno inesperado. Inténtelo de nuevo.*

Para evitar este problema, inicie sesión con la dirección de correo electrónico que aparece al hacer clic en el icono de usuario en el servicio de Power BI en lugar de con el dominio personal.

![Correo electrónico de inicio de sesión](media/service-admin-office-365-dedicated-known-issues/sign-in-address.png)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

