---
title: Sugerencias para el diseño de informes en el Generador de informes de Power BI
description: Use las siguientes sugerencias para diseñar sus informes paginados en el Generador de informes paginados de Power BI.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d7e232d09eee2a4cfff17d4565443195e6f7f1aa
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840358"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Sugerencias para el diseño de informes en el Generador de informes de Power BI
  Use las siguientes sugerencias para diseñar sus informes paginados en el Generador de informes paginados de Power BI.  
  
   
  
##  <a name="DesigningReports"></a> Diseñar informes  
  
-   Un informe bien diseñado transmite información que conduce a la acción. Identifique las preguntas que el informe ayuda a responder. Tenga en cuenta esas preguntas al diseñar el informe.  
  
-   Para diseñar visualizaciones de datos efectivas, piense en cómo mostrar la información de manera que sea fácil de entender para el usuario del informe. Elija una región de datos que sea apropiada para los datos que desea visualizar. Por ejemplo, un gráfico transmite información resumida y agregada mejor que una tabla que abarca muchas páginas de información detallada. Puede visualizar los datos de un conjunto de datos en cualquier región de datos, incluidos gráficos, mapas, indicadores, minigráficos, barras de datos y datos tabulares, con diversos diseños de cuadrícula basados en una tablix. 
  
-   Si va a entregar el informe en un formato de exportación concreto, pruebe el formato de exportación al principio de su diseño. La compatibilidad con las características varía en función del representador que elija.  
  
-   Si crea diseños complejos, genere el diseño por etapas. Puede utilizar rectángulos como contenedores para organizar los elementos de informe. Puede crear regiones de datos directamente en la superficie de diseño para maximizar el área de trabajo; a continuación, a medida que complete cada una, arrástrela al contenedor de rectángulo. Si utiliza rectángulos como contenedores, puede colocar todo su contenido en un solo paso. Los rectángulos también ayudan a controlar la manera en que los elementos de informe se representan en cada página.  
  
-   Para reducir el desorden en un informe, puede utilizar visibilidad condicional para elementos de informe específicos y que el usuario pueda elegir si desea mostrar los elementos. Puede establecer la visibilidad en función de un parámetro o un control de alternancia de cuadro de texto. Puede agregar cuadros de texto ocultos condicionalmente para mostrar los resultados de expresiones provisionales. Si en un informe aparecen datos inesperados, puede mostrar estos resultados provisionales para facilitar la depuración de las expresiones.  
  
-   Cuando se trabaja con elementos anidados en celdas o rectángulos de tablix, se pueden establecer diferentes colores de fondo para el contenedor y los elementos contenidos. De forma predeterminada, el color de fondo es **Ningún color**. Los elementos que tienen un color de fondo específico se muestran en los elementos con el color de fondo establecido en **Ningún color**. Esta técnica puede ayudarle a seleccionar el elemento correcto para establecer las propiedades de presentación, como la visibilidad del borde de las celdas de tablix.  
  
 Para más información acerca de lo que hay que tener en cuenta al diseñar el informe, consulte [Planeamiento de un informe en el Generador de informes](report-builder-planning-report.md)).  
  
##  <a name="NamingConventions"></a> Convenciones de nomenclatura para informes, orígenes de datos y conjuntos de datos  
  
-   Utilice las convenciones de nomenclatura para los orígenes de datos y conjuntos de datos que documenten el origen de datos.  
  
    1.  **Orígenes de datos.** Si no desea utilizar un servidor real o la base de datos debido a motivos de seguridad, utilice un alias que indique al usuario cuál es el origen de datos.  
  
    2.  **Conjuntos de datos.** Utilice un nombre que indique en qué origen de datos se basa.  
  
##  <a name="Data"></a> Trabajar con datos  
  
-   Como primer paso, obtenga todos los datos con los que desea trabajar para que aparezcan en el panel Datos de informe. Cuando ajuste las preguntas que el informe está diseñado para responder, piense cómo limitar los datos en los conjuntos de datos de informe a solo los necesarios.  
  
-   En general, incluya solo los datos que se van a mostrar en un informe. Use variables de consulta en las consultas de conjunto de datos para que el usuario pueda elegir los datos que desean ver en el informe. Si va a crear conjuntos de datos compartidos, proporcione filtros basados en parámetros de informe para proporcionar la misma funcionalidad.  
  
-   Si tiene experiencia escribiendo consultas, sabrá que para cantidades de datos intermedias, tal vez desee agrupar los datos en el informe y no en la consulta. Si hace todas las agrupaciones en la consulta, el informe suele ser una presentación del conjunto de resultados de la consulta. Por otro lado, para mostrar los valores agregados para grandes cantidades de datos en un gráfico o una matriz, no es necesario incluir datos detallados.  
  
-   Según sus requisitos, puede mostrar los nombres y ubicaciones de los orígenes de datos del informe, el texto de los comandos de consulta del conjunto de datos y los valores de parámetro del informe. Lo primero que se preguntan muchos usuarios nuevos es de dónde proceden los datos. Para reducir el desorden en el informe, puede ocultar condicionalmente los cuadros de texto con este tipo de información y dejar que los usuarios elijan si quieren verlo. Intente agregar esta información en la última página del informe. Establezca la visibilidad del cuadro de texto según un parámetro que el usuario pueda cambiar.  
  
##  <a name="DesignSurface"></a> Interactuar con la superficie de diseño del informe  
 La superficie de diseño del informe no es WYSIWIG. Al colocar los elementos de informe en la superficie de diseño, su ubicación relativa afecta a la manera en que aparecen los elementos en la página del informe representado. Se conserva el espacio en blanco.  
  
-   Utilice los botones de diseño y las líneas de ajuste para alinear y organizar los elementos en la superficie de diseño del informe. Por ejemplo, puede alinear las partes superiores o los bordes de los elementos seleccionados, expandir un elemento para que coincida con el tamaño de otro elemento o ajustar el espaciado entre los elementos.  
  
-   Utilice las teclas de dirección para ajustar la posición y el tamaño de los elementos seleccionados en la superficie de diseño. Por ejemplo, las siguientes combinaciones de teclas son muy útiles:  
  
    -   **Teclas de dirección**: mover el elemento de informe seleccionado.  
  
    -   **Ctrl+Teclas de dirección**: desplazar el elemento de informe seleccionado.  
  
    -   **Ctrl+Mayús+Teclas de dirección**: aumentan o reducen el tamaño del elemento de informe seleccionado.  
  
-   Para agregar un elemento a un rectángulo, utilice la punta superior izquierda del mouse para que apunte a la ubicación inicial del elemento en el contenedor de rectángulo. Use los métodos abreviados de teclado para ayudar a colocar los objetos seleccionados. El rectángulo se expande automáticamente para adaptarse al tamaño de los elementos contenidos.  
  
-   Para agregar varios elementos a una celda de tablix, primero agregue un rectángulo y, a continuación, agregue los elementos.  
  
     De forma predeterminada, cada celda de tablix contiene un cuadro de texto. Cuando se agrega un rectángulo a una celda, el rectángulo reemplaza al cuadro de texto. Por ejemplo, coloque indicadores anidados en un rectángulo en una celda de tablix para ayudar a controlar cómo se expande el tamaño de un gráfico o indicador cuando cambia el alto de la fila que se encuentra la celda.  
  
-   Use el control **Zoom** para ajustar la vista de la superficie de diseño. Puede trabajar con la página entera o con secciones más pequeñas de la página.  
  
-   Para arrastrar campos desde el panel Datos de informe hasta el panel Agrupación, no lo haga arrastrando el campo sobre otros elementos de informe en la superficie de diseño porque esto selecciona los demás elementos y se anula la selección de la región de datos de tablix. Arrastre el campo hacia abajo en el panel Datos de informe y, después, al panel Agrupación.  
  
###  <a name="Selecting"></a> Seleccionar elementos  
 Para seleccionar el objeto que desee en la superficie de diseño del informe, utilice la tecla ESC, el menú contextual, el panel Propiedades y el panel Agrupación.  
  
-   -   Presione ESC para recorrer la pila de elementos de informe que ocupan el mismo espacio en la superficie de diseño.  
  
    -   En algunos elementos de informe, pruebe a usar el menú contextual para seleccionar el elemento de informe o la parte del elemento de informe que desee.  
  
    -   El panel Propiedades muestra las propiedades de la selección actual.  
  
    -   Para trabajar con grupos de filas y grupos de columnas en una región de datos de tablix, seleccione el grupo en el panel Agrupación.  

  
##  <a name="ReportItems"></a> Trabajar con tipos específicos de elementos de informe  
  
###  <a name="Parameters"></a> Trabajar con parámetros  
  
-   El propósito principal de los parámetros de informe es filtrar los datos en el origen de datos y recuperar solo los necesarios para el informe.  
  
-   Para los parámetros de informe, busque un equilibrio entre permitir la interactividad y ayudar a un usuario a obtener los resultados que desea. Por ejemplo, puede establecer valores predeterminados para un parámetro con valores que sabe que son habituales.  
  
###  <a name="Text"></a> Trabajar con texto  
  
-   Cuando se pegan varias líneas en un cuadro de texto, el texto se agrega como una unidad de texto. Solo puede aplicar formato a las unidades de texto en conjunto. Para dar formato por separado a cada línea, inserte una nueva línea presionando RETORNO en la unidad de texto según sea necesario. A continuación, puede aplicar estilos y formato a cada línea de texto independiente en el cuadro de texto.  
  
-   Puede establecer las propiedades de formato y las acciones en un cuadro de texto o en el texto del marcador de posición en el cuadro de texto. Si hay solo una línea de texto, resulta más eficiente establecer las propiedades en el cuadro de texto que en el texto.  
  
###  <a name="Expressions"></a> Trabajar con expresiones  
  
-   Descripción de los formatos de expresiones simples y complejas Puede escribir el formato de expresión simple directamente en los cuadros de texto, en las propiedades del panel Propiedades o en ubicaciones de los cuadros de diálogo que acepten una expresión.
  
-   Cuando se crea una expresión, resulta útil crear cada parte de forma independiente y comprobar su valor. Después puede combinar todas las partes en una expresión final. Una técnica útil es agregar un cuadro de texto en una celda de matriz, mostrar cada parte de la expresión y establecer la visibilidad condicional en el cuadro de texto. Para controlar el estilo de borde y el color cuando se oculta el cuadro de texto, coloque primero el cuadro de texto en un rectángulo y, a continuación, establezca el estilo de borde y el color del rectángulo para que coincida con la matriz.  
  
###  <a name="Indicators"></a> Trabajar con indicadores  
  
-   De forma predeterminada, un indicador muestra al menos tres estados. Después de agregar un indicador a un informe, puede configurarlo agregando o quitando estados. Para facilitar la visualización, elija un indicador que varíe el color y la forma.  
  
##  <a name="Rendering"></a> Controlar la representación de elementos de informe en la página del informe  
  
-   En la superficie de diseño del informe, los elementos de informe aumentan de tamaño para dar cabida al contenido del conjunto de datos, expresión, subinforme o texto asociados.  
  
    -   Al colocar un elemento en la página del informe, la distancia entre el elemento y todos los elementos que comienzan a la derecha se convierte en la distancia mínima que se debe mantener cuando un elemento de informe crece horizontalmente. De forma similar, la distancia entre un elemento y el elemento anterior se convierte en la distancia mínima que debe mantenerse cuando el elemento superior aumenta de tamaño verticalmente.  
  
    -   Un elemento en un informe crece para acomodar los datos y aparta a los elementos del mismo nivel (elementos dentro del mismo contenedor primario) utilizando las reglas siguientes:  
  
    -   Cada elemento se desplaza hacia abajo para mantener el espacio mínimo entre él y los elementos que terminan por encima de él.  
  
    -   Cada elemento se desplaza hacia la derecha para mantener el espacio mínimo entre él y los elementos que terminan a su izquierda. En los sistemas con distribución de derecha a izquierda, los elementos se mueven a la izquierda para mantener el espacio mínimo entre él y los elementos que acaban a su derecha.  
  
    -   Los contenedores se expanden para alojar el crecimiento de los elementos secundarios. Para un elemento seleccionado, en el panel Propiedades, la propiedad Parent identifica el contenedor del elemento. También puede usar el panel Esquema del documento para ver la jerarquía de los elementos de informe.  
  
    -   La barra de herramientas **Diseño** ofrece varios botones para ajustar la alineación de los bordes, el centrado y el espaciado de los elementos de informe. Para habilitar la barra de herramientas **Diseño**, en el menú **Ver**, elija **Barras de herramientas** y haga clic en **Diseño**.  
  
-   Si va a guardar el informe como un archivo .pdf, el ancho del informe debe establecerse explícitamente en un valor que proporcione los resultados que desea incluir en el formato de archivo de exportación. Por ejemplo, establezca el ancho de página del informe exactamente en 20,16 cm y los márgenes izquierdos y derecho a 1,27 cm.  
  
-   Use **Diseño de impresión** y **Configurar página** en la barra de herramientas del visor de informes para mostrar una vista del informe con compatible con la impresión. Para ayudar a quitar páginas las horizontales no deseadas, haga lo siguiente:  
  
    1.  Quite todos los espacios en blanco adicionales entre las regiones de datos y en los bordes del informe.  
  
    2.  Reduzca los márgenes de página en el cuadro de diálogo **Propiedades del informe**.  
  
    3.  Use **Rectángulos** como contenedores para ayudar a controlar la manera en que los elementos de informe se representan en cada página.  
  
    4.  En los encabezados de columna, cambie la propiedad del cuadro de texto WritingMode para que use texto vertical.  
  
 La combinación de estas propiedades de comportamiento, el ancho y alto de los elementos de informe, el tamaño del cuerpo del informe, la definición del ancho y alto de página, la configuración de los márgenes del informe principal y la compatibilidad específica del representador con la paginación determinan qué elementos de informe pueden estar juntos en una página representada. 
 
## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
