---
title: Introducción a los conjuntos de datos de áreas de trabajo (versión preliminar)
description: Obtenga información sobre cómo se puede compartir un conjunto de datos con usuarios en toda la organización. Después, podrán crear informes basados en el conjunto de datos en sus propias áreas de trabajo.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d30a8012161934ada4ff3cb2ce6852fe62f48892
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "73877195"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Introducción a los conjuntos de datos de áreas de trabajo (versión preliminar)

La inteligencia empresarial es una actividad de colaboración. Es importante establecer conjuntos de datos estandarizados que puedan ser el "único origen de la verdad". La detección y reutilización de esos conjuntos de datos estandarizados es fundamental. Cuando los expertos en modelos de datos de la organización crean y comparten conjuntos de datos optimizados, los creadores de informes pueden comenzar con esos conjuntos de datos para generar informes precisos. Después, la organización contará con datos coherentes para tomar decisiones, y una cultura de datos en buen estado.

![Selección de un conjunto de datos compartido](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

En Power BI, los creadores de conjuntos de datos pueden controlar quién tiene acceso a los datos mediante el [permiso de compilación](service-datasets-build-permissions.md). Los creadores de conjuntos de datos también pueden *certificar* o *promover* conjuntos de datos para que otros usuarios los puedan detectar. De ese modo, los autores de informes saben qué conjuntos de datos son de alta calidad y oficiales, y pueden usar estos conjuntos de datos siempre que se creen en Power BI. Los administradores de inquilinos tienen una nueva configuración de inquilino para [controlar el uso de los conjuntos de datos entre áreas de trabajo](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Uso compartido de conjuntos de datos y la nueva experiencia de área de trabajo

La creación de informes basados en conjuntos de datos de diferentes áreas de trabajo y la copia de informes a otras áreas de trabajo están vinculadas estrechamente con la [nueva experiencia de área de trabajo](service-create-the-new-workspaces.md):

- En el servicio, cuando se abre el catálogo de conjunto de datos desde una nueva experiencia de área de trabajo, se muestran los conjuntos de datos en Mi área de trabajo y en áreas de trabajo de la nueva experiencia de área de trabajo. 
- Cuando se abre el catálogo de conjunto de datos desde un área de trabajo clásica, solo se ven los conjuntos de datos de esa área de trabajo, no de otras.
- En Power BI Desktop, puede publicar informes de Live Connect en otras áreas de trabajo, siempre y cuando sus conjuntos de datos estén en la nueva experiencia de áreas de trabajo.
- Al copiar informes entre áreas de trabajo, el área de trabajo de destino debe ser un área de trabajo de la nueva experiencia.

## <a name="discover-datasets-preview"></a>Detección de conjuntos de datos (versión preliminar)

Cuando se compila un informe a partir de un conjunto de datos existente, el primer paso es conectarse al conjunto de datos, ya sea en el servicio Power BI o en Power BI Desktop. Más información sobre [detección de conjuntos de datos de diferentes áreas de trabajo (versión preliminar)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copia de un informe

Cuando encuentre un informe que le guste en un área de trabajo o una aplicación, puede realizar una copia y después modificarlo para ajustarlo a sus necesidades. No tiene que preocuparse de crear el modelo de datos. Ya se ha creado de forma automática. Y resulta mucho más fácil modificar un informe existente que empezar desde cero. Más información sobre la [copia de informes](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Permiso de compilación para conjuntos de datos

Con el tipo de permiso de compilación, si es creador de un conjunto de datos, puede determinar qué usuarios de la organización pueden compilar contenido nuevo en los conjuntos de datos. Los usuarios con permiso de compilación también pueden compilar contenido en el conjunto de datos fuera de Power BI, como hojas de Excel a través de Analizar en Excel, XMLA y Exportar. Obtenga más información sobre el [permiso de compilación](service-datasets-build-permissions.md).

## <a name="promotion-and-certification"></a>Promoción y certificación

Si crea conjuntos de datos, al crear uno del que otros usuarios se puedan beneficiar, puede facilitar su detección si [promociona el conjunto de datos](service-datasets-promote.md). También puede solicitar que los expertos de la organización [certifiquen el conjunto de datos](service-datasets-certify.md).

## <a name="licensing"></a>Licencias

Las características y experiencias específicas basadas en funciones de conjuntos de datos compartidos tienen licencias acordes a sus escenarios existentes. Por ejemplo:

- En general, la detección y conexión a conjuntos de datos compartidos está disponible para todos los usuarios, no es una característica limitada solo a la versión Premium.
- Los usuarios sin licencia Pro solo pueden usar conjuntos de datos en las áreas de trabajo para la creación de informes si esos conjuntos de datos residen en el área de trabajo personal de los usuarios o en un área de trabajo con respaldo Premium. Se aplica la misma restricción de licencia a la creación de informes en Power BI Desktop y en el servicio Power BI.
- Para copiar informes entre áreas de trabajo se necesita una licencia Pro.
- Para copiar informes desde una aplicación se requiere una licencia Pro, como para los paquetes de contenido de la organización.
- La promoción y certificación de conjuntos de datos requiere una licencia Pro.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

- Como publicador de la aplicación, tiene que asegurarse de que la audiencia tenga acceso a los conjunto de datos fuera del área de trabajo. De lo contrario, los usuarios experimentarán problemas al interactuar con la aplicación: los informes no se abrirán sin acceso al conjunto de datos y los iconos del panel aparecerán bloqueados. Además, los usuarios no podrán abrir la aplicación si el primer elemento de su navegación es un informe sin acceso al conjunto de elementos.
- Para crear un informe sobre un conjunto de datos en otra área de trabajo se requiere la nueva experiencia de área de trabajo en ambos extremos: El informe y el conjunto de datos deben estar en una nueva experiencia de área de trabajo.
- En un área de trabajo clásica, la experiencia de detección de conjunto de datos solo muestra los conjuntos de datos de esa área de trabajo.
- De manera predeterminada, "Publicar en la web" no funciona para un informe basado en un conjunto de datos compartido.
- Si dos usuarios son miembros de un área de trabajo que accede a un conjunto de datos compartido, es posible que solo uno de ellos pueda ver el conjunto de datos relacionado en el área de trabajo. Solo los usuarios que tengan al menos acceso de lectura al conjunto de datos podrán ver el conjunto de datos compartido. 

## <a name="next-steps"></a>Pasos siguientes

- [Promoción de los conjuntos de datos](service-datasets-promote.md)
- [Certificación de los conjuntos de datos](service-datasets-certify.md)
- [Control del uso de conjuntos de datos entre áreas de trabajo](service-datasets-admin-across-workspaces.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
