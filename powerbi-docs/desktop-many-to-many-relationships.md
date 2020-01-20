---
title: Relaciones de varios a varios en Power BI Desktop
description: Uso de relaciones con una cardinalidad de varios a varios en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7452879e47cd4b058fcdb3e08f0ded35a85da1aa
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761074"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Aplicación de relaciones de varios a varios en Power BI Desktop

Con las *relaciones con una cardinalidad de varios a varios* de Power BI Desktop, se pueden combinar tablas con una cardinalidad de *varios a varios*. Puede crear modelos de datos que contengan dos o más orígenes de datos de forma más fácil e intuitiva. Las *relaciones con una cardinalidad de varios a varios* forman parte del conjunto de funcionalidades de los *modelos compuestos* de Power BI Desktop.

![Relación de varios a varios en el panel "Editar relación" de Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Una *relación con una cardinalidad de varios a varios* de Power BI Desktop consta de una de tres características relacionadas:

* **Modelos compuestos**: un *modelo compuesto* permite que un informe tenga dos o más conexiones de datos, incluidas conexiones DirectQuery o Importación, en cualquier combinación. Para más información, consulte [Usar modelos compuestos en Power BI Desktop](desktop-composite-models.md).

* **Relaciones con una cardinalidad de varios a varios**: con los modelos compuestos se pueden establecer *relaciones con una cardinalidad de varios a varios* entre tablas. Este enfoque elimina los requisitos de valores únicos en tablas. También permite descartar las soluciones alternativas anteriores, como el hecho de presentar nuevas tablas solo para establecer relaciones. La característica se describe más detalladamente en este artículo.

* **Modo de almacenamiento**: ahora puede especificar los objetos visuales que requieren una consulta a los orígenes de datos back-end. Los objetos visuales que no requieran una consulta se importarán incluso aunque estén basados en DirectQuery. Esta característica permite mejorar el rendimiento y reducir la carga de back-end. Anteriormente, incluso los objetos visuales simples, como las segmentaciones, iniciaban consultas que se enviaban a orígenes de back-end. Para obtener más información, consulte [Modo de almacenamiento en Power BI Desktop](desktop-storage-mode.md).

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>Qué resuelve una relación con una cardinalidad de varios a varios

Antes de que las *relaciones con una cardinalidad de varios a varios* estuviesen disponibles, la relación entre dos tablas se definía en Power BI. Al menos una de las columnas de las tablas implicadas en la relación tenía que contener valores únicos. No obstante, a menudo ninguna columna contiene valores únicos.

Por ejemplo, dos tablas podían tener una columna con la etiqueta Country. Pero los valores de Country no eran únicos en ninguna de las tablas. Para combinar esas tablas, había que crear una solución alternativa. Una solución alternativa podía ser incorporar tablas adicionales con los valores únicos necesarios. Con las *relaciones con una cardinalidad de varios a varios*, puede combinar esas tablas directamente si usa una relación con una cardinalidad de *varios a varios*.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Uso de relaciones con una cardinalidad de varios a varios

Cuando define una relación entre dos tablas de Power BI, debe definir la cardinalidad de la relación. Por ejemplo, la relación entre ProductSales y Product (con las columnas ProductSales [ProductCode] y Product[ProductCode]) se definiría como de *varios a uno*. La relación se define de esta manera porque cada producto tiene muchas ventas y la columna de la tabla Product (ProductCode) es única. Al definir la cardinalidad de una relación como de *varios a uno*, de *uno a varios* o de *uno a uno*, Power BI la valida para que la cardinalidad seleccionada coincida con los datos reales.

Por ejemplo, observe el modelo simple de esta imagen:

![Tablas ProductSales y Product, vista de relaciones, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Ahora, imagine que la tabla **Product** solo muestra dos filas, como se muestra a continuación:

![Objeto visual de la tabla Product con dos filas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Además, imagine que la tabla Sales solo tiene cuatro filas, incluida una para un producto C. Debido a un error de integridad referencial, la fila del producto C no existe en la tabla **Product**.

![Objeto visual de la tabla Sales con cuatro filas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Los elementos **ProductName** y **Price** (de la tabla **Product**), junto con el elemento **Qty** total de cada producto (de la tabla ProductSales) se mostrarían así:

![Visualización del nombre del producto, el precio y la cantidad, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Como puede ver en la imagen anterior, hay una fila **ProductName** en blanco asociada a las ventas del producto C. Esta fila en blanco se aplica para lo siguiente:

* Cualquier fila de la tabla **ProductSales** para la que no existe ninguna fila correspondiente en la tabla **Producto**. Hay un problema de integridad referencial, como se observa en el producto C de este ejemplo.

* Cualquier fila de la tabla **ProductSales** para la que la columna de clave externa es NULL.

Por estas razones, en ambos casos la fila en blanco se contabiliza para las ventas en las que no se conoce el valor de **ProductName** ni de **Precio**.

A veces las tablas se combinan por dos columnas, aunque ninguna de ellas es única. Por ejemplo, observe estas dos tablas:

* La tabla **Ventas** contiene los datos de ventas por **Estado** y cada fila contiene el importe de ventas para el tipo de ventas de este estado. Los estados incluyen CA, WA y TX.

    ![Tabla Sales con las ventas por estado, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* La tabla **CityData** muestra datos sobre las ciudades, incluida la población y el estado (como CA, WA y Nueva York).

    ![Tabla Sales con la ciudad, el estado y la población, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Ahora hay una columna para **State** en ambas tablas. Es razonable querer informar sobre las ventas totales por estado y la población total de cada estado. Pero hay un problema: la columna **State** no es única en ninguna de las tablas.

## <a name="the-previous-workaround"></a>Solución anterior

Antes de la versión de julio de 2018 de Power BI Desktop, no se podía crear una relación directa entre estas tablas. Una solución alternativa era:

* Crear una tercera tabla que solo incluía los identificadores de estado únicos. La tabla podía ser una o todas las siguientes:
  * Tabla calculada (definida mediante el uso de expresiones de análisis de datos [DAX]).
  * Tabla basada en una consulta que se define en el Editor de consultas, que puede mostrar los identificadores únicos procedentes de una de las tablas.
  * Conjunto combinado completo.

* Luego se relacionaban las dos tablas originales con esa tabla nueva mediante relaciones comunes de *varios a uno*.

La tabla de la solución alternativa se podía dejar visible. También se podía ocultar para que no apareciera en la lista **Campos**. Al ocultar la tabla, las relaciones de *varios a uno* normalmente se establecían para filtrar en ambas direcciones y se podía usar el campo State de cualquiera de las tablas. El filtrado cruzado posterior se propaga a la otra tabla. Este enfoque se muestra en la siguiente imagen:

![Tabla State oculta, vista de relaciones, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Un objeto visual que muestra **Estado** (desde la tabla **CityData**) junto con el valor de **Población** y **Ventas** totales sería como aparece a continuación:

![Tablas State, Population y Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Dado que en esta solución alternativa se usa el estado de la tabla **CityData**, solo aparecen los estados de esa tabla, así que TX no está incluido. Además, a diferencia de las relaciones de *varios a uno*, si bien la fila total incluye todas las **ventas** (incluidas las de TX), los detalles no incluyen una fila en blanco que cubre esas filas no coincidentes. Del mismo modo, ninguna fila en blanco cubriría las **ventas** en las que hubiera un valor nulo en **State**.

Imagine que también agrega la ciudad a ese objeto visual. Aunque se conoce la población por ciudad, las **ventas** mostradas por ciudad simplemente repiten las **ventas** del **estado** correspondiente. Este escenario normalmente se produce cuando la agrupación de columnas no está relacionada con alguna medida de agregado, como se muestra aquí:

![Tablas State, City population y Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Imagine que define la nueva tabla Sales como la combinación de todos los estados y que la hace visible en la lista **Campos**. El mismo objeto visual mostraría el **estado** (en la nueva tabla), la **población** total y las **ventas** totales:

![Objeto visual de estado, población y ventas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Como puede ver, se incluirían TX (con datos de **ventas** pero datos de *población* desconocidos) y Nueva York (con datos de **población** conocidos pero sin datos de **ventas**). Esta solución no es óptima y presenta muchos problemas. En las relaciones con una cardinalidad de varios a varios se abordan estos problemas, como se explica en la sección siguiente.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Uso de una relación con una cardinalidad de varios a varios en lugar de la solución alternativa

Con la versión de julio de 2018 de Power BI Desktop, es posible relacionar tablas directamente, como las que se han descrito anteriormente, sin tener que recurrir a soluciones alternativas similares. Ahora es posible establecer la cardinalidad de una relación como de *varios a varios*. Este valor indica que ninguna tabla contiene valores únicos. En estas relaciones se puede controlar qué tabla filtra a la otra tabla. O bien se puede aplicar filtrado bidireccional, donde cada tabla filtra a la otra.

En Power BI Desktop, la cardinalidad se establece de manera predeterminada en *varios a varios* cuando se determina que ninguna tabla contiene valores únicos para las columnas de la relación. En estos casos, un mensaje de advertencia pide confirmación de que se quiere establecer una relación, de modo que el cambio no sea el efecto no deseado de un problema de los datos.

Por ejemplo, al crear una relación directamente entre CityData y Sales (donde los filtros fluirían desde CityData a Sales), Power BI Desktop muestra el cuadro de diálogo **Editar relación**:

![Cuadro de diálogo Editar relación, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La vista de **relaciones** resultante mostrará la relación de varios a varios directa entre las dos tablas. La apariencia de las tablas en la lista **Campos**, así como su comportamiento posterior al crear los objetos visuales, son similares a cuando se aplica la solución alternativa. En la solución alternativa, la tabla adicional que muestra los datos de estado distintos no está visible. Como se ha explicado anteriormente, se mostraría un objeto visual con los datos de **State**, **Population** y **Sales**:

![Tablas State, Population y Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Las principales diferencias entre las *relaciones con una cardinalidad de varios a varios*  y las relaciones de *varios a uno* más típicas son las siguientes:

* Los valores mostrados no incluyen una fila en blanco dedicada a las filas que no coinciden en la otra tabla. Además, los valores no se aplican a las filas donde la columna usada en la relación de la otra tabla es nula.
* No se puede usar la función `RELATED()`, ya que se podría relacionar más de una fila.
* Usar la función `ALL()` en una tabla no quita los filtros aplicados a otras tablas relacionadas con una relación de varios a varios. En el ejemplo anterior, una medida definida como se muestra aquí no quitaría los filtros de las columnas de la tabla CityData relacionada:

    ![Ejemplo de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Un objeto visual que mostrara datos de **State**, **Sales** y **Sales total** daría lugar a este gráfico:

    ![Objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Teniendo en cuenta las diferencias anteriores, asegúrese de que los cálculos que usen `ALL(<Table>)`, como *% del total general*, devuelvan los resultados deseados.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Existen algunas limitaciones para esta versión de las *relaciones con una cardinalidad de varios a varios* y los modelos compuestos.

Los siguientes orígenes de Live Connect (multidimensionales) no se pueden usar con modelos compuestos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de datos de Power BI
* Azure Analysis Services

Al conectarse a estos orígenes multidimensionales mediante DirectQuery, no es posible conectar a otro origen de DirectQuery ni combinarlo con datos importados.

Las limitaciones existentes del uso de DirectQuery se siguen aplicando cuando se utilizan las *relaciones con una cardinalidad de varios a varios*. Muchas limitaciones ahora son por tabla, en función del modo de almacenamiento de la tabla. Por ejemplo, una columna calculada en una tabla importada puede hacer referencia a otras tablas, pero una columna calculada en una tabla DirectQuery puede hacer referencia solo a columnas de la misma tabla. Otras limitaciones se aplican al modelo completo si cualquiera de las tablas del modelo es de DirectQuery. Por ejemplo, las características Conclusiones rápidas y Preguntas y respuestas no están disponibles en un modelo si alguna tabla de este tiene un modo de almacenamiento de DirectQuery.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre los modelos compuestos y DirectQuery, consulte los siguientes artículos:
* [Usar modelos compuestos en Power BI Desktop](desktop-composite-models.md)
* [Modo de almacenamiento en Power BI Desktop](desktop-storage-mode.md)
* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos de Power BI](power-bi-data-sources.md)
