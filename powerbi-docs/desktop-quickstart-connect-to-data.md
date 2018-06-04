---
title: Inicio rápido sobre conexión a datos
description: Conexión a un origen de datos en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: quickstart
ms.date: 05/07/2018
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 3f29bd899c62adbe2de1fdedd25b60cb104c71e0
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34287840"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Inicio rápido: Conectarse a los datos en Power BI Desktop

En este inicio rápido, se conecta a datos mediante **Power BI Desktop**, que es el primer paso para compilar modelos de datos y crear informes.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Si no está registrado en Power BI, [regístrese para obtener una evaluación gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para completar los pasos descritos en este artículo, necesita lo siguiente:
* Descargue e instale **Power BI Desktop**, que es una aplicación gratuita que se ejecuta en el equipo local. Puede [descargar **Power BI Desktop**](https://powerbi.microsoft.com/desktop) directamente,o bien puede obtenerlo [de **Microsoft Store**](http://aka.ms/pbidesktopstore).
* [Descargue este libro de Excel de ejemplo](http://go.microsoft.com/fwlink/?LinkID=521962) y cree una carpeta denominada *C:\PBID-qs* donde puede almacenar el archivo de Excel. En los pasos posteriores de este inicio rápido se supone que esa es la ubicación del archivo para el libro de Excel descargado.

## <a name="launch-power-bi-desktop"></a>Inicio de Power BI Desktop

Una vez que instale **Power BI Desktop**, inicie la aplicación, para que se ejecute en el equipo local. Aparece un lienzo en blanco, que es donde crea los objetos visuales y los informes de los datos a los que se conecta. 

![Power BI Desktop: lienzo en blanco](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Conectar a datos

Con **Power BI Desktop** puede conectarse a muchos tipos de datos diferentes. Puede conectarse a orígenes de datos básicos, como un archivo de Microsoft Excel, y también puede conectarse a servicios en línea que contienen todo tipo de datos, como Salesforce, Microsoft Dynamics, Azure Blob Storage y muchos más. 

Para conectarse a datos, seleccione **Obtener datos** desde la cinta de opciones **Inicio**.

![Obtener datos](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Se abre la ventana **Obtener datos**, donde puede elegir entre muchos orígenes de datos diferentes a los que poder conectar **Power BI Desktop**. En este inicio rápido se usa el libro de Excel que ha descargado, como se describe en la sección *Requisitos previos* al principio de este artículo. 

![Obtener datos](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Como se trata de un archivo de Excel, se selecciona **Excel** en la ventana **Obtener datos** y luego se selecciona el botón **Conectar**.

Se le pedirá que proporcione la ubicación del archivo de Excel al que se desea conectar. El archivo descargado se llama *Financial Sample*, así que se selecciona dicho archivo y luego **Abrir**.

![Obtener datos](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

**Power BI Desktop** carga el libro, lee su contenido y muestra los datos disponibles en el archivo en la ventana **Navegador**, donde puede elegir qué datos desea cargar en Power BI Desktop. Seleccione las tablas; para ello, marque las casillas que están al lado de cada tabla que desea importar. En este caso, se podrán importar las dos tablas disponibles.

![Obtener datos](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Una vez realizadas las selecciones, haga clic en **Cargar** para importar los datos en Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Visualización de los datos en el panel Campos

Una vez cargadas las tablas, se muestran los datos en el panel **Campos**. Seleccione el triángulo que está junto al nombre de cada tabla para expandirlas. En la siguiente imagen, se expande la tabla *financials*, que muestra cada uno de sus campos. 

![Obtener datos](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Y ya está. Se ha conectado a los datos de **Power BI Desktop**, ha cargado esos datos y ahora puede ver todos los campos disponibles en las tablas.


## <a name="next-steps"></a>Pasos siguientes
Puede hacer muchísimas cosas con **Power BI Desktop** tras conectarlo a los datos, como crear objetos visuales e informes. Eche un vistazo a los siguientes recursos para ayudarlo a empezar:

* [Guía de introducción de Power BI Desktop](desktop-getting-started.md)


