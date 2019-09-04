---
title: Opciones de configuración de la aplicación para iOS de Power BI
description: Cómo personalizar el comportamiento de Power BI para iOS mediante una herramienta de MDM
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: bc9c6dd8cd892ab0304cc5a99a3bb780486f32f0
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160154"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Configuración remota de la aplicación para iOS de Power BI mediante la herramienta de administración de dispositivos móviles (MDM)

La aplicación para iOS de Power BI Mobile admite opciones de la aplicación que permiten a los administradores de Office 365 y de administración de dispositivos móviles (MDM), como Intune, personalizar el comportamiento de la aplicación.

La aplicación para iOS de Power BI Mobile admite los siguientes escenarios de configuración:

- Configuración del servidor de informes
- Configuración de la protección de datos

## <a name="report-server-configuration"></a>Configuración del servidor de informes

La aplicación para iOS de Power BI permite a los administradores "insertar" de forma remota la configuración del servidor de informes con los dispositivos inscritos.

| Clave | Tipo | Descripción |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Cadena | Dirección URL del servidor de informes.<br><br>Debe comenzar por http o https.|
| com.microsoft.powerbi.mobile.ServerUsername | Cadena | (opcional)<br><br>El nombre de usuario que se usará para conectar el servidor.<br><br>Si no existe, la aplicación pide al usuario que escriba el nombre de usuario para la conexión.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadena | (opcional)<br><br>El valor predeterminado es “Servidor de informes”<br><br>Nombre descriptivo que se usa en la aplicación para representar al servidor. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | (opcional)<br><br>El valor predeterminado es True. Si se establece en True, invalida cualquier definición del servidor de informes que ya esté disponible en el dispositivo móvil. Los servidores existentes ya configurados se eliminan. Al establecer Reemplazar en True también se evita que el usuario quite esa configuración.<br><br>Si se establece en False, se agregan los valores insertados, dejando cualquier configuración existente. Si la misma dirección URL del servidor ya está configurada en la aplicación móvil, esta deja dicha configuración tal cual. La aplicación no pide al usuario que vuelva a autenticarse para el mismo servidor. |

## <a name="data-protection-setting"></a>Configuración de la protección de datos

La aplicación para iOS de Power BI ofrece a los administradores la capacidad de personalizar la configuración predeterminada para las opciones de seguridad y privacidad. Puede obligar a que los usuarios proporcionen su identificación Face ID, Touch ID o un código de acceso al acceder a la aplicación de Power BI.

| Clave | Tipo | Descripción |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booleano | El valor predeterminado es False. <br><br>La identificación biométrica, como Touch ID o Face ID, puede ser requerida para que los usuarios puedan acceder a la aplicación en su dispositivo. Cuando es requerida, la identificación biométrica se usa además de la autenticación.<br><br>Si usa directivas de protección de aplicaciones, Microsoft recomienda deshabilitar esta opción para impedir solicitudes de acceso dobles. |

## <a name="deploying-app-configuration-settings"></a>Implementación de los valores de configuración de la aplicación

Los pasos siguientes le permiten crear una directiva de configuración de aplicaciones. Una vez creada la directiva de configuración, puede asignar su configuración a grupos de usuarios.

1. Conecte la herramienta MDM.

2. Cree una nueva directiva de configuración de aplicaciones y asígnele un nombre.

3. Elija los usuarios a los que quiere distribuir esta directiva de configuración de aplicación.

4. Cree pares de clave y valor para la configuración que desea insertar a los usuarios.

El portal de Intune permite a los administradores implementar fácilmente esta configuración a la aplicación para iOS de Power BI mediante directivas de configuración.
No obstante, se admite cualquier proveedor de MDM. Si no usa Intune, deberá consultar con la documentación de MDM sobre cómo implementar esta configuración.

## <a name="next-steps"></a>Pasos siguientes

* Descargue la [aplicación móvil Power BI para iPhone](http://go.microsoft.com/fwlink/?LinkId=522062)
* Siga [@MSPowerBI en Twitter](https://twitter.com/MSPowerBI)
* Únase a la conversación en la [comunidad de Power BI](http://community.powerbi.com/)
