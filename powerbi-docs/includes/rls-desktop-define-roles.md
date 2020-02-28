---
ms.openlocfilehash: 27d6db6cf8ad8ebd7b2c957954ceec34b83681d0
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464446"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definir roles y reglas en Power BI Desktop
Puede definir roles y reglas en Power BI Desktop. Al publicar en Power BI, publica también definiciones de roles.

Para definir los roles de seguridad, siga estos pasos.

1. Importar datos en el informe de Power BI Desktop o configurar una conexión de DirectQuery.
   
   > [!NOTE]
   > No puede definir roles en Power BI Desktop para conexiones dinámicas de Analysis Services. Debe hacerlo en el modelo de Analysis Services.
   > 
   > 
2. En la pestaña **Modelado**, seleccione **Administrar roles**.
   
   ![Selección de Administrar roles](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
3. En la ventana **Administrar roles**, seleccione **Crear**.
   
   ![Seleccionar Crear](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
4. En **Roles**, proporcione un nombre para el rol. 
5. En **Tablas**, seleccione la tabla a la que quiere aplicar una regla DAX.
6. En el cuadro **Expresión DAX de filtro de tabla**, escriba las expresiones DAX. Esta expresión devuelve un valor de true o false. Por ejemplo: ```[Entity ID] = “Value”```.
      
   ![Ventana Administrar roles](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)

   > [!NOTE]
   > Puede usar *username()* en esta expresión. Tenga en cuenta que *username()* tiene el formato *DOMINIO\usuario* en Power BI Desktop. En el servicio Power BI y en Power BI Report Server, está en el formato del nombre principal de usuario (UPN). Como alternativa, puede usar *userprincipalname()* , que siempre devuelve el usuario en el formato de su nombre principal de usuario, *username\@contoso.com*.
   > 
   > 

7. Después de haber creado la expresión DAX, seleccione la marca de verificación situada encima del cuadro de expresión para validar la expresión.
      
   ![Validación de la expresión DAX](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > En este cuadro de expresión, utilice comas para separar los argumentos de la función DAX, incluso si usa una configuración regional que normalmente usa separadores de punto y coma (por ejemplo, francés o alemán). 
   >
   >
   
8. Seleccione **Guardar**.

No puede asignar usuarios a un rol en Power BI Desktop. Los asigna en el servicio Power BI. Para habilitar la seguridad dinámica en Power BI Desktop, puede usar las funciones DAX *username()* y *userprincipalname()* . Las relaciones deben estar configuradas correctamente. 

