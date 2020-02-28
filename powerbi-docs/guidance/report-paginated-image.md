---
title: Instrucciones de uso de imágenes para informes paginados
description: Instrucciones para usar imágenes en informes paginados de Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 09fd2197cca31e083c0242b187d7e242244235eb
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530381"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Instrucciones de uso de imágenes para informes paginados

Este artículo está dirigido a los autores de informes que diseñan [informes paginados](../paginated-reports-report-builder-power-bi.md) de Power BI. Proporciona sugerencias para trabajar con imágenes. Normalmente, las imágenes de los diseños de informes pueden mostrar un gráfico como un logotipo de empresa o ilustraciones.

Las imágenes se pueden almacenar en tres ubicaciones diferentes:

- Dentro del informe (insertadas)
- En un servidor web
- En una base de datos, que se puede recuperar mediante un conjunto de datos

Después, se pueden usar en distintos escenarios en los diseños de informe:

- Logotipo de posición libre o imagen
- Imágenes asociadas a filas de datos
- Fondo de elementos de informe concretos:
  - Cuerpo del informe
  - Cuadro de texto
  - Rectángulo
  - Región de datos Tablix (tabla, matriz o lista)

## <a name="suggestions"></a>Sugerencias

Tenga en cuenta las sugerencias siguientes para ofrecer diseños de informes profesionales, facilitar el mantenimiento y optimizar el rendimiento de los informes:

- **Use el menor tamaño posible**: se recomienda preparar imágenes con un tamaño pequeño pero con un aspecto nítido. Es un equilibrio entre la calidad y el tamaño. Considere la posibilidad de usar un editor de gráficos (como MS Paint) para reducir el tamaño del archivo de imagen.
- **Evite imágenes insertadas**: en primer lugar, las imágenes insertadas pueden sobrecargar el tamaño del archivo de informe, lo que puede contribuir a que se represente más lentamente. En segundo lugar, las imágenes insertadas pueden convertirse rápidamente en una pesadilla de mantenimiento si tiene que actualizar muchas imágenes de informe (como podría ser si cambia el logotipo de la empresa).
- **Use almacenamiento en servidor web**: almacenar imágenes en un servidor web es una buena opción, especialmente para el logotipo de la empresa, que se puede obtener del sitio web de la empresa. Pero tenga cuidado si los usuarios del informe van a acceder a los informes fuera de la red. En este caso, asegúrese de que las imágenes estén disponibles a través de Internet.

    Cuando las imágenes están relacionadas con los datos (como las de los vendedores), asigne un nombre a los archivos de imagen para que una expresión de informe pueda generar dinámicamente la ruta de la dirección URL de la imagen. Por ejemplo, puede asignar un nombre a las imágenes de los vendedores con el número de empleado de cada uno. Si el conjunto de datos del informe recupera el número de empleado, puede escribir una expresión para generar la ruta de acceso completa de la dirección URL de la imagen.
- **Use almacenamiento de base de datos**: cuando una base de datos relacional almacena datos de imagen, tiene sentido obtener los datos de imagen directamente de las tablas de la base de datos, especialmente cuando las imágenes no son demasiado grandes.
- **Imágenes de fondo adecuadas**: si decide usar imágenes de fondo, procure no distraer al usuario del informe de los datos del informe. 

    Además, asegúrese de usar _imágenes con estilo de marca de agua_. Por lo general, las imágenes con estilo de marca de agua tienen un fondo transparente (o el mismo color de fondo que usa el informe). También usan colores tenues. Algunos ejemplos comunes de imágenes con estilo de marca de agua son el logotipo de la empresa o las etiquetas de confidencialidad, como "Borrador" o "Confidencial".

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [¿Qué son los informes paginados en Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)
