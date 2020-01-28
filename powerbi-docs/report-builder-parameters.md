---
title: Parámetros de informe en el Generador de informes de Power BI
description: En este tema se describen los usos comunes de los parámetros de informe del Generador de informes de Power BI, las propiedades que puede establecer y mucho más.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/06/2019
ms.openlocfilehash: 5a7e91c03b11902f324d6a7c639a03f7652acf16
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160866"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Parámetros de informe en el Generador de informes de Power BI

En este tema se describen los usos comunes de los parámetros de informe del Generador de informes de Power BI, las propiedades que puede establecer y mucho más. Con los parámetros de informe, puede controlar los datos del informe, conectar informes relacionados y variar la presentación del informe. Puede usar los parámetros de informe en informes paginados que cree en el Generador de informes.

## <a name="bkmk_Common_Uses_for_Parameters"></a> Usos comunes de los parámetros

 Estos son algunos de los usos más comunes de los parámetros.  
  
**Control de los datos de informes paginados**
  
- Para filtrar los datos del informe paginado en el origen de datos, escriba consultas de conjunto de datos que contengan variables.  
  
- Permita que los usuarios puedan especificar valores para personalizar los datos de un informe paginado. Por ejemplo, proporcione dos parámetros de fecha de inicio y fecha de finalización para los datos de ventas.  
  
**Cambiar la presentación de los informes**
  
- Permita que los usuarios puedan especificar valores para ayudar a personalizar la apariencia de un informe. Por ejemplo, proporcione un parámetro booleano para indicar si se deben expandir o contraer todos los grupos de filas anidados en una tabla.  
  
- Incluya parámetros en una expresión para que los usuarios puedan personalizar la apariencia y los datos del informe.  
  
## <a name="UserInterface"></a> Ver un informe con parámetros

Al ver un informe que tiene parámetros, la barra de herramientas del visor de informes muestra cada parámetro para especificar valores de forma interactiva. La siguiente ilustración muestra el área de parámetros de un informe con los parámetros @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota y @SalesDate.  

![Ver un informe con parámetros](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Ver un informe con parámetros")
  
1. **Panel de parámetros** La barra de herramientas del visor de informes muestra un aviso y un valor predeterminado para cada parámetro. Puede personalizar el diseño de parámetros en el panel de parámetros.  
  
2. **@SalesDate parámetro** el parámetro @SalesDate es de tipo de datos **DateTime**. El mensaje Seleccione la fecha aparece junto al cuadro de texto. Para modificar la fecha, escriba una nueva fecha en el cuadro de texto o utilice el control de calendario.  
  
3. **@ShowAll parámetro** el parámetro @ShowAll es de tipo de datos **booleano**. Use los botones de radio para especificar **True** o **False**.  
  
4. **Control Mostrar u ocultar el área de parámetros** En la barra de herramientas del visor de informes, haga clic en esta flecha para mostrar u ocultar el panel de parámetros.  
  
5. **@CategoryQuota parámetro** el parámetro @CategoryQuota es de tipo de datos **Float**, por lo que tendrá un valor numérico.  @CategoryQuota está establecido para permitir varios valores.  
  
6. **Ver informe** Después de escribir los valores de los parámetros, haga clic en **Ver informe** para ejecutar el informe. Si todos los parámetros tienen valores predeterminados, el informe se ejecuta automáticamente en la primera vista.  
  
## <a name="bkmk_Create_Parameters"></a> Creación de parámetros

Puede crear parámetros de informe de varias maneras diferentes.
  
> [!NOTE]
>  No todos los orígenes de datos admiten parámetros.
  
**Consulta o procedimiento almacenado de conjunto de datos con parámetros**
  
 Agregue una consulta de conjunto de datos que contenga variables o un procedimiento almacenado de conjunto de datos que contenga parámetros de entrada. Se crea un parámetro de conjunto de datos para cada variable o parámetro de entrada, y se crea un parámetro de informe para cada parámetro de conjunto de datos.  
  
![Propiedades del conjunto de datos de parámetros del Generador de informes](media/report-builder-parameters/report-builder-parameter-dataset.png "Propiedades del conjunto de datos de parámetros del Generador de informes")

  
 Esta imagen del Generador de informes muestra:  
  
1.  Los parámetros de informe en el panel Datos de informe.  
  
2.  El conjunto de datos con los parámetros.  
  
3.  El panel Parámetros.  
  
4.  Los parámetros enumerados en el cuadro de diálogo Propiedades del conjunto de datos.  
  
**Crear un parámetro manualmente**
  
Cree un parámetro manualmente en el panel Datos de informe. Puede configurar los parámetros de informe para que un usuario pueda escribir valores de forma interactiva para ayudar a personalizar el contenido o la apariencia de un informe. También puede configurar los parámetros de informe para que un usuario no pueda cambiar los valores preconfigurados.  
  
> [!NOTE]  
>  Dado que los parámetros se administran de forma independiente en el servidor, al volver a publicar un informe principal con la nueva configuración de los parámetros no se sobrescribe la configuración de los parámetros existente en el informe.  

### <a name="parameter-values"></a>Valores de parámetro

 Las siguientes opciones permiten seleccionar los valores de los parámetro del informe.  
  
- Seleccione un solo valor de parámetro en una lista desplegable.  
  
- Seleccione varios valores de parámetro en una lista desplegable.  
  
- Seleccione un valor en una lista desplegable para un parámetro, que determina los valores que habrá disponibles en la lista desplegable de otro parámetro. Estos son parámetros en cascada. Los parámetros en cascada permiten filtrar sucesivamente los valores de parámetro para reducir de miles de valores a números manejables. Para obtener más información, consulte [Uso de parámetros en cascada en informes paginados](guidance/paginated-report-cascading-parameter.md).
  
- Ejecute el informe sin tener que seleccionar un valor de parámetro porque se ha creado un valor predeterminado para el parámetro.  
  
## <a name="bkmk_Report_Parameters"></a> Propiedades de parámetros de informe

 Puede cambiar las propiedades de los parámetros de informe con el cuadro de diálogo Propiedades del informe. En la tabla siguiente se resumen las propiedades que se pueden establecer para cada parámetro:  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Nombre|Escriba un nombre para el parámetro, que distingue mayúsculas de minúsculas. El nombre debe comenzar con una letra y puede tener letras, números y un carácter de subrayado (_). El nombre no puede tener espacios. Para los parámetros generados automáticamente, el nombre coincide con el parámetro de la consulta de conjunto de datos. De forma predeterminada, los parámetros creados manualmente son similares a ReportParameter1.|  
|Pedir confirmación|El texto que aparece junto al parámetro en la barra de herramientas del visor de informes.|  
|Tipo de datos|Un parámetro de informe debe ser uno de los siguientes tipos de datos:<br /><br /> **Booleano**. El usuario selecciona True o False con un botón de radio.<br /><br /> **Fecha y hora**. El usuario selecciona una fecha en un control de calendario.<br /><br /> **Entero**. El usuario escribe valores en un cuadro de texto.<br /><br /> **Flotante**. El usuario escribe valores en un cuadro de texto.<br /><br /> **Texto**. El usuario escribe valores en un cuadro de texto.<br /><br /> Cuando se definen los valores disponibles para un parámetro, el usuario elige los valores en una lista desplegable, aunque cuando el tipo de datos sea **DateTime**.|  
|Permitir valores en blanco|Seleccione esta opción si el valor del parámetro puede ser una cadena vacía o un valor en blanco.<br /><br /> Si especifica los valores válidos de un parámetro y quiere que uno de los valores válidos sea un valor en blanco, debe incluirlo como uno de los valores que especifique. Al seleccionar esta opción no se incluye automáticamente un espacio en blanco en los valores disponibles.|  
|Permitir valor null|Seleccione esta opción si el valor del parámetro puede ser un valor null.<br /><br /> Si especifica los valores válidos de un parámetro y quiere que null sea uno de los valores válidos, debe incluir null como uno de los valores que especifique. Al seleccionar esta opción no incluye automáticamente un valor null en los valores disponibles.|  
|Permitir varios valores|Proporcione los valores disponibles para crear una lista desplegable en la que los usuarios puedan elegir. Esta es una buena forma de asegurarse de que solo se enviarán valores válidos en la consulta de conjunto de datos.<br /><br /> Seleccione esta opción si el valor del parámetro puede ser varios valores que se muestran en una lista desplegable. No se permiten valores null Cuando se selecciona esta opción, se agregan casillas a la lista de valores disponibles en una lista desplegable de parámetros. La parte superior de la lista incluye una casilla de verificación **Seleccionar todo**. Los usuarios pueden seleccionar los valores que deseen.<br /><br /> Si los datos que proporcionan los valores cambian rápidamente, la lista que ve el usuario podría no ser la más actual.|  
|Visible|Seleccione esta opción para mostrar el parámetro de informe en la parte superior del informe cuando se ejecute. Esta opción permite a los usuarios seleccionar valores de parámetro en tiempo de ejecución.|  
|Oculto|Seleccione esta opción para ocultar el parámetro de informe en el informe publicado. Los valores del parámetro de informe se pueden establecer en una dirección URL del informe, en una definición de suscripción o en el servidor de informes.|  
|Interno|Seleccione esta opción para ocultar el parámetro de informe. El parámetro de informe solo puede verse en la definición de informe, en el informe publicado.|  
|Valores disponibles|Si ha especificado los valores disponibles para un parámetro, los valores válidos siempre aparecen como una lista desplegable. Por ejemplo, si proporciona los valores disponibles para un parámetro **DateTime**, aparece una lista desplegable con fechas en el panel de parámetros en lugar de un control de calendario.<br /><br /> Para asegurarse de que una lista de valores sea coherente en un informe y los subinformes, puede establecer una opción en el origen de datos para utilizar una sola transacción para todas las consultas de los conjuntos de datos que están asociados con un origen de datos.<br /><br /> **Nota de seguridad** En cualquier informe que incluya un parámetro del tipo de datos **Texto**, asegúrese de utilizar una lista de valores disponibles (también conocida como lista de valores válidos) y asegúrese de que los usuarios que ejecuten el informe tengan solo los permisos necesarios para ver los datos en el informe.|  
|Valores predeterminados|Establezca los valores predeterminados de una consulta o una lista estática.<br /><br /> Si todos los parámetros tienen valores predeterminados, el informe se ejecuta automáticamente en la primera vista.|  
|Opciones avanzadas|Establezca el atributo de definición de informe **UsedInQuery**, un valor que indica si este parámetro afecta directa o indirectamente a los datos de un informe.<br /><br /> **Determinar automáticamente cuándo actualizar**<br /> Elija esta opción si desea que el procesador de informes determine la configuración de este valor. El valor es **True** si el procesador de informes detecta una consulta de conjunto de datos con una referencia directa o indirecta a este parámetro, o si el informe tiene subinformes.<br /><br /> **Actualizar siempre**<br /> Elija esta opción cuando el parámetro de informe se use directa o indirectamente en una expresión de consulta o parámetro de conjunto de datos. Esta opción establece **UsedInQuery** en True.<br /><br /> **No actualizar nunca**<br /> Elija esta opción cuando el parámetro de informe no se use directa o indirectamente en una expresión de consulta o parámetro de conjunto de datos. Esta opción establece **UsedInQuery** en False.<br /><br /> **Precaución** Use **No actualizar nunca** con precaución. En el servidor de informes, **UsedInQuery** se usa para ayudar a controlar las opciones de caché para los datos del informe y para los informes representados, así como las opciones de parámetros para informes de instantáneas. Si no establece **No actualizar nunca** correctamente, podría hacer que se almacenen en caché los informes o datos de informe incorrectos, o provocar que un informe de instantánea tenga datos incoherentes. |  
  
##  <a name="bkmk_Dataset_Parameters"></a> Consulta de conjunto de datos  
 Para filtrar los datos de la consulta de conjunto de datos, puede especificar los valores que se incluirán o excluirán del conjunto de resultados en una cláusula de restricción que limita los datos recuperados.  
  
 Utilice el diseñador de consultas con el origen de datos para crear una consulta parametrizada.  
  
-   Para las consultas de Transact-SQL, los diferentes orígenes de datos admiten una sintaxis diferente para los parámetros. Admite intervalos de parámetros que se identifican en la consulta por posición o por nombre. En el diseñador de consultas relacionales, debe seleccionar la opción de parámetro para un filtro para crear una consulta parametrizada.   
  
-   En el caso de las consultas que se basan en un origen de datos multidimensional, como Microsoft SQL Server Analysis Services, puede especificar si se debe crear un parámetro basado en un filtro especificado en el diseñador de consultas. 
  
##  <a name="bkmk_Manage_Parameters"></a> Administración de parámetros para un informe publicado  
 Cuando se diseña un informe, los parámetros de informe se guardan en la definición de informe. Al publicar un informe, los parámetros de informe se guardan y se administran por separado de la definición de informe.  
  
 Para un informe publicado, puede utilizar lo siguiente:  
  
-   **Propiedades de parámetros de informe**. Cambie los valores de parámetro de informe directamente en el servidor de informes, independientemente de la definición de informe.  
  
-   **Suscripciones de informes**. Puede especificar valores de parámetro para filtrar los datos y entregar los informes mediante suscripciones. 
  
 Las propiedades de parámetro de un informe publicado se conservan si vuelve a publicar la definición de informe. Si se vuelve a publicar la definición de informe como el mismo informe, y los tipos de datos y los nombres de parámetro siguen siendo los mismos, se conservan los valores de las propiedades. Si agrega o elimina parámetros de la definición de informe o cambia el nombre o el tipo de datos de un parámetro existente, deberá cambiar las propiedades del parámetro en el informe publicado.  
  
 No todos los parámetros pueden modificarse en todos los casos. Si un parámetro de informe obtiene un valor predeterminado de una consulta de conjunto de datos, ese valor no se puede modificar para un informe publicado y no se puede modificar en el servidor de informes. El valor que se usa en tiempo de ejecución se determina cuando se ejecuta la consulta o, en el caso de los parámetros basados en una expresión, cuando se evalúa la expresión.  
  
 Las opciones de ejecución de informes pueden afectar a cómo se procesan los parámetros. Un informe que se ejecuta como una instantánea no puede usar los parámetros que se derivan de una consulta, a menos que la consulta incluya los valores predeterminados para los parámetros.  
  
##  <a name="bkmk_Parameters_Subscription"></a> Parámetros de una suscripción  
 Puede definir una suscripción para una instantánea o un informe a petición, y especificar los valores de parámetro que se usarán durante el procesamiento de la suscripción.  
  
-   **Informes a petición**.  En el caso de un informe a petición, puede especificar un valor de parámetro diferente al valor publicado para cada parámetro indicado en el informe. Por ejemplo, suponga que tiene un informe de llamadas de servicio que utiliza el parámetro *Período de tiempo* para devolver las solicitudes de servicio al cliente del día, la semana o el mes. Si el valor de parámetro predeterminado para el informe se establece en **Hoy**, la suscripción puede usar un valor de parámetro diferente (como **semana** o **mes**) para generar un informe que contenga cifras semanales o mensuales.  
  
## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Uso de parámetros en cascada en informes paginados](guidance/paginated-report-cascading-parameter.md)
