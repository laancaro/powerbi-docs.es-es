---
title: Uso de parámetros en cascada en informes paginados
description: Instrucciones para diseñar informes paginados mediante parámetros en cascada.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 2a8dca43077fe12e4903585e3926cc67fe864136
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76162420"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Uso de parámetros en cascada en informes paginados

Este artículo está dirigido a los autores de informes que diseñan [informes paginados](../paginated-reports-report-builder-power-bi.md) de Power BI. Proporciona escenarios para diseñar parámetros en cascada. Los parámetros en cascada son parámetros de informe con dependencias. Cuando un usuario del informe selecciona un valor (o valores) de parámetro, se usa para establecer los valores disponibles para otro parámetro.

> [!NOTE]
> En este artículo no se incluye una introducción a los parámetros en cascada y cómo configurarlos. Si no está familiarizado con los parámetros en cascada, se recomienda que primero lea [Agregar parámetros en cascada a un informe (Generador de informes y SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs).

## <a name="design-scenarios"></a>Escenarios de diseño

Existen dos escenarios de diseño para el uso de parámetros en cascada. Se pueden usar de forma eficaz para:

- Filtrar _conjuntos grandes_ de elementos
- Presentar elementos _pertinentes_

### <a name="example-database"></a>Base de datos de ejemplo

Los ejemplos presentados en este artículo se basan en una instancia de Azure SQL Database. La base de datos registra las operaciones de ventas y contiene varias tablas que almacenan revendedores, productos y pedidos de venta.

Una tabla llamada **Reseller** almacena un registro para cada revendedor y contiene varios miles de registros. La tabla **Reseller** tiene las siguientes columnas:

- ResellerCode (entero)
- ResellerName
- País-región
- State-Province
- Ciudad
- Código postal

También hay una tabla denominada **Sales**. Almacena los registros de pedidos de ventas y tiene una relación de clave externa con la tabla **Reseller**, en la columna **ResellerCode**.

### <a name="example-requirement"></a>Requisito de ejemplo

Hay un requisito para desarrollar un informe de perfil del revendedor. El informe debe estar diseñado para mostrar información para un único revendedor. No se recomienda que el usuario del informe escriba un código de revendedor, ya que raramente lo memoriza.

## <a name="filter-large-sets-of-items"></a>Filtrado de grandes conjuntos de elementos

Echemos un vistazo a tres ejemplos que le ayudarán a limitar grandes conjuntos de elementos disponibles, como los revendedores. Son las siguientes:

- [Filtrado por columnas relacionadas](#filter-by-related-columns)
- [Filtrado por una columna de agrupación](#filter-by-a-grouping-column)
- [Filtrado por un patrón de búsqueda](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtrado por columnas relacionadas

En este ejemplo, el usuario del informe interactúa con cinco parámetros de informe. Deben seleccionar país-región, estado-provincia, ciudad y código postal. A continuación, un parámetro final enumera los revendedores que residen en esa ubicación geográfica.

![La imagen muestra cinco parámetros de informe: País-región, estado-provincia, ciudad, código postal y revendedor. Los cuatro primeros tienen valores establecidos y la lista de revendedores se filtra a solo cuatro elementos.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

A continuación se muestra cómo puede desarrollar los parámetros en cascada:

1. Cree los cinco parámetros de informe ordenados en la secuencia correcta.
2. Cree el conjunto de datos **CountryRegion** que recupera valores de país y región distintos mediante la siguiente instrucción de consulta:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Cree el conjunto de datos **StateProvince** que recupera valores de estado y provincia distintos para la región y país seleccionada mediante la siguiente instrucción de consulta:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Cree el conjunto de datos **City** que recupera valores de ciudad distintos para la región y país seleccionada mediante la siguiente instrucción de consulta:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Continúe con este patrón para crear el conjunto de datos **PostalCode**.
6. Cree el conjunto de datos **Reseller** para recuperar todos los revendedores de los valores geográficos seleccionados mediante la siguiente instrucción de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Para cada conjunto de datos excepto el primero, asigne los parámetros de consulta a los parámetros de informe correspondientes.

> [!NOTE]
> Todos los parámetros de consulta (con el prefijo del símbolo @) que se muestran en estos ejemplos se pueden insertar en las instrucciones SELECT o pasarse a los procedimientos almacenados.
>
> Por lo general, los procedimientos almacenados son un enfoque de diseño mejor. Se debe a que sus planes de consulta se almacenan en caché para una ejecución más rápida y permiten desarrollar lógica más sofisticada cuando sea necesario. Sin embargo, no se admiten actualmente para orígenes de datos relacionales de puerta de enlace, lo que significa SQL Server, Oracle y Teradata.
>
> Por último, siempre debe asegurarse de que existan índices adecuados para admitir la recuperación eficaz de datos. De lo contrario, los parámetros de informe pueden tardar en rellenarse y la base de datos podría sobrecargarse. Para más información sobre la indización de SQL Server, consulte [Guía de diseño y de arquitectura de índices de SQL Server](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017).

### <a name="filter-by-a-grouping-column"></a>Filtrado por una columna de agrupación

En este ejemplo, el usuario del informe interactúa con un parámetro de informe para seleccionar la primera letra del revendedor. Un segundo parámetro muestra a los revendedores cuando el nombre comienza con la letra seleccionada.

![La imagen muestra dos parámetros de informe: Grupo y Revendedor. El primer valor de parámetro se establece en la letra A, y la lista de revendedores se filtra por varios elementos que empiezan con esa letra.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

A continuación se muestra cómo puede desarrollar los parámetros en cascada:

1. Cree los parámetros de informe **ReportGroup** y **Reseller**, ordenados en la secuencia correcta.
2. Cree el conjunto de datos **ReportGroup** para recuperar las primeras letras usadas por todos los revendedores, mediante la siguiente instrucción de consulta:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Cree el conjunto de datos **Reseller** para recuperar todos los revendedores que empiezan con la letra seleccionada mediante la siguiente instrucción de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Asigne el parámetro de consulta del conjunto de datos **Revendedor** al parámetro de informe correspondiente.

Es más eficaz agregar la columna de agrupación a la tabla **Reseller**. Cuando se almacenan y se indexan, ofrece el mejor resultado. Para más información, consulte [Specify Computed Columns in a Table](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Esta técnica puede ofrecer incluso mayor potencial. Considere el siguiente script que agrega una nueva columna de agrupación para filtrar a los revendedores por _bandas predefinidas de letras_. También crea un índice para recuperar de forma eficaz los datos requeridos por los parámetros de informe.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtrado por patrón de búsqueda

En este ejemplo, el usuario del informe interactúa con un parámetro de informe para especificar un patrón de búsqueda. Un segundo parámetro muestra después a los revendedores cuando el nombre contiene el patrón.

![La imagen muestra dos parámetros de informe: Buscar y Revendedor. El primer valor de parámetro se establece en el texto "red" y la lista de revendedores se filtra por varios elementos que contienen ese texto.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

A continuación se muestra cómo puede desarrollar los parámetros en cascada:

1. Cree los parámetros de informe **Search** y **Reseller**, ordenados en la secuencia correcta.
2. Cree el conjunto de datos **Reseller** para recuperar todos los revendedores que contienen el texto de búsqueda, mediante la siguiente instrucción de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Asigne el parámetro de consulta del conjunto de datos **Revendedor** al parámetro de informe correspondiente.

> [!TIP]
> Puede mejorar este diseño para proporcionar más control a los usuarios del informe. Permite definir su propio valor de coincidencia de patrones. Por ejemplo, el valor de búsqueda "red%" filtrará a los revendedores cuyos nombres _empiecen_ con los caracteres en "rojo".
>
> Para más información, consulte [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character).

A continuación se indica cómo puede permitir que los usuarios del informe definan su propio patrón.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Sin embargo, muchos profesionales que no dominan las bases de datos no conocen el carácter comodín de porcentaje (%). Por el contrario, están familiarizados con el carácter asterisco (*). Mediante la modificación de la cláusula WHERE, puede permitirles utilizar este carácter.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Presentación de elementos relevantes

En este escenario, puede usar datos factuales para limitar los valores disponibles. Los usuarios del informe se presentarán con los elementos en los que se ha registrado la actividad.

En este ejemplo, el usuario del informe interactúa con tres parámetros de informe. Los dos primeros establecen un intervalo de fechas de pedidos de venta. El tercer parámetro muestra a continuación los revendedores que han creado pedidos durante ese período de tiempo.

![La imagen muestra tres parámetros de informe: fecha de inicio del pedido, fecha de finalización del pedido y revendedor. Los dos parámetros de fecha se establecen para el mes de enero de 2020 y la lista de revendedores se filtra por varios elementos que representan a los revendedores que han realizado pedidos durante este mes.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

A continuación se muestra cómo puede desarrollar los parámetros en cascada:

1. Cree los parámetros de informe **OrderDateStart**, **OrderDateEnd** y **Reseller**, ordenados en la secuencia correcta.
2. Cree el conjunto de datos **Reseller** para recuperar todos los revendedores que crearon pedidos en el período de fecha mediante la siguiente instrucción de consulta:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Recomendaciones

Se recomienda diseñar los informes con parámetros en cascada, siempre que sea posible. Se debe a que:

- Proporcionan experiencias intuitivas y útiles para los usuarios del informe.
- Son eficaces, ya que recuperan conjuntos más pequeños de valores disponibles.

Asegúrese de optimizar los orígenes de datos mediante:

- El uso de procedimientos almacenados, siempre que sea posible
- La adición de índices adecuados para una recuperación eficaz de datos
- La materialización de valores de columna (e incluso filas) para evitar evaluaciones de tiempo de consulta costosas

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Parámetros de informe en el Generador de informes de Power BI](../report-builder-parameters.md)
- [Agregar parámetros en cascada a un informe (Generador de informes y SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com)
