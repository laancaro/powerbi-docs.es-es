---
title: Medidas en Power BI Desktop
description: Creación y uso de medidas en Power BI Desktop tales como medidas rápidas y sintaxis DAX
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9c181deb4e36624fa714242583e3fe209abdfb47
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2020
ms.locfileid: "76889337"
---
# <a name="create-measures-for-data-analysis-in-power-bi-desktop"></a>Creación de medidas para el análisis de datos en Power BI Desktop

Power BI Desktop le ayuda a crear información sobre sus datos en unos cuantos clics. Pero a veces los datos simplemente no incluyen todo lo que necesita para responder algunas de las preguntas más importantes. En esos casos, las medidas pueden ser de ayuda.

Las medidas se usan en algunos de los análisis de datos más comunes. Los resúmenes simples, como sumas, promedios, mínimo, máximo y recuentos, también se pueden establecer a través del área **Campos**. Los resultados calculados de las medidas cambian constantemente en respuesta a la interacción con los informes, lo que permite la exploración rápida y dinámica de datos ad hoc. Analicemos la cuestión más detenidamente. Para más información, vea [Creación de medidas calculadas](/learn/modules/model-data-power-bi/4b-create-calculated-measures).

## <a name="understanding-measures"></a>Descripción de las medidas

En Power BI Desktop, las medidas se crean y muestran en *Vista de informes* o *Vista de datos*. Las medidas que se creen aparecerán en la lista **Campos** con un icono de calculadora. Puede asignar el nombre que desee a las medidas y agregarlas a una visualización nueva o existente como cualquier otro campo.

![Campos de medida en Campos](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Quizá también esté interesado en las *medidas rápidas*, medidas listas para usar que puede seleccionar en los cuadros de diálogo. Son una buena manera de crear medidas rápidamente y de aprender a usar la sintaxis de expresiones de análisis de datos (DAX), ya que se trata de fórmulas DAX creadas automáticamente que están disponibles para su revisión. Para obtener más información, vea el artículo sobre [medidas rápidas](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Expresiones de análisis de datos

Las medidas calculan un resultado a partir de una fórmula de expresiones. Al crear sus propias medidas, debe usar el lenguaje de fórmulas de [expresiones de análisis de datos](/dax/) (DAX). DAX incluye una biblioteca de más de 200 funciones, operadores y construcciones. Su biblioteca ofrece una gran flexibilidad al momento de crear medidas para calcular los resultados de casi cualquier necesidad de análisis de datos.

Las fórmulas DAX son muy similares a las fórmulas de Excel. DAX tiene incluso muchas de las mismas funciones que Excel, tales como `DATE`, `SUM` y `LEFT`. Sin embargo, las funciones DAX están diseñadas para trabajar con datos relacionales como los que tenemos en Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Veamos un ejemplo

Jan es jefa de ventas de Contoso. Le han pedido que presente los pronósticos de ventas de los revendedores para el próximo año fiscal. Jan decide que basará las estimaciones en las cifras de ventas del año pasado, agregando un seis por ciento anual, resultante de las distintas promociones programadas para los próximos seis meses.

Para informar de las estimaciones, Jan importa datos de las ventas del año pasado en Power BI Desktop. Busca el campo **SalesAmount** de la tabla **Venta del distribuidor**. Debido a que los datos importados solo contienen los importes de las ventas del año pasado, Jan cambia el nombre del campo **SalesAmount** a *Ventas de los últimos años*. Después, Jan arrastra el campo **Ventas de los últimos años** al lienzo del informe. Aparece en una visualización de gráfico como un valor único, que es la suma de las ventas de todos los distribuidores durante el año pasado.

Jan se da cuenta de que, aunque no ha especificado ningún cálculo, se ha facilitado uno automáticamente. Power BI Desktop creó su propia medida con la suma de todos los valores de **Ventas de los últimos años**.

Sin embargo, Jan necesita una medida para calcular las previsiones de ventas para el año siguiente, que se basarán en las ventas del año anterior multiplicadas por 1,06 para tener en cuenta el aumento del 6 % previsto en los negocios. Para este cálculo, Jan creará su propia medida. Mediante la característica *Nueva medida*, crea otra medida y luego escribe la siguiente fórmula DAX:

```sql
    Projected Sales = SUM('Sales'[Last Years Sales])*1.06
```

Después Jan arrastra la nueva medida Ventas previstas hasta el gráfico.

![Nuevos objetos visuales de ventas previstas](media/desktop-measures/measuresinpbid_lastyearsales.png)

Rápidamente y con el mínimo esfuerzo, ahora Jan tiene una medida para calcular las ventas previstas. Jan puede analizar con más detalle los pronósticos al filtrar por revendedores específicos o agregar otros campos al informe.

## <a name="data-categories-for-measures"></a>Categorías de datos de medidas

También puede elegir categorías de datos de medidas.

Entre otras cosas, estas categorías de datos le permiten usar medidas para crear direcciones URL de forma dinámica y marcar la categoría de datos como URL web.

Puede crear tablas que muestren las medidas como URL web y en las que pueda hacer clic en la dirección URL que se crea según su selección. Esto es especialmente útil si quiere establecer vínculos con otros informes de Power BI con [parámetros de filtro de URL](service-url-filters.md).

## <a name="organizing-your-measures"></a>Organización de las medidas

Las medidas tienen una tabla *Inicio* que define dónde se encuentran en la lista de campos. Puede cambiar su ubicación eligiendo una ubicación de las tablas en el modelo.

![Selección de una tabla para la medida](media/desktop-measures/measures-03.png)

También puede organizar los campos de una tabla en *carpetas para mostrar*. Seleccione **Modelo** en el margen izquierdo de la ventana de Power BI Desktop. En el panel **Propiedades**, seleccione el campo que quiere mover de la lista de campos disponibles. Escriba el nombre de una nueva carpeta en **Carpeta para mostrar** para crear una carpeta. Al crear una carpeta, el campo seleccionado se mueve a esa carpeta.

![Creación de un campo para las medidas](media/desktop-measures/measures-04.gif)

Puede crear subcarpetas mediante un carácter de barra diagonal inversa. Por ejemplo *Finance\Currencies* crea una carpeta *Finance* y, dentro de ella, una carpeta *Currencies*.

Puede hacer que un campo aparezca en varias carpetas mediante un punto y coma para separar los nombres de carpeta. Por ejemplo, *Products\Names;Departments* hace que el campo aparezca en una carpeta *Departments*, así como en una carpeta *Names* dentro de una carpeta *Products*.

Puede crear una tabla especial que solo contenga medidas. Esa tabla siempre aparece en la parte superior de la lista **Campos**. Para ello, cree una tabla con una sola columna. Puede usar **Especificar datos** para crear esa tabla. Luego, mueva las medidas a esa tabla. Por último, oculte la columna (no la tabla) que creó. Seleccione la flecha situada en la parte superior de **Campos** para cerrar y volver a abrir la lista de campos para ver los cambios.

![Organización de medidas y mantenerlas en la parte superior de la lista de campos](media/desktop-measures/measures-05.png)

## <a name="learn-more"></a>Más información

Aquí solo ofrecemos una breve introducción a las medidas. Hay mucho más para ayudarle a aprender a crear las suyas propias. Para más información, consulte el [Tutorial: Creación de medidas propias en Power BI Desktop](desktop-tutorial-create-measures.md). Puede descargar un archivo de ejemplo y obtener lecciones paso a paso sobre cómo crear otras medidas.  

Para profundizar un poco más en DAX, vea [Aspectos básicos de DAX en Power BI Desktop](desktop-quickstart-learn-dax-basics.md). La [referencia de expresiones de análisis de datos](/dax/) proporciona artículos detallados sobre cada una de las funciones, la sintaxis, los operadores y las convenciones de nomenclatura. DAX lleva varios años en Power Pivot en Excel y SQL Server Analysis Services. También hay muchos otros excelentes recursos disponibles. Asegúrese de revisar el [wiki del centro de recursos de DAX](https://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), donde miembros destacados de la comunidad de BI comparten sus conocimientos sobre DAX.
