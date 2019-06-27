---
title: Vista previa de los informes en el Generador de informes de Power BI
description: Mientras se crea un informe paginado del Generador de informes, puede resultar útil obtener una vista previa del informe con frecuencia para comprobar que muestra lo que desea.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840243"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Vista previa de los informes en el Generador de informes de Power BI
  Mientras se crea un informe paginado del Generador de informes, puede resultar útil obtener una vista previa del informe con frecuencia para comprobar que muestra lo que desea. Para obtener una vista previa del informe, haga clic en **Ejecutar**. El informe se representa en el modo de vista previa.  
  
 El Generador de informes mejora la experiencia de vista previa mediante el uso de sesiones de edición cuando se conecta a un servidor de informes. La sesión de edición crea una memoria caché de los datos y hace que los conjuntos de datos de la memoria caché estén disponibles para mostrar vistas previas repetidas del informe. Una sesión de edición no es una característica con la que se interactúa directamente, pero conocer cuándo se actualiza el conjunto de datos de la memoria caché le ayudará a mejorar el rendimiento al obtener una vista previa de un informe y comprender por qué el informe se representa con más rapidez o lentitud.  

  
> [!NOTE]  
> Hay algunas diferencias entre una vista previa en el Generador de informes y la visualización en un explorador. Por ejemplo, un control de calendario, que se agrega a un informe cuando se especifica un parámetro del tipo de fecha y hora, es diferente en el Generador de informes y en un explorador. 
  
## <a name="improving-preview-performance"></a>Mejora del rendimiento de la vista previa  
 El modo en el que se crean y actualizan los informes afecta a la rapidez con la que se representan en la vista previa. La primera vez que se obtiene una vista previa de un informe que se basa en una referencia de servidor, se crea automáticamente una sesión de edición y los datos que se utilizaron al ejecutar el informe se agregan a una memoria caché de datos que se almacena. Al realizar cambios en el informe que no afectan a los datos, se usa la copia en caché de los datos. Esto significa que no verá cambios en los datos cada vez que obtenga una vista previa del informe. Si desea ver los nuevos datos, haga clic en el botón **Actualizar** en la cinta de opciones.  
  
 Las siguientes acciones hacen que la memoria caché se actualice y ralentizan la representación del informe en la siguiente vista previa del mismo:  
  
-   Agregar, cambiar o eliminar un conjunto de datos. El conjunto de datos almacenado en memoria caché contiene todos los conjuntos de datos utilizados por un informe y la modificación de cualquier conjunto de datos invalida el conjunto de datos en la memoria caché. Esto incluye cambiar el nombre, la consulta o los campos del conjunto de datos.  
  
    > [!NOTE]  
    >  Si el conjunto de datos tiene un gran número de campos que no espera utilizar, considere la posibilidad de actualizar el conjunto de datos para omitirlos. Aunque esto crea una nueva sesión de edición y la primera vista previa del informe es más lenta, un conjunto de datos en caché más pequeño resulta beneficioso para el rendimiento del servidor de informes.  
  
-   Agregar, cambiar o eliminar un origen de datos. Esto incluye cambiar el nombre o las propiedades del origen de datos, la extensión de los datos del origen de datos o las propiedades de la conexión al origen de datos.  
  
-   Cambiar el origen de datos que utiliza el informe a un origen de datos diferente.  
  
-   Cambiar el idioma del informe.  
  
-   Cambiar los ensamblados o el código personalizado que utiliza el informe.  
  
-   Agregar, cambiar o eliminar los parámetros de consulta del informe o los valores de los parámetros.  
  
 Los cambios realizados en el diseño del informe y el formato de los datos no afectan al conjunto de datos de la memoria caché. Puede realizar las acciones siguientes sin actualizar el conjunto de datos de la memoria caché:  
  
-   Agregar o eliminar regiones de datos, como tablas, matrices o gráficos.  
  
-   Agregar o eliminar columnas del informe. Todos los campos del conjunto de datos están disponibles para su uso en el informe. Agregar o eliminar campos en el informe no tiene ningún efecto en el conjunto de datos.  
  
-   Cambiar el orden de los campos de las tablas y las matrices.  
  
-   Agregar, cambiar o eliminar grupos de filas y columnas.  
  
-   Agregar, cambiar o eliminar el formato de los valores de los datos de los campos.  
  
-   Agregar, cambiar o eliminar imágenes, líneas o cuadros de texto.  
  
-   Cambiar los saltos de página.  
  
La sesión de edición se crea la primera vez que se obtiene una vista previa de un informe. De forma predeterminada, una sesión de edición dura 7 200 segundos (2 horas). La sesión se vuelve a establecer en dos horas cada vez que se ejecuta el informe. Cuando expira la sesión de edición, se eliminan los datos almacenados en la memoria caché. Si la sesión de edición expira, se crea automáticamente una la próxima vez que se obtiene una vista previa del informe.
  
De forma predeterminada, la memoria caché de los datos puede contener hasta cinco conjuntos de datos. Si utiliza muchas combinaciones diferentes de los valores de los parámetros, el informe podría necesitar más datos. Esto requiere que se actualice la memoria caché y el informe se representará más lentamente la próxima vez que se obtenga la vista previa. 
  
## <a name="concurrency-of-report-updates"></a>Simultaneidad de actualizaciones de informes  
Con frecuencia, se obtiene una vista previa de un informe como un paso de su actualización para, a continuación, guardar el informe en el servicio Power BI. Cuando se actualiza un informe, es posible que otra persona esté actualizando y guardando el informe al mismo tiempo. El informe que se guarda en último lugar es la versión del informe que está disponible para su posterior consulta y actualización. Esto significa que la versión del informe del que se obtuvo una vista previa podría no ser la versión que se vuelva a abrir. Tiene la opción de guardar el informe con un nombre nuevo mediante la opción **Guardar como** del menú del Generador de informes.  
  
## <a name="external-report-items"></a>Elementos externos del informe  
 El informe puede incluir elementos como imágenes externas que se almacenan por separado del informe. Dado que los elementos se almacenan por separado, es posible que se puedan mover a otra ubicación o ser eliminados. Si esto ocurre, podría producirse un error al obtener una vista previa del informe. Puede actualizar el informe para indicar la ubicación actualizada del elemento o, si el elemento se eliminó, reemplazarlo por un elemento existente o eliminar la referencia al elemento desde el informe.  
  
## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
