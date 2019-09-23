---
title: Incorporación de hipervínculos (direcciones URL) a una tabla
description: En este tema se enseña cómo agregar hipervínculos (direcciones URL) a una tabla. Usará Power BI Desktop para agregar hipervínculos (direcciones URL) a una tabla o matriz. Luego, en Power BI Desktop o en el servicio Power BI, puede agregar esos hipervínculos a las tablas y matrices de informes.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/30/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 58cb009e29c05ce318c5931fb418617e1ef63f4f
ms.sourcegitcommit: ba085b248c54e8fb1fd8eb2bb23a814e3fdd7ff6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937057"
---
# <a name="add-hyperlinks-urls-to-a-table"></a>Incorporación de hipervínculos (direcciones URL) a una tabla
En este tema se enseña cómo agregar hipervínculos (direcciones URL) a una tabla. Usará Power BI Desktop para agregar hipervínculos (direcciones URL) a una tabla o matriz. Luego, en Power BI Desktop o en el servicio Power BI, puede agregar esos hipervínculos a las tablas y matrices de informes. 

![Tabla con hipervínculos](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> [!NOTE]
> Puede crear hipervínculos de los [iconos de los paneles](service-dashboard-edit-tile.md) y de los [cuadros de texto de los paneles](service-dashboard-add-widget.md) sobre la marcha mediante el servicio Power BI. También, puede crear hipervínculos de los [cuadros de texto de los informes](service-add-hyperlink-to-text-box.md) sobre la marcha con el servicio Power BI y Power BI Desktop.
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Crear un hipervínculo de una tabla o matriz con Power BI Desktop
Puede crear hipervínculos de tablas y matrices en Power BI Desktop, pero no en el servicio Power BI. También puede crear hipervínculos en Power Pivot para Excel antes de importar el libro en Power BI. Ambos métodos se describen a continuación.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Crear un hipervínculo de tabla o matriz en Power BI Desktop
El procedimiento para agregar un hipervínculo depende de si ha importado los datos o los ha conectado mediante DirectQuery. Ambos escenarios se describen a continuación.

### <a name="for-data-imported-into-power-bi"></a>Para los datos importados en Power BI
1. Si el hipervínculo aún no existe como campo en el conjunto de datos, use Power BI Desktop para agregarlo como una [columna personalizada](desktop-common-query-tasks.md).
2. En la vista de datos, seleccione la columna y, en la pestaña **Modelado**, elija la lista desplegable de **Categoría de datos**.
   
    ![Lista desplegable de categorías de datos](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Seleccione **URL web**.
4. Cambie a la vista de informe y cree una tabla o matriz mediante el campo que se categoriza como una dirección URL web. Los hipervínculos aparecerán subrayados y de color azul.

    ![Vínculos de color azul y subrayados](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)

    > [!NOTE]
    > Las direcciones URL deben comenzar por **http://, https://** o **www**.
    >
   
1. Si no quiere que aparezca una dirección URL larga en una tabla, puede mostrar un icono de hipervínculo  ![Icono de hipervínculo](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) en su lugar. Tenga en cuenta que en las matrices no se muestran iconos.
   
    Seleccione el gráfico para activarlo.

    Seleccionar el icono de formato ![Icono de rodillo de pintura](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) para abrir la pestaña Formato.

    Expanda **Valores**, busque el **icono de la dirección URL** y **actívelo**.

    ![Activación del icono de la dirección URL](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Opcional) [Publique el informe de Power BI Desktop en el servicio Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) y ábralo ahí. Los hipervínculos también funcionará en el servicio.

### <a name="for-data-connected-with-directquery"></a>Para los datos conectados con DirectQuery
No podrá crear una nueva columna en el modo DirectQuery.  Pero si los datos ya contienen direcciones URL, puede convertirlas en hipervínculos.

1. En la vista de informe, cree una tabla con un campo que contenga las direcciones URL.
2. Seleccione la columna y, en la pestaña **Modelado**, elija la lista desplegable de **Categoría de datos**.
3. Seleccione **URL web**. Los hipervínculos aparecerán subrayados y de color azul.
4. (Opcional) [Publique el informe de Power BI Desktop en el servicio Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) y ábralo ahí. Los hipervínculos también funcionará en el servicio.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Crear un hipervínculo de tabla o matriz en Power Pivot para Excel
Otra manera de agregar hipervínculos a las tablas y matrices de Power BI es crear los hipervínculos en el conjunto de datos antes de importar o conectarse a ese conjunto de datos desde Power BI. Este ejemplo utiliza un libro de Excel.

1. Abra el libro en Excel.
2. Seleccione la pestaña **PowerPivot** y, a continuación, elija **Administrar**.
   
   ![Abrir PowerPivot en Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Cuando se abra PowerPivot, seleccione la pestaña **Opciones avanzadas**.
   
   ![Pestaña Opciones avanzadas de PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Coloque el cursor en la columna que contiene las direcciones URL que desea convertir en hipervínculos de tablas de Power BI.
   
   > [!NOTE]
   > Las direcciones URL deben comenzar por **http://, https://** o **www**.
   > 
5. En el grupo **Propiedades de informes** , seleccione la lista desplegable **Categoría de datos** y elija **Dirección URL web**. 
   
   ![Lista desplegable de categorías de datos en Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. En el servicio Power BI o Power BI Desktop, conéctese a este libro o impórtelo.
7. Cree una visualización de la tabla que incluya el campo de dirección URL.
   
   ![Crear una tabla en Power BI con el campo de dirección URL](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
P: ¿Puedo usar una dirección URL personalizada como hipervínculo en una tabla o matriz?    
R: No. Puede utilizar un icono de vínculo. Si necesita texto personalizado para los hipervínculos y la lista de direcciones URL es breve, considere la posibilidad de utilizar un cuadro de texto en su lugar.


## <a name="next-steps"></a>Pasos siguientes
[Visualizaciones en informes de Power BI](visuals/power-bi-report-visualizations.md)

[Conceptos básicos para los diseñadores en el servicio Power BI](service-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

