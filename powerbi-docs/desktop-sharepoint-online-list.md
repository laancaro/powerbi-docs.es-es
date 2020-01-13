---
title: Creación de un informe en una lista de SharePoint
description: En este tutorial se muestra cómo transformar los datos de la lista de SharePoint en un informe de Power BI.
author: AdamDWilson
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/27/2019
ms.author: adamw
LocalizationGroup: Visualizations
ms.openlocfilehash: a583957cddfc6554aae323624caaa5430038cecf
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75772710"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Creación de un informe en una lista de SharePoint

Muchos equipos y organizaciones usan listas de SharePoint Online para almacenar datos porque es fácil de configurar y, para los usuarios, de actualizar.  A veces, un gráfico resulta mucho más sencillo para comprender rápidamente los datos, en lugar de mirar la propia lista. En este tutorial se muestra cómo transformar los datos de la lista de SharePoint en un informe de Power BI.

Vea este vídeo del tutorial de cinco minutos o desplácese hacia abajo para obtener instrucciones paso a paso.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>Parte 1: Conexión a la lista de SharePoint

1. Si todavía no lo tiene, descargue e instale [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
2. Abra Power BI Desktop y, en la pestaña Inicio de la cinta, seleccione **Obtener datos** > **Más**.
3. Seleccione **Servicios en línea** y, después, **Lista de SharePoint Online**.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="get data" width="350"/>

4. Seleccione **Conectar**.
4. Busque la dirección (también conocida como dirección URL) del sitio de SharePoint Online que contenga la lista.  Desde una página de SharePoint Online, normalmente puede obtener la dirección del sitio en **Inicio**, en el panel de navegación (o el icono del sitio en la parte superior) y, después, copiar la dirección de la barra de direcciones del explorador web.

   Vea un vídeo de este paso:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. En Power BI Desktop, pegue la dirección en el campo **URL del sitio** del cuadro de diálogo Abrir.

6. Es posible que vea o no una pantalla de acceso de SharePoint como la de la imagen siguiente.  Si no la ve, vaya al paso 10.  Si la ve, seleccione **Cuenta de Microsoft** en el lado izquierdo de la página.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Seleccione **Iniciar sesión** y escriba el nombre de usuario y la contraseña que usa para iniciar sesión en Microsoft Office 365.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. Cuando haya iniciado sesión, seleccione **Conectar**.

9. En el lado izquierdo del navegador, active la casilla situada junto a la lista de SharePoint a la que se quiere conectar.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="get data" width="450"/>

10. Seleccione **Cargar**.  Power BI carga los datos de la lista en un informe nuevo.

## <a name="part-2-create-a-report"></a>Parte 2: Crear un informe

1. En el lado izquierdo, seleccione el icono **Datos** para ver que se han cargado los datos de la lista de SharePoint.

2. Asegúrese de que las columnas de la lista con números muestren el icono de suma, o Sigma, en el **panel Campos** de la derecha.  Si en alguna no se muestra, seleccione el encabezado de columna en la vista de tabla, seleccione la pestaña **Modelado** y, después, cambie **Tipo de datos** a **Número decimal** o **Número entero**, en función de los datos.  Si se le pide que confirme el cambio, seleccione **Sí**.  Si el número es un formato especial, como de moneda, también puede elegirlo en **Formato**.

   Vea un vídeo de este paso:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. En el lado izquierdo, seleccione el icono **Informe**.
4. Para elegir las columnas que quiere visualizar, seleccione la casilla situada junto a ellas en el panel **Campos** de la derecha.

   Vea un vídeo de este paso:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Cambie el tipo de objeto visual si es necesario.
6. Puede crear varias visualizaciones en el mismo informe anulando la selección del objeto visual existente y seleccionando las casillas de otras columnas en el panel **Campos**.
7. Seleccione **Guardar** para guardar el informe.
