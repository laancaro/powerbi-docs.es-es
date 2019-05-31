---
title: Auto instalar aplicaciones de Power BI cuando inserte contenido para su organización
description: Obtenga información sobre cómo automáticamente aplicaciones de instalación de Power BI cuando inserte contenido para su organización.
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: bb9ba5531c2a23f15ccbf98261e246ab7080aecb
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61376221"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Instalar aplicaciones de Power BI automáticamente al insertar contenido para su organización

Para insertar contenido desde una aplicación, debe tener el usuario que se insertan [acceso a la aplicación](../service-create-distribute-apps.md). Si la aplicación se instala para el usuario, a continuación, insertar funciona sin problemas. Para obtener más información, consulte [incrustar informes o paneles de la aplicación](embed-from-apps.md). Es posible definir en PowerBI.com que todas las aplicaciones pueden [instala automáticamente](https://powerbi.microsoft.com/blog/automatically-install-apps/). Sin embargo, esta acción se realiza en el nivel del inquilino y se aplica a todas las aplicaciones.

## <a name="auto-install-app-on-embedding"></a>Instalar automáticamente la aplicación de incrustación

Si un usuario tiene acceso a una aplicación, pero no está instalada la aplicación, insertar, a continuación, se produce un error. Para evitar estos errores al insertar desde una aplicación, puede permitir instalación automática de la aplicación tras la inserción. Esta acción significa que si no está instalada la aplicación que el usuario intenta insertar, se instala automáticamente para usted. Por lo que el contenido que desea se incrusta inmediatamente, lo que resulta en una experiencia fluida para el usuario.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Inserción para usuarios de Power BI (usuario posee los datos)

Para permitir la instalación automática de aplicaciones para los usuarios, debe conceder el permiso "Crear contenido" de la aplicación cuando [registrando su aplicación](register-app.md#register-with-the-power-bi-application-registration-tool), o agréguela si ha registrado la aplicación.

![Aplicación de registro crea contenido](media/embed-auto-install-app/register-app-create-content.png)

A continuación, deberá proporcionar el identificador de aplicación en la dirección URL. Para proporcionar el identificador de aplicación, el creador de la aplicación en primer lugar debe instalar la aplicación, a continuación, utilice una de las [API de Rest de Power BI](https://docs.microsoft.com/rest/api/power-bi/) llamadas - [obtener informes](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) o [obtener paneles](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). A continuación, el creador de la aplicación debe tomar la dirección Url de la respuesta de API de REST. El identificador de aplicación aparece en la dirección URL si el contenido procede de una aplicación.  Una vez que la dirección URL de inserción, se puede usar para insertar con regularidad.

## <a name="secure-embed"></a>Proteger incrustar

Para usar la instalación automática de aplicaciones, el creador de la aplicación en primer lugar debe instalar la aplicación, a continuación, vaya a la aplicación en PowerBI.com, navegue hasta el informe y obtener el vínculo de manera habitual. Todos los usuarios con acceso a la aplicación que puede usar el vínculo pueden incrustar el informe.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* Solo puede insertar informes y paneles para este escenario.

* Esta característica no se admite para la aplicación posee los datos y escenarios de inserción de SharePoint.