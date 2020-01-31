---
title: Conexión de un informe a un conjunto de datos mediante el enlace dinámico
description: Obtenga información sobre cómo insertar un informe mediante el enlace dinámico.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: 1f54ce3a6bfd69caa3f386b7684e3df7f725523d
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709532"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Conexión de un informe a un conjunto de datos mediante el enlace dinámico 

Cuando un informe está conectado a un conjunto de datos puede usar el enlace dinámico. La conexión entre el informe y el conjunto de datos se conoce como *enlace*. Cuando se determina el enlace en el momento de la inserción, en lugar de hacerlo con anterioridad, este se conoce como enlace dinámico.

Al insertar un informe de Power BI con el *enlace dinámico*, puede conectar el mismo informe a distintos conjuntos de datos dependiendo de cuáles sean las credenciales del usuario.

Esto significa que puede usar un informe para mostrar información diferente, dependiendo del conjunto de datos al que esté conectado. Por ejemplo, un informe que muestre valores de ventas al por menor puede estar conectado a distintos conjuntos de datos del minorista y producir resultados diferentes dependiendo del conjunto de datos del minorista al que esté conectado.

No es preciso que el informe y el conjunto de datos se encuentren en la misma área de trabajo. Las dos áreas de trabajo (la que contiene el informe y la que contiene el conjuntos de datos) deben asignarse a una [capacidad](azure-pbie-create-capacity.md).

Como parte del proceso de inserción, asegúrese de *generar un token con los permisos suficientes* y *ajustar el objeto de configuración*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Generación de un token con permisos suficientes

El enlace dinámico se admite en los dos escenarios de inserción: *Inserción de contenido para la organización* e *Inserción de contenido para los clientes*. En la tabla siguiente, se describen las consideraciones para cada escenario.

|Escenario  |Propiedad de los datos  |Token  |Requisitos  |
|---------|---------|---------|---------|
|*Inserción de contenido para la organización*    |El usuario posee los datos         |Token de acceso para usuarios de Power BI         |Se usa el usuario que es el token de Azure AD, debe tener los permisos adecuados para todos los artefactos.         |
|*Inserción de contenido para los clientes*     |La aplicación posee los datos         |Token de acceso para usuarios que no usen Power BI         |Se deben incluir permisos tanto para el informe como para el conjunto de datos enlazado dinámicamente. Use la [API para generar un token de inserción para varios elementos](embed-sample-for-customers.md#multiEmbedToken) con el fin de admitir varios artefactos.         |

## <a name="adjusting-the-config-object"></a>Ajuste del objeto de configuración
Agregue `datasetBinding` al objeto de configuración. Use el ejemplo siguiente como referencia.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Pasos siguientes

Si es la primera vez que inserta en Power BI, consulte estos tutoriales para aprender a insertar el contenido de Power BI:
* [Tutorial: Inserción del contenido de Power BI en una aplicación para los clientes](embed-sample-for-customers.md)
* [Tutorial: Inserción del contenido de Power BI en una aplicación para la organización](embed-sample-for-your-organization.md)