---
title: Insertar un informe mediante un elemento iFrame
description: Inserción de un informe de Power BI Report Server con un elemento iFrame en SharePoint Server
author: markingmyname
ms.author: maghan
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.component: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 8d7653e6f390959df745fa2b19076ee89b26b1bc
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34293706"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Inicio rápido: Inserción de un informe de Power BI Report Server con un elemento iFrame en SharePoint Server

En este inicio rápido obtendrá información sobre cómo insertar un informe de Power BI Report Server mediante el uso de un elemento iFrame en una página de SharePoint. Si trabaja con SharePoint Online, Power BI Report Server debe ser de acceso público. En SharePoint Online, el elemento web de Power BI que funciona con el servicio Power BI no funcionará con Power BI Report Server. 

![Ejemplo de iFrame](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>Requisitos previos
* Debe tener [Power BI Report Server](https://powerbi.microsoft.com/en-us/report-server/) instalado y configurado.
* Necesitará tener instalado [Power BI Desktop optimizado para Power BI Report Server](install-powerbi-desktop.md).
* Debe tener un entorno de [SharePoint](https://docs.microsoft.com/en-us/sharepoint/install/install) instalado y configurado.

## <a name="creating-the-power-bi-report-server-report-url"></a>Creación de la dirección URL del informe de Power BI Report Server

1. Descargue el ejemplo de GitHub: [demostración de blog](https://github.com/Microsoft/powerbi-desktop-samples).

    ![Descargar archivo PBIX de ejemplo](media/quickstart-embed/quickstart_embed_14.png)

2. Abra el archivo PBIX de ejemplo desde GitHub en **Power BI Desktop optimizado para Power BI Report Server**.

    ![Herramienta de PBI RS Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Guarde el informe en **Power BI Report Server**. 

    ![Guardar en PBI RS](media/quickstart-embed/quickstart_embed_03.png)

4. Vea el informe en el **portal web**.

    ![Portal web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>Captura del parámetro de dirección URL

Cuando tenga la dirección URL, puede crear un iFrame en una página de SharePoint para hospedar el informe. Para cualquier dirección URL de informes de Power BI Report Server, puede agregar un parámetro de cadena de consulta de `?rs:embed=true` para insertar el informe en un elemento iFrame. 

   Por ejemplo:
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>Inserción de un informe de Power BI Report Server con un elemento iFrame en SharePoint

1. Vaya a la página **Contenidos del sitio** de SharePoint.

    ![Página de contenidos del sitio](media/quickstart-embed/quickstart_embed_05.png)

2. Elija la página donde desea agregar el informe.

    ![Aplicación de página de contenidos del sitio](media/quickstart-embed/quickstart_embed_06.png)

3. Seleccione el icono de engranaje en la parte superior derecha y seleccione **Editar página**.

    ![Opción Editar página](media/quickstart-embed/quickstart_embed_07.png)

4. Seleccione **Agregar elemento web**.

    ![Agregar elemento web](media/quickstart-embed/quickstart_embed_08.png)

5. En **Categorías**, seleccione **Medios y contenido**, en **Elementos**, seleccione **Editor de contenido** y, a continuación, seleccione **Agregar**.

    ![Seleccionar elemento web en el editor de contenido](media/quickstart-embed/quickstart_embed_09.png) ![Seleccionar Agregar](media/quickstart-embed/quickstart_embed_091.png)

6. Seleccione **Click here to add new content** (Haga clic aquí para agregar contenido nuevo).

    ![Agregar contenido nuevo](media/quickstart-embed/quickstart_embed_10.png)

7. En la cinta de opciones, seleccione la pestaña **Aplicar formato al texto** y luego seleccione **Editar origen**.

     ![Editar origen](media/quickstart-embed/quickstart_embed_11.png)

8. En la ventana Editar origen, pegue el código del elemento iFrame y seleccione Aceptar.

    ![Código de iFrame](media/quickstart-embed/quickstart_embed_12.png)

     Por ejemplo:
     ```
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. En la cinta de opciones, seleccione la pestaña **Página** y luego seleccione **Detener la edición**.

    ![Detener la edición](media/quickstart-embed/quickstart_embed_13.png)

10. Ahora debería ver el informe en la página.

    ![Ejemplo de iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Pasos siguientes

[Inicio rápido: Creación de un informe de Power BI para el servidor de informes de Power BI](quickstart-create-powerbi-report.md)  
[Inicio rápido: Creación de un informe paginado para el servidor de informes de Power BI](quickstart-create-paginated-report.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/) 