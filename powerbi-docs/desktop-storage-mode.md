---
title: Uso del modo de almacenamiento en Power BI Desktop
description: Uso del modo de almacenamiento para controlar si los datos se almacenan en caché en memoria para los informes de Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: e3a7130cf24fb4fb3f4a61c22f2a3874afc53d45
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464578"
---
# <a name="manage-storage-mode-in-power-bi-desktop"></a>Administración del modo de almacenamiento en Power BI Desktop

En Microsoft Power BI Desktop, puede especificar el modo de almacenamiento de una tabla. El modo de almacenamiento le permite controlar si Power BI Desktop almacena datos en caché en memoria para los informes. 

El hecho de establecer el modo de almacenamiento proporciona varias ventajas. Puede establecer el modo de almacenamiento para cada tabla individualmente en el modelo. Esta acción permite un único conjunto de datos, lo cual proporciona las siguientes ventajas:

* **Rendimiento de las consultas**: cuando los usuarios interactúan con objetos visuales en los informes de Power BI, las consultas de expresiones de análisis de datos (DAX) se envían al conjunto de datos. Si almacena datos en caché en memoria establecimiento correctamente el modo de almacenamiento, puede mejorar el rendimiento de consulta y la interactividad de los informes.

* **Conjuntos de datos de gran tamaño**: las tablas que no se almacenan en caché no consumen memoria para el almacenamiento en caché. Puede habilitar el análisis interactivo de conjuntos de datos de gran tamaño que son demasiado grandes o costosos de almacenar completamente en caché en la memoria. Puede elegir las tablas que merezca la pena almacenar en caché y las que no.

* **Optimización de la actualización de datos**: no es necesario actualizar las tablas que no se almacenan en caché. Puede reducir los tiempos de actualización mediante el almacenamiento en caché solo de los datos necesarios para cumplir los acuerdos de nivel de servicio y los requisitos del negocio.

* **Requisitos casi en tiempo real**: las tablas con requisitos casi en tiempo real se pueden beneficiar de que no se almacenan en caché con el fin de reducir la latencia de los datos.

* **Escritura diferida**: la escritura diferida permite que los usuarios profesionales exploren escenarios hipotéticos cambiando los valores de las celdas. Las aplicaciones personalizadas pueden aplicar cambios al origen de datos. Las tablas que no se almacenan en caché pueden mostrar los cambios de inmediato, lo que permite analizar los efectos de manera instantánea.

La configuración del modo de almacenamiento de Power BI Desktop es una de tres características relacionadas:

* **Modelos compuestos**: esta característica permite que un informe tenga dos o varias conexiones de datos, incluidas conexiones DirectQuery o Importación, en cualquier combinación. Para más información, consulte [Usar modelos compuestos en Power BI Desktop](desktop-composite-models.md).

* **Relaciones de varios a varios**: con los modelos compuestos, puede establecer *relaciones de varios a varios* entre las tablas. En una relación varios a varios se eliminan los requisitos de valores únicos en tablas. También permite descartar las soluciones alternativas anteriores, como la presentación de nuevas tablas solo para establecer relaciones. Para obtener más información, vea [Relaciones de varios a varios en Power BI Desktop](desktop-many-to-many-relationships.md).

* **Modo de almacenamiento**: con el modo de almacenamiento, ahora puede especificar los objetos visuales que requieren una consulta a los orígenes de datos de back-end. Los objetos visuales que no requieran una consulta se importarán incluso aunque estén basados en DirectQuery. Esta característica permite mejorar el rendimiento y reducir la carga de back-end. Anteriormente, incluso los objetos visuales simples, como las segmentaciones, iniciaban consultas que se enviaban a los orígenes de back-end. 

## <a name="use-the-storage-mode-property"></a>Uso de la propiedad de modo de almacenamiento

**Modo de almacenamiento** es una propiedad que se puede establecer en cada tabla del modelo y controla cómo Power BI almacena en caché los datos de tabla.

Para establecer la propiedad **Modo de almacenamiento** o ver su configuración actual: 

1. En la vista **Modelo**, seleccione la tabla cuyas propiedades quiera ver o establecer. 
2. En el panel **Propiedades**, expanda la sección **Opciones avanzadas** y la lista desplegable **Modo de almacenamiento**.

   ![Selección de la propiedad de modo de almacenamiento](media/desktop-storage-mode/storage-mode-02.png)

Establezca la propiedad **Modo de almacenamiento** en uno de estos tres valores:

* **Importación**: las tablas importadas con esta configuración se almacenan en caché. Las consultas enviadas al conjunto de datos de Power BI que devuelven datos desde las tablas de importación solo se pueden satisfacer desde los datos en caché.

* **DirectQuery**: las tablas con esta configuración no se almacenan en caché. Las consultas que envíe al conjunto de datos de Power BI (por ejemplo, las consultas DAX) y que devuelvan datos desde las tablas DirectQuery solo se pueden satisfacer mediante la ejecución de consultas a petición al origen de datos. Las consultas que envíe al origen de datos usan el lenguaje de consulta de ese origen de datos (por ejemplo, SQL).

* **Dual**: las tablas con esta configuración pueden actuar como tablas en caché o no en caché, en función del contexto de la consulta enviada al conjunto de datos de Power BI. En algunos casos, puede satisfacer las consultas a partir de datos en caché. Sin embargo, en otros casos puede hacerlo ejecutando una consulta a petición al origen de datos.

El cambio del **modo de almacenamiento** de una tabla a **Importación** es una operación *irreversible*. Una vez establecida, esta propiedad no se puede cambiar después a **DirectQuery** o **Dual**.

> [!NOTE]
> Puede usar el modo de almacenamiento **Dual** en Power BI Desktop y en el servicio Power BI.


## <a name="constraints-on-directquery-and-dual-tables"></a>Restricciones en las tablas de DirectQuery y las tablas duales

Las tablas duales tienen las mismas restricciones funcionales que las tablas de DirectQuery. Estas restricciones pueden incluir transformaciones M limitadas y funciones DAX restringidas en las columnas calculadas. Para obtener más información, vea [Implicaciones de usar DirectQuery](desktop-directquery-about.md#implications-of-using-directquery).

## <a name="propagation-of-the-dual-setting"></a>Propagación de la configuración Dual
Considere el modelo sencillo siguiente, donde todas las tablas provienen de un solo origen que admite la importación y DirectQuery.

![Ejemplo de vista de relaciones para el modo de almacenamiento](media/desktop-storage-mode/storage-mode-04.png)

Imagine que todas las tablas de este modelo están establecidas inicialmente en **DirectQuery**. Si después cambia el **modo de almacenamiento** de la tabla **SurveyResponse** a **Importación**, se mostrará la siguiente ventana de advertencia:

![Ventana de advertencia del modo de almacenamiento](media/desktop-storage-mode/storage-mode-05.png)

Puede establecer las tablas de dimensiones (**Customer**, **Geography** y **Date**) en **Dual** para reducir el número de relaciones débiles en el conjunto de datos y mejorar el rendimiento. Las relaciones débiles implican normalmente al menos una tabla de DirectQuery, donde no se puede insertar lógica de combinación en los sistemas de origen. Como las tablas duales pueden actuar como tablas de DirectQuery o Importación, se evita esta situación.

La lógica de propagación está diseñada para ayudar con los modelos que contienen muchas tablas. Imagine que tiene un modelo con 50 tablas y solo se deben almacenar en caché algunas tablas de hechos (transaccionales). La lógica de Power BI Desktop calcula el conjunto mínimo de tablas de dimensiones que se deben establecer en **Dual** para que no tenga que hacerlo el usuario.

La lógica de propagación solo se desplaza al lado "uno" de las relaciones uno a varios.

## <a name="storage-mode-usage-example"></a>Ejemplo de uso del modo de almacenamiento
Continuemos con el ejemplo de la sección anterior e imaginemos que se aplica la configuración de la propiedad de modo de almacenamiento siguiente:

| Tabla                   | Modo de almacenamiento         |
| ----------------------- |----------------------| 
| Ventas                 | DirectQuery          | 
| SurveyResponse        | Importación               | 
| Fecha                  | Dual                 | 
| Cliente              | Dual                 | 
| Geografía             | Dual                 | 


Al establecer estas propiedades de modo de almacenamiento se producen los comportamientos siguientes, siempre que la tabla **Sales** (Ventas) tenga un volumen de datos considerable:
* Power BI Desktop almacena en caché las tablas de dimensiones (**Date**, **Customer** y **Geography**), por lo que los tiempos de carga de los informes iniciales son rápidos al recuperar los valores de segmentación que se van a mostrar.
* Power BI Desktop no almacena en caché la tabla **Sales**. Al no almacenar esta tabla en caché, Power BI Desktop proporciona los resultados siguientes:
    * Se mejoran los tiempos de actualización de los datos y se reduce el consumo de memoria.
    * Las consultas de informes que se basan en la tabla **Sales** se ejecutan en el modo **DirectQuery**. Es posible que estas consultas tarden más tiempo, pero están más cerca de realizarse en tiempo real, ya que no se ha introducido ninguna latencia de almacenamiento en caché.

* Las consultas de informes que se basan en la tabla **SurveyResponse** se devuelven desde la caché en memoria y, por tanto, son relativamente rápidas.

## <a name="queries-that-hit-or-miss-the-cache"></a>Consultas que aciertan o pierden la memoria caché

Si conecta SQL Profiler al puerto de diagnóstico de Power BI Desktop, puede ver las consultas que alcanzan o no la caché en memoria mediante un seguimiento basado en los eventos siguientes:

* Eventos de consultas\Inicio de consulta
* Procesamiento de consulta\Inicio de consulta de Vertipaq SE
* Procesamiento de consulta\Inicio de consulta DirectQuery

Para cada evento de *Inicio de consulta*, compruebe otros eventos con el mismo *ActivityID*. Por ejemplo, si no hay ningún evento *Inicio de consulta DirectQuery*, pero sí un evento *Inicio de consulta de Vertipaq SE*, significa que la consulta se responde desde la caché.

Las consultas que hacen referencia a las tablas Dual devuelven datos de la caché si es posible; de lo contrario, se revierten a DirectQuery.

Siguiendo con el ejemplo anterior, la consulta siguiente solo hace referencia a una columna de la tabla **Date** (Fecha) que está en el modo **Dual**. Por tanto, la consulta debe alcanzar la caché:

![Script para el diagnóstico del modo de almacenamiento](media/desktop-storage-mode/storage-mode-06.png)

La consulta siguiente solo hace referencia a una columna de la tabla **Sales** (Ventas), que está en el modo **DirectQuery**. Por tanto, *no* debe alcanzar la caché:

![Script para el diagnóstico del modo de almacenamiento](media/desktop-storage-mode/storage-mode-07.png)

La consulta siguiente resulta interesante porque combina ambas columnas. Esta consulta no alcanza la caché. Inicialmente podría esperar que recuperase los valores de **CalendarYear** desde la caché y los valores de **SalesAmount** desde el origen y, luego, combinase los resultados, pero este enfoque sería menos eficaz que enviar la operación SUM/GROUP BY al sistema de origen. Si la operación se transfiere al origen, el número de filas devueltas probablemente será mucho menor: 

![Script para el diagnóstico del modo de almacenamiento](media/desktop-storage-mode/storage-mode-08.png)

> [!NOTE]
> Este comportamiento es distinto del de las [relaciones de varios a varios](desktop-many-to-many-relationships.md) de Power BI Desktop, donde se combinan tablas en caché y no en caché.

## <a name="caches-should-be-kept-in-sync"></a>Las cachés se deben mantener sincronizadas

Las consultas de la sección anterior muestran que las tablas de tipo Dual a veces alcanzan la caché y, otras, no. Como resultado, si la caché está obsoleta, se pueden devolver distintos valores. La ejecución de consultas no intentará enmascarar los problemas de datos mediante, por ejemplo, el filtrado de los resultados de DirectQuery para coincidir con los valores en caché. Es su responsabilidad conocer los flujos de datos y debe diseñar en consecuencia. En caso de ser necesario, hay técnicas establecidas para controlar este tipo de casos en el origen.

El modo de almacenamiento **dual** es una optimización del rendimiento. Solo se debe usar de maneras que no pongan en peligro la capacidad de cumplir con los requisitos empresariales. Para el comportamiento alternativo, considere la posibilidad de usar las técnicas que se describen en [Relaciones de varios a varios en Power BI Desktop](desktop-many-to-many-relationships.md).

## <a name="data-view"></a>Vista de datos
Si al menos una tabla del conjunto de datos tiene el modo de almacenamiento establecido en **Importación** o **Dual**, aparece la pestaña de la vista **Datos**.

![Vista de datos en Power BI Desktop](media/desktop-storage-mode/storage-mode-03.png)

Al seleccionar tablas de tipo Dual e Importación en la vista **Datos**, muestran los datos en caché. Las tablas DirectQuery no muestran datos, y se muestra un mensaje en el que se indica que las tablas DirectQuery no se pueden mostrar.


## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Existen algunas limitaciones para esta versión del modo de almacenamiento y su correlación con los modelos compuestos.

Los orígenes de conexión dinámica (multidimensionales) siguientes no se pueden usar con los modelos compuestos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de datos de Power BI
* Azure Analysis Services

Al conectarse a esos orígenes multidimensionales mediante DirectQuery, no se puede conectar a otro origen de DirectQuery ni combinarlo con los datos importados.

Las limitaciones existentes del uso de DirectQuery siguen aplicándose cuando se usan los modelos compuestos. Muchas de esas limitaciones son ahora por tabla, en función del modo de almacenamiento de la tabla. Por ejemplo, una columna calculada en una tabla importada puede hacer referencia a otras tablas, pero una columna calculada en una tabla de DirectQuery sigue restringida para hacer referencia solo a columnas de la misma tabla. Otras limitaciones se aplican al modelo como un todo, si cualquiera de las tablas dentro del modelo son DirectQuery. Por ejemplo, las características Conclusiones rápidas y Preguntas y respuestas no están disponibles en un modelo si cualquiera de las tablas dentro del mismo tiene un modo de almacenamiento de DirectQuery. 

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre los modelos compuestos y DirectQuery, consulte los siguientes artículos:
* [Modelos compuestos en Power BI Desktop](desktop-composite-models.md)
* [Relaciones de varios a varios en Power BI Desktop](desktop-many-to-many-relationships.md)
* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos admitidos por DirectQuery en Power BI](desktop-directquery-data-sources.md)
