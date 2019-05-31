---
title: Confianza de los conectores de terceros en Power BI
description: Para confiar en un conector de terceros con signo en Power BI
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607777"
---
# <a name="trusting-third-party-connectors"></a>Confiar en los conectores de terceros

## <a name="why-do-you-need-trusted-third-party-connectors"></a>¿Por qué necesita conectores de terceros de confianza?

En Power BI, generalmente recomendamos mantener su "seguridad de extensión de datos' nivel en el nivel superior, que impide la carga de código no están certificada por Microsoft. Sin embargo, puede haber muchos casos en los que desea cargar los conectores específicos: las que ha escrito o las proporcionada por un consultor o un proveedor fuera de la ruta de acceso de certificación de Microsoft.

El desarrollador de un objeto connector determinado puede firmar con un certificado y proporcionarle la información que necesita cargarlo de forma segura sin reducir la configuración de seguridad.

Si desea obtener más información sobre la configuración de seguridad, puede leer sobre ellos [aquí](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Mediante el registro para los conectores de terceros de confianza

Confiar en los conectores de terceros en Power BI se realiza enumerando la huella digital del certificado que desea confiar en un valor del registro especificada. Si esta huella digital coincide con la huella digital del certificado en el conector que desea cargar, podrá realizar la carga en el nivel de seguridad "Recomendadas" de Power BI. 

La ruta de acceso del registro es HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Asegúrese de que existe la ruta de acceso o crearla. Elegimos esta ubicación debido a la que se controla principalmente mediante la directiva de TI, así como que requiere acceso de administración del equipo local para editar. 

![Establecer el registro de Power BI Desktop con ninguna clave de terceros de confianza](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Agregue un nuevo valor en la ruta de acceso especificada anteriormente. El tipo debe ser "Valor de cadena múltiple" (REG_MULTI_SZ), y debe llamarse "TrustedCertificateThumbprints" 

![Registro de Power BI Desktop con una entrada para los conectores de terceros de confianza, pero no hay claves](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Agregue las huellas digitales de los certificados de confianza. Puede agregar varios certificados mediante el uso de "\0" como un delimitador, o en el editor del registro, derecho -> haga clic en modificar y colocan cada huella digital en una línea nueva. Huella digital de ejemplo procede de un certificado autofirmado. 

 ![Registro de Power BI Desktop con un conjunto de claves de confianza de terceros](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Si ha seguido las instrucciones correctamente y recibieron la huella digital adecuada por el desarrollador, ahora debe ser capaz de forma segura los conectores de confianza firmados con el certificado asociado.

## <a name="how-to-sign-connectors"></a>Los conectores de inicio de sesión

Si tiene un conector de usted o un desarrollador debe iniciar sesión, puede leer sobre él en la documentación de Power Query [aquí](https://docs.microsoft.com/power-query/handlingconnectorsigning).
