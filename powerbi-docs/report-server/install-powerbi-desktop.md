---
title: Instalar Power BI Desktop optimizado para el servidor de informes de Power BI
description: Aprenda a instalar Power BI Desktop optimizado para el servidor de informes de Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/03/2019
ms.openlocfilehash: 2a95f8afce2762b82e73741563a29fa22b433d36
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874113"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Instalar Power BI Desktop optimizado para el servidor de informes de Power BI

Para crear informes de Power BI para Power BI Report Server, tendrá que descargar e instalar la versión de Power BI Desktop optimizada para Power BI Report Server. Esta es una versión de Power BI Desktop distinta de la que se usa con el servicio Power BI. Por ejemplo, la versión de Power BI Desktop para el servicio Power BI contiene características en versión preliminar que no se incluyen en la versión de Power BI Report Server hasta que están disponibles con carácter general. Es necesario usar esta versión para asegurarse de que el servidor de informes puede interactuar con una versión conocida de los informes y el modelo. 

La buena noticia es que puede instalar en paralelo Power BI Desktop y una versión optimizada para Power BI Report Server en el mismo equipo.

## <a name="download-and-install-power-bi-desktop"></a>Descarga e instalación de Power BI Desktop

La mejor manera de asegurarse de que tiene la versión más actualizada de Power BI Desktop optimizado para Power BI Report Server es iniciarlo desde el portal web de su servidor de informes.

1. En el portal web de Report Server, seleccione la flecha **Descargar** > **Power BI Desktop**.

    ![Descarga de Power BI Desktop desde el portal web](media/install-powerbi-desktop/report-server-download-web-portal.png)

    O bien, vaya a la página principal de [Power BI Report Server](https://powerbi.microsoft.com/report-server/) y seleccione **Opciones avanzadas de descarga**.

2. En la página del Centro de descarga, seleccione un idioma y después **Descargar**.

3. En función de su equipo, seleccione: 

    - **PBIDesktopRS.msi** (versión de 32 bits).
    - **PBIDesktopRS_x64.msi** (versión de 64 bits).

1. Después de descargar el instalador, ejecute el Asistente para la instalación de Power BI Desktop (septiembre de 2019).

2. Al final del proceso de instalación, seleccione **Iniciar Power BI Desktop**.

    Se inicia automáticamente y está listo para funcionar.

## <a name="verify-youre-using-the-correct-version"></a>Comprobación relativa al uso de una versión correcta
Comprobar que esté usando la versión correcta de Power BI Desktop es muy sencillo: solo tiene que echar un vistazo a la pantalla de inicio o a la barra de título de Power BI Desktop. Sabrá que tiene la versión correcta porque aparece **Power BI Desktop (septiembre de 2019)** en la barra de título. Además, los colores del logotipo de Power BI aparecen invertidos, es decir, amarillo sobre negro en lugar de negro sobre amarillo.

![Power BI Desktop, septiembre de 2019](media/install-powerbi-desktop/power-bi-report-server-desktop-sept-2019.png)

La versión de Power BI Desktop para el servicio Power BI no indica el mes ni el año en la barra de título.

## <a name="file-extension-association"></a>Asociación de extensión de archivo
Si instala Power BI Desktop y una versión optimizada para Power BI Report Server en la misma máquina, la instalación más reciente de Power BI Desktop será la que esté asociada a los archivos .pbix. Así pues, al hacer doble clic en un archivo .pbix, se iniciará la versión de Power BI Desktop que haya instalado más recientemente.

Si tiene Power BI Desktop e instala una versión optimizada para Power BI Report Server, los archivos .pbix se abrirán en esta última versión de forma predeterminada. Si quiere que Power BI Desktop sea la opción predeterminada para abrir un archivo .pbix, reinstale [Power BI Desktop desde Microsoft Store](https://aka.ms/pbidesktopstore).

Siempre puede abrir la versión de Power BI Desktop que desea usar en primer lugar. Y, después, abra el archivo desde Power BI Desktop.

Al editar un informe de Power BI desde Power BI Report Server, así como al crear un nuevo informe de Power BI desde el portal web, siempre se abre la versión correcta de Power BI Desktop.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Los informes de Power BI de Power BI Report Server, del servicio Power BI (https://app.powerbi.com) ) y de las aplicaciones móviles de Power BI actúan prácticamente igual, pero hay algunas características diferentes.

### <a name="selecting-a-language"></a>Selección de un idioma

Para Power BI Desktop optimizado para Power BI Report Server, el idioma se selecciona al instalar la aplicación. Después no se puede cambiar, pero se puede instalar una versión en otro idioma.

### <a name="report-visuals-in-a-browser"></a>Objetos visuales de informe en un explorador

Los informes de Power BI Report Server admiten casi todas las visualizaciones, incluidos los objetos visuales personalizados. Los informes del servidor de informes de Power BI no admiten:

* Objetos visuales de R
* Mapas de ArcGIS
* Rutas de navegación
* Características de la versión preliminar de Power BI Desktop

### <a name="reports-in-the-power-bi-mobile-apps"></a>Informes en las aplicaciones móviles de Power BI

Los informes del servidor de informes de Power BI admiten toda la funcionalidad básica en las [aplicaciones móviles de Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md), lo que incluye:

* [Diseño del informe en el teléfono](../desktop-create-phone-report.md): puede optimizar un informe para las aplicaciones móviles de Power BI. En teléfonos móviles, los informes optimizados presentan una disposición especial y el icono ![Icono de diseño de informes en el teléfono](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png).
  
    ![Informe optimizado para teléfonos](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Los informes del servidor de informes de Power BI no admiten estas características en las aplicaciones móviles de Power BI:

* Objetos visuales de R
* Mapas de ArcGIS
* Objetos visuales personalizados
* Rutas de navegación
* Filtrado geográfico o códigos de barras

## <a name="power-bi-desktop-for-earlier-versions-of-power-bi-report-server"></a>Power BI Desktop para versiones anteriores de Power BI Report Server

Si la versión de Power BI Report Server es anterior, se necesita la versión correspondiente de Power BI Desktop. Este es el vínculo para descargar una versión anterior.

- Microsoft Power BI Desktop ([optimizado para Power BI Report Server: enero de 2019](https://go.microsoft.com/fwlink/?linkid=2055039))

## <a name="next-steps"></a>Pasos siguientes

Una vez que Power BI Desktop se ha instalado, puede empezar a crear informes de Power BI.

[Creación de un informe de Power BI para Power BI Report Server](quickstart-create-powerbi-report.md)  
[¿Qué es Power BI Report Server?](get-started.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
