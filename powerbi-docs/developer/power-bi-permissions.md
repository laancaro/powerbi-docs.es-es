---
title: Permisos de Power BI
description: Permisos de Power BI
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 8a48ec007f2d8c9c07de5cc0d51049e3dbf19662
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61269366"
---
# <a name="power-bi-permissions"></a>Permisos de Power BI

## <a name="permission-scopes"></a>Ámbitos de permiso

Permisos de Power BI proporcionan a una aplicación la capacidad de realizar ciertas acciones en nombre de un usuario. Todos los permisos deben ser aprobados por un usuario para que sean válidos.

| Nombre para mostrar | Descripción | Valor de ámbito |
| --- | --- | --- |
| Ver todos los conjuntos de datos |La aplicación puede ver todos los conjuntos de datos para el usuario que tiene la sesión iniciada y los conjuntos de datos a los que tiene acceso el usuario. |Dataset.Read.All |
| Leer y escribir todos los conjuntos de datos |La aplicación puede ver y escribir en todos los conjuntos de datos para el usuario que tiene la sesión iniciada y los conjuntos de datos a los que tiene acceso el usuario. |Dataset.ReadWrite.All |
| Agregar datos al conjunto de datos de un usuario |Proporciona acceso a una aplicación para agregar o eliminar filas de conjuntos de datos de un usuario. Este permiso no concede a la aplicación acceso a los datos del usuario. |Data.Alter_Any |
| Crear contenido |La aplicación puede crear automáticamente el contenido y los conjuntos de datos de un usuario. |Content.Create |
| Ver grupos de usuarios |La aplicación puede ver todos los grupos a los que pertenece el usuario que tiene la sesión iniciada. |Group.Read |
| Ver todos los grupos |La aplicación puede ver todos los grupos a los que pertenece el usuario que tiene la sesión iniciada. |Group.Read.All |
| Leer y escribir en todos los grupos |La aplicación puede ver y escribir en todos los grupos del usuario que ha iniciado la sesión y en los grupos a los que el usuario tiene acceso. |Group.ReadWrite.All |
| Ver todos los paneles |La aplicación puede ver todos los paneles del usuario que tiene la sesión iniciada y los paneles a los que este tiene acceso. |Dashboard.Read.All |
| Ver todos los informes |La aplicación puede ver todos los informes para el usuario que tiene la sesión iniciada y los informes a los que tiene acceso el usuario. La aplicación también puede ver los datos de los informes, así como su estructura. |Report.Read.All |
| Leer y escribir todos los informes |La aplicación puede ver y escribir en todos los informes del usuario que inició la sesión y en los informes a los que el usuario tiene acceso. No proporciona derechos para crear un nuevo informe. |Report.ReadWrite.All |
| Leer y escribir en todas las capacidades |La aplicación puede ver y escribir en todas las capacidades del usuario que ha iniciado la sesión y en cualquier capacidad a la que el usuario tenga acceso. No proporciona derechos para crear una nueva capacidad. |Capacities.ReadWrite.All |
| Leer todas las capacidades |La aplicación puede ver y escribir en todas las capacidades del usuario que ha iniciado la sesión y en cualquier capacidad a la que el usuario tenga acceso. No proporciona derechos para crear una nueva capacidad. |Capacities.Read.All |
| Leer y escribir en todo el contenido del inquilino |La aplicación puede ver y escribir en todos los artefactos, como grupos, informes, paneles y conjuntos de datos en Power BI. La condición es que el usuario que ha iniciado sesión sea un administrador del servicio Power BI. |Tenant.ReadWrite.All |
| Ver todo el contenido del inquilino |La aplicación puede ver todos los artefactos, como grupos, informes, paneles y conjuntos de datos en Power BI. La condición es que el usuario que ha iniciado sesión sea un administrador del servicio Power BI. |Tenant.Read.All |

Una aplicación puede solicitar permisos cuando primero intenta iniciar sesión en la página de un usuario pasando los permisos solicitados en el parámetro de ámbito de la llamada. Si se conceden los permisos, se devolverá un token de acceso a la aplicación que se puede usar en futuras llamadas API. El acceso solo puede ser usado por una aplicación específica.

> [!NOTE]
> Las API de Power BI siguen haciendo referencia a las áreas de trabajo de la aplicación como grupos. Todas las referencias a grupos significan que está trabajando con áreas de trabajo de la aplicación.

## <a name="requesting-permissions"></a>Solicitar permisos

Mientras que puede llamar a la API para autenticarse con un nombre de usuario y una contraseña, para realizar acciones en nombre de otro usuario, necesitará solicitar permisos que el usuario aprobará posteriormente y, a continuación, enviar el token de acceso resultante en todas las futuras llamadas. En este proceso, se sigue el protocolo [OAuth 2.0](http://oauth.net/2/) estándar. Aunque es posible que la implementación real varíe, el flujo de OAuth de Power BI tiene los siguientes elementos:

* **Interfaz de usuario de inicio de sesión** : se trata de una interfaz de usuario que el desarrollador puede evocar para solicitar permisos. Necesitaría que el usuario inicie sesión si no lo ha hecho ya. El usuario también necesitaría aprobar los permisos que solicita la aplicación. La ventana de inicio de sesión publicará un código de acceso o un mensaje de error en una dirección URL de redireccionamiento proporcionada.
  * Power BI debe proporcionar una dirección URL de redireccionamiento estándar para su uso por parte de las aplicaciones nativas.
* **Código de autorización** : los códigos de autorización se devuelven a las aplicaciones web después de iniciar sesión a través de los parámetros de dirección URL en la dirección URL de redireccionamiento. Como son parámetros de entrada, hay cierto riesgo de seguridad. Las aplicaciones web tendrán que intercambiar el código de autorización para un token de autorización
* **Token de autorización** : se usa para autenticar las llamadas de API en nombre de otro usuario. Se limitarán a una aplicación específica. Los tokens tienen una duración establecida y cuando caducan necesitan actualizarse.
* **Token de actualización** : cuando expiran los tokens, se produce un proceso de actualización de estos.

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)