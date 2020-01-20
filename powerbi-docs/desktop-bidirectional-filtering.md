---
title: Filtrado cruzado bidireccional en Power BI Desktop
description: Habilitar el filtrado cruzado con DirectQuery en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8aeae0075ed32a832c27f475ef3786b7df76576c
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761781"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Habilitación del filtrado cruzado bidireccional para DirectQuery en Power BI Desktop

Al filtrar tablas para crear la vista de datos adecuada, los creadores de informes (y los modeladores de datos) se enfrentan a desafíos al determinar cómo se aplica el filtrado a un informe; el contexto de filtro de una tabla se ha mantenido en un lado de la relación, pero no en el otro, que a menudo requiere fórmulas DAX complejas para obtener los resultados deseados.

Con el filtrado cruzado bidireccional, los creadores de informes (y los modeladores de datos) ahora tienen más control sobre cómo se aplican los filtros al trabajar con tablas relacionadas, lo que habilita esos filtros para que se apliquen en *ambos* lados de una relación de tabla. Para ello, hay que tener el contexto de filtro propagado a una segunda tabla relacionada en el otro lado de una relación de tabla.

## <a name="detailed-whitepaper-for-bidirectional-cross-filtering"></a>Notas del producto detalladas para el filtrado cruzado bidireccional
Hay [notas del producto detalladas](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) disponibles en las que se explica el filtrado cruzado bidireccional en Power BI Desktop (las notas del producto también abarcan SQL Server Analysis Services 2016, ambos tienen el mismo comportamiento).

* Descargar las notas del producto del [filtrado cruzado bidireccional para Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)

## <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Habilitar el filtrado cruzado bidireccional para DirectQuery

Para habilitar el filtrado cruzado, en el cuadro de diálogo **Editar relación** de una relación, se debe seleccionar lo siguiente:

* La **Dirección del filtro cruzado** debe establecerse en **Ambos**
* **Aplicar filtro de seguridad en ambas direcciones** también debe estar seleccionado

  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Al crear fórmulas DAX de filtrado cruzado en Power BI Desktop, use *UserPrincipalName* (que suele ser el mismo que el inicio de sesión de un usuario, como <em>joe@contoso.com</em>) en lugar de *UserName*. Por tanto, puede que necesite crear una tabla relacionada que asigne *UserName* (o EmployeeID, por ejemplo) a *UserPrincipalName*.

Para obtener más información y ejemplos de cómo funciona el filtrado cruzado bidireccional, consulte las [notas del producto](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) mencionadas anteriormente en este artículo.

