---
title: ¿Qué pueden hacer los desarrolladores con Power BI?
description: Power BI ofrece una amplia gama de opciones para los desarrolladores. Desde inserción, pasando por objetos visuales personalizados y hasta conjuntos de datos de transmisión.
author: markingmyname
ms.author: maghan
ms.date: 05/25/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 07fb8d365a6fe4a874b057a71a90a99fc8a9e5fa
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34564705"
---
# <a name="what-can-developers-do-with-power-bi"></a>¿Qué pueden hacer los desarrolladores con Power BI?

Los desarrolladores tienen distintas opciones para tratar de incluir contenido de Power BI en las aplicaciones. Estas opciones incluyen **inserciones con Power BI**, **objetos visuales personalizados** e **inserciones de datos en Power BI**.

## <a name="embedding"></a>Inserción
El servicio Power BI (SaaS) y el servicio Power BI Embedded en Azure (PaaS) tienen las API para insertar los paneles e informes. Esto significa que dispondrá de un conjunto de funcionalidades y acceso a las últimas características de Power BI (como paneles, puertas de enlace y áreas de trabajo de la aplicación) para insertar el contenido.

Puede seguir los pasos de la [herramienta para incorporar la inserción](https://aka.ms/embedsetup) para empezar a trabajar rápidamente y descargar una aplicación de ejemplo.

Elija la solución que más le convenga:
* La [inserción para los clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Ejecute la solución de [inserción para los clientes](https://aka.ms/embedsetup/AppOwnsData).
* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Ejecute la solución de [inserción para la organización](https://aka.ms/embedsetup/UserOwnsData).

![Ejemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="develop-custom-visuals"></a>Desarrollo de objetos visuales personalizados
Los objetos visuales personalizados le permiten crear sus propios objetos visuales para su uso en informes de Power BI. Los objetos visuales personalizados se escriben con TypeScript, que es un superconjunto de JavaScript. TypeScript es compatible con algunas características avanzadas y un acceso anticipado a la funcionalidad de ES6/ES7. La aplicación de estilos de objeto visual se administra mediante hojas de estilo en cascada (css). Para su comodidad, usamos el precompilador Less, que admite algunas características avanzadas (por ejemplo, el anidamiento, variables, condiciones, bucles, etc.). Si no quiere usar ninguna de estas características, puede escribir css plano en el archivo de Less.

![Ejemplo de CV](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Insertar datos en Power BI
Puede usar la API de Power BI para insertar datos en un conjunto de datos. Esto le permite agregar una fila a una tabla dentro de un conjunto de datos. Luego, los nuevos datos se pueden reflejar en iconos en un panel y dentro de los objetos visuales de su informe.

![Ejemplo de inserción de datos](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Pasos siguientes
[Inserción con Power BI](embedding.md)  
[Publicación de objetos visuales personalizados en la Tienda Office](office-store.md)  
[Insertar datos en un panel](walkthrough-push-data.md)
