---
title: Actualizaciones incrementales en Power BI Premium
description: Obtenga información sobre cómo permitir el uso de conjuntos de datos voluminosos en el servicio Power BI Premium.
author: christianwade
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 04/30/2018
ms.author: chwade
LocalizationGroup: Premium
ms.openlocfilehash: 1b6a3c35abeff33e2fb1e0fecdc5c2a5c88e1530
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "34298191"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Actualizaciones incrementales en Power BI Premium

La actualización incremental permite usar conjuntos de datos muy grandes en el servicio Power BI Premium, lo que reporta las siguientes ventajas:

- **Las actualizaciones son más rápidas.** Solo se actualizarán los datos que hayan cambiado. Sería el caso, por ejemplo, de actualizar solo los últimos 5 días de un conjunto de datos de 10 años.

- **Las actualizaciones son más confiables.** Por ejemplo, no es necesario mantener las conexiones de larga duración a sistemas de origen volátiles.

- **El consumo de recursos es menor.** Si hay menos datos que actualizar, se reduce el consumo total de memoria y de otros recursos.

## <a name="how-to-use-incremental-refresh"></a>Cómo usar una actualización incremental

Las directivas de actualización incremental se definen en Power BI Desktop y se aplican cuando se publican en el servicio Power BI.

Comience habilitando las actualizaciones incrementales en las características de vista previa.

![Opciones - Características de vista previa](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Filtrar conjuntos de datos grandes en Power BI Desktop

Los conjuntos de datos grandes (que pueden contener miles de millones de filas) pueden no caber en Power BI Desktop, ya que este suele estar limitado por los recursos disponibles en el equipo del usuario. Por tanto, normalmente estos conjuntos de datos se filtran durante la importación para que puedan caber en Power BI Desktop. Esto es así tanto si se usa la actualización incremental como si no.

#### <a name="rangestart-and-rangeend-parameters"></a>Parámetros RangeStart y RangeEnd

Para usar la actualización incremental en el servicio Power BI, deberá realizarse un filtrado usando los parámetros de fecha y hora de Power Query con los nombres reservados **RangeStart** y **RangeEnd** (distinguen mayúsculas de minúsculas).

En el editor de Power Query, seleccione **Administrar parámetros** para definir los parámetros con valores predeterminados.

![Administrar parámetros](media/service-premium-incremental-refresh/manage-parameters.png)

Con los parámetros ya definidos, se puede aplicar el filtro seleccionando la opción de menú **Filtro personalizado** en una columna.

![Filtro personalizado](media/service-premium-incremental-refresh/custom-filter.png)

Procure filtrar las filas en las que el valor de la columna sea *igual o posterior a* **RangeStart** y *anterior a* **RangeEnd**.

![Filtrar filas](media/service-premium-incremental-refresh/filter-rows.png)

> [!TIP]
> Si bien el tipo de datos de los parámetros debe ser fecha y hora, estos se pueden convertir para que coincidan con los requisitos del origen de datos. Por ejemplo, la siguiente función de Power Query convierte un valor de fecha y hora para que aparezca como una clave suplente de enteros con la forma *ddmmaaaa*, algo habitual en los almacenamientos de datos. Se puede llamar a la función durante el paso de filtrado.
>
> `(x as datetime) => Date.Year(x)*10000 + Date.Month(x)*100 + Date.Day(x)`

Seleccione **Cerrar y aplicar** en el editor de Power Query. Ahora deberíamos tener un subconjunto del conjunto de datos en Power BI Desktop.

> [!NOTE]
> Una vez publicados, el servicio Power BI reemplaza automáticamente los valores de parámetro, de modo que no es necesario establecerlos en la configuración del conjunto de datos.

### <a name="define-the-refresh-policy"></a>Definir la directiva de actualización

La actualización incremental está disponible en el menú contextual de las tablas, excepto en los modelos de conexión dinámica.

![Directiva de actualización](media/service-premium-incremental-refresh/refresh-policy.png)

#### <a name="incremental-refresh-dialog"></a>Cuadro de diálogo Actualización incremental

Se abre el cuadro de diálogo Actualización incremental. Use el botón de alternancia para habilitar o deshabilitar el cuadro de diálogo.

![Detalles de la actualización](media/service-premium-incremental-refresh/refresh-details.png)

> [!NOTE]
> Si la expresión de Power Query relativa a la tabla no hace referencia a los parámetros con nombres reservados, el botón de alternancia se deshabilita.

En el texto del encabezado se explica lo siguiente:

-   Solo se admiten actualizaciones incrementales en las áreas de trabajo con capacidad Premium. Las directivas de actualización se definen en Power BI Desktop y se aplican por medio de operaciones de actualización en el servicio.

-   Si descarga el archivo PBIX que contiene una directiva de actualización incremental desde el servicio Power BI, no se abrirá en Power BI Desktop. Pronto no podrá descargarlo en ninguna circunstancia. Aunque esto puede que sí sea posible en el futuro, recuerde que estos conjuntos de datos pueden crecer tanto que sea poco práctico descargarlos y abrirlos en un equipo de escritorio al uso.

#### <a name="refresh-ranges"></a>Frecuencias de actualización

En el siguiente ejemplo se define una directiva de actualización por la que se almacenan 5 años de datos en total, y se actualiza incrementalmente 10 días de datos. Si el conjunto de datos se actualiza a diario, se lleva a cabo lo siguiente en cada operación de actualización.

-   Se agrega un nuevo día de datos.

-   Se actualizan 10 días hasta la fecha actual.

-   Se quitan los años naturales con una antigüedad de más de 5 años con respecto a la fecha actual. Por ejemplo, si la fecha actual es 1 de enero de 2019, se quitará el año 2013.

La primera actualización en el servicio Power BI puede tardar más en importar los 5 años enteros, pero las siguientes finalizarán en un tiempo mucho menor.

![Frecuencias de actualización](media/service-premium-incremental-refresh/refresh-ranges.png)

**Definir estas frecuencias de actualización probablemente sea todo lo que necesita, en cuyo caso puede ir directamente al paso de publicación. Las listas desplegables adicionales se corresponden con características avanzadas.**

#### <a name="detect-data-changes"></a>Detectar cambios de datos

Una actualización incremental de 10 días es, evidentemente, mucho más eficaz que realizar una actualización completa de 5 años. Pero hasta esto podemos mejorarlo. Si activa la casilla **Detectar cambios de datos**, puede seleccionar una columna de fecha y hora y usarla para identificar y actualizar solo los días donde los datos hayan cambiado. Aquí se da por hecho que esta columna existe en el sistema de origen, que se suele usar con fines de auditoría. El valor máximo de esta columna se evalúa para cada uno de los períodos en la frecuencia incremental. Si no ha cambiado desde la última actualización, no es necesario actualizar período. En el ejemplo, esto podría reducir aún más los días actualizados incrementalmente de 10 a, quizá, 2.

![Detectar cambios](media/service-premium-incremental-refresh/detect-changes.png)

> [!TIP]
> El diseño actual requiere que la columna que detecta los cambios de datos sea persistente y esté almacenada en la memoria caché. Puede que quiera sopesar el uso de una de las siguientes técnicas para reducir la cardinalidad y el consumo de memoria.
>
> Durante la actualización solo debe persistir el valor máximo de esta columna, posiblemente usando una función de Power Query.
>
> Reduzca la precisión a un nivel que sea aceptable para sus requisitos de frecuencia de actualización.
>
> Tenemos previsto permitir en el futuro que se puedan definir consultas personalizadas para detectar cambios de datos. De este modo, se podrá prescindir por completo del valor de columna persistente.

#### <a name="only-refresh-complete-periods"></a>Actualizar solo períodos completos

Supongamos que nuestra actualización está programada para ejecutarse todas las mañanas a las 4:00 A.M. Si aparecen datos en el sistema de origen durante esas 4 horas, probablemente no quiera tenerlos en cuenta. Algunas métricas empresariales (como, por ejemplo, los barriles por día en el sector petrolífero) no tienen sentido en días parciales.

Pensemos en otro ejemplo en el que hay que actualizar los datos de un sistema financiero donde los datos del mes anterior se aprueban el día 12 del mes en curso. Puede establecer la frecuencia incremental en 1 mes y programar la actualización para que se ejecute el día 12 del mes. Así, con esta opción activada, los datos de enero se actualizarían el 12 de febrero.

![Períodos completos](media/service-premium-incremental-refresh/complete-periods.png)

> [!NOTE]
> Las operaciones de actualización del servicio se ejecutan según la hora UTC. Esto puede determinar la fecha de vigencia y repercutir en los períodos completos. Tenemos previsto incluir la posibilidad de invalidar la fecha de vigencia en las operaciones de actualización.

## <a name="publish-to-the-service"></a>Publicar en el servicio

Puesto que la actualización incremental es una característica única de Premium, el cuadro de diálogo Publicar solo permite seleccionar un área de trabajo de la capacidad Premium.

![Publicar en el servicio](media/service-premium-incremental-refresh/publish.png)

Ahora podemos actualizar el modelo. La primera actualización puede tardar más tiempo en importar los datos históricos, mientras que las siguientes serán bastante más rápidas, ya que serán actualizaciones incrementales.

## <a name="query-timeouts"></a>Tiempos de espera de las consultas

En este artículo de [solución problemas de actualización](https://docs.microsoft.com/power-bi/refresh-troubleshooting-refresh-scenarios) se explica que las operaciones de actualización en el servicio Power BI están sujetas a tiempos de espera. Las consultas también pueden verse limitadas por el tiempo de espera predeterminado del origen de datos. La mayoría de los orígenes relacionales permiten invalidar los tiempos de espera en la expresión. Por ejemplo, en la siguiente expresión se usa la [función de acceso a datos de SQL Server](https://msdn.microsoft.com/query-bi/m/sql-database) para establecerla en 2 horas. Cada período definido por los intervalos de directiva envía una consulta que respeta el valor de tiempo de espera del comando.

```
let
    Source = Sql.Database("myserver.database.windows.net", "AdventureWorks", [CommandTimeout=#duration(0, 2, 0, 0)]),
    dbo_Fact = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
    #"Filtered Rows" = Table.SelectRows(dbo_Fact, each [OrderDate] >= RangeStart and [OrderDate] < RangeEnd)
in
    #"Filtered Rows"
```
