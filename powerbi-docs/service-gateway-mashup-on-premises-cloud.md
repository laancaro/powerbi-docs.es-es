---
title: Combinar o anexar orígenes de datos locales o en la nube
description: Use la puerta de enlace de datos local para combinar o anexar orígenes de datos locales o en la nube en la misma consulta.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 06/06/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2547be7f7bdadb7f991db54230d4fd791941838d
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37600076"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Combinar o anexar orígenes de datos locales o en la nube

La puerta de enlace de datos local le permite combinar o anexar orígenes de datos locales o en la nube en la misma consulta. Es útil cuando quiere mezclar datos de varios orígenes sin tener que usar consultas independientes.

## <a name="prerequisites"></a>Requisitos previos

- Una [puerta de enlace instalada](service-gateway-install.md) en un equipo local.
- Un archivo de Power BI Desktop con consultas que combinan orígenes de datos locales y en la nube.

1. En la esquina superior derecha del servicio Power BI, seleccione el icono del engranaje ![Icono de engranaje de configuración](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) > **Administrar puertas de enlace**.

    ![Administrar puertas de enlace](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. Seleccione la puerta de enlace que quiere configurar.

3. En **Configuración del clúster de puerta de enlace**, seleccione **Allow user's cloud data sources to refresh through this gateway cluster** (Permitir que los orígenes de datos en la nube del cliente se actualicen mediante este clúster de puerta de enlace)  > **Aplicar**.

    ![Actualización mediante este clúster de puerta de enlace](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. En este clúster de puerta de enlace, agregue cualquier [origen de datos local](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source) empleado en las consultas. No es necesario agregar aquí los orígenes de datos de nube.

5. Cargue en el servicio Power BI el archivo de Power BI Desktop con las consultas que combinan orígenes de datos locales y en la nube.

6. En la página **Configuración del conjunto de datos** del conjunto de datos nuevo:

   - Para el origen local, seleccione la puerta de enlace asociada a este origen de datos.

   - En **Credenciales del origen de datos**, edite las credenciales del origen de datos en la nube según sea necesario.

     ![Configuración del conjunto de datos](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

7. Con las credenciales en la nube establecidas, ahora puede actualizar el conjunto de datos con la opción **Actualizar ahora** o programarlo para que se actualice periódicamente.


## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre la actualización de datos para las puertas de enlace, vea [Uso del origen de datos para actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh).