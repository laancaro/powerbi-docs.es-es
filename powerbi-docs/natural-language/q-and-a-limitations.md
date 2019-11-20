---
title: Limitaciones de Preguntas y respuestas de Power BI
description: Limitaciones actuales de Preguntas y respuestas de Power BI
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 9f1beed3408d53a58a0fb725f9d98a4a95bb1b7c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874901"
---
# <a name="limitations-of-power-bi-qa"></a>Limitaciones de Preguntas y respuestas de Power BI

Preguntas y respuestas de Power BI actualmente tiene algunas limitaciones.

## <a name="data-sources"></a>Orígenes de datos

### <a name="supported-data-sources"></a>Orígenes de datos compatibles

Preguntas y respuestas de Power BI admite las siguientes configuraciones de orígenes de datos en el servicio Power BI:

- Modo de importación
- Conexión dinámica a Azure Analysis Services
- Conexión dinámica a SQL Server Analysis Services (con una puerta de enlace)
- Conjuntos de datos de Power BI. Power BI Desktop notifica un error con Preguntas y respuestas cuando se usa un conjunto de datos de Power BI. Sin embargo, al publicar el informe en el servicio Power BI, el error desaparece.

En cada una de estas configuraciones, también se admite la seguridad en el nivel de fila.

### <a name="data-sources-not-supported"></a>Orígenes de datos no compatibles

Preguntas y respuestas de Power BI no admite actualmente las siguientes configuraciones:

- Seguridad en el nivel de objeto con cualquier tipo de origen de datos.
- DirectQuery con cualquier origen. Una solución alternativa para admitirlo es usar Live Connect con Azure Analysis Services, que usa DirectQuery.
- Modelos compuestos
- Reporting Services 

## <a name="tooling-limitations"></a>Limitaciones de las herramientas

El nuevo cuadro de diálogo de herramientas permite a los usuarios personalizar y mejorar el lenguaje natural en Preguntas y respuestas. Para más información acerca de las herramientas, consulte [Introducción a las herramientas de Preguntas y respuestas](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Limitaciones de la revisión de las preguntas

La revisión de las preguntas solo almacena las preguntas que se han hecho al modelo de datos durante un máximo de 28 días. Al usar la nueva funcionalidad de revisión de las preguntas, es posible que observe que algunas no se registran. Esto es así intencionadamente, ya que el motor de lenguaje natural realiza una serie de pasos de limpieza de datos para asegurarse de que no se graben ni se muestren todas las pulsaciones de teclas de un usuario.

Los administradores de inquilinos pueden usar las opciones de administración de inquilinos para administrar la capacidad de almacenar preguntas. Los permisos se basan en grupos de seguridad. 

Para evitar que se graben sus preguntas, los usuarios pueden seleccionar **Configuración** > **General** y desactivar **Allow Q&A to record my utterance** (Permitir que Preguntas y respuestas registre mi expresión). 

## <a name="teach-qa-limitations"></a>Limitaciones de Enseñanza de Preguntas y respuestas

Enseñanza de Preguntas y respuestas permite corregir dos tipos de errores:

- Asignar una palabra a un campo.
- Asignar una palabra a una condición de filtro.

Actualmente no se permite redefinir un término reconocido ni definir otros tipos de condiciones o frases. Además, al definir las condiciones de filtro, solo puede usar un subconjunto limitado del idioma, como es:

- "País" que sea "Francia"
- "País" que no sea "Francia"
- "Peso" > 2000
- "Peso" = 2000
- "Peso" < 2000

> [!NOTE]
> Las herramientas de Preguntas y respuestas solo admiten el modo de importación. Todavía no admite la conexión a un origen de datos local o de Azure Analysis Services. Esta limitación actual se quitará en las versiones posteriores de Power BI.

### <a name="statements-not-supported"></a>Instrucciones no admitidas

- Actualmente no se admite el uso de medidas en las condiciones. En su lugar, convierta las medidas en columnas calculadas para que funcionen.
- No se admiten varias condiciones. Como alternativa, cree una columna calculada DAX que evalúe un valor booleano de la instrucción de varias condiciones y use este campo en su lugar.
- Si no se especifica una condición de filtro cuando Preguntas y respuestas pide un subconjunto de datos, no se puede guardar la definición, aunque la instrucción completa no tenga ningún subrayado en rojo.
