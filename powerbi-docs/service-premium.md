---
title: ¿Qué es Microsoft Power BI Premium?
description: Power BI Premium cuenta con capacidad dedicada para su organización o equipo, lo que le ofrece un rendimiento más confiable y mayores volúmenes de datos, sin tener que adquirir licencias por usuario.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/21/2018
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: ea26ba39a9ec06b79330719afd4fb3b3a572d912
ms.sourcegitcommit: 9913c213d40b45ba83c6c3b3a7ef0b757800e3ad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2018
ms.locfileid: "53301813"
---
# <a name="what-is-microsoft-power-bi-premium"></a>¿Qué es Microsoft Power BI Premium?

Microsoft Power BI Premium proporciona recursos dedicados para ejecutar el servicio Power BI en la organización. Ofrece un rendimiento más confiable y permite mayores volúmenes de datos. Premium también permite la distribución generalizada de contenido sin necesidad de adquirir licencias Pro para cada consumidor de contenido. Para obtener información de compra, vea [Adquisición de Power BI Premium](service-admin-premium-purchase.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="premium-capacity-and-shared-capacity"></a>Capacidad compartida y capacidad Premium

Puede aprovechar las ventajas de Power BI Premium asignando áreas de trabajo a una *capacidad Premium*. La capacidad Premium es un recurso dedicado para su organización. Las áreas de trabajo que no están asignadas a una capacidad Premium se encuentran en una *capacidad compartida*. Gracias a la capacidad compartida, las cargas de trabajo se ejecutan en recursos informáticos compartidos con otros clientes.

La siguiente imagen muestra la relación entre la capacidad Premium y la capacidad compartida, con la organización de Contoso como ejemplo.

![Ilustración de Power BI Premium](media/service-premium/premium-chart.png)

| Área | Descripción |
| --- | --- |
| **(1)** Elementos dentro de una capacidad Premium | <ul><li>El acceso a áreas de trabajo de aplicaciones (como miembros o administradores) y la publicación de aplicaciones requieren una licencia de Power BI Pro.<li>Para compartir una aplicación se necesita una licencia de Pro, pero no para usarla.<li>Todos los destinatarios del panel, sea cual sea la licencia que tengan asignada, pueden establecer alertas de datos.<li>Las API de REST para la inserción utilizan una cuenta de servicio con una licencia de Pro, en lugar de una cuenta de usuario.</ul> |
| **(2)** Mi área de trabajo en capacidad compartida | <ul><li>Tanto para compartir una aplicación como para usarla se necesita una licencia de Pro.</ul> |
| **(3)** Áreas de trabajo de aplicación en capacidad compartida | <ul><li>Cualquier uso que se haga de la aplicación requiere una licencia de Pro.</ul>|
| | |

En la capacidad compartida, Power BI establece más límites a cada usuario para garantizar la calidad de la experiencia de todos ellos. De forma predeterminada, el área de trabajo está en una capacidad compartida, lo que incluye *Mi área de trabajo* personal y las áreas de trabajo de aplicación.

La siguiente tabla proporciona un resumen de las diferencias entre la capacidad compartida y la capacidad Premium.

|  | Capacidad compartida | Capacidad Power BI Premium |
| --- | --- | --- |
| **Frecuencia de actualización** |8/día |48/día |
| **Aislamiento con hardware dedicado** |![No disponible](media/service-premium/not-available.png) |![Disponible](media/service-premium/available.png) |
| **Distribución empresarial a** _**todos los usuarios**_ | | |
| Aplicaciones y uso compartido |![No disponible](media/service-premium/not-available.png) |![Disponible](media/service-premium/available.png) |
| API y controles insertados |![No disponible](media/service-premium/not-available.png) |![Disponible](media/service-premium/available.png)<sup>2</sup> |
| **Publicar informes de Power BI en entornos locales** |![No disponible](media/service-premium/not-available.png) |![Disponible](media/service-premium/available.png) |
| | | |

*<sup>1</sup> Para obtener más información, vea [Características por tipo de licencia](service-features-license-type.md).*  
*<sup>2</sup> Se introducirán futuras mejoras en Power BI Premium.*

Para saber más sobre la asignación de áreas de trabajo a una capacidad Premium, vea [Administración de la capacidad en Power BI Premium y Power BI Embedded](service-admin-premium-manage.md).

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nodos de la capacidad Premium

Power BI Premium está disponible en las configuraciones de nodo con capacidades diferentes de núcleos V. Para más información sobre ofertas y costos de SKU específicos, vea los [precios de Power BI](https://powerbi.microsoft.com/pricing/). También se encuentra disponible una [calculadora de costos](https://powerbi.microsoft.com/calculator/). Para obtener información sobre el planeamiento de capacidad de análisis insertada, vea las [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/pbienterprisedeploy). Para resumir:

* Los nodos P se pueden usar para las implementaciones de servicio o insertadas.

* Los nodos EM solo se pueden usar para las implementaciones insertadas. Los nodos EM no tienen acceso a las funciones premium, como el uso compartido de aplicaciones con los usuarios que no tienen una licencia de Power BI Pro.

>[!NOTE]
>Los vínculos de esta tabla solo funcionan correctamente para los usuarios que tienen el rol Administrador global de Office 365. Los demás reciben un error 404.

| Nodo de capacidad | Total de núcleos virtuales<br/>*(Back-end y front-end)* | Núcleos virtuales de back-end | Núcleos virtuales de front-end | Límites de conexiones dinámicas/DirectQuery | Disponibilidad |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mes a mes)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |0,5 núcleos virtuales, 2,5 GB de RAM |0,5 núcleos virtuales |3,75 por segundo |Disponible |
| [EM2 (mes a mes)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos V |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |Disponible |
| [EM3 (mes a mes)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos V |2 núcleos virtuales, 10 GB de RAM |2 núcleos V | |Disponible |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 núcleos V |4 núcleos virtuales, 25 GB de RAM |4 núcleos V |30 por segundo |Disponible (también está disponible [mes a mes](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 núcleos V |8 núcleos virtuales, 50 GB de RAM |8 núcleos V |60 por segundo |Disponible |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 núcleos V |16 núcleos virtuales, 100 GB de RAM |16 núcleos V |120 por segundo |Disponible |
| | | | | | | |

* Los núcleos virtuales front-end son responsables de la administración de informes, paneles y servicios web, la administración de derechos de acceso, la programación, las API, las cargas y descargas y, en general, de todo lo relacionado con la experiencia del usuario.

* Los núcleos virtuales back-end son responsables de todo el trabajo pesado: procesamiento de consultas, administración de caché, ejecución de servidores R, actualización de datos, procesamiento de lenguaje natural, fuentes en tiempo real y representación del lado servidor de informes e imágenes. Con los núcleos virtuales de back-end, también se reserva una cantidad determinada de memoria. Disponer de memoria suficiente es especialmente importante para trabajar con grandes modelos de datos o con un número elevado de conjuntos de datos activos.

## <a name="workloads-in-premium-capacity"></a>Cargas de trabajo en capacidad Premium

Piense en una carga de trabajo en Power BI como uno de los muchos servicios que se pueden exponer a los usuarios. De forma predeterminada, las funcionalidades de **Power BI Premium** y **Power BI Embedded** admiten solo la carga de trabajo asociada con la ejecución de consultas de Power BI en la nube.

Ahora ofrecemos compatibilidad con versiones preliminares para dos cargas de trabajo adicionales: **Informes paginados** y **flujos de datos**. Habilite estas cargas de trabajo en el portal de administración de Power BI o mediante la API de REST de Power BI. Establezca también la memoria máxima que cada carga de trabajo puede consumir, para poder controlar la forma en que las distintas cargas de trabajo se afectan entre sí. Para más información, vea [Configuración de cargas de trabajo](service-admin-premium-manage.md#configure-workloads).

### <a name="default-memory-settings"></a>Configuración de memoria predeterminada

En la tablas siguientes se muestran los valores de memoria predeterminados y mínimos, en función de los diferentes [nodos de capacidad](#premium-capacity-nodes) disponibles. La memoria se asigna de manera dinámica a los flujos de datos, pero se asigna de forma estática a los informes paginados. Para más información, vea la siguiente sección, [Consideraciones sobre los informes paginados](#considerations-for-paginated-reports).

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKU de Microsoft Office para los escenarios de software como servicio (SaaS)

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Informes paginados | N/D | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo | 20 % predeterminado; 2,5 % mínimo |
| Flujos de datos | 20 % predeterminado; 8 % mínimo  | 20 % predeterminado; 4 % mínimo  | 20 % predeterminado; 2 % mínimo | 20 % predeterminado; 1 % mínimo  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKU de Microsoft Azure para los escenarios de plataforma como servicio (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Informes paginados | N/D                      | N/D                      | N/D                     | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo | 20 % predeterminado; 2,5 % mínimo |
| Flujos de datos         | 27 % predeterminado; 27 % mínimo | 20 % predeterminado; 16 % mínimo | 20 % predeterminado; 8 % mínimo | 20 % predeterminado; 4 % mínimo  | 20 % predeterminado; 2 % mínimo | 20 % predeterminado; 1 % mínimo   |

### <a name="considerations-for-paginated-reports"></a>Consideraciones sobre los informes paginados

Si usa la carga de trabajo de informes paginados, tenga en cuenta los siguientes puntos.

* **Asignación de memoria en informes paginados**: los informes paginados le permiten ejecutar su propio código al representar un informe (como cambiar de forma dinámica el color del texto en función del contenido). Dado este hecho, protegemos la capacidad Premium de Power BI mediante la ejecución de informes paginados en un espacio contenido dentro de la capacidad. Asignamos la memoria máxima especificada a este espacio, independientemente de si la carga de trabajo está o no activa. Si usa informes o flujos de datos de Power BI en la misma capacidad, asegúrese de establecer una cantidad de memoria lo suficientemente baja para los informes paginados, de tal forma que no afecte negativamente a las otras cargas de trabajo.

* **Los informes paginados no están disponibles**: en circunstancias excepcionales, la carga de trabajo de informes paginados deja de estar disponible. En este caso, la carga de trabajo muestra un estado de error en el portal de administración y los usuarios ven los tiempos de expiración para la representación de informes. Para mitigar este problema, deshabilite la carga de trabajo y luego vuelva a habilitarla.

## <a name="power-bi-report-server"></a>Power BI Report Server

Power BI Premium también incluye la posibilidad de ejecutar Power BI Report Server en local en la organización. Para saber más, vea [¿Qué es Power BI Report Server?](report-server/get-started.md).

## <a name="next-steps"></a>Pasos siguientes

[Preguntas más frecuentes sobre Power BI Premium](service-premium-faq.md)
[Adquisición de Power BI Premium](service-admin-premium-purchase.md)
[Administración de Power BI Premium](service-admin-premium-manage.md)
[Notas del producto de Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[Notas del producto: Planning a Power BI Enterprise Deployment](https://aka.ms/pbienterprisedeploy) (Planeación de una implementación de Power BI Enterprise) 
[Administración de Power BI en su organización](service-admin-administering-power-bi-in-your-organization.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
