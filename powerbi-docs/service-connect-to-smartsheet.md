---
title: Conexión a Smartsheet con Power BI
description: Smartsheet para Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 841201aa87139b9630d6fc076d57109fb2b09804
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578890"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Conexión a Smartsheet con Power BI
Este artículo le guiará a través de extraer los datos de su cuenta de Smartsheet con una aplicación de la plantilla de Power BI. Smartsheet ofrece una plataforma sencilla para la colaboración y el uso compartido de archivos. La aplicación de la plantilla de Smartsheet para Power BI proporciona un panel, informes y conjunto de datos que muestra información general de la cuenta de Smartsheet. También puede usar [Power BI Desktop](desktop-connect-to-data.md) para conectarse directamente a hojas individuales en su cuenta. 

Después de instalar la aplicación de la plantilla, puede cambiar los paneles e informes. A continuación, puede distribuirla como una aplicación a los compañeros de su organización.

Conectarse a la [Smartsheet plantilla aplicación](https://app.powerbi.com/groups/me/getdata/services/smartsheet) para Power BI.

>[!NOTE]
>Una cuenta de administrador de Smartsheet es preferida para conectarse y cargar la aplicación de la plantilla de Power BI, ya que tiene acceso adicional.

## <a name="how-to-connect"></a>Cómo conectarse

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. Seleccione **Smartsheet** \> **obtenerla ahora**.
4. En **instalar esta aplicación de Power BI?** seleccione **instalar**.
4. En el **aplicaciones** panel, seleccione el **Smartsheet** icono.

    ![Icono de la aplicación de Power BI Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-tile.png)

6. En **empezar a trabajar con la nueva aplicación**, seleccione **conectar datos**.

    ![Empezar a trabajar con la nueva aplicación](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

4. En Método de autenticación, seleccione **oAuth2 \> Iniciar sesión**.
   
   Cuando se le solicite, escriba las credenciales de Smartsheet y siga el proceso de autenticación.
   
   ![Credenciales de Smartsheet](media/service-connect-to-smartsheet/creds.png)
   
   ![Inicio de sesión de Smartsheet](media/service-connect-to-smartsheet/creds2.png)

5. Una vez que Power BI importe los datos, se abre el panel de Smartsheet.
   
   ![Panel de Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>Modificar y distribuir la aplicación

Ha instalado la aplicación de la plantilla de Smartsheet. Esto significa también que ha creado el área de trabajo de aplicación de Smartsheet. En el área de trabajo, puede cambiar los informes y el panel y distribuirla como un *aplicación* a compañeros de su organización. 

1. Para ver todo el contenido de la nueva área de trabajo de Smartsheet, en la barra de navegación izquierdo, seleccione **las áreas de trabajo** > **Smartsheet**. 

    ![Área de trabajo de Smartsheet en el panel de navegación izquierdo](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace.png)

    Esta vista es la lista de contenido del área de trabajo. En la esquina superior derecha, verá **actualizar aplicación**. Cuando esté listo para distribuir la aplicación a sus compañeros, es donde podrá empezar. 

    ![Lista de contenido de Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace-content.png)

2. Seleccione **informes** y **conjuntos de datos** para ver los demás elementos en el área de trabajo.

    Obtenga información sobre [distribuir aplicaciones](service-create-distribute-apps.md) a sus compañeros.

## <a name="whats-included"></a>Qué se incluye
Tiene la Smartsheet plantilla aplicación de Power BI incluye información general de la cuenta Smartsheet, como el número de áreas de trabajo, informes y hojas que, cuando se modifican etcetera. Los usuarios administradores también ven cierta información en torno a los usuarios en su sistema, como los creadores de hojas más.  

Para conectarse directamente a hojas individuales de su cuenta, puede usar el conector de Smartsheet en [Power BI Desktop](desktop-connect-to-data.md).  

## <a name="next-steps"></a>Pasos siguientes

* [Crear las nuevas áreas de trabajo en Power BI](service-create-the-new-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](consumer/end-user-apps.md)
* [Conectarse a aplicaciones de Power BI para servicios externos](service-connect-to-services.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)