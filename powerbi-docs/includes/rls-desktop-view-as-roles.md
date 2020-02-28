---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464415"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Validar los roles en Power BI Desktop
Después de haber creado los roles, pruebe sus resultados en Power BI Desktop.

1. En la pestaña **Modelado**, seleccione **Ver como roles**. 

    ![Selección de Ver como roles](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Se abre la ventana **Ver como roles**, en la que se muestran los roles que ha creado.

    ![Ventana Ver como roles](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Seleccione un rol que haya creado y después **Aceptar** para aplicarlo. 

   Los informes representan los datos pertinentes para ese rol.

4. También puede seleccionar **Otro usuario** y proporcionar un usuario determinado. 

    ![Selección de otro usuario](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   Es mejor proporcionar el nombre principal de usuario (UPN), ya que es el que usarán el servicio Power BI y Power BI Report Server.

   En Power BI Desktop, **Otro usuario** solo muestra otros resultados si usa la seguridad dinámica basada en las expresiones DAX. 

5. Seleccione **Aceptar**. 

   El informe se representará en función de lo que pueda ver ese usuario.



