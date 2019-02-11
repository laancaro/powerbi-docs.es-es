---
title: Análisis integrado con Power BI
description: Power BI ofrece API para usar análisis integrados con los paneles e informes en las aplicaciones. Aprenda más sobre la inserción con Power BI tanto en entornos PaaS como SaaS mediante software de análisis integrado, herramientas de análisis integrado o herramientas de inteligencia empresarial de análisis integrado.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.custom: seodec18
ms.date: 02/05/2019
ms.openlocfilehash: ca159fb8cea26f4c707aabc99d9fa2c308a32e1a
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762453"
---
# <a name="embedded-analytics-with-power-bi"></a>Análisis integrado con Power BI

El servicio Power BI (SaaS) y el servicio Power BI Embedded en Azure (PaaS) tienen las API para insertar los paneles e informes. Con esta característica dispone de un conjunto de funcionalidades y acceso a las últimas características de Power BI (como paneles, puertas de enlace y áreas de trabajo de la aplicación) al insertar el contenido.

Puede ver la [herramienta de configuración de inserción](https://aka.ms/embedsetup) para empezar rápidamente y descargar una aplicación de ejemplo.

Elija la solución que más le convenga:

* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Ejecute la solución de [inserción para la organización](https://aka.ms/embedsetup/UserOwnsData).
* La [inserción para los clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Ejecute la solución de [inserción para los clientes](https://aka.ms/embedsetup/AppOwnsData).

![Ejemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>Uso de API

Hay dos escenarios principales al insertar el contenido de Power BI. La inserción para usuarios de la organización (con licencias de Power BI) y la inserción para usuarios y clientes sin que necesiten licencias de Power BI. La API de REST de Power BI permite ambos escenarios.

En el caso de clientes y usuarios que no tengan licencia de Power BI, puede insertar paneles e informes en la aplicación personalizada con las mismas API, tanto para la organización como para los clientes. Los clientes verán los datos que la aplicación administre. Además, en el caso de los usuarios de Power BI de la organización, tienen opciones adicionales para ver *sus datos* directamente en Power BI o en el contexto de la aplicación insertada. Puede aprovechar al máximo las API de REST y de JavaScript para lo que necesite insertar.

Para ver un ejemplo de cómo funciona la inserción, consulte [Ejemplo de inserción de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserción de contenido para la organización

La **inserción para la organización** permite ampliar el servicio Power BI. La inserción para la organización requiere que los usuarios de la aplicación que quieran ver el contenido inicien sesión en el servicio Power BI. Cuando los usuarios de la organización inician sesión, solo tienen acceso a los paneles e informes de los que sean propietarios o que alguien haya compartido contenido con ellos en el servicio Power BI.

*Entre los ejemplos de inserción de contenido para la organización se incluye la inserción de aplicaciones internas, como [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), las [integraciones de Microsoft Teams (se necesitan privilegios de administrador)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) y [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).*

Para insertar contenido para su organización, consulte lo siguiente:

* [Integrar un informe en una aplicación](embed-sample-for-your-organization.md)

Al usar la inserción para los usuarios de Power BI, las funcionalidades de autoservicio (como son editar, guardar y otras) están disponibles a través de la [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript).

Puede seguir los pasos de la [herramienta de configuración de inserción](https://aka.ms/embedsetup/UserOwnsData) para realizar inserciones en la organización para empezar a trabajar y descargar una aplicación de ejemplo que le guiará por los pasos para integrar un informe para la organización.

## <a name="embedding-for-your-customers"></a>Inserción de contenido para los clientes

La **inserción de contenido para los clientes** le permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. La inserción de contenido para los clientes también se conoce como **Power BI Embedded**.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) es un servicio de **Microsoft Azure** que permite que los proveedores y desarrolladores de software independientes (ISV) inserten objetos visuales, informes y paneles con gran rapidez en las aplicaciones gracias a un modelo de medición por horas basado en la capacidad.

![Flujo de inserción para insertar contenido para los clientes](media/embedding/powerbi-embed-flow.png)

Power BI Embedded ofrece ventajas para los ISV, los desarrolladores y los clientes. Por ejemplo, un ISV puede empezar creando objetos visuales con Power BI Desktop de forma gratuita. Los ISV pueden acortar el tiempo y el esfuerzo dedicados al desarrollo de análisis visuales y, así, reducir los tiempos de creación y comercialización, y destacar entre la competencia con experiencias de datos diferenciadoras. Asimismo, los ISV también pueden elegir cobrar un cargo suplementario por el valor adicional creado gracias a los análisis insertados.

Con Power BI Embedded, los clientes no necesitan saber nada sobre Power BI. Puede usar dos métodos diferentes para crear una aplicación insertada. Una de las opciones consiste en usar una cuenta de Power BI Pro. La otra opción es usar una entidad de servicio. 

Esa cuenta actuará como cuenta maestra de la aplicación (considérela como una cuenta de proxy). La cuenta de Power BI Pro permite generar tokens de inserción que proporcionan acceso a los paneles e informes dentro del servicio Power BI que la aplicación posee y administra.

La [entidad de servicio](embed-service-principal.md) puede insertar contenido de Power BI en una aplicación mediante un token **de solo aplicación**. La entidad de servicio permite generar tokens de inserción que proporcionan acceso a los paneles e informes dentro del servicio Power BI que la aplicación posee y administra.

Con Power BI Embedded, los desarrolladores pueden centrarse en la creación de las características básicas de su aplicación, en lugar de en el desarrollo de los objetos visuales y los análisis. Además, los desarrolladores pueden satisfacer rápidamente las necesidades de los clientes en materia de informes y paneles, así como integrarlos fácilmente con las API y SDK, ambas con su documentación correspondiente. Al habilitar en sus aplicaciones la exploración de datos de navegación fácil, los ISV permiten a los clientes tomar decisiones rápidas y fundamentadas de conformidad con los datos, en contexto en cualquier dispositivo.

> [!IMPORTANT]
> Aunque la inserción de contenido tiene una dependencia del servicio Power BI, no existe ninguna dependencia de Power BI para los clientes. No es necesario que se registren en Power BI para ver el contenido insertado en la aplicación.

Cuando esté listo para pasar a producción, se debe asignar una capacidad dedicada a su área de trabajo. Power BI Embedded de Microsoft Azure ofrece [capacidades dedicadas](azure-pbie-create-capacity.md) para usarlas con las aplicaciones.

Para obtener más información sobre cómo realizar la inserción, vea [Como insertar contenido de Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Pasos siguientes

Ahora puede intentar insertar contenido de Power BI en una aplicación o intentar insertar el contenido de Power BI para los clientes.

> [!div class="nextstepaction"]
> [Insertar para la organización](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [¿Qué es Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)