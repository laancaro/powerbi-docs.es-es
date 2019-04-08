---
title: ¿Qué puedo hacer con la API de Power BI?
description: ¿Qué puedo hacer con la API de Power BI?
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 03/25/2019
ms.openlocfilehash: 443aa370ebb4122d0f979f60726ba953ce13195d
ms.sourcegitcommit: 3a05f34dbeabac62ea8c35c12a045284271971bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872579"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>¿Qué pueden hacer los desarrolladores con la API de Power BI?

Con la API REST de Power BI, puede crear aplicaciones que integren informes, paneles e iconos de Power BI.

Con la API REST de Power BI, se pueden realizar tareas de administración de objetos de Power BI tales como informes, conjuntos de datos y áreas de trabajo.

A continuación se indican algunas de las cosas que puede hacer con las API de Power BI.

| **Para obtener más información** | **Consulte esta información** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Sobre cómo insertar informes, paneles e iconos para usuarios de Power BI y otros que no lo usen. | [Procedimiento para insertar paneles, informes e iconos de Power BI ](embedding-content.md) |
| Realice tareas de administración en objetos de Power BI. | [Referencia de la API de REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/) |
| Ampliar un flujo de trabajo de empresa existente para insertar datos clave en un panel de Power BI. | [Insertar datos en un panel ](walkthrough-push-data.md) |
| Autenticación en Power BI. | [Autenticación en Power BI ](get-azuread-access-token.md) |

> [!NOTE]
> Las API de Power BI siguen haciendo referencia a las áreas de trabajo de la aplicación como grupos. Todas las referencias a grupos significan que está trabajando con áreas de trabajo de la aplicación.

## <a name="api-developer-tools"></a>Herramientas de desarrollo de interfaces de programación de aplicaciones (API)

| Herramientas | Descripción |  |  |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| [Área de juegos](https://microsoft.github.io/PowerBI-JavaScript/demo) | Descubra un ejemplo completo del uso de las API de JavaScript para Power BI. Esta herramienta es también una forma rápida de reproducir diferentes tipos de ejemplos de Power BI Embedded. |  |  |
| [Wiki de JavaScript para Power BI](https://github.com/Microsoft/powerbi-javascript/wiki) | Para obtener más información sobre las API de JavaScript para Power BI. |  |  |
| [Postman](https://www.getpostman.com/) | Ejecute solicitudes, pruebe, depure, supervise, realice pruebas automatizadas y mucho más. |

## <a name="push-data-into-power-bi"></a>Insertar datos en Power BI

Puede usar la API de Power BI para [insertar datos en un conjunto de datos](walkthrough-push-data.md). Esta característica le permite agregar una fila a una tabla dentro de un conjunto de datos. Los nuevos datos se reflejan luego en iconos en un panel y en los objetos visuales dentro de su informe.

![Ejemplo de inserción de datos](media/what-can-you-do/powerbi-push-data.png)

## <a name="github-repositories"></a>Repositorios de GitHub

* [Ejemplos de desarrolladores de Power BI](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [SDK para .NET](https://github.com/Microsoft/PowerBI-CSharp)
* [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)

## <a name="next-steps"></a>Pasos siguientes

* [Inserción de datos en un conjunto de datos](walkthrough-push-data.md)
* [Desarrollo de objetos visuales personalizados de Power BI](custom-visual-develop-tutorial.md)
* [Referencia de la API de REST de Power BI](rest-api-reference.md)
* [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
