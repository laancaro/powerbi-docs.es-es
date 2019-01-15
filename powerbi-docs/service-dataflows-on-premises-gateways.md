---
title: Uso de flujos de datos con orígenes de datos locales
description: Aprenda a usar datos locales en flujos de datos.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 82c8bbb5361730b306cacd14dc9598ca12035027
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54276477"
---
# <a name="using-dataflows-with-on-premises-data-sources-preview"></a>Uso de flujos de datos con orígenes de datos locales (versión preliminar)

Con **flujos de datos**, puede crear una colección de datos de varios orígenes, limpiar los datos, transformarlos y cargarlos en el almacenamiento de Power BI. Al crear el flujo de datos, puede que desee usar orígenes de datos locales. En este artículo se explican los requisitos asociados con la creación de flujos de datos y cómo debe configurarse **Enterprise Gateway** para habilitar dichas conexiones.

![Flujos de datos y puertas de enlace](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

> [!NOTE]
> La funcionalidad de flujos de datos se encuentra en versión preliminar y está sujeta a cambios y actualizaciones antes de la disponibilidad general.
 
## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>Configuración de Enterprise Gateway para usarlo con flujos de datos

Para usar un origen de datos local en un flujo de datos, cualquier usuario que crea el flujo de datos debe tener **Enterprise Gateway** instalado y configurado. El usuario que crea el flujo de datos también debe ser administrador de Enterprise Gateway para poder usar esa puerta de enlace para un flujo de datos.

> [!NOTE]
> Los flujos de datos solo se admiten con Enterprise Gateway.

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>Uso de un origen de datos local en un flujo de datos

Al crear un flujo de datos, seleccione un origen de datos local en la lista de orígenes de datos, como se muestra en la siguiente imagen.

![Elección de un origen de datos local](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

Una vez realizada la selección, se le pedirá que proporcione los detalles de conexión de Enterprise Gateway que se usarán para tener acceso a los datos locales. Debe seleccionar la puerta de enlace y proporcionar las credenciales de la puerta de enlace seleccionada. En la lista desplegable solo aparecen las puertas de enlace de las que el usuario es administrador.

![Proporcionar los detalles de conexión](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>Supervisión de la puerta de enlace

Puede supervisar Enterprise Gateway para un flujo de datos de la misma forma en que supervisa las puertas de enlace de un conjunto de datos.

En la pantalla de configuración del flujo de datos de Power BI, puede supervisar el estado de la puerta de enlace de un flujo de datos y asignar una puerta de enlace al flujo de datos, como se muestra en la imagen siguiente.

![Supervisión de la puerta de enlace](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>Cambio de una puerta de enlace

Puede cambiar la instancia de Enterprise Gateway utilizada para un flujo de datos determinado de dos formas:

1. **Desde la herramienta de creación**: puede cambiar la puerta de enlace asignada a todas las consultas mediante la herramienta de creación de flujo de datos.

    > [!NOTE]
    > El flujo de datos intentará encontrar o crear los orígenes de datos necesarios mediante la nueva puerta de enlace. Si no puede hacerlo, podrá cambiar la puerta de enlace hasta que todos los flujos de datos necesarios estén disponibles desde la puerta de enlace seleccionada.

2. **Desde la pantalla de configuración**: puede cambiar la puerta de enlace asignada con el uso de la pantalla de configuración para el flujo de datos en el servicio Power BI.

Para obtener más información sobre Enterprise Gateway, vea [Puerta de enlace de datos local](service-gateway-onprem.md).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Hay algunas limitaciones conocidas para el uso de Enterprise Gateway y de los flujos de datos:

* Cada flujo de datos puede usar solo una puerta de enlace. Por lo tanto, todas las consultas se deberían configurar utilizando la misma puerta de enlace.
* Cambiar la puerta de enlace repercute en todo el flujo de datos.
* Si se necesitan varias puertas de enlace, el procedimiento recomendado es crear varios flujos de datos (uno para cada puerta de enlace) y usar las funcionalidades de referencia a procesos o entidades para unificar los datos.
* Los flujos de datos solo se admiten con Enterprise Gateway. Las puertas de enlace personales no estarán disponibles para seleccionarlas en las listas desplegables ni en las pantallas de configuración.


## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporciona información sobre el uso de los orígenes de datos locales para los flujos de datos y sobre cómo usar y configurar las puertas de enlace para acceder a dichos datos. Los siguientes artículos también pueden resultarle útiles.

* [Preparación de datos de autoservicio con flujos de datos](service-dataflows-overview.md)
* [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
* [Uso de entidades calculadas en Power BI Premium (versión preliminar)](service-dataflows-computed-entities-premium.md)
* [Recursos de desarrollador para flujos de datos de Power BI](service-dataflows-developer-resources.md)

Para obtener más información sobre Power Query y la actualización programada, puede leer estos artículos:
* [Información general sobre consultas en Power BI Desktop](desktop-query-overview.md)
* [Configuración de la actualización programada](refresh-scheduled-refresh.md)

Para más información sobre Common Data Service, puede leer su artículo de introducción:
* [Introducción a Common Data Service](https://docs.microsoft.com/powerapps/common-data-model/overview)

