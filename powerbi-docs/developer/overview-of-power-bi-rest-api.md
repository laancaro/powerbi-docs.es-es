---
title: ¿Qué puedo hacer con la API de Power BI?
description: ¿Qué puedo hacer con la API de Power BI?
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 84e43f67c78949139ec856ef8ac770555fc6bd96
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282710"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>¿Qué pueden hacer los desarrolladores con la API de Power BI?

Power BI muestra los paneles que son interactivos y se pueden crear y actualizar desde muchos orígenes de datos diferentes en tiempo real. Con cualquier lenguaje de programación que admita llamadas de REST, puede crear aplicaciones que se integren con un panel de Power BI en tiempo real. También puede integrar informes e iconos de Power BI en las aplicaciones.

Los desarrolladores también pueden crear sus propias visualizaciones de datos para que estas puedan usarse en informes y paneles interactivos.

A continuación se indican algunas de las cosas que puede hacer con las API de Power BI.

| **Para hacerlo** | **Vaya aquí** |
| --- | --- |
| Insertar paneles, informes e iconos para usuarios de Power BI y usuarios que no usan Power BI (la aplicación es propietaria de los datos) |[Procedimiento para insertar paneles, informes e iconos de Power BI](embedding-content.md) |
| Ampliar un flujo de trabajo de empresa existente para insertar datos clave en un panel de Power BI. |[Insertar datos en un panel](walkthrough-push-data.md) |
| Autenticación en Power BI. |[Autenticación en Power BI](get-azuread-access-token.md) |
| Crear un objeto visual personalizado. |[Desarrollo de objetos visuales personalizados de Power BI](custom-visual-develop-tutorial.md) |

> [!NOTE]
> Las API de Power BI siguen haciendo referencia a las áreas de trabajo de la aplicación como grupos. Todas las referencias a grupos significan que está trabajando con áreas de trabajo de la aplicación.

## <a name="power-bi-developer-samples"></a>Ejemplos de desarrolladores de Power BI

Entre los ejemplos de desarrolladores de Power BI se incluyen elementos para insertar paneles, informes e iconos.

[Power BI developer samples](https://github.com/Microsoft/PowerBI-Developer-Samples) (Ejemplos de desarrolladores de Power BI)

* Los ejemplos de **App Owns Data** (La aplicación es propietaria de los datos) son para la inserción con usuarios que no usan Power BI.
* Los ejemplos de **User Owns Data** (El usuario es propietario de los datos) son para la inserción con usuarios de Power BI.

## <a name="github-repositories"></a>Repositorios de GitHub

* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)
* [Objetos visuales personalizados](https://github.com/Microsoft/PowerBI-visuals)

## <a name="developer-tools"></a>Herramientas de desarrolladores

Las siguientes son herramientas que puede usar para ayudarle a desarrollar elementos de Power BI.

Puede ver la [herramienta de configuración de inserción](https://aka.ms/embedsetup) para empezar a trabajar rápidamente y descargar una aplicación de ejemplo sobre cómo insertar contenido de Power BI.

Elija la solución que más le convenga:

* La [inserción para los clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Ejecute la solución de [inserción para los clientes](https://aka.ms/embedsetup/AppOwnsData).

* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Ejecute la solución de [inserción para la organización](https://aka.ms/embedsetup/UserOwnsData).

Para obtener un ejemplo completo del uso de la API de JavaScript, puede usar la [herramienta de área de juegos](https://microsoft.github.io/PowerBI-JavaScript/demo). Esta herramienta es una forma rápida de reproducir diferentes tipos de ejemplos de Power BI Embedded. También puede obtener más información sobre la API de JavaScript si consulta la página de la [wiki de PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

## <a name="push-data-into-power-bi"></a>Insertar datos en Power BI

Puede usar la API de Power BI para insertar datos en un conjunto de datos. Esta característica le permite agregar una fila a una tabla dentro de un conjunto de datos. Luego, los nuevos datos se pueden reflejar en iconos en un panel y dentro de los objetos visuales de su informe.

![Ejemplo de inserción de datos](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Pasos siguientes

[Inserción de datos en un conjunto de datos](walkthrough-push-data.md)  
[Desarrollo de objetos visuales personalizados de Power BI](custom-visual-develop-tutorial.md)  
[Referencia de la API de REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
