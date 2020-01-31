---
title: Uso del Analizador de rendimiento para examinar el rendimiento de los elementos de los informes en Power BI Desktop
description: Descubra qué hacen los objetos visuales y los elementos de informe en términos de uso de recursos y capacidad de respuesta
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e3e9e8ebc7feda46cb4c79ffd1535807d04a178b
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709771"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Uso del Analizador de rendimiento para examinar el rendimiento de los elementos de los informes

En **Power BI Desktop** puede averiguar cómo se están desarrollando cada uno de los elementos de informe, como los objetos visuales y las fórmulas DAX. Con el **Analizador de rendimiento**, puede ver y grabar registros que midan la forma en que cada uno de los elementos del informe funciona cuando los usuarios interactúan con ellos, y cuáles son los aspectos de su rendimiento que utilizan la mayor (o menor) cantidad de recursos.

![Analizador de rendimiento](media/desktop-performance-analyzer/performance-analyzer-01.png)

El Analizador de rendimiento inspecciona y muestra la duración necesaria para actualizar todos los objetos visuales que inician las interacciones de usuario,además presenta la información para que pueda ver, explorar en profundidad o exportar los resultados. El Analizador de rendimiento puede ayudarle a identificar los objetos visuales que afectan al rendimiento de los informes y reconocer el motivo que puede estar repercutiendo en este rendimiento.

## <a name="displaying-the-performance-analyzer-pane"></a>Visualización del panel del Analizador de rendimiento

En **Power BI Desktop** seleccione la cinta de opciones **Ver**. En el área **Mostrar** de la cinta de opciones **Ver** puede seleccionar la casilla situada junto a **Analizador de rendimiento** para mostrar el panel del Analizador de rendimiento.

![En la cinta de opciones Ver, seleccione Analizador de rendimiento](media/desktop-performance-analyzer/performance-analyzer-02.png)

Una vez seleccionado, el Analizador de rendimiento se muestra en su propio panel, a la derecha del lienzo del informe.

## <a name="using-performance-analyzer"></a>Uso del Analizador de rendimiento

El Analizador de rendimiento mide el tiempo de procesamiento necesario (incluido el tiempo para crear o actualizar un objeto visual) para actualizar los elementos de informe iniciados como resultado de cualquier interacción del usuario que tenga como resultado la ejecución de una consulta. Por ejemplo, ajustar una segmentación requiere que se modifique el objeto visual de la segmentación, una consulta que se va a enviar al modelo de datos y los objetos visuales afectados que tienen que actualizarse como resultado de la nueva configuración. 

Para que el Analizador de rendimiento empiece a grabar, simplemente seleccione **Iniciar grabación**

![Iniciar grabación](media/desktop-performance-analyzer/performance-analyzer-03.png)

Cualquier acción que se lleve a cabo en el informe se muestra y se registra en el panel del Analizador de rendimiento, en el mismo orden en el que Power BI carga el objeto visual. Por ejemplo, los usuarios han comentado que hay un informe que tarda mucho tiempo en actualizarse. O que ciertos objetos visuales de un informe tardan mucho tiempo en mostrarse cuando se ajusta un control deslizante. El Analizador de rendimiento puede indicarle qué tipo objeto visual es el culpable, identificando además los aspectos del objeto visual que tardan más tiempo en procesarse. 

Una vez iniciada la grabación, el botón **Iniciar grabación** está atenuado (inactivo, ya que ya ha empezado a grabar) y el botón **Detener** está activo. 

El Analizador de rendimiento recopila y muestra la información de medida de rendimiento en tiempo real. Por lo tanto, cada vez que haga clic en un objeto visual, mueva una segmentación o interactúe de cualquier otra manera, el Analizador de rendimiento muestra inmediatamente los resultados de rendimiento en su panel.

Si el panel tiene más información de la que se puede mostrar, aparece una barra de desplazamiento para ir a la información adicional.

Cada interacción tiene un identificador de sección en el panel, que describe la acción que inició las entradas de registro. En la imagen siguiente, la interacción que se produjo fue que los usuarios cambiaron una segmentación.

![Secciones basadas en el tipo de interacción](media/desktop-performance-analyzer/performance-analyzer-04.png)

La información de cada registro de objetos visuales incluye el tiempo empleado (duración) para completar las siguientes categorías de tareas:

* **Consultas DAX**: si se requiere una consulta DAX, este es el tiempo transcurrido desde que el objeto visual envía la consulta hasta que Analysis Services devuelve los resultados.
* **Presentación visual**: tiempo necesario para que el objeto visual dibuje en la pantalla, incluido el tiempo necesario para recuperar imágenes web o geocodificación. 
* **Otros**: tiempo que el objeto visual necesita para preparar las consultas, esperar a que se completen otros objetos visuales o realizar otro procesamiento en segundo plano.

Los valores **Duración (ms)** indican la diferencia entre una marca de tiempo de *inicio* y de *finalización* para cada operación. La mayoría de las operaciones del lienzo y los objetos visuales se ejecutan de forma secuencial en un único subproceso de interfaz de usuario, que se comparte entre varias operaciones. Las duraciones notificadas incluyen el tiempo invertido en cola mientras se completan otras operaciones. En el [ejemplo Analizador de rendimiento](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer) de GitHub y su [documentación](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx) asociada se proporcionan detalles sobre cómo los objetos visuales consultan los datos y cómo se representan.


![elementos de información de registro](media/desktop-performance-analyzer/performance-analyzer-06.png)

Después de haber interactuado con los elementos del informe que desea medir con el Analizador de rendimiento, puede seleccionar el botón **Detener**. La información de rendimiento permanece en el panel después de seleccionar **Detener** para su análisis.

Para borrar la información del panel del Analizador de rendimiento, seleccione **Borrar**. Se borra toda la información y no se guarda al seleccionar **Borrar**. Vea la sección siguiente para aprender a guardar información en los registros. 

## <a name="refreshing-visuals"></a>Actualización de objetos visuales

Puede seleccionar **Actualizar objetos visuales** en el panel del Analizador de rendimiento para actualizar todos los objetos visuales de la página actual del informe, y con ello hacer que el Analizador de rendimiento recopile información sobre todos estos objetos visuales.

También puede actualizar objetos visuales individuales. Cuando el Analizador de rendimiento está grabando, puede seleccionar **Actualizar este objeto visual**, que se encuentra en la esquina superior derecha de cada uno de los objetos visuales, para actualizar dicho objeto visual y capturar su información de rendimiento.

![actualizar un solo objeto visual](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Almacenamiento de la información de rendimiento

Puede guardar la información que el Analizador de rendimiento crea sobre un informe seleccionando el botón **Exportar**. Al seleccionar **Exportar**, se crea un archivo .json con información del panel del Analizador de rendimiento. 

![Guarde el archivo de registro para el Analizador de rendimiento](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Pasos siguientes
Para más información acerca de **Power BI Desktop** y cómo empezar a trabajar, consulte los siguientes artículos.

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Conectarse a los datos en Power BI Desktop](desktop-connect-to-data.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)   

Para obtener más información sobre el ejemplo Analizador de rendimiento, consulte los recursos siguientes.

* [Ejemplo Analizador de rendimiento](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer)
* [Documentación del ejemplo Analizador de rendimiento](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx)