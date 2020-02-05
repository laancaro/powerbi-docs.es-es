---
title: Formato de tabla condicional en Power BI Desktop
description: Aplicar formato personalizado a las tablas
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/26/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: c79a8ddd68fa64b0a16663500a3f02e9a991835b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "75730531"
---
# <a name="use-conditional-formatting-in-tables"></a>Uso de formato condicional en tablas 

Con el formato condicional para tablas de Power BI Desktop, puede especificar colores de celda personalizados, incluidos valores según el campo y degradados de color. También puede representar valores de celda con barras de datos o iconos de KPI, o como vínculos web activos. Puede aplicar formato condicional a cualquier campo de texto o de datos, siempre y cuando base el formato en un campo que tenga valores numéricos, de nombre de color o de código hexadecimal, o de URL web. 

Para aplicar formato condicional, seleccione una visualización de **tabla** o **matriz** en Power BI Desktop. En la sección **Campos** del panel **Visualizaciones**, haga clic con el botón derecho o seleccione la flecha abajo situada junto al campo del área **Valores** a la que quiere dar formato. Seleccione **Formato condicional** y elija el tipo de formato que quiere aplicar.

![Menú de formato condicional](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

> [!NOTE]
> Formato condicional invalida los colores de fondo o de fuente personalizados que se aplican a la celda con formato condicional.

Para quitar el formato condicional de una visualización, seleccione **Quitar formato condicional** en el menú desplegable del campo y elija el tipo de formato que va a quitar.

![Menú Quitar formato condicional](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

En estas secciones se describen cada una de las opciones de formato condicional. Puede combinar más de una opción en una sola columna de tabla.

## <a name="format-background-or-font-color"></a>Asignación de formato al color de fondo o de fuente

Para dar formato al fondo o al color de fuente de la celda, seleccione **Formato condicional** en un campo y luego elija **Color de fondo** o **Color de fuente** en el menú desplegable. 

![Selección del color de fondo o el color de fuente](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

Se abre el cuadro de diálogo **Color de fondo** o **Color de fuente** con el nombre del campo al que se va a aplicar formato en el título. Después de seleccionar las opciones de formato condicional, elija **Aceptar**. 

![Cuadros de diálogo Color de fondo y Color de fuente](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

Las opciones **Color de fondo** y **Color de fuente** son las mismas, pero afectan al color de fondo de la celda y al color de fuente, respectivamente. Puede aplicar el mismo u otro formato condicional al color de fuente y al color de fondo de un campo. Si hace que la fuente y el fondo de un campo tengan el mismo color, la fuente se combina en segundo plano, por lo que la columna de la tabla solo muestra los colores.

## <a name="color-by-color-scale"></a>Color por escala de colores

Para cambiar el formato del color de fondo o de fuente de una celda por escala de colores, en el campo **Dar formato por** del cuadro de diálogo **Color de fondo** o **Color de fuente**, seleccione **Escala de colores**. En **Según el campo**, seleccione el campo en el que se basará el formato. Puede basar el formato en el campo actual o en cualquier campo del modelo que tenga datos numéricos o de color. 

En **Resumen**, especifique el tipo de agregación que quiere utilizar para el campo seleccionado. En **Formato predeterminado**, seleccione un formato para aplicarlo a valores en blanco. 

En **Mínimo** y **Máximo**, elija si quiere aplicar la combinación de colores según los valores de los campos Mínimo y Máximo o según valores personalizados que especifique. Despliegue y seleccione los muestrarios de colores que quiere aplicar a los valores mínimo y máximo. Active la casilla **Divergente** para especificar también un valor y un color de **Centro**. 

![Establecimiento del fondo de celda con escala de colores](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

Una tabla de ejemplo con formato de fondo de escala de colores en la columna **Affordability** (Asequibilidad) tiene el siguiente aspecto:

![Tabla de ejemplo con escala de colores de fondo divergentes](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Una tabla de ejemplo con un formato de fuente de escala de colores en la columna **Affordability** (Asequibilidad) tiene el siguiente aspecto:

![Tabla de ejemplo con escala de colores de fuente divergentes](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="color-by-rules"></a>Color según las reglas

Para dar formato al color de fondo o de fuente de la celda según las reglas, en el campo **Dar formato por** del cuadro de diálogo **Color de fondo** o **Color de fuente**, seleccione **Reglas**. De nuevo, en **Según el campo** se muestra el campo en el que se basará el formato y en **Resumen** se muestra el tipo de agregación del campo. 

En **Reglas**, escriba uno o varios intervalos de valores y establezca un color para cada uno. Cada intervalo de valor tiene una condición *Si el valor*, una condición de valor *Y* y un color. Los fondos o las fuentes de celda de cada intervalo de valores están coloreados con el color especificado. En el ejemplo siguiente se crean tres reglas:

![Color según las reglas](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Una tabla de ejemplo con formato de color de fondo basado en reglas en la columna **Affordability** (Asequibilidad) tiene el siguiente aspecto:

![Tabla de ejemplo con color por reglas](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)

## <a name="color-by-color-values"></a>Color por valores de color

Si tiene un campo o una medida con datos de nombre de color o de valor hexadecimal, puede usar el formato condicional para aplicar automáticamente esos colores al color de fondo o de fuente de una columna. También puede usar lógica personalizada para aplicar colores a la fuente o al fondo.

En el campo se pueden utilizar los valores de color que aparecen en la especificación CSS de colores en [https://www.w3.org/TR/css-color-3/](https://www.w3.org/TR/css-color-3/). Estos valores de color pueden incluir:
- Códigos hexadecimales de 3, 6 u 8 dígitos, por ejemplo #3E4AFF. Asegúrese de incluir el símbolo # al principio del código. 
- Valores RGB o RGBA como, por ejemplo, RGBA(234, 234, 234, 0,5).
- Valores HSL o HSLA como, por ejemplo, HSLA(123, 75 %, 75 %, 0,5).
- Nombres de colores tales como Green, SkyBlue o PeachPuff. 

La tabla siguiente incluye un nombre de color asociado a cada Estado: 

![Tabla de estado con nombres de colores](media/desktop-conditional-table-formatting/conditional-table-formatting_01.png)

Para dar formato a la columna **Color** según sus valores de campo, seleccione **Formato condicional** en el campo **Color** y luego elija **Color de fondo** o **Color de fuente**. 

En el cuadro de diálogo **Color de fondo** o **Color de fuente**, seleccione **Valor del campo** en el campo desplegable **Dar formato por**.

![Valor de campo Dar formato por](media/desktop-conditional-table-formatting/conditional-table-formatting_02.png)

Una tabla de ejemplo con formato **Color de fondo** basado en el valor del campo **Color** tiene el siguiente aspecto:

![Tabla de ejemplo con formato de fondo por valor de campo](media/desktop-conditional-table-formatting/conditional-table-formatting_03.png)

Si también utiliza **Valor de campo** para dar formato al **Color de fuente** de la columna, el resultado es un color sólido en la columna **Color**:

![Asignación de formato y de fuente al fondo por valor de campo](media/desktop-conditional-table-formatting/conditional-table-formatting_04.png)

## <a name="color-based-on-a-calculation"></a>Color basado en un cálculo

Puede crear un cálculo DAX que genere diferentes valores basados en condiciones de la lógica de negocios que seleccione. La creación de una fórmula DAX suele ser más rápida que la creación de varias reglas en el cuadro de diálogo de formato condicional. 

Por ejemplo, la siguiente fórmula DAX aplica valores de color hexadecimales a una nueva columna **Affordability rank** (Rango de asequibilidad), según los valores existentes en la columna **Affordability** (Asequibilidad):

![Cálculo DAX](media/desktop-conditional-table-formatting/conditional-table-formatting_05.png)

Para aplicar los colores, seleccione formato condicional de **Color de fondo** o **Color de fuente** para la columna **Affordability** (Asequibilidad), y base el formato en el **Valor de campo** de la columna **Affordability rank** (Rango de asequibilidad). 

![Color de fondo base de una columna calculada](media/desktop-conditional-table-formatting/conditional-table-formatting_06.png)

La tabla de ejemplo con el color de fondo de **Affordability** (Asequibilidad) en función del **Affordability rank** (Rango de asequibilidad) tiene el siguiente aspecto:

![Tabla de ejemplo con un color basado en valores calculados](media/desktop-conditional-table-formatting/conditional-table-formatting_07.png)

Puede crear muchas variaciones más tan solo con su imaginación y un poco de DAX.

## <a name="add-data-bars"></a>Adición de barras de datos

Para mostrar barras de datos basadas en valores de celda, seleccione **Formato condicional** en el campo **Affordability** (Asequibilidad) y luego elija **Barras de datos** en el menú desplegable. 

En el cuadro de diálogo **Barras de datos**, la opción **Show bar only** (Mostrar solo la barra) está desactivada de forma predeterminada, por lo que las celdas de tabla muestran las barras y los valores reales. Para mostrar solo las barras de datos, active la casilla **Show bar only** (Mostrar solo la barra).

Puede especificar valores **mínimos** y **máximos**, la dirección y los colores de la barra de datos, y el color del eje. 

![Cuadro de diálogo Barras de datos](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Al aplicar barras de datos a la columna **Affordability** (Asequibilidad), la tabla de ejemplo tiene el siguiente aspecto:

![Tabla de ejemplo con barras de datos](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)

## <a name="add-icons"></a>Adición de iconos

Para mostrar iconos basados en valores de celda, seleccione **Formato condicional** en el campo y luego elija **Iconos** en el menú desplegable. 

En el cuadro de diálogo **Iconos**, en **Dar formato por**, seleccione **Reglas** o **Valor de campo**. 

Para aplicar formato según las reglas, seleccione el método **Según el campo** o **Resumen**, **Diseño de los iconos**, **Alineación de los iconos**, icono **Estilo** y una o más **Reglas**. En **Reglas**, escriba una o varias reglas con una condición *Si el valor* y una condición de valor *Y*, y seleccione un icono para aplicar a cada regla. 

Para aplicar formato por valores de campo, seleccione el método **Según el campo** o **Resumen**, **Diseño de los iconos** y **Alineación de los iconos**.

En el ejemplo siguiente se agregan iconos basados en tres reglas:

![Cuadro de diálogo iconos](media/desktop-conditional-table-formatting/table-formatting-1-default-table.png)

Seleccione **Aceptar**. Al aplicar iconos a la columna **Affordability** (Asequibilidad) según las reglas, la tabla de ejemplo tiene el siguiente aspecto:

![Tabla de ejemplo con iconos](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

## <a name="format-as-web-urls"></a>Asignación de formato como direcciones URL web

Si tiene una columna o una medida que contiene direcciones URL de sitios web, puede usar el formato condicional para aplicar dichas direcciones URL a los campos como vínculos activos. Por ejemplo, la tabla siguiente tiene una columna **Sitio web** con direcciones URL de sitios web para cada estado:

![Tabla con columna de dirección URL web](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

Para mostrar el nombre de cada estado como vínculo dinámico al sitio web, seleccione **Formato condicional** en el campo**Estado** y elija **Dirección URL web**. En el cuadro de diálogo **Dirección URL web**, en **Según el campo**, seleccione **Sitio web** y luego elija **Aceptar**. 

Al aplicar el formato **URL web** al campo **Estado**, el nombre de cada estado es un vínculo activo al sitio web. En la siguiente tabla de ejemplo se ha aplicado el formato **URL web** a la columna **Estado** y el formato condicional **Barras de datos** y **Background formatting** (Formato de fondo) a la columna **Affordability** (Asequibilidad). 

![Tabla con dirección URL web, barras de datos y color de fondo](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones
Hay algunas consideraciones que tener en cuenta al trabajar con el formato condicional de tabla:

- El formato condicional solo se aplica a los valores de objetos visuales Tabla o Matriz, y no a los subtotales, los totales generales o la fila **Total**. 
- Las tablas que no tengan una agrupación se muestran como una sola fila que no admite el formato condicional.
- No se puede aplicar formato de degradado con valores máximos y mínimos automáticos, ni un formato basado en reglas con reglas de porcentaje, si los datos contienen valores *NaN*. NaN significa "no es un número", lo que suele deberse a un error de división entre cero. Se puede usar la [función DIVIDE() DAX](https://docs.microsoft.com/dax/divide-function-dax) para evitar estos errores.
- El formato condicional requiere que se aplique una agregación o una medida al valor. Es por eso que se ve "Primero" o "Último"' en el ejemplo de **Color por valor**. Si va a crear un informe en un cubo multidimensional de Analysis Services, no podrá utilizar un atributo para el formato condicional a menos que el propietario del cubo haya generado una medida que proporcione el valor.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre formatos de color, vea [Sugerencias y trucos para el formato de color en Power BI](visuals/service-tips-and-tricks-for-color-formatting.md).  

