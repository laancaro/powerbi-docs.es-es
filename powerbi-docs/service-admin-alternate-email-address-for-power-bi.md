---
title: Usar una dirección de correo electrónico alternativa
description: Usar una dirección de correo electrónico alternativa
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906650"
---
# <a name="use-an-alternate-email-address"></a>Usar una dirección de correo electrónico alternativa

Al suscribirse a Power BI, proporciona una dirección de correo electrónico. De forma predeterminada, Power BI usa esta dirección para enviar actualizaciones acerca de la actividad en el servicio. Por ejemplo, cuando alguien le envía una invitación de uso compartido, se remite a esta dirección.

A veces, puede que desee que estos correos electrónicos se entreguen a una dirección de correo electrónico alternativa en lugar de a la que usó para registrarse. En este artículo se explica cómo especificar una dirección alternativa en Office 365 y en PowerShell. El artículo también explica cómo se resuelve una dirección de correo electrónico en Azure Active Directory (Azure AD).

> [!NOTE]
> Especificar una dirección alternativa no afecta a qué dirección de correo electrónico usa Power BI para las actualizaciones del servicio, los boletines y otras comunicaciones promocionales. Estas comunicaciones siempre se envían a la dirección de correo electrónico que utilizó al suscribirse a Power BI.

## <a name="use-office-365"></a>Uso de Office 365

Para especificar una dirección alternativa en Office 365, siga estos pasos.

1. Abra la [página de información personal de Office 365](https://portal.office.com/account/#personalinfo). Si la aplicación le pide, inicie sesión con la dirección de correo electrónico y contraseña que se usa para Power BI.

1. En el menú izquierdo, seleccione **Información personal**.

1. En la sección **Detalles de contacto**, seleccione **Editar**.

    Si no se puede editar los detalles, esto significa que el Administrador de Office 365 administra la dirección de correo electrónico. Póngase en contacto con su administrador para actualizar su dirección de correo electrónico.

    ![Detalles de contacto](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. En el **correo electrónico alternativo** , escriba la dirección de correo electrónico que le gustaría Office 365 que se usará para las actualizaciones de Power BI.

## <a name="use-powershell"></a>Uso de PowerShell

Para especificar una dirección alternativa en PowerShell, use el comando [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Resolución de direcciones de correo electrónico en Azure AD

Captura de una instancia de Azure AD token de inserción para Power BI, puede usar uno de los tres tipos diferentes de direcciones de correo electrónico:

* La dirección de correo electrónico principal asociada con la cuenta de Azure AD del usuario

* La dirección de correo electrónico de UserPrincipalName (UPN)

* El atributo de matriz *Otra dirección de correo electrónico*

Power BI selecciona la dirección de correo electrónico que se va según la siguiente secuencia:

1. Si el atributo de correo electrónico del objeto de usuario de Azure AD está presente, Power BI usará ese atributo para la dirección de correo electrónico.

1. Si la dirección de correo electrónico UPN *no* es una dirección de correo electrónico con el dominio **\*.onmicrosoft.com** (la información que aparece detrás del símbolo "\@"), Power BI usa ese atributo de correo para la dirección de correo electrónico.

1. Si el *otra dirección de correo electrónico* está presente el atributo de matriz en el objeto de usuario de Azure AD y, después, Power BI usa el primer correo electrónico de la lista (dado que puede haber una lista de correos electrónicos en este atributo).

1. Si ninguna de las condiciones anteriores están presentes, Power BI usa la dirección UPN.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)