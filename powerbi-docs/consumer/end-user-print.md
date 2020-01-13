---
title: Impresión desde el servicio Power BI
description: Impresión de un panel, un icono o una página de informe desde el servicio Power BI.
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/12/2019
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 5ad3e1f18e6b18116a070d9013bf7cd64d7e1c0f
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "75218064"
---
# <a name="printing-from-the-power-bi-service"></a>Impresión desde el servicio Power BI

## <a name="what-can-be-printed"></a>Qué se puede imprimir
[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Imprima todo un panel, un icono de panel, una página de informe o un objeto visual de informe desde el servicio Power BI. Si el informe tiene más de una página, tendrá que imprimir cada una por separado. 

## <a name="printing-considerations"></a>Consideraciones sobre impresión

La mayoría de los informes y paneles de Power BI los crean los *diseñadores* de informes para usarlos en línea y que tengan un aspecto increíble cuando se muestren en distintos dispositivos. Al imprimir un informe, el explorador controla cómo se muestra ese contenido en papel. 

Se pueden usar opciones del explorador para ajustar la copia impresa, pero incluso al usarlas es posible que no obtenga el resultado deseado. Considere primero la posibilidad de [exportar a PDF](end-user-pdf.md) e imprimir el PDF en su lugar. 

## <a name="adjust-your-browser-print-settings"></a>Ajuste de la configuración de impresión del explorador
Al imprimir desde Power BI, el explorador abre una ventana de impresión. La ventana de impresión de cada explorador es diferente del resto. Pero verá que todas tienen opciones similares que puede usar para controlar el aspecto de la copia impresa. 

A continuación se muestran algunas recomendaciones rápidas que puede usar para dar formato a la copia impresa.

   > 
1. Si el panel, informe u objeto visual es más ancho que alto, considere la posibilidad de usar el diseño **Horizontal**. 

   ![Cuadro de diálogo Imprimir en el que se muestra el diseño como Horizontal](./media/end-user-print/power-bi-landscape-layout.png)

2. Para ajustar más contenido en una página impresa, ajuste elementos como los márgenes y la escala. 

    ![Cuadro de diálogo Imprimir en el que se muestran más opciones](./media/end-user-print/power-bi-margins.png)

Experimente con la configuración del explorador hasta que obtenga el aspecto que le guste. Algunos exploradores incluso tienen opciones para imprimir gráficos de fondo. 

## <a name="print-a-dashboard"></a>Imprimir un panel
1. Abra el panel que quiere imprimir.
2. En la esquina superior izquierda, seleccione Exportar y luego **Imprimir esta página**.
   
    ![Opción de impresión de panel](./media/end-user-print/power-bi-dashboard-print.png)

3. Se abre la ventana de impresión del explorador. Elija la configuración. Por ejemplo, si el panel es más ancho que largo, puede que le interese cambiar el diseño a **Horizontal**. Seleccione **Imprimir**.
   
    ![Cuadro de diálogo de impresión](./media/end-user-print/power-bi-print-dash.png)

## <a name="print-a-dashboard-tile"></a>Imprimir un icono de panel
1. Abra el panel en [modo de pantalla completa](end-user-focus.md) al seleccionar el icono de pantalla completa ![icono de pantalla completa](./media/end-user-print/power-bi-full-screen.png) en la barra de menús superior.

3. [Abra el icono en modo de enfoque](end-user-focus.md); para ello, mantenga el puntero hasta que aparezca **Más opciones** (...) y seleccione **Abrir en modo de enfoque** o el icono de enfoque ![Icono de enfoque](./media/end-user-print/power-bi-focus-icon.png).
   
    ![Menú del botón de puntos suspensivos](./media/end-user-print/power-bi-menu-options.png)

4. Mantenga el mouse sobre el icono para que se muestren las opciones de menú.
   
    ![Menú de opciones de pantalla completa](./media/end-user-print/menu-options-new.png)

4. Seleccione el icono de impresión. ![Icono de impresión](./media/end-user-print/print-icon.png).     

5. Se abre la ventana de impresión del explorador. Elija la configuración. Por ejemplo, si el icono no está ajustado en la página, puede que le interese cambiar la escala a 75 %. Seleccione **Imprimir**.

    ![Ventana de impresión](./media/end-user-print/power-bi-scale.png) 

> [!TIP]
> Si ha seguido todos estos pasos y el icono todavía no se muestra de la forma deseada, pruebe lo siguiente.
> 1. Abra la ventana de impresión y realice los cambios en la configuración de impresión que cree que darán como resultado la mejor impresión. Por ejemplo, cambie el diseño, los márgenes y la escala. 
> 2. Pero, en lugar de imprimir, seleccione **Cancelar**. 
> 3. Vuelva a realizar los pasos del 1-5. El icono se ajustará a la nueva configuración de la ventana de impresión y estará listo para imprimirse.

## <a name="print-a-report-page"></a>Imprimir una página de un informe
Los informes se pueden imprimir una página a la vez.

1. Abra el informe y seleccione **Exportar** > **Imprimir** para imprimir la página actual del informe.
   
    ![Menú Archivo de Power BI](./media/end-user-print/power-bi-report-print.png)
2. Se abre la ventana de impresión del explorador.

3. Siga los pasos anteriores de impresión en **Impresión de un panel**.
   


## <a name="print-a-report-visual"></a>Imprimir un objeto visual de informe
1. [Abra el objeto visual en modo de enfoque](end-user-focus.md) al mantener el puntero sobre el icono y seleccionar el icono de enfoque ![icono de enfoque](./media/end-user-print/power-bi-focus-icon.png) en la esquina superior derecha.

2. En la esquina superior izquierda, seleccione **Exportar** > **Imprimir** para imprimir el objeto visual.

    ![Menú Archivo de Power BI](./media/end-user-print/power-bi-report-print.png)


3. Siga los pasos anteriores de impresión en **Impresión de un panel**.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

* P: No puedo imprimir todas las páginas de un informe a la vez.    
* R: Así es. Las páginas de informes solo se pueden imprimir una a la vez.
* P: No puedo imprimir a un archivo PDF.    
* R: Solo verá esta opción si tiene configurado el controlador PDF del explorador.    
* P: Lo que veo cuando selecciono **Imprimir** no es lo que me muestran aquí.    
* R: Las pantallas de impresión varían en función del explorador y la versión de software.
* P: Mi copia impresa no tiene una escala correcta.  El panel no se ajusta a la página. Otras preguntas sobre escala y orientación.    
* R: No se puede garantizar que la copia impresa sea idéntica a lo que aparece en el servicio Power BI. Power BI no controla aspectos como la escala, los márgenes, los detalles de los objetos visuales, la orientación ni el tamaño. Intente ajustar las opciones de impresión del explorador. Algunas de las que se han sugerido antes son la orientación de la página (horizontal o vertical), el tamaño del margen y la escala. Si no le sirven de ayuda, consulte la documentación correspondiente al explorador específico.      
* P: Al imprimir desde el modo de pantalla completa, no veo la opción de impresión al mantener el mouse sobre el objeto visual.   
* R: Vuelva al panel o informe en la vista predeterminada, abra de nuevo el objeto visual en modo de enfoque y, después, en modo de pantalla completa. 

## <a name="next-steps"></a>Pasos siguientes
[Uso compartido de paneles e informes con compañeros y otros usuarios](../service-share-dashboards.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

