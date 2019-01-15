---
title: Cambio del tamaño de presentación y la proporción de una página de informe
description: Cambiar la configuración de presentación de una página en un informe de Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 075751a95512a7d06e22eb104aacf056978a93ea
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275787"
---
# <a name="change-the-size-of-a-report-page"></a>Cambiar el tamaño de una página del informe
En el [artículo y el vídeo anteriores](../power-bi-report-display-settings.md), conoció las dos maneras distintas de controlar la presentación de una página en los informes de Power BI: **Vista** y **Tamaño de página**. La vista de página y el tamaño de página están disponibles en el servicio Power BI y en Power BI Desktop y tienen una apariencia y comportamiento similar, pero en este tutorial vamos a utilizar el servicio Power BI.

### <a name="prerequisites"></a>Requisitos previos
- Servicio Power BI   
- [Informe del Ejemplo de análisis de minoristas](../sample-retail-analysis.md)

## <a name="first-lets-change-the-page-view-setting"></a>En primer lugar, vamos a cambiar la configuración de la vista de página

1. Abra el informe en la vista de lectura o la vista de edición y seleccione la pestaña del informe **Nuevas tiendas**. De forma predeterminada, esta página del informe se muestra con la configuración **Ajustar a la página**.  En este caso, la configuración Ajustar a la página muestra la página del informe sin barras de desplazamiento, pero no se pueden leer algunos de los detalles y títulos porque son demasiado pequeños.

   ![informe mostrado en el lienzo](media/end-user-report-view/pbi_fit_to_page.png)
2. Asegúrese de que no haya ninguna visualización seleccionada en el lienzo. Seleccione **Vista** y revise las opciones de presentación.

   * En la vista de lectura verá esto.

     ![Menú desplegable Vista con Ajustar a la página seleccionado](media/end-user-report-view/power-bi-page-view-menu-new.png)
   * En la vista de edición verá esto.

     ![Menú desplegable Vista con Ajustar a la página seleccionado](media/end-user-report-view/power-bi-view-editing-view.png)

3. Veamos cómo se muestra la página con la opción **Tamaño real**.

   ![el informe se muestra en el lienzo, con dos barras de desplazamiento](media/end-user-report-view/power-bi-actal-size2.png)

   No se ve muy bien, ya que ahora el panel tiene barras de desplazamiento dobles.
4. Cambie a **Ajustar al ancho**.

   ![el informe se muestra sin barras de desplazamiento, solo una barra de desplazamiento](media/end-user-report-view/pbi_fit_to_width.png)

   Tiene un mejor aspecto, aún tenemos una barra de desplazamiento, pero es más fácil leer los detalles.

## <a name="change-the-default-view-for-a-report-page"></a>Cambiar la vista predeterminada de una página de informe
Si es un *creador* del informe, puede cambiar la vista predeterminada de las páginas del informe. Al compartir el informe con otros usuarios, las páginas del informe se abrirán con la vista que ha establecido. Los *consumidores* del informe podrán cambiar la vista, pero no podrán guardar los cambios realizados después de salir del informe.

1. En la página **New stores** del informe, cambie a la vista **Tamaño real**.

   ![Menú desplegable Vista con Tamaño real seleccionado](media/end-user-report-view/power-bi-actual-size.png)

2. En la página del informe **Ventas mensuales del distrito**, establezca la vista en **Ajustar al ancho**.

3. En la página del informe **Información general**, deje la configuración de vista predeterminada.

4. Ahora, guarde el informe seleccionando **Archivo > Guardar**. La próxima vez que abra este informe, las páginas se mostrarán con las nuevas opciones de vista. Vamos a verlo.

   ![Menú desplegable Archivo con Guardar seleccionado](media/end-user-report-view/power-bi-save.png)
3. Seleccione el nombre del área de trabajo actual en la barra de navegación superior para volver a esa área de trabajo.  

   ![Barra de menús superior, que muestra las rutas de navegación](media/end-user-report-view/power-bi-my-workspace.png)
4. Seleccione la pestaña **Informes** y elija el mismo informe (Ejemplo de análisis de minoristas).

    ![Vista Contenido con la pestaña Informes seleccionada](media/end-user-report-view/power-bi-new-report2.png)
5. Abra cada página del informe para ver la nueva configuración.

   ![vídeo que muestra cómo cambiar las opciones de Vista](media/end-user-report-view/power-bi-page-view.gif)

## <a name="now-lets-explore-the-page-size-setting"></a>Ahora, vamos a explorar la configuración del *tamaño de página*
Los valores de tamaño de página solo están disponibles en la [vista de edición](../service-interact-with-a-report-in-editing-view.md), por lo que debe tener permisos de edición (*creador*) en el informe para cambiar los valores de tamaño de página. Si se conectó a cualquiera de nuestros [ejemplos](../sample-datasets.md), tendrá permisos de *creador* en esos informes.

1. Abra la página "District monthly sales" del [Ejemplo de análisis de venta directa](../sample-retail-analysis.md) en la vista de edición.
2. Asegúrese de que no haya ninguna visualización seleccionada en el lienzo.  En el panel **Visualizaciones**, seleccione el icono del rodillo de pintura ![](media/end-user-report-view/power-bi-paintroller.png).
3. Seleccione **Tamaño de página** &gt; **Tipo** para mostrar las opciones de tamaño de página.

   ![Tarjeta de Tamaño de página expandida y 16:9 seleccionado](media/end-user-report-view/power-bi-page-size-menu-new.png)
4. Seleccione **Carta**.  En el lienzo, solo el contenido que se ajusta a 816 x 1056 píxeles (tamaño Carta) permanece en la parte en blanco del lienzo.

   ![Lienzo de informe con tarjeta de Tamaño de página expandida y Tipo > Carta seleccionado](media/end-user-report-view/power-bi-letter-new.png)
5. Seleccione **Tamaño de página** relación **16:9**.

   ![Tarjeta de Tamaño de página expandido y Tipo > 16:9 seleccionado](media/end-user-report-view/power-bi-16-to-9-new.png)

   La página del informe se muestra con una relación de 16 de ancho por 9 de alto. Para ver el tamaño real en píxeles que se usa, mire los campos Ancho y Alto (1280x720), que aparecen atenuados. Hay mucho espacio vacío alrededor del lienzo del informe; esto se debe a que antes establecimos **Vista** en "Ajustar al ancho".
7. Continúe explorando las opciones de **Tamaño de página**.

## <a name="use-page-view-and-page-size-together"></a>Uso de Vista de página y Tamaño de página conjuntamente
Use la vista de página y el tamaño de página conjuntamente para crear un informe que tenga un aspecto óptimo al ser compartido con los compañeros o insertado en otra aplicación.

En este ejercicio, creará una página de informe que se mostrará en una aplicación que tenga espacio para 500 píxeles de ancho por 750 píxeles de alto.

Recuerde que, en el paso anterior, vimos que nuestra página de informe se muestra en 1280 píxeles de ancho por 720 píxeles de alto. Así pues, sabemos que tendremos que cambiar bastante el tamaño y la organización para que quepan todos nuestros gráficos.

1. Cambie el tamaño de los objetos visuales y muévalos para que quepan en menos de la mitad del área de lienzo actual.

    ![vídeo que muestra cómo se cambian de tamaño los objetos visuales y cómo se mueven por el lienzo](media/end-user-report-view/power-bi-custom-view.gif)
2. Seleccione **Tamaño de página** &gt; **Personalizado**.
3. Establezca el ancho en 500 y el alto en 750.

    ![Panel Formato con la tarjeta Tamaño de página expandida](media/end-user-report-view/power-bi-custom-new.png)
4. Retoque la página de informe para que tenga un aspecto óptimo. Cambie entre **Vista > Tamaño real** y **Vista > Ajustar a la página** para realizar ajustes.

    ![Lienzo de informe con panel Formato expandido](media/end-user-report-view/power-bi-final-new.png)

## <a name="next-steps"></a>Pasos siguientes
[Crear informes para Cortana](../service-cortana-answer-cards.md)

Vuelva a [Configuración de presentación de página en un informe de Power BI](../power-bi-report-display-settings.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
