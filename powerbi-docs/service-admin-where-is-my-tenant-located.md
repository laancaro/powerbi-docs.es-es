---
title: ¿Dónde se encuentra mi inquilino de Power BI?
description: Obtenga información sobre dónde se encuentra su inquilino de Power BI y cómo se selecciona esa ubicación. Es importante saber esto, ya que puede afectar las interacciones que tiene con el servicio.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 3f12e6f0b54f85ebd626b2bd35bf1a03d513c17a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873344"
---
# <a name="where-is-my-power-bi-tenant-located"></a>¿Dónde se encuentra mi inquilino de Power BI?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Obtenga información sobre dónde se encuentra su inquilino de Power BI y cómo se selecciona esa ubicación. Saber la ubicación es importante, ya que puede afectar las interacciones que tiene con el servicio.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Cómo determinar dónde se encuentra el inquilino de Power BI

Para buscar la región en la que se encuentra su inquilino, siga estos pasos.

1. En el servicio Power BI, en el menú superior, seleccione Ayuda ( **?** ) y, a continuación, **Acerca de Power BI**.

1. Busque el valor situado junto a **Los datos están almacenados en**. Es la región donde se encuentra el inquilino. Esta valor también es la región donde se almacenan los datos, a menos que se usen capacidades dedicadas en regiones diferentes para las áreas de trabajo.

    ![Región de datos](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Cómo se selecciona la región de datos

La región de datos se basa en el país que seleccionó al crear el inquilino. La selección se aplica para suscribirse a Office 365 y Power BI, porque esta información se comparte. Si se trata de un nuevo inquilino, seleccione el país correspondiente en la lista cuando se suscriba.

![Selección de país](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI selecciona una región de datos más cercana a su selección, que determina dónde se almacenan los datos del inquilino.

> [!IMPORTANT]
> No se puede cambiar la selección después de crear el inquilino.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

