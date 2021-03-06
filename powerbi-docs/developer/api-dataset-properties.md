---
title: Propiedades de conjunto de datos de Power BI
description: Obtenga información sobre las propiedades de las API de conjunto de datos de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 9d0ab5bcffe3b0267b3e07a684c2c7c9bd0fd316
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "74265824"
---
# <a name="dataset-properties"></a>Propiedades del conjunto de datos

La v1 actual de la API de conjuntos de datos solo permite crear un conjunto de datos con un nombre y una colección de tablas. Cada tabla puede tener un nombre y una colección de columnas. Cada columna tiene un nombre y un tipo de datos. Estamos ampliando considerablemente estas propiedades, principalmente con compatibilidad con las medidas y las relaciones entre tablas. La lista completa de propiedades compatibles con esta versión es la siguiente:

> [!IMPORTANT]
> Puede tener acceso a ellas en la página de [grupos de operaciones de conjuntos de datos](https://docs.microsoft.com/rest/api/power-bi/datasets).

## <a name="dataset"></a>Conjunto de datos

Nombre  |Tipo  |Descripción  |Solo lectura  |Requerido
---------|---------|---------|---------|---------
id     |  GUID       | Identificador único de todo el sistema para el conjunto de datos.        | Verdadero        | False        
name     | Cadena        | Nombre definido por el usuario del conjunto de datos.        | False        | Verdadero        
tables     | Tabla[]        | Colección de tablas.        |  False       | False        
relationships     | Relación[]        | Colección de relaciones entre tablas.        | False        |  False  
defaultMode     | Cadena        | Determina si el conjunto de datos se inserta, se transmite, o ambas posibilidades, con los valores de "Push" y "Streaming".         | False        |  False

## <a name="table"></a>Tabla

Nombre  |Tipo  |Descripción  |Solo lectura  |Requerido
---------|---------|---------|---------|---------
name     | Cadena        |  Nombre definido por el usuario de la tabla. También se usa como identificador de la tabla.       | False        |  Verdadero       
columns     |  columna[]       |  Colección de columnas.       | False        |  Verdadero       
measures     | medida[]        |  Colección de medidas.       | False        |  False       
isHidden     | Booleano        | Si es true, se ocultará la tabla de las herramientas cliente.        | False        | False        

## <a name="column"></a>Columna

Nombre  |Tipo  |Descripción  |Solo lectura  |Requerido
---------|---------|---------|---------|---------
name     |  Cadena        | Nombre definido por el usuario de la columna.        |  False       | Verdadero       
dataType     |  Cadena       |  [Tipos de datos de EDM](https://msdn.microsoft.com/library/ee382832.aspx) y restricciones compatibles. Vea [Restricciones de tipo de datos](#DataTypeRestrictions).      |  False       | Verdadero        
formatString     | Cadena        | Cadena que describe cómo debe ser el formato del valor al mostrarse. Para más información sobre el formato de cadena, vea [FORMAT_STRING, contenido](https://msdn.microsoft.com/library/ms146084.aspx).      | False        | False        
sortByColumn    | Cadena        |   Nombre de cadena de una columna de la misma tabla que se va a usar para ordenar la columna actual.     | False        | False       
dataCategory     | Cadena        |  Valor de cadena que se va a usar para la categoría de datos que describe los datos de esta columna. Algunos valores habituales son: dirección, ciudad, continente, país, imagen, URL de imagen, latitud, longitud, organización, ubicación, código postal, estado o provincia, URL de web       |  False       | False        
isHidden    |  Booleano       |  Propiedad que indica si la columna está oculta de la vista. El valor predeterminado es false.       | False        | False        
summarizeBy     | Cadena        |  Método de agregación predeterminado para la columna. Los valores incluyen: default, none, sum, min, max, count, average, distinctCount     |  False       | False

## <a name="measure"></a>Medida

Nombre  |Tipo  |Descripción  |Solo lectura  |Requerido
---------|---------|---------|---------|---------
name     | Cadena        |  Nombre definido por el usuario de la medida.       |  False       | Verdadero        
expression     | Cadena        | Expresión DAX válida.        | False        |  Verdadero       
formatString     | Cadena        |  Cadena que describe cómo debe ser el formato del valor al mostrarse. Para más información sobre el formato de cadena, vea [FORMAT_STRING, contenido](https://msdn.microsoft.com/library/ms146084.aspx).       | False        | False        
isHidden     | Cadena        |  Si es true, se ocultará la tabla de las herramientas cliente.       |  False       | False       

## <a name="relationship"></a>Relación

Nombre  |Tipo  |Descripción  |Solo lectura  |Requerido 
---------|---------|---------|---------|---------
name     | Cadena        | Nombre definido por el usuario de la relación. También se usa como identificador de la relación.        | False       | Verdadero        
crossFilteringBehavior     | Cadena        |    La dirección del filtro de la relación: OneDirection (valor predeterminado), BothDirections, Automatic       | False        | False        
fromTable     | Cadena        | Nombre de la tabla de clave externa.        | False        | Verdadero         
fromColumn    | Cadena        | Nombre de la columna de clave externa.        | False        | Verdadero         
toTable    | Cadena        | Nombre de la tabla de clave principal.        | False        | Verdadero         
toColumn     | Cadena        | Nombre de la columna de clave principal.        | False        | Verdadero        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Restricciones de tipo de datos (se aplica a la propiedad dataType)

Tipo de datos  |Restricciones  
---------|---------
Int64     |   Int64.MaxValue e Int64.MinValue no están permitidos.      
Doble     |  Double.MaxValue y Double.MinValue no están permitidos. NaN no se admite. +Infinity y -Infinity no se admiten en algunas funciones (por ejemplo, Min, Max).       
Booleano     |   True o False.
Fecha y hora    |   Durante la carga de datos se cuantifican valores con fracciones de día a múltiplos enteros de 1/300 segundos (3,33 ms).      
Cadena     |  Actualmente, se permite un máximo de 4000 caracteres por valor de cadena.
Decimal|precisión=28, escala=4

## <a name="example"></a>Ejemplo
El siguiente ejemplo de código incluye una serie de estas propiedades:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```