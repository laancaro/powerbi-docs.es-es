---
title: Introducción al formato de las visualizaciones de los informes
description: Introducción al uso de las opciones de formato con las visualizaciones de los informes
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2433f030f00ec8cd337d97c4402b83ed6c4c5a00
ms.sourcegitcommit: 64a270362c60581a385af7fbc31394e3ebcaca41
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "76895240"
---
# <a name="getting-started-with-the-formatting-pane"></a>Introducción al panel de formato
Si tiene permisos de edición para un informe, hay numerosas opciones de formato disponibles. En los informes de Power BI, puede cambiar el color de la serie de datos, los puntos de datos e incluso el fondo de las visualizaciones. Puede cambiar la presentación de los ejes X e Y. Incluso puede aplicar formato a las propiedades de fuente de visualizaciones, formas y títulos. Power BI proporciona control total sobre el modo en que aparecen los informes.

Para empezar, abra un informe en Power BI Desktop o en el servicio Power BI. En ambos casos se proporcionan opciones de formato prácticamente idénticas. Al abrir un informe en el servicio Power BI, asegúrese de seleccionar **Editar** en la barra de menús. 

![Barra de menús con la opción Editar](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-edit.png)

Cuando vaya a editar un informe y tenga una visualización seleccionada, aparece el panel **Visualizaciones**. Use este panel para cambiar las visualizaciones. Justo debajo del panel **Visualizaciones** hay tres iconos: el icono **Campos** (una pila de barras), el icono **Formato** (un rodillo de pintura) y el icono **Análisis** (una lupa). En la imagen siguiente, el icono **Campos** está seleccionado, lo que se indica con una barra amarilla debajo.

![](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-format.png)

Al seleccionar **Formato**, el área debajo del icono muestra las personalizaciones disponibles para la visualización seleccionada.  

![](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-format-selected.png)

Puede personalizar muchos elementos de cada visualización: Las opciones disponibles dependen del objeto visual seleccionado. Algunas de estas opciones son:

* Leyenda
* Eje X
* Eje Y
* Colores de datos
* Etiquetas de datos
* Formas
* Área de trazado
* Título
* Fondo
* Aspecto de bloqueo
* Borde
* Información sobre herramientas
* Encabezados de objetos visuales
* Formas
* Posición    
Y mucho más...


> [!NOTE]
>  
> No verá todos estos elementos con cada tipo de visualización. La visualización que seleccione afectará a las personalizaciones disponibles; por ejemplo, no verá un eje X si está seleccionado un gráfico circular porque los gráficos circulares no tienen eje X.

Tenga en cuenta también que si no tiene ninguna visualización seleccionada, **Filtros** aparece en lugar de los iconos, que le permite aplicar filtros a todas las visualizaciones de la página.

La mejor manera de aprender a usar las opciones de formato es probarlas. Siempre puede deshacer los cambios o volver al valor predeterminado. Hay una cantidad increíble de opciones disponibles y siempre se están agregando otras nuevas. No es posible describir todas las opciones de formato en un artículo. Pero para comenzar, vamos a revisar algunas aquí. 

1. Cambiar los colores usados en el objeto visual   
2. Aplicar un estilo    
3. Cambiar las propiedades del eje    
4. Agregar etiquetas de datos    




## <a name="working-with-colors"></a>Trabajo con colores

Vamos a ver los pasos necesarios para personalizar los colores de una visualización.

1. Seleccione una visualización para activarla.

2. Seleccione el icono de rodillo de pintura para abrir la pestaña Formato. La pestaña Formato muestra todos los elementos de formato disponibles para el elemento visual seleccionado.

    ![Gráfico con la pestaña del panel Formato seleccionada](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-formatting.png)

3. Seleccione **Colores de datos** para expandir sus personalizaciones disponibles.  

    ![Gráfico con el panel Formato abierto y los colores de datos expandidos](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-data-colors.png)

4. Cambie **Mostrar todo** a Activado y seleccione colores diferentes para las columnas.

    ![Gráfico con nuevos colores aplicados a algunas columnas](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-change-colors.png)

Estas son algunas sugerencias útiles para trabajar con colores. Los números de la lista siguiente se muestran también en la pantalla siguiente, lo que indica que se puede acceder o cambiar estos elementos útiles.

1. ¿No está satisfecho con los colores? Ningún problema, simplemente seleccione **Volver al valor predeterminado** y la selección vuelve a la configuración predeterminada. 

2. ¿No le gusta ninguno de los cambios de color? Seleccione **Volver al valor predeterminado** en la parte inferior de la sección **Color de datos** y los colores vuelven a la configuración predeterminada. 

3. ¿Desea un color que no aparece en la paleta? Simplemente seleccione **Color personalizado**y elija uno en el espectro.  

   ![Sección de color de datos con la paleta de colores abierta](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-color-extras.png)

¿No está del todo contento con el cambio que acaba de crear? Use **CTRL+Z** para deshacerlo, de la manera habitual.

## <a name="applying-a-style-to-a-table"></a>Aplicación de un estilo a una tabla
Algunas visualizaciones de Power BI tienen una opción **Estilo**. Con un solo clic, se aplica un conjunto completo de opciones de formato a la visualización, todas a la vez. 

1. Seleccione una tabla o una matriz para activarla.   
1. Abra la pestaña Formato y seleccione **Estilo**.

   ![Selección de Estilo en la pestaña Formato](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-style.png)


1. Seleccione un estilo de la lista desplegable. 

   ![Misma tabla con la opción Filas llamativas del encabezado en negrita aplicada](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-style-flashy.png)

Incluso después de aplicar un estilo, puede seguir dando formato a las propiedades, incluido el color, de esa visualización.


## <a name="changing-axis-properties"></a>Cambio de las propiedades del eje

A menudo, resulta útil modificar el eje X o el eje Y. De igual forma que al trabajar con colores, puede modificar un eje seleccionando el icono de flecha abajo, situado a la izquierda del eje que quiere cambiar, tal como se muestra en la siguiente imagen.  
![](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-y-axis.png)

En el ejemplo siguiente, hemos aplicado formato al eje Y de esta manera:
- se han movido las etiquetas al lado derecho de la visualización.

- se ha cambiado el valor inicial a cero.

- se ha cambiado el color de fuente de la etiqueta a negro.

- se ha aumentado el tamaño de fuente de la etiqueta a 12.

- se ha agregado un título al eje Y


    ![mismo gráfico de columnas pero con gran cantidad de formato del eje Y](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-axis-changes.png)

Puede quitar totalmente las etiquetas de eje, alternando el botón de radio junto a **Eje X** o **Eje Y**. También puede elegir si se deben activar o desactivar los títulos de eje mediante la selección del botón de radio junto a **Título**.  



## <a name="adding-data-labels"></a>Adición de etiquetas de datos    

Un último ejemplo de formato antes de empezar a explorar por su cuenta.  Vamos a agregar etiquetas de datos a un gráfico de áreas. 

Este es la imagen de *antes*. 

![gráfico de áreas sin formato](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-area-chart.png)


Y esta es la imagen de *después*.

![gráfico de áreas con formato](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-data-labels.png)

Hemos seleccionado la visualización para activarla y abrir la pestaña Formato.  Hemos seleccionado **Etiquetas de datos** y las hemos activado. Luego, hemos aumentado la fuente a 12, hemos cambiado la familia de fuentes a Arial Black, hemos activado **Mostrar fondo** y hemos seleccionado un color de fondo blanco con una transparencia del 5 %.

Estas son solo algunas de las tareas de formato posibles. Abra un informe en el modo de edición y diviértase explorando el panel de formato para crear visualizaciones atractivas e informativas.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información, consulte el artículo siguiente:  

* [Sugerencias y trucos para el formato de color en Power BI](service-tips-and-tricks-for-color-formatting.md)  
* [Formato condicional en tablas](../desktop-conditional-table-formatting.md)

