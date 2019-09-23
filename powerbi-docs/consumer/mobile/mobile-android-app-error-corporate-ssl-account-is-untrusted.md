---
title: Corrección del problema de "su certificado SSL corporativo no es de confianza"
description: Al iniciar sesión en la aplicación de Android para Power BI, podría ver el mensaje "No se pudo realizar la autenticación porque este dispositivo considera que su certificado SSL corporativo no es de confianza".
.": ''
author: paulinbar
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 08/28/2019
ms.author: mshenhav
ms.openlocfilehash: 19bcdf08d4eacff5e080bf1a2f987ea848e4bfb9
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/16/2019
ms.locfileid: "70840907"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>Corrección del problema de "su certificado SSL corporativo no es de confianza" - Power BI
Al iniciar sesión en la aplicación móvil de Android para Microsoft Power BI, podría ver el mensaje "No se pudo realizar la autenticación porque este dispositivo considera que su certificado SSL corporativo no es de confianza. Póngase en contacto con el administrador de TI de su compañía". 

El procedimiento que debe seguir normalmente depende del sistema operativo del dispositivo Android, pero hay un par problemas que también pueden producir este error.

## <a name="on-android-7-or-later"></a>Android 7 y versiones posteriores
Busque una actualización para una aplicación denominada **Chrome** e instálela.

## <a name="on-android-6-and-earlier"></a>Android 6 y versiones anteriores
El dispositivo podría necesitar una versión actualizada de System Webview. Es posible que esté instalado en el dispositivo, y solo deberá hacer clic en **Actualizar**.

Si WebView del sistema no está instalado en el dispositivo:

1. En el dispositivo Android, cierre Power BI.
2. Abra Google Play Store y busque **WebView del sistema** de Google Inc.
3. Instálelo.
4. Reinicie la aplicación Power BI e inicie sesión.

## <a name="time-zone-settings"></a>Configuración de zona horaria
La configuración de zona horaria del dispositivo podría no ser correcta. 

Vaya a **Ajustes** > **Sistema** > **Fecha y hora** para comprobarla.

## <a name="custom-authentication-server"></a>Servidor de autenticación personalizada
Si usa un servidor de autenticación personalizada, el certificado SSL del servidor de autenticación de la empresa podría no ser válido. Trabaje con el equipo de TI de su organización para probar la configuración del servidor de autenticación corporativo, con las instrucciones de [este artículo](https://support.microsoft.com/en-us/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce).

## <a name="next-steps"></a>Pasos siguientes
* [Descarga de la aplicación Android](http://go.microsoft.com/fwlink/?LinkID=544867) desde la tienda de aplicaciones Android.
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/) 

