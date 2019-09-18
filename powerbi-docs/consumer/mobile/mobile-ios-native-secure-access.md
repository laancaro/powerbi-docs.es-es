---
title: Protección de los datos de Power BI con la identificación nativa del dispositivo
description: Aprenda a configurar la aplicación iOS para requerir la identificación adicional antes de acceder a los datos de Power BI
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: b7418c9579a439a18a30a967947c15d58693fd44
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/16/2019
ms.locfileid: "66816832"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-or-passcode"></a>Protección de la aplicación de Power BI con Face ID, Touch ID o código de acceso 

En muchos casos, los datos administrados en Power BI son confidenciales y deben protegerse para que solo los usuarios autorizados puedan tener acceso. 

La aplicación para iOS de Power BI le permite proteger los datos mediante la configuración de la identificación adicional. Deberá proporcionar su Face ID, Touch ID o un código de acceso cada vez que inicie la aplicación o cuando la aplicación pasa de segundo a primer plano.

| ![iPhone](./media/tutorial-mobile-apps-ios-qna/iphone-logo-50-px.png) | ![iPad](./media/tutorial-mobile-apps-ios-qna/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone |iPad |

## <a name="turn-on-face-id-touch-id-or-passcode-in-app-setting"></a>Activación de Face ID, Touch ID o un código de acceso en la configuración de la aplicación

Para usar la identificación adicional en Power BI, vaya a la configuración de la aplicación en **Privacidad y seguridad**. Verá la opción para activar Face ID, Touch ID o un código de acceso, según las funcionalidades del dispositivo.

![Página de configuración de la aplicación para iOS de Power BI](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-setting.png)

Una vez que esta opción está activada, cada vez que inicie Power BI o lo ponga en primer plano, se le pedirá que proporcione su identificación antes de que pueda tener acceso a la aplicación. 

La decisión de solicitar Face ID, Touch ID o un código de acceso la realiza iOS, según la funcionalidad del dispositivo. Si el dispositivo admite Face ID, deberá usarlo. Si el dispositivo admite Touch ID, deberá usarlo. Si no admite ninguno de los dos, deberá proporcionar un código de acceso.

![Face ID de Power BI para iOS](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="use-mdm-to-enforce-face-id-touch-id-or-passcode"></a>Uso de MDM para requerir Face ID, Touch ID o un código de acceso

Algunas organizaciones tienen directivas de seguridad y cumplimiento normativo que requieren la identificación adicional antes de tener acceso a los datos confidenciales del negocio. 

La aplicación móvil para iOS de Power BI permite a los administradores controlar esa configuración mediante la inserción de los valores de configuración de aplicación de Microsoft Intune y otras soluciones de administración de dispositivos móviles (MDM). Los administradores pueden usar la directiva de protección de aplicaciones para activar esta configuración para todos los usuarios o para un grupo de usuarios.

|Clave  |Tipo  |Descripción  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booleano | El valor predeterminado es False. <br>Cuando se establece en True, la aplicación obligará a que los usuarios se identifiquen con Face ID, Touch ID o un código de acceso antes de que puedan ver los datos de Power BI en la aplicación. Los usuarios que no tienen Face ID, Touch ID o un código de acceso configurado en su dispositivo, deberán configurarlo antes de poder acceder a Power BI.  |

## <a name="next-steps"></a>Pasos siguientes

[Uso de MDM para configurar la aplicación para iOS de Power BI de forma remota](mobile-app-configuration.md)
