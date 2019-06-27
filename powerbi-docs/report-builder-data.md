---
title: Datos del informe en el Generador de informes de Power BI
description: El primer paso para diseñar un informe en el Generador de informes paginados de Power BI consiste en crear los orígenes de datos y los conjuntos de datos que representan los datos del informe subyacente.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: 3c2f6882e9480802d40ff61580ebfda9bbf3b14a
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840335"
---
# <a name="report-data-in-power-bi-report-builder"></a>Datos del informe en el Generador de informes de Power BI

Los datos del informe pueden proceder de varios orígenes de datos de la organización. El primer paso para diseñar un informe en el Generador de informes de Power BI consiste en crear los orígenes de datos y los conjuntos de datos que representan los datos del informe subyacente. Cada origen de datos incluye la información de la conexión de datos. Cada conjunto de datos incluye un comando de consulta que define el conjunto de campos que se utilizan como datos de un origen de datos. Para visualizar los datos de cada conjunto de datos, agregue una región de datos, como una tabla, una matriz, un gráfico o un mapa. Cuando se procesa el informe, las consultas se ejecutan en el origen de datos y cada región de datos se expande según sea necesario para mostrar los resultados de la consulta para el conjunto de datos.  

Obtenga información sobre la [Creación de un origen de datos insertado para informes paginados en el Generador de informes de Power BI](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Términos  
  
- **Conexión de datos.** También se conoce como un *origen de datos*. Una conexión de datos incluye un nombre de conexión y propiedades que dependen del tipo de conexión. Por diseño, una conexión de datos no incluye las credenciales. Una conexión de datos no especifica qué datos deben recuperarse del origen de datos externo. Para ello, se especifica una consulta al crear un conjunto de datos.  
  
- **Cadena de conexión.** Una cadena de conexión es una versión de cadena de las propiedades de conexión que son necesarias para conectarse a un origen de datos. Las propiedades de conexión varían en función del tipo de conexión de datos.  
  
- **Origen de datos insertado.** También se denomina un *origen de datos específico del informe*. Un origen de datos que se define en un informe y se usa solo en ese informe.  
  
- **Credenciales.** Las credenciales son la información de autenticación que se debe proporcionar para poder tener acceso a datos externos.  
  
##  <a name="BkMk_ReportDataTips"></a> Sugerencias para especificar los datos del informe

 Use la siguiente información para diseñar la estrategia de datos del informe.  
  
- **Filtrar datos**. Los datos del informe se pueden filtrar en la consulta o en el informe. Puede usar variables de consulta y conjuntos de datos para crear parámetros en cascada y proporcionar al usuario la posibilidad de reducir las opciones de miles de selecciones a un número más fácil de administrar. Puede filtrar los datos de una tabla o un gráfico según los valores de los parámetros u otros valores que especifique.  
  
- **Parámetros**. Los comandos de la consulta del conjunto de datos que incluyen variables de consulta crean automáticamente los parámetros del informe correspondiente. También puede crear manualmente los parámetros. Cuando se visualiza un informe, la barra de herramientas del informe muestra los parámetros. Los usuarios pueden seleccionar valores para controlar los datos del informe o el aspecto del informe. Para personalizar los datos del informe para públicos específicos, puede crear conjuntos de parámetros del informe con diferentes valores predeterminados vinculados a la misma definición de informe o usar el campo integrado **UserID**. 
  
- **Agrupar y agregar datos**. Los datos del informe se pueden agrupar y agregar en la consulta o en el informe. Si agrega los valores en la consulta, puede también combinar los valores en el informe dentro de las restricciones de lo que es significativo.  
  
- **Ordenar datos**. Los datos del informe se pueden ordenar en la consulta o en el informe. En las tablas también puede agregar un botón de ordenación interactivo para permitir al usuario controlar el criterio de ordenación.  
  
- **Datos basados en expresiones**. Puesto que la mayoría de las propiedades del informe pueden estar basadas en expresiones y las expresiones pueden incluir referencias a los campos del conjunto de datos y los parámetros del informe, puede escribir expresiones eficaces para controlar los datos y el aspecto del informe. Puede proporcionar a un usuario la posibilidad de controlar los datos que visualiza mediante la definición de parámetros.  
  
- **Mostrar los datos de un conjunto de datos**. Los datos de un conjunto de datos normalmente se muestran en una o más regiones de datos; por ejemplo, una tabla y un gráfico.  
  
- **Mostrar los datos de varios conjuntos de datos**. Puede escribir expresiones en una región de datos basadas en un conjunto de datos que busca o agrega los valores de otros conjuntos de datos. Puede incluir subinformes en una tabla basada en un conjunto de datos para mostrar los datos de un origen de datos diferente.  
  
 Utilice la siguiente lista para ayudar a definir los orígenes de datos de un informe.  
  
- Comprender la arquitectura de la capa de datos del software de la organización y las posibles incidencias que surgen de los tipos de datos. Comprender cómo pueden afectar las extensiones de datos y las extensiones de procesamiento de datos a los resultados de la consulta. Los tipos de datos varían entre el origen de datos, los proveedores de datos y los tipos de datos almacenados en el archivo de definición del informe (.rdl).  
  
- Los orígenes de datos y los conjuntos de datos se crean en un informe y se publican en el servicio Power BI. Una vez que se publican, puede configurar las credenciales directamente en el servicio Power BI o en la puerta de enlace empresarial. 

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
