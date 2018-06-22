---
title: Filtrado cruzado bidireccional en Power BI Desktop
description: Habilitar el filtrado cruzado con DirectQuery en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a584d61e1f2f55c244b453e6c086f3222217ee9a
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34289013"
---
# <a name="bidirectional-cross-filtering-using-directquery-in-power-bi-desktop"></a>Filtrado cruzado bidireccional con DirectQuery en Power BI Desktop

Al filtrar tablas para crear la vista de datos adecuada, los creadores de informes (y los modeladores de datos) se enfrentan a desafíos al determinar cómo se aplica el filtrado a un informe; el contexto de filtro de una tabla se ha mantenido en un lado de la relación, pero no en el otro, que a menudo requiere fórmulas DAX complejas para obtener los resultados deseados.

Con el filtrado cruzado bidireccional, los creadores de informes (y los modeladores de datos) ahora tienen más control sobre cómo se aplican los filtros al trabajar con tablas relacionadas, lo que habilita esos filtros para que se apliquen en *ambos* lados de una relación de tabla. Para ello, hay que tener el contexto de filtro propagado a una segunda tabla relacionada en el otro lado de una relación de tabla.

Hay [notas del producto detalladas](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) disponibles en las que se explica el filtrado cruzado bidireccional en Power BI Desktop (las notas del producto también abarcan SQL Server Analysis Services 2016, ambos tienen el mismo comportamiento).

* Descargar las notas del producto del [filtrado cruzado bidireccional para Power BI Desktop](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)

### <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Habilitar el filtrado cruzado bidireccional para DirectQuery

Para habilitar el filtrado cruzado, en el cuadro de diálogo **Editar relación** de una relación, se debe seleccionar lo siguiente:

* La **Dirección del filtro cruzado** debe establecerse en **Ambos**
* **Aplicar filtro de seguridad en ambas direcciones** también debe estar seleccionado
  
  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Al crear fórmulas DAX de filtrado cruzado en Power BI Desktop, use *UserPrincipalName* (que suele ser el mismo que el inicio de sesión de un usuario, como *joe@contoso.com*) en lugar de *UserName*. Por tanto, puede que necesite crear una tabla relacionada que asigne *UserName* (o EmployeeID, por ejemplo) a *UserPrincipleName*.
> 
> 

Para obtener más información y ejemplos de cómo funciona el filtrado cruzado bidireccional, consulte las [notas del producto](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) mencionadas anteriormente en este artículo.

