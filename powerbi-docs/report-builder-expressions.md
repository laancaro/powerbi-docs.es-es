---
title: Expresiones en el Generador de informes de Power BI
description: En los informes paginados de Power BI Report Builder se usan ampliamente expresiones para recuperar, calcular, mostrar, agrupar, ordenar, filtrar, parametrizar y dar formato a los datos.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 96c62fec55f87a31970b624a79314656ced0c159
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953859"
---
# <a name="expressions-in-power-bi-report-builder"></a>Expresiones en el Generador de informes de Power BI
  En los informes paginados de Power BI Report Builder se usan ampliamente expresiones para recuperar, calcular, mostrar, agrupar, ordenar, filtrar, parametrizar y dar formato a los datos. 
  
  Muchas propiedades de los elementos de informe pueden establecerse en una expresión. Las expresiones ayudan a controlar el contenido, el diseño y la interactividad de un informe. Las expresiones se escriben en Microsoft Visual Basic, se guardan en la definición de informe y el procesador de informes las evalúa al ejecutar el informe.  
  
 A diferencia de aplicaciones como Excel de Microsoft Office, donde se trabaja con datos directamente en una hoja de cálculo, en un informe se trabaja con expresiones que actúan como marcadores de posición para los datos. Para ver los datos reales de las expresiones evaluadas, debe obtener una vista previa del informe. Al ejecutar el informe, el procesador de informes evalúa cada expresión a medida que combina los datos del informe y los elementos de diseño del informe, tales como tablas y gráficos.  
  
 Al diseñar un informe, se establecen automáticamente muchas expresiones de elementos de informe. Por ejemplo, cuando se arrastra un campo desde el panel de datos a una celda de tabla en la superficie de diseño del informe, se establece el valor del cuadro de texto en una expresión simple para el campo. En la ilustración siguiente, el panel Datos de informe muestra los campos del conjunto de datos ID, Name, SalesTerritory, Code y Sales. Se han agregado tres campos a la tabla: [Name], [Code] y [Sales]. La notación [Name] en la superficie de diseño representa la expresión subyacente `=Fields!Name.Value`.  
  
![Vista de diseño del Generador de informes](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 Al mostrar la vista previa del informe, el procesador de informes combina la región de datos de tabla con los datos reales de la conexión de datos y muestra una fila de la tabla para cada fila del conjunto de resultados.  
  
 Para escribir expresiones manualmente, seleccione un elemento en la superficie de diseño y utilice los menús contextuales y los cuadros de diálogo para establecer las propiedades del elemento. Cuando vea el botón ***(fx)*** o el valor `<Expression>` en una lista desplegable, sabrá que puede establecer la propiedad en una expresión. 
  
##  <a name="Types"></a> Descripción de las expresiones simples y complejas  
 Las expresiones comienzan por un signo igual (=) y se escriben en Microsoft Visual Basic. Las expresiones pueden incluir una combinación de constantes, operadores y referencias a valores integrados (campos, colecciones y funciones) y a código externo o personalizado.  
  
 Puede utilizar expresiones para especificar el valor de muchas propiedades de elementos de informe. Las propiedades más comunes son los valores de los cuadros de texto y el texto de los marcadores de posición. Normalmente, si un cuadro de texto contiene solo una expresión, esta es el valor de la propiedad del cuadro de texto. Si un cuadro de texto contiene varias expresiones, cada una es el valor del texto de los marcadores de posición en el cuadro de texto.  
  
 De forma predeterminada, las expresiones aparecen en la superficie de diseño del informe como *expresiones simples* o *complejas*.  
  
-   **Simples**. Las expresiones simples contienen una referencia a un único elemento de una colección integrada, por ejemplo, un campo de conjunto de datos, un parámetro o un campo integrado. En la superficie de diseño, una expresión simple aparece entre corchetes. Por ejemplo, `[FieldName]` corresponde a la expresión subyacente `=Fields!FieldName.Value`. Las expresiones simples se crean automáticamente al crear el diseño del informe y arrastrar elementos desde el panel Datos de informe a la superficie de diseño. Para más información sobre los símbolos que representan las diferentes colecciones integradas, consulte la [descripción de los símbolos de prefijo para las expresiones simples](#DisplayText).  
  
-   **Complejas**. Las expresiones complejas contienen referencias a varias referencias integradas, operadores y llamadas de función. Una expresión compleja aparece como <\<Expr >> cuando el valor de expresión incluye más de una referencia simple. Para ver la expresión, mantenga el mouse sobre ella y use la información sobre herramientas. Para modificar la expresión, ábrala en el cuadro de diálogo **Expresión**.  
  
 La siguiente ilustración muestra expresiones simples y complejas típicas para cuadros de texto y texto de marcadores de posición.  
  
![Formato predeterminado de las expresiones en el Generador de informes](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Para mostrar valores de ejemplo en lugar de texto para las expresiones, aplique formato al texto del marcador de posición o al cuadro de texto. La siguiente ilustración muestra la superficie de diseño del informe alternando para mostrar los valores de ejemplo:  
  
![Formato de ejemplo de las expresiones en el Generador de informes](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="DisplayText"></a> Descripción de los símbolos de prefijo en expresiones simples  

Las expresiones simples usan símbolos para indicar si la referencia es un campo, un parámetro, una colección integrada o la colección ReportItems. En la tabla siguiente se muestran ejemplos de texto para mostrar y texto de la expresión:  
  
|Artículo|Ejemplo de texto para mostrar|Ejemplo de texto de la expresión|  
|----------|--------------------------|-----------------------------|  
|Campos del conjunto de datos|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Parámetros de informe|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Campos integrados|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Caracteres literales usados para mostrar texto|`\[Sales\]`|`[Sales]`|  
  
##  <a name="References"></a> Escritura de expresiones complejas  
 Las expresiones pueden incluir referencias a funciones, operadores, constantes, campos, parámetros, elementos de colecciones integradas y código personalizado insertado o ensamblados personalizados.  
  
 En la tabla siguiente se enumeran los tipos de referencias que puede incluir en una expresión:  
  
|Referencias|Descripción|Ejemplo|  
|----------------|-----------------|-------------|  
|Constantes|Describe las constantes a las que puede tener acceso interactivamente para las propiedades que requieren valores constantes, como los colores de fuente.|`="Blue"`|  
|Operadores|Describe los operadores que puede utilizar para combinar referencias en una expresión. Por ejemplo, el operador **&** se utiliza para concatenar cadenas.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Colecciones integradas|Describe las colecciones integradas que puede incluir en una expresión, por ejemplo, `Fields`, `Parameters` y `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Informes integrados y funciones de agregado|Describe las funciones integradas, como `Sum` o `Previous`, a las que puede tener acceso desde una expresión.|`=Previous(Sum(Fields!Sales.Value))`|  
|Referencias a código y ensamblados personalizados en expresiones en el Generador de informes |Describe cómo obtener acceso a las clases integradas de CLR `xref:System.Math` y `xref:System.Convert`, otras clases de CLR, funciones de biblioteca en tiempo de ejecución de Visual Basic o métodos de un ensamblado externo.<br /><br /> Describe cómo tener acceso a código personalizado que está insertado en el informe o que se compila e instala como un ensamblado personalizado en el cliente de informes y el servidor de informes.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="Valid"></a> Validación de expresiones  
 Cuando se crea una expresión para una propiedad de elemento de informe determinada, las referencias que se pueden incluir en una expresión dependen de los valores que la propiedad deñ elemento de informe puede aceptar y el ámbito en el que se evalúa la propiedad. Por ejemplo:  
  
-   De forma predeterminada, la expresión [sum] calcula la suma de los datos que están en el ámbito en el momento en que se evalúa la expresión. En el caso de una celda de tabla, el ámbito depende de la pertenencia a grupos de filas y columnas. 
  
-   En el caso del valor de una propiedad de fuente, el valor debe evaluarse como el nombre de una fuente.  
  
-   La sintaxis de expresión se valida en tiempo de diseño. La validación del ámbito de la expresión se produce cuando se publica el informe. Si la validación depende de los datos reales, los errores solo se pueden detectar en tiempo de ejecución. Algunas de estas expresiones generan #Error como mensaje de error en el informe representado. 

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
