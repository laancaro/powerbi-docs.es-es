---
title: Categorización de datos en Power BI Desktop
description: Categorización de datos en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 218a05c41c3befed8f8600f6a584560f5be92a1f
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709597"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Especificación de categorías de datos en Power BI Desktop
En Power BI Desktop, puede especificar la *categoría de datos* para una columna, de manera que Power BI Desktop sepa cómo debe tratar sus valores en una visualización.

Cuando Power BI Desktop importa datos, obtiene más información aparte de los propios datos, como los nombres de tabla y de columna, y si los datos son una clave principal. Con esa información, Power BI Desktop realiza algunas suposiciones sobre cómo proporcionar una buena experiencia predeterminada al crear una visualización.
Por ejemplo, cuando una columna tiene valores numéricos, es posible que quiera agregarla de alguna manera, por lo que Power BI Desktop la coloca en el área de **Valores** del panel **Visualizaciones**. O bien, para una columna con valores de fecha y hora en un gráfico de líneas, Power BI Desktop supone que la va a utilizar probablemente como un eje de la jerarquía de tiempo.

Sin embargo, existen algunos casos que son un poco más difíciles, como la ubicación geográfica. Tenga en cuenta la tabla siguiente desde una hoja de cálculo de Excel:

![](media/desktop-data-categorization/datacategorizationtable.png)

¿Power BI Desktop debe tratar los códigos en la columna **GeoCode** como una abreviatura para un país o un estado de EE. UU.?  No está claro, porque un código como este puede hacer referencia a cualquiera de ellos. Por ejemplo, AL puede significar Alabama o Albania, AR puede significar Arkansas o Argentina y CA puede significar California o Canadá. Esto es diferente cuando nos dirigimos a nuestro campo de código geográfico en un mapa. 

¿Power BI Desktop debe mostrar una imagen del mundo con países resaltados? ¿O debe mostrar una imagen de Estados Unidos con estados resaltados?  Puede especificar una categoría de datos como esta para los datos. La categorización de datos restringe aún más la información que Power BI Desktop puede usar para proporcionar las mejores visualizaciones.  

**Para especificar una categoría de datos**

1. En las vistas **Informes** o **Datos**, en la lista **Campos**, seleccione el campo que quiera ordenar por una categorización diferente.
2. En la cinta de opciones, en el área **Propiedades** de la pestaña **Modelado**, seleccione la flecha desplegable situada junto a **Categoría de datos**.  De esta forma, se muestra la lista de categorías de datos que puede elegir para la columna. Algunas selecciones pueden deshabilitarse si no funcionan con el tipo de datos actual de la columna.  Por ejemplo, si una columna es un tipo de datos binarios, Power BI Desktop no le permitirá elegir categorías de datos geográficos. 
3. Seleccione la categoría que quiera.

   ![](media/desktop-data-categorization/desktop-data-categorization.png)

También le podría interesar aprender sobre el [filtrado geográfico para aplicaciones móviles de Power BI](desktop-mobile-geofiltering.md).

