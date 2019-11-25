---
title: Pausar e iniciar una capacidad de Power BI Embedded en Azure Portal | Microsoft Docs
description: En este artículo se explica cómo pausar e iniciar una capacidad de Power BI Embedded en Microsoft Azure.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 09/28/2017
ms.openlocfilehash: 07c9c12366b100936e03fe07358ee180e026dfc5
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265673"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Pausar e iniciar una capacidad de Power BI Embedded en Azure Portal

En este artículo se explica cómo pausar e iniciar una capacidad de Power BI Embedded en Microsoft Azure. Se da por supuesto que ya ha creado una capacidad de Power BI Embedded, pero si no lo ha hecho, vea [Creación de una capacidad de Power BI Embedded en Azure Portal](azure-pbie-create-capacity.md) para empezar.

Si no tiene ninguna suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/) antes de empezar.

## <a name="pause-your-capacity"></a>Pausar la capacidad

Si pausa la capacidad, detiene la facturación. Es muy útil pausar la capacidad si no necesita usarla durante un período de tiempo. Siga los pasos que se indican a continuación para pausar la capacidad.

> [!NOTE]
> Al pausar una capacidad, puede impedir que el contenido esté disponible en Power BI. Asegúrese de desasignar las áreas de trabajo de la capacidad antes de pausarla para evitar la interrupción.

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).

2. Seleccione **All services (Todos los servicios)**  > **Power BI Embedded** para ver las capacidades.

    ![Todos los servicios en Azure Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Seleccione la capacidad que quiere pausar.

    ![Lista de capacidades de Power BI Embedded en Azure Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. En los detalles de la capacidad, seleccione **Pausar**.

    ![Pausar la capacidad](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Seleccione **Sí** para confirmar que quiere pausar la capacidad.

    ![Confirmación de la pausa](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Iniciar la capacidad

Inicie la capacidad para seguir usándola. Al iniciar la capacidad, también se reanuda la facturación.

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).

2. Seleccione **All services (Todos los servicios)**  > **Power BI Embedded** para ver las capacidades.

    ![Todos los servicios en Azure Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Seleccione la capacidad que quiere iniciar.

    ![Lista de capacidades de Power BI Embedded en Azure Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. En los detalles de la capacidad, seleccione **Iniciar**.

    ![Iniciar la capacidad](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Seleccione **Sí** para confirmar que quiere iniciar la capacidad.

    ![Confirmación del inicio](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Si esta capacidad tiene contenido asignado, estará disponible cuando se inicie.

## <a name="next-steps"></a>Pasos siguientes

Si quiere aumentar o reducir la escala de la capacidad, vea [Escalar una capacidad de Power BI Embedded](azure-pbie-scale-capacity.md).

Para empezar a insertar contenido de Power BI en la aplicación, vea [Inserción de un informe, un panel o un icono de Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)