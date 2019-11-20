---
title: Compatibilidad de la extensión de representación en PDF con ISO 14289-1 - Power BI Report Server
description: En este documento se describe la compatibilidad de la extensión de representación en PDF de Power BI Report Server y SQL Reporting Services con las especificaciones ISO 14289-1 (PDF/UA).
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: c800ee995bc3c03b3cbcda91503e6dea9495f6b5
ms.sourcegitcommit: 721cf375627b010e8ad12c4c668295f38d450a17
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73638089"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server"></a>Compatibilidad de la extensión de representación en PDF con ISO 14289-1: Power BI Report Server 

Se aplica a: Power BI Report Server y SQL Reporting Services

En este documento se describe la compatibilidad de la extensión de representación en PDF de Power BI Report Server y SQL Reporting Services con las especificaciones [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/).

> [!NOTE]
> Para guardar o imprimir estas notas del producto, haga clic en **Imprimir** en el explorador y después en **Guardar como PDF**.

## <a name="1--scope"></a>1.  Ámbito

No aplicable

## <a name="2--normative-references"></a>2.  Referencias de normativas

No aplicable

## <a name="3--terms-and-definitions"></a>3.  Términos y definiciones

No aplicable

## <a name="4--notation"></a>4.  Notación

No aplicable

## <a name="5-version-identification"></a>5. Identificación de la versión

La extensión de representación en PDF proporciona compatibilidad con PDF/UA, tal y como se describe en este documento. En algunos casos, que se indican a continuación, es el usuario el que debe tomar medidas para asegurarse de que un PDF es totalmente compatible con PDF/UA.  Esperamos que el usuario agregue la versión de PDF/UA adecuada y los identificadores de cumplimiento como último paso de este proceso, lo que indica que se ha realizado el trabajo necesario para que el PDF sea totalmente compatible con PDF/UA.

Todo lo que se muestra en este documento se basa en la representación de un documento PDF con la configuración de información del dispositivo AccessiblePdf establecida en `true`. En algunos casos, las limitaciones de cumplimiento se deben a limitaciones en el lenguaje RDL (Report Definition Language).

## <a name="6--conformance-requirements"></a>6.  Requisitos de conformidad

|     Criterios     |     Característica de compatibilidad     |     Notas      |
|----|--------|--------|
|    6.1 General    |                 Admitido    |    La extensión de representación en PDF crea la versión 1.7 de PDF.    |
|    6.2 Archivos conformes    |                 Se admiten con excepciones    |    Vea los comentarios en la sección 7. Requisitos de formato de archivo.    |
|    6.3 Lector conforme    |     No aplicable     |         |
|    6.4 Tecnología de asistencia conforme    |     No aplicable     |         |

## <a name="7--file-format-requirements"></a>7.  Requisitos de formato de archivo

|     Criterios     |     Característica de compatibilidad     |     Notas      |
|-----|-------|------------------------|
|    7.1 General    |                 Se admiten con excepciones    |    Todo el contenido real se etiquetará como se define en ISO 32000-1:2008, 14.8. Los artefactos (ISO 32000-1:2008, 14.8.2.2.2) no se etiquetarán en el árbol de estructura. <li> La extensión de representación en PDF no ofrece la flexibilidad de marcar explícitamente elementos individuales como artefactos, por lo que en su lugar creará un artefacto todo lo que se asigna a los criterios de ISO 32000-1:2008, 14.8.2.2.2.<br>El contenido se marcará en el árbol de estructura con etiquetas semánticamente adecuadas en un orden de lectura lógico. <br> **Nota** 4 WCAG 2.0, la directriz 1.4 explica los problemas relacionados con el contraste, el color y otros formatos de accesibilidad. <br><li> El usuario debe asegurarse de que su documento no esté sujeto a estos problemas. <br>Las etiquetas estándar definidas en ISO 32000-1:2008, 14.8.4, no se reasignarán. <li> La extensión de representación en PDF no reasigna las etiquetas estándar. Los documentos comienzan con el elemento raíz del documento. <br>Los archivos que reclaman la conformidad con este estándar internacional deben tener false como valor de Suspects (ISO 32000-1:2008, tabla 321). <li> La extensión de representación en PDF no tiene la entrada Suspects. Esta propiedad es opcional.    |
|    7.2 Texto    |                 Se admite con excepciones    |    El contenido se etiquetará en el orden lógico de lectura. Se utilizará la etiqueta más adecuada semánticamente para cada elemento lógico del contenido del documento. <br><li> La extensión de representación en PDF muestra el contenido en orden lógico de lectura en la medida de lo posible.<br>Los códigos de caracteres se asignan a Unicode, tal como se describe en ISO 32000-1:2008, 14.8.2.4.2. Los caracteres no incluidos en la especificación Unicode pueden utilizar el área de uso privado Unicode o declarar otra codificación de caracteres. <br>El lenguaje natural se declarará como se describe en ISO 32000-1:2008, 14.9.2 o en ISO 32000-1:2008, 7.9.2. Se declararán los cambios en el lenguaje natural. Los cambios en el lenguaje natural dentro de las cadenas de texto (por ejemplo, en las descripciones alternativas) se declararán mediante un identificador de idioma, tal como se describe en ISO 32000-1:2008, 14.9.2.2. <br><li> La extensión de representación en PDF solo declara el lenguaje natural en el nivel de documento    |
|    7.3 Gráficos    |                 Se admite con excepciones    |    Los objetos gráficos, a excepción de los objetos de texto, se etiquetarán con una etiqueta de ilustración tal y como se describe en ISO 32000-1:2008, 14.8.4.5, Tabla 340. Si se cumple alguna de las siguientes excepciones, el gráfico se etiquetará como un artefacto: <br><li> el gráfico no representa contenido significativo o bien <li>  el gráfico aparece como fondo de una anotación de vínculo, en cuyo caso, el texto alternativo del vínculo debe describir tanto el gráfico como el vínculo. <li> La extensión de representación en PDF etiqueta los objetos gráficos con la etiqueta de la ilustración. <br>El título que acompaña a una ilustración se etiqueta con una etiqueta de título. <li> La extensión de representación en PDF no etiqueta actualmente los títulos en las ilustraciones con una etiqueta de título. <br>Las etiquetas de las ilustraciones incluirán una representación alternativa o un texto de reemplazo que represente el contenido marcado con la etiqueta de la ilustración como se indica en ISO 32000-1:2008, 14.7.2, Tabla 323. <br>**Nota** 1 Vea también WCAG 2.0, Directriz 1.1. <br>Si el texto representado en un gráfico no es texto en un lenguaje natural diseñado para ser leído por un lector humano, se proporcionará un texto alternativo que describa la naturaleza o el propósito del gráfico. <br>**Nota** 2 El texto que es un ejemplo del tipo o del sistema de escritura utilizados por un idioma son ejemplos que no están en un lenguaje natural.   La extensión de representación en PDF admite texto alternativo en las ilustraciones, aunque depende del usuario agregar el texto alternativo. <br>Nota adicional relacionada con el atributo BBox: <br><li> La extensión de representación en PDF no escribe actualmente el atributo BBox. <li> Una solución alternativa consiste en cambiar las etiquetas de las ilustraciones manualmente como nuevas o como artefactos.    |
|    7.4 Encabezados    |                 No aplicable    |    RDL no admite la marca de los encabezados de ningún modo. Es el usuario quien debe etiquetarlos según corresponda.    |
|    7.5 Tablas    |                 Se admite con excepciones    |    Las tablas deben incluir encabezados. Los encabezados de tabla se etiquetarán de acuerdo con las normas ISO 32000-1:2008, Tabla 337 y Tabla 349. <br>**Nota** 1 Las tablas pueden contener encabezados de columna, encabezados de fila o ambos. <br>**Nota** 2 Hay que incluir el máximo de información posible sobre la estructura de las tablas cuando se confía en la tecnología de asistencia. Los encabezados desempeñan un papel clave a la vez que proporcionan información estructural. <br><li> Es el usuario quien debe incluir los encabezados en sus tablas. RDL y la extensión de representación en PDF proporcionan compatibilidad con los encabezados de fila. <br>  Los elementos de estructura del tipo TH deben tener un atributo Scope, de ámbito.   <li> La extensión de representación en PDF incluye un atributo de ámbito en los elementos TH de columna y de miembros de fila, pero no para las celdas de esquina.<br>Las estructuras de etiquetado de tablas solo se usarán para etiquetar el contenido que se presenta dentro de las relaciones lógicas de filas y columnas.   <li> Esto depende de cómo el usuario haya elegido usar las tablas en su RDL.    |
|    7.6 Listas    |                 No aplicable    |    RDL no admite la marca de listas. En RDL, son estructuralmente una tabla con una sola celda de tabla. <br>Es el usuario quien debe etiquetarlas según corresponda.    |
|    7.7 Expresiones matemáticas    |                 Se admite con excepciones    |    Todas las expresiones matemáticas deben encerrarse dentro de una etiqueta de fórmula, tal y como se detalla en ISO 32000-1:2008, 14.8.4.5 y deben tener un atributo Alt. <br><li> La extensión de representación en PDF no incluye actualmente expresiones matemáticas dentro de una etiqueta de fórmula. <br>Los requisitos relativos a la asignación de caracteres a Unicode se aplican a las expresiones matemáticas que se establecen en ISO 32000-1:2008, 9.10.2 y 14.8.2.4. <br><li> Esto se admite en la extensión de representación en PDF.    |
|    7.8 Encabezados y pies de página    |                 Admitido    |    Los encabezados y pies de página en ejecución se identificarán como artefactos de paginación y se clasificarán como subtipos de encabezado o de pie de página según ISO 32000-1:2008, 14.8.2.2.2, Tabla 330. <br><li> Los encabezados y pies de página se tratan y etiquetan como artefactos.    |
|    7.9 Notas y referencias    |                 No aplicable    |    La extensión de representación en PDF no admite la marca de notas y referencias. <br>Es el usuario quien debe etiquetarlas según corresponda.    |
|    7.10 Contenido opcional    |                 No aplicable    |         |
|    7.11 Archivos insertados    |                 No aplicable    |         |
|    7.12 Subprocesos de artículos    |                 No aplicable    |         |
|    7.13 Firmas digitales    |                 No aplicable    |         |
|    7.14 Formularios no interactivos    |                 No aplicable    |         |
|    7.15 XFA    |                 No aplicable    |         |
|    7.16 Seguridad    |                 No aplicable    |         |
|    7.17 Navegación    |                 Admitido    |    Un documento debe incluir un esquema de documento que coincida con el orden de lectura y el nivel de destinos de navegación (ISO 32000-1:2008, 12.3.3). <br><li> RDL admite marcadores para un elemento de informe, pero el usuario debe seleccionar esta opción. Después, la extensión de representación en PDF representa esos marcadores como un esquema de documento. <br>Si está presente, las entradas del árbol de números PageLabels (ISO 32000-1:2008, 7.7.2, Tabla 28) deben ser semánticamente apropiadas. <br><li> La extensión de representación en PDF no incluye un árbol de números PageLabels.    |
|    7.18 Anotaciones    |                 No aplicable    |    RDL no admite anotaciones    |
|    7.21 Fuentes    |                 Admitido    |         |
|    7.21.1 General    |                 Admitido    |         |
|    7.21.2 Tipos de fuente    |                 Admitido    |         |
|    7.21.3 Fuentes compuestas    |                 Admitido    |         |
|    7.21.3.1 General    |                 Admitido    |         |
|    7.21 3.2 CIDFonts    |                 Admitido    |         |
|    7.21.3.3 CMaps    |                 Admitido    |         |
|    7.21.4 Inserción    |                 Admitido    |         |
|    7.21.4.1 General    |                 Admitido    |         |
|    7.21.4.2 Inserción de subconjuntos    |                 Admitido    |         |
|    7.21.5 Métricas de fuentes    |                 Admitido    |         |
|    7.21.6 Codificación de caracteres    |                 Admitido    |         |
|    7.21.7 Mapas de caracteres Unicode    |                 Admitido    |         |
|    7.21.8 Uso del glifo .notdef    |                 Admitido    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Requisitos de los lectores conformes

No aplicable

## <a name="9--at-requirements"></a>9.  Requisitos de AT

No aplicable

## <a name="disclaimer"></a>Declinación de responsabilidades

© 2017 Microsoft Corporation. Todos los derechos reservados. Los nombres de las empresas y productos reales mencionados aquí pueden ser marcas comerciales de sus respectivos propietarios. La información contenida en este documento representa la vista actual de Microsoft Corporation sobre los problemas descritos en la fecha de la publicación. Microsoft no puede garantizar la exactitud de la información presentada después de la fecha de publicación. Microsoft actualiza periódicamente sus sitios web con información nueva sobre la accesibilidad de los productos a medida que esa información está disponible.

La personalización del producto anula esta declaración de conformidad de Microsoft. Póngase en contacto con los proveedores de tecnología de asistencia (AT) para conocer las especificaciones de compatibilidad de determinados productos.

Este documento tiene fines meramente informativos. MICROSOFT NO OTORGA NINGUNA GARANTÍA, NI EXPRESA NI IMPLÍCITA, EN ESTE DOCUMENTO.


## <a name="next-steps"></a>Pasos siguientes
[Información general de administrador](admin-handbook-overview.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

