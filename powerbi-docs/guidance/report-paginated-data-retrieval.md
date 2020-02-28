---
title: Guía de recuperación de datos de informes paginados
description: Instrucciones para crear orígenes de datos y conjuntos de datos para informes paginados de Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 1da75b14f628c8c765ea89a34dd2a2665cdf9a4b
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530450"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Guía de recuperación de datos de informes paginados

Este artículo está dirigido a los autores de informes que diseñan [informes paginados](../paginated-reports-report-builder-power-bi.md) de Power BI. En él se proporcionan recomendaciones que le ayudarán a diseñar una recuperación de datos eficaz.

## <a name="data-source-types"></a>Tipos de origen de datos

Los informes paginados admiten de forma nativa orígenes de datos relacionales y analíticos. Estos orígenes se clasifican aún más como locales o en la nube. Los orígenes de datos locales (ya sean hospedados localmente o en una máquina virtual) requieren una puerta de enlace de datos para que Power BI pueda conectarse a ellos, mientras que en el caso de los basados en la nube, Power BI se puede conectar a ellos directamente con una conexión a Internet.

Si puede elegir el tipo de origen de datos (posiblemente sea el caso cuando el proyecto es nuevo), se recomienda usar orígenes de datos basados en la nube. Los informes paginados pueden conectarse con una latencia de red menor, especialmente cuando los orígenes de datos residen en la misma región que el inquilino de Power BI. Además, existe la posibilidad de conectarse a estos orígenes mediante inicio de sesión único (SSO). Esto significa que la identidad del usuario del informe puede fluir hasta el origen de datos, lo que permite que se apliquen permisos de nivel de fila por usuario. Actualmente, SSO no es compatible con los orígenes de datos locales (es decir, SQL Server Analysis Services no puede aplicar permisos de nivel de fila por usuario).

> [!NOTE]
> Aunque actualmente no es posible conectarse a bases de datos locales mediante SSO, sí que se pueden aplicar permisos de nivel de fila. Para ello, hay que pasar el campo integrado **UserID** a un parámetro de consulta de conjunto de datos. El origen de datos deberá almacenar los valores de nombre principal de usuario (UPN) de forma tal que sea posible filtrar correctamente los resultados de la consulta.
>
> Imaginemos, por ejemplo, que cada vendedor se almacena como una fila en una tabla denominada **Vendedores**.  La tabla tiene columnas para UPN y, también, la región de ventas del vendedor. En el momento de la consulta, la tabla se filtra por el UPN del usuario del informe y, asimismo, se relaciona con hechos de ventas mediante una combinación interna. De este modo, la consulta filtra eficazmente las filas de hechos de ventas para mostrar los de la región de ventas del usuario del informe en cuestión.

### <a name="relational-data-sources"></a>Orígenes de datos relacionales

Por lo general, los orígenes de datos relacionales son adecuados con informes de estilo operativo, como las facturas de ventas. También son apropiados en informes donde es necesario recuperar conjuntos de datos de gran tamaño (más de 10 000 filas). Aparte de esto, los orígenes de datos relacionales pueden definir procedimientos almacenados que los conjuntos de datos del informe pueden ejecutar. Los procedimientos almacenados reportan diversas ventajas:

- Parametrización
- Encapsulación de la lógica de programación, lo que permite una preparación de datos más compleja (por ejemplo, tablas temporales, cursores o funciones escalares definidas por el usuario)
- Mejor capacidad de mantenimiento, lo que permite actualizar la lógica del procedimiento almacenado con suma facilidad. En algunos casos, esto se puede hacer sin necesidad de modificar y volver a publicar los informes paginados (los nombres de columna y los tipos de datos permanecen inalterados).
- Mejor rendimiento, ya que los planes de ejecución se almacenan en la memoria caché para que se puedan reutilizar
- Reutilización de procedimientos almacenados en varios informes

En Power BI Report Builder, se puede usar el diseñador de consultas relacionales para crear gráficamente una instrucción de consulta, pero esto solo es posible con orígenes de datos de Microsoft.

### <a name="analytic-data-sources"></a>Orígenes de datos analíticos

Los orígenes de datos analíticos son adecuados en informes operativos y analíticos, y pueden proporcionar resultados de consulta de resumen rápido incluso con volúmenes de datos muy grandes. Los KPI y las medidas de modelo pueden encapsular reglas de negocio complejas para obtener un resumen de los datos, pero estos orígenes de datos no son adecuados en informes donde es necesario recuperar conjuntos de datos de gran tamaño (más de 10 000 filas).

En Power BI Report Builder, existe la posibilidad de elegir entre dos diseñadores de consultas: el diseñador de consultas de DAX de Analysis Services y diseñador de consultas de MDX de Analysis Services. Estos diseñadores se pueden usar con orígenes de datos de conjuntos de datos de Power BI o con cualquier modelo de SQL Server Analysis Services o Azure Analysis Services, sea tabular o multidimensional.

Le recomendamos que use el diseñador de consultas de DAX, siempre y cuando satisfaga por completo sus necesidades de consulta. Si el modelo no define las medidas que necesita, deberá cambiar al modo de consulta. En este modo, puede personalizar la instrucción de consulta agregando expresiones (para obtener un resumen).

El diseñador de consultas de MDX requiere que el modelo incluya medidas. Este diseñador tiene dos funciones que el diseñador de consultas de DAX no admite. En concreto, permite lo siguiente:

- Definir miembros calculados en el nivel de consulta (en MDX).
- Configurar regiones de datos para solicitar [agregados de servidor](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) en grupos no detallados. Si es necesario que el informe muestre resúmenes de medidas de suma parcial o de no suma (como medidas de cálculo de inteligencia de tiempo o medidas de recuento distintivas), probablemente sea más práctico usar agregados de servidor que recuperar las filas de detalle de bajo nivel y hacer que el informe calcule los resúmenes.

## <a name="query-result-size"></a>Tamaño del resultado de la consulta

En general, lo mejor es recuperar únicamente los datos que son necesarios en el informe, de modo que no recupere columnas ni filas prescindibles en el informe.

Para limitar las filas, conviene aplicar siempre los filtros más restrictivos y definir consultas de agregado. Las consultas de agregado agrupan y resumen los datos de origen para recuperar los resultados más pormenorizados. Por ejemplo, imaginemos que el informe debe mostrar un resumen de las ventas de los vendedores. En lugar de recuperar todas las filas de pedidos de ventas, crearemos una consulta de conjunto de datos que agrupe por vendedor y que resuma las ventas de cada grupo.

## <a name="expression-based-fields"></a>Campos basados en expresiones

Un conjunto de datos de informe se puede extender con campos basados en expresiones. Por ejemplo, si un conjunto de datos contiene nombres y apellidos de clientes, probablemente nos interese un campo que concatene ambos campos para generar el nombre completo del cliente. Para lograr este cálculo, existen dos opciones. Puede:

- Crear un _campo calculado_, que es un campo de conjunto de campos basado en una expresión.
- Insertar una expresión directamente en la consulta del conjunto de datos (usando el lenguaje nativo del origen de datos) y esto dará como resultado un campo de conjunto de datos normal.

Siempre que sea posible, recomendamos la última opción. Existen dos motivos de peso por los que es mejor insertar expresiones directamente en la consulta del conjunto de datos:

- Puede que el origen de datos esté optimizado para evaluar la expresión de forma más eficaz que Power BI (es el caso específicamente de las bases de datos relacionales).
- El rendimiento del informe es mejor, porque no es necesario que Power BI materialice los campos calculados antes de representar el informe. Los campos calculados pueden ampliar considerablemente el tiempo de representación del informe cuando los conjuntos de datos recuperan un gran número de filas.

## <a name="field-names"></a>Nombres de campo

Cuando se crea un conjunto de datos, el nombre que se asigna automáticamente a los campos es el mismo que el de las columnas de consulta, cuando es probable que estos nombres no sean descriptivos o intuitivos. También es posible que los nombres de columna de la consulta de origen contengan caracteres que no se pueden usar en los identificadores de objeto de lenguaje RDL (Report Definition Language), como, por ejemplo, espacios y símbolos. En este caso, los caracteres prohibidos se reemplazan por un carácter de subrayado (_).

Se recomienda comprobar antes que todos los nombres de campo son descriptivos, concisos y tienen sentido. Si no es así, se recomienda cambiarles el nombre _antes de_ empezar el diseño del informe, ya que los campos cuyo nombre ha cambiado no propagan esos cambios a las expresiones que se usan en el diseño del informe. Si, en cambio, decide cambiar el nombre de los campos después de haber iniciado el diseño del informe, deberá encontrar y actualizar todas las expresiones incorrectas.

## <a name="filter-vs-parameter"></a>Filtro frente a parámetro

Es bastante probable que los diseños de informes paginados tengan parámetros de informe. Los parámetros de informe se suelen usar para pedir al usuario del informe que filtre el informe. Como autor de un informe paginado, tiene dos maneras filtrar un informe. Puede asignar un parámetro de informe a:

- Un _filtro_ de conjunto de datos, en cuyo caso los valores de parámetro del informe se usan para filtrar los datos ya recuperados por el conjunto de datos.
- Un _parámetro_ de conjunto de datos, en cuyo caso los valores del parámetro de informe se insertan en la consulta nativa que se envía al origen de datos.

> [!NOTE]
> Todos los conjuntos de datos de informe se almacenan en la memoria caché de _cada sesión_ durante 10 minutos _desde su último uso_. Un conjunto de datos se puede reutilizar cuando se envían nuevos valores de parámetro (filtrado), cuando el informe se representa en un formato diferente o cuando se interactúa de algún modo con el diseño del informe, como al alternar la visibilidad o al ordenar.

Veamos pues un ejemplo de un informe de ventas que tiene un único parámetro de informe para filtrar el informe por un único año. El conjunto de datos recupera las ventas de _todos los años_, debido a que el parámetro de informe se asigna a los filtros del conjunto de datos. El informe muestra los datos del año solicitado, que es un subconjunto de los datos del conjunto de datos. Cuando el usuario del informe cambia el parámetro de informe a otro año y visualiza el informe, Power BI no necesita recuperar ningún dato de origen, sino que aplica un filtro distinto al conjunto de datos ya almacenado en la memoria caché. Cuando el conjunto de datos está almacenado en la memoria caché, se puede filtrar con enorme rapidez.

Veamos ahora un diseño de informe diferente. Esta vez, el diseño de informe asigna el parámetro de informe de año de ventas a un parámetro de conjunto de datos. De este modo, Power BI inserta el valor de año en la consulta nativa y el conjunto de datos recupera solo los datos de ese año. Cada vez que el usuario del informe cambia el valor del parámetro de informe de año y visualiza el informe, el conjunto de datos recupera un nuevo resultado de la consulta, exclusivo de ese año.

Ambos métodos de diseño permiten filtrar los datos del informe y pueden funcionar bien con sus diseños de informe. Con todo, un diseño optimizado dependerá de los volúmenes de datos anticipados, de la volatilidad de los datos y de los comportamientos anticipados de los usuarios del informe.

Le recomendamos que use el _filtrado de conjunto de datos_ si prevé que un subconjunto diferente de filas del conjunto de datos se va a reutilizar muchas veces (con lo que ahorrará mucho tiempo de representación, ya que no es necesario recuperar datos nuevos). En este escenario, está claro que el coste de recuperar un conjunto de datos de gran volumen se compensa con el número de veces que se va a volver a usar. Por lo tanto, resulta útil para las consultas que tardan mucho tiempo en generarse. Pero cuidado: almacenar en la memoria caché conjuntos de datos grandes de cada usuario puede afectar negativamente al funcionamiento y al rendimiento de la capacidad.

Le recomendamos que use la _parametrización de conjunto de datos_ cuando prevea que es poco probable que se solicite un subconjunto diferente de filas del conjunto de datos, o si existe la posibilidad de que el número de filas del conjunto de datos que se van a filtrar sea muy grande (lo cual es poco práctico almacenar en la memoria caché). Este método de diseño también funciona bien cuando el almacén de datos es volátil. En este caso, con cada cambio del valor de parámetro del informe se recuperarán datos actualizados.

## <a name="non-native-data-sources"></a>Orígenes de datos no nativos

Si necesita desarrollar informes paginados basados en orígenes de datos que no [se admiten de forma nativa en los informes paginados](../paginated-reports-data-sources.md), puede desarrollar en primer lugar un modelo de datos de Power BI Desktop. De este modo, podrá conectarse a más de 100 [orígenes de datos de Power BI](../power-bi-data-sources.md). Una vez publicado en el servicio Power BI, puede desarrollar un informe paginado que se conecte al conjunto de datos de Power BI.

## <a name="data-integration"></a>Integración de datos

Si necesita combinar datos procedentes de varios orígenes de datos, tiene dos opciones:

- **Combinar conjuntos de datos de informe**: si los orígenes de datos [se admiten de forma nativa en los informes paginados](../paginated-reports-data-sources.md), puede plantearse crear campos calculados que usen las funciones de Report Builder [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) o [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function).
- **Desarrollar un modelo de Power BI Desktop**: probablemente sea más eficaz desarrollar un modelo de datos en Power BI Desktop. Puede usar Power Query para combinar consultas basadas en [cualquier origen de datos compatible](../power-bi-data-sources.md). Una vez publicado en el servicio Power BI, puede desarrollar un informe paginado que se conecte al conjunto de datos de Power BI.

## <a name="sql-server-complex-data-types"></a>Tipos de datos complejos de SQL Server

Como SQL Server es un origen de datos local, Power BI se debe conectar a través de una puerta de enlace, pero las puertas de enlace no admiten la recuperación de datos de tipos de datos complejos. Entre los tipos de datos complejos se incluyen tipos integrados como los [tipos de datos espaciales](/sql/relational-databases/spatial/spatial-data-sql-server) GEOMETRY y GEOGRAPHY, así como [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). También engloban tipos definidos por el usuario que se implementan a través de una clase de un ensamblado de Common Language Runtime (CLR) de Microsoft .NET Framework.

El trazado de datos espaciales y análisis en la visualización de mapa requiere datos espaciales de SQL Server. Por lo tanto, no se puede trabajar con la visualización de mapa cuando SQL Server es el origen de datos. Para ser claros, funcionará si el origen de datos es Azure SQL Database, ya que Power BI no se conecta a través de una puerta de enlace.

## <a name="data-related-images"></a>Imágenes relacionadas con datos

Se pueden usar imágenes para agregar logotipos o fotos al diseño del informe. Cuando se relacionan imágenes con las filas recuperadas por un conjunto de datos, existen dos opciones:

- Puede que los datos de imagen se puedan recuperar también del origen de datos (si ya están almacenados en una tabla).
- Cuando las imágenes están almacenadas en un servidor web, se puede usar una expresión dinámica para crear la ruta de dirección URL de la imagen.

Para más información y obtener sugerencias, vea [Guía de imágenes de informes paginados](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Recuperación de datos redundantes

Es posible que el informe recupere datos redundantes. Esto puede suceder cuando se eliminan campos de consulta del conjunto de datos o cuando el informe tiene conjuntos de datos sin usar. Evite este tipo de situaciones, ya que suponen una carga innecesaria en los orígenes de datos, la red y los recursos de capacidad de Power BI.

### <a name="deleted-query-fields"></a>Campos de consulta eliminados

En la página **Campos** de la ventana **Propiedades del conjunto de datos**, se pueden eliminar _campos de consulta_ del conjunto de datos (los campos de consulta se asignan a las columnas recuperadas por la consulta del conjunto de datos). Sin embargo, Report Builder no quita las columnas correspondientes de la consulta del conjunto de datos.

Si necesita eliminar campos de consulta del conjunto de datos, le recomendamos quitar las columnas correspondientes de la consulta desde el conjunto de datos. Report Builder quitará automáticamente todos los campos de consulta redundantes. Si elimina campos de consulta, asegúrese de modificar también la instrucción de consulta del conjunto de datos para quitar las columnas.

### <a name="unused-datasets"></a>Conjuntos de datos sin usar

Cuando se ejecuta un informe, se evalúan todos los conjuntos de objetos, incluso si no están enlazados a objetos de informe. Por esta razón, asegúrese de quitar todos los conjuntos de datos de prueba o de desarrollo antes de publicar un informe.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Orígenes de datos admitidos para informes paginados de Power BI](../paginated-reports-data-sources.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)
