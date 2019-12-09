---
title: P+F sobre alta disponibilidad, conmutación por error y recuperación ante desastres en Power BI
description: Descripción de cómo el servicio Power BI ofrece alta disponibilidad y proporciona continuidad empresarial y recuperación ante desastres a los usuarios.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 24867d231cca0135c09119f4b885b393cb2b8dd8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699070"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>P+F sobre alta disponibilidad, conmutación por error y recuperación ante desastres en Power BI

En este artículo se describe cómo el servicio Power BI ofrece alta disponibilidad y proporciona continuidad empresarial y recuperación ante desastres a los usuarios. Después de leer este artículo, debería comprender mejor cómo se logra la alta disponibilidad, en qué circunstancias realiza Power BI una conmutación por error y qué esperar del servicio cuando la realiza.

## <a name="what-does-high-availability-mean-for-power-bi"></a>¿Qué significa "alta disponibilidad" para Power BI?

Power BI es software como servicio (SaaS) totalmente administrado.  Microsoft lo diseña y hace funcionar para que sea resistente a los errores de infraestructura de modo que los usuarios siempre puedan acceder a sus informes.  El servicio está respaldado por un [SLA del 99,9 %](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>¿Qué es la conmutación por error de Power BI?

Power BI mantiene varias instancias de cada componente en centros de datos Azure (también conocidos como regiones) para garantizar la continuidad empresarial. Si se produce una interrupción o un problema que hace que Power BI sea inaccesible o no funcione en una región, Power BI realiza la conmutación por error de todos sus componentes en esa región en una instancia de copia de seguridad. La conmutación por error restaura la disponibilidad y operatividad en la instancia del servicio Power BI en una región nueva (normalmente en la misma ubicación geográfica, como se indica en el [Centro de confianza de Microsoft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

Una instancia del servicio Power BI conmutada por error solo admite _operaciones de lectura_, lo que significa que las operaciones siguientes no se admiten durante la conmutación por error: actualizaciones, operaciones de publicación de informes, modificaciones de paneles o informes, y otras operaciones que requieran cambios en los metadatos de Power BI (por ejemplo, la inserción de un comentario en un informe).  Las operaciones de lectura, como la visualización de paneles e informes (que no se basan en DirectQuery o Live Connect a orígenes de datos locales) seguirán funcionando con normalidad.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>¿Cómo se mantienen sincronizadas las instancias de copia de seguridad con los datos?

Todos los componentes del servicio Power BI sincronizan con regularidad sus instancias de copia de seguridad. El objetivo es una sincronización a un momento dado de 15 minutos para todo el contenido que se cargue o modifique en Power BI. Si se produce una conmutación por error, Power BI usa [la replicación geográficamente redundante de Azure Storage](/azure/storage/common/storage-redundancy-grs) y la [replicación geográficamente redundante de Azure SQL](/azure/sql-database/sql-database-active-geo-replication) para garantizar la existencia de instancias de copia de seguridad en otras regiones y que se puedan usar si se produce una conmutación por error.

## <a name="where-are-the-failover-clusters-located"></a>¿Dónde están ubicados los clústeres de conmutación por error?

Las instancias de copia de seguridad residen dentro de la misma ubicación geográfica (geoárea) que seleccionó cuando la organización se registró en Power BI, excepto donde se indique en el [Centro de confianza de Microsoft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Una geoárea puede contener varias regiones, y Microsoft puede replicar datos en cualquiera de las regiones dentro de una geoárea determinada para lograr la resistencia de los datos. Microsoft no replicará ni moverá los datos del cliente fuera de la geoárea. Para obtener una asignación de las geoáreas que ofrece Power BI y las regiones que contienen, vea el [Centro de confianza de Microsoft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-failover"></a>¿Cómo decide Microsoft la conmutación por error?

Hay dos sistemas diferentes que indican cuándo puede ser necesaria una conmutación por error:

- Nuestro sondeos de supervisión internos y externos indican una falta de disponibilidad o la incapacidad de funcionar de forma correcta. Esas indicaciones se pueden basar en interrupciones detectadas en los componentes de Power BI o uno o varios de los servicios de los que Power BI depende en una región.
- El equipo de operaciones central de Microsoft Azure nos informa de una interrupción crítica en una región.

En ambos casos, los miembros del equipo ejecutivo de Power BI toman la decisión de realizar la conmutación por error; la propia decisión no está automatizada. Una vez que se toma la decisión, el proceso de conmutación por error se realiza de forma automática.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>¿Cómo se puede saber que Power BI ya está en modo de conmutación por error?

Se publica una notificación en la página de soporte técnico de Power BI ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). La notificación incluye las operaciones principales que no están disponibles durante la conmutación por error, incluidas las de publicación, actualización, creación de paneles, duplicación de paneles y cambios de permisos.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>¿Cuánto tiempo tarda Power BI en realizar la conmutación por error?

Una vez que se toma la decisión de la conmutación por error, una instancia de conmutación por error puede tardar hasta 60 minutos en estar disponible.

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>¿Cuando vuelve la instancia de Power BI a la región original?

Las instancias del servicio Power BI vuelven a su región original cuando se resuelva el problema que ha provocado la conmutación por error. Consulte la página de soporte técnico de Power BI: Cuando se resuelve el problema, el equipo de Power BI quita la notificación que describe la conmutación por error. En ese momento, las operaciones deberían recuperar la normalidad.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>¿Soy responsable de la disponibilidad de mi solución de Power BI?

Si la solución de Power BI que se usa en la organización implica uno de los elementos siguientes, debe tomar ciertas medidas para garantizar que la solución sigue teniendo alta disponibilidad:

- Si en la organización se usa Power BI Premium, debe asegurarse de que la capacidad Premium tiene el tamaño para satisfacer las demandas de carga de la implementación.  Las [notas del producto de planeación e implementación de Power BI Premium](https://aka.ms/Premium-Capacity-Planning-Deployment) y la [aplicación Premium Capacity Metrics de Power BI](service-admin-premium-monitor-capacity.md) pueden ayudar a planear y satisfacer este requisito. Periódicamente se agregan características nuevas a la aplicación de métricas y al portal de administración de Power BI para que sirvan de ayuda.
- Si en la organización se accede a orígenes de datos locales mediante la puerta de enlace de datos local, tendrá que configurar la puerta de enlace [como se describe en este artículo](/data-integration/gateway/service-gateway-high-availability-clusters) para admitir la alta disponibilidad. Siga estas instrucciones si va a actualizar informes en modo de importación o va a acceder a datos o modelos de datos mediante DirectQuery o Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>¿Las puertas de enlace funcionarán en el modo de conmutación por error?

No. Los datos necesarios de orígenes de datos locales (todos los informes y paneles basados en Direct Query y Live Connect) no funcionarán durante una conmutación por error. Pero la configuración de puerta de enlace no cambia: cuando la instancia de Power BI vuelve a su estado original, las puertas de enlace recuperan su funcionamiento normal.
