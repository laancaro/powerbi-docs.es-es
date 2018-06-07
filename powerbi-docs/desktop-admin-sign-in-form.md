---
title: Administración del formulario de inicio de sesión de Power BI Desktop por parte de los administradores
description: Aprenda a administrar el formulario de inicio de sesión inicial al abrir Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/02/2018
ms.author: davidi
ms.openlocfilehash: f35553acd65aeea2c1bf02b04fcbd665af4b99ea
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721096"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Administración del formulario de inicio de sesión de Power BI Desktop por parte de los administradores
La primera vez que se inicia Power BI Desktop, aparece un formulario de inicio de sesión. Se puede rellenar la información o iniciar sesión en Power BI para continuar. Los administradores administran este formulario mediante una clave de registro. 

![Formulario de inicio de sesión inicial para Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Los administradores usan la siguiente clave de registro para deshabilitar el formulario de inicio de sesión. Esto también se puede desarrollar en toda la organización mediante directivas globales.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Un valor de 0 deshabilitará el cuadro de diálogo.

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

