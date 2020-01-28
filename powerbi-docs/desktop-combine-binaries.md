---
title: Combinación de archivos (binarios) en Power BI Desktop
description: Combine fácilmente orígenes de datos de archivos (binarios) en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 07381461375ea7b9707b91c807e92cdb85c1d440
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161145"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinación de archivos (binarios) en Power BI Desktop

Este es un enfoque eficaz para la importación de datos en **Power BI Desktop**: Si dispone de varios archivos que tienen el mismo esquema, combínelos en una sola tabla lógica. Se han aumentado la comodidad y la expansión de esta popular técnica.

Para iniciar el proceso de combinar archivos de una misma carpeta, seleccione **Obtener datos**, elija **Archivo** > **Carpeta** y, a continuación, seleccione **Conectar**.

![Conectarse al archivo de carpetas, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Especifique la ruta de acceso a la carpeta, seleccione **Aceptar** y, a continuación, seleccione **Transformar datos** para ver los archivos de la carpeta en el Editor de Power Query.

## <a name="combine-files-behavior"></a>Comportamiento al combinar archivos

Para combinar archivos binarios en el Editor de Power Query, seleccione **Contenido** (la primera etiqueta de columna) y seleccione **Inicio** > **Combinar archivos**. O bien, basta con que seleccione el icono **Combinar archivos** situado junto a **Contenido**.

![Comando Combinar archivos, Editor de Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

La transformación *Combinar archivos* se comporta como se especifica debajo:

* La transformación Combinar archivos analiza todos los archivos de entrada para determinar el formato de archivo correcto que debe usarse, como *texto*, *libro de Excel* o *archivo JSON*.
* La transformación permite seleccionar un objeto específico del primer archivo (por ejemplo, un libro de Excel) para extraerlo.
  
  ![Cuadro de diálogo Combinar archivos, Editor de Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* A continuación, la transformación Combinar archivos realiza automáticamente estas acciones:
  
  * Crea una consulta de ejemplo que realiza todos los pasos de extracción necesarios en un único archivo.
  * Crea una *consulta de función* que parametriza la entrada de archivo/binario en la *consulta de ejemplo*. La consulta de ejemplo y la consulta de función se vinculan, de modo que los cambios hechos en la consulta de ejemplo se reflejan en la consulta de función.
  * Aplica la *consulta de función* a la consulta original con archivos binarios de entrada, como la consulta *Carpeta*. Aplica la consulta de función para entradas binarias en cada fila y, a continuación, expande la extracción de datos resultante como columnas de nivel superior.

    ![Resultados de la transformación Combinar archivos, Editor de Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> El ámbito de la selección en un libro de Excel afectará al comportamiento de combinar binarios. Por ejemplo, puede seleccionar una hoja de cálculo específica para combinar esa hoja de cálculo o seleccionar la raíz para combinar el archivo completo. Al seleccionar una carpeta se combinan los archivos que se encuentran en esa carpeta. 

Con el comportamiento de combinar archivos, se pueden combinar fácilmente todos los archivos de una determinada carpeta, siempre y cuando tengan el mismo tipo de archivo y estructura (como, por ejemplo, las mismas columnas).

Además, se pueden aplicar fácilmente pasos de transformación o extracción adicionales mediante la modificación de la consulta de ejemplo creada automáticamente y sin necesidad de preocuparse de la modificación o creación de más pasos de consulta de función. Cualquier cambio hecho en la consulta de ejemplo se generará automáticamente en la consulta de función vinculada.

## <a name="next-steps"></a>Pasos siguientes

Puede conectarse a todo tipo de datos con Power BI Desktop. Para obtener más información sobre orígenes de datos, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectarse a archivos CSV en Power BI Desktop](desktop-connect-csv.md)
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
