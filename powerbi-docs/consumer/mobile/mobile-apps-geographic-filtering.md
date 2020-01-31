---
title: Filtrar un informe por ubicación geográfica en una aplicación móvil de Power BI
description: Aprenda cómo filtrar un informe por ubicación geográfica en las aplicaciones móviles de Microsoft Power BI, si el propietario del informe estableció etiquetas geográficas.
author: mshenhav
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: mshenhav
ms.openlocfilehash: 002ddeac915b2b2b67570e8b4078a175de09aaef
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538207"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Filtrar un informe por ubicación geográfica en las aplicaciones móviles de Power BI
Se aplica a:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Teléfono Android](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Tableta Android](./media/mobile-apps-view-dashboard/android-tablet-logo-50-px.png) | ![Teléfono Windows](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Teléfonos Android |Tabletas Android |Teléfonos con Windows 10 |

Al examinar un informe de Power BI en su dispositivo móvil, ¿ve un pequeño icono de chincheta en la esquina superior derecha? Si es así, puede filtrar ese informe según su ubicación geográfica.

> [!NOTE]
> Solo puede filtrar por ubicación si los nombres geográficos del informe están en inglés; por ejemplo, "New York City" o "Germany". Las tabletas y los equipos Windows 10 no admiten el filtrado geográfico, pero los teléfonos Windows 10 sí.
> 
> 

## <a name="filter-your-report-by-your-geographic-location"></a>Filtrar un informe por ubicación geográfica
1. Abra un informe en la aplicación móvil Power BI de su dispositivo móvil.
2. Si el informe contiene datos geográficos, podrá ver un mensaje preguntándole si desea permitir que Power BI acceda a su ubicación. Haga clic en **Permitir** y, después, pulse en **Permitir** otra vez.
3. Pulse el icono de chincheta ![Icono de chincheta](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). Puede filtrar por ciudad, estado o provincia, o país o región, en función de los datos del informe. El filtro solo muestra las opciones que coincidan con la ubicación actual.
   
    ![Filtro del icono de chincheta](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>¿Por qué no veo etiquetas de ubicación en un informe?
Para ver las etiquetas de ubicación, se deben cumplir estas tres condiciones. 

* La persona que ha creado el informe en Power BI Desktop debe tener [los datos geográficos clasificados](../../desktop-mobile-geofiltering.md) para al menos una columna, como Ciudad, Estado, o País o Región.
* Se encuentra en una de las ubicaciones que tiene datos en esa columna.
* Usa uno de estos dispositivos móviles:
  * iOS (iPad, iPhone, iPod).
  * Android (teléfono, tableta).
  * Teléfono Windows 10 (otros dispositivos Windows 10, como tabletas y equipos, no admiten el filtrado geográfico).

Obtenga más información sobre cómo [configurar el filtrado geográfico](../../desktop-mobile-geofiltering.md) en Power BI Desktop.

### <a name="next-steps"></a>Pasos siguientes
* [Get Power BI data from the real world with the mobile apps](mobile-apps-data-in-real-world-context.md) (Obtener datos de Power BI del mundo real con las aplicaciones móviles)
* [Categorización de datos en Power BI Desktop](../../desktop-data-categorization.md) 
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

