---
title: Trabajar con agregados (suma, promedio etc.) en el servicio Power BI
description: Obtenga información sobre cómo cambiar la agregación de un gráfico (suma, promedio, máximo y así sucesivamente.) en el servicio Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710668"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Trabajar con agregados (suma, promedio etc.) en el servicio Power BI

## <a name="what-is-an-aggregate"></a>¿Qué es un agregado?

A veces, querrá combinar matemáticamente los valores de los datos. La operación matemática podría ser suma, promedio, máximo, recuento y así sucesivamente. Cuando se combinan los valores de los datos, se llama a *agregación*. El resultado de esa operación matemática es un *agregado*.

Cuando el servicio Power BI y Power BI Desktop crean las visualizaciones, pueden agregar los datos. A menudo el agregado es exactamente lo que necesita, pero en otras ocasiones deseará agregar los valores de forma diferente.  Por ejemplo, una suma frente a una media. Hay varias formas de administrar y cambiar el agregado de que Power BI usa en una visualización.

En primer lugar, echemos un vistazo a los datos *tipos* porque el tipo de datos determina cómo y si, Power BI puede agregarla.

## <a name="types-of-data"></a>Tipos de datos

La mayoría de los conjuntos de datos tienen más de un tipo de datos. En el nivel más básico, los datos son valores numéricos o no está. Power BI puede agregar datos numéricos con una suma, promedio, recuento, mínimo, varianza y mucho más. El servicio incluso puede acumular datos textuales, a menudo denominadas *categorías* datos. Si intenta agregar un campo de categoría y colocarla en un depósito solo numérico como **valores** o **informaciones sobre herramientas**, Power BI se contar las apariciones de cada categoría o contar las apariciones distintas de cada uno categoría. Tipos especiales de datos, como las fechas, tienen algunas de sus propias opciones de agregado: más antiguo, más reciente, primero y último.

En el ejemplo siguiente:

- **Units Sold** y **Manufacturing Price** son columnas que contienen datos numéricos

- **Segment**, **Country**, **Product**, **Month** y **Month Name** contienen datos de categorías

   ![Captura de pantalla de un conjunto de datos de ejemplo.](media/service-aggregates/power-bi-aggregate-chart.png)

Al crear una visualización en Power BI, el servicio realizará la agregación de los campos numéricos (el valor predeterminado es *suma*) a través de algún campo de categoría.  Por ejemplo, "unidades vendidas ***por producto***", "unidades vendidas ***por mes***" y "Manufacturing Price ***por segmento***". Power BI hace referencia a algunos campos numéricos como **medidas**. Es fácil identificar las medidas en el editor de informes de Power BI--el **campos** lista muestra las medidas con el símbolo ∑ junto a ellos. Consulte [el editor de informes... un paseo](service-the-report-editor-take-a-tour.md) para obtener más información.

![Captura de pantalla de Power BI con la lista de campos que se mencionan.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>¿Por qué los agregados no funcionan como quiero?

Trabajar con agregados en Power BI service puede resultar confuso. Quizá tenga un campo numérico y Power BI no le permitirá cambiar la agregación. O quizá tenga un campo, como un año, y no desea agregarlo sino que desea contar el número de repeticiones.

Normalmente, el problema subyacente es la definición de campo del conjunto de datos. Quizás el propietario del conjunto de datos definido por el campo como texto y explica por qué no se puede sumar o valor medio, Power BI. Por desgracia, [solo el propietario del conjunto de datos puede cambiar la manera en que se clasifica un campo](desktop-measures.md). Por lo que si tiene permisos de propietario para el conjunto de datos, en el escritorio o el programa usado para crear el conjunto de datos (por ejemplo, Excel), puede corregir este problema. En caso contrario, debe ponerse en contacto con el propietario del conjunto de datos para obtener ayuda.  

Hay una sección especial al final de este artículo titulada [ **consideraciones y solución de problemas**](#considerations-and-troubleshooting). Proporciona orientación y sugerencias. Si no encuentra la respuesta en esa sección, publique su pregunta en el [foro de comunidad de Power BI](http://community.powerbi.com). Obtendrá una respuesta rápida directamente desde el equipo de Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Cambiar el modo en que un campo numérico se agrega

Supongamos que tiene un gráfico que suma las unidades vendidas de los distintos productos, pero prefiere disponer de la media.

1. Crear un **gráfico de columnas agrupadas** que usa una medida y una categoría. En este ejemplo Units Sold by Product.  De forma predeterminada, Power BI crea un gráfico que suma las unidades vendidas (arrastre la medida en el **valor** bien) para cada producto (arrastre la categoría en la **eje** bien).

   ![Captura de pantalla del gráfico, panel visualizaciones y lista de campos con suma mencionada.](media/service-aggregates/power-bi-aggregate-sum.png)

1. En el **visualizaciones** panel, haga clic en la medida y seleccione el tipo agregado que necesita. En este caso, seleccionamos **promedio**. Si no ve la agregación que necesita, consulte el [ **consideraciones y solución de problemas** ](#considerations-and-troubleshooting) sección.

   ![Captura de pantalla de la lista de agregados con Media seleccionado y mencionadas.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > Las opciones disponibles en la lista desplegable varían según (1) el campo seleccionado y 2) la manera en que el propietario del conjunto de datos clasificados ese campo.

1. La visualización ahora está usando una agregación por la media.

   ![Captura de pantalla del gráfico ahora muestra el promedio de unidades vendidas por producto.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Formas de agregar los datos

Algunas de las opciones que pueden estar disponibles para agregar un campo:

- **No resumir**. Elige esta opción, Power BI trata cada valor en ese campo por separado y no resumirlos. Use esta opción si tiene una columna de identificador numérica que no debe sumar el servicio.

- **Suma**. Suma todos los valores de ese campo.

- **Media**. Calcula la media aritmética de los valores.

- **Mínimo**. Muestra el valor menor.

- **Máximo**. Muestra el valor mayor.

- **Recuento (no vacíos).** Cuenta el número de valores de ese campo que no están en blanco.

- **Recuento (Distinct).** Cuenta el número de valores diferentes en ese campo.

- **Desviación estándar.**

- **Varianza**.

- **Mediana**.  Muestra el valor de la mediana (intermedio). Este valor tiene el mismo número de elementos por encima que por debajo.  Si hay dos medianas, Power BI calcula su promedio.

Por ejemplo, estos datos:

| País | Cantidad |
|:--- |:--- |
| Estados Unidos |100 |
| Reino Unido |150 |
| Canadá |100 |
| Alemania |125 |
| Francia | |
| Japón |125 |
| Australia |150 |

Arrojarían estos resultados:

- **No resumir**: cada valor se muestra por separado

- **Suma**: 750

- **Media**: 125

- **Máximo**:  150

- **Mínimo**: 100

- **Recuento (no vacíos):** 6

- **Recuento (distinto)** 4

- **Desviación estándar:** 20.4124145...

- **Varianza:** 416.666...

- **Mediana:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Creación de un agregado con un campo de categoría (texto)

También es posible agregar un campo no numérico. Por ejemplo, si tiene un campo Nombre de producto, puede agregarlo como un valor y después establecerlo en **Recuento**, **Recuento distinto**, **Primero** o **Último**.

1. Arrastre el **producto** campo el **valores** bien. El **valores** también se utiliza normalmente para campos numéricos. Power BI reconoce que este campo es un campo de texto, Establece el agregado en **no resumir**y se presenta con una sola columna de tabla.

   ![Captura de pantalla del campo de producto en los valores correcto.](media/service-aggregates/power-bi-aggregate-value.png)

1. Si cambia la agregación del valor predeterminado **no resumir** a **Count (Distinct)** , Power BI contará el número de productos diferentes. En este caso, hay cuatro.
  
   ![Captura de pantalla del recuento de productos distinto.](media/service-aggregates/power-bi-aggregate-count.png)

1. Si modifica la agregación a **Recuento**, Power BI contará el número total. En este caso, hay siete entradas para **producto**.

   ![Captura de pantalla del recuento de productos.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Arrastrando el mismo campo (en este caso **producto**) en el **valores** bien y dejando la agregación predeterminada **no resumir**, Power BI desglosa el recuento por producto.

   ![Captura de pantalla del producto y el recuento de productos.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

P:  ¿Por qué no dispongo de la opción **No resumir**?

R:  El campo que ha seleccionado es probablemente una medida calculada o una medida avanzada creada en Excel o [Power BI Desktop](desktop-measures.md). Cada medida calculada tiene su propia fórmula codificada de forma rígida. No se puede cambiar la agregación que utiliza Power BI. Por ejemplo, si es una suma, solo puede ser una suma. El **campos** lista muestra *medidas calculadas* con el símbolo de calculadora.

P:  Mi campo **es** numérico; ¿por qué solo tengo las opciones **Recuento** y **Recuento distinto**?

R1:  Lo más probable es que el propietario del conjunto de datos tiene *no* clasificado el campo como un número. Por ejemplo, si tiene un conjunto de datos un **año** campo, el propietario del conjunto de datos puede clasificar el valor como texto. Es más probable que Power BI contará el **año** campo (por ejemplo, el número de personas nacidas en 1974). Es menos probable que Power BI se suma o promedio. Si es el propietario, puede abrir el conjunto de datos en Power BI Desktop y usar el **modelado** tab para cambiar el tipo de datos.

A2: Si el campo tiene un icono de calculadora, eso significa que es un *medida calculada*. Cada medida calculada tiene su propia fórmula codificada de forma rígida que puede cambiar solo el propietario del conjunto de datos. El cálculo de que Power BI usa puede ser una agregación simple como un promedio o una suma. También puede ser algo más complicado como un "porcentaje de contribución a la categoría primaria" o "total acumulado desde el inicio del año". Power BI no va a sumar o calcular el promedio de los resultados. En su lugar, acaba recalculará (usando la fórmula codificada de forma rígida) para cada punto de datos.

A3:  Otra posibilidad es que el campo esté en un *depósito* que solo permite valores de categoría.  En ese caso, las únicas opciones que tendrá disponibles serán recuento y recuento distinto.

A4:  Y una cuarta posibilidad es que esté usando el campo para un eje. Por ejemplo, en un eje del gráfico de barras, Power BI muestra una barra para cada valor distinto, y en ningún caso agrega los valores de campo.

>[!NOTE]
>La excepción a esta regla son los gráficos de dispersión, que *requieren* valores agregados para los ejes X e Y.

P:  ¿Por qué no puedo agregar campos de texto de orígenes de datos de SQL Server Analysis Services (SSAS)?

R:  Las conexiones dinámicas a modelos multidimensionales de SSAS no admiten agregaciones del lado cliente, como first, last, avg, min, max y sum.

P:  Tengo un gráfico de dispersión y quiero que mi campo *no* se agregue.  ¿Cómo lo hago?

R:  Agregue el campo al depósito **Detalles** y no a los depósitos de los ejes X o Y.

P:  Cuando agrego un campo numérico a una visualización, el valor predeterminado de la mayoría es la suma, pero el de algunos es la media y el de otros la agregación.  ¿Por qué la agregación predeterminada no es siempre la misma?

R:  Los propietarios del conjunto de datos pueden establecer el resumen predeterminado para cada campo. Si es propietario de un conjunto de datos, cambiar el resumen predeterminado en el **modelado** pestaña de Power BI Desktop.

P:  Soy el propietario de un conjunto de datos y quiero asegurarme de que nunca se agrega un campo.

R:  En Power BI Desktop, en la pestaña **Modelado**, establezca **Tipo de datos** en **Texto**.

P:  No se ve **no resumir** como una opción en la lista desplegable.

R:  Pruebe a quitar el campo y agregarlo de nuevo.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)