---
title: Relaciones de varios a varios en Power BI Desktop (versión preliminar)
description: Uso de relaciones de varios a varios en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/23/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 1105de002f6461589d61c6f0077cceeedaada471
ms.sourcegitcommit: 6faeb642721ee5abb41c04a8b729880c01c4d40e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39211782"
---
# <a name="many-to-many-relationships-in-power-bi-desktop-preview"></a>Relaciones de varios a varios en Power BI Desktop (versión preliminar)

Con la característica **Relación de varios a varios** de **Power BI Desktop**, puede combinar tablas usando una cardinalidad de **varios a varios** y crear modelos de datos que contienen varios orígenes de datos de manera más sencilla e intuitiva. La característica **Relación de varios a varios** forma parte del conjunto de funcionalidades de los **modelos compuestos** de **Power BI Desktop**.

![varios a varios en el cuadro de diálogo Editar relación](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La funcionalidad **Relaciones de varios a varios** de **Power BI Desktop** forma parte de una colección de tres características relacionadas:

* **Modelos compuestos**: esta característica permite que un informe tenga varias conexiones de datos, incluidas conexiones de DirectQuery o importación, en cualquier combinación de ambas.
* **Relaciones de varios a varios**: con los **modelos compuestos** puede establecer **relaciones de varios a varios** entre tablas, quitando los requisitos de valores únicos en las tablas y quitando soluciones alternativas anteriores, como la introducción de tablas nuevas solo para establecer relaciones. 
* **Modo de almacenamiento**: ahora puede especificar qué objetos visuales requieren una consulta a los orígenes de datos de back-end y los que no la requieren se importan incluso si están basados en DirectQuery, lo que permite mejorar el rendimiento y reducir la carga de back-end. Anteriormente, incluso los objetos visuales simples, como las segmentaciones, iniciaban consultas que se enviaban a los orígenes de back-end. 

Cada una de las tres características relacionadas de los **modelos compuestos** de esta colección se describe en artículos independientes:

* Los **modelos compuestos** se describen en detalle en el artículo [Modelos compuestos en Power BI Desktop](desktop-composite-models.md).
* Las **relaciones de varios a varios** se describen en este artículo.
* El **modo de almacenamiento** se describe en su propio artículo, [Modo de almacenamiento en Power BI Desktop (versión preliminar)](desktop-storage-mode.md).

## <a name="enabling-the-many-to-many-relationships-preview-feature"></a>Habilitación de la característica de relaciones de varios a varios en versión preliminar

La característica de **relaciones de varios a varios** forma parte de las funcionalidades de los **modelos compuestos** y está en versión preliminar, por lo que se debe habilitar en **Power BI Desktop**. Para habilitar los **modelos compuestos**, seleccione **Archivo > Opciones y configuración > Opciones > Características de versión preliminar** y active la casilla de verificación **Modelos compuestos**.

![habilitación de características de versión preliminar](media/desktop-composite-models/composite-models_02.png)

Deberá reiniciar **Power BI Desktop** para que se habilite la característica.

![reinicio necesario para que los cambios surtan efecto](media/desktop-composite-models/composite-models_03.png)


## <a name="what-many-to-many-relationships-solves"></a>Qué resuelve la característica Relaciones de varios a varios

Antes de la disponibilidad de las **relaciones de varios a varios**, al definir una relación entre dos tablas en Power BI, al menos una de las columnas involucradas en la relación tenía que contener valores únicos. Pero en muchas circunstancias, ninguna de las columnas de la tabla contenía valores únicos. 

Por ejemplo, dos tablas podían tener una columna que con el *País*, pero los valores de *País* no eran únicos en ninguna tabla. Para combinar dichas tablas, era necesario crear una solución alternativa como introducir tablas adicionales en el modelo que contenían los valores únicos necesarios. La característica **Relaciones de varios a varios** proporciona un enfoque alternativo que permite que dichas tablas se combinen directamente mediante una relación con una cardinalidad de **Varios a varios**.  

## <a name="using-many-to-many-relationships"></a>Uso de relaciones de varios a varios

Cuando define una relación entre dos tablas de Power BI, debe definir la cardinalidad de la relación. Por ejemplo, la relación entre *ProductSales* y *Product* (con las columnas *ProductSales[ProductCode]* y *Product[ProductCode]*) se definiría como una relación de **varios a uno**, porque hay varias ventas para cada producto, y la columna de la tabla *Product* *(ProductCode)* es única. Cuando defina la cardinalidad de una relación como de **varios a uno**, de **uno a varios** o de **uno a uno**, Power BI realiza la validación para garantizar que la cardinalidad seleccionada coincide con los datos reales.

Por ejemplo, echemos un vistazo al modelo simple que aparece en la imagen siguiente.

![vista de relaciones](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Luego imagine que la tabla *Product* solo contiene dos filas.

![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imagine también que la tabla *Sales* solo tiene cuatro filas, incluida la fila *Sales* correspondiente a un producto **C** que no existe en la tabla *Product* (debido a un error de integridad referencial).

![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Un objeto visual que muestra *ProductName* y *Price* (desde la tabla *Producto*), junto con la *cantidad* total de cada producto (desde la tabla *ProductSales*) se mostraría como la imagen que aparece a continuación: 

![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Como puede ver en la imagen anterior, hay una fila en el objeto visual con un elemento *ProductName* en blanco, asociado con las ventas correspondientes al producto *C*. Esta fila en blanco se contabiliza para lo siguiente:

* Cualquier fila de la tabla *ProductSales* para la que no exista fila correspondiente en la tabla *Product*: hay un problema de integridad referencial, como vemos en el producto *C* de este ejemplo.

* Cualquier fila de la tabla *ProductSales* para la que la columna de clave externa es NULL. 

Por estas razones, en ambos casos la fila en blanco se contabiliza para las ventas en las que no se conoce el valor de *ProductName* ni de *Price*.

Pero a veces se da el caso de que las tablas se combinan mediante dos columnas, si bien ninguna de estas es única. Por ejemplo, considere las dos tablas siguientes:

* La tabla *Sales* (Ventas) contiene los datos de ventas por *State* (Estado), donde cada fila contiene el importe de ventas para el tipo de ventas de este estado (incluidos los estados de CA, WA y TX) 

    ![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* La tabla *CityData* contiene datos sobre las ciudades, incluida la población y el estado (incluidos los estados de CA, WA y Nueva York)

    ![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Si bien hay una columna para *State* en ambas tablas y es razonable querer informar las *ventas* totales por *estado*, junto con la población total de cada estado, existe un problema: la columna *State* (Estado) no es exclusiva de ninguna de las tablas. 

## <a name="the-prior-workaround"></a>La solución alternativa anterior

En versiones de **Power BI Desktop** anteriores a la versión de julio de 2018, no era posible crear una relación directamente entre estas tablas. Una solución alternativa para este problema era hacer lo siguiente:

* Crear una tercera tabla que solo incluía los identificadores únicos de *State* (Estado). Podía tratarse de una tabla calculada (definida mediante DAX) o una tabla que se definía mediante una consulta definida en el **Editor de consultas** que podía incluir los identificadores únicos extraídos de una de las tablas, o bien el conjunto completo unido.

* Relacionar las dos tablas originales con esa tabla nueva, mediante el uso de relaciones comunes de **varios a uno*.

Esa tabla alternativa podía quedar visible, o bien podían ocultarla de manera tal que no apareciera en la lista de campos. En el último caso, las relaciones de **varios a uno** habitualmente se establecían para filtrar en ambas direcciones, como que se podía usar el campo *State* (Estado) desde cualquier tabla, con el filtrado cruzado subsiguiente propagándose a la otra tabla. Ese enfoque alternativo se muestra en la imagen siguiente de la **vista de relaciones**.

![vista de relaciones](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Un objeto visual que muestra *State* (Estado) (desde la tabla *CityData*) junto con el valor de *Population* (Población) y *Sales* (Ventas) totales sería como aparece a continuación.

![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

Tenga en cuenta que, dado el uso del estado desde la tabla *CityData* en esta solución alternativa, solo se muestran los *estados* de esa tabla (y, por tanto, no se incluye TX). Además, a diferencia del caso con las relaciones de **varios a uno**, si bien la fila total incluye todas las *ventas* (incluidas las de TX), los detalles no incluyen una fila en blanco que abarca esas filas no coincidentes. Del mismo modo, no habría ninguna fila en blanco abarcando ninguna *venta* para la que hubiera un valor NULL para *State* (Estado).

Si *Ciudad* también se hubiese agregado a ese objeto visual, si bien se conoce la población por *ciudad*, las *ventas* que se muestran para la *ciudad* simplemente repetirían las *ventas* para el *estado* correspondiente (como suele ser el caso al agrupar en una columna no relacionada con una medida de agregado), como se muestra en la imagen siguiente.

![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Si la nueva tabla *Sales* (Ventas) se hubiese definido como la unión de todos los *States* (Estados) de esta solución alternativa y se hubiese hecho visible en la lista de campos, el mismo objeto visual que muestra *State* (Estado) (en la tabla nueva) junto con el valor total de *Population* (Población) y *Sales* (Ventas) sería como se muestra a continuación.

![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

En ese caso y tal como se muestra en el objeto visual, se incluirían *TX* (con *Sales* pero una población desconocida) y *Nueva York* (con una población conocida pero sin *Sales*). 

Como puede ver, esta solución alternativa no era óptima y presentaba varios problemas. Con la creación de la **relación de varios a varios**, se abordan estos problemas tal como se indica en la sección siguiente.

## <a name="using-many-to-many-relationships-instead-of-the-workaround"></a>Uso de las relaciones de varios a varios en lugar de la solución alternativa

En las versiones de **Power BI Desktop** a partir de julio de 2018, es posible relacionar directamente las tablas que se describieron en la sección anterior sin la necesidad de recurrir a las soluciones alternativas mencionadas. Ahora es posible establecer la cardinalidad de una relación en **De varios a varios**, lo que indica que ninguna tabla contiene valores únicos. Para dichas relaciones, todavía tiene el control de qué tabla filtra la otra tabla o el filtrado bidireccional, donde ambas tablas se filtran entre sí.  

> [!NOTE]
> La capacidad de crear relaciones de **varios a varios** está en versión preliminar y, mientras así sea, no es posible publicar modelos mediante las relaciones de **varios a varios** en el servicio Power BI. 

En **Power BI Desktop**, la cardinalidad se establece de manera predeterminada en **Varios a varios** cuando se determina que ninguna tabla contiene valores únicos para las columnas de la relación. En tales casos se muestra una advertencia para confirmar que esa configuración de relación es el comportamiento deseado, en lugar de ser el efecto no deseado de un problema de datos. 

Por ejemplo, al crear una relación directamente entre *CityData* y *Sales*, donde los filtros deben fluir desde *CityData* hasta *Sales*, el cuadro de diálogo de la relación aparece tal como se muestra en la imagen siguiente.

![Cuadro de diálogo Editar relación](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La **vista de relaciones** resultante incluiría la relación de **varios a varios** directa entre las dos tablas. La apariencia en la lista de **campos** y el comportamiento subsecuente cuando se crean los objetos visuales son los mismos que si se emplea la solución alternativa descrita en la sección anterior, donde la tabla adicional (con los distintos *States* (Estados) en ella) no es visible. Por ejemplo, como en la sección anterior que describe la solución alternativa, un objeto visual que muestra *States* (Estados) junto con la población total y las ventas se vería de la siguiente manera.

![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Por tanto, la principal diferencia entre las relaciones de **varios a varios** y las relaciones de **varios a uno** más típicas es la siguiente.

* Los valores que se muestran no incluyen una fila en blanco que se contabilice para ninguna fila no coincidente en la otra tabla ni para las filas donde la columna que se usa en la relación de la otra tabla sea NULL.
* No es posible usar la función *RELATED()* (ya que se podría relacionar más de una fila)
* Usar la función *ALL()* en una tabla no quitará los filtros aplicados a otras tablas relacionadas con ella mediante una relación de **varios a varios**. Por ejemplo, una medida definida como se muestra a continuación en el ejemplo siguiente no quitaría los filtros de las columnas en la tabla *CityData* relacionada:

    ![ejemplo de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Por tanto, un objeto visual que muestra *State* (Estado), *Sales* (Ventas) y *Sales total* (Total de ventas) resultaría en lo siguiente:

    ![objeto visual de tabla](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Por este motivo, se debe tener cuidado para garantizar que los cálculos que se realicen con *ALL(\<Table>)*, como *% del total general*, devuelven los resultados deseados. 


## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Existen algunas limitaciones para esta versión de las **relaciones de varios a varios** y los **modelos compuestos**.

Los orígenes multidimensionales siguientes no se pueden usar con los **modelos compuestos**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de datos de Power BI

Al conectarse a esos orígenes multidimensionales mediante DirectQuery, no se puede conectar también a otro origen de DirectQuery ni combinar con los datos importados.

Las limitaciones existentes de usar DirectQuery siguen aplicándose cuando se usan las **relaciones de varios a varios**. Muchas de esas limitaciones son ahora por tabla, en función del **modo de almacenamiento** de la tabla. Por ejemplo, una columna calculada en una tabla importada puede hacer referencia a otras tablas, pero una columna calculada en una tabla de DirectQuery sigue restringida para hacer referencia solo a columnas de la misma tabla. Otras limitaciones se aplican al modelo como un todo, si cualquiera de las tablas dentro del modelo son DirectQuery. Por ejemplo, las características **Conclusiones rápidas** y **Preguntas y respuestas** no están disponibles en un modelo si cualquiera de las tablas dentro del mismo tiene un **modo de almacenamiento** de DirectQuery. 

## <a name="next-steps"></a>Pasos siguientes

Los artículos siguientes describen más información sobre los modelos compuestos y también describen DirectQuery detalladamente.

* [Modelos compuestos en Power BI Desktop (versión preliminar)](desktop-composite-models.md)
* [Modo de almacenamiento en Power BI Desktop (versión preliminar)](desktop-storage-mode.md)

Artículos sobre DirectQuery:

* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos admitidos por DirectQuery en Power BI](desktop-directquery-data-sources.md)

