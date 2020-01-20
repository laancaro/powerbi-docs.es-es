---
title: Inicio rápido sobre conexión a datos en Power BI Desktop
description: Conexión a los orígenes de datos disponibles en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 5aed52ec232d3e603d69bfe93640187401279ff6
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885240"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Inicio rápido: Conectarse a los datos en Power BI Desktop

En este inicio rápido, se conecta a datos mediante Power BI Desktop, que es el primer paso para compilar modelos de datos y crear informes.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Si no está registrado en Power BI, [regístrese para obtener una evaluación gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para completar los pasos de este artículo, necesitará los siguientes recursos:

* Descargar e instalar Power BI Desktop, que es una aplicación gratuita que se ejecuta en el equipo local. Puede [descargar Power BI Desktop](https://powerbi.microsoft.com/desktop) directamente,o bien puede obtenerlo en [Microsoft Store](https://aka.ms/pbidesktopstore).
* [Descargue este libro de Excel de ejemplo](https://go.microsoft.com/fwlink/?LinkID=521962) y cree una carpeta denominada *C:\PBID-qs* donde puede almacenar el archivo de Excel. En los pasos posteriores de este inicio rápido se supone que esa es la ubicación del archivo para el libro de Excel descargado.
* Para muchos conectores de datos de Power BI Desktop, se requiere Internet Explorer 10 (o posterior) para la autenticación.

## <a name="launch-power-bi-desktop"></a>Inicio de Power BI Desktop

Una vez que instale Power BI Desktop, inicie la aplicación, para que se ejecute en el equipo local. Se le mostrará un tutorial de Power BI. Siga el tutorial o cierre el cuadro de diálogo para empezar con un lienzo en blanco. En el lienzo se crean objetos visuales e informes a partir de los datos.

![Power BI Desktop con lienzo en blanco](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Conectar a datos

Con Power BI Desktop puede conectarse a muchos tipos de datos diferentes. Estos orígenes incluyen orígenes de datos básicos, como un archivo de Microsoft Excel. Puede conectarse a servicios en línea que contienen todo tipo de datos, como Salesforce, Microsoft Dynamics, Azure Blob Storage y muchos más.

Para conectarse a datos, seleccione **Obtener datos** desde la cinta de opciones **Inicio**.

![Obtener datos en la cinta Inicio](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Aparecerá la ventana **Obtener datos**. Puede elegir entre muchos orígenes de datos diferentes a los que poder conectar Power BI Desktop. En este inicio rápido, use el libro de Excel que descargó en [Requisitos previos](#prerequisites).

![Obtener datos de todos los orígenes](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Como este origen de datos es un archivo de Excel, seleccione **Excel** en la ventana **Obtener datos** y luego elija el botón **Conectar**.

Power BI le pedirá que proporcione la ubicación del archivo de Excel al que se quiere conectar. El archivo descargado se denomina *Ejemplo financiero*. Seleccione el archivo y luego elija **Abrir**.

![Obtención de datos en el ejemplo financiero](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

Power BI Desktop carga el libro, lee su contenido y muestra los datos disponibles en el archivo en la ventana **Navegador**. En esa ventana, puede elegir qué datos quiere cargar en Power BI Desktop. Seleccione las tablas marcando las casillas situadas junto a cada tabla que quiere importar. Importe ambas tablas disponibles.

![Selección de datos en la ventana Navegador](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Una vez realizadas las selecciones, haga clic en **Cargar** para importar los datos en Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Visualización de los datos en el panel Campos

Una vez cargadas las tablas, se muestran los datos en el panel **Campos**. Seleccione la flecha que está junto al nombre de cada tabla para expandirlas. En la siguiente imagen, se expande la tabla *financials*, que muestra cada uno de sus campos.

![Obtener datos](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Y ya está. Se ha conectado a los datos de Power BI Desktop, ha cargado esos datos y ahora puede ver todos los campos disponibles en las tablas.

## <a name="next-steps"></a>Pasos siguientes

Puede hacer muchísimas cosas con Power BI Desktop tras conectarse a los datos. Puede crear objetos visuales e informes. Eche un vistazo a los siguientes recursos para ayudarlo a empezar:

* [Introducción a Power BI Desktop](desktop-getting-started.md)
