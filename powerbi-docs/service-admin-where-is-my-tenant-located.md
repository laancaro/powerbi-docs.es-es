---
title: ¿Dónde se encuentra mi inquilino de Power BI?
description: Obtenga información sobre dónde se encuentra su inquilino de Power BI y cómo se selecciona esa ubicación. Es importante comprenderlo, ya que puede afectar a las interacciones con el servicio.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e71844110eb3452cbcb3b224bbca9db57475367e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282181"
---
# <a name="where-is-my-power-bi-tenant-located"></a>¿Dónde se encuentra mi inquilino de Power BI?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Obtenga información sobre dónde se encuentra su inquilino de Power BI y cómo se selecciona esa ubicación. Saber la ubicación es importante, ya que puede afectar a las interacciones que tiene con el servicio.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Cómo determinar dónde se encuentra el inquilino de Power BI

Para buscar la región en la que se encuentra su inquilino, siga estos pasos.

1. En el servicio Power BI, en el menú superior, seleccione Ayuda (**?**) y, a continuación, **Acerca de Power BI**.

1. Busque el valor situado junto a **Los datos están almacenados en**. Esta es la región donde se encuentra el inquilino.

    ![Región de datos](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Cómo se selecciona la región de datos

La región de datos se basa en el país que seleccionó al crear el inquilino. Esto se aplica a la suscripción a Office 365 además de a Power BI, ya que esta información se comparte. Si se trata de un nuevo inquilino, seleccione el país correspondiente en la lista cuando se suscriba.

![Selección de país](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI selecciona una región de datos más cercana a esta selección, que determina dónde se almacenan los datos del inquilino.

> [!IMPORTANT]
> No se puede cambiar esta selección después de crear el inquilino.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

