---
title: Ejemplos de expresiones en el Generador de informes de Power BI
description: A menudo se usan expresiones en los informes paginados de Power BI Report Builder para controlar el aspecto y el contenido de estos.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48e81c91a4555b4c8ea847ddffb1413058bbb152
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953978"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Ejemplos de expresiones en el Generador de informes de Power BI
A menudo se usan expresiones en los informes paginados de Power BI Report Builder para controlar el aspecto y el contenido de estos. Las expresiones se escriben en Microsoft Visual Basic y pueden usar funciones integradas, código personalizado, variables de informe y grupo, y variables definidas por el usuario. Las expresiones comienzan con un signo igual (=).   

En este tema se proporcionan ejemplos de expresiones que se pueden usar para tareas comunes en un informe.  
  
-   [Funciones de Visual Basic](#VisualBasicFunctions): ejemplos de funciones de fecha, cadena, conversión y condicionales de Visual Basic.  
  
-   [Funciones de informes](#ReportFunctions): ejemplos de agregados y otras funciones de informe integradas.  
  
-   [Apariencia de los datos de informe](#AppearanceofReportData): ejemplos para cambiar la apariencia de un informe.  
  
-   [Propiedades](#Properties): ejemplos para establecer las propiedades de los elementos de informe con el fin de controlar el formato o la visibilidad.  
  
-   [Parámetros](#Parameters): ejemplos para usar parámetros en una expresión.  
  
-   [Código personalizado](#CustomCode): ejemplos de código personalizado insertado.  
  
Para más información sobre las expresiones simples y complejas, dónde se pueden usar las expresiones y los tipos de referencias que se pueden incluir en una expresión, consulte los temas incluidos en [Expressions in Power BI Report Builder](report-builder-expressions.md) (Expresiones en el Generador de informes de Power BI). 
  
## <a name="functions"></a>Funciones  
 Muchas expresiones en un informe contienen funciones. Puede usar esta funciones para dar formato a los datos, aplicar lógica y acceder a los metadatos del informe. Puede escribir expresiones que usen funciones de la biblioteca en tiempo de ejecución de Microsoft Visual Basic y de los espacios de nombres `xref:System.Convert` y `xref:System.Math`. Puede agregar referencias a funciones en el código personalizado. También puede usar las clases de Microsoft .NET Framework, incluida `xref:System.Text.RegularExpressions`.  
  
##  <a name="VisualBasicFunctions"></a> Funciones de Visual Basic  
 Puede usar funciones de Visual Basic para manipular los datos que se muestran en los cuadros de texto o que se utilizan para los parámetros, las propiedades u otras áreas del informe. En esta sección se proporcionan ejemplos que demuestran algunas de estas funciones. Para más información, consulte [Miembros de la biblioteca en tiempo de ejecución de Visual Basic](https://go.microsoft.com/fwlink/?LinkId=198941) en MSDN.  
  
 .NET Framework proporciona muchas opciones de formato personalizado, por ejemplo, formatos de fecha específicos. Para más información, consulte [Aplicar formato a tipos en .NET](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Funciones matemáticas  
  
-   La función **Round** es útil para redondear números al entero más cercano. La expresión siguiente redondea 1,3 a 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     También puede escribir una expresión para redondear un valor al múltiplo que especifique, similar a la función **REDOND.MULT** de Excel. Multiplique el valor por un factor que cree un entero, redondee el número y, a continuación, divida por el mismo factor. Por ejemplo, para redondear 1,3 al múltiplo más cercano de 0,2 (1,4), use la siguiente expresión:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="DateFunctions"></a> Funciones de fecha  
  
-   La función **Today** proporciona la fecha actual. Esta expresión puede utilizarse en un cuadro de texto para mostrar la fecha en el informe, o en un parámetro para filtrar los datos según la fecha actual.  
  
    ```  
    =Today()  
    ```  
  
-   Use la función **DateInterval** para extraer una parte de una fecha específica. Estos son algunos parámetros válidos de **DateInterval**:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Por ejemplo, esta expresión mostrará el número de la semana del año actual para el día de hoy:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   La función **DateAdd** es útil para suministrar un intervalo de fechas basado en un único parámetro. La siguiente expresión proporciona una fecha que es seis meses posterior a la fecha del parámetro llamado *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   La función **año** muestra el año correspondiente a una fecha determinada. Se puede usar para agrupar fechas o para mostrar el año como una etiqueta para un conjunto de fechas. Esta expresión proporciona el año de un grupo determinado de fechas de pedidos de ventas. La función **Month** y otras funciones también pueden usarse para manipular fechas. Para más información, consulte la documentación sobre Visual Basic.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Puede combinar funciones en una expresión para personalizar el formato. La siguiente expresión cambia el formato de una fecha con el formato mes-día-año a un número mes-semana-semana. Por ejemplo, 12/23/2009 a diciembre semana 3:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Cuando se usa como un campo calculado en un conjunto de datos, puede utilizar esta expresión en un gráfico para agregar valores por semana dentro de cada mes.  
  
-   La siguiente expresión da formato al valor SellStartDate como MMM-YY. El campo SellStartDate es un tipo de datos de fecha y hora.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   La siguiente expresión da formato al valor SellStartDate como dd/MM/aaaa. El campo SellStartDate es un tipo de datos de fecha y hora.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   La función **CDate** convierte el valor en una fecha. La función **Now** devuelve un valor de fecha que contiene la fecha y hora actuales según el sistema. **DateDiff** devuelve un valor Long que especifica el número de intervalos de tiempo entre dos valores de fecha.  
  
     En el ejemplo siguiente se muestra la fecha de inicio del año actual.  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   En el ejemplo siguiente se muestra la fecha de inicio del mes anterior en función del mes actual.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   La siguiente expresión genera los años en el intervalo entre SellStartDate y LastReceiptDate. Estos campos están en dos conjuntos de datos distintos, DataSet1 y DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   La función **DatePart** devuelve un valor entero que contiene el componente especificado de un valor de fecha dado. La siguiente expresión devuelve el año para el primer valor de SellStartDate en DataSet1. Se especifica el ámbito del conjunto de datos porque hay varios conjuntos de datos en el informe.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   La función **DateSerial** devuelve un valor de fecha que representa un año, mes y día, con la información de hora establecida a medianoche. En el ejemplo siguiente se muestra la fecha de fin del mes anterior en función del mes actual.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Las siguientes expresiones muestran varias fechas según un valor de parámetro de fecha seleccionado por el usuario.  
  
|Descripción del ejemplo|Ejemplo|  
|-------------------------|-------------|  
|Ayer|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Hace dos días|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Hace un mes|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Hace dos meses|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Hace un año|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Hace dos años|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="StringFunctions"></a> Funciones de cadena  
  
-   Combine más de un campo mediante el uso de operadores de concatenación y constantes de Visual Basic. La siguiente expresión devuelve dos campos, cada uno en una línea diferente del mismo cuadro de texto:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Dé formato a fechas y números en una cadena con la función **Format**. La siguiente expresión muestra los valores de los parámetros *StartDate* y *EndDate* en formato de fecha larga:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Si el cuadro de texto contiene solo una fecha o un número, debe usar la propiedad Format del cuadro de texto para aplicar formato en lugar de usar la función **Format** en el cuadro de texto.  
  
-   Las funciones **Right**, **Len** e **InStr** son útiles para devolver una subcadena; por ejemplo, para recortar solo el nombre del usuario en *DOMAIN*\\*username*. La siguiente expresión devuelve la parte de la cadena situada a la derecha de una barra diagonal inversa (\\) en un parámetro llamado *user*:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     La siguiente expresión da como resultado el mismo valor que el anterior, usando los miembros de la clase `xref:System.String` de .NET Framework en lugar de funciones de Visual Basic:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Muestre los valores seleccionados de un parámetro de varios valores. En el ejemplo siguiente se usa la función **Join** para concatenar los valores seleccionados del parámetro *MySelection* en una sola cadena que se puede establecer como una expresión para el valor de un cuadro de texto en un elemento de informe:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     El ejemplo siguiente hace lo mismo que el ejemplo anterior, y muestra también una cadena de texto antes de la lista de valores seleccionados.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   Las funciones **Regex** de la clase `xref:System.Text.RegularExpressions` de .NET Framework son útiles para cambiar el formato de cadenas existentes, por ejemplo, para dar formato a un número de teléfono. La siguiente expresión utiliza la función **Replace** para cambiar el formato de un número de teléfono de diez dígitos de un campo "*nnn*-*nnn*-*nnnn*" a "(*nnn*) *nnn*-*nnnn*":  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Compruebe que el valor de Fields!Phone.Value no tenga espacios adicionales y es del tipo `xref:System.String`.  
  
### <a name="lookup"></a>Lookup  
  
-   Puede especificar un campo de clave para usar la función **Lookup** para recuperar un valor de un conjunto de datos en una relación uno a uno; por ejemplo, un par de clave y valor. La siguiente expresión muestra el nombre del producto de un conjunto de datos ("Product") que coincida con el identificador de producto especificado:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Puede especificar un campo de clave para usar la función **LookupSet** para recuperar un conjunto de valores de un conjunto de datos en una relación uno a uno. Por ejemplo, una persona puede tener varios números de teléfono. En el ejemplo siguiente, suponga que el conjunto de datos PhoneList contiene un identificador de persona y un número de teléfono en cada fila. **LookupSet** devuelve una matriz de valores. La siguiente expresión combina los valores devueltos en una sola cadena y muestra la lista de números de teléfono de la persona especificada por ContactID:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="ConversionFunctions"></a> Funciones de conversión  
 Puede usar funciones de Visual Basic para convertir un campo de un tipo de datos a otro. Las funciones de conversión se pueden usar para convertir el tipo de datos predeterminado de un campo al tipo de datos necesario para realizar cálculos o para combinar texto.  
  
-   La expresión siguiente convierte la constante 500 al tipo Decimal con el fin de compararla con un tipo de datos monetario de Transact-SQL en el campo Value de una expresión de filtro.  
  
    ```  
    =CDec(500)  
    ```  
  
-   La siguiente expresión muestra el número de valores seleccionados para el parámetro de varios valores *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="DecisionFunctions"></a> Funciones de decisión  
  
-   La función **Iif** devuelve uno de dos valores dependiendo de si la expresión es cierta o no. La siguiente expresión utiliza la función **Iif** para devolver un valor booleano **True** si el valor de `LineTotal` es superior a 100. De lo contrario, devuelve **False**:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Use varias funciones **IIF** (lo que también se conoce como "funciones IIF anidadas") para devolver uno de tres valores dependiendo del valor de `PctComplete`. La siguiente expresión se puede colocar en el color de relleno de un cuadro de texto para cambiar el color de fondo según el valor que hay en el cuadro de texto.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Valores mayores o iguales que 10 se muestran con un fondo verde, entre 1 y 9 se muestran con un fondo azul y menores que 1 se muestran con un fondo rojo.  
  
-   Otra forma de obtener la misma funcionalidad es con la función **Switch**. La función **Switch** es útil cuando se necesita probar tres o más condiciones. La función **Switch** devuelve el valor asociado a la primera expresión de una serie que se evalúa como True:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Los valores mayores o iguales que 10 se muestran con un fondo verde, entre 1 y 9 se muestran con un fondo azul, igual que 1 se muestra con un fondo amarillo, y 0 o menores se muestran con un fondo rojo.  
  
-   Prueba el valor del campo `ImportantDate` y devuelve "Red" si tiene más de una semana de antigüedad o "Blue" en caso contrario. Esta expresión puede utilizarse para controlar la propiedad Color de un cuadro de texto en un elemento de informe:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Prueba el valor del campo `PhoneNumber` y devuelve "No Value" si es **null** (**Nothing** en Visual Basic); en caso contrario, devuelve un valor de número de teléfono. Esta expresión puede utilizarse para controlar el valor de un cuadro de texto en un elemento de informe.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Prueba el valor del campo `Department` y devuelve un nombre de subinforme o **null** (**Nothing** en Visual Basic). Esta expresión puede utilizarse con subinformes detallados condicionales.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Prueba si el valor de un campo es null. Esta expresión puede utilizarse para controlar la propiedad **Hidden** de un elemento de informe de imagen. En el ejemplo siguiente, la imagen especificada por el campo [LargePhoto] se muestra solamente si el valor del campo no es null.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   La función **MonthName** devuelve un valor de cadena que contiene el nombre del mes especificado. El ejemplo siguiente muestra NA en el campo Month si el campo contiene el valor 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="ReportFunctions"></a> Funciones de informe  
 En una expresión, puede agregar una referencia a funciones de informe adicionales que manipulan los datos de un informe. En esta sección se proporcionan ejemplos de estas funciones. 
  
###  <a name="Sum"></a> Sum  
  
-   La función **Sum** puede sumar los valores de un grupo o una región de datos. Esta función puede ser útil en el encabezado o pie de página de un grupo. La siguiente expresión muestra la suma de los datos del grupo o la región de datos Order:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   También puede usar **Sum** para calcular agregados condicionales. Por ejemplo, si un conjunto de datos tiene un campo llamado State con los valores posibles No Started, Started y Finished, cuando se coloca en un encabezado de grupo, la siguiente expresión calcula la suma agregada solo para el valor Finished:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="RowNumber"></a> RowNumber  
  
-   Cuando se usa en un cuadro de texto dentro de una región de datos, la función **RowNumber** muestra el número de fila de cada instancia del cuadro de texto en el que aparece la expresión. Esta función puede ser útil para numerar las filas de una tabla. También puede ser útil para tareas más complejas, como proporcionar saltos de página en función del número de filas. Para más información, consulte [Saltos de página](#PageBreaks) en este tema.  
  
     El ámbito que especifique para **RowNumber** controlará cuándo comienza la nueva numeración. La palabra clave **Nothing** indica que la función empezará a contar desde la primera fila de la región de datos más externa. Para empezar a contar dentro de regiones de datos anidadas, utilice el nombre de la región de datos. Para empezar a contar dentro de un grupo, use el nombre del grupo.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="AppearanceofReportData"></a> Apariencia de los datos del informe  
 Puede usar expresiones para manipular cómo aparecen los datos en un informe. Por ejemplo, puede mostrar los valores de dos campos en un solo cuadro de texto, mostrar información sobre el informe o especificar cómo se insertan los saltos de página en el informe.  
  
###  <a name="PageHeadersandFooters"></a> Encabezados y pies de página  
 Al diseñar un informe, quizás quiera mostrar el nombre de lo informes y número de página en el pie de página del informe. Para ello, puede usar las siguientes expresiones:  
  
-   La siguiente expresión proporciona el nombre del informe y la fecha y hora a la que se ejecutó. Se puede colocar en un cuadro de texto en el pie de página o en el cuerpo del informe. La fecha y hora se presenta con el formato de fecha corta de .NET Framework:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   La siguiente expresión se coloca en un cuadro de texto en el pie de página de un informe y proporciona el número de página y el número total de páginas del informe:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 Los ejemplos siguientes describen cómo mostrar los valores primero y último de una página en el encabezado de página, similar a lo que aparece en una lista de directorios. En el ejemplo se da por hecho que una región de datos contiene un cuadro de texto llamado `LastName`.  
  
-   La siguiente expresión se sitúa en un cuadro de texto en el lado izquierdo del encabezado de página y proporciona el primer valor del cuadro de texto `LastName` en la página:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   La siguiente expresión se sitúa en un cuadro de texto en el lado derecho del encabezado de página y proporciona el último valor del cuadro de texto `LastName` en la página:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 El ejemplo siguiente describe cómo mostrar el total de páginas. En el ejemplo se da por hecho que una región de datos contiene un cuadro de texto llamado `Cost`.  
  
-   La siguiente expresión se sitúa en el encabezado o pie de página y proporciona la suma de los valores del cuadro de texto `Cost` de la página:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Solo puede hacer referencia a un elemento de informe por expresión en un encabezado o pie de página. Además, en las expresiones de pie de página o encabezado, puede hacer referencia al nombre del cuadro de texto, pero no a la expresión de datos real dentro del cuadro de texto.  
  
###  <a name="PageBreaks"></a> Saltos de página  
 En algunos informes, tal vez quiera insertar un salto de página al final de un número de filas determinado en lugar o además de por grupos o elementos de informe. Para ello, cree un grupo que contenga los grupos o registros detallados que desee, agregue un salto de página al grupo y, a continuación, agregue una expresión de grupo para agrupar por un número determinado de filas.  
  
-   Cuando se coloca en la expresión de grupo, la siguiente expresión asigna a un número a cada conjunto de 25 filas. Cuando se define un salto de página para el grupo, la expresión inserta un salto de página cada 25 filas.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Para que el usuario pueda establecer el número de filas por página, cree un parámetro llamado `RowsPerPage` y base la expresión de grupo en el parámetro, tal y como se muestra en la siguiente expresión:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="Properties"></a> Propiedades  
 Las expresiones no sirven únicamente para mostrar datos en cuadros de texto. También pueden usarse para cambiar cómo se aplican las propiedades a los elementos de informe. Puede cambiar la información de estilo de un elemento de informe o cambiar su visibilidad.  
  
###  <a name="Formatting"></a> Formato  
  
-   Cuando se utiliza en la propiedad Color de un cuadro de texto, la siguiente expresión cambia el color del texto según el valor del campo `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     También puede usar la variable de objeto de Visual Basic `Me`. Esta variable es otra manera de hacer referencia al valor de un cuadro de texto.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   Cuando se utiliza en la propiedad BackgroundColor de un elemento de informe en una región de datos, la siguiente expresión alterna el color de fondo de cada fila entre verde claro y blanco:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Si está utilizando una expresión para un ámbito especificado, deberá indicar el conjunto de datos para la función de agregado:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Los colores disponibles son los de la enumeración KnownColor de .NET Framework.  
  
### <a name="chart-colors"></a>Colores de gráfico  
 Para especificar los colores de un gráfico de forma, puede usar código personalizado para controlar el orden con el que los colores se asignan a los valores de punto de datos. Esto le permitirá usar colores coherentes en distintos gráficos que tengan los mismos grupos de categorías. 
  
###  <a name="Visibility"></a> Visibilidad  
 Puede mostrar y ocultar los elementos de un informe mediante las propiedades de visibilidad del elemento de informe. En una región de datos, como una tabla, puede ocultar inicialmente las filas de detalle en función del valor de una expresión.  
  
-   Cuando se usa para la visibilidad inicial de las filas de detalles de un grupo, la siguiente expresión muestra las filas de detalles de todas las ventas que superen el 90 por ciento en el campo `PctQuota`:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   Cuando se establece en la propiedad Hidden de una tabla, la siguiente expresión muestra la tabla solo si tiene más de 12 filas:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   Cuando se establece en la propiedad **Hidden** de una columna, la siguiente expresión muestra la columna solo si el campo existe en el conjunto de datos de informe después de recuperar los datos del origen de datos:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="Hyperlinks"></a> Direcciones URL  
 Puede personalizar las direcciones URL usando los datos del informe y también puede controlar condicionalmente si las direcciones URL se agregan como una acción para un cuadro de texto.  
  
-   Cuando se usa como una acción en un cuadro de texto, la siguiente expresión genera una dirección URL personalizada que especifica el campo de conjunto de datos `EmployeeID` como un parámetro de URL.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   La expresión siguiente controla de forma condicional si se debe agregar una dirección URL a un cuadro de texto. Esta expresión depende de un parámetro llamado `IncludeURLs` que permite al usuario decidir si desea incluir direcciones URL activas en un informe. Esta expresión se establece como una acción en un cuadro de texto. Para exportar el informe a Microsoft Excel sin hipervínculos, puede establecer el parámetro en False y, a continuación, ver el informe.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="ReportData"></a> Datos del informe  
 Las expresiones pueden usarse para manipular los datos que se incluyen en el informe. Se puede hacer referencia a parámetros y otra información del informe. Puede cambiar incluso la consulta que se usa para recuperar los datos del informe.  
  
###  <a name="Parameters"></a> Parámetros  
 Puede utilizar expresiones en un parámetro para modificar el valor predeterminado del parámetro. Por ejemplo, puede usar un parámetro para filtrar los datos de un usuario determinado basándose en el identificador de usuario utilizado para ejecutar el informe.  
  
-   Cuando se usa como el valor predeterminado de un parámetro, la siguiente expresión recopila el identificador de usuario de la persona que ejecuta el informe:  
  
    ```  
    =User!UserID  
    ```  
  
-   Para hacer referencia a un parámetro en un cuadro de texto, una expresión de filtro, un parámetro de consulta u otra área del informe, use la colección global **Parameters**. En este ejemplo se da por supuesto que el parámetro se llama *Department*:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Los parámetros se pueden crear en un informe y establecerse como ocultos. Cuando se ejecuta el informe en el servidor de informes, el parámetro no aparece en la barra de herramientas y el lector del informe no puede cambiar el valor predeterminado. Puede usar un parámetro oculto establecido en un valor predeterminado como constante personalizada. Puede usar este valor en cualquier expresión, incluida una expresión de campo. La siguiente expresión identifica el campo especificado por el valor predeterminado del parámetro llamado *ParameterField*:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="CustomCode"></a> Código personalizado  
 Puede usar código personalizado insertado en un informe. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Uso de variables de grupo para la agregación personalizada  
 Puede inicializar el valor de una variable de grupo que sea local para ámbito de grupo en particular y, a continuación, incluir una referencia a esa variable en expresiones. Una de las formas que puede usar una variable de grupo con código personalizado es implementar un agregado personalizado. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Supresión de valores null o cero en tiempo de ejecución  
 Algunos valores de una expresión pueden evaluarse como null o no definidos en el momento de procesar el informe. Esto puede provocar errores en tiempo de ejecución que hacen que se muestre **#Error** en el cuadro de texto en lugar de la expresión evaluada. La función **IIF** es especialmente sensible a este comportamiento porque, a diferencia de una instrucción If-Then-Else, se evalúa cada parte de la instrucción **IIF** (incluidas las llamadas de función) antes de pasar a la rutina que comprueba si es **true** o **false**. La instrucción `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` genera **#Error** en el informe representado si `Fields!Sales.Value` es NOTHING.  
  
 Para evitar esta condición, use una de las estrategias siguientes:  
  
-   Establezca el numerador en 0 y el denominador en 1 si el valor deL campo B es 0 o no definido; en caso contrario, establezca el numerador en el valor del campo A y el denominador en el valor del campo B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Use una función de código personalizado para devolver el valor de la expresión. El ejemplo siguiente devuelve la diferencia porcentual entre un valor actual y un valor anterior. Esto puede usarse para calcular la diferencia entre dos valores consecutivos cualesquiera y controla el caso límite de la primera comparación (cuando no hay ningún valor anterior) y los casos en los que el valor anterior o el valor actual es **null** (**Nothing** en Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     La expresión siguiente muestra cómo llamar a este código personalizado desde un cuadro de texto para el contenedor "ColumnGroupByYear" (grupo o región de datos).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Esto ayuda a evitar las excepciones de tiempo de ejecución. Ahora puede usar una expresión como `=IIF(Me.Value < 0, "red", "black")` en la propiedad **Color** del cuadro de texto para mostrar condicionalmente el texto en función de si los valores son mayores o menores que 0.  
  
## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
