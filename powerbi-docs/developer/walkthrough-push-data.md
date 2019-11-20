---
title: Inserción de datos en un conjunto de datos
description: Inserción de datos en un conjunto de datos de Power BI
author: rkarlin
ms.author: rkarlin
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 5db16bfdc1013668be5103f392d6f298c8faf925
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875447"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Inserción de datos en un conjunto de datos de Power BI

La API de Power BI permite insertar datos en un conjunto de datos de Power BI. En este artículo, le mostramos cómo insertar un conjunto de datos de marketing de ventas que contiene una tabla de productos en un conjunto de datos existente.

Antes de empezar, necesita una [cuenta de Power BI](create-an-azure-active-directory-tenant.md) y Azure Active Directory (Azure AD).

## <a name="steps-to-push-data-into-a-dataset"></a>Pasos para insertar datos en un conjunto de datos

* Paso 1: [Registrar una aplicación con Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Paso 2: [Obtener un token de acceso de autenticación](walkthrough-push-data-get-token.md)
* Paso 3: [Creación de un conjunto de datos en Power BI](walkthrough-push-data-create-dataset.md)
* Paso 4: [Obtener un conjunto de datos para agregar filas a una tabla de Power BI](walkthrough-push-data-get-datasets.md)
* Paso 5: [Agregar filas a una tabla de Power BI](walkthrough-push-data-add-rows.md)

La siguiente sección es una discusión general de las operaciones de la API de Power BI que insertan datos.

## <a name="power-bi-api-operations-to-push-data"></a>Operaciones de la API de Power BI para insertar datos

Con la API de REST de Power BI, puede insertar orígenes de datos en Power BI. Cuando una aplicación agrega filas a un conjunto de datos, los iconos del panel se actualizan automáticamente con los datos nuevos. Para insertar datos, use las operaciones [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset) y [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows). Para buscar un conjunto de datos, use la operación [Obtener conjuntos de datos](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets). Puede pasar un identificador de grupo para trabajar con un grupo para cualquiera de estas operaciones. Para obtener una lista de identificadores de grupo, use la operación [Obtener grupos](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups).

Estas son las operaciones para insertar datos en un conjunto de datos:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Obtener conjuntos de datos](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Obtener grupos](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Para crear un conjunto de datos en Power BI se pasa una cadena de notación de objetos JavaScript (JSON) al servicio Power BI. Para obtener más información acerca de JSON, consulte [Introducción a JSON](https://json.org/).

La cadena JSON para un conjunto de datos tiene el formato siguiente:

**Objeto JSON de conjunto de datos de Power BI**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Para nuestro ejemplo de conjunto de datos de marketing de ventas, pasaría una cadena JSON como se muestra a continuación. En este ejemplo, **SalesMarketing** es el nombre del conjunto de datos y **Product** es el nombre de la tabla. Después de definir la tabla, se define el esquema de la tabla. Para el conjunto de datos **SalesMarketing**, el esquema de tabla tiene las siguientes columnas: ProductID, Manufacturer, Category, Segment, Product e IsCompete.

**Ejemplo de JSON de objeto de conjunto de datos**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

Para un esquema de tabla de Power BI, puede usar los siguientes tipos de datos.

## <a name="power-bi-table-data-types"></a>Tipos de datos de tabla de Power BI

| **Tipo de datos** | **Restricciones** |
| --- | --- |
| Int64 |Int64.MaxValue e Int64.MinValue no están permitidos. |
| Doble |Double.MaxValue y Double.MinValue no están permitidos. NaN no se admite. +Infinity y -Infinity no se admiten en algunas funciones (por ejemplo, Min, Max). |
| Booleano |Ninguno |
| Fecha y hora |Durante la carga de datos se cuantifican valores con fracciones de día a múltiplos enteros de 1/300 segundos (3,33 ms). |
| Cadena |Actualmente permite hasta 128 K caracteres. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Más información sobre la inserción de datos en Power BI

Para empezar a insertar datos en un conjunto de datos, consulte [Paso 1: Registrar una aplicación en Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) en el panel de navegación.

[Paso siguiente >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Pasos siguientes

[Suscribirse en Power BI](create-an-azure-active-directory-tenant.md)  
[Introducción a JSON](https://json.org/)  
[Información general sobre la API de REST de Power BI](overview-of-power-bi-rest-api.md)  
¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)