---
title: Inserción con Power BI
description: Power BI ofrece API para la inserción de paneles e informes en las aplicaciones.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 2e899593cbe3453381dd2d3457cec97467aec4d6
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34561756"
---
# <a name="embedding-with-power-bi"></a>Inserción con Power BI
Power BI ofrece API para la inserción de paneles e informes en las aplicaciones. Al insertar el contenido, las API de Power BI ofrecen un conjunto coherente de funcionalidades y acceso a las últimas características de Power BI (como paneles, puertas de enlace y áreas de trabajo de la aplicación).

## <a name="a-single-api"></a>Una sola API
Hay dos escenarios principales al insertar el contenido de Power BI.  Inserción de contenido para usuarios de la organización (con licencia de Power BI) e inserción de contenido para usuarios y clientes sin que necesiten licencia de Power BI. La API de REST de Power BI permite ambos escenarios. 

En el caso de clientes y usuarios que no tengan licencia de Power BI, puede insertar paneles e informes en la aplicación personalizada con las mismas API, tanto para la organización como para los clientes. Los clientes verán los datos que la aplicación administre. Y, en el caso de los usuarios de Power BI de su organización, tendrán la opción tradicional de ver *sus propios datos* directamente en Power BI o en el contexto de la aplicación insertada. Puede aprovechar al máximo las API de REST y de JavaScript para lo que necesite insertar.

Para ver un ejemplo de cómo funciona la inserción, consulte [Ejemplo de inserción de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserción de contenido para la organización
La inserción de contenido para la organización le permite ampliar el servicio Power BI. Cuando los usuarios quieran ver el contenido, deberán iniciar sesión en el servicio Power BI. Cuando los usuarios de la organización inicien sesión, solo tendrán acceso a los paneles e informes que se hayan compartido con ellos en el servicio Power BI. 

*Entre los ejemplos de inserción de contenido para la organización se incluye la inserción de aplicaciones web internas, elementos web de SharePoint Online y las integraciones de Microsoft Teams.*

Para insertar contenido para su organización, consulte lo siguiente:

* [Integrar un informe en una aplicación](integrate-report.md)
* [Integrar un panel en una aplicación](integrate-dashboard.md)
* [Integrar un icono en una aplicación](integrate-tile.md)

Al usar la inserción para los usuarios de Power BI, las funcionalidades de autoservicio (como son editar, guardar y otras) están disponibles a través de la [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript).

Puede seguir los pasos de [Onboarding experience tool to embed for your organization](https://aka.ms/embedsetup/UserOwnsData) (Herramienta para incorporar la inserción para la organización) para empezar a trabajar rápidamente y descargar una aplicación de ejemplo que le guiará por los pasos para integrar un informe para la organización.

## <a name="embedding-for-your-customers"></a>Inserción de contenido para los clientes
La inserción de contenido para los clientes permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Los clientes no necesitan saber nada acerca de Power BI. Se necesita al menos una cuenta de Power BI Pro para crear una aplicación insertada. Esa cuenta actuará como cuenta maestra de la aplicación. Considérela como una cuenta de proxy. La cuenta de Power BI Pro le permite también generar tokens de inserción que proporcionan acceso a los paneles e informes dentro del servicio Power BI que la aplicación posea o administre. 

*Un ejemplo de inserción para los clientes es una aplicación de ISV que se quiere vender a otras compañías.*

![Flujo de inserción para insertar contenido para los clientes](media/embedding/powerbi-embed-flow.png)

Para insertar paneles, informes e iconos, puede usar las mismas API que se usan para insertar contenido para la organización.

> [!IMPORTANT]
> Aunque la inserción de contenido tiene una dependencia del servicio Power BI, no existe ninguna dependencia de Power BI para los clientes. No es necesario que se registren en Power BI para ver el contenido insertado en la aplicación.
> 

Cuando esté listo para pasar a producción, se debe asignar una capacidad a su área de trabajo de aplicaciones. Power BI Embedded, de Microsoft Azure, ofrece capacidad para usarla con las aplicaciones.

Para más información acerca de los procedimientos de inserción, consulte [Procedimiento para insertar paneles, informes e iconos de Power BI](embedding-content.md).

Puede seguir los pasos de [Onboarding experience tool to embed for your customers](https://aka.ms/embedsetup/AppOwnsData) (Herramienta para incorporar la inserción para los clientes) para empezar a trabajar rápidamente y descargar una aplicación de ejemplo que le guíe por los pasos para integrar un informe en la aplicación.

Si usó el servicio Colección de áreas de trabajo de Power BI en Azure, consulte [Migración de contenido desde el servicio Colección de áreas de trabajo de Power BI](migrate-from-powerbi-embedded.md) para más información sobre cómo migrar el contenido.

## <a name="next-steps"></a>Pasos siguientes
[Procedimiento para insertar paneles, informes e iconos de Power BI](embedding-content.md)  
[Migración de contenido de la colección de áreas de trabajo de Power BI Embedded a Power BI](migrate-from-powerbi-embedded.md)  
[¿Qué es Power BI Premium?](../service-premium.md)  
[Repositorio Git de la API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositorio Git de C# de Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Ejemplo de inserción de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Notas del producto sobre el planeamiento de la capacidad de análisis de inserción](https://aka.ms/pbiewhitepaper)  
[Notas del producto de Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

