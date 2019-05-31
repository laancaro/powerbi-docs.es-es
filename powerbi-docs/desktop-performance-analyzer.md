---
title: Usar el analizador de rendimiento para examinar el rendimiento del elemento de informe en Power BI Desktop
description: Descubra cómo funcionan los objetos visuales y elementos de informe en cuanto a la capacidad de respuesta y el uso de recursos
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854422"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Usar el analizador de rendimiento para examinar el rendimiento del elemento de informe

En **Power BI Desktop** puede encontrar fuera cómo funcionan cada uno de los elementos del informe, como los objetos visuales y las fórmulas DAX. Mediante el **Performance Analyzer**, puede ver y registro de los registros que medir cada uno de los elementos del informe rendimiento cuando los usuarios interactuar con ellos, y qué aspectos de su rendimiento se consumen muchos recursos (o más).

![Analizador de rendimiento](media/desktop-performance-analyzer/performance-analyzer-01.png)

Analizador de rendimiento inspecciona y muestra el tiempo necesario para actualizar o actualizar todos los objetos visuales que iniciar interacciones del usuario y presenta la información para que pueda ver, explorar en profundidad o exportar los resultados. Analizador de rendimiento puede ayudarle a identificar los objetos visuales que afectan al rendimiento de los informes e identificar el motivo del impacto.

## <a name="displaying-the-performance-analyzer-pane"></a>Mostrar el panel del analizador de rendimiento

En **Power BI Desktop** seleccione la **vista** cinta de opciones. En el **mostrar** área de la **vista** cinta de opciones que puede seleccionar la casilla de verificación junto a **Performance Analyzer** para mostrar el panel del analizador de rendimiento.

![Seleccione el analizador de rendimiento en la cinta de opciones de vista](media/desktop-performance-analyzer/performance-analyzer-02.png)

Una vez seleccionado, el analizador de rendimiento se muestra en su propio panel, a la derecha del lienzo del informe.

## <a name="using-performance-analyzer"></a>Con el analizador de rendimiento

Las medidas del analizador de rendimiento (incluido el tiempo para crear o actualizar un objeto visual) el tiempo de procesamiento necesario para actualizar produce como resultado ninguna interacción del usuario que es el resultado de ejecutar una consulta de elementos de informe. Por ejemplo, ajustar una segmentación de datos requiere la visual de segmentación de datos que desea modificar, una consulta para enviarse al modelo de datos y los objetos visuales afectados que se deben actualizar como resultado de la nueva configuración. 

Para que el analizador de rendimiento de iniciar la grabación, simplemente seleccione **iniciar la grabación**

![Iniciar grabación](media/desktop-performance-analyzer/performance-analyzer-03.png)

Cualquier acción que realizar en el informe se muestran y se registran en el panel del analizador de rendimiento, en el orden en que se carga el objeto visual por Power BI. Por ejemplo, quizás tiene un informe que los usuarios han dicho que tarda mucho tiempo en actualizar. O algunos de los objetos visuales en un informe tardan mucho tiempo que se muestra cuando se ajusta un control deslizante. Analizador de rendimiento puede indicar a qué objeto visual es el culpable, así que identifica qué aspectos del objeto visual está tardando más tardan en completarse para procesar. 

Una vez que comience la grabación, la **iniciar la grabación** botón se atenúa fuera (inactivo, puesto que ya haya empezado a grabación) y el **detener** botón está activo. 

Analizador de rendimiento recopila y muestra la información de medición de rendimiento en tiempo real. Por lo que cada vez que haga clic en un objeto visual, mover una segmentación de datos o interactuar de cualquier otra forma, analizador de rendimiento muestra inmediatamente los resultados de rendimiento en su panel.

Si el panel tiene más información que se pueden mostrar, aparece una barra de desplazamiento para desplazarse a información adicional.

Cada interacción tiene un identificador de la sección en el panel, que describe la acción que inició las entradas del registro. En la siguiente imagen, la interacción era que los usuarios cambiar una segmentación de datos.

![Secciones según el tipo de interacción](media/desktop-performance-analyzer/performance-analyzer-04.png)

Información del registro de cada objeto visual incluye el tiempo empleado (duración) para completar las siguientes categorías de tareas:

* **Consulta DAX** -si era necesaria una consulta de DAX, se trata de la hora entre el objeto visual que enviar la consulta y para Analysis Services devolver los resultados.
* **Presentación visual** -tiempo necesario para que el objeto visual se va a dibujar en la pantalla, incluido el tiempo necesario para recuperar las imágenes de web o la codificación geográfica. 
* **Otros** -tiempo requerido por el objeto visual para preparar las consultas, esperando a otros objetos visuales completar o realizando otro procesamiento en segundo plano.

![elementos de información de registro](media/desktop-performance-analyzer/performance-analyzer-06.png)

Una vez haya interactuado con elementos del informe que desea medir con el analizador de rendimiento, puede seleccionar la **detener** botón. La información de rendimiento permanece en el panel después de seleccionar **detener** para su análisis.

Para borrar la información en el panel del analizador de rendimiento, seleccione **borrar**. Toda la información se borra y no se guarda cuando se selecciona **clara**. Consulte la sección siguiente para obtener información sobre cómo guardar la información en los registros. 

## <a name="refreshing-visuals"></a>Actualizar los objetos visuales

Puede seleccionar **actualizar objetos visuales** en el panel del analizador de rendimiento para actualizar todos los objetos visuales en la página actual del informe y, por tanto, tienen Performance Analyzer recopilar información acerca de todos los objetos visuales este tipo.

También puede actualizar los objetos visuales individuales. Cuando se graba el analizador de rendimiento, puede seleccionar **actualizar este objeto visual** se encuentra en la esquina superior derecha de cada objeto visual, para actualizar ese objeto visual y capturar su información de rendimiento.

![actualización de un objeto visual](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Guardar información de rendimiento

Puede guardar la información que se crea el analizador de rendimiento sobre un informe seleccionando el **exportar** botón. Seleccionar **exportar** crea un archivo .json con información desde el panel del analizador de rendimiento. 

![Guarde el archivo de registro para el analizador de rendimiento](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Pasos siguientes
Para más información acerca de **Power BI Desktop** y cómo empezar a trabajar, consulte los siguientes artículos.

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Conectarse a los datos en Power BI Desktop](desktop-connect-to-data.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)   

