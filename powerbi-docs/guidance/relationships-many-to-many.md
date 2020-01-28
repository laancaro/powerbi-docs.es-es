---
title: Instrucciones para relaciones de varios a varios
description: Instrucciones para desarrollar relaciones de modelos de varios a varios.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/25/2019
ms.author: v-pemyer
ms.openlocfilehash: 6ce82516413fe43cfbc1336e2f6f51003277fb4a
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161303"
---
# <a name="many-to-many-relationship-guidance"></a>Instrucciones para relaciones de varios a varios

Este artículo está dirigido a modeladores de datos como usted que trabajan con Power BI Desktop. Describe tres escenarios diferentes de modelado de varios a varios. También se proporcionan instrucciones sobre cómo diseñarlos correctamente en los modelos.

> [!NOTE]
> En este artículo no se incluye una introducción a las relaciones de modelo. Si no está familiarizado con las relaciones, sus propiedades o cómo configurarlas, se recomienda que primero lea el artículo [Relaciones de modelos en Power BI Desktop](../desktop-relationships-understand.md).
>
> También es importante que conozca el diseño del esquema de estrella. Para más información, vea [Descripción de un esquema de estrella e importancia para Power BI](star-schema.md).

En realidad, hay tres escenarios varios a varios. Se pueden producir cuando tiene que:

- [Relacionar dos tablas de tipo de dimensión](#relate-many-to-many-dimensions)
- [Relacionar dos tablas de tipo de hechos](#relate-many-to-many-facts)
- [Relacionar tablas de tipo de hechos con un nivel de detalle más alto](#relate-higher-grain-facts), cuando la tabla de tipo de hechos almacena filas con un nivel de detalle más alto que las de la tabla de tipo de dimensión

## <a name="relate-many-to-many-dimensions"></a>Relación de dimensiones varios a varios

A continuación se considerará el primer tipo de escenario de varios a varios con un ejemplo. En el escenario clásico se relacionan dos entidades: clientes de banco y cuentas bancarias. Imagine que los clientes pueden tener varias cuentas y que las cuentas pueden tener varios clientes. Cuando una cuenta tiene varios clientes, normalmente se denominan _titulares conjuntos de la cuenta_.

El modelado de estas entidades es sencillo. En una tabla de tipo de dimensión se almacenan las cuentas y en otra los clientes. Como es característico de las tablas de tipo de dimensión, en cada una hay una columna de identificador. Para modelar la relación entre las dos tablas, se requiere una tercera. Esta tabla se conoce comúnmente como _tabla de puente_. En este ejemplo, su finalidad es almacenar una fila por cada asociación de cuenta y cliente. Curiosamente, cuando esta tabla solo contiene columnas de identificador, se denomina [_tabla de hechos sin hechos_](star-schema.md#factless-fact-tables).

Este es un sencillo diagrama de modelo de las tres tablas.

![Un diagrama de modelos contiene tres tablas. En el párrafo siguiente se describe el diseño.](media/relationships-many-to-many/bank-account-customer-model-example.png)

La primera tabla se denomina **Account** (Cuenta) y contiene dos columnas: **AccountID** (IdDeCuenta) y **Account** (Cuenta). La segunda tabla se denomina **AccountCustomer** (ClienteCuenta) y contiene dos columnas: **AccountID** (IdDeCuenta) y **CustomerID** (IdDeCliente). La tercera tabla se denomina **Customer** (Cliente) y contiene dos columnas: **CustomerID** (IdDeCliente) y **Customer** (Cliente). No existen relaciones entre ninguna de las tablas.

Se agregan dos relaciones uno a varios para relacionar las tablas. Este es un diagrama de modelo actualizado de las tablas relacionadas. Se ha agregado una tabla de tipo de hechos denominada **Transaction** (Transacción). Registra las transacciones de las cuentas. Se han ocultado la tabla de puente y todas las columnas de identificador.

![Ahora el diagrama de modelo contiene cuatro tablas. Se han agregado relaciones uno a varios para relacionar todas las tablas.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

Para facilitar la descripción del funcionamiento de la propagación del filtro de relaciones, se ha modificado el diagrama del modelo para mostrar las filas de la tabla.

> [!NOTE]
> No es posible mostrar filas de tabla en el diagrama de modelo de Power BI Desktop. En este artículo se hace para complementar la explicación con ejemplos claros.

![Ahora el diagrama del modelo muestra las filas de la tabla. En el párrafo siguiente se describen los detalles de las filas.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

Los detalles de las filas de las cuatro tablas se describen en la siguiente lista con viñetas:

- La tabla **Account** tiene dos filas:
  - **AccountID** 1 es para Account-01
  - **AccountID** 2 es para Account-02
- La tabla **Customer** tiene dos filas:
  - **CustomerID** 91 es para Customer-91
  - **CustomerID** 92 es para Customer-92
- La tabla **AccountCustomer** tiene tres filas:
  - **AccountID** 1 se asocia a **CustomerID** 91
  - **AccountID** 1 se asocia a **CustomerID** 92
  - **AccountID** 3 se asocia a **CustomerID** 92
- La tabla **Transaction** tiene tres filas:
  - **Date** January 1 2019, **AccountID** 1, **Amount** 100
  - **Date** February 2 2019, **AccountID** 2, **Amount** 200
  - **Date** March 3 2019, **AccountID** 1, **Amount** -25

A continuación se verá lo que sucede cuando se consulta el modelo.

A continuación se muestran dos objetos visuales que resumen la columna **Amount** de la tabla **Transaction**. El primer objeto visual agrupa por cuenta y, por tanto, la suma de las columnas **Amount** representa el _saldo de cuenta_. El segundo objeto visual agrupa por cliente y, por tanto, la suma de las columnas **Amount** representa el _saldo del cliente_.

![Dos objetos visuales de informe en paralelo. En el párrafo siguiente se describen los objetos visuales.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

El nombre del primer objeto visual es **Account Balance** (Saldo de la cuenta) y tiene dos columnas: **Account** (Cuenta) y **Amount** (Cantidad). Muestra el resultado siguiente:

- El saldo de Account-01 es 75
- El saldo de Account-02 es 200
- El total es 275

El nombre del segundo objeto visual es **Customer balance** (Saldo del cliente) y tiene dos columnas: **Customer** (Cliente) y **Amount** (Cantidad). Muestra el resultado siguiente:

- El saldo de Customer-91 es 275
- El saldo de Customer-92 es 275
- El total es 275

Un examen rápido de las filas de tabla y el objeto visual **Account Balance** muestra que el resultado es correcto, para cada cuenta y la cantidad total. Se debe a que cada agrupación de cuentas genera una propagación de filtro a la tabla **Transaction** de esa cuenta.

Pero parece que algo no es correcto en el objeto visual **Customer Balance**. Cada cliente del objeto visual **Customer Balance** tiene el mismo saldo que el saldo total. Este resultado solo podría ser correcto si todos los clientes fueran titulares conjuntos de todas las cuentas. Pero en este ejemplo no es el caso. El problema está relacionado con la propagación del filtro. No fluye de forma completa hasta la tabla **Transaction**.

Siga las direcciones del filtro de relaciones desde la tabla **Customer** a la tabla**Transaction**. Debe ser evidente que la relación entre la tabla **Account** y **AccountCustomer** se propaga en la dirección equivocada. La dirección del filtro para esta relación se debe establecer en **Ambos**.

![El diagrama del modelo se ha actualizado. Se ha realizado un solo cambio en la relación entre la tabla Account y AccountCustomer. Ahora se filtra en ambas direcciones.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![Los dos mismos objetos visuales de informe en paralelo. El primer objeto visual no ha cambiado. El segundo objeto visual revela otro resultado, que se describe en los párrafos siguientes.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Como se esperaba, no ha habido ningún cambio en el objeto visual **Account Balance**.

Pero ahora los objetos visuales **Customer Balance** muestran el siguiente resultado:

- El saldo de Customer-91 es 75
- El saldo de Customer-92 es 275
- El total es 275

Ahora el objeto visual **Customer Balance** muestra un resultado correcto. Siga personalmente las direcciones del filtro y vea cómo se han calculado los saldos del cliente. Además, recuerde que el total visual significa _todos los clientes_.

Alguien que no esté familiarizado con las relaciones del modelo podría concluir que el resultado es incorrecto. Se podría preguntar: _¿Por qué el saldo total de **Customer-91** y **Customer-92** no es igual a 350 (75 + 275)?_

La respuesta a su pregunta radica en comprender la relación varios a varios. Cada saldo de cliente puede representar la suma de varios saldos de cuenta, y los saldos del cliente _no son aditivos_.

### <a name="relate-many-to-many-dimensions-guidance"></a>Instrucciones para la relación de dimensiones varios a varios

Si tiene una relación de varios a varios entre tablas de tipo de dimensión, siga las instrucciones siguientes:

- Agregue cada entidad relacionada de varios a varios como una tabla de modelo, y asegúrese de que tiene una columna de identificador único (ID)
- Agregue una tabla de puente para almacenar entidades asociadas
- Cree relaciones de uno a varios entre las tres tablas
- Configure **una** relación bidireccional para permitir que la propagación del filtro continúe a las tablas de tipo de hechos
- Si no es adecuado tener valores de identificador que faltan, establezca la propiedad **Admite valores NULL** de las columnas ID en FALSE; después, se producirá un error en la actualización de datos si hay valores que faltan en el origen
- Oculte la tabla de puente (a menos que contenga columnas o medidas adicionales necesarias para la generación de informes)
- Oculte las columnas de identificador que no sean adecuadas para los informes (por ejemplo, cuando los identificadores son claves suplentes)
- Si tiene sentido dejar visible una columna de identificador, asegúrese de que se encuentra en el lado "uno" de la relación; oculte siempre la columna del lado "varios". El resultado será el rendimiento óptimo de los filtros.
- Para evitar confusiones o malinterpretaciones, comunique las explicaciones a los usuarios del informe: puede agregar descripciones con cuadros de texto o [información sobre herramientas de encabezado a los objetos visuales](report-page-tooltips.md)

No se recomienda relacionar directamente las tablas de tipo de dimensión de varios a varios. Este enfoque de diseño requiere la configuración de una relación con una cardinalidad de varios a varios. Conceptualmente se puede lograr, pero implica que las columnas relacionadas contendrán valores duplicados. Pero es un procedimiento recomendado de diseño que las tablas de tipo de dimensión tengan una columna ID. Las tablas de tipo de dimensión siempre deben usar la columna ID como el lado "uno" de una relación.

## <a name="relate-many-to-many-facts"></a>Relación varios a varios de hechos

El segundo tipo de escenario de varios a varios implica la relación de dos tablas de tipo de hechos. Dos tablas de tipo de hechos se pueden relacionar directamente. Esta técnica de diseño puede ser útil para la exploración de datos rápida y sencilla. Pero para ser claros, generalmente no se recomienda este enfoque de diseño. Más adelante en esta sección se explicarán los motivos.

Considere un ejemplo con dos tablas de tipo de hechos: **Order** (Pedido) y **Fulfillment** (Suministro). La tabla **Order** contiene una fila por línea de pedido y la tabla **Fulfillment** puede contener cero o más filas por línea de pedido. Las filas de la tabla **Order** representan pedidos de venta. Las filas de la tabla **Fulfillment** representan los artículos de pedidos que se han enviado. Una relación varios a varios relaciona las dos columnas **OrderID**, y el filtro solo se propaga desde la tabla **Order** (**Order** filtra **Fulfillment**).

![Un diagrama de modelos contiene dos tablas: Order y Fulfillment. Una relación de varios a varios relaciona las dos columnas OrderID, y realiza el filtrado de Order a Fulfillment.](media/relationships-many-to-many/order-fulfillment-model-example.png)

La cardinalidad de relación se establece en varios a varios para admitir el almacenamiento de valores **OrderID** duplicados en las dos tablas. En la tabla **Order** pueden existir valores **OrderID** duplicados porque un pedido puede tener varias líneas. En la tabla **Fulfillment** pueden existir valores **OrderID** duplicados porque los pedidos pueden tener varias líneas, y las líneas de pedido se pueden cumplir con varios envíos.

A continuación se examinarán las filas de la tabla. En la tabla **Fulfillment**, observe que varios pedidos se pueden cumplir mediante varios envíos. (La ausencia de una línea de pedido significa que el pedido todavía no se ha cumplido).

![Ahora el diagrama del modelo muestra las filas de la tabla. En el párrafo siguiente se describen los detalles de las filas.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

Los detalles de las filas de las dos tablas se describen en la siguiente lista con viñetas:

- La tabla **Order** tiene cinco filas:
  - **OrderDate** January 1 2019, **OrderID** 1, **OrderLine** 1, **ProductID** Prod-A, **OrderQuantity** 5, **Sales** 50
  - **OrderDate** January 1 2019, **OrderID** 1, **OrderLine** 2, **ProductID** Prod-B, **OrderQuantity** 10, **Sales** 80
  - **OrderDate** February 2 2019, **OrderID** 2, **OrderLine** 1, **ProductID** Prod-B, **OrderQuantity** 5, **Sales** 40
  - **OrderDate** February 2 2019, **OrderID** 2, **OrderLine** 2, **ProductID** Prod-C, **OrderQuantity** 1, **Sales** 20
  - **OrderDate** March 3 2019, **OrderID** 3, **OrderLine** 1, **ProductID** Prod-C, **OrderQuantity** 5, **Sales** 100
- La tabla **Fulfillment** tiene cuatro filas:
  - **FulfillmentDate** January 1 2019, **FulfillmentID** 50, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 2
  - **FulfillmentDate** February 2 2019, **FulfillmentID** 51, **OrderID** 2, **OrderLine** 1, **FulfillmentQuantity** 5
  - **FulfillmentDate** February 2 2019, **FulfillmentID** 52, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 3
  - **FulfillmentDate** January 1 2019, **FulfillmentID** 53, **OrderID** 1, **OrderLine** 2, **FulfillmentQuantity** 10

A continuación se verá lo que sucede cuando se consulta el modelo. A continuación se muestra un objeto visual de tabla en el que se comparan las cantidades de pedidos y de cumplimiento por la columna **OrderID** de la tabla **Order**.

![Un objeto visual de tabla tiene tres columnas: OrderID, OrderQuantity y FulfillmentQuantity. Hay tres filas, una para cada pedido. OrderID 2 y 3 no se han cumplido de forma completa.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

El objeto visual presenta un resultado exacto. Pero la utilidad del modelo es limitada: solo se puede filtrar o agrupar por la columna **OrderID** de la tabla **Order**.

### <a name="relate-many-to-many-facts-guidance"></a>Instrucciones para la relación de hechos varios a varios

Por lo general, no se recomienda relacionar directamente dos tablas de tipo de hechos mediante la cardinalidad de varios a varios. La razón principal es que el modelo no proporcionará flexibilidad a los objetos visuales de informe para filtrar o agrupar. En el ejemplo, solo es posible que los objetos visuales filtren o agrupen por la columna **OrderID** de la tabla **Order**. Un motivo adicional está relacionado con la calidad de los datos. Si los datos tienen problemas de integridad, es posible que algunas filas se omitan durante las consultas debido a la naturaleza de la _relación débil_. Para más información, vea [Evaluación de las relaciones](../desktop-relationships-understand.md#relationship-evaluation).

En lugar de relacionar directamente tablas de tipos de hechos, se recomienda adoptar principios de diseño de [esquema de estrella](star-schema.md). Para ello, agregue tablas de tipo de dimensión. Las tablas de tipo de dimensión se relacionan con las tablas de tipo de hechos mediante relaciones de uno a varios. Este enfoque de diseño es robusto, ya que ofrece opciones de informe flexibles. Permite filtrar o agrupar con cualquiera de las columnas de tipo de dimensión y resumir cualquier tabla de tipo de hechos relacionada.

A continuación se considerará una solución mejor.

![Un diagrama de modelo incluye seis tablas: OrderLine, OrderDate, Order, Fulfillment, Product y FulfillmentDate. Todas las tablas están relacionadas. En el párrafo siguiente se describe el diseño.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Tenga en cuenta los siguientes cambios de diseño:

- Ahora el modelo tiene cuatro tablas adicionales: **OrderLine**, **OrderDate**, **Product** y **FulfillmentDate**
- Las cuatro tablas adicionales son todas de tipo de dimensión y las relaciones uno a varios las relacionan con las tablas de tipo de hechos.
- La tabla **OrderLine** contiene una columna **OrderLineID**, que representa el valor **OrderID** multiplicado por 100, más el valor **OrderLine**, un identificador único para cada línea de pedido
- Las tablas **Order** y **Fulfillment** ahora contienen una columna **OrderLineID** y ya no contienen las columnas **OrderID** ni **OrderLine**.
- La tabla **Fulfillment** contiene ahora columnas **OrderDate** y **ProductID**.
- La tabla **FulfillmentDate** solo está relacionada con la tabla **Fulfillment**.
- Todas las columnas de identificador único están ocultas

Dedicar tiempo a aplicar los principios de diseño de esquema de estrella ofrece las ventajas siguientes:

- Los objetos visuales del informe pueden _filtrar o agrupar_ por cualquier columna visible de las tablas de tipo de dimensión.
- Los objetos visuales del informe pueden _resumir_ por cualquier columna visible de las tablas de tipo de hechos.
- Los filtros aplicados a las tablas **OrderLine**, **OrderDate** o **Product** se propagarán a ambas tablas de tipo de hechos.
- Todas las relaciones son de uno a varios, y cada una es una _relación sólida_. Los problemas de integridad de los datos no se enmascaran. Para más información, vea [Evaluación de las relaciones](../desktop-relationships-understand.md#relationship-evaluation).

## <a name="relate-higher-grain-facts"></a>Relación de hechos con un nivel de detalle más alto

Este escenario de varios a varios es muy diferente de los otros dos que ya se han descrito en este artículo.

A continuación se verá un ejemplo en el que se incluyen cuatro tablas: **Date** (Fecha), **Sales** (Ventas), **Product** (Producto) y **Target** (Destino). **Date** y **Product** son tablas de tipo de dimensión, y las relaciones de uno a varios las relacionan con la tabla de tipo de hechos **Sales**. Hasta ahora, representa un buen diseño de esquema de estrella. Pero la tabla **Target** todavía se tiene que relacionar con las demás tablas.

![Un diagrama de modelo incluye cuatro tablas: Date, Sales, Product y Target. La tabla Target no está relacionada con ninguna otra. En el párrafo siguiente se describe el diseño.](media/relationships-many-to-many/sales-targets-model-example.png)

La tabla **Target** contiene tres columnas: **Category**, **TargetQuantity** y **TargetYear**. Las filas de la tabla revelan una granularidad de año y categoría de producto. En otras palabras, los destinos, que se usan para medir el rendimiento de las ventas, se establecen cada año para cada categoría de producto.

![La tabla Target tiene tres columnas: TargetYear, Category y TargetQuantity. Seis filas registran los destinos para 2019 y 2020, para tres categorías cada uno.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Como en la tabla **Target** se almacenan datos en un nivel superior al de las tablas de tipo de dimensión, no se puede crear una relación de uno a varios. Bueno, es cierto para una sola de las relaciones. A continuación se verá cómo se puede relacionar la tabla **Target** con las tablas de tipo de dimensión.

### <a name="relate-higher-grain-time-periods"></a>Relación de períodos de tiempo con un nivel de detalle más alto

Una relación entre las tablas **Date** y **Target** debe ser de uno a varios. Se debe a que los valores de la columna **TargetYear** son fechas. En este ejemplo, cada valor de columna **TargetYear** es la primera fecha del año de destino.

> [!TIP]
> Al almacenar hechos con una granularidad de tiempo superior a la de un día, establezca el tipo de datos de la columna en **Fecha** (o **Número entero** si usa claves de fecha). En la columna, almacene un valor que represente el primer día del período de tiempo. Por ejemplo, un período de año se registra como el 1 de enero del año, y un período de mes como el primer día de ese mes.

Pero debe tener cuidado para asegurarse de que los filtros de nivel de mes o de fecha producen un resultado significativo. Sin una lógica de cálculo especial, los objetos visuales de informe pueden notificar que las fechas de destino son literalmente el primer día de cada año. Todos los demás días (y todos los meses excepto enero) resumirán la cantidad de destino como en blanco.

En el siguiente objeto visual de matriz se muestra lo que sucede cuando el usuario del informe profundiza en los meses de un año. El objeto visual resume la columna **TargetQuantity**. (La opción [Mostrar elementos sin datos](../desktop-show-items-no-data.md) se ha habilitado para las filas de la matriz).

![Un objeto visual de matriz muestra la cantidad de destino del año 2020 como 270. Cuando se expande para mostrar los meses de 2020, enero es 270 y todas las demás cantidades de destino de nivel mensual están en blanco.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

Para evitar este comportamiento, se recomienda controlar el resumen de los datos de hechos mediante medidas. Una manera de controlar el resumen consiste en devolver un valor en blanco cuando se consultan los períodos de tiempo de nivel inferior. Otra manera, definida con sofisticadas funciones DAX, consiste en es prorratear los valores en períodos de tiempo de nivel inferior.

Considere la siguiente definición de medida que usa la función DAX [ISFILTERED](/dax/isfiltered-function-dax). Solo devuelve un valor cuando las columnas **Date** o **Month** no se filtran.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

El siguiente objeto visual de matriz usa ahora la medida **Target Quantity** (Cantidad de destino). Muestra que todas las cantidades de destino mensuales están en blanco.

![Un objeto visual de matriz muestra la cantidad de destino del año 2020 como 270. Cuando se expande para mostrar los meses de 2020, todas las cantidades de destino de nivel mensual están en blanco.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Relación con un nivel de detalle más alto (distinto de fechas)

Al relacionar una columna que no sea de fecha de una tabla de tipo de dimensión con una tabla de tipo de hechos (y en un nivel de detalle más alto que la tabla de tipo de dimensión) se requiere otro enfoque de diseño.

Las columnas **Category** (de las tablas **Product** y **Target**) contienen valores duplicados. Por tanto, no hay ningún "uno" para una relación de uno a varios. En este caso, tendrá que crear una relación de varios a varios. La relación debe propagar los filtros en una sola dirección, desde la tabla de tipo de dimensión a la de tipo de hechos.

![Un fragmento de diagrama del modelo muestra las tablas Target y Product. Una relación de varios a varios relaciona las dos tablas. La dirección del filtro es desde Product a Target.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

A continuación se examinarán las filas de la tabla.

![Un diagrama de modelos contiene dos tablas: Target y Product. Una relación de varios a varios relaciona las dos columnas Category. En el párrafo siguiente se describen los detalles de las filas.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

En la tabla **Target** hay cuatro filas: dos para cada año de destino (2019 y 2020) y dos categorías (ropa y accesorios). En la tabla **Product** hay tres productos. Dos pertenecen a la categoría de ropa y uno a la de accesorios. Uno de los colores de la ropa es el verde y los dos restantes son azules.

Un objeto visual de tabla que agrupe por la columna **Category** de la tabla **Product** genera el resultado siguiente.

![Un objeto visual de tabla tiene dos columnas: Category y TargetQuantity. Accessories es 60, Clothing es 40 y el total es 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

Este objeto visual genera el resultado correcto. Ahora se verá qué sucede cuando se usa la columna **Color** de la tabla **Product** para agrupar la cantidad de destino.

![Un objeto visual de tabla tiene dos columnas: Color y TargetQuantity. Blue es 100, Green es 40 y el total es 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

El objeto visual genera una representación incorrecta de los datos. ¿Qué sucede aquí?

Un filtro en la columna **Color** de la tabla **Product** genera dos filas. Una de las filas es para la categoría Clothing y la otra para la categoría Accessories. Estos dos valores de categoría se propagan como filtros a la tabla **Target**. En otras palabras, como los productos de dos categorías usan el color azul, _esas categorías_ se usan para filtrar los destinos.

Para evitar este comportamiento, como se ha descrito antes, se recomienda controlar el resumen de los datos de hechos mediante medidas.

Considere la siguiente definición de medida. Observe que todas las columnas de la tabla **Product** que están debajo del nivel de categoría se prueban para los filtros.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

El siguiente objeto visual de tabla usa ahora la medida **Target Quantity** (Cantidad de destino). Muestra que todas las cantidades de destino de color están en blanco.

![Un objeto visual de tabla tiene dos columnas: Color y TargetQuantity. Blue está en blanco, Green está en blanco y el total es 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

El diseño final del modelo es similar al siguiente.

![El diagrama del modelo muestra que las tablas Date y Target se relacionan con una relación de uno a varios. Las tablas Product y Target están relacionadas con una relación de varios a varios, y se filtra de Product a Target.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Instrucciones para la relación de hechos con un nivel de detalle más alto

Si necesita relacionar una tabla de tipo de dimensión con una de tipo de hechos, y la tabla de tipo de hechos almacena filas con un nivel de detalle más alto que las filas de la tabla de tipo de dimensión, siga estas instrucciones:

- Para fechas de hechos con un nivel de detalle más alto:
  - En la tabla de tipo de hechos, almacene la primera fecha del período de tiempo
  - Cree una relación de uno a varios entre la tabla de fechas y la de tipo de hechos
- Para otros hechos con un nivel de detalle más alto:
  - Cree una relación de varios a varios entre la tabla de tipo de dimensión y la de tipo de hechos
- Para los dos tipos:
  - Controle el resumen mediante lógica de medida: devuelva valores en blanco cuando se usen columnas de tipo de dimensión de nivel inferior para filtrar o agrupar
  - Oculte las columnas de tabla de tipo de hechos que se puedan resumir: de esta forma, solo se podrán usar medidas para resumir la tabla de tipo de hechos.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Relaciones de modelos en Power BI Desktop](../desktop-relationships-understand.md)
- [Descripción de un esquema de estrella e importancia para Power BI](star-schema.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
