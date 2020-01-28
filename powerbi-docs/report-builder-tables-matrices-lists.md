---
title: Tablas, matrices y listas en el Generador de informes de Power BI
description: En Power BI Report Builder, las tablas, las matrices y las listas son las regiones de datos que muestran los datos del informe paginado en celdas organizadas en filas y columnas.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 02ac131325dab59590cb88c524ace68a1226fc69
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953845"
---
# <a name="tables-matrixes-and-lists-in-power-bi-report-builder"></a>Tablas, matrices y listas en el Generador de informes de Power BI
 En el Generador de informes, las tablas, matrices y listas son las *regiones de datos* que muestran los datos del informe paginado en celdas organizadas en filas y columnas. Normalmente, las celdas contienen datos de texto como texto, fechas y números, pero también pueden contener elementos de informe como imágenes, gráficos o medidores. En conjunto, las tablas, matrices y listas suelen aparecer como regiones de datos *tablix*.  
  
 Las plantillas de tabla, matriz y lista se basan en la región de datos tablix, que es una cuadrícula flexible que puede mostrar datos en las celdas. En las plantillas de tabla y matriz, las celdas se organizan en filas y columnas. Como las plantillas son variaciones de la región de datos tablix genérica subyacente, puede mostrar los datos con diversos formatos de plantilla y, durante el desarrollo del informe, puede cambiar la tabla, matriz o lista para incluir las características de otra región de datos. Por ejemplo, si agrega una tabla y se da cuenta de que no responde a sus necesidades, puede agregar grupos de columnas para convertir la tabla en una matriz.  
  
 Las regiones de datos de tabla y matriz pueden mostrar relaciones complejas de datos mediante la inclusión de medidores, matrices, listas, gráficos y tablas anidadas. Las tablas y matrices tienen un diseño tabular y sus datos proceden de un único conjunto de datos basado en un único origen de datos. La principal diferencia entre las tablas y matrices es que las tablas pueden incluir solo grupos de filas, mientras que las matrices tienen grupos de filas y grupos de columnas.  
  
 Las listas son un poco diferentes. Admiten un diseño libre que puede incluir varias tablas del mismo nivel o matrices, cada una con los datos de otro conjunto de datos. Las listas también pueden usarse para los formularios, como las facturas.  
  
 Las siguientes imágenes ilustran informes sencillos con una tabla, matriz o lista.  

![Tabla, matriz y lista en el Generador de informes](media/report-builder-tables-matrices-lists/report-builder-table-matrix-list.png)
  
##  <a name="Table"></a> Tablas  
 Utilice una tabla para mostrar datos detallados, organizar los datos en grupos de filas, o ambos. La plantilla de tabla contiene tres columnas con una fila de encabezado de tabla y una fila de detalles de datos. La siguiente ilustración muestra la plantilla de tabla inicial, seleccionada en la superficie de diseño:  

![Plantilla de tabla del Generador de informes en la superficie de diseño, seleccionada](media/report-builder-tables-matrices-lists/report-builder-new-table.png)
  
 Puede agrupar datos por un solo campo, por varios campos o escribiendo su propia expresión. Puede crear grupos anidados o independientes, crear grupos adyacentes y mostrar valores agregados para los datos agrupados o agregar totales a grupos. Por ejemplo, si la tabla tiene un grupo de filas llamado **Categoría**, puede agregar un subtotal para cada grupo, así como un total general para el informe. Para mejorar la apariencia de la tabla y resaltar los datos a los que desea dar énfasis, puede combinar celdas y aplicar formato a datos y encabezados de tabla.  
  
 Puede ocultar inicialmente los detalles o los datos agrupados e incluir controles de alternancia de exploración en profundidad para que los usuarios puedan elegir interactivamente cuántos datos quiere mostrar.  
  
##  <a name="Matrix"></a> Matrices  
 Use una matriz para mostrar resúmenes de los datos agregados, agrupados en filas y columnas, similares a una tabla dinámica o de referencias cruzadas. El número de filas y columnas para los grupos se determina por el número de valores únicos en cada grupo de filas y columnas. La siguiente ilustración muestra la plantilla de matriz inicial, seleccionada en la superficie de diseño:  

![Nueva matriz del Generador de informes agregada desde el cuadro de herramientas, seleccionada](media/report-builder-tables-matrices-lists/report-builder-new-matrix.png)
 
 Puede agrupar datos por varios campos o expresiones en grupos de filas y columnas. En tiempo de ejecución, cuando se combinan los datos de informe y las regiones de datos, la matriz crece horizontal y verticalmente en la página a medida que se agregan columnas a los grupos de columnas y filas a los grupos de filas. Las celdas de la matriz muestran valores agregados cuyo ámbito es la intersección de los grupos de filas y columnas a la que pertenece la celda. Por ejemplo, si su matriz tiene un grupo de filas (Categoría) y dos grupos de columnas (Territorio y Año) que muestran la suma de las ventas, el informe muestra dos celdas con las sumas de las ventas para cada valor del grupo Categoría. El ámbito de las celdas son las dos intersecciones: Categoría y Territorio, y Categoría y Año. La matriz puede incluir grupos anidados y adyacentes. Los grupos anidados tienen una relación de elementos primarios y secundarios, y los grupos adyacentes tienen una relación del mismo nivel. Puede agregar subtotales para todos los niveles de grupos de filas y columnas anidados dentro de la matriz.  
  
 Para que los datos de la matriz sean más legibles y resaltar los datos a los que quiera dar énfasis, puede combinar celdas o dividirlas horizontal y verticalmente, y aplicar formato a los datos y encabezados de grupo.  
  
 También puede incluir controles de alternancia de exploración en profundidad que ocultan inicialmente los datos de detalle; después, el usuario puede hacer clic en los botones de alternancia para mostrar más o menos detalles según sea necesario.  
  
##  <a name="List"></a> Listas  
 Use una lista para crear un diseño de forma libre. No está limitado a un diseño de cuadrícula; puede colocar los campos libremente dentro de la lista. Puede usar una lista para diseñar un formulario para mostrar muchos campos de conjunto de datos, o como un contenedor para mostrar datos agrupados de varias regiones de datos en paralelo. Por ejemplo, puede definir un grupo para obtener una lista, agregar una tabla, gráfico e imagen, y mostrar los valores en forma de tabla y gráfico para cada valor de grupo, igual que haría para un registro de empleados o pacientes.  

![Nueva lista del Generador de informes agregada desde el cuadro de herramientas, seleccionada](media/report-builder-tables-matrices-lists/report-builder-new-list.png)
  
##  <a name="PreparingData"></a> Preparación de los datos  
 Las regiones de datos de tabla, matriz y lista muestran los datos de un conjunto de datos. Puede preparar los datos de la consulta que recupera los datos del conjunto de datos o puede establecer las propiedades de la tabla, matriz o lista.  
  
 Para preparar los datos, los lenguajes de consulta, como Transact-SQL, que se usan para recuperar los datos para los conjuntos de datos de informe pueden filtros para incluir solo un subconjunto de los datos, reemplazar los valores null o en blanco por constantes que hagan el informe más legible, y ordenar y agrupar los datos.  
  
 Si decide preparar los datos en la región de datos de tabla, matriz o lista de un informe, establezca las propiedades de la región de datos o las celdas de la región de datos. Si desea filtrar u ordenar los datos, establezca las propiedades de la región de datos. Por ejemplo, para ordenar los datos, se especifica las columnas que se van a ordenar y la dirección de ordenación. Si desea proporcionar un valor alternativo para un campo, establezca los valores del texto de celda que muestra el campo. Por ejemplo, para mostrar En blanco cuando un campo esté vacío o sea null, utilice una expresión para establecer el valor.  
  
##  <a name="BuildingConfiguringTableMatrixList"></a> Creación y configuración de una tabla, matriz o lista  
 Al agregar tablas o matrices a un informe, puede usar el asistente para tablas y matrices, o puede generarlas manualmente con las plantillas que proporciona el Generador de informes. Las listas se generan manualmente con la plantilla de lista.  
  
 El asistente le guiará por los pasos necesarios para crear y configurar una tabla o matriz rápidamente. Después de completar el asistente o de crear las regiones de datos tablix desde cero, puede seguir configurándolas y refinándolas. Los cuadros de diálogo, disponibles en los menús contextuales en las regiones de datos, facilitan la tarea de establecer las propiedades más utilizadas para los saltos de página, repeticiones y visibilidad de los encabezados y pies de página, opciones de presentación, filtros y ordenación. Pero la región de datos tablix proporciona una gran cantidad de propiedades adicionales, que se pueden establecer solo en el panel Propiedades del Generador de informes. Por ejemplo, si desea mostrar un mensaje cuando el conjunto de datos de una tabla, matriz o lista esté vacío, especifique el texto del mensaje en la propiedad de tablix NoRowsMessage, en el panel Propiedades.  
  
##  <a name="ChangingBetweenTablixTemplates"></a> Cambiar entre las plantillas de tablix  
 No tiene por qué limitarse a la plantilla de tablix que elija inicialmente. A medida que agregue grupos, totales y etiquetas, es posible que desee modificar el diseño de tablix. Por ejemplo, podría comenzar con una tabla y, a continuación, eliminar la fila de detalles y agregar grupos de columnas.  
  
 Puede continuar desarrollando una tabla, matriz o lista agregando características de tablix. Las características de tablix son, entre otras, mostrar datos detallados o agregados para los datos agrupados en filas y columnas. Puede crear grupos anidados, grupos adyacentes independientes o grupos recursivos. Puede filtrar y ordenar los datos agrupados y combinar grupos fácilmente incluyendo varias expresiones de grupo en una definición de grupo.  
  
 También puede agregar totales para un grupo o totales generales para la región de datos. Puede ocultar filas o columnas para simplificar un informe y permitir que el usuario alterne la presentación de los datos ocultos, como en un informe de exploración en profundidad. 

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
