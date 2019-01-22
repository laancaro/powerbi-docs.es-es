---
title: Usar modelos compuestos en Power BI Desktop
description: Creación de modelos de datos con varias conexiones de datos y relaciones de varios a varios en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/12/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 734af04ae515b1cae19b5afc99166619a85ab828
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290476"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>Usar modelos compuestos en Power BI Desktop

Anteriormente en Power BI Desktop, cuando se usaba DirectQuery en un informe, no se permitía usar ninguna otra conexión de datos en ese informe, ya fuese que se tratara de DirectQuery o importación. Con los modelos compuestos esa restricción ya no existe. Un informe puede incluir sin problemas conexiones de datos de más de una conexión de datos de DirectQuery o de importación, en la combinación de su preferencia.

![Modelos compuestos en Power BI Desktop](media/desktop-composite-models/composite-models_01.png)

La funcionalidad de modelos compuestos de Power BI Desktop consta de tres características relacionadas:

* **Modelos compuestos**: esta característica permite que un informe tenga varias conexiones de datos, incluidas conexiones de DirectQuery o importación, en cualquier combinación. En este artículo se describen los modelos compuestos en detalle.

* **Relaciones de varios a varios**: mediante el uso de *modelos compuestos*, puede establecer *relaciones de varios a varios* entre las tablas. Este enfoque elimina los requisitos de valores únicos en tablas. También permite descartar las soluciones alternativas anteriores, como el hecho de presentar nuevas tablas solo para establecer relaciones. Para obtener más información, vea [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md).

* **Modo de almacenamiento**: ahora puede especificar los objetos visuales que requieren una consulta a los orígenes de datos back-end. Los objetos visuales que no requieran una consulta se importarán incluso aunque estén basados en DirectQuery. Esta característica permite mejorar el rendimiento y reducir la carga de back-end. Anteriormente, incluso los objetos visuales simples, como las segmentaciones, iniciaban consultas que se enviaban a los orígenes de back-end. Para obtener más información, vea [Modo de almacenamiento en Power BI Desktop (versión preliminar)](desktop-storage-mode.md).


## <a name="use-composite-models"></a>Usar modelos compuestos

Con los modelos compuestos puede conectarse a una gran variedad de orígenes de datos al usar Power BI Desktop o el servicio Power BI. Puede realizar esas conexiones de datos de dos maneras:

* Mediante la importación de datos a Power BI, que es la manera más común para obtener datos.
* Mediante una conexión directa a los datos en su repositorio de origen inicial con DirectQuery. Para obtener más información acerca de DirectQuery, vea [Uso de DirectQuery en Power BI](desktop-directquery-about.md).

Usar DirectQuery con los *modelos compuestos* posibilita crear un modelo de Power BI (como un archivo *.pbix* de Power BI Desktop único) que tiene como resultado uno de los siguientes o ambos:

* Combina los datos de uno o varios orígenes de DirectQuery.
* Combina los datos de orígenes de DirectQuery e importa los datos.

Por ejemplo, mediante el uso de modelos compuestos, puede crear un modelo que combine los siguientes tipos de datos:

* Datos de ventas de un almacenamiento de datos empresarial.
* Datos de objetivos de ventas de una base de datos de SQL Server departamental.
* Datos que se importan a partir de una hoja de cálculo. 

Un modelo que combina datos de más de un origen de DirectQuery o que combina DirectQuery con datos importados se conoce como un *modelo compuesto*.

> [!NOTE]
> A partir de la versión de octubre de 2018 de Power BI Desktop, *puede* publicar modelos compuestos en el servicio Power BI. Para la actualización programada y la actualización del icono del panel, los modelos compuestos en el servicio Power BI se comportan de la misma manera que los modelos de importación. 

Puede crear relaciones entre tablas como siempre lo ha hecho, incluso cuando esas tablas provienen de distintos orígenes, con estas restricciones: se debe definir que toda relación proveniente de distintos orígenes tenga una cardinalidad de *varios a varios*, independientemente de su cardinalidad real. De ese modo, el comportamiento de dichas relaciones es el mismo que el normal para las relaciones de *varios a varios*, tal como se describe en [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md). 

> [!NOTE]
> En el contexto de los modelos compuestos, todas las tablas importadas son efectivamente un solo origen, independientemente del origen de datos subyacente real desde donde se importan.   

## <a name="example-of-a-composite-model"></a>Ejemplo de un modelo compuesto

Un ejemplo de *modelo compuesto* podría ser un informe que se ha conectado a un almacenamiento de datos corporativos en SQL Server mediante el uso de DirectQuery. En este caso, el almacenamiento de datos contiene datos de *Sales by Country* (Ventas por país), *Quarter* (Trimestre) y *Bike (Product)* (Bicicleta [Producto]), como se muestra en la siguiente imagen:

![Vista de relaciones para los modelos compuestos](media/desktop-composite-models/composite-models_04.png)

En este momento, podría crear objetos visuales sencillos con campos de este origen. Por ejemplo, la siguiente imagen muestra las ventas totales por *ProductName* para un trimestre seleccionado. 

![Objeto visual basado en los datos](media/desktop-composite-models/composite-models_05.png)

Pero ¿qué ocurre si tiene datos en una hoja de cálculo de Excel de Office sobre el administrador de producto asignado a cada artículo con la prioridad de marketing? Si quiere conocer el valor de *Sales Amount* (Cantidad de ventas) por *Product Manager* (Administrador de producto), es posible que no se puedan agregar estos datos locales en el almacenamiento de datos corporativos. O bien, en el mejor de los casos, se trata de una tarea que puede llevar meses. 

Es posible importar los datos de ventas del almacenamiento de datos, en lugar de usar DirectQuery. Después, se podrían combinar los datos de ventas con los datos que haya importado desde la hoja de cálculo. No obstante, este enfoque es poco razonable, por los motivos que llevaron a usar DirectQuery en primer lugar. Los motivos pueden incluir:

* Alguna combinación de las reglas de seguridad aplicadas en el origen subyacente.
* Existencia de la necesidad de poder consultar los datos más recientes.
* Dimensiones de los datos, que pueden ser bastante grandes. 

Aquí es donde aparecen los modelos compuestos. Los modelos compuestos le permiten conectarse al almacenamiento de datos a través de DirectQuery y luego usar GetData para los orígenes adicionales. En este ejemplo, establecemos primero la conexión de DirectQuery al almacén de datos corporativos. Utilice la función GetData, elija Excel y, después, vaya a la hoja de cálculo que contiene los datos locales. Por último, importe la hoja de cálculo que contiene los valores *Product Names* (Nombres de producto), *Sales Manager* (Administrador de ventas) asignado y *Priority* (Prioridad).  

![Ventana Navegador](media/desktop-composite-models/composite-models_06.png)

En la lista **Campos**, puede ver dos tablas: la tabla *Bike* (Bicicleta) original de SQL Server y una tabla **ProductManagers** nueva. La nueva tabla contiene los datos que se han importado de Excel. 

![Vista de campos de las tablas](media/desktop-composite-models/composite-models_07.png)

Del mismo modo, en la vista **Relaciones** en Power BI Desktop, ahora veremos una tabla adicional denominada **ProductManagers** (Administradores de productos). 

![Vista de relaciones de las tablas](media/desktop-composite-models/composite-models_08.png)

Ahora necesitamos relacionar estas tablas con las otras en el modelo. Como siempre, creamos una relación entre la tabla **Bike** (Bicicleta) de SQL Server y la tabla **ProductManagers** importada. Es decir, la relación se establece entre *Bike[ProductName]* y *ProductManagers[ProductName]*. Como se ha explicado anteriormente, todas las relaciones entre el origen deben tener la cardinalidad de *varios a varios* predeterminada. 

![Ventana Crear diálogo](media/desktop-composite-models/composite-models_09.png)

Una vez que se ha establecido esta relación, se muestra en la vista **Relaciones** en Power BI Desktop tal como se esperaría.

![La nueva vista de relaciones](media/desktop-composite-models/composite-models_10.png)

Ahora podemos crear objetos visuales mediante cualquiera de los campos de la lista **Campos**. Este enfoque combina sin problemas datos de varios orígenes. Por ejemplo, el valor *SalesAmount* (Cantidad de ventas) total para cada *Product Manager* (Administrador de productos) se muestra en la siguiente imagen: 

![El panel Campos](media/desktop-composite-models/composite-models_11.png)

En el ejemplo siguiente se muestra un caso común de una tabla de *dimensiones*, como *Product* (Producto) o *Customer* (Cliente), que se extiende con algunos datos adicionales que se importan desde otro lugar. También es posible hacer que las tablas usen DirectQuery para conectarse a diversos orígenes. Para continuar con el ejemplo, imaginemos que *Sales Targets* (Objetivos de ventas) por *Country* (País) y *Period* (Período) se almacenan en una base de datos departamental independiente. Como es habitual, puede usar *GetData* para conectarse a esos datos, tal como se muestra en la siguiente imagen: 

![La ventana Navegador](media/desktop-composite-models/composite-models_12.png)

Como hicimos anteriormente, podemos crear relaciones entre la tabla nueva y las demás tablas del modelo, y después crear objetos visuales que combinen los datos de la tabla. Volvamos a examinar la vista **Relaciones**, donde establecimos relaciones nuevas:

![La vista de relaciones con varias tablas](media/desktop-composite-models/composite-models_13.png)

La siguiente imagen se basa en los nuevos datos y las relaciones que hemos creado. El objeto visual en la esquina inferior izquierda muestra el valor *Sales Amount* (Cantidad de ventas) total frente a *Target* (Objetivo), mientras que el cálculo de la varianza muestra la diferencia. Los datos de *Sales Amount* (Cantidad de ventas) y *Target* (Objetivo) proceden de dos bases de datos de SQL Server diferentes. 

![Imagen que muestra más datos](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>Establecer el modo de almacenamiento

Cada tabla de un modelo compuesto tiene un modo de almacenamiento que indica si la tabla se basa en DirectQuery o en importación. El modo de almacenamiento se puede ver y modificar en el panel **Propiedad**. Para mostrar el modo de almacenamiento, haga clic en una tabla en la lista **Campos** y, después, seleccione **Propiedades**. En la siguiente imagen se muestra el modo de almacenamiento para la tabla **SalesTargets** (Objetivos de ventas).

![Establecimiento del modo de almacenamiento](media/desktop-composite-models/composite-models_15.png)

El modo de almacenamiento también se puede ver en la información sobre herramientas de cada tabla.

![Información en pantalla que muestra el modo de almacenamiento](media/desktop-composite-models/composite-models_16.png)

En el caso de los archivos de Power BI Desktop (.*.pbix*) que contengan tablas DirectQuery e Importación, la barra de estado mostrará un modo de almacenamiento denominado **Combinado**. Puede hacer clic en ese término en la barra de estado y cambiar fácilmente todas las tablas para importación.

Para obtener más información sobre el modo de almacenamiento, vea [Modo de almacenamiento en Power BI Desktop (versión preliminar)](desktop-storage-mode.md).  

## <a name="calculated-tables"></a>Tablas calculadas

Puede agregar tablas calculadas a un modelo que use DirectQuery. Las expresiones de análisis de datos (DAX) que definen la tabla calculada pueden hacer referencia a cualquier tabla importada o de DirectQuery, o una combinación de ambas. 

Las tablas calculadas siempre se importan y los datos se actualizan cuando se actualizan las tablas. Si una tabla calculada hace referencia a una tabla DirectQuery, los objetos visuales que hagan referencia a la tabla DirectQuery siempre mostrarán los valores más recientes en el origen subyacente. Como alternativa, los objetos visuales que hacen referencia a la tabla calculada muestran los valores en el momento de la última actualización de la tabla calculada.

## <a name="security-implications"></a>Implicaciones de seguridad 

Los modelos compuestos tienen algunas implicaciones de seguridad. Una consulta enviada a un origen de datos puede incluir valores de datos que se han recuperado desde otro origen de datos. En el ejemplo anterior, el objeto visual que muestra *Sales Amount* (Cantidad de ventas) por *Product Manager* (Administrador de productos) envía una consulta SQL para la base de datos relacional **Sales** (Ventas). La consulta SQL puede contener los nombres de *Product Managers* (Administradores de producto) y sus *Products* (Productos) asociados. 

![Script que muestra las implicaciones de seguridad](media/desktop-composite-models/composite-models_17.png)

Por lo tanto, la información que se almacena en la hoja de cálculo ahora se incluye en una consulta enviada a la base de datos relacional. Si esta información es confidencial, se deben considerar las implicaciones de seguridad. En concreto, tenga en cuenta lo siguiente:

* Cualquier administrador de la base de datos que pueda ver los seguimientos o registros de auditoría puede ver esta información, incluso sin permisos para los datos de su fuente original. En este ejemplo, el administrador necesitaría permisos para el archivo de Excel.

* Se debe considerar la configuración de cifrado para cada origen. Lo habitual es querer evitar tener que recuperar la información desde un origen a través de una conexión cifrada y, después, incluirla de forma accidental en una consulta que se envía a otro origen a través de una conexión no cifrada. 

Con el fin de permitir la confirmación de que se consideraron todas las implicaciones de seguridad, Power BI Desktop muestra un mensaje de advertencia cuando se realiza una acción para crear un modelo compuesto.  

Por motivos similares, se debe tener cuidado al abrir un archivo de Power BI Desktop enviado desde un origen que no es de confianza. Si el archivo contiene modelos compuestos, la información que alguien recupere de un origen con las credenciales del usuario que abre el archivo se enviará a otro origen de datos como parte de la consulta. El autor del archivo de Power BI Desktop malintencionado podría ver esta información. Por lo tanto, al abrir inicialmente un archivo de Power BI Desktop que contiene varios orígenes, Power BI Desktop muestra una advertencia. La advertencia es similar a la que aparece al abrir un archivo que incluye consultas SQL nativas.  

## <a name="performance-implications"></a>Implicaciones de rendimiento  

Siempre se debe considerar el rendimiento al usar DirectQuery, principalmente para garantizar que el origen de back-end tenga los recursos suficientes para proporcionar una buena experiencia para los usuarios. Para que la experiencia se considere buena, los objetos visuales deben actualizarse en cinco segundos o menos. También debe seguir el consejo sobre el rendimiento que aparece en el artículo [Uso de DirectQuery en Power BI](desktop-directquery-about.md). 

El uso de modelos compuestos agrega consideraciones de rendimiento adicionales. Un solo objeto visual puede producir que se envíen consultas a varios orígenes, lo que a menudo pasa los resultados de una consulta a un segundo origen. Esta situación puede generar las siguientes formas de ejecución:

* **Consulta SQL con un gran número de valores literales**: por ejemplo, un objeto visual que solicita el valor *Sales Amount* (Cantidad de ventas) total para un conjunto de *Product Managers* (Administradores de productos) seleccionado primero tendría que determinar qué *Products* (Productos) administraban. Esta secuencia debe realizase antes de que el objeto visual envíe una consulta SQL que incluya todos los identificadores de producto en una cláusula *WHERE*.

* **Consulta SQL con un nivel de granularidad inferior y en la que los datos se agregan de forma local posteriormente**: como el número de *Products* (Productos) que cumplen los criterios de filtro de *Product Manager* (Administrador de productos) va en aumento, puede resultar ineficaz o imposible incluir todos los productos en una cláusula *WHERE*. En su lugar, puede consultar el origen relacional en el nivel inferior de *Product* (Producto) y después agregar los resultados localmente. Si la cardinalidad de los *Productos* (Productos) supera un límite de 1 millón, la consulta generará un error.

* **Varias consultas SQL, una por grupo por valor**: cuando la agregación usa **DistinctCount** (Recuento continuo) y la agrupa por una columna desde otro origen y si el origen externo no admite pasar de manera eficaz varios valores literales que definen la agrupación, es necesario enviar una consulta SQL por grupo por valor. 

   Por ejemplo, un objeto visual que solicita un recuento distinto de *CustomerAccountNumber* (Número de cuenta de cliente) (desde la tabla de SQL Server) por *Product Manager* (Administrador de productos) (importado desde una hoja de cálculo) debería pasar los detalles de la tabla *Product Managers* (Administradores de productos) en la consulta enviada a SQL Server. Esta acción es inviable a través de otros orígenes (por ejemplo, Redshift). En su lugar, habría una consulta SQL enviada por *Sales Manager* (Administrador de ventas) (hasta algún límite práctico, momento en el cual se generaría un error en la consulta). 

Cada uno de estos casos tiene sus propias implicaciones en el rendimiento y los detalles exactos varían en función de cada origen de datos. Aunque la cardinalidad de las columnas usadas en la relación que combina ambos orígenes permanece baja (unos pocos miles), el rendimiento no debería verse afectado. A medida que crece esta cardinalidad, debe prestar más atención a la repercusión en el rendimiento resultante. Aplique estas instrucciones a modo de regla general. 

Además, el uso de las relaciones de *varios a varios* significa que se deben enviar consultas independientes al origen subyacente de cada nivel total o subtotal, en lugar de agregar localmente los valores detallados. Un objeto visual de tabla simple con totales podría enviar dos consultas SQL en lugar de una. 

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Existen algunas limitaciones para esta versión de los modelos compuestos.

Los orígenes de Live Connect (multidimensionales) siguientes no se pueden usar con los modelos compuestos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de datos de Power BI
* Azure Analysis Services

Al conectarse a esos orígenes multidimensionales mediante DirectQuery, no se puede conectar a otro origen de DirectQuery ni combinar con los datos importados.

Las limitaciones existentes de DirectQuery siguen aplicándose cuando se usan los modelos compuestos. Muchas de esas limitaciones son ahora por tabla, en función del modo de almacenamiento de la tabla. Por ejemplo, una columna calculada en una tabla Importación puede hacer referencia a otras tablas, pero una columna calculada en una tabla DirectQuery puede hacer referencia solo a columnas de la misma tabla. Otras limitaciones se aplican al modelo como un todo, si cualquiera de las tablas dentro del modelo son DirectQuery. Por ejemplo, las características Conclusiones rápidas y Preguntas y respuestas no están disponibles en un modelo si cualquiera de las tablas dentro del mismo tiene un modo de almacenamiento de DirectQuery. 

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre los modelos compuestos y DirectQuery, consulte los siguientes artículos:
* [Relaciones de varios a varios en Power BI Desktop (versión preliminar)](desktop-many-to-many-relationships.md)
* [Modo de almacenamiento en Power BI Desktop (versión preliminar)](desktop-storage-mode.md)
* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos admitidos por DirectQuery en Power BI](desktop-directquery-data-sources.md)

