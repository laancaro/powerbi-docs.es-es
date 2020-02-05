---
title: Conceptos sobre los objetos visuales de Power BI
description: En este artículo se describe cómo los objetos visuales se integran con Power BI y cómo los usuarios pueden interactuar con ellos.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bb0834527ba23c6cfcc155cc65cd0318b296ba84
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "75925590"
---
# <a name="visuals-in-power-bi"></a>Objetos visuales en Power BI

En este artículo se describe cómo los objetos visuales se integran con Power BI y cómo los usuarios pueden interactuar con ellos. 

En la ilustración siguiente se muestra cómo se procesan en Power BI las acciones comunes basadas en objetos visuales que realiza un usuario, como la selección de un marcador.

![Diagrama de acciones de objetos visuales de Power BI](./media/visual-concept.svg)

## <a name="visuals-get-updates-from-power-bi"></a>Los objetos visuales obtienen actualizaciones de Power BI

Un objeto visual llama a un método `update` para obtener actualizaciones de Power BI. Normalmente, el método `update` contiene la lógica principal del objeto visual y es responsable de representar un gráfico o de visualizar datos.

Las actualizaciones se desencadenan cuando el objeto visual llama al método `update`.

## <a name="action-and-update-patterns"></a>Patrones de acción y actualización

Las acciones y posteriores actualizaciones de los objetos visuales de Power BI se producen en uno de estos tres patrones:

* El usuario interactúa con el objeto visual mediante Power BI.
* El usuario interactúa directamente con el objeto visual.
* El objeto visual interactúa con Power BI.

### <a name="user-interacts-with-a-visual-through-power-bi"></a>El usuario interactúa con un objeto visual mediante Power BI

* Un usuario abre el panel de propiedades del objeto visual.

    Cuando un usuario abre el panel de propiedades del objeto visual, Power BI captura los objetos y las propiedades admitidos del archivo *capabilities.json*. Para recibir valores reales de las propiedades, Power BI llama al método `enumerateObjectInstances` del objeto visual. El objeto visual devuelve los valores reales de las propiedades.

    Para más información, consulte [Funcionalidades y propiedades de objetos visuales de Power BI](capabilities.md).

* Un usuario [cambia la propiedad de un objeto visual](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) en el panel de formato.

    Cuando un usuario cambia el valor de una propiedad en el panel de formato, Power BI llama al método `update` del objeto visual. Power BI pasa el nuevo objeto `options` al método `update`. Los objetos contienen los nuevos valores.

    Para obtener más información, vea [Objetos y propiedades de objetos visuales de Power BI](objects-properties.md).

* El usuario cambia el tamaño del objeto visual.

    Cuando un usuario cambia el tamaño de un objeto visual, Power BI llama al método `update` con el nuevo objeto `options`. Los objetos `options` tienen objetos `viewport` anidados que contienen el nuevo ancho y alto del objeto visual.

* Un usuario aplica un filtro en el nivel de informe, página u objeto visual.

    Power BI filtra los datos en función de las condiciones de filtro. Power BI llama al método `update` del objeto visual para actualizar este con nuevos datos.

    El objeto visual obtiene una nueva actualización de los objetos `options` cuando hay nuevos datos en uno de los objetos anidados. La forma en que se produzca la actualización depende de la configuración de la asignación de la vista de datos del objeto visual.

    Para obtener más información, consulte [Información sobre las asignaciones de vistas de datos en objetos visuales de Power BI](dataview-mappings.md).

* Un usuario selecciona un punto de datos de otro objeto visual del informe.

    Cuando un usuario selecciona un punto de datos de otro objeto visual del informe, Power BI filtra o resalta los puntos de datos seleccionados y llama al método de `update` del objeto visual. El objeto visual obtiene nuevos datos filtrados o los mismos datos con una matriz de resaltados.

    Para obtener más información, consulte [Resaltado de puntos de datos en objetos visuales de Power BI](highlight.md).

* Un usuario selecciona un marcador en el panel de marcadores del informe.

    Cuando un usuario selecciona un marcador en el panel de marcadores del informe, puede tener lugar una de las dos acciones siguientes:

    * Power BI llama a una función que se pasa y se registra mediante el método `registerOnSelectionCallback`. La función de devolución de llamada obtiene matrices de selecciones para el marcador correspondiente.

    * Power BI llama al método `update` con un objeto `filter` correspondiente dentro del objeto `options`.

    En cualquier caso, el objeto visual debe cambiar su estado de acuerdo con las selecciones recibidas o el objeto `filter`.

    Para más información sobre los marcadores y los filtros, consulte [Visual Filters API en objetos visuales de Power BI](filter-api.md).

### <a name="user-interacts-with-the-visual-directly"></a>El usuario interactúa directamente con el objeto visual

* Un usuario mantiene el mouse sobre un elemento de datos.

    Un objeto visual puede mostrar más información sobre un punto de datos mediante la API de información sobre herramientas de Power BI. Cuando un usuario mantiene el mouse sobre un elemento visual, el objeto visual puede administrar el evento y mostrar datos sobre el elemento de información sobre herramientas asociado. El objeto visual puede mostrar información sobre herramientas estándar o información sobre herramientas de página de informe.

    Para más información, consulte [Información sobre herramientas en objetos visuales de Power BI](add-tooltips.md).

* Un usuario cambia las propiedades del objeto visual. (Por ejemplo, un usuario expande un árbol y el objeto visual guarda el estado en sus propiedades).

    Un objeto visual puede guardar los valores de las propiedades mediante la API de Power BI. Por ejemplo, cuando un usuario interactúa con el objeto visual y este necesita guardar o actualizar los valores de propiedades, el objeto visual puede llamar al método `presistProperties`.

* Un usuario selecciona una dirección URL.

    De forma predeterminada, un objeto visual no puede abrir directamente una dirección URL. En su lugar, para abrir una dirección URL en una nueva pestaña, el objeto visual puede llamar al método `launchUrl` y pasar la dirección URL como un parámetro.

    Para más información, consulte [Creación de una URL de inicio](launch-url.md).

* Un usuario aplica un filtro mediante el objeto visual.

    Un objeto visual puede llamar al método `applyJsonFilter` y pasar condiciones para filtrar los datos de otros objetos visuales. Hay varios tipos de filtros disponibles, incluidos los filtros básico, avanzado y de tupla.

    Para más información, consulte [Visual Filters API en objetos visuales de Power BI](filter-api.md).

* Un usuario selecciona elementos del objeto visual.

    Para más información sobre las selecciones de un objeto visual de Power BI, consulte [Incorporación de interactividad mediante las selecciones de objetos visuales de Power BI](selection-api.md).

### <a name="visual-interacts-with-power-bi"></a>El objeto visual interactúa con Power BI

* Un objeto visual solicita más datos de Power BI.

    Un objeto visual procesa los datos parte por parte. El método de API `fetchMoreData` solicita el siguiente fragmento del conjunto de datos.

    Para más información, consulte [Captura de más datos desde Power BI](fetch-more-data.md).

* Los desencadenadores del servicio de eventos.

    Power BI puede exportar un informe a PDF o enviar un informe por correo electrónico (se aplica solo a los objetos visuales certificados). Para notificar a Power BI que la representación ha finalizado y que el objeto visual está listo para capturarse como PDF o correo electrónico, el objeto visual debe llamar a la API de eventos de representación.

    Para más información, consulte [Exportación de informes de Power BI a PDF](../../consumer/end-user-pdf.md).

    Para información sobre el servicio de eventos, consulte [Representación de eventos en objetos visuales de Power BI](event-service.md).

## <a name="next-steps"></a>Pasos siguientes

¿Está interesado en crear visualizaciones y agregarlas a Microsoft AppSource? Consulte estos artículos:

* [Desarrollo de un objeto visual de Power BI](./custom-visual-develop-tutorial.md)
* [Publicación de objetos visuales de Power BI en el Centro de partners](../office-store.md)
