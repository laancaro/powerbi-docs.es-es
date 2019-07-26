---
title: Guía para la implementación de una puerta de enlace de datos para Power BI
description: Obtenga información acerca de los procedimientos recomendados y las consideraciones para implementar una puerta de enlace para Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271720"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Guía para la implementación de una puerta de enlace de datos para Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

En este artículo se proporcionan instrucciones y consideraciones para implementar una puerta de enlace de datos para Power BI en el entorno de red.

Para obtener información sobre cómo descargar, instalar, configurar y administrar la puerta de enlace de datos local, vea [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-onprem). También puede obtener más información sobre la puerta de enlace de datos local y Power BI si visita el [blog de Microsoft Power](https://powerbi.microsoft.com/blog/) y el sitio de la [comunidad de Microsoft Power BI](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Consideraciones para la instalación de la puerta de enlace de datos local

Antes de instalar la puerta de enlace de datos local para el servicio en la nube de Power BI, debe tener en cuenta una serie de consideraciones. En las secciones siguientes se describen estas consideraciones.

### <a name="number-of-users"></a>Número de usuarios

El número de usuarios que usan un informe que utiliza la puerta de enlace es una métrica importante para decidir dónde instalar la puerta de enlace. Estas son algunas preguntas a tomar en consideración:

* ¿Los usuarios utilizan estos informes en distintos momentos del día?
* ¿Qué tipos de conexiones están utilizando (DirectQuery o importación)?
* ¿Todos los usuarios utilizan el mismo informe?

Si todos los usuarios acceden a un informe determinado al mismo tiempo cada día, querrá asegurarse de instalar la puerta de enlace en un equipo que sea capaz de controlar todas esas solicitudes (vea las secciones siguientes para obtener información sobre los contadores de rendimiento y los requisitos mínimos que pueden ayudarle a determinarlo).

Hay una restricción en **Power BI** que solo permite *una* puerta de enlace por *informe*, por lo que incluso si un informe se basa en varios orígenes de datos, todos estos orígenes de datos deben pasar por una sola puerta de enlace. Sin embargo, si un panel se basa en *varios* informes, puede utilizar una puerta de enlace dedicada para cada informe contribuyente y, por tanto, distribuir la carga de la puerta de enlace entre esos varios informes que contribuyen a ese panel único.

### <a name="connection-type"></a>Tipo de conexión

**Power BI** ofrece dos tipos de conexiones: **DirectQuery** e **Importación**. No todos los orígenes de datos admiten ambos tipos de conexión y varias razones pueden contribuir a elegir una frente a otra, como los requisitos de seguridad, rendimiento, límites de datos y tamaños de modelo de datos. Puede obtener más información sobre los tipos de conexión y orígenes de datos admitidos en la [lista de tipos de orígenes de datos disponibles](service-gateway-data-sources.md#list-of-available-data-source-types).

En función del tipo de conexión en uso, la utilización de la puerta de enlace puede ser diferente. Por ejemplo, es conveniente separar los orígenes de datos **DirectQuery** de los orígenes de datos de **Actualización programada** siempre que sea posible (suponiendo que están en diferentes informes y se pueden separar). Al hacerlo así evita que la puerta de enlace tenga miles de solicitudes de DirectQuery en cola, al mismo tiempo que la actualización programada de la mañana de un modelo de datos de gran tamaño que se usa para el panel principal de la compañía. Esto es lo que debe tener en cuenta para cada uno de ellos:

* Para **Actualización programada**: según el tamaño de la consulta y el número de actualizaciones que se producen al día, puede elegir entre permanecer con los requisitos mínimos de hardware recomendados o actualizar a una máquina de rendimiento superior. Si una consulta determinada no se dobla, las transformaciones se producen en el equipo de la puerta de enlace y, por lo tanto, la máquina de la puerta de enlace se beneficia de tener más RAM disponible.

* Para **DirectQuery**: se enviará una consulta cada vez que cualquier usuario abre el informe o examine datos. Por lo que si prevé que más de 1.000 usuarios tendrán acceso a los datos simultáneamente, querrá asegurarse de que el equipo tiene componentes de hardware sólidos y eficaces. Más núcleos de CPU darán como resultado un mejor rendimiento para una conexión **DirectQuery**.

Los requisitos para un equipo en el que se realiza la instalación se pueden encontrar en los [requisitos de instalación](/data-integration/gateway/service-gateway-install#requirements) de la puerta de enlace de datos local.

### <a name="location"></a>Ubicación

La ubicación de la instalación de la puerta de enlace puede tener un impacto significativo en el rendimiento de las consultas, así que intente asegurarse de que la puerta de enlace, las ubicaciones de origen de datos y el inquilino de Power BI están tan cerca como sea posible entre sí para minimizar la latencia de red. Para determinar la ubicación del inquilino de Power BI, en el servicio Power BI seleccione el icono **?** en la esquina superior derecha y, a continuación, seleccione **Acerca de Power BI**.

![Determinación de la ubicación del inquilino de Power BI](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Además, si piensa usar la puerta de enlace de Power BI con Azure Analysis Services, asegúrese de que las regiones de datos coinciden en los dos. Para más información sobre la configuración de regiones de datos para varios servicios, [ vea este vídeo](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Pasos siguientes

* [Configuración de proxy](/data-integration/gateway/service-gateway-proxy)  
* [Solución de problemas de puertas de enlace: Power BI](service-gateway-onprem-tshoot.md)  
* [Preguntas más frecuentes sobre la puerta de enlace de datos local: Power BI](service-gateway-power-bi-faq.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

