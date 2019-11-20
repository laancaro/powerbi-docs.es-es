---
title: Enlace dinámico
description: Aprenda a insertar un informe mediante el enlace dinámico.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8110023de4df28f65129bd53203cec9752acc1af
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73864443"
---
# <a name="dynamic-binding"></a>Enlace dinámico

El enlace dinámico permite seleccionar dinámicamente un conjunto de datos mientras se inserta un informe. No es preciso que el informe y el conjunto de datos se encuentren en la misma área de trabajo. Los usuarios finales ven resultados diferentes en función del conjunto de datos seleccionado.

Las dos áreas de trabajo (la que contienen el informe y la que contiene el conjuntos de datos) deben asignarse a una capacidad.

La inserción de un informe mediante el enlace dinámico tiene dos fases:
1. Generación de un token
2. Ajuste del objeto de configuración

## <a name="generating-a-token"></a>Generación de un token
Para generar un token, use la [API para generar un token de inserción para varios elementos](embed-sample-for-customers.md#multiEmbedToken).

El enlace dinámico se admite en los dos escenarios de inserción: *Inserción de contenido para la organización* e *Inserción de contenido para los clientes*.

| Solución                   | Token                               | Requisitos                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Inserción de contenido para la organización* | Token de acceso para usuarios de Power BI     | Se usa el usuario que es el token de Azure AD, debe tener los permisos adecuados para todos los artefactos.                                                                    |
| *Inserción de contenido para los clientes*    | Token de acceso para usuarios que no usen Power BI | Se deben incluir permisos tanto para el informe como para el conjunto de datos enlazado dinámicamente. Use la nueva API para generar un token de inserción que admita varios artefactos. |

## <a name="adjusting-the-config-object"></a>Ajuste del objeto de configuración
Agregue `datasetBinding` al objeto de configuración. Use el ejemplo de la parte inferior de la página como referencia.

Si es la primera vez que inserta en Power BI, consulte estos tutoriales para aprender a insertar el contenido de Power BI:
* [Inserción del contenido de Power BI en una aplicación para los clientes](embed-sample-for-customers.md)
* [Tutorial: Inserción del contenido de Power BI en una aplicación para la organización](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Ejemplo
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```