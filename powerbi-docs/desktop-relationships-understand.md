---
title: Relaciones de modelos en Power BI Desktop
description: Introducción a la teoría sobre las relaciones de modelo en Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 0029d275e5180c29e8653f549d8450014362b59b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "75304244"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Relaciones de modelos en Power BI Desktop

Este artículo está dirigido a modeladores de datos de importación que trabajan con Power BI Desktop. Es un tema importante sobre el diseño de modelos, esencial para ofrecer modelos intuitivos, precisos y óptimos.

Para obtener una explicación más detallada sobre el diseño de modelos óptimos, incluidos los roles y las relaciones de tablas, consulte el artículo [Descripción de un esquema de estrella e importancia para Power BI](guidance/star-schema.md).

## <a name="relationship-purpose"></a>Finalidad de la relación

En pocas palabras, las relaciones de Power BI propagan los filtros aplicados en las columnas de las tablas de un modelo a otras tablas del modelo. Los filtros se propagarán siempre que haya una ruta de relación que seguir, lo que puede implicar la propagación a varias tablas.

Las rutas de relación son deterministas; es decir, los filtros siempre se propagan de la misma manera y sin variación aleatoria. Sin embargo, las relaciones pueden deshabilitarse o el contexto del filtro puede modificarse debido a los cálculos del modelo que usan funciones DAX concretas. Para más información, consulte el tema [Funciones de DAX pertinentes](#relevant-dax-functions), más adelante en este artículo.

> [!IMPORTANT]
> Es importante comprender que las relaciones de modelo no exigen la integridad de los datos. Para más información, consulte el tema [Evaluación de las relaciones](#relationship-evaluation), más adelante en este artículo. En este tema se explica cómo se comportan las relaciones de modelo cuando hay problemas de integridad de datos.

Veamos, con un ejemplo animado, cómo las relaciones propagan los filtros.

![Ejemplo animado de propagación de filtros de relación](media/desktop-relationships-understand/animation-filter-propagation.gif)

En este ejemplo, el modelo se compone de cuatro tablas: **Category**, **Product**, **Year** y **Sales** (Categoría, Producto, Año y Ventas). La tabla **Category** (Categoría) está relacionada con la tabla **Product** (Producto) y la tabla **Product** (Producto) está relacionada con la tabla **Sales** (Ventas). La tabla **Year** (Año) también está relacionada con la tabla **Sales** (Ventas). Todas las relaciones son de uno a varios (los detalles de esta relación se describen más adelante en este artículo).

Una consulta —tal vez generada por un objeto visual de tarjeta de Power BI— solicita las ventas totales correspondientes a los pedidos realizados para una sola categoría, **Cat-A** (Categoría A) y para un solo año, **CY2018** (AC2018). Esta es la razón por la que se pueden ver filtros aplicados en las tablas **Category** (Categoría) y **Year** (Año). El filtro de la tabla **Category** (Categoría) se propaga a la tabla **Product** (Producto) para aislar dos productos asignados a la categoría **Cat-A** (Categoría A). A continuación, los filtros de la tabla **Product** (Producto) se propagan a la tabla **Sales** (Ventas) para aislar solo dos filas de ventas de estos productos. Estas dos filas de ventas representan las ventas de productos asignados a la categoría **Cat-A** (Categoría A). Su cantidad combinada es de 14 unidades. Al mismo tiempo, el filtro de la tabla **Year** (Año) se propaga para filtrar aún más la tabla **Sales** (Ventas), lo que da lugar a la única fila de ventas que corresponde a los productos asignados a la categoría **Cat-A** (Categoría A) solicitados en el año **CY2018** (AC2018). El valor devuelto por la consulta es de 11 unidades. Tenga en cuenta que, cuando se aplican varios filtros a una tabla, (como en el caso de la tabla **Sales** [Ventas] en este ejemplo), siempre se trata de una operación AND, lo que significa que se deben cumplir todas las condiciones.

### <a name="disconnected-tables"></a>Tablas desconectadas

Es poco frecuente que una tabla del modelo no esté relacionada con otra tabla del modelo. Este tipo de tabla en un diseño de modelo válido se puede describir como una _tabla desconectada_. La tabla desconectada no pretende propagar filtros a otras tablas del modelo. En vez de ellos, se usa para aceptar la "entrada del usuario" (quizás con un objeto visual de segmentación), lo que permite que los cálculos del modelo usen el valor de entrada de una manera significativa. Por ejemplo, pensemos en una tabla desconectada que se carga con un intervalo de valores de tasas de cambio de divisa. Suponiendo que se aplica un filtro para conseguir un valor de tasa único, este valor se puede usar en una expresión de medida para convertir valores de ventas.

El parámetro de hipótesis de Power BI Desktop es una característica que crea una tabla desconectada. Para más información, consulte el artículo [Creación y uso de un parámetro de hipótesis para visualizar variables en Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Propiedades de la relación

Una relación de modelo relaciona una columna de una tabla con una columna de otra tabla. Hay un caso especial en el que este requisito no es cierto, que solo se aplica a las relaciones de varias columnas en los modelos de DirectQuery; para más información, consulte el artículo de la función DAX [COMBINEVALUES](/dax/combinevalues-function-dax).

> [!NOTE]
> No es posible relacionar una columna con una columna diferente _de la misma tabla_. A veces, esto se confunde con la capacidad de definir una restricción de clave externa de base de datos relacional que supone una referencia de la tabla a sí misma. Este concepto de base de datos relacional se puede usar para almacenar relaciones de elementos primarios y secundarios (por ejemplo, cada registro de empleado está relacionado con un empleado del que depende). La generación de una jerarquía del modelo basada en este tipo de relación no se puede resolver mediante la creación de relaciones de modelo. Para esta finalidad, consulte el artículo [Funciones primarias y secundarias](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Cardinalidad

Cada relación de modelo debe definirse con un tipo de cardinalidad. Hay cuatro opciones de tipo de cardinalidad, que representan las características de los datos de las columnas relacionadas "de" y "a". El lado "uno" significa que la columna contiene valores únicos; el lado "dos" significa que la columna puede contener valores duplicados.

> [!NOTE]
> Si una operación de actualización de datos intenta cargar valores duplicados en una columna de lado "uno", se producirá un error en la operación completa de actualización.

En la siguiente lista con viñetas se describen las cuatro opciones, junto con sus anotaciones abreviadas:

- Uno a varios (1:\*)
- Varios a uno (\*:1)
- Uno a uno (1:1)
- Varios a varios (\*:\*)

Cuando se crea una relación en Power BI Desktop, el diseñador detecta y establece automáticamente el tipo de cardinalidad. Puede hacerlo porque consulta el modelo para saber qué columnas contienen valores únicos. En el caso de los modelos de importación, utiliza estadísticas de almacenamiento internas; en el caso de los modelos DirectQuery, envía consultas de generación de perfiles al origen de datos. En ocasiones, sin embargo, puede equivocarse. Esto sucede porque todavía tienen que cargarse los datos de las tablas o porque las columnas que se espera que contengan valores duplicados actualmente contienen valores únicos. En cualquiera de estos casos, puede actualizar el tipo de cardinalidad, siempre que las columnas del lado "uno" contengan valores únicos (o la tabla aún se deba cargar con filas de datos).

Las opciones de cardinalidad de **uno a varios** y **varios a uno** son esencialmente iguales y son también los tipos de cardinalidad más comunes.

A la hora de configurar una relación de uno a varios o de varios a uno, deberá elegir la que coincida con el orden en el que relacionó las columnas. Considere cómo configuraría la relación desde la tabla **Product** (Producto) a la tabla **Sales** (Ventas) mediante la columna **ProductID** (IdProducto) incluida en cada tabla. El tipo de cardinalidad sería de _uno a varios_, ya que la columna **ProductID** (IdProducto) de la tabla **Product** (Producto) contiene valores únicos. Si relacionó las tablas en dirección inversa, de **Sales** (Ventas) a **Product** (Producto), la cardinalidad sería de _varios a uno_.

Una relación de **uno a uno** significa que ambas columnas contienen valores únicos. Este tipo de cardinalidad no es común y probablemente representa un diseño de modelo poco óptimo debido al almacenamiento de datos redundantes.<!-- For guidance on using this cardinality type, see the [One-to-one relationship guidance](guidance/relationships-one-to-one) article.-->

Una relación de **varios a varios** significa que ambas columnas pueden contener valores duplicados. Este tipo de cardinalidad no se usa con frecuencia. Suele resultar útil cuando se diseñan requisitos de modelos complejos. Para obtener instrucciones sobre el uso de este tipo de cardinalidad, vea [Instrucciones para relaciones de varios a varios](guidance/relationships-many-to-many.md).

> [!NOTE]
> Actualmente no se admite el tipo de cardinalidad de varios a varios en los modelos desarrollados para Power BI Report Server.

> [!TIP]
> En la vista de modelo de Power BI Desktop, puede interpretar el tipo de cardinalidad de una relación examinando los indicadores (1 o \*) en cualquiera de los lados de la línea de relación. Si quiere determinar qué columnas están relacionadas, deberá seleccionar (o mover el cursor sobre) la línea de relación para resaltar las columnas.

### <a name="cross-filter-direction"></a>Dirección de filtro cruzado

Cada relación de modelo debe definirse con una dirección de filtro cruzado. La selección determina en qué direcciones se propagarán los filtros. Las posibles opciones de filtro cruzado dependen del tipo de cardinalidad.

| Tipo de cardinalidad | Opciones de filtro cruzado |
| --- | --- |
| Uno a varios (o varios a uno) | Único<br>Ambos |
| Uno a uno | Ambos |
| Varios a varios | Único (Tabla1 a Tabla2)<br>Único (Tabla2 a Tabla1)<br>Ambos |

La dirección del filtro cruzado _Único_ significa "dirección única" y _Ambos_ se aplica a "ambas direcciones". Una relación que filtra en ambas direcciones se describe normalmente como _bidireccional_.

En el caso de las relaciones de uno a varios, la dirección del filtro cruzado siempre es desde el lado "uno" y, opcionalmente, desde el lado "varios" (bidireccional). En el caso de las relaciones de uno a uno, la dirección del filtro cruzado siempre es desde ambas tablas. Por último, en las relaciones de varios a varios, la dirección del filtro cruzado puede ser desde cualquiera de las tablas o desde ambas tablas. Tenga en cuenta que cuando el tipo de cardinalidad incluye un lado "uno", los filtros siempre se propagarán desde ese lado.

Si la dirección del filtro cruzado se establece en **Ambos**, hay disponible una propiedad adicional para aplicar el filtrado bidireccional cuando se aplican reglas de seguridad de nivel de fila (RLS). Para más información sobre la seguridad de nivel de fila, consulte el artículo [Seguridad de nivel de fila (RLS) con Power BI Desktop](desktop-rls.md).

La dirección del filtro cruzado de la relación, incluida la deshabilitación de la propagación de filtros, también puede modificarse mediante un cálculo del modelo. Esto se consigue gracias el uso de la función DAX [CROSSFILTER](/dax/crossfilter-function).

Las relaciones bidireccionales pueden afectar negativamente al rendimiento. Además, intentar configurar una relación bidireccional podría producir rutas de propagación de filtro ambiguas. En este caso, es posible que Power BI Desktop no pueda confirmar el cambio de relación y le avisará con un mensaje de error. Sin embargo, a veces Power BI Desktop puede permitir que se definan rutas de relación ambiguas entre las tablas. Las reglas de precedencia que afectan a la detección de ambigüedades y la resolución de rutas se describen más adelante en este artículo, en el tema [Reglas de precedencia](#precedence-rules).

Se recomienda usar el filtrado bidireccional solo cuando sea necesario.<!-- For guidance on bi-directional filtering, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

> [!TIP]
> En la vista de modelo de Power BI Desktop, puede interpretar la dirección del filtro cruzado de una relación mediante las puntas de flecha a lo largo de la línea de relación. Una sola punta de flecha representa un filtro de dirección única en la dirección de la punta de flecha; una punta de flecha doble representa una relación bidireccional.

### <a name="make-this-relationship-active"></a>Activar esta relación

Solo puede haber una ruta de propagación de filtros activa entre dos tablas del modelo. Sin embargo, es posible introducir rutas de relación adicionales, aunque estas relaciones deben configurarse como _inactivas_. Las relaciones inactivas solo se pueden activar durante la evaluación de un cálculo del modelo. Esto se consigue mediante el uso de la función DAX [USERELATIONSHIP](/dax/userelationship-function-dax).

<!--For guidance on defining inactive relationships, see the [Active vs inactive relationship guidance](guidance/relationships-active-inactive) article.-->

> [!TIP]
> En la vista de modelo de Power BI Desktop, puede interpretar el estado activo o inactivo de una relación. Una relación activa se representa mediante una línea continua; una relación inactiva se representa como una línea discontinua.

### <a name="assume-referential-integrity"></a>Asumir integridad referencial

La propiedad _Asumir integridad referencial_ solo está disponible para las relaciones de uno a varios y uno a uno entre dos tablas del modo de almacenamiento DirectQuery basadas en el mismo origen de datos. Cuando está habilitada, las consultas nativas enviadas al origen de datos combinan las dos tablas utilizando una combinación interna en lugar de una combinación externa. La habilitación de esta propiedad mejora, por lo general, el rendimiento de la consulta, aunque depende de las características específicas del origen de datos.

Esta propiedad siempre debe estar habilitada cuando existe una restricción de clave externa de base de datos entre las dos tablas. Si no existe una restricción de clave externa, puede habilitar la propiedad siempre y cuando tenga la certeza de que existe integridad de datos.

> [!IMPORTANT]
> Si se pone en peligro la integridad de los datos, la combinación interna eliminará las filas no coincidentes entre las tablas. Por ejemplo, supongamos que tenemos una tabla **Sales** (Ventas) del modelo con un valor en la columna **ProductID** (IdProducto) que no existe en la tabla relacionada **Product** (Producto). La propagación del filtro de la tabla **Product** (Producto) a la tabla **Sales** (Ventas) eliminaría las filas de ventas de los productos desconocidos. Esto daría lugar a una subestimación de los resultados de ventas.
>
> Para más información, consulte el artículo [Configuración de Asumir integridad referencial en Power BI Desktop](desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Funciones DAX pertinentes

Hay varias funciones DAX pertinentes para las relaciones de modelo. En la siguiente lista con viñetas se describe brevemente cada una de estas funciones:

- [RELATED](/dax/related-function-dax): recupera el valor del lado "uno".
- [RELATEDTABLE](/dax/relatedtable-function-dax): recupera una tabla de filas del lado "varios".
- [USERELATIONSHIP](/dax/userelationship-function-dax): fuerza el uso de una relación de modelo inactiva específica.
- [CROSSFILTER](/dax/crossfilter-function): modifica la dirección del filtro cruzado de la relación (a uno o ambos) o deshabilita la propagación del filtro (ninguna).
- [COMBINEVALUES](/dax/combinevalues-function-dax): combina dos o más cadenas de texto en una sola. El propósito de esta función es admitir relaciones de varias columnas en los modelos DirectQuery.
- [TREATAS](/dax/treatas-function): aplica el resultado de una expresión de tabla como filtros en las columnas de una tabla no relacionada.
- [Funciones primarias y secundarias](/dax/parent-and-child-functions-dax): familia de funciones relacionadas que se pueden usar para generar columnas calculadas y naturalizar una jerarquía de elementos primarios y secundarios. Estas columnas se pueden usar después para crear una jerarquía de nivel fijo.

## <a name="relationship-evaluation"></a>Evaluación de las relaciones

Las relaciones de modelo, desde la perspectiva de la evaluación, se clasifican como _fuertes_ o _débiles_. No se trata de una propiedad configurable de la relación; en realidad, se deduce del tipo de cardinalidad y del origen de datos de las dos tablas relacionadas. Es importante comprender el tipo de evaluación, porque puede haber implicaciones en el rendimiento o consecuencias si se pone en peligro la integridad de los datos. En este tema se describen estas implicaciones y las consecuencias respecto a la integridad.

En primer lugar, se necesita un poco de teoría de modelado para llegar a comprender las evaluaciones de las relaciones.

Un modelo de importación o DirectQuery consigue todos sus datos de la caché de Vertipaq o de la base de datos de origen. En ambos casos, Power BI puede determinar que existe un lado "uno" de una relación.

Sin embargo, un modelo compuesto puede constar de tablas que usan diferentes modos de almacenamiento (importación, DirectQuery o dual) o varios orígenes de DirectQuery. Cada origen, incluida la caché de Vertipaq de datos de importación, se considera una _isla de datos_. Así, las relaciones de modelo se pueden clasificar como _intraisla_ o _entre islas_. Una relación intraisla es aquella que relaciona dos tablas de una misma isla de datos, mientras que una relación entre islas relaciona tablas de diferentes islas de datos. Tenga en cuenta que las relaciones en los modelos de importación o DirectQuery siempre son intraisla.

Veamos un ejemplo de un modelo compuesto.

![Ejemplo de un modelo compuesto formado por dos islas](media/desktop-relationships-understand/data-island-example.png)

En este ejemplo, el modelo compuesto consta de dos islas: una isla de datos de Vertipaq y una isla de datos de origen de DirectQuery. La isla de datos de Vertipaq contiene tres tablas y la isla de datos de origen de DirectQuery contiene dos. Existe una relación entre islas que relaciona una tabla de la isla de datos de Vertipaq con una tabla de la isla de datos de origen de DirectQuery.

### <a name="strong-relationships"></a>Relaciones fuertes

Una relación de modelo es _fuerte_ cuando el motor de consultas puede determinar el lado "uno" de la relación. Tiene la confirmación de que la columna del lado "uno" contiene valores únicos. Todas las relaciones intraisla de uno a varios son relaciones fuertes.

En el ejemplo siguiente, hay dos relaciones fuertes, ambas marcadas como **F**. Hay una relación de uno a varios incluida dentro de la isla de Vertipaq y otra relación de uno a varios incluida dentro del origen de DirectQuery.

![Ejemplo de un modelo compuesto formado por dos islas con relaciones fuertes marcadas](media/desktop-relationships-understand/data-island-example-strong.png)

En el caso de los modelos de importación, donde todos los datos se almacenan en la caché de Vertipaq, se crea una estructura de datos para cada relación fuerte en el momento de la actualización de datos. Las estructuras de datos están formadas por asignaciones indexadas de todos los valores de columna a columna y su finalidad es acelerar la combinación de las tablas en el momento de la consulta.

Cuando se produce la consulta, las relaciones fuertes permiten que se produzca la _expansión de la tabla_. Esta expansión da como resultado la creación de una tabla virtual mediante la inclusión de las columnas nativas de la tabla base y, a continuación, su expansión en tablas relacionadas. En el caso de las tablas de importación, esto se lleva a cabo en el motor de consultas; en el caso de las tablas de DirectQuery, se lleva a cabo en la consulta nativa que se envía a la base de datos de origen (siempre que la propiedad "Asumir integridad referencial" no esté habilitada). A continuación, el motor de consultas actúa sobre la tabla expandida, aplicando los filtros y agrupando según los valores de las columnas de la tabla expandida.

> [!NOTE]
> También se expanden las relaciones inactivas, incluso si la relación no se utiliza en ningún cálculo. Las relaciones bidireccionales no tienen ningún impacto en la expansión de tablas.

En el caso de las relaciones de uno a varios, la expansión de tablas tiene lugar desde el lado "varios" al lado "uno" mediante la semántica LEFT OUTER JOIN. Cuando no existe un valor coincidente del lado "varios" en el lado "uno", se agrega una fila virtual en blanco en la tabla del lado "uno".

La expansión de tablas también se produce en las relaciones de uno a uno intraisla, pero mediante la semántica de combinación externa completa. Así se garantiza que las filas virtuales en blanco se agregan en cualquiera de los lados, cuando es necesario.

Las filas virtuales en blanco son, de hecho, _miembros desconocidos_. Los miembros desconocidos representan infracciones de la integridad referencial en las que el valor del lado "varios" no tiene un valor correspondiente en el lado "uno". Idóneamente, estos espacios en blanco no deben existir y se pueden eliminar mediante la limpieza o la reparación de los datos de origen.

Veamos cómo funciona la expansión de tablas con un ejemplo animado.

![Ejemplo animado de expansión de tablas](media/desktop-relationships-understand/animation-expanded-table.gif)

En este ejemplo, el modelo consta de tres tablas: **Category**, **Product** y **Sales** (Categoría, Producto y Ventas). La tabla **Category** (Categoría) está relacionada con la tabla **Product** (Producto) en una relación de uno a varios y la tabla **Product** (Producto) está relacionada con la tabla **Sales** (Ventas) también en una relación de uno a varios. La tabla **Category** (Categoría) contiene dos filas, la tabla **Product** (Producto) contiene tres filas y la tabla **Sales** (Ventas) contiene cinco filas. Hay valores coincidentes en ambos lados de todas las relaciones, lo que significa que no hay ninguna infracción de la integridad referencial. Se desvela una tabla expandida en tiempo de consulta. La tabla consta de las columnas de las tres tablas. Es, de hecho, una perspectiva desnormalizada de los datos incluidos en las tres tablas. Se agrega una nueva fila a la tabla **Sales** (Ventas), con un valor de identificador de producción (9) sin ningún valor coincidente en la tabla **Product** (Producto). Supone una infracción de la integridad referencial. En la tabla expandida, la nueva fila tiene valores (en blanco) para las columnas de tabla **Category** (Categoría) y **Product** (Producto).

### <a name="weak-relationships"></a>Relaciones débiles

Una relación de modelo es _débil_ cuando no hay ningún lado "uno" garantizado. Esto puede deberse a dos motivos:

- La relación usa un tipo de cardinalidad de varios a varios (aunque una o ambas columnas contengan valores únicos).
- La relación es entre islas (lo que solo puede suceder en los modelos compuestos).

En el ejemplo siguiente, hay dos relaciones débiles, ambas marcadas como **D**: la relación de varios a varios incluida dentro de la isla de Vertipaq y la relación de uno a varios entre islas.

![Ejemplo de un modelo compuesto formado por dos islas con relaciones débiles marcadas](media/desktop-relationships-understand/data-island-example-weak.png)

En el caso de los modelos de importación, nunca se crean estructuras de datos para las relaciones débiles. Esto significa que las combinaciones de tablas deben resolverse en el momento de la consulta.

En las relaciones débiles tampoco se produce la expansión de las tablas. Las combinaciones de tablas se logran mediante la semántica de combinación interna y, por este motivo, no se agregan filas virtuales en blanco para compensar las infracciones de integridad referencial.

Existen restricciones adicionales relacionadas con las relaciones débiles:

- No se puede usar la función DAX RELATED para recuperar los valores de las columnas del lado "uno".
- La aplicación de RLS tiene restricciones de topología.

> [!NOTE]
> En la vista de modelo de Power BI Desktop, no siempre es posible determinar si una relación de modelo es fuerte o débil. Una relación de varios a varios siempre será débil, así como una relación de uno a varios si es entre islas. Para determinar de forma correcta si se trata de una relación entre islas, deberá inspeccionar los modos de almacenamiento de tabla y los orígenes de datos.

### <a name="precedence-rules"></a>Reglas de precedencia

Las relaciones bidireccionales pueden introducir varias rutas, y por tanto ambiguas, de propagación de filtro entre las tablas del modelo. En la lista siguiente se presentan las reglas de precedencia que Power BI usa para la detección de ambigüedades y la resolución de rutas:

1. Relaciones de varios a uno y uno a uno, incluidas las relaciones débiles
2. Relaciones de varios a varios
3. Relaciones bidireccionales, en la dirección inversa (es decir, desde el lado "varios")

### <a name="performance-preference"></a>Preferencia de rendimiento

En la lista siguiente se ordena el rendimiento de la propagación de filtros, desde el rendimiento más rápido al más lento:

1. Relaciones de uno a varios intraisla
2. Relaciones de cardinalidad de varios a varios
3. Relaciones de modelo de varios a varios logradas con una tabla intermediaria y que implican al menos una relación bidireccional
4. Relaciones entre islas

<!--For further information and guidance on many-to-many relationships, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

## <a name="next-steps"></a>Pasos siguientes

- [Descripción de un esquema de estrella e importancia para Power BI](guidance/star-schema.md)
- [Instrucciones para relaciones de varios a varios](guidance/relationships-many-to-many.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
