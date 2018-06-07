---
title: Formato de tabla condicional en Power BI Desktop
description: Aplicar formato personalizado a las tablas
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 70aa61d6a02bea1b7058a68b20718008ace1b8c8
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34480897"
---
# <a name="conditional-formatting-in-tables"></a>Formato condicional en tablas 
Con el formato condicional de tablas, se pueden especificar colores personalizados de las celdas en función de los valores de esas celdas o de otros valores o campos, usando incluso colores de degradado. También puede mostrar valores de celda con barras de datos. 

Para acceder al formato condicional, en el área **Campos** del panel **Visualizaciones** de Power BI Desktop, seleccione la flecha hacia abajo que está situada junto al valor del área **Valores** que desea formatear (o haga clic con el botón derecho en el campo). El formato condicional solo se puede administrar en el área **Valores** de **Campos**.

![Menú de formato condicional](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

En estas secciones se describen cada una de estas tres opciones de formato condicional. Una o varias opciones pueden combinarse en una sola columna de tabla.

> [!NOTE]
> Cuando se aplica a una tabla, el formato condicional reemplaza cualquier estilo de tabla personalizada aplicado a las celdas con formato condicional.

Para quitar el formato condicional de una visualización, simplemente vuelva a hacer clic con el botón derecho en el campo, seleccione **Quitar formato condicional** y elija el tipo de formato que va a quitar.

![Menú Quitar formato condicional](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

## <a name="background-color-scales"></a>Escalas de color de fondo

Seleccione **Formato condicional** y **Escalas de color de fondo**. Se abrirá el cuadro de diálogo siguiente.

![Cuadro de diálogo Escalas de color de fondo](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

Puede seleccionar un campo en el modelo de datos en el que basar los colores, estableciendo **Color based on** (Color basado en) en ese campo. Además, puede especificar el tipo de agregación para el campo seleccionado con el valor **Resumen**. El campo que se coloreará se especifica en el campo **Apply color to** (Aplicar color a), para que pueda realizar un seguimiento. Se puede aplicar formato condicional a los campos de texto y de fecha, siempre y cuando se elija un valor numérico como base del formato.

![Campo Color based on (Color basado en)](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Para usar valores de colores discretos para determinados intervalos de valor, seleccione **Color by rules** (Color por reglas). Para usar un espectro de colores, deje **Color by rules** (Color por reglas) desactivado. 

![Cuadro de diálogo Escalas de color de fondo](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

### <a name="color-by-rules"></a>Color según las reglas

Cuando selecciona **Color by rules** (Color por reglas), puede especificar uno o varios intervalos de valor, cada uno con un conjunto de colores.  Cada intervalo de valor empieza por una condición de valor *Si* y una condición de valor *Y*, y un color.

![Intervalo de valor Color por reglas](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Las celdas de la tabla con valores en cada intervalo se rellenan con el color especificado. Hay tres reglas en esta imagen.

![Ejemplo de Color por reglas](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules.png)

La tabla de ejemplo se parece a esta:

![Tabla de ejemplo con color por reglas](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)


### <a name="color-minimum-to-maximum"></a>Color mínimo a máximo

Puede configurar los valores *Mínimo* y *Máximo* y sus colores. Si selecciona el cuadro **Diverging**, puede configurar un valor *Centro* opcional.

![Botón divergente](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

La tabla de ejemplo se parece a esta:

![Tabla de ejemplo con colores divergentes](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

## <a name="font-color-scales"></a>Escalas de color de fuente

Al seleccionar **Formato condicional** y **Escalas de color de fuente**, se abre este cuadro de diálogo. Este cuadro de diálogo es similar a **Escalas de color de fondo**, pero cambia el color de la fuente en lugar del color de fondo de la celda.

![Cuadro de diálogo Escalas de color de fuente](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

La tabla de ejemplo se parece a esta:

![Tabla de ejemplo con escalas de color de fuente](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="data-bars"></a>Barras de datos

Al seleccionar **Formato condicional** y **Barras de datos**, se abre este cuadro de diálogo. 

![Cuadro de diálogo Barras de datos](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

De forma predeterminada, la opción **Show bar only** (Mostrar solo la barra) está desactivada, por lo que la celda de tabla muestra la barra y el valor real.

![Tabla de ejemplo con barras de datos y valores](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

Si la opción **Show bar only** (Mostrar solo la barra) está activada, la celda de tabla solo muestra la barra.

![Tabla de ejemplo con solo barras de datos](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)
