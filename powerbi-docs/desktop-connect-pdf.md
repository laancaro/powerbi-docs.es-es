---
title: Conectarse a un archivo PDF en Power BI Desktop (versión preliminar)
description: Conéctese fácilmente a archivos PDF y úselos en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/13/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 2ecd4b8e6295431f520dea61454bbf868bfab254
ms.sourcegitcommit: 6a6f552810a596e1000a02c8d144731ede59c0c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619687"
---
# <a name="connect-to-a-pdf-file-in-power-bi-desktop-preview"></a>Conectarse a un archivo PDF en Power BI Desktop (versión preliminar)
En Power BI Desktop, puede conectarse a un **archivo PDF** y usar los datos incluidos del archivo, como con cualquier otro origen de datos en Power BI Desktop.

![Conectarse a datos en archivos PDF](media/desktop-connect-pdf/connect-pdf_04.png)

En las secciones siguientes se describe cómo conectarse a un **archivo PDF**, seleccionar datos y enviarlos a **Power BI Desktop**.

## <a name="enable-the-pdf-connector"></a>Habilitar el conector de PDF
El conector de PDF es una versión preliminar para **Power BI Desktop** y debe habilitarse. Para habilitar el conector de PDF, seleccione **Archivo > Opciones y configuración > Opciones > Características en vista previa** y, después, active la casilla situada junto a **Get data from PDF files** (Obtener datos de archivos PDF). 

![Habilitar el conector de PDF en Opciones > Características en vista previa](media/desktop-connect-pdf/connect-pdf_01.png)

Deberá reiniciar **Power BI Desktop** después de realizar la selección.

Cuando use por primera vez el conector de **PDF (beta)**, se le advertirá de que el conector de PDF está aún en desarrollo y puede cambiar en el futuro. Seleccione **Continuar** para usar el conector.

Siempre se recomienda actualizar a la versión más reciente de **Power BI Desktop**, que se puede obtener desde un vínculo en [Obtener Power BI Desktop](desktop-get-the-desktop.md). 

## <a name="connect-to-a-pdf-file"></a>Conectarse a un archivo PDF
Para conectarse a un archivo **PDF**, seleccione **Get Data** (Obtener datos) en la cinta **Inicio** de Power BI Desktop. Seleccione **Archivo** en las categorías de la izquierda para mostrar **PDF (beta)**.

![Seleccionar PDF en Get Data (Obtener datos)](media/desktop-connect-pdf/connect-pdf_01.png)

Se le pedirá que indique la ubicación del archivo PDF que quiere usar. Después de indicar la ubicación del archivo y de cargarse el archivo PDF, aparece una ventana de **Navegador**, en la que se muestran los datos disponibles del archivo, desde donde puede seleccionar uno o varios elementos para importarlos y usarlos en **Power BI Desktop**.

![Conectarse a datos en archivos PDF](media/desktop-connect-pdf/connect-pdf_04.png)

Al activar una casilla junto a elementos detectados en el archivo PDF, estos se muestran en el panel derecho. Cuando esté listo para importar, seleccione el botón **Cargar** para introducir los datos en **Power BI Desktop**.

A partir del lanzamiento de **Power BI Desktop** en noviembre de 2018, puede especificar la **página de inicio** y la **página de finalización** como parámetros opcionales para la conexión PDF. También puede especificar estos parámetros en el lenguaje de fórmulas M, con el formato siguiente:

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`


## <a name="next-steps"></a>Pasos siguientes
Hay todo tipo de datos a los que puede conectarse con Power BI Desktop. Para obtener más información sobre orígenes de datos, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

