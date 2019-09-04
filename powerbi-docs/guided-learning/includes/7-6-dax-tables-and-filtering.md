---
ms.openlocfilehash: 629c53358f757002f2b3dcda468641bbaaa2f4d4
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "70166781"
---
Una diferencia significativa entre **DAX** y el lenguaje de fórmulas de Excel es que DAX le permite pasar *tablas enteras* entre expresiones en lugar de estar limitado a un único valor. Un efecto eficaz es que DAX permite filtrar las tablas en sus expresiones y, después, trabajar con el conjunto de valores filtrados.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

Con DAX, puede crear tablas calculadas completamente nuevas y, después, tratarlas como cualquier otra tabla, incluida la creación de relaciones entre ellas y otras tablas del modelo de datos.

## <a name="dax-table-functions"></a>Funciones de tabla DAX
DAX tiene un amplio conjunto de funciones de **tabla**, incluidas las siguientes:

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

Estas funciones devuelven una tabla completa en lugar de un valor. Normalmente, usaría los resultados de una función de **tabla** en análisis posteriores como parte de una expresión mayor, en lugar de un valor final en la tabla devuelta. Es importante recordar que, al usar una función de tabla, los resultados heredan las relaciones de sus columnas.

Puede combinar funciones de tabla en la expresión, siempre y cuando cada una de ellas use y devuelva una tabla. Por ejemplo, considere la siguiente expresión de DAX:

    FILTER (ALL (Table), Condition)

Esta expresión aplicaría un filtro en toda la *tabla*, con lo que omitiría el contenido de filtro actual.

La función DISTINCT devuelve los distintos valores de una columna que también están visibles en el contexto actual. Por tanto, para usar el ejemplo de expresión DAX anterior, el uso de **ALL** en esa expresión omite los filtros, mientras que cambiar **ALL** por **DISTINCT** los observaría.

## <a name="counting-values-with-dax"></a>Recuento de valores con DAX
Los generadores de informes de Power BI se suelen hacer esta pregunta:

* ¿Cuántos valores tengo para esta columna?

Se trata de una pregunta sencilla de responder si se tiene delante una tabla, pero con DAX es diferente, sobre todo cuando existe una relación entre las tablas.

Por ejemplo, Power BI y DAX incluyen valores que no se han indexado correctamente con referencias cruzadas. Si se interrumpe la relación entrante, DAX agrega una nueva fila a la tabla relacionada que tiene espacios en blanco en cada campo y la vincula a la fila sin indexar para garantizar la integridad referencial. Si la función incluye filas en blanco, como suele pasar al usar **ALL**, se incluirán en el número de valores devueltos para esa columna.

También puede crear tablas calculadas completas mediante funciones DAX. Las tablas calculadas creadas con DAX requieren una función **NAME** y una función **TABLE**. Las tablas calculadas se pueden usar como cualquier otra tabla; por ejemplo, también pueden establecerse relaciones.

> Contenido del vídeo cortesía de [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

