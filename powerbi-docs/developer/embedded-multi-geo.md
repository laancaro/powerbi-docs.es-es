---
title: Compatibilidad de Multi-Geo con Power BI Embedded
description: Conozca cómo puede implementar contenido en centros de datos situados en regiones distintas de la región principal de Power BI Embedded.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 57f01a458bad36c73a01adb1bc62bfd5a055a337
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61345006"
---
# <a name="multi-geo-support-for-power-bi-embedded"></a>Compatibilidad de Multi-Geo con Power BI Embedded

La **compatibilidad de Multi-Geo con Power BI Embedded** significa que los ISV y las organizaciones que compilan aplicaciones con Power BI Embedded para insertar análisis en sus aplicaciones ahora pueden implementar sus datos en diferentes regiones de todo el mundo.

Ahora los clientes que usan **Power BI Embedded** pueden configurar una **capacidad A** mediante **Multi-Geo**, según las mismas características y limitaciones que [admite Power BI Premium mediante Multi-Geo](../service-admin-premium-Multi-Geo.md).

## <a name="creating-new-power-bi-embedded-capacity-resource-with-multi-geo"></a>Creación de nuevos recurso de capacidad de Power BI Embedded con Multi-Geo

En la pantalla **Crear recurso**, debe elegir la ubicación de su capacidad. Hasta ahora, estaba limitado solo a la ubicación del inquilino de Power BI, de modo que solo había una ubicación disponible. Con Multi-Geo, puede elegir entre diferentes regiones para implementar su capacidad.

![Configuración de Multi-Geo para Power BI Embedded](media/embedded-multi-geo/pbie-multi-geo-setup.png)

Tenga en cuenta que al abrir el menú desplegable de ubicación, el inquilino principal es la selección predeterminada.
  
![Ubicación predeterminada de Multi-Geo para Power BI Embedded](media/embedded-multi-geo/pbie-multi-geo-default-location.png)

Al elegir una ubicación diferente, un mensaje le pide que confirme la selección.

![Cambio de ubicación](media/embedded-multi-geo/pbie-multi-geo-location-change.png)

## <a name="view-capacity-location"></a>Visualización de la ubicación de capacidad

Puede ver fácilmente la ubicación de las capacidades cuando vaya a la página principal de administración de Power BI Embedded en Azure Portal.

![Capacidades con ubicaciones diferentes](media/embedded-multi-geo/pbie-multi-geo-location-different.png)

También está disponible en el Portal de administración en Powerbi.com. En el Portal de administración, elija "Configuración de la capacidad" y, a continuación, cambie a la pestaña "Power BI Embedded".

![Visualización en el Portal de administración](media/embedded-multi-geo/pbie-multi-geo-admin-portal.png)

[Más información sobre la creación de capacidades con Power BI Embedded.](azure-pbie-create-capacity.md)

## <a name="manage-existing-capacities-location"></a>Administración de la ubicación de capacidades existentes

No puede cambiar una ubicación de recursos de Power BI Embedded después de crear una capacidad.

Para mover el contenido de Power BI a una región diferente, siga estos pasos:

1. [Cree una nueva capacidad](azure-pbie-create-capacity.md) en una región distinta.

2. Asigne todas las áreas de trabajo de la capacidad existente a la nueva capacidad.

3. Elimine o pause la capacidad anterior.

Es importante tener en cuenta que si decide eliminar una capacidad sin volver a asignar su contenido, todo el contenido de esa capacidad se mueve a una capacidad compartida, que se encuentra en la región principal.

## <a name="api-support-for-multi-geo"></a>Compatibilidad de API en Multi-Geo

Para que sea posible la administración de capacidades con Multi-Geo mediante API, se han realizado algunos cambios en las API existentes:

1. **[Get Capacities](https://docs.microsoft.com/rest/api/power-bi/capacities/getcapacities)** : la API devuelve una lista de capacidades con acceso al usuario. La respuesta incluye ahora una propiedad adicional denominada "region", que especifica la ubicación de la capacidad.

2. **[Assign To Capacity](https://docs.microsoft.com/rest/api/power-bi/capacities)** : la API permite asignar un área de trabajo determinada a una capacidad. Esta operación no permite asignar áreas de trabajo a una capacidad fuera de la región principal ni mover áreas de trabajo entre capacidades de diferentes regiones. Para realizar esta operación, el usuario o la [entidad de servicio](embed-service-principal.md) todavía necesita permisos de administrador en el área de trabajo, y permisos de administración o asignación en la capacidad de destino.

3. **[API de Azure Resource Manager](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities)** : todas las operaciones de API de Azure Resource Manager, como *Crear* y *Eliminar*, admiten Multi-Geo.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

* Antes de iniciar la transferencia de datos, confirme que cualquier movimiento que inició entre regiones satisface todos los requisitos de cumplimiento corporativos y gubernamentales.

* Una consulta en caché almacenada en una región remota permanece en esa región en reposo. Sin embargo, otros datos en tránsito pueden ir y venir entre distintas geografías.

* Al mover datos de una región a otra en un entorno Multi-Geo, los datos de origen pueden permanecer en la región de la que se movieron durante 30 días como máximo. Durante ese período, los usuarios no tienen acceso a ellos. Se quitan de esta región y se destruyen durante el período de 30 días.

* En términos generales, Multi-Geo no genera un mejor rendimiento. La carga de informes y paneles aún implica solicitudes de metadatos a la región principal.

## <a name="next-steps"></a>Pasos siguientes

Consulte los siguientes vínculos para más información sobre las capacidades de Power BI Embedded y las opciones Multi-Geo para todas las capacidades.

* [¿Qué es Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

* [Creación de una capacidad de Power BI Embedded](azure-pbie-create-capacity.md)

* [Multi-Geo en capacidades de Power BI Premium](../service-admin-premium-multi-geo.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)