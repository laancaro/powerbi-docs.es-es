---
title: Incorporación de hipervínculos (direcciones URL) a una tabla o matriz
description: En este tema se enseña cómo agregar hipervínculos (direcciones URL) a una tabla. Usará Power BI Desktop para agregar hipervínculos (direcciones URL) a un conjunto de datos. Luego, en Power BI Desktop o en el servicio Power BI, puede agregar esos hipervínculos a las tablas y matrices de informes.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: f8a49780804449296194d7adb8091f7f0c5748fe
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427815"
---
# <a name="add-hyperlinks-urls-to-a-table-or-matrix"></a>Incorporación de hipervínculos (direcciones URL) a una tabla o matriz
En este tema se enseña cómo agregar hipervínculos (direcciones URL) a una tabla. Usará Power BI Desktop para agregar hipervínculos (direcciones URL) a un conjunto de datos. Esos hipervínculos se pueden agregar luego a las tablas y matrices de informes de Power BI Desktop o del servicio Power BI. De esta manera, puede mostrar la dirección URL o un icono de vínculo, o dar formato a otra columna como texto de vínculo.

![Tabla con hipervínculos](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

También puede crear hipervínculos en [cuadros de texto de los informes](service-add-hyperlink-to-text-box.md) en el servicio Power BI y Power BI Desktop. Y, en el servicio Power BI, puede agregar hipervínculos a [iconos de los paneles](service-dashboard-edit-tile.md) y a [cuadros de texto de los paneles](service-dashboard-add-widget.md). 


## <a name="format-a-url-as-a-hyperlink-in-power-bi-desktop"></a>Aplicación de formato a una dirección URL como un hipervínculo en Power BI Desktop

Puede dar formato a un campo con direcciones URL como hipervínculos en Power BI Desktop, pero no en el servicio Power BI. También puede [dar formato a hipervínculos en Power Pivot para Excel](#create-a-table-or-matrix-hyperlink-in-excel-power-pivot) antes de importar el libro en Power BI.

1. En Power BI Desktop, si aún no existe en el conjunto de datos un campo con un hipervínculo, agréguelo como una [columna personalizada](desktop-common-query-tasks.md).

    > [!NOTE]
    > No puede crear una columna en modo DirectQuery.  Pero si los datos ya contienen direcciones URL, puede convertirlas en hipervínculos.

2. En la vista Datos o Informe, seleccione la columna. 

3. En la pestaña **Modelado**, seleccione **Categoría de datos** > **Dirección URL web**.
   
    ![Lista desplegable de categorías de datos](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url.png)

    > [!NOTE]
    > Las direcciones URL tienen que comenzar con determinados prefijos. Para obtener una lista completa, consulte [Consideraciones y solución de problemas](#considerations-and-troubleshooting) en este artículo.

## <a name="create-a-table-or-matrix-with-a-hyperlink"></a>Creación de tablas o matrices con hipervínculos

1. Después de [dar formato a un hipervínculo como una dirección URL](#format-a-url-as-a-hyperlink-in-power-bi-desktop), cambie a la vista de informe.
2. Cree una tabla o una matriz con el campo al que le ha aplicado la categoría de dirección URL web. Los hipervínculos son de color azul y están subrayados.

    ![Vínculos de color azul y subrayados](media/power-bi-hyperlinks-in-tables/power-bi-url-blue-underline.png)


## <a name="display-a-hyperlink-icon-instead-of-a-url"></a>Visualización de un icono de hipervínculo en lugar de una dirección URL

Si no quiere que aparezca una dirección URL larga en una tabla, puede mostrar un icono de hipervínculo ![Icono de hipervínculo](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) en su lugar. 

> [!NOTE]
> No se pueden mostrar iconos en una matriz.
   
1. Primero, [cree una tabla con un hipervínculo](#create-a-table-or-matrix-with-a-hyperlink).

2. Seleccione la tabla para activarla.

    Seleccione el icono de **Formato** ![icono de rodillo de pintura](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) para abrir la pestaña Formato.

    Expanda **Valores**, busque el **icono de dirección URL** y **actívelo**.

    ![Activación del icono de la dirección URL](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Opcional) [Publique el informe](desktop-upload-desktop-files.md) de Power BI Desktop en el servicio Power BI. Al abrir el informe en el servicio Power BI, los hipervínculos también funcionan ahí.

## <a name="format-link-text-as-a-hyperlink"></a>Aplicación de formato al texto del vínculo como un hipervínculo

También puede dar formato a otro campo de una tabla como hipervínculo y no tener una columna para la dirección URL. En este caso, no da formato a la columna como dirección URL web.

> [!NOTE]
> No se puede dar formato a otro campo como hipervínculo en una matriz.

1. Si no existe aún un campo con un hipervínculo en el conjunto de datos, use Power BI Desktop para agregarlo como [columna personalizada](desktop-common-query-tasks.md). De nuevo, no puede crear una columna en modo DirectQuery.  Pero si los datos ya contienen direcciones URL, puede convertirlas en hipervínculos.

2. En la vista Datos o Informe, seleccione la columna que contiene la dirección URL. 

3. En la pestaña **Modelado**, seleccione **Categoría de datos**. Asegúrese de que la columna tenga el formato **Sin categoría**.

2. En la vista de informe, cree una tabla o una matriz con la columna de dirección URL y la columna a la que va a aplicar formato como texto de vínculo.

3. Con la tabla seleccionada, seleccione el icono de **Formato** ![icono de rodillo de pintura](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) para abrir la pestaña Formato.

4. Expanda **Formato condicional** y asegúrese de que el nombre del cuadro sea la columna que quiere como texto de vínculo. Busque **URL web** y **actívelo**.

    ![Dirección URL web de formato condicional](media/power-bi-hyperlinks-in-tables/power-bi-format-conditional-web-url.png)

    > [!NOTE]
    > Si no ve una opción **URL web**, asegúrese de que la columna que contiene los hipervínculos *no* tenga formato de **URL web** en el cuadro desplegable **Categoría de datos**.

5. En el cuadro de diálogo **Dirección URL web**, seleccione el campo que contiene la dirección URL en el cuadro **Según el campo** > **Aceptar**.

    ![Cuadro de diálogo Dirección URL web](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url-dialog.png)

    Ahora el texto de esa columna tiene el formato del vínculo.

    ![Texto con formato de hipervínculo](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

1. (Opcional) [Publique el informe](desktop-upload-desktop-files.md) de Power BI Desktop en el servicio Power BI. Al abrir el informe en el servicio Power BI, los hipervínculos también funcionan ahí.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Crear un hipervínculo de tabla o matriz en Power Pivot para Excel

Otra manera de agregar hipervínculos a las tablas y matrices de Power BI es crear los hipervínculos en el conjunto de datos antes de importar o conectarse a ese conjunto de datos desde Power BI. Este ejemplo utiliza un libro de Excel.

1. Abra el libro en Excel.
2. Seleccione la pestaña **PowerPivot** y, a continuación, elija **Administrar**.
   
   ![Abrir PowerPivot en Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Cuando se abra PowerPivot, seleccione la pestaña **Opciones avanzadas**.
   
   ![Pestaña Opciones avanzadas de PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Coloque el cursor en la columna que contiene las direcciones URL que desea convertir en hipervínculos de tablas de Power BI.
   
   > [!NOTE]
   > Las direcciones URL tienen que comenzar con determinados prefijos. Para obtener una lista completa, consulte [Consideraciones y solución de problemas](#considerations-and-troubleshooting).
   > 
   
5. En el grupo **Propiedades de informes** , seleccione la lista desplegable **Categoría de datos** y elija **Dirección URL web**. 
   
   ![Lista desplegable de categorías de datos en Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. En el servicio Power BI o Power BI Desktop, conéctese a este libro o impórtelo.
7. Cree una visualización de la tabla que incluya el campo de dirección URL.
   
   ![Crear una tabla en Power BI con el campo de dirección URL](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

Las direcciones URL tienen que comenzar con uno de los siguientes elementos:
- http
- https
- -mailto
- file
- ftp
- news
- telnet

P: ¿Puedo usar una dirección URL personalizada como hipervínculo en una tabla o matriz?    
R: No. Puede utilizar un icono de vínculo. Si necesita texto personalizado para los hipervínculos y la lista de direcciones URL es breve, considere la posibilidad de utilizar un cuadro de texto en su lugar.


## <a name="next-steps"></a>Pasos siguientes
[Visualizaciones en informes de Power BI](visuals/power-bi-report-visualizations.md)

[Conceptos básicos para los diseñadores en el servicio Power BI](service-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

