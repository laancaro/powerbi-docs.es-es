---
title: Análisis integrado con Power BI
description: Power BI ofrece API para usar análisis integrados con los paneles e informes en las aplicaciones. Aprenda más sobre la inserción con Power BI tanto en entornos PaaS como SaaS mediante software de análisis integrado, herramientas de análisis integrado o herramientas de inteligencia empresarial de análisis integrado.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051061"
---
# <a name="embedded-analytics-with-power-bi"></a>Análisis integrado con Power BI

El servicio Power BI (SaaS) y el servicio Power BI Embedded en Azure (PaaS) tienen las API para insertar los paneles e informes. Al insertar el contenido, esto le otorga acceso a las últimas características de Power BI como paneles, puertas de enlace y áreas de trabajo de aplicación.

Puede ver la [herramienta de configuración de inserción](https://aka.ms/embedsetup) para empezar rápidamente y descargar una aplicación de ejemplo.

Elija la solución que más le convenga:

* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Para ello, implemente el [Embed para su organización](https://aka.ms/embedsetup/UserOwnsData) solución.
* [Inserción de contenido para sus clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes a los usuarios que no tienen una cuenta de Power BI. Para ello, implemente el [Embed para sus clientes](https://aka.ms/embedsetup/AppOwnsData) solución.

![Ejemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Use las API

Hay dos escenarios principales para insertar contenido de Power BI:
- Inserción de contenido para los usuarios de su organización (que tienen licencias de Power BI). 
 
- Inserción de contenido para los usuarios y los clientes que no necesitan licencias de Power BI. 

El [API de REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/) permite ambos escenarios.

En el caso de clientes y usuarios que no tengan licencia de Power BI, puede insertar paneles e informes en la aplicación personalizada con las mismas API, tanto para la organización como para los clientes. Los clientes verán los datos administrados de la aplicación. Además, los usuarios de Power BI de su organización tienen opciones adicionales para ver *sus datos* directamente en Power BI o en el contexto de la aplicación incrustada. Puede aprovechar al máximo las API de REST y de JavaScript para lo que necesite insertar.

Para entender cómo funciona la inserción, vea el [ejemplo de inserción de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserción de contenido para la organización

La **inserción para la organización** permite ampliar el servicio Power BI. Esta inserción requiere inicio de sesión de los usuarios de su aplicación en el servicio Power BI para ver el contenido. Cuando los usuarios de la organización inician sesión, solo tienen acceso a los paneles e informes de los que sean propietarios o que alguien haya compartido contenido con ellos en el servicio Power BI.

Algunos ejemplos de incrustación de organización son las aplicaciones internas, como [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [(debe tener derechos de administrador) de integración de Microsoft Teams](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), y [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Para incrustar para su organización, consulte [Tutorial: Insertar contenido de Power BI en una aplicación para su organización](embed-sample-for-your-organization.md).

Al usar la inserción para los usuarios de Power BI, las funcionalidades de autoservicio (como son editar, guardar y otras) están disponibles a través de la [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript).

Puede pasar por el [herramienta programa de instalación de incrustación](https://aka.ms/embedsetup/UserOwnsData) para empezar a trabajar y descargar una aplicación de ejemplo que le guiará a través de la integración de un informe para su organización.

## <a name="embedding-for-your-customers"></a>Inserción de contenido para los clientes

**Inserción de contenido para sus clientes** le permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Esta inserción es también conocida como *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) es un **Microsoft Azure** servicio que permite a los proveedores de software independientes (ISV) y desarrolladores rápidamente insertar objetos visuales, informes y paneles en una aplicación. Esta inserción se realiza a través de un modelo de uso medido por hora, según la capacidad.

![Flujo de inserción para insertar contenido para los clientes](media/embedding/powerbi-embed-flow.png)

Power BI Embedded ofrece ventajas para los ISV, los desarrolladores y los clientes. Por ejemplo, un ISV puede empezar creando objetos visuales con Power BI Desktop de forma gratuita. Ya que minimiza los esfuerzos de desarrollo visual de análisis, los ISV lograr acceso más rápido al mercado y distinguirlo de competidores con experiencias de datos diferenciadoras. ISV también pueden elegir para cobrar una prima por el valor adicional que se crean con análisis insertados.

Con Power BI Embedded, los clientes no necesitan saber nada sobre Power BI. Puede usar dos métodos diferentes para crear una aplicación insertada:
- Cuenta de Power BI Pro 
- Entidad de servicio 

La cuenta de Power BI Pro actúa como la cuenta maestra de la aplicación (Considérela una cuenta de proxy). Esta cuenta le permite generar tokens de inserción que proporcionan acceso a los paneles de Power BI e informes de la aplicación.

La [entidad de servicio](embed-service-principal.md) puede insertar contenido de Power BI en una aplicación mediante un token **de solo aplicación**. También permite generar tokens de inserción que proporcionan acceso a los paneles de Power BI e informes de la aplicación.

Los desarrolladores que usan Power BI Embedded pueden dedicar tiempo sobre la creación funcionalidad principal en de la aplicación lugar de gasto tiempo a desarrollar objetos visuales y análisis. Puede satisfacer las exigencias de informes y paneles del cliente e insertarlos fácilmente con el SDK y API totalmente documentadas rápidamente. Al habilitar en sus aplicaciones la exploración de datos de navegación fácil, los ISV permiten a los clientes tomar decisiones rápidas y fundamentadas de conformidad con los datos, en contexto en cualquier dispositivo.

> [!IMPORTANT]
> Al incrustar requiere el servicio Power BI, los clientes no es necesario tener una cuenta de Power BI para ver el contenido insertado de la aplicación. 

Cuando esté listo para pasar a producción, se debe asignar una capacidad dedicada a su área de trabajo. Power BI Embedded de Microsoft Azure ofrece [capacidades dedicadas](azure-pbie-create-capacity.md) para usarlas con las aplicaciones.

Para insertar los detalles, consulte [cómo insertar contenido de Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Pasos siguientes

Ahora puede intentar insertar contenido de Power BI en una aplicación o intentar insertar el contenido de Power BI para los clientes.

> [!div class="nextstepaction"]
> [Insertar para la organización](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [¿Qué es Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
