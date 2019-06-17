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
ms.openlocfilehash: 8154370a78f418148381c201ba0c2bd50d8ae021
ms.sourcegitcommit: 24781cdab5fbe43fc14248db636169cc54ef6721
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66497910"
---
# <a name="embedded-analytics-with-power-bi"></a>Análisis integrado con Power BI

El servicio Power BI (SaaS) y el servicio Power BI Embedded en Azure (PaaS) tienen las API para insertar los paneles e informes. Cuando se inserta el contenido, se puede acceder a las últimas características de Power BI, tales como paneles, puertas de enlace y áreas de trabajo de la aplicación.

Puede ver la [herramienta de configuración de inserción](https://aka.ms/embedsetup) para empezar rápidamente y descargar una aplicación de ejemplo.

Elija la solución que más le convenga:

* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Para ello, implemente la solución de [inserción para la organización](https://aka.ms/embedsetup/UserOwnsData).
* La [inserción de contenido para los clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes a los usuarios que no tienen una cuenta de Power BI. Para ello, implemente la solución de [inserción para los clientes](https://aka.ms/embedsetup/AppOwnsData).

![Ejemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Uso de las API

Hay dos escenarios principales para insertar el contenido de Power BI:
- Inserción de contenido para los usuarios de la organización (que tienen licencias de Power BI). 
 
- Inserción de contenido para los usuarios y clientes sin necesidad de licencias de Power BI. 

La [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/) permite ambos escenarios.

En el caso de clientes y usuarios que no tengan licencia de Power BI, puede insertar paneles e informes en la aplicación personalizada con las mismas API, tanto para la organización como para los clientes. Los clientes verán los datos que la aplicación administre. Además, los usuarios de Power BI de la organización tienen opciones adicionales para ver *sus datos* directamente en Power BI o en el contexto de la aplicación insertada. Puede aprovechar al máximo las API de REST y de JavaScript para lo que necesite insertar.

Para entender cómo funciona la inserción, consulte el [Ejemplo de inserción de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserción de contenido para la organización

La **inserción para la organización** permite ampliar el servicio Power BI. Este tipo de inserción requiere que los usuarios de la aplicación inicien sesión en el servicio Power BI para ver el contenido. Cuando los usuarios de la organización inician sesión, solo tienen acceso a los paneles e informes de los que sean propietarios o que alguien haya compartido contenido con ellos en el servicio Power BI.

Entre los ejemplos de inserción de contenido se incluyen aplicaciones internas, como [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [Microsoft Teams Integration (se necesitan derechos de administrador)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) y [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Si quiere obtener más información sobre la inserción para la organización, consulte [Tutorial: insertar contenido de Power BI en una aplicación para la organización](embed-sample-for-your-organization.md).

Al usar la inserción para los usuarios de Power BI, las funcionalidades de autoservicio (como son editar, guardar y otras) están disponibles a través de la [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript).

Puede seguir los pasos de la [herramienta de configuración de inserción](https://aka.ms/embedsetup/UserOwnsData) para empezar y descargar una aplicación de ejemplo que le guiará por los pasos necesarios para integrar un informe para la organización.

## <a name="embedding-for-your-customers"></a>Inserción de contenido para los clientes

La **inserción de contenido para los clientes** permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Este tipo de inserción de contenido también se conoce como *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) es un servicio de **Microsoft Azure** que permite que los desarrolladores y proveedores de software independientes (ISV) inserten objetos visuales, informes y paneles con gran rapidez en una aplicación. Esta inserción se realiza a través de un modelo de medición por horas basado en la capacidad.

![Flujo de inserción para insertar contenido para los clientes](media/embedding/powerbi-embed-flow.png)

Power BI Embedded ofrece ventajas para los ISV, los desarrolladores y los clientes. Por ejemplo, un ISV puede empezar creando objetos visuales con Power BI Desktop de forma gratuita. Los ISV pueden minimizar el esfuerzo dedicado al desarrollo de análisis visuales y, de este modo, reducir los tiempos de creación y comercialización para destacar entre la competencia con experiencias de datos diferenciadoras. Asimismo, los ISV también pueden elegir cobrar un cargo suplementario por el valor adicional creado gracias a los análisis insertados.

Con Power BI Embedded, los clientes no necesitan saber nada sobre Power BI. Se pueden usar dos métodos diferentes para crear una aplicación insertada:
- Cuenta de Power BI Pro 
- Entidad de servicio 

La cuenta de Power BI Pro actuará como la cuenta maestra de la aplicación (considérela como una cuenta de proxy). Esta cuenta permite generar tokens de inserción que proporcionan acceso a los paneles e informes del servicio Power BI.

La [entidad de servicio](embed-service-principal.md) puede insertar contenido de Power BI en una aplicación mediante un token **de solo aplicación**. También permite generar tokens de inserción que proporcionan acceso a los paneles e informes del servicio Power BI.

Con Power BI Embedded, los desarrolladores pueden centrarse en la compilación de las funciones básicas de su aplicación, en lugar de en el desarrollo de los objetos visuales y los análisis. Pueden satisfacer rápidamente las necesidades de los clientes en materia de informes y paneles, así como integrarlos fácilmente con las API y SDK, ambas con su documentación correspondiente. Al habilitar en sus aplicaciones la exploración de datos de navegación fácil, los ISV permiten a los clientes tomar decisiones rápidas y fundamentadas de conformidad con los datos, en contexto en cualquier dispositivo.

> [!IMPORTANT]
> Mientras que la inserción requiere el servicio Power BI, los clientes no necesitan tener una cuenta de Power BI para ver el contenido insertado de la aplicación. 

Cuando esté listo para pasar a producción, se debe asignar una capacidad dedicada a su área de trabajo. Power BI Embedded de Microsoft Azure ofrece [capacidades dedicadas](azure-pbie-create-capacity.md) para usarlas con las aplicaciones.

Para obtener más información sobre la inserción, consulte [Como insertar contenido de Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Pasos siguientes

Ahora puede intentar insertar contenido de Power BI en una aplicación o intentar insertar el contenido de Power BI para los clientes.

> [!div class="nextstepaction"]
> [Insertar para la organización](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [¿Qué es Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
