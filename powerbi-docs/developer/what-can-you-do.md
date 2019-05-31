---
title: ¿Qué pueden hacer los desarrolladores con Power BI?
description: Power BI ofrece una amplia gama de opciones para los desarrolladores. Desde inserción, pasando por objetos visuales personalizados y hasta conjuntos de datos de transmisión.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 03/15/2019
ms.openlocfilehash: d2e3ba69cde609638e54eaa1206714f0fb420d18
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61262721"
---
# <a name="what-can-developers-do-with-power-bi"></a>¿Qué pueden hacer los desarrolladores con Power BI?

Los desarrolladores tienen distintas opciones para tratar de incluir contenido de Power BI en las aplicaciones. Como desarrollador, estas opciones incluyen **inserciones con Power BI**, **objetos visuales personalizados** e **inserciones de datos en Power BI**.

## <a name="embedding-power-bi-content"></a>Inserción de contenido de Power BI

El servicio Power BI (SaaS) y el servicio Power BI Embedded en Azure (PaaS) tienen las API para insertar los paneles e informes. Con esta característica puede acceder a las características de Power BI más actualizadas (como paneles, puertas de enlace y áreas de trabajo de la aplicación) para insertar el contenido.

Puede ver la [herramienta de configuración de inserción](https://aka.ms/embedsetup) para empezar rápidamente y descargar una aplicación de ejemplo.

Elija la solución que más le convenga:

* La [inserción para los clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Ejecute la solución de [inserción para los clientes](https://aka.ms/embedsetup/AppOwnsData).

* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Ejecute la solución de [inserción para la organización](https://aka.ms/embedsetup/UserOwnsData).

![Ejemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

Para más información sobre la inserción con Power BI, vea [Inserción con Power BI](embedding.md).

## <a name="developing-custom-visuals"></a>Desarrollar objetos visuales personalizados

Puede usar objetos visuales personalizados con Power BI para crear un único tipo de objeto visual adaptado a sus necesidades o a las de su empresa. A menudo son los desarrolladores los que crean estos objetos visuales personalizados. Se crean cuando la gran cantidad de objetos visuales que se incluyen con Power BI no se ajustan a sus necesidades.

Con los objetos visuales personalizados puede crear sus propios objetos visuales para usarlos en informes de Power BI. Los objetos visuales personalizados se escriben con TypeScript, que es un superconjunto de JavaScript. TypeScript es compatible con algunas características avanzadas y un acceso anticipado a la funcionalidad de ES6/ES7. La aplicación de estilos de objeto visual se administra mediante hojas de estilo en cascada (CSS). Para su comodidad, usamos el precompilador Less, que admite algunas características avanzadas (por ejemplo, el anidamiento, variables, condiciones, bucles, entre otras). Si no quiere usar ninguna de estas características, puede escribir CSS plano en el archivo de Less.

![Ejemplo de CV](media/what-can-you-do/powerbi-custom-visual-store.png)

Para saber más sobre el desarrollo visual personalizado, vea [Desarrollo de objetos visuales personalizados de Power BI](custom-visual-develop-tutorial.md).

## <a name="using-api-automation"></a>Uso de automatización de la API

Power BI muestra los paneles que son interactivos y se pueden crear y actualizar desde muchos orígenes de datos diferentes en tiempo real. Con cualquier lenguaje de programación que admita llamadas de REST, puede crear aplicaciones que se integren con un panel de Power BI en tiempo real. También puede integrar informes e iconos de Power BI en las aplicaciones.

Los desarrolladores también pueden crear sus propias visualizaciones de datos para que estas puedan usarse en informes y paneles interactivos.

![Ejemplo de inserción de datos](media/what-can-you-do/powerbi-push-data.png)

Para ver algunas de las cosas que se pueden hacer con la API de Power BI, eche un vistazo a [¿Qué pueden hacer los desarrolladores con la API de Power BI?](overview-of-power-bi-rest-api.md)

## <a name="next-steps"></a>Pasos siguientes

[Inserción con Power BI](embedding.md)  

[Desarrollo de objetos visuales personalizados de Power BI](https://microsoft.github.io/PowerBI-visuals/docs/step-by-step-lab/developing-a-power-bi-custom-visual/)

[¿Qué pueden hacer los desarrolladores con la API de Power BI?](overview-of-power-bi-rest-api.md)

[Centro para desarrolladores de Power BI](https://powerbi.microsoft.com/developers/)