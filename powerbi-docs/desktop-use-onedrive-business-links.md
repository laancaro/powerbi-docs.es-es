---
title: Usar vínculos de OneDrive para la Empresa en Power BI Desktop
description: Usar vínculos de OneDrive para la Empresa en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 706703985242284725fb4fc2d42bf46e54c605c7
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709729"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Usar vínculos de OneDrive para la Empresa en Power BI Desktop
Muchas personas tienen los libros de Excel almacenados en OneDrive para la Empresa, que sería ideal para su uso con Power BI Desktop. Con Power BI Desktop, puede usar los vínculos en línea para archivos de Excel almacenados en OneDrive para la Empresa con el fin de crear informes y objetos visuales. Puede usar una cuenta de grupo de OneDrive para la Empresa, o bien una personal.

La obtención de un vínculo en línea desde OneDrive para la Empresa requiere unos pasos específicos. Las siguientes secciones explican estos pasos, que le permiten compartir el vínculo de archivo entre grupos, en distintos equipos y con sus compañeros de trabajo.

## <a name="get-a-link-from-excel"></a>Obtención de un vínculo de Excel
1. Vaya a la ubicación de OneDrive para la Empresa mediante un explorador. Haga clic con el botón derecho en el archivo que desee usar y seleccione **Abrir en Excel**.
   
   > [!NOTE]
   > Es posible que la interfaz de explorador no tenga exactamente el mismo aspecto que la siguiente imagen. Hay muchas maneras de seleccionar **Abrir en Excel** para los archivos de la interfaz del explorador de OneDrive para la Empresa. Puede utilizar cualquier opción que permita abrir el archivo en Excel.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. En Excel, seleccione **Archivo** > **Información** y, después, seleccione **Copiar ruta de acceso**, encima de **Proteger libro**.
   
   ![](media/desktop-use-onedrive-business-links/onedrive-copy-path.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Usar el vínculo en Power BI Desktop
En Power BI Desktop, puede usar el vínculo que acaba de copiar en el portapapeles. Realice los pasos siguientes:

1. En Power BI Desktop, seleccione **Obtener datos** > **Web**.
   
   ![](media/desktop-use-onedrive-business-links/power-bi-web-link-onedrive.png)
2. Con la opción **Básico** seleccionada, pegue el vínculo en el cuadro de diálogo **De la web**.
3. Quite la cadena *?web=1* al final del vínculo para que Power BI Desktop pueda navegar correctamente hasta el archivo y, después, seleccione **Aceptar**.
   
    ![](media/desktop-use-onedrive-business-links/power-bi-web-link-confirmation.png) 
4. Si Power BI Desktop solicita las credenciales, elija **Windows** (para sitios de SharePoint locales) o **Cuenta profesional** (para los sitios de Office 365 o OneDrive para la Empresa).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

   Aparecerá un cuadro de diálogo **Navegador**, que le permite realizar la selección a partir de las tablas, hojas y rangos que se encuentran en el libro de Excel. Desde allí, puede usar el archivo de OneDrive para la Empresa, al igual que cualquier otro archivo de Excel. Puede crear informes y utilizarlos en conjuntos de datos, tal como lo haría con cualquier otro origen de datos.

> [!NOTE]
> Para usar un archivo de OneDrive para la Empresa como origen de datos en el servicio Power BI, con **Actualizar servicio** habilitado para ese archivo, asegúrese de seleccionar **OAuth2** como **Método de autenticación** al configurar las opciones de actualización. De lo contrario, podría encontrarse un error (como *No se pudieron actualizar las credenciales del origen de datos*) al intentar realizar la conexión o la actualización. Seleccionar **OAuth2** como método de autenticación soluciona ese error de credenciales.
> 
> 

