---
title: Escalar una capacidad de Power BI Embedded | Microsoft Docs
description: En este artículo se explica cómo escalar una capacidad de Power BI Embedded en Microsoft Azure.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 01/31/2019
ms.openlocfilehash: 365f24ec80d58297a852fa3d040c04c8c763eeda
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265617"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Escalar una capacidad de Power BI Embedded en Azure Portal

En este artículo se explica cómo escalar una capacidad de Power BI Embedded en Microsoft Azure. El escalado permite aumentar o disminuir el tamaño de la capacidad.

Se da por supuesto que ya ha creado una capacidad de Power BI Embedded, pero si no lo ha hecho, vea [Creación de una capacidad de Power BI Embedded en Azure Portal](azure-pbie-create-capacity.md) para empezar.

> [!NOTE]
> Una operación de escalado puede llevar aproximadamente un minuto. Durante este tiempo, la capacidad no estará disponible y puede producirse un error al cargar el contenido insertado.

## <a name="scale-a-capacity"></a>Escalar una capacidad

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).

2. Seleccione **All services (Todos los servicios)**  > **Power BI Embedded** para ver las capacidades.

    ![Todos los servicios en Azure Portal](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Seleccione la capacidad que quiere escalar.

    ![Lista de capacidades de Power BI Embedded en Azure Portal](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. En la capacidad, seleccione **Plan de tarifa** en **Escala**.

    ![Opción Plan de tarifa en Escala](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    El plan de tarifa actual se muestra en azul.

    ![Plan de tarifa actual en azul](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Para aumentar o reducir la escala, seleccione el nuevo plan al que quiere cambiar. Si elige un nuevo plan, la selección se rodea con un contorno discontinuo de color azul. Haga clic en **Seleccionar** para escalar al nuevo plan.

    ![Seleccione un nuevo plan](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    El escalado de la capacidad puede tardar en completarse un minuto o dos.

6. Para confirmar el plan, consulte la pestaña de información general. Aquí se muestra el plan de tarifa actual.

    ![Confirmación del plan actual](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Pasos siguientes

Para pausar o iniciar la capacidad, vea [Pausar e iniciar una capacidad de Power BI Embedded en Azure Portal](azure-pbie-pause-start.md).

Para empezar a insertar contenido de Power BI en la aplicación, vea [Inserción de un informe, un panel o un icono de Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
