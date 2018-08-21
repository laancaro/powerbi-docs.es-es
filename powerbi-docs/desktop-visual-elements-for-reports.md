---
title: Uso de elementos visuales para mejorar los informes de Power BI
description: Uso de elementos visuales como papel tapiz y encabezados visuales para mejorar los informes
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a3e39e6326eb5b32cd72e2aefec74c07804b4639
ms.sourcegitcommit: cce10e14c111e8a19f282ad6c032d802ebfec943
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39657906"
---
# <a name="use-visual-elements-to-enhance-power-bi-reports"></a>Uso de elementos visuales para mejorar los informes de Power BI

Con **Power BI Desktop** puede usar elementos visuales, como papel tapiz y encabezados visuales mejorados para las visualizaciones con el fin de mejorar la apariencia de los informes.

![Agregar papel tapiz y pequeños encabezados visuales para mejorar los informes](media/desktop-visual-elements-for-reports/visual-elements-for-reports_01.png)

A partir de la versión de **Power BI Desktop** de julio de 2018, puede agregar mejoras para usarlas en los informes y hacer que sus análisis e informes sean incluso más atractivos que antes. Las mejoras que se describen en este artículo incluyen las siguientes: 

* Aplicar **papel tapiz** a los informes para que el fondo pueda mejorar o resaltar los elementos de la historia que quiere contar con los datos.
* Usar **encabezados visuales** mejorados para visualizaciones individuales con el fin de crear objetos visuales perfectamente alineados en el lienzo del informe. 

En las secciones siguientes se describe cómo usar estas mejoras y cómo aplicarlas a los informes.

## <a name="using-wallpaper-in-power-bi-reports"></a>Uso de papel tapiz en los informes de Power BI

Puede usar el **papel tapiz** para dar formato al área gris fuera de la página del informe. En la imagen siguiente, una flecha indica claramente dónde se aplica el área del papel tapiz. 

![El papel tapiz cubre el área gris alrededor de un informe](media/desktop-visual-elements-for-reports/visual-elements-for-reports_02.png)

Puede establecer el papel tapiz por página del informe, o bien puede tener el mismo papel tapiz para cada página del informe. Para establecer el papel tapiz, pulse o haga clic en el icono **Formato** cuando no haya ningún objeto visual seleccionado en el informe y aparecerá la tarjeta **Papel tapiz** en el panel.

![Área del papel tapiz en el panel Formato](media/desktop-visual-elements-for-reports/visual-elements-for-reports_03.png)

Puede elegir aplicar un color como **papel tapiz** si selecciona el menú desplegable **Color**, o bien puede seleccionar el botón **Add Image** (Agregar imagen) para seleccionar una imagen que aplicar como papel tapiz. También puede aplicar transparencia al papel tapiz, ya sea que se trate de un color o una imagen, con el control deslizante **Transparency** (Transparencia).

Resulta útil tener en cuenta las siguientes definiciones que se refieren al **papel tapiz**:

* El área gris fuera del área del informe es el área del **papel tapiz**
* El área del lienzo donde puede colocar objetos visuales se conoce como la **página** del informe y se puede modificar en el **panel de formato** mediante la lista desplegable **Page background** (Fondo de página).

La **página** del informe siempre está en primer plano (en comparación con el papel tapiz), mientras que el **papel tapiz** está detrás y es el elemento que está más al fondo de la pagina del informe. Cuando aplica transparencia a la página, también se aplica a los objetos visuales del informe, lo que permite que el papel tapiz esté visible en el fondo a través de los objetos visuales.

Estos son los valores predeterminados para todos los informes nuevos:

* La **página** del informe está establecida en **blanco** y su transparencia, en **100 %**
* El **papel tapiz** está establecido en **blanco** y su transparencia, en **0 %**

Al establecer el fondo de la página en una transparencia superior al 50 %, aparece un borde punteado mientras crea o edita el informe para mostrar el límite del borde del lienzo del informe. 

![Una transparencia superior al 50 % genera un borde punteado](media/desktop-visual-elements-for-reports/visual-elements-for-reports_04.png)

Es importante tener en cuenta que el límite punteado *solo* aparece al editar el informe y *no* es visible para quienes ven el informe publicado, como cuando se ve en el **servicio Power BI**.

> [!NOTE]
> Si usa fondos de colores oscuros para el papel tapiz y establece el color del texto en blanco o muy claro, tenga en cuenta que la característica **Exportar a PDF** no incluye el papel tapiz, por lo que las exportaciones con fuentes de color blanco serán casi invisibles en el archivo PDF exportado. Vea [Export to PDF](desktop-export-to-pdf.md) (Exportar a PDF) para obtener más información sobre **Exportar a PDF**.


## <a name="using-improved-visual-headers-in-power-bi-reports"></a>Uso de encabezados visuales mejorados en los informes de Power BI

A partir de la versión de **Power BI Desktop** de julio de 2018, los encabezados de los objetos visuales en los informes mejoraron de manera considerable. Las mejoras principales son que el encabezado se separó del objeto visual, por lo que se puede ajustar su posición según su preferencia de diseño y posicionamiento, y que el encabezado ahora aparece dentro del objeto visual mismo en lugar de flotar sobre él. 

De manera predeterminada, el encabezado aparece dentro del objeto visual alineado con el título. En la imagen siguiente, puede ver el encabezado (el icono de anclaje, el icono de expansión y el icono de puntos suspensivos) dentro del objeto visual y alineado a la derecha, junto con la misma posición horizontal que tiene el título del objeto visual.

![Los encabezados visuales ahora pueden residir dentro de un objeto visual o se pueden mover](media/desktop-visual-elements-for-reports/visual-elements-for-reports_05.png)

Si el objeto visual no tiene título, el encabezado flota sobre la parte superior del objeto visual alineado a la derecha, tal como se muestra en la imagen siguiente. 

![Los encabezados visuales flotan sobre los objetos visuales si no hay título](media/desktop-visual-elements-for-reports/visual-elements-for-reports_07.png)

Si el objeto visual está posicionado en la parte superior del informe, el encabezado visual se ajusta a la parte inferior del objeto visual. 

![Los encabezados visuales se ajustan a la parte inferior cuando se bordea la parte superior del informe](media/desktop-visual-elements-for-reports/visual-elements-for-reports_08.png)

Cada objeto visual también tiene una tarjeta en la sección **Formato** del panel **Visualizaciones** que se denomina **Encabezado visual**. En esa tarjeta puede ajustar todo tipo de características del encabezado visual

![Cada objeto visual tiene una tarjeta de encabezado visual en el panel Formato](media/desktop-visual-elements-for-reports/visual-elements-for-reports_09.png)

> [!NOTE]
> La visibilidad de las alternancias no afecta el informe cuando lo crea o edita. Debe publicar el informe y verlo en el modo de lectura para ver el efecto. Este comportamiento garantiza que las numerosas opciones que se proporcionan en los encabezados visuales son importantes durante la edición, especialmente los iconos de advertencia que alertan sobre problemas al editar.

En el caso de los informes que solo aparecen en el **servicio Power BI**, puede ajustar el uso de los encabezados visuales si va a **Mi área de trabajo > Informes** y luego selecciona el icono **Configuración**. Ahí verá la configuración del informe para el cual seleccionó la opción **Configuración** y podrá ajustar esa configuración desde ahí, como se muestra en la imagen siguiente.

![Configuración del servicio Power BI para usar los encabezados visuales mejorados](media/desktop-visual-elements-for-reports/visual-elements-for-reports_10.png)

### <a name="enabling-improved-visual-headers-for-existing-reports"></a>Habilitación de los encabezados visuales mejorados para los informes existentes

El encabezado visual nuevo es el comportamiento predeterminado de todos los informes nuevos. En el caso de los informes existentes, debe habilitar este comportamiento en **Power BI Desktop** si va a **Archivo > Opciones y configuración > Opciones** y luego en la sección **Configuración de informes**, activa la casilla de verificación **Use the modern visual header with updated styling options** (Usar el encabezado visual moderno con opciones de estilo actualizadas).

![Los informes existentes deben activar la casilla de verificación Opciones para usar los encabezados visuales mejorados](media/desktop-visual-elements-for-reports/visual-elements-for-reports_06.png)


## <a name="next-steps"></a>Pasos siguientes
Para más información acerca de **Power BI Desktop** y cómo empezar a trabajar, consulte los siguientes artículos.

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Conectarse a los datos en Power BI Desktop](desktop-connect-to-data.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)   

