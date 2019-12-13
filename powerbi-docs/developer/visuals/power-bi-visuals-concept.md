---
title: Concepto de objetos visuales de Power BI
description: En este artículo se describe cómo se integran los objetos visuales con Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700855"
---
# <a name="power-bi-visual-concept"></a>Concepto de objetos visuales de Power BI

En el artículo se explica cómo interactúan con Power BI un usuario y un objeto visual, y cómo interactúa un usuario con un objeto visual de Power BI. En el diagrama verá qué acciones influyen directamente en el objeto visual o a través de Power BI (por ejemplo, cuando el usuario selecciona marcadores).

![Objeto visual de Power BI](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>El objeto visual se actualiza desde Power BI

El objeto visual tiene el método `update`, que suele contener la lógica principal del objeto visual y se encarga de representar el gráfico o de visualizar los datos.

Se obtienen más actualizaciones del método `update`.

### <a name="user-interacts-with-visual-through-power-bi"></a>El usuario interactúa con el objeto visual a través de Power BI

* El usuario abre el panel de propiedades de los objetos visuales.

    Power BI captura los objetos y propiedades compatibles del `capabilities.json` visual y, para recibir los valores reales de las propiedades, Power BI llama al método `enumerateObjectInstances` del objeto visual.

    El objeto visual tiene que devolver los valores reales de las propiedades.

    Para obtener más información, [lea sobre las funcionalidades de los objetos visuales](capabilities.md).

* [El usuario cambia la propiedad del objeto visual](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) en el panel Formato.

    Después de cambiar el valor de una propiedad, Power BI llama al método `update` del objeto visual y pasa al método update el nuevo objeto `options` con los nuevos valores de los objetos.

    Para obtener más información, [lea sobre los objetos y las propiedades del objeto visual](objects-properties.md).

* El usuario cambia el tamaño del objeto visual.

    Cuando un usuario cambia el tamaño del objeto visual, Power BI llama al método `update` con el nuevo objeto `option`. Las opciones tienen el objeto `viewport` anidado con el nuevo ancho y alto del objeto visual.

* El usuario aplica el filtro de informe, de página o de objeto visual.

    Power BI filtra los datos según las condiciones del filtro y llama al método `update` del objeto visual para proporcionar nuevos datos al objeto visual.

    El objeto visual obtiene una nueva actualización de `options` con datos nuevos en uno de los objetos anidados. Depende de la configuración de la asignación de la vista de datos del objeto visual.

    Para obtener más información, [lea sobre las asignaciones de vistas de datos](dataview-mappings.md).

* El usuario selecciona un punto de datos en otro objeto visual del informe.

    Power BI filtra o resalta los puntos de datos seleccionados y llama al método `update` del objeto visual.

    El objeto visual obtiene nuevos datos filtrados o los mismos datos con una matriz de resaltados.

    Para obtener más información, [lea sobre cómo resaltar datos en los objetos visuales](highlight.md).

* El usuario selecciona un marcador en el panel de marcadores del informe.

    Pueden pasar dos cosas:

    1. Power BI llama a la función pasada que ha registrado el método `registerOnSelectionCallback` y la función de devolución de llamada obtiene matrices de selecciones para el marcador correspondiente.

    2. Power BI llama al método `update` con el objeto de filtro correspondiente dentro de `options`.

    En ambos casos, el objeto visual tiene que cambiar el estado de visualización según las selecciones o el objeto de filtro recibidos.

    Para obtener más información sobre los marcadores, [lea sobre cómo administrar los marcadores](filter-api.md).

    Para obtener más información sobre los filtros, [lea cómo los objetos visuales de Power BI pueden filtrar los datos en otros objetos visuales](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>El usuario interactúa directamente con el objeto visual

* El usuario mantiene el puntero sobre el elemento de datos

    El objeto visual puede mostrar información adicional sobre el punto de datos mediante la API de información sobre herramientas de Power BI.
    El usuario mantiene el puntero sobre el elemento visual. El objeto visual puede controlar el evento y mostrar los datos en el elemento de información sobre herramientas.

    El objeto visual puede mostrar la información sobre herramientas estándar o la información sobre herramientas de página de informe.

    Para obtener más información, lea la guía sobre [cómo agregar información sobre herramientas](add-tooltips.md).

* El usuario cambia las propiedades del objeto visual (por ejemplo, el usuario expande el árbol y el objeto visual guarda el estado en las propiedades)

    El objeto visual puede guardar los valores de las propiedades mediante la API de Power BI. Por ejemplo, cuando el usuario interactúa con el objeto visual. Así mismo, el objeto visual debe guardar o actualizar los valores de las propiedades. El objeto visual puede llamar al método `presistProperties`.

* El usuario hace clic en un vínculo de dirección URL.

    De forma predeterminada, el objeto visual no puede abrir la dirección URL. Para abrir la dirección URL en la pestaña nueva, el objeto visual debe llamar al método `launchURL` y pasar la dirección URL como parámetro.

    Para obtener más información, lea sobre la [API de inicio de URL](launch-url.md).

* El usuario aplica el filtro mediante el objeto visual

    El objeto visual llama a `applyJSONFilter` y pasa las condiciones de filtro para filtrar los datos en otro objeto visual.

    El objeto visual puede usar varios tipos de filtro (por ejemplo, un filtro básico, un filtro avanzado o un filtro de tupla).

    Para obtener más información sobre los filtros, [lea cómo los objetos visuales de Power BI pueden filtrar los datos en otros objetos visuales](filter-api.md).

* El usuario hace clic o selecciona elementos del objeto visual.

    Para obtener más información sobre las selecciones, [lea sobre cómo interactúan los objetos visuales](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>El objeto visual interactúa con Power BI

* El objeto visual solicita más datos de Power BI.

    El objeto visual puede procesar los datos parte por parte. El método de API FetchMoreData solicita el siguiente fragmento del conjunto de datos.

    Para obtener más información sobre `fetchMoreData`, [lea sobre cómo capturar más datos de Power BI](fetch-more-data.md)

* Servicio de eventos

    Power BI puede exportar los informes a PDF o enviarlos por correo electrónico (solo se admiten los objetos visuales certificados). Para notificar a Power BI que ha concluido la representación y que está listo para capturar PDF/correos electrónicos, el objeto visual debe llamar a la API de representación de eventos.

    Para obtener más información, [lea sobre cómo exportar informes de Power BI a PDF](../../consumer/end-user-pdf.md)

    Puede obtener más información [sobre el servicio de eventos](event-service.md)

## <a name="next-steps"></a>Pasos siguientes

¿Es un desarrollador web interesado en crear sus propias visualizaciones y agregarlas a AppSource? Consulte [Desarrollo de objetos visuales de Power BI](./custom-visual-develop-tutorial.md) y obtenga información sobre cómo [publicar objetos visuales de Power BI en AppSource](../office-store.md).
