---
title: Filtrado cruzado bidireccional en Power BI Desktop
description: Habilitar el filtrado cruzado con DirectQuery en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 141dabdce7816d21c49d8c7f98d1438c2fc20e8d
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709829"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Habilitación del filtrado cruzado bidireccional para DirectQuery en Power BI Desktop

Al filtrar las tablas para crear la vista adecuada de los datos, los creadores de informes y los modeladores de datos se enfrentan a desafíos que determinan cómo aplicar filtros a un informe. Anteriormente, el contexto de filtro de la tabla se ha retenido en un lado de la relación, pero no en el otro. Esta organización a menudo requiere una fórmula DAX compleja para obtener los resultados deseados.

Con el filtrado cruzado bidireccional, los creadores de informes y los modeladores de datos ahora tienen más control sobre cómo pueden aplicar filtros al trabajar con tablas relacionadas. El filtrado cruzado bidireccional permite aplicar filtros en *ambos* lados de una relación de tabla. Puede aplicar los filtros propagando el contexto de filtro en una segunda tabla relacionada en el otro lado de una relación de tabla.

## <a name="enable-bidirectional-cross-filtering-for-directquery"></a>Habilitación del filtrado cruzado bidireccional para DirectQuery

Puede habilitar el filtrado cruzado en el cuadro de diálogo **Editar relación**. Para habilitar el filtrado cruzado de una relación, debe configurar las opciones siguientes:

* Establezca **Dirección del filtro cruzado** en **Ambos**.
* Seleccione **Aplicar filtro de seguridad en ambas direcciones**.

  ![Configure el filtrado cruzado bidireccional en Power BI Desktop.](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Al crear fórmulas DAX de filtrado cruzado en Power BI Desktop, use *UserPrincipalName*. Este campo suele ser el mismo que el inicio de sesión de un usuario, por ejemplo <em>joe@contoso.com</em>, en lugar de *UserName*. Por tanto, puede que necesite crear una tabla relacionada que asigne *UserName* o *EmployeeID* a *UserPrincipalName*.

Para obtener más información y ejemplos de cómo funciona el filtrado cruzado bidireccional, consulte las [notas del producto sobre el filtrado cruzado bidireccional para Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx).

