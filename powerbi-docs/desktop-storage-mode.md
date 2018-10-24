---
title: Uso del modo de almacenamiento en Power BI Desktop (versión preliminar)
description: Uso del modo de almacenamiento para controlar si los datos se almacenan en caché en memoria para los informes de Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ce4aab1a477485a30a4166d86d166a4ac289108f
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45974239"
---
# <a name="storage-mode-in-power-bi-desktop-preview"></a>Modo de almacenamiento en Power BI Desktop (versión preliminar)

En **Power BI Desktop**, puede especificar el **modo de almacenamiento** de las tablas, para tener el control sobre si los datos de tabla se almacenan en caché en memoria para los informes. 

![Modo de almacenamiento en Power BI Desktop](media/desktop-storage-mode/storage-mode_01.png)

Establecer el **modo de almacenamiento** proporciona varias ventajas. Puede establecer el **modo de almacenamiento** para cada tabla de manera individual en el modelo, lo que permite habilitar un conjunto de datos único para aprovechar una o varias de las ventajas siguientes:

* **Rendimiento de consultas**: cuando los usuarios interactúan con objetos visuales en los informes de Power BI, las consultas de DAX se envían al conjunto de datos. Almacenar datos en caché en la memoria al establecer correctamente el **modo de almacenamiento** puede mejorar el rendimiento de consulta y la interactividad de los informes.
* **Conjuntos de datos de gran tamaño**: las tablas que no se almacenan en caché no consumen memoria para el almacenamiento en caché. Puede habilitar el análisis interactivo de conjuntos de datos de gran tamaño que son demasiado grandes o costos para almacenar completamente en caché en la memoria. Puede elegir las tablas que vale la pena almacenar en caché y las que no.
* **Optimización de la actualización de datos**: no es necesario actualizar las tablas que no se almacenan en caché. Puede reducir los tiempos de actualización mediante el almacenamiento en caché solo de los datos necesarios para cumplir los acuerdos de nivel de servicio y los requisitos del negocio.
* **Requisitos casi en tiempo real**: las tablas con requisitos casi en tiempo real se pueden beneficiar de que no se almacenan en caché con el fin de reducir la latencia de los datos.
* **Escritura diferida**: la escritura diferida permite que los usuarios profesionales exploren escenarios hipotéticos cambiando los valores de las celdas. Las aplicaciones personalizadas pueden aplicar cambios al origen de datos. Las tablas que no se almacenan en caché pueden reflejar los cambios de inmediato, lo que permite analizar los efectos de manera instantánea.

La configuración del **modo de almacenamiento** de **Power BI Desktop** es una de tres características relacionadas:

* **Modelos compuestos**: esta característica permite que un informe tenga varias conexiones de datos, incluidas conexiones de DirectQuery o importación, en cualquier combinación de ambas.
* **Relaciones de varios a varios**: con los **modelos compuestos** puede establecer **relaciones de varios a varios** entre tablas, quitando los requisitos de valores únicos en las tablas y quitando soluciones alternativas anteriores, como la introducción de tablas nuevas solo para establecer relaciones. 
* **Modo de almacenamiento**: ahora puede especificar qué objetos visuales requieren una consulta a los orígenes de datos de back-end y los que no la requieren se importan incluso si están basados en DirectQuery, lo que permite mejorar el rendimiento y reducir la carga de back-end. Anteriormente, incluso los objetos visuales simples, como las segmentaciones, iniciaban consultas que se enviaban a los orígenes de back-end. 

Cada una de las tres características relacionadas de los **modelos compuestos** de esta colección se describe en artículos independientes:

* Los **modelos compuestos** se describen en detalle en su propio artículo, [Modelos compuestos en Power BI Desktop](desktop-composite-models.md).
* Las **relaciones de varios a varios** se describen en su propio artículo, [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md).
* El **modo de almacenamiento** se describe en detalle en este artículo.

## <a name="enabling-the-storage-mode-preview-feature"></a>Habilitación de la característica del modo de almacenamiento en versión preliminar

La característica del **modo de almacenamiento** está en versión preliminar y se debe habilitar en **Power BI Desktop**. Para habilitar el **modo de almacenamiento**, seleccione **Archivo > Opciones y configuración > Opciones > Características de versión preliminar** y active la casilla de verificación **Modelos compuestos**. 

![habilitación de características de versión preliminar](media/desktop-composite-models/composite-models_02.png)

Deberá reiniciar **Power BI Desktop** para que se habilite la característica.

![reinicio necesario para que los cambios surtan efecto](media/desktop-composite-models/composite-models_03.png)


## <a name="using-the-storage-mode-property"></a>Uso de la propiedad de modo de almacenamiento

El **modo de almacenamiento** es una propiedad que puede establecer en cada tabla del modelo. Para establecer el **modo de almacenamiento**, seleccione la tabla del panel **Campos** y haga clic con el botón derecho para que aparezca el menú contextual. En el menú contextual, seleccione **Propiedades**.

![Selección de Propiedades en el menú contextual](media/desktop-storage-mode/storage-mode_02.png)

La selección del **modo de almacenamiento** se muestra en el panel **Propiedades de campo** de la tabla. Desde ahí puede ver el **modo de almacenamiento** actual o modificarlo.

![Establecimiento del modo de almacenamiento de una tabla](media/desktop-storage-mode/storage-mode_03.png)

Existen tres valores para el **modo de almacenamiento**:

* **Importación**: cuando se establece en **Importación**, las tablas importadas se almacenan en caché. Las consultas enviadas al conjunto de datos de Power BI que devuelven datos desde las tablas de importación solo se pueden satisfacer desde los datos en caché.
* **DirectQuery**: con esta configuración, las tablas de DirectQuery no se almacenan en caché. Las consultas enviadas al conjunto de datos de Power BI (por ejemplo, las consultas DAX) que devuelven datos desde las tablas de DirectQuery solo se pueden satisfacer mediante la ejecución de consultas a petición al origen de datos. Las consultas enviadas al origen de datos usan el lenguaje de la consulta para ese origen de datos (por ejemplo, SQL).
* **Dual**: las tablas duales pueden actuar como tablas almacenadas en caché o no almacenadas en caché, en función del contexto de la consulta enviada al conjunto de datos de Power BI. En algunos casos, las consultas se satisfacen a partir de datos en caché; en otros casos, mediante la ejecución de una consulta a petición al origen de datos.

Cambiar una tabla a importación es una operación *irreversible* que no se puede cambiar a DirectQuery ni a Dual.

## <a name="constraints-on-directquery-and-dual-tables"></a>Restricciones en las tablas de DirectQuery y las tablas duales

Las tablas duales están sujetas a las mismas restricciones que las tablas de DirectQuery. Estas pueden incluir transformaciones M limitadas y funciones DAX restringidas en las columnas calculadas. Para más información, consulte [Implicaciones de usar DirectQuery](desktop-directquery-about.md#implications-of-using-directquery).

## <a name="relationship-rules-on-tables-with-different-storage-modes"></a>Reglas de relación en tablas con distintos modos de almacenamiento

Las relaciones deben cumplir con las reglas en función del **modo de almacenamiento** de las tablas relacionadas. En esta sección se proporcionan ejemplos de combinaciones válidas. Para más información, consulte [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md).

En un conjunto de datos con un solo origen de datos, son válidas las combinaciones de relaciones de **uno a varios** siguientes:

| Tabla en el lado de **varios** | Tabla en el lado de **uno** |
| ------------- |----------------------| 
| Dual          | Dual                 | 
| Importar        | Importación o dual       | 
| DirectQuery   | DirectQuery o dual  | 

## <a name="propagation-of-dual"></a>Propagación de dual
Veamos un ejemplo. Considere el modelo sencillo siguiente, donde todas las tablas provienen de un solo origen que admite la importación y DirectQuery.

![Ejemplo de vista de relaciones para el modo de almacenamiento](media/desktop-storage-mode/storage-mode_04.png)

Para empezar, supongamos que todas las tablas de este modelo son DirectQuery. Si luego cambiamos el **modo de almacenamiento** de la tabla *SurveyResponse* a Importación, aparecerá la confirmación siguiente:

![Cuadro de diálogo de advertencia del modo de almacenamiento](media/desktop-storage-mode/storage-mode_05.png)

Las tablas de dimensiones (*Customer* [Cliente], *Date* [Fecha] y *Geography* [Geografía]) se deben establecer en **Dual** para cumplir con las reglas de relaciones anteriormente descritas. En lugar de exigir que estas tablas se establezcan en **Dual** antes de tiempo, pueden establecerse en una sola operación.

La lógica de propagación está diseñada para ayudar con los modelos que contienen muchas tablas. Supongamos que tiene un modelo con 50 tablas y solo se deben almacenar en caché ciertas tablas de hechos (transaccionales). La lógica de **Power BI Desktop** determina el conjunto mínimo de tablas de dimensiones que se deben establecer en **Dual** para que no tenga que hacerlo usted.

La lógica de propagación solo recorre en dirección al lado de uno de las relaciones de **uno a varios**.

* No se permite cambiar la tabla *Customer* (Cliente) a **Importación** (en lugar de cambiar *SurveyResponse*) debido a sus relaciones con las tablas *Sales* y *SurveyResponse* de DirectQuery.
* Sí se permite cambiar la tabla *Customer* (Cliente) a **Dual** (en lugar de cambiar *SurveyResponse*). La lógica de propagación establece que la tabla *Geography* (Geografía) también sea **Dual**.

## <a name="storage-mode-usage-example"></a>Ejemplo de uso del modo de almacenamiento
Continuemos con el ejemplo de la sección anterior e imaginemos que se aplica la configuración de la propiedad de **modo de almacenamiento** siguiente:

| Tabla                   | Modo de almacenamiento         |
| ----------------------- |----------------------| 
| *Sales*                 | DirectQuery          | 
| *SurveyResponse*        | Importar               | 
| *Date*                  | Dual                 | 
| *Customer*              | Dual                 | 
| *Geography*             | Dual                 | 


Al establecer estas configuraciones de la propiedad de modo de almacenamiento, se producen los comportamientos siguientes, suponiendo que la tabla *Sales* (Ventas) tiene un volumen de datos considerable.
* Las tablas de dimensiones (*Date* [Fecha], *Customer* [Cliente] y *Geography* [Geografía]) se almacenan en caché, por lo que los tiempos de carga de informes iniciales deben ser rápidos al recuperar los valores de segmentación que se van a mostrar.
* Si la tabla *Sales* (Ventas) no se almacena en caché, se producen los resultados siguientes:
    * Se mejoran los tiempos de actualización de los datos y se reduce el consumo de memoria
    * Las consultas de informe basadas en la tabla *Sales* (Ventas) se ejecutan en el modo DirectQuery, lo que puede tardar un poco más pero son más cercanas al tiempo real porque no se introduce ninguna latencia de almacenamiento en caché

* Las consultas de informe basadas en la tabla *SurveyResponse* se devuelven desde la caché en memoria y, por tanto, deben ser relativamente rápidas.

## <a name="queries-that-hit-or-miss-the-cache"></a>Consultas que aciertan o pierden la memoria caché

Mediante la conexión de **SQL Profiler** con el puerto de diagnóstico de **Power BI Desktop**, puede ver qué consultas aciertan o pierden la caché en memoria mediante un seguimiento basado en los eventos siguientes:

* Eventos de consultas\Inicio de consulta
* Procesamiento de consulta\Inicio de consulta de Vertipaq SE
* Procesamiento de consulta\Inicio de consulta DirectQuery

Para cada evento de *Inicio de consulta*, compruebe otros eventos con el mismo *ActivityID*. Por ejemplo, si no hay ningún evento *Inicio de consulta DirectQuery* pero sí un evento *Inicio de consulta de Vertipaq SE*, la consulta se respondió desde la caché.

Las consultas que hacen referencia a las tablas del modo **Dual** devuelven datos de la caché si es posible; de lo contrario, se revierten a DirectQuery.

Siguiendo con el ejemplo anterior, la consulta siguiente solo hace referencia a una columna de la tabla *Date* (Fecha) que está en el modo **Dual**. Por tanto, debe acertar la caché.

![Script para el diagnóstico del modo de almacenamiento](media/desktop-storage-mode/storage-mode_06.png)

La consulta siguiente solo hace referencia a una columna de la tabla *Sales* (Ventas), que está en el modo **DirectQuery**. Por tanto, *no* debe acertar la caché.

![Script para el diagnóstico del modo de almacenamiento](media/desktop-storage-mode/storage-mode_07.png)

La consulta siguiente resulta interesante porque combina ambas columnas. Esta consulta no acertará la caché. Inicialmente podría esperar que recupere los valores de *CalendarYear* desde la caché y los valores de *SalesAmount* desde el origen y luego combine los resultados, pero esto sería menos eficaz que enviar la operación SUM/GROUP BY al sistema de origen. Si la operación se transfiere al origen, la cantidad de filas devueltas probablemente será mucho menor. 

![Script para el diagnóstico del modo de almacenamiento](media/desktop-storage-mode/storage-mode_08.png)

> [!NOTE]
> Este comportamiento es distinto del que se describe en las [relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md) cuando se combinan las tablas en caché y no en caché.

## <a name="caches-should-be-kept-in-sync"></a>Las cachés se deben mantener sincronizadas

Las consultas que se muestran en la sección anterior muestran que las tablas de tipo **Dual** a veces aciertan la caché y a veces no lo hacen. Debido a esto, si la caché está obsoleta, se pueden devolver distintos valores. La ejecución de consultas no intentará enmascarar los problemas de datos mediante, por ejemplo, el filtrado de los resultados de DirectQuery para coincidir con los valores en caché. Es su responsabilidad conocer los flujos de datos y debe diseñar en consecuencia. En caso de ser necesario, hay técnicas establecidas para controlar este tipo de casos en el origen.

El modo de almacenamiento **dual** es una optimización del rendimiento. Solo se debe usar de maneras que no pongan en peligro la capacidad de cumplir con los requisitos empresariales. Para el comportamiento alternativo, considere usar las técnicas que se describen en el artículo [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md).

## <a name="data-view"></a>Vista de datos
Si al menos una tabla del conjunto de datos tiene el **modo de almacenamiento** establecido en Importación o en Dual, aparece la pestaña **Vista de datos**.

![Vista de datos en Power BI Desktop](media/desktop-storage-mode/storage-mode_09.png)

Cuando se seleccionan en *Vista de datos**, las tablas **Dual** e **Importación** muestran los datos en caché. Las tablas de DirectQuery no muestran datos y se muestra un mensaje que establece que no se pueden mostrar las tablas DirectQuery.


## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Existen algunas limitaciones para esta versión del **modo de almacenamiento** y su correlación con los **modelos compuestos**.

Los orígenes de Live Connect (multidimensionales) siguientes no se pueden usar con los **modelos compuestos**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de datos de Power BI
* Azure Analysis Services

Al conectarse a esos orígenes multidimensionales mediante DirectQuery, no se puede conectar también a otro origen de DirectQuery ni combinar con los datos importados.

Las limitaciones existentes de usar DirectQuery siguen aplicándose cuando se usan los **modelos compuestos**. Muchas de esas limitaciones son ahora por tabla, en función del **modo de almacenamiento** de la tabla. Por ejemplo, una columna calculada en una tabla importada puede hacer referencia a otras tablas, pero una columna calculada en una tabla de DirectQuery sigue restringida para hacer referencia solo a columnas de la misma tabla. Otras limitaciones se aplican al modelo como un todo, si cualquiera de las tablas dentro del modelo son DirectQuery. Por ejemplo, las características **Conclusiones rápidas** y **Preguntas y respuestas** no están disponibles en un modelo si cualquiera de las tablas dentro del mismo tiene un **modo de almacenamiento** de DirectQuery. 

## <a name="next-steps"></a>Pasos siguientes

Los artículos siguientes describen más información sobre los modelos compuestos y también describen DirectQuery detalladamente.

* [Modelos compuestos en Power BI Desktop (versión preliminar)](desktop-composite-models.md)
* [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md)

Artículos sobre DirectQuery:

* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos admitidos por DirectQuery en Power BI](desktop-directquery-data-sources.md)

