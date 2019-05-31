---
title: Configuración del acceso de la aplicación móvil de iOS a un servidor de informes de forma remota
description: Aprenda a configurar las aplicaciones móviles de iOS de forma remota para el servidor de informes.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/15/2018
ms.author: maggies
ms.openlocfilehash: 27b3aad6f1a96c069f56ed68823b71b38115a98a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770634"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Configurar el acceso de la aplicación móvil de iOS de Power BI a un servidor de informes de forma remota

En este artículo se explica cómo usar la herramienta MDM de su organización para configurar el acceso de la aplicación móvil de iOS de Power BI a un servidor de informes de forma remota. Para configurarlo, los administradores de TI deben crear una directiva de configuración de aplicaciones con la información necesaria para que se envíe a la aplicación. 

 Con la conexión del servidor de informes configurada, los usuarios de la aplicación móvil de iOS de Power BI pueden conectarse al servidor de informes de la organización más fácilmente. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Crear la directiva de configuración de aplicaciones en la herramienta MDM 

Como administrador, estos son los pasos que debe seguir en Microsoft Intune para crear la directiva de configuración de aplicaciones. Estos pasos y la experiencia de crear la directiva de configuración de aplicaciones pueden variar en otras herramientas MDM. 

1. Conecte la herramienta MDM. 
2. Cree una nueva directiva de configuración de aplicaciones y asígnele un nombre. 
3. Elija los usuarios a los que quiere distribuir esta directiva de configuración de aplicación. 
4. Crear pares de clave-valor. 

En la tabla de abajo se detallan los pares.

|Clave  |Tipo  |Descripción  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Cadena | URL del servidor de informes <br> Debe empezar por http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Cadena | (opcional) <br> El nombre de usuario que se usará para conectar el servidor. <br> Si no existe, la aplicación pide al usuario que escriba el nombre de usuario para la conexión.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadena | (opcional) <br> El valor predeterminado es “Servidor de informes” <br> Nombre descriptivo que se usa en la aplicación para representar el servidor | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | El valor predeterminado es True <br>Si se establece en "true", invalida cualquier definición de servidor de informes que ya esté disponible en el dispositivo móvil. Los servidores existentes ya configurados se eliminan. <br> Al establecer Reemplazar en True también se evita que el usuario quite esa configuración. <br> Si se establece en “False”, se agregan los valores insertados, dejando cualquier configuración existente. <br> Si la misma dirección URL del servidor ya está configurada en la aplicación móvil, esta deja dicha configuración tal cual. La aplicación no pide al usuario que vuelva a autenticarse para el mismo servidor. |

Este es un ejemplo de configuración de la directiva de configuración mediante Intune.

![Opciones de configuración de Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Los usuarios finales se conectan a un servidor de informes

 Supongamos que publica la directiva de configuración de aplicaciones para una lista de distribución. Cuando los usuarios y los dispositivos de dicha lista de distribución inicien la aplicación móvil de iOS, tendrán la siguiente experiencia. 

1. Se muestra un mensaje que indica que su aplicación móvil está configurada con un servidor de informes y deben pulsar en **Iniciar sesión**.

    ![Iniciar sesión en el servidor de informes](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  En la página **Conectar al servidor**, los detalles del servidor de informes ya están rellenados. Pulsan en **Conectar**.

    ![Detalles del servidor de informes rellenados](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Escriben una contraseña para autenticarse y luego pulsan en **Iniciar sesión**. 

    ![Detalles del servidor de informes rellenados](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Ya pueden ver e interactuar con los KPI y los informes de Power BI almacenados en el servidor de informes.

## <a name="next-steps"></a>Pasos siguientes
[Información general de administrador](admin-handbook-overview.md)  
[Instalar un servidor de informes de Power BI](install-report-server.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

