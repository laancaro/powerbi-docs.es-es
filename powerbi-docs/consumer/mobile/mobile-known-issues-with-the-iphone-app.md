---
title: 'Solución de "errores de comunicación" en aplicaciones móviles de iOS: Power BI'
description: 'En este artículo puede se de ayuda si ve este mensaje: "Encontramos errores de comunicación. Es posible que estos errores estén relacionados con la configuración del proxy de la conexión Wi-Fi.'
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: mshenhav
ms.openlocfilehash: 9e487f4305b663028714cbe45ab76abaaa4a6db9
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61135713"
---
# <a name="fixing-communication-failures-in-ios-mobile-apps---power-bi"></a>Solución de "errores de comunicación" en aplicaciones móviles de iOS: Power BI

| ![iPhone](./media/mobile-known-issues-with-the-iphone-app/iphone-logo-50-px.png) | ![iPad](./media/mobile-known-issues-with-the-iphone-app/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone |iPad |

## <a name="we-encountered-communication-failures"></a>"Encontramos errores de comunicación"
"Encontramos errores de comunicación. Estos errores pueden estar relacionados con la configuración del proxy de la conexión Wi-Fi. Es posible que cambiar a otra conexión Wi-Fi resuelva el problema".

Este mensaje podría aparecer si la conexión a Internet del iPhone o iPad requiere configurar un proxy HTTP explícito obligatorio, ya sea manual o automático. En este caso, la aplicación de Power BI no funcionará en el dispositivo iOS.

### <a name="workaround"></a>Solución alternativa
Cambie el iPhone o el iPad a otra conexión que no requiera una configuración del proxy HTTP explícita (es decir, una donde la configuración del proxy HTTP esté desactivada).

## <a name="other-issues"></a>¿Otros problemas?
Pruebe a preguntar a la [comunidad de Power BI](http://community.powerbi.com/).

