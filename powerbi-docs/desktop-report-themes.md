---
title: Uso de los temas para los informes en Power BI Desktop
description: Aprenda a usar una paleta de colores personalizada y a aplicarla a un informe completo en Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5a4ed3ffc833b2405a3c231b80047c71b40a64cc
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753706"
---
# <a name="use-report-themes-in-power-bi-desktop"></a>Uso de los temas para los informes en Power BI Desktop

Con los *temas para informes* de Power BI Desktop puede aplicar cambios de diseño a todo el informe; por ejemplo, usar colores corporativos, cambiar conjuntos de iconos o aplicar nuevos formatos visuales predeterminados. Al aplicar un tema para informes, todos los objetos visuales del informe usan los colores y el formato del tema seleccionado. Hay algunas excepciones que se describen más adelante en este artículo.

![Temas de informes](media/desktop-report-themes/report-themes-1a.png)

Hay dos tipos de temas para informes: los que vienen integrados y los personalizados.

- Los temas para informes integrados proporcionan diferentes tipos de esquemas de colores predefinidos que se instalan con Power BI Desktop. Estos se seleccionan directamente desde el menú de Power BI Desktop.

- Los archivos de temas para informes personalizados se crean en archivos JSON que definen su estructura básica. Para aplicar un tema para informes personalizado, importe su archivo JSON en Power BI Desktop y aplíquelo al informe.

  También puede personalizar un tema para informes existente desde Power BI Desktop con el [cuadro de diálogo **Personalización del tema**](#create-and-customize-a-theme-in-power-bi-desktop-preview).

Puede personalizar y normalizar casi todos los elementos que se enumeran en la sección **Formato** del panel **Visualizaciones**, ya sea a través de las personalizaciones realizadas directamente en Power BI Desktop o a través de un archivo JSON de temas para informes. El objetivo es ofrecer el control total de la apariencia y el comportamiento de los informes a un nivel pormenorizado.

## <a name="how-report-themes-work"></a>Funcionamiento de los temas para informes

Para aplicar un tema para informes a un informe de Power BI Desktop, puede seleccionar entre los [temas para informes integrados disponibles](#built-in-report-themes), puede [importar un archivo JSON de temas personalizado](#import-custom-report-theme-files) o puede [usar el cuadro de diálogo **Personalización del tema**](#create-and-customize-a-theme-in-power-bi-desktop-preview).

Para obtener información detallada sobre los valores predeterminados que se pueden personalizar, consulte la sección siguiente sobre el [formato JSON de temas para informes](#report-theme-json-file-format).

### <a name="built-in-report-themes"></a>Temas para informes integrados

Para seleccionar los temas para informes integrados que hay disponibles:

1. Seleccione **Cambiar tema** en la cinta de opciones **Inicio**.

   ![Seleccionar un tema de informe](media/desktop-report-themes/report-themes-2a.png)

2. Seleccione uno de los temas incluidos en el menú desplegable.

   El tema para informes está ahora aplicado al informe.

En la tabla siguiente se muestran los temas para informes integrados disponibles.

| Tema para informes integrado | Secuencia de color predeterminada |
|------ |---------- |
| Predeterminado | ![Predeterminado](media/desktop-report-themes/report-themes-color-scheme-default.png)|
| Rascacielos | ![Rascacielos](media/desktop-report-themes/report-themes-color-scheme-highrise.png)|
| Ejecutivo | ![Ejecutivo](media/desktop-report-themes/report-themes-color-scheme-executive.png)|
| Frontera| ![Frontera](media/desktop-report-themes/report-themes-color-scheme-frontier.png)|
| Innovación | ![Innovación](media/desktop-report-themes/report-themes-color-scheme-innovative.png)|
| Eclosión | ![Eclosión](media/desktop-report-themes/report-themes-color-scheme-bloom.png)|
| Corriente| ![Corriente](media/desktop-report-themes/report-themes-color-scheme-tidal.png)|
| Temperatura | ![Temperatura](media/desktop-report-themes/report-themes-color-scheme-temperature.png)|
| Solar| ![Solar](media/desktop-report-themes/report-themes-color-scheme-solar.png)|
| Divergente | ![Divergente](media/desktop-report-themes/report-themes-color-scheme-divergent.png)|
| Tormenta | ![Tormenta](media/desktop-report-themes/report-themes-color-scheme-storm.png)|
| Clásico | ![Clásico](media/desktop-report-themes/report-themes-color-scheme-classic.png)|
| Parque | ![Parque](media/desktop-report-themes/report-themes-color-scheme-city-park.png)|
| Clase | ![Clase](media/desktop-report-themes/report-themes-color-scheme-classroom.png)|
| Apto para daltónicos | ![Apto para daltónicos](media/desktop-report-themes/report-themes-color-scheme-colorblind-safe.png)|
| Eléctrico | ![Eléctrico](media/desktop-report-themes/report-themes-color-scheme-electric.png)|
| Contraste alto | ![Contraste alto](media/desktop-report-themes/report-themes-color-scheme-high-contrast.png)|
| Puesta de sol | ![Puesta de sol](media/desktop-report-themes/report-themes-color-scheme-sunset.png)|
| Crepúsculo | ![Crepúsculo](media/desktop-report-themes/report-themes-color-scheme-twilight.png)|

## <a name="customize-report-themes"></a>Personalización de temas para informes

A partir de la versión de diciembre de 2019 de Power BI Desktop, ahora hay dos maneras de personalizar un tema para informes:

- [Creación y personalización de temas en Power BI Desktop (versión preliminar)](#create-and-customize-a-theme-in-power-bi-desktop-preview)
- [Creación y personalización de archivos JSON de temas para informes personalizados](#introduction-to-report-theme-json-files)

### <a name="create-and-customize-a-theme-in-power-bi-desktop-preview"></a>Crear y personalizar un tema en Power BI Desktop (versión preliminar)

A partir de la versión de diciembre de 2019 de Power BI Desktop, la funcionalidad para personalizar un tema directamente en Power BI Desktop ahora está disponible como versión previa.

Para personalizar un tema directamente en Power BI Desktop:

1. Seleccione **Archivo** > **Opciones y configuración** > **Opciones**.

2. En la sección **Características de vista previa**, seleccione **Personalizar tema actual** y, a continuación, seleccione **Aceptar**.

   ![Habilitación de temas personalizados](media/desktop-report-themes/report-themes_5a.png)

   Es posible que se le pida reiniciar Power BI Desktop para habilitar la característica en versión preliminar. Después de reiniciar, puede empezar a personalizar el tema aplicado actualmente.

3. En la cinta de opciones **Inicio**, seleccione **Cambiar tema** > **Personalizar tema actual**.

   Aparece un cuadro de diálogo que muestra las formas de personalizar el tema para informes que se aplica actualmente al informe.

   ![Personalización del tema](media/desktop-report-themes/report-themes_5b.png)

4. Si le gusta un tema existente y quiere realizar algunos ajustes, seleccione (o importe) el tema y, luego, elija **Personalizar tema actual**.

   ![Personalización del tema actual](media/desktop-report-themes/report-themes_5c.png)

Las opciones de tema que se pueden personalizar se encuentran en las categorías siguientes, reflejadas en el cuadro de diálogo **Personalizar tema**:

- **Nombre y colores**: nombre del tema y opciones de colores, entre las que se encuentran [colores del tema](#how-report-theme-colors-stick-with-your-reports), colores de las opiniones, colores divergentes y [colores estructurales (avanzado)](#setting-structural-colors).
- **Texto**: la configuración del texto incluye la familia, el tamaño y el color de fuente, que establece los [valores predeterminados de la clase de texto principal](#setting-formatted-text-defaults) para las etiquetas, los títulos, las tarjetas y KPI, y los encabezados de las pestañas.
- **Objetos visuales**: entre las opciones de objetos visuales se encuentran el fondo, el borde, el encabezado y la información sobre herramientas.
- **Página**: opciones de elementos de página, como el papel tapiz y el fondo.
- **Panel de filtros**: opciones del panel de filtros, incluido el color de fondo, la transparencia, la fuente y el color de los iconos, el tamaño, las tarjetas de filtro, etc.

Después de realizar los cambios, seleccione **Aplicar y guardar** para guardar el tema. Ahora se puede usar el tema en el informe actual y exportarlo.

Este tipo de personalización del tema actual simplifica y agiliza la personalización de los temas. Sin embargo, puede realizar ajustes más precisos en los temas, que requieren la modificación del [archivo JSON](#report-theme-json-file-format) del tema.

> [!TIP]
> Puede personalizar las opciones de los temas para los informes más comunes mediante los controles del cuadro de diálogo **Personalización del tema**. A continuación, puede exportar si quiere el archivo JSON y realizar ajustes personalizados de forma manual modificando la configuración en ese archivo. Puede cambiar el nombre de ese archivo JSON optimizado y, después, importarlo.

### <a name="import-custom-report-theme-files"></a>Importación de archivos de tema para informes personalizado

Para importar un archivo de tema para informes personalizado:

1. Seleccione **Cambiar tema** en la cinta de opciones **Inicio** y, a continuación, seleccione **Importar tema** en el menú desplegable.

   ![Importar tema](media/desktop-report-themes/report-themes-3a.png)

   Aparecerá una ventana que le permite examinar la ubicación del archivo del tema JSON.

2. En la siguiente imagen, hay una serie de archivos de tema de vacaciones disponibles. Elegiremos un tema de vacaciones para marzo, *St Patricks Day.json*.

   ![Tema de vacaciones](media/desktop-report-themes/report-themes_4.png)

   Cuando el archivo de tema se haya cargado correctamente, Power BI Desktop muestra un mensaje de operación correcta.

   ![El tema se ha importado correctamente.](media/desktop-report-themes/report-themes_5.png)

## <a name="introduction-to-report-theme-json-files"></a>Introducción a los archivos JSON de temas para informes

 Cuando abra el archivo JSON básico mencionado en la sección anterior (St Patricks Day.json), aparecerá de la siguiente manera:

 ```json
    {
        "name": "St Patrick's Day",
        "dataColors": ["#568410", "#3A6108", "#70A322", "#915203", "#D79A12", "#bb7711", "#114400", "#aacc66"],
        "background":"#FFFFFF",
        "foreground": "#3A6108",
        "tableAccent": "#568410"
    }
```

Este archivo JSON de tema para informes tiene las siguientes líneas:

- **name**: nombre del tema para informes. Este campo es el único obligatorio.
- **dataColors**: la lista de códigos de color hexadecimales que se usará para los datos de los objetos visuales de Power BI Desktop. La lista puede contener todos los colores que se desee.
- **background**, **firstLevelElements** y **tableAccent** (etc.): las clases de color. Las clases de color permiten establecer muchos colores estructurales a la vez en el informe.

Puede usar este archivo JSON como base para crear su propio archivo de tema para informes personalizado con el objetivo de importarlo. Si desea ajustar solo los colores básicos del informe, cambie el nombre y los códigos hexadecimales en el archivo.

En un archivo JSON de tema para informes, solo se define el formato que se desea cambiar. Cualquier cosa que no especifique en el archivo JSON revierte a la configuración predeterminada de Power BI Desktop.

Son muchas las ventajas de crear un archivo JSON. Por ejemplo, puede especificar que todos los gráficos utilicen un tamaño de fuente de 12 o que ciertos objetos visuales utilicen una familia de fuentes determinada, o bien desactivar las etiquetas de datos para tipos de gráfico específicos. Si usa un archivo JSON, puede crear un archivo de tema para informes que normalice los gráficos e informes para facilitar la coherencia de los informes de la organización.

Para obtener más información sobre el formato del archivo JSON, vea [Formato de archivo JSON de tema para informes](#report-theme-json-file-format).

> [!NOTE]
> Modificar un tema para informes JSON personalizado con el [cuadro de diálogo **Personalización del tema**](#create-and-customize-a-theme-in-power-bi-desktop-preview) es seguro.  En el cuadro de diálogo no se modificará la configuración de tema que no puede controlar y se actualizarán los cambios realizados en el tema para informes en contexto.

## <a name="how-report-theme-colors-stick-with-your-reports"></a>Aplicación de los colores de los temas a los informes

Cuando publica un informe en el servicio Power BI, los colores del tema para informes permanecen con él. La sección **Colores de datos** del panel **Formato** refleja el tema para el informe.

Para ver los colores disponibles en un tema para informes:

1. Seleccione un objeto visual.

2. En la sección **Formato** del panel **Visualización**, seleccione **Colores de datos**.

3. Seleccione la lista desplegable de un elemento para ver la información de **Colores del tema** del tema para informes.

   ![Colores del tema](media/desktop-report-themes/report-themes_8.png)

En nuestro ejemplo, después de aplicar la gran cantidad de colores verdes y marrones del tema para informes St. Patrick's Day, vea los colores del tema. ¿Puede ver toda esa cantidad de verde? Esto se debe a que esos colores formaban parte del tema para informes que importamos y aplicamos.

Los colores de la paleta de colores también son relativos al tema actual. Por ejemplo, supongamos que selecciona el tercer color de la fila superior de un punto de datos. Más adelante, si cambia a otro tema, el color del punto de datos se actualiza automáticamente al tercer color de la fila superior del nuevo tema, tal como se vería al cambiar los temas en Microsoft Office.

### <a name="situations-when-report-theme-colors-wont-stick-to-your-reports"></a>Situaciones en las que los colores del tema no se aplican a los informes

Supongamos que aplica un conjunto de colores personalizado (o uno solo) a un punto de datos determinado en un objeto visual con la opción **Color personalizado** del selector de colores. Al aplicar un tema para informes, *no* invalidará el color del punto de datos personalizado.

Es posible que también quiera establecer manualmente el color de un punto de datos mediante el uso de la sección **Colores de tema**. Al aplicar un nuevo tema para informes, los colores *no* se actualizan. Para volver a los colores predeterminados y así permitir que se actualicen cuando aplique un nuevo tema para informes, seleccione **Volver al valor predeterminado** o un color en la paleta **Colores del tema** en el selector de colores.

![Volver al valor predeterminado](media/desktop-report-themes/report-themes_9.png)

Además, muchos otros objetos visuales personalizados no aplicarán temas para informes.

## <a name="custom-report-theme-files-you-can-use-right-now"></a>Archivos de temas para informes personalizados que se pueden usar ya

¿Quiere empezar a trabajar con temas para informes? Consulte los temas para informes personalizados en la [galería de temas](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery) o pruebe los siguientes archivos JSON de temas para informes personalizados listos para usar, que puede descargar e importar en el informe de Power BI Desktop:

- [Tema de olas](https://community.powerbi.com/t5/Themes-Gallery/Waveform/m-p/140536). Este tema del informe se presentó en la [entrada de blog](https://powerbi.microsoft.com/blog/power-bi-desktop-march-feature-summary/) que anunció la primera versión de los temas para informes. [Descargar Waveform.json](https://go.microsoft.com/fwlink/?linkid=843924)

  ![Tema Waverform.json](media/desktop-report-themes/report-themes_10.png)

- [Tema para personas daltónicas](https://community.powerbi.com/t5/Themes-Gallery/Color-Blind-Friendly/m-p/140597).
Este tema para informes es más fácil de leer para las personas daltónicas. [Descargar ColorblindSafe-Longer.json](https://go.microsoft.com/fwlink/?linkid=843923)

  ![El tema ColorblindSafe-Longer.json](media/desktop-report-themes/report-themes_11.png).

- Temas de Power View temas, que incluye Apothecary.json. [Descargar temas de Power View en un archivo ZIP](https://go.microsoft.com/fwlink/?linkid=843925)

  ![El tema Apothecary.json](media/desktop-report-themes/report-themes_12.png)

- El tema para el día de San Valentín

  ![El tema para el día de San Valentín](media/desktop-report-themes/report-themes_13.png)

  Este es el código del archivo JSON del tema para el día de San Valentín:

   ```json
       {
           "name": "Valentine's Day",
           "dataColors": ["#990011", "#cc1144", "#ee7799", "#eebbcc", "#cc4477", "#cc5555", "#882222", "#A30E33"],
           "background":"#FFFFFF",
           "foreground": "#ee7799",
           "tableAccent": "#990011"
       }
   ```

A continuación, se incluyen algunos temas para informes que puede usar como puntos de partida:

- [Sunflower-twilight](https://community.powerbi.com/t5/Themes-Gallery/Sunflower-Twilight/m-p/140749)
- [Plum](https://community.powerbi.com/t5/Themes-Gallery/Plum/m-p/140711)
- [Autumn](https://community.powerbi.com/t5/Themes-Gallery/Autumn/m-p/140746)
- [High contrast](https://community.powerbi.com/t5/Themes-Gallery/Color-Blind-Friendly/m-p/140597)

Los temas para informes pueden crear coloridos informes de Power BI Desktop para usted, su organización o incluso para la temporada o festividad que se celebre en ese momento.

## <a name="export-report-themes-preview"></a>Exportación de temas para informes (versión preliminar)

A partir de la versión de diciembre de 2019 de Power BI Desktop, ahora puede tener la opción de exportar el tema para informes aplicado actualmente directamente desde Power BI Desktop a un archivo JSON. Después de exportar un tema para informes, puede reutilizarlo en otros informes. Esta opción permite exportar el archivo JSON para la mayoría de los temas integrados. Las únicas excepciones son los temas base: el clásico y el predeterminado, en los que se basan otros temas cuando se importan.

Para exportar el tema actualmente aplicado desde Power BI Desktop:

1. Seleccione **Archivo** > **Opciones y configuración** > **Opciones**.

2. En la sección **Características de vista previa**, seleccione **Personalizar tema actual** y, a continuación, seleccione **Aceptar**.

   Es posible que se le pida reiniciar Power BI Desktop para habilitar la característica en versión preliminar. Después de reiniciar, puede empezar a exportar el tema aplicado actualmente.

3. En la cinta de opciones **Inicio**, seleccione **Cambiar tema** > **Exportar tema actual**.

4. En el cuadro de diálogo **Guardar como**, vaya a un directorio en el que guardar el archivo JSON y, a continuación, seleccione **Guardar**.

## <a name="report-theme-json-file-format"></a>Formato de archivo JSON de tema para informes

En su nivel más básico, el archivo JSON del tema solo tiene una línea necesaria: el **nombre**.

```json
{
    "name": "Custom Theme"
}
```

Aparte del **nombre**, todo lo demás es opcional, lo que significa que solo tiene que agregar al archivo de tema las propiedades a las que quiere aplicar formato específicamente y seguir usando los valores predeterminados de Power BI con el resto.

### <a name="setting-theme-colors"></a>Establecimiento de los colores del tema

En **Nombre**, puede agregar las siguientes propiedades básicas relacionadas con el color de los datos:

- **dataColors**: lista de códigos de color hexadecimales que se usarán para colorear las formas que representan los datos de los objetos visuales de Power BI Desktop. La lista puede contener todos los colores que se desee. Cuando se hayan usado todos los colores de esta lista, si el objeto visual todavía necesita más colores, vuelva para usar la paleta de colores predeterminada de Power BI.
- **bueno**, **neutro** y **malo**: estas propiedades establecen los colores de estado que se usan en el gráfico de cascada y el objeto visual de KPI.
- **máximo**, **centro**, **mínimo** y **nulo**: estos colores establecen los distintos colores de degradado en el cuadro de diálogo de formato condicional.

Un tema básico que define estos colores podría mostrarse de la siguiente manera:

```json
{
    "name": "Custom Theme",
    "dataColors": [
        "#118DFF",
        "#12239E",
        "#E66C37",
        "#6B007B",
        "#E044A7",
        "#744EC2",
        "#D9B300",
        "#D64550",
        "#197278",
        "#1AAB40"
    ],
    "good": "#1AAB40",
    "neutral": "#D9B300",
    "bad": "#D64554",
    "maximum": "#118DFF",
    "center": "#D9B300",
    "minimum": "#DEEFFF",
    "null": "#FF7F48"
}
```

### <a name="setting-structural-colors"></a>Establecimiento de colores estructurales

A continuación, puede agregar varias clases de color, tales como **background** y **firstLevelElements**. Estas clases de color establecen los colores estructurales de los elementos del informe, tales como las líneas de cuadrícula del eje, los colores de resaltado y los colores de fondo de los elementos visuales.

Puede ver las seis clases de color a las que puede aplicar formato en la tabla siguiente.  Los nombres relativos a **Clase de color** corresponden a los nombres de la subsección "Avanzado" de la sección "Nombre y colores" del [cuadro de diálogo **Personalización del tema**](#create-and-customize-a-theme-in-power-bi-desktop-preview).

|Clase de color  |A qué aplica formato  |
|---------|---------|
| **firstLevelElements** <br> **foreground** (en desuso) | Color de fondo de las etiquetas (cuando están fuera de los puntos de datos) <br> Color de línea de tendencia <br>  Color predeterminado del cuadro de texto <br> Colores de fuente de valores y totales de tabla y matriz, color de eje de barras de datos <br> Etiquetas de datos de tarjeta <br> Color del valor de globo del medidor <br> Color del objetivo de KPI <br>  Color de texto de KPI <br> Color del elemento de segmentación (en el modo de enfoque)  <br> Color de fuente del elemento de lista desplegable de segmentación <br> Color de fuente de entrada numérica de segmentación <br> Color de fuente del encabezado de segmentación <br> Color de línea de proporción de gráfico de dispersión <br> Color de línea de previsión de gráfico de líneas <br> Color de línea de guía de mapa <br> Color del texto de tarjeta y panel de filtro|
| **secondLevelElements** <br> **foregroundNeutralSecondary** (en desuso) | [Clases de texto secundario](#setting-formatted-text-defaults) "light" <br> Colores de etiqueta  <br> Color de etiqueta de leyenda <br> Color de etiqueta de eje <br> Color de fuente de encabezado de tabla y matriz <br> Color de línea de guía de destino y destino de medidor <br>  Color de eje de tendencia de KPI <br> Color de control deslizante de segmentación <br> Color de fuente de elemento de segmentación <br> Color de contorno de segmentación <br> Color al mantener el puntero en el gráfico de líneas <br> Color del título de la tarjeta de varias filas <br> Color de trazo del gráfico de la barra de herramientas <br> Color de borde del mapa de formas <br> Color de fuente del texto de botón <br> Color de línea del icono de botón <br> Color de contorno del botón |
| **thirdLevelElements** <br >**backgroundLight** (en desuso) | Color de cuadrícula del eje <br> Color de cuadrícula de tabla y matriz <br> Color de fondo del encabezado de segmentación (en modo de enfoque)  <br> Color de esquema de tarjeta de varias filas  <br> Color de relleno de forma <br> Color de fondo del arco del medidor <br> Color de fondo de la tarjeta de filtro aplicado <br> |
| **fourthLevelElements** <br> **foregroundNeutralTertiary** (en desuso) | color atenuado de leyenda <br> Color de etiqueta de categoría de tarjeta <br> Color de etiquetas de categoría de tarjeta de varias filas <br> Color de la barra de tarjeta de varias filas <br> Color de trazo de la tasa de conversión de gráficos de embudo
| **background** | Color de fondo de las etiquetas (cuando están dentro de los puntos de datos) <br> Color de fondo de los elementos de lista desplegable de segmentación  <br> Color de trazo del gráfico de anillos <br> Color de trazo del gráfico de rectángulos <br> Color de fondo de gráfico combinado <br> Color de relleno del botón <br> Color de fondo de la tarjeta de filtro disponible y del panel de filtros |
| **secondaryBackground** <br> **backgroundNeutral** (en desuso) | Color de esquema de cuadrícula de tabla y matriz <br> Color predeterminado de mapa de formas <br> Color de relleno de la cinta del gráfico de la barra de herramientas (cuando la opción de coincidencia de series está desactivada) |
| **tableAccent** | Reemplaza el color de contorno de la cuadrícula de tabla y matriz cuando existe. |

Este es un tema de ejemplo con las clases de color:

```json
{
    "name": "Custom Theme",
    "firstLevelElements": "#252423",
    "secondLevelElements": "#605E5C",
    "thirdLevelElements": "#F3F2F1",
    "fourthLevelElements": "#B3B0AD",
    "background": "#FFFFFF",
    "secondaryBackground": "#C8C6C4",
    "tableAccent": "#118DFF"
}
```

> [!TIP]
> Si va a crear un "tema oscuro" u otro tema multicolor que difiera del típico **firstLevelElements** "negro" sobre **background** "blanco", asegúrese también de establecer los valores de otros colores estructurales y los [colores de la clase de texto principal](#setting-formatted-text-defaults).  Esto garantizará que, por ejemplo, las etiquetas de datos de los gráficos con un fondo de etiqueta coincidirán con el estilo previsto y serán legibles, además de garantizar la visibilidad de las líneas de cuadrícula del eje.

### <a name="setting-formatted-text-defaults"></a>Establecimiento de valores predeterminados de texto con formato

después, puede agregar clases de texto al archivo JSON. Las clases de texto son similares a las clases de color, pero están diseñadas para permitirle actualizar el tamaño, el color y la familia de fuentes de los grupos de texto en el informe.

Aunque hay 12 clases de texto, solo es necesario establecer cuatro clases, denominadas *clases principales*, para cambiar todo el formato de texto del informe.  Estas cuatro clases principales se pueden establecer en la sección "Texto" del [cuadro de diálogo **Personalización del tema**](#create-and-customize-a-theme-in-power-bi-desktop-preview): "General" corresponde a **label**; "Título", a **title**; "Tarjetas y KPI", a **callout**; y "Encabezados de pestaña", a **header**.

Otras clases de texto, consideradas *clases secundarias*, obtienen automáticamente sus propiedades de sus clases principales asociadas. A menudo, una clase secundaria selecciona un tono más claro de color de texto, o un porcentaje de tamaño de texto grande o más pequeño en comparación con la clase primaria.

Tome como ejemplo la clase **label**. El formato predeterminado de la clase **label** es Segoe UI, #252423 (color gris oscuro) y 12 puntos. Esta clase se utiliza para dar formato a los valores de la tabla y la matriz. Normalmente, los totales de una tabla o matriz tienen un formato similar, pero aparecen en negrita para que resalten más, de modo que usan la clase **bold label**. Sin embargo, no es necesario especificar esa clase en el archivo JSON del tema; Power BI lo hace automáticamente. Más adelante, si decide especificar etiquetas que tienen una fuente de 14 puntos en el tema, no es necesario actualizar también la clase **bold**, ya que hereda el formato de texto de la clase **label**.

En la tabla siguiente se muestra la siguiente información:

- Cada una de las cuatro clases de texto principales, a lo que se aplica formato y su configuración predeterminada.
- Cada clase secundaria, a lo que aplica formato y su configuración predeterminada que es única en comparación con la clase principal.

|Clase principal  |Clases secundarias  |Nombre de clase JSON  | Configuración predeterminada  |Objetos visuales asociados  |
|---------|---------|---------|---------|---------|
| Callout | N/D | callout | DIN <br> #252423 <br> 45pt |Etiquetas de datos de tarjeta <br> Indicadores de KPI|
|Encabezado|N/D|header|Segoe UI Semibold <br> #252423 <br> 12pt |Encabezados de influenciadores clave |
| Título || título |DIN <br> #252423 <br> 12pt |Título del eje de categoría <br> Título del eje de valores <br> Título de tarjeta de varias filas * <br> Encabezado de segmentación|
|-| Large title | largeTitle |14pt |Título de objeto visual |
|Label ||label |Segoe UI<br>#252423<br>10pt |Encabezados de columna de tabla y matriz <br> Encabezados de fila de matriz<br>Cuadrícula de tabla y matriz<br>Valores de tabla y matriz |
|-|Semibold |semiboldLabel| Segoe UI Semibold | Texto del perfil de influenciadores clave
|-|Grande |largeLabel |12pt | Etiquetas de datos de tarjeta de varias filas |
|-|Pequeño |smallLabel |9pt |Etiquetas de línea de referencia * <br>Etiquetas de intervalo de fechas de segmentación<br> Estilo de texto de entrada numérica de segmentación<br>Cuadro de búsqueda de segmentación<br>Texto de influenciadores clave|
|-|Claro |lightLabel |#605E5C |Texto de leyenda<br>Texto de botón<br>Etiquetas del eje de categoría<br>Etiquetas de datos del gráfico de embudo<br>Etiquetas de tasa de conversión del gráfico de embudo<br>Destino del medidor<br>Etiqueta de categoría del gráfico de dispersión<br>Elementos de segmentación|
|-|Bold |boldLabel |Segoe UI Bold |Subtotales de matriz<br>Totales generales de matriz<br>Totales de tabla |
|-|Large and Light |largeLightLabel |#605E5C<br>12pt |Etiquetas de categoría de tarjeta<br>Etiqueta del medidor<br>Etiquetas de categoría de tarjeta de varias filas |
|-|Small and Light |smallLightLabel |#605E5C<br>9pt |Etiquetas de datos<br>Etiquetas del eje de valores|

*\* Los elementos señalados con asterisco también se colorean en función del primer color de datos del tema para informes.*

> [!TIP]
> Las variaciones *light* de las clases de texto adoptan el color claro de los [colores estructurales](#setting-structural-colors) definidos anteriormente.  Si va a crear un "tema oscuro", asegúrese de establecer también los colores "firstLevelElements" (que coincida con el color de texto principal), "secondLevelElements" (que coincida con el color "light" previsto para el texto) y "background" (con suficiente contraste con los colores de los elementos de primer y segundo nivel).

Este es un tema de ejemplo que solo establece las clases de texto principales:

```json
{
    "name": "Custom Theme",
    "textClasses": {
        "callout": {
            "fontSize": 45,
            "fontFace": "DIN",
            "color": "#252423"
        },
        "title": {
            "fontSize": 12,
            "fontFace": "DIN",
            "color": "#252423"
        },
        "header": {
            "fontSize": 12,
            "fontFace": "Segoe UI Semibold",
            "color": "#252423"
        },
        "label": {
            "fontSize": 10,
            "fontFace": "Segoe UI",
            "color": "#252423"
        }
    }
}
```

Dado que las clases secundarias se heredan de las clases principales, no es necesario establecerlas en el archivo de tema. Sin embargo, si no le gustan las reglas de herencia (por ejemplo, si no quiere que los totales sean una versión en negrita de los valores de una tabla), puede dar formato explícitamente a las clases secundarias del archivo de tema, al igual que puede dar formato a las clases principales.

### <a name="setting-visual-property-defaults-visualstyles"></a>Establecimiento de valores predeterminados de propiedades de objetos visuales (`visualStyles`)

Finalmente, para crear un archivo JSON de formato extendido, con un control más pormenorizado y detallado sobre todo el formato de los objetos visuales del informe, agregue una sección **visualStyles** al archivo JSON para anidar las características específicas de formato. Este es un ejemplo con plantilla de la sección **visualStyles**:

```json
    "visualStyles": {
        "<visualName>": {
            "<styleName>": {
                "<cardName>": [{
                    "<propertyName>": <propertyValue>
                }]
            }
        }
    }
```

En las secciones **visualName** y **cardName**, use un objeto visual y un nombre de tarjeta específicos. Actualmente, **styleName** siempre es un asterisco (*), pero en una versión futura podrá crear distintos estilos para sus objetos visuales y proporcionarles nombres (similar a la característica de estilo de tabla y matriz). **propertyName** es el nombre de la opción de formato y **propertyValue** es el valor de esa opción de formato.

Para **visualName** y **cardName**, use un asterisco con comillas si desea que la configuración se aplique a todos los objetos visuales o las tarjetas que tienen una propiedad. Si usa el asterisco en el nombre del objeto visual y la tarjeta, se aplicaría en la práctica una configuración global en el informe, por ejemplo, un tamaño de fuente o una familia de fuentes específica para todo el texto de todos los objetos visuales.

Este es un ejemplo de configuración de algunas propiedades mediante los estilos visuales:

```json
{
   "name":"Custom Theme",
   "visualStyles":{
      "*": {
         "*": {
            "*": [{
                "wordWrap": true
            }],
            "categoryAxis": [{
                "gridlineStyle": "dotted"
            }],
            "filterCard": [
              {
                "$id": "Applied",
                "foregroundColor": {"solid": {"color": "#252423" } }
              },
              {
                "$id":"Available",
                "border": true
              }
            ]
         }
      },
      "scatterChart": {
         "*": {
            "bubbles": [{
                  "bubbleSize": -10
            }]
         }
      }
   }
}
```

En este ejemplo se realizan los siguientes ajustes:

- Active el ajuste automático de línea en todas partes.
- Estable el estilo de la cuadrícula en puntos para todos los objetos visuales con un eje de categoría.
- Establece el formato de las tarjetas disponibles y de filtro aplicadas (tenga en cuenta el formato con "$id" para establecer las diferentes versiones de las tarjetas de filtro).
- Establece el tamaño de la burbuja de los gráficos de dispersión en -10.

> [!NOTE]
> Solo debe especificar los elementos de formato que desea ajustar. Los elementos de formato no incluidos en el archivo JSON simplemente vuelven a sus valores y configuración predeterminados.

### <a name="visualstyles-definition-list"></a>Lista de definiciones de `visualStyles`

En las tablas de esta sección se definen los nombres de objetos visuales (**visualName**), los nombres de tarjetas (**cardName**), los nombres de propiedades (**propertyName**) y las enumeraciones necesarias para crear el archivo JSON.

| Valores de visualName |
| --- |
| areaChart |
| barChart |
| basicShape |
| tarjeta |
| clusteredBarChart |
| clusteredColumnChart |
| columnChart |
| comboChart |
| donutChart |
| filledMap |
| embudo |
| medidor |
| hundredPercentStackedBarChart |
| hundredPercentStackedColumnChart |
| imagen |
| kpi |
| lineChart |
| lineClusteredColumnComboChart |
| lineStackedColumnComboChart |
| mapa |
| multiRowCard |
| pieChart |
| pivotTable |
| ribbonChart |
| scatterChart |
| shapeMap |
| segmentación |
| stackedAreaChart |
| tableEx |
| gráfico de rectángulos |
| waterfallChart |

La siguiente tabla define los valores de **cardName**. El primer valor de cada celda es el término del archivo JSON. El segundo valor es el nombre de la tarjeta tal y como se muestra en la interfaz de usuario de Power BI Desktop.

| Valores de cardName |
| --- |
| axis: Eje medidor |
| breakdown: Desglose |
| bubbles: Burbujas |
| calloutValue: Valor de la llamada |
| card: Tarjeta |
| cardTitle: Título de tarjeta |
| categoryAxis: Eje X |
| categoryLabels: Etiquetas de categoría |
| columnFormatting: Formato de campo |
| columnHeaders: Encabezados de columna |
| dataLabels: Etiquetas de datos |
| fill: Rellenar |
| fillPoint: Punto de relleno |
| forecast: Previsión |
| general: General |
| goals: Objetivos |
| grid: Cuadrícula |
| header: Encabezado |
| imageScaling: Escala |
| indicator: Indicador |
| items: Elementos |
| labels: Etiquetas de datos |
| legend: Leyenda |
| lineStyles: Formas |
| mapControls: Controles de mapa |
| mapStyles: Estilos de mapa |
| numericInputStyle: Entradas numéricas |
| percentBarLabel: Etiqueta de tasa de conversión |
| plotArea: Área de trazado |
| plotAreaShading: Sombreado de simetría |
| ratioLine: Línea de relación |
| referenceLine: Línea constante |
| ribbonChart: Barras de herramientas |
| rotation: Rotación |
| rowHeaders: Encabezados de fila |
| selection: Controles de selección |
| sentimentColors: Tendencia de las opiniones |
| shape: Forma |
| slider: Control deslizante |
| status: Codificación del color |
| subTotals: Subtotales |
| target: Destino |
| total: Total general |
| trend: Línea de tendencia |
| trendline: Eje de tendencia |
| valueAxis: Eje Y |
| values: Valores |
| wordWrap: Ajuste automático de línea |
| xAxisReferenceLine: Línea constante del eje X |
| y1AxisReferenceLine: Línea constante |
| zoom: Zoom |

### <a name="properties-within-each-card"></a>Propiedades de cada tarjeta

En la siguiente sección se definen las propiedades de cada tarjeta. El nombre de la tarjeta va seguido del nombre de cada propiedad. Para cada nombre de propiedad verá si se muestra el panel de formato, una descripción de lo que hace la opción de formato y el tipo de la opción de formato. Este enfoque le permite saber qué tipo de valores puede usar en el archivo de tema.

Cuando se usa **dateTime**, la fecha debe ser una fecha ISO entre comillas simples, precedida de datetime. Vea el ejemplo siguiente:

  "datetime'2011-10-05T14:48:00.000Z'"

Los valores booleanos son true o false. Las cadenas deben ir entre comillas dobles, como en "esto es una cadena". Los números son solo el propio valor, sin comillas.

Los colores usan el formato siguiente, donde el código hexadecimal personalizado va donde "FFFFFF" se encuentra en el ejemplo siguiente:

    { "solid": { "color": "#FFFFFF" } }

Una enumeración, que se usa normalmente para las opciones de formato de lista desplegable, significa que se puede establecer en cualquiera de las opciones que se muestran en el panel, por ejemplo, "RightCenter" para la posición de la leyenda o "Valor de datos, porcentaje de total" para la etiqueta de datos del gráfico circular. Las opciones de enumeración se muestran debajo de la lista de propiedades.

```json
{
      "general":{
        "responsive": {
          "type": [
            "bool"
          ],
          "displayName": [
            "(Preview) Responsive"
          ],
          "description": [
            "The visual will adapt to size changes"
          ]
        },
        "legend": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select the location for the legend"
          ]
        },
        "showTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Display a title for legend symbols"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "categoryAxis": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "axisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "start": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "end": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "axisType": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Type"
          ]
        },
        "showAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the X-axis",
            "Title for the Y-axis"
          ]
        },
        "axisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "concatenateLabels": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Concatenate labels"
          ],
          "description": [
            "Always concatenate levels of the hierarchy instead of drawing the hierarchy."
          ]
        },
        "preferredCategoryWidth": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Minimum category width"
          ]
        },
        "titleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "titleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "titleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "duration": {
          "type": [
            "numeric"
          ]
        }
      },
      "valueAxis": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "axisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "start": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "end": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "showAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the Y-axis",
            "Title for the X-axis"
          ]
        },
        "axisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "titleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "titleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "titleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        },
        "axisLabel": {
          "type": [
            "none"
          ],
          "displayName": [
            "Y-Axis (Column)"
          ]
        },
        "secShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show secondary"
          ]
        },
        "alignZeros": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Align zeros"
          ],
          "description": [
            "Align the zero tick marks for both value axes"
          ]
        },
        "secAxisLabel": {
          "type": [
            "none"
          ],
          "displayName": [
            "Y-Axis (Line)"
          ]
        },
        "secPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "secAxisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "secStart": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "secEnd": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "secShowAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the Y-axis"
          ]
        },
        "secAxisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "secLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "secFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "secFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "secLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "secLabelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "secTitleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "secTitleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "secTitleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        }
      },
      "dataPoint": {
        "defaultColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Default color",
            "Default Column Color"
          ]
        },
        "fill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Fill"
          ]
        },
        "defaultCategoryColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Default color",
            "Default Column Color"
          ]
        },
        "showAllDataPoints": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show all"
          ]
        }
      },
      "labels": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "showSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "showAll": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Customize series"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "labelDensity": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Label density"
          ]
        },
        "labelOrientation": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Orientation"
          ]
        },
        "labelPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ]
        },
        "percentageLabelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "% decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the percentages"
          ]
        },
        "labelStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Label style"
          ]
        }
      },
      "lineStyles": {
        "strokeWidth": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Stroke width"
          ]
        },
        "strokeLineJoin": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Join type"
          ]
        },
        "lineStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "showMarker": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show marker"
          ]
        },
        "markerShape": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Marker shape"
          ]
        },
        "markerSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Marker size"
          ]
        },
        "markerColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Marker color"
          ]
        },
        "showSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Customize series",
            "Show"
          ]
        },
        "shadeArea": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Shade area"
          ]
        }
      },
      "plotArea": {
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "trend": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set trend line name"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set trend line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for trend line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ],
          "description": [
            "Set trend line style"
          ]
        },
        "combineSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Combine Series"
          ],
          "description": [
            "Show one trend line per series or combine"
          ]
        }
      },
      "y1AxisReferenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "referenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set reference line name"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "line": {
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        },
        "weight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Weight"
          ]
        },
        "roundEdge": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Round edges"
          ]
        }
      },
      "fill": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "fillColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Fill color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "rotation": {
        "angle": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Rotation"
          ]
        }
      },
      "categoryLabels": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "wordWrap": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "dataLabels": {
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "cardTitle": {
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "card": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "outlineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Outline color"
          ],
          "description": [
            "Color of the outline"
          ]
        },
        "outlineWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Outline weight"
          ],
          "description": [
            "Thickness of the outline in pixels"
          ]
        },
        "barShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show bar"
          ],
          "description": [
            "Display a bar to the left side of the card as an accent"
          ]
        },
        "barColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Bar color"
          ]
        },
        "barWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Bar thickness"
          ],
          "description": [
            "Thickness of the bar in pixels"
          ]
        },
        "cardPadding": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Padding"
          ],
          "description": [
            "Background"
          ]
        },
        "cardBackground": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        }
      },
      "percentBarLabel": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "axis": {
        "min": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Min"
          ]
        },
        "max": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Max"
          ]
        },
        "target": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Target"
          ]
        }
      },
      "target": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "calloutValue": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        }
      },
      "forecast": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set forecast name"
          ]
        },
        "confidenceBandStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Confidence band style"
          ],
          "description": [
            "Set forecast confidence band style"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set forecast line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "transform": {
          "type": [
            "queryTransform"
          ]
        }
      },
      "bubbles": {
        "bubbleSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Size"
          ]
        }
      },
      "mapControls": {
        "autoZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto zoom"
          ]
        },
        "zoomLevel": {
          "type": [
            "numeric"
          ]
        },
        "centerLatitude": {
          "type": [
            "numeric"
          ]
        },
        "centerLongitude": {
          "type": [
            "numeric"
          ]
        }
      },
      "mapStyles": {
        "mapTheme": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Theme"
          ]
        }
      },
      "shape": {
        "map": {
          "type": [
            "geoJson"
          ]
        },
        "projectionEnum": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Projection"
          ],
          "description": [
            "Projection"
          ]
        }
      },
      "zoom": {
        "autoZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto zoom"
          ],
          "description": [
            "Zoom in on shapes with available data"
          ]
        },
        "selectionZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Selection zoom"
          ],
          "description": [
            "Zoom in on selected shapes"
          ]
        },
        "manualZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Manual zoom"
          ],
          "description": [
            "Allow user to zoom and pan"
          ]
        }
      },
      "xAxisReferenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "fillPoint": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "colorByCategory": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "plotAreaShading": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "upperShadingColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Upper shading"
          ],
          "description": [
            "Shading color of the upper region"
          ]
        },
        "lowerShadingColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Lower shading"
          ],
          "description": [
            "Shading color of the lower region"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "ratioLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        }
      },
      "grid": {
        "outlineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Outline color"
          ],
          "description": [
            "Color of the outline"
          ]
        },
        "outlineWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Outline weight"
          ],
          "description": [
            "Thickness of the outline in pixels"
          ]
        },
        "gridVertical": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Vert grid"
          ],
          "description": [
            "Show/Hide the vertical gridlines"
          ]
        },
        "gridVerticalColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Vert grid color"
          ],
          "description": [
            "Color for the vertical gridlines"
          ]
        },
        "gridVerticalWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Vert grid thickness"
          ],
          "description": [
            "Thickness of the vertical gridlines in pixels"
          ]
        },
        "gridHorizontal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Horiz grid"
          ],
          "description": [
            "Show/Hide the horizontal gridlines"
          ]
        },
        "gridHorizontalColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Horiz grid color"
          ],
          "description": [
            "Color for the horizontal gridlines"
          ]
        },
        "gridHorizontalWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Horiz grid thickness"
          ],
          "description": [
            "Thickness of the horizontal gridlines in pixels"
          ]
        },
        "rowPadding": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Row padding"
          ],
          "description": [
            "Padding in pixels applied to top and bottom of every row"
          ]
        },
        "imageHeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Image height"
          ],
          "description": [
            "The height of images in pixels"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "columnHeaders": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "autoSizeColumnWidth": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto-size column width"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        }
      },
      "values": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color scales"
          ]
        },
        "fontColorPrimary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the odd rows"
          ]
        },
        "backColorPrimary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the odd rows"
          ]
        },
        "fontColorSecondary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Alternate font color"
          ],
          "description": [
            "Font color of the even rows"
          ]
        },
        "backColorSecondary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Alternate background color"
          ],
          "description": [
            "Background color of the even rows"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "bandedRowHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Banded row style"
          ],
          "description": [
            "Apply banded row style to the last level of the row group headers, using the colors of the values."
          ]
        },
        "valuesOnRow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show on rows"
          ],
          "description": [
            "Show values in row groups rather than columns"
          ]
        }
      },
      "total": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "applyToHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Apply to labels"
          ]
        },
        "totals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Totals"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "columnFormatting": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "styleHeader": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color header"
          ]
        },
        "styleValues": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color values"
          ]
        },
        "styleTotal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color total"
          ]
        },
        "styleSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color subtotals"
          ]
        }
      },
      "rowHeaders": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "stepped": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Stepped layout"
          ],
          "description": [
            "Render row headers with stepped layout"
          ]
        },
        "steppedLayoutIndentation": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Stepped layout indentation"
          ],
          "description": [
            "Set the indentation, in pixels, applied to row headers"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        }
      },
      "subTotals": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "rowSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Total row"
          ]
        },
        "columnSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Total column"
          ]
        },
        "applyToHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Apply to labels"
          ]
        }
      },
      "selection": {
        "selectAllCheckboxEnabled": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Select All"
          ]
        },
        "singleSelect": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Single Select"
          ]
        }
      },
      "header": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        },
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "items": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        },
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "numericInputStyle": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        }
      },
      "slider": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        }
      },
      "dateRange": {
        "includeToday": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Include today"
          ]
        }
      },
      "sentimentColors": {
        "increaseFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Increase"
          ]
        },
        "decreaseFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Decrease"
          ]
        },
        "totalFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Total"
          ]
        },
        "otherFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Other"
          ]
        }
      },
      "breakdown": {
        "maxBreakdowns": {
          "type": [
            "integer"
          ],
          "displayName": [
            "Max breakdowns"
          ],
          "description": [
            "The number of individual breakdowns to show (rest grouped into Other)"
          ]
        }
      },
      "indicator": {
        "indicatorDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "indicatorPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "kpiFormat": {
          "type": [
            "text"
          ],
          "displayName": [
            "Format"
          ]
        }
      },
      "trendline": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "goals": {
        "showGoal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Goal"
          ]
        },
        "showDistance": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Distance"
          ]
        }
      },
      "status": {
        "direction": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Direction"
          ]
        },
        "goodColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Good Color"
          ]
        },
        "neutralColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Neutral Color"
          ]
        },
        "badColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Bad Color"
          ]
        }
      }
```



### <a name="enumerations-in-the-json-file"></a>Enumeraciones en el archivo JSON
La siguiente sección define las enumeraciones que se pueden usar en el archivo JSON.

```json
    {
        "legend": {
            "position": [
                {
                    "value": "Top",
                    "displayName": "Top"
                },
                {
                    "value": "Bottom",
                    "displayName": "Bottom"
                },
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                },
                {
                    "value": "TopCenter",
                    "displayName": "Top Center"
                },
                {
                    "value": "BottomCenter",
                    "displayName": "Bottom Center"
                },
                {
                    "value": "LeftCenter",
                    "displayName": "Left Center"
                },
                {
                    "value": "RightCenter",
                    "displayName": "Right center"
                }
            ],
            "legendMarkerRendering": [
                {
                    "value": "markerOnly",
                    "displayName": "Markers only"
                },
                {
                    "value": "lineAndMarker",
                    "displayName": "Line and markers"
                },
                {
                    "value": "lineOnly",
                    "displayName": "Line only"
                }
            ]
        },
        "categoryAxis": {
            "axisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "axisType": [
                {
                    "value": "Scalar",
                    "displayName": "Continuous"
                },
                {
                    "value": "Categorical",
                    "displayName": "Categorical"
                }
            ],
            "axisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ],
            "gridlineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "position": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ]
        },
        "valueAxis": {
            "position": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ],
            "axisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "axisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ],
            "gridlineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "secPosition": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ],
            "secAxisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "secAxisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ]
        },
        "lineStyles": {
            "strokeLineJoin": [
                {
                    "value": "miter",
                    "displayName": "Miter"
                },
                {
                    "value": "round",
                    "displayName": "Round"
                },
                {
                    "value": "bevel",
                    "displayName": "Bevel"
                }
            ],
            "lineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "markerShape": [
                {
                    "value": "circle",
                    "displayName": "●"
                },
                {
                    "value": "square",
                    "displayName": "■"
                },
                {
                    "value": "diamond",
                    "displayName": "◆"
                },
                {
                    "value": "triangle",
                    "displayName": "▲"
                },
                {
                    "value": "x",
                    "displayName": "☓"
                },
                {
                    "value": "shortDash",
                    "displayName": " -"
                },
                {
                    "value": "longDash",
                    "displayName": "—"
                },
                {
                    "value": "plus",
                    "displayName": "+"
                }
            ]
        },
        "trend": {
            "style": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
            }
        ]
    },
    "y1AxisReferenceLine": {
        "style": [
            {
                "value": "dashed",
                "displayName": "Dashed"
            },
            {
                "value": "solid",
                "displayName": "Solid"
            },
            {
                "value": "dotted",
                "displayName": "Dotted"
            }
        ],
        "position": [
            {
                "value": "back",
                "displayName": "Behind"
            },
            {
                "value": "front",
                "displayName": "In Front"
            }
        ],
        "dataLabelText": [
            {
                "value": "Value",
                "displayName": "Value"
            },
            {
                "value": "Name",
                "displayName": "Name"
            },
            {
                "value": "ValueAndName",
                "displayName": "Name and Value"
            }
        ],
        "dataLabelHorizontalPosition": [
            {
                "value": "left",
                "displayName": "Left"
            },
            {
                "value": "right",
                "displayName": "Right"
            }
        ],
        "dataLabelVerticalPosition": [
            {
                "value": "above",
                "displayName": "Above"
            },
            {
                "value": "under",
                "displayName": "Under"
            }
        ]
    },
    "referenceLine": {
        "style": [
            {
                "value": "dashed",
                "displayName": "Dashed"
            },
            {
                "value": "solid",
                "displayName": "Solid"
            },
            {
                "value": "dotted",
                "displayName": "Dotted"
            }
        ],
        "position": [
            {
                "value": "back",
                "displayName": "Behind"
            },
            {
                "value": "front",
                "displayName": "In Front"
            }
        ],
        "dataLabelText": [
      {
        "value": "Value",
        "displayName": "Value"
      },
      {
        "value": "Name",
        "displayName": "Name"
      },
      {
        "value": "ValueAndName",
        "displayName": "Name and Value"
      }
    ],
    "dataLabelHorizontalPosition": [
      {
        "value": "left",
        "displayName": "Left"
      },
      {
        "value": "right",
        "displayName": "Right"
      }
    ],
    "dataLabelVerticalPosition": [
      {
        "value": "above",
        "displayName": "Above"
      },
      {
        "value": "under",
        "displayName": "Under"
      }
    ]
    },
    "labels": {
    "labelOrientation": [
      {
        "value": "vertical",
        "displayName": "Vertical"
      },
      {
        "value": "horizontal",
        "displayName": "Horizontal"
      }
    ],
    "labelPosition": [
      {
        "value": "Auto",
        "displayName": "Auto"
      },
      {
        "value": "InsideEnd",
        "displayName": "Inside End"
      },
      {
        "value": "OutsideEnd",
        "displayName": "Outside End"
      },
      {
        "value": "InsideCenter",
        "displayName": "Inside Center"
      },
      {
        "value": "InsideBase",
        "displayName": "Inside Base"
      }
    ],
    "labelStyle": [
      {
        "value": "Category",
        "displayName": "Category"
      },
      {
        "value": "Data",
        "displayName": "Data value"
      },
      {
        "value": "Percent of total",
        "displayName": "Percent of total"
      },
      {
        "value": "Both",
        "displayName": "Category, data value"
      },
      {
        "value": "Category, percent of total",
        "displayName": "Category, percent of total"
      },
      {
        "value": "Data value, percent of total",
        "displayName": "Data value, percent of total"
      },
      {
        "value": "Category, data value, percent of total",
        "displayName": "All detail labels"
      }
     ]
    },
    "card": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
         ]
    },
    "imageScaling": {
        "imageScalingType": [
          {
            "value": "Normal",
            "displayName": "Normal"
          },
          {
            "value": "Fit",
            "displayName": "Fit"
          },
          {
            "value": "Fill",
            "displayName": "Fill"
          }
        ]
    },
    "forecast": {
        "confidenceBandStyle": [
          {
            "value": "fill",
            "displayName": "Fill"
          },
          {
            "value": "line",
            "displayName": "Line"
          },
          {
            "value": "none",
            "displayName": "None"
          }
        ],
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ]
        },
        "mapStyles": {
        "mapTheme": [
          {
            "value": "aerial",
            "displayName": "Aerial"
          },
          {
            "value": "canvasDark",
            "displayName": "Dark"
          },
          {
            "value": "canvasLight",
            "displayName": "Light"
          },
          {
            "value": "grayscale",
            "displayName": "Grayscale"
          },
          {
            "value": "road",
            "displayName": "Road"
          }
        ]
    },
    "shape": {
        "projectionEnum": [
          {
            "value": "albersUsa",
            "displayName": "Albers USA"
          },
          {
            "value": "equirectangular",
            "displayName": "Equirectangular"
          },
          {
            "value": "mercator",
            "displayName": "Mercator"
          },
          {
            "value": "orthographic",
            "displayName": "Orthographic"
          }
        ]
        },
        "xAxisReferenceLine": {
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ],
        "position": [
          {
            "value": "back",
            "displayName": "Behind"
          },
          {
            "value": "front",
            "displayName": "In Front"
          }
        ],
        "dataLabelText": [
          {
            "value": "Value",
            "displayName": "Value"
          },
          {
            "value": "Name",
            "displayName": "Name"
          },
          {
            "value": "ValueAndName",
            "displayName": "Name and Value"
          }
        ],
        "dataLabelHorizontalPosition": [
          {
            "value": "left",
            "displayName": "Left"
          },
          {
            "value": "right",
            "displayName": "Right"
          }
        ],
        "dataLabelVerticalPosition": [
          {
            "value": "above",
            "displayName": "Above"
          },
          {
            "value": "under",
            "displayName": "Under"
          }
        ]
        },
        "ratioLine": {
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ]
        },
        "columnHeaders": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "values": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "total": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "rowHeaders": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "subTotals": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ],
        "rowSubtotalsPosition": [
          {
            "value": "Top",
            "displayName": "Top"
          },
          {
            "value": "Bottom",
            "displayName": "Bottom"
          }
        ]
        },
        "general": {
        "orientation": [
          {
            "value": "vertical",
            "displayName": "Vertical"
          },
          {
            "value": "horizontal",
            "displayName": "Horizontal"
          }
        ]
        },
        "data": {
        "relativeRange": [
          {
            "value": "Last",
            "displayName": "Last"
          },
          {
            "value": "Next",
            "displayName": "Next"
          },
          {
            "value": "This",
            "displayName": "This"
          }
        ],
        "relativePeriod": [
          {
            "value": "None",
            "displayName": "Select"
          },
          {
            "value": "Days",
            "displayName": "Days"
          },
          {
            "value": "Weeks",
            "displayName": "Weeks"
          },
          {
            "value": "Calendar Weeks",
            "displayName": "Weeks (Calendar)"
          },
          {
            "value": "Months",
            "displayName": "Months"
          },
          {
            "value": "Calendar Months",
            "displayName": "Months (Calendar)"
          },
          {
            "value": "Years",
            "displayName": "Years"
          },
          {
            "value": "Calendar Years",
            "displayName": "Years (Calendar)"
          }
        ],
        "mode": [
          {
            "value": "Between",
            "displayName": "Between"
          },
          {
            "value": "Before",
            "displayName": "Before"
          },
          {
            "value": "After",
            "displayName": "After"
          },
          {
            "value": "Basic",
            "displayName": "List"
          },
          {
            "value": "Dropdown",
            "displayName": "Dropdown"
          },
          {
            "value": "Relative",
            "displayName": "Relative"
          },
          {
            "value": "Single",
            "displayName": "Single Value"
          }
        ]
        },
        "header": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "items": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "status": {
        "direction": [
          {
            "value": "Positive",
            "displayName": "High is good"
          },
          {
            "value": "Negative",
            "displayName": "Low is good"
          }
         ]
       }
    }
  }
}
```

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Si utiliza uno de nuestros temas originales, el tema "Clásico", o un tema personalizado que haya importado encima de uno de estos, la sección de texto del cuadro de diálogo del tema no estará disponible para su configuración.

Entre los temas integrados que se ven afectados por esta limitación se incluyen los siguientes:
* Clásico
* Parque
* Clase
* Apto para daltónicos
* Eléctrico
* Alto contraste
* Puesta de sol
* Crepúsculo

Si utiliza uno de los temas afectados y no tiene que modificar la configuración de texto, puede usar de forma segura las demás pestañas del cuadro de diálogo sin problemas. Sin embargo, si quiere usar las clases de texto con uno de los temas afectados, tiene un par de opciones:

- La forma más rápida y fácil de habilitar las clases de texto es seleccionar las opciones del tema predeterminado.
- Si quiere conservar el tema personalizado actual, para habilitar la pestaña de texto:
  1. Exporte el tema actual.
  1. Seleccione el tema predeterminado.
  1. Importe el tema personalizado que exportó en el primer paso.

El texto del informe tendrá un aspecto diferente, pero podrá acceder a la pestaña de texto en el cuadro de diálogo del tema.


