---
title: 'Uso de conjuntos de datos entre áreas de trabajo (versión preliminar): Power BI'
description: Obtenga información sobre cómo se puede compartir un conjunto de datos con usuarios en toda la organización. Después, podrán crear informes basados en el conjunto de datos en sus propias áreas de trabajo.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a5e4b41b36dfbf6cca14a348268b96eaad21b00e
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461865"
---
# <a name="use-datasets-across-workspaces-preview"></a>Uso de conjuntos de datos entre áreas de trabajo (versión preliminar)

La inteligencia empresarial es una actividad de colaboración. Es importante establecer conjuntos de datos estandarizados que puedan ser el "único origen de la verdad". La detección y reutilización de esos conjuntos de datos estandarizados es fundamental. Cuando los expertos en modelos de datos de la organización crean y comparten conjuntos de datos optimizados, los creadores de informes pueden comenzar con esos conjuntos de datos para generar informes precisos. Después, la organización contará con datos coherentes para tomar decisiones, y una cultura de datos en buen estado.

Power BI hace que para los creadores de conjuntos de datos sea más fácil certificarlos o promocionarlos para que otros usuarios los puedan detectar. Después, los autores de informes encuentran conjuntos de datos oficiales de calidad que pueden usar en cualquier parte de Power BI. Los propietarios de conjuntos de datos pueden mantener el control de quién tiene acceso a los datos mediante el [permiso de compilación](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Los administradores de inquilinos tienen una nueva configuración de inquilino para [controlar el uso de los conjuntos de datos entre áreas de trabajo](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Uso compartido de conjuntos de datos y la nueva experiencia de área de trabajo

La creación de informes basados en conjuntos de datos de diferentes áreas de trabajo y la copia de informes a otras áreas de trabajo están vinculadas estrechamente con la [nueva experiencia de área de trabajo](service-create-the-new-workspaces.md):

- En el servicio, cuando se abre el catálogo de conjunto de datos desde una nueva experiencia de área de trabajo, se muestran los conjuntos de datos en Mi área de trabajo y en áreas de trabajo de la nueva experiencia de área de trabajo. 
- Cuando se abre el catálogo de conjunto de datos desde un área de trabajo clásica, solo se ven los conjuntos de datos de esa área de trabajo, no de otras.
- En el escritorio, puede publicar informes de Live Connect en otras áreas de trabajo, siempre y cuando sus conjuntos de datos estén en la nueva experiencia de áreas de trabajo.
- Al copiar informes entre áreas de trabajo, el área de trabajo de destino debe ser un área de trabajo de la nueva experiencia.

## <a name="build-permission-for-datasets"></a>Permiso de compilación para conjuntos de datos

Con el tipo de permiso de compilación, puede permitir que otros usuarios de la organización creen contenido, como informes, paneles e iconos anclados de Preguntas y respuestas, en un conjunto de datos existente. También pueden crear contenido en el conjunto de datos fuera de Power BI, como hojas de Excel a través de Analizar en Excel, XMLA y exportar. Obtenga más información sobre el [permiso de compilación](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Detección de conjuntos de datos (versión preliminar)

Cuando se crea un informe sobre un conjunto de datos existente, el primer paso es conectarse al conjunto de datos, en el servicio Power BI o Power BI Desktop. Más información sobre [detección de conjuntos de datos de diferentes áreas de trabajo (versión preliminar)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copia de un informe

Cuando encuentre un informe que le guste en un área de trabajo o una aplicación, puede realizar una copia y después modificarlo para ajustarlo a sus necesidades. No tiene que preocuparse de crear el modelo de datos. Ya se ha creado de forma automática. Y resulta mucho más fácil modificar un informe existente que empezar desde cero. Más información sobre la [copia de informes](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Promoción y certificación

Si crea conjuntos de datos, y crea uno del que otros usuarios se puedan beneficiar, puede facilitar su detección si [promociona el conjunto de datos](service-datasets-promote.md). También puede solicitar que los expertos de la organización [certifiquen el conjunto de datos](service-datasets-certify.md).

## <a name="licensing"></a>Licencias

Las características y experiencias específicas basadas en funciones de conjuntos de datos compartidos tienen licencias acordes a sus escenarios existentes.  Por ejemplo:

- En general, la detección y conexión a conjuntos de datos compartidos está disponible para todos los usuarios. Pero los usuarios sin una licencia Pro solo se pueden conectar a conjuntos de datos que residen en sus áreas de trabajo personales o en áreas de trabajo Premium.
- Para promocionar y certificar conjuntos de datos que se encuentran fuera de las áreas de trabajo personales se necesita una licencia Pro, ya que se necesita una licencia Pro para ser miembro de un área de trabajo de la aplicación.
- Para copiar conjuntos de datos entre áreas de trabajo se necesita una licencia Pro, ya que como antes se necesita una licencia Pro para ser miembro de un área de trabajo de la aplicación.
- Para copiar informes desde una aplicación se requiere una licencia Pro, como para los paquetes de contenido de la organización.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

- Para crear un informe sobre un conjunto de datos en otra área de trabajo se requiere la nueva experiencia de área de trabajo en ambos extremos: El informe y el conjunto de datos deben estar en una nueva experiencia de área de trabajo.
- En un área de trabajo clásica, la experiencia de detección de conjunto de datos solo muestra los conjuntos de datos de esa área de trabajo.
- Puede crear informes en áreas de trabajo de la aplicación basadas en conjuntos de datos de otra área de trabajo. Pero no puede crear una aplicación para un área de trabajo que contenga estos conjuntos de datos.
- Los usuarios de la versión gratuita de Desktop solo verán conjuntos de datos de Mi área de trabajo y de áreas de trabajo basadas en Premium.
- Si quiere agregar un informe basado en un conjunto de datos compartido a una aplicación, tendrá que ser miembro del área de trabajo del conjunto de datos. Se trata de un problema conocido.
- "Publicar en la web" no funciona para un informe basado en un conjunto de datos compartido. Esto es así por diseño.
- Si dos usuarios son miembros de un área de trabajo que accede a un conjunto de datos compartido, es posible que solo uno de ellos pueda ver el conjunto de datos relacionado en el área de trabajo. Solo los usuarios que tengan al menos acceso de lectura al conjunto de datos podrán ver el conjunto de datos compartido. 

## <a name="next-steps"></a>Pasos siguientes

- [Promoción de los conjuntos de datos](service-datasets-promote.md)
- [Certificación de los conjuntos de datos](service-datasets-certify.md)
- [Control del uso de conjuntos de datos entre áreas de trabajo](service-datasets-admin-across-workspaces.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
