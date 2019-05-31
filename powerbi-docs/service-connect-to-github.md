---
title: Conexión a GitHub con Power BI
description: GitHub para Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: b0f2bd53f1d8b82b70072446723c2ca3723eeacd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65608440"
---
# <a name="connect-to-github-with-power-bi"></a>Conexión a GitHub con Power BI
Este artículo le guiará a través de extraer los datos de la cuenta de GitHub con una aplicación de la plantilla de Power BI. La aplicación de la plantilla genera un área de trabajo con un panel, un conjunto de informes y un conjunto de datos le permiten explorar los datos de GitHub. La aplicación de GitHub para Power BI le muestren información en el repositorio de GitHub, también conocido como repositorio, con datos en torno a las contribuciones, problemas, solicitudes de extracción y usuarios activos.

Después de instalar la aplicación de la plantilla, puede cambiar los paneles e informes. A continuación, puede distribuirla como una aplicación a los compañeros de su organización.

Conectarse a la [aplicación de la plantilla de GitHub](https://app.powerbi.com/getdata/services/github) u obtenga más información sobre la [integración con GitHub](https://powerbi.microsoft.com/integrations/github) con Power BI.

También puede probar la [GitHub tutorial](service-tutorial-connect-to-github.md). Instala datos reales de GitHub sobre el repositorio público de la documentación de Power BI.

>[!NOTE]
>La aplicación de la plantilla requiere que la cuenta de GitHub para tener acceso al repositorio. Consulte más detalles sobre los requisitos a continuación.

## <a name="how-to-connect"></a>Cómo conectarse
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]
   
3. Seleccione **GitHub** \> **obtenerla ahora**.
4. En **instalar esta aplicación de Power BI?** seleccione **instalar**.
4. En el **aplicaciones** panel, seleccione el **GitHub** icono.

    ![Icono de GitHub en Power BI](media/service-connect-to-github/power-bi-github-tile.png)

6. En **empezar a trabajar con la nueva aplicación**, seleccione **conectar datos**.

    ![Empezar a trabajar con la nueva aplicación](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

5. Escriba el nombre del repositorio y el propietario del repositorio. Consulte los detalles acerca de la [búsqueda de parámetros](#FindingParams) más adelante.
   
    ![Nombre del repositorio de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Escriba sus credenciales de GitHub (este paso se podría omitir si ya ha iniciado sesión con el explorador). 
6. En **Método de autenticación**, seleccione **oAuth2** \> **Iniciar sesión**. 
7. Siga las pantallas de autenticación de GitHub. Conceder permiso de aplicación de plantilla de Power BI a los datos de GitHub GitHub.
   
   ![Autorización de GitHub de Power BI](media/service-connect-to-github/github_authorize.png)
   
    Power BI se conecta a GitHub y los datos.  Los datos se actualizan una vez al día. Una vez que Power BI importe los datos, vea el contenido de la nueva área de trabajo de GitHub.

## <a name="modify-and-distribute-your-app"></a>Modificar y distribuir la aplicación

Ha instalado la aplicación de la plantilla de GitHub. Esto significa también que ha creado el área de trabajo de la aplicación GitHub. En el área de trabajo, puede cambiar los informes y el panel y distribuirla como un *aplicación* a compañeros de su organización. 

1. En la barra de navegación izquierdo, seleccione la flecha situada junto al nombre del área de trabajo. Verá que el área de trabajo contiene un panel y un informe.

    ![Aplicación en el panel de navegación izquierdo](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

8. Seleccione la nueva [panel de GitHub](https://powerbi.microsoft.com/integrations/github).    
    ![Panel de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

3. Para ver todo el contenido de la nueva área de trabajo de GitHub, en la barra de navegación izquierdo, seleccione **las áreas de trabajo** > **GitHub**.
 
   ![Área de trabajo de GitHub en el panel de navegación izquierdo](media/service-connect-to-github/power-bi-github-left-nav.png)

    Esta vista es la lista de contenido del área de trabajo. En la esquina superior derecha, verá **actualizar aplicación**. Cuando esté listo para distribuir la aplicación a sus compañeros, es donde podrá empezar. 

    ![Lista de contenido de GitHub](media/service-connect-to-github/power-bi-github-content-list.png)

2. Seleccione **informes** y **conjuntos de datos** para ver los demás elementos en el área de trabajo.

    Obtenga información sobre [distribuir aplicaciones](service-create-distribute-apps.md) a sus compañeros.

## <a name="whats-included-in-the-app"></a>¿Qué se incluye en la aplicación
Los siguientes datos están disponibles desde GitHub en Power BI:     

| Nombre de tabla | Descripción |
| --- | --- |
| Contribuciones |La tabla de contribuciones proporciona el total de adiciones, eliminaciones y confirmaciones creadas por el colaborador agregado por semana. Se incluyen los 100 colaboradores principales. |
| Problemas |Lista de todos los problemas para el repositorio seleccionado con cálculos como, por ejemplo, tiempo total y promedio para cerrar un problema, total de problemas abiertos o total de problemas cerrados. Esta tabla estará vacía cuando no haya ningún problema en el repositorio. |
| Solicitudes de extracción |Esta tabla contiene todas las solicitudes de extracción para el repositorio, así como quién extrajo la solicitud. También contiene cálculos de cuántas solicitudes de incorporación de cambios abiertas, cerradas y total, cuánto tiempo se tardó en las solicitudes de incorporación de cambios y cuánto tiempo tardó la solicitud de extracción promedio. Esta tabla estará vacía cuando no haya ningún problema en el repositorio. |
| Usuarios |Esta tabla proporciona una lista de usuarios de GitHub o colaboradores que han realizado aportaciones, presentado problemas o resuelto solicitudes de extracción para el repositorio seleccionado. |
| Hitos |Contiene todos los hitos para el repositorio seleccionado. |
| DateTable |Esta tabla contiene las fechas de hoy y los años anteriores que le permiten analizar los datos de GitHub por fecha. |
| ContributionPunchCard |Esta tabla puede usarse como una tarjeta perforada de contribución para el repositorio seleccionado. Muestra confirmaciones por día de la semana y hora del día. Esta tabla no está conectada a otras tablas en el modelo. |
| RepoDetails |Esta tabla proporciona detalles para el repositorio seleccionado. |

## <a name="system-requirements"></a>Requisitos del sistema
* La cuenta de GitHub que tiene acceso al repositorio.  
* Permiso concedido a la aplicación de Power BI para GitHub durante el primer inicio de sesión. Vea los detalles siguientes sobre la revocación del acceso.  
* Llamadas de API suficientes disponibles para extraer y actualizar los datos.  

### <a name="de-authorize-power-bi"></a>Quitar autorización de Power BI
Para quitar la autorización Power BI se conecte al repositorio de GitHub, puede revocar el acceso en GitHub. Vea este [ayuda de GitHub](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth) tema para obtener más información.

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>Búsqueda de parámetros
Para determinar el propietario y el repositorio, examine el repositorio en GitHub:

![Propietario y el nombre del repositorio](media/service-connect-to-github/github_ownerrepo.png)

La primera parte, "Azure", es el propietario y la segunda parte, "azure-sdk-for-php" es el repositorio mismo.  Verá estos dos mismos elementos en la dirección URL del repositorio:

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>Solución de problemas
Si es necesario, puede comprobar las credenciales de GitHub.  

1. En otra ventana del explorador, vaya al sitio web de GitHub e inicie sesión GitHub. Puede ver si está conectado en la esquina superior derecha del sitio de GitHub.    
2. En GitHub, vaya a la dirección URL del repositorio al que desea tener acceso en Power BI. Por ejemplo: https://github.com/dotnet/corefx.  
3. En Power BI, intente conectarse a GitHub. En el cuadro de diálogo Configurar GitHub, use los nombres del repositorio y el propietario del repositorio para dicho repositorio.  

## <a name="next-steps"></a>Pasos siguientes

* [Tutorial: Conectarse a un repositorio de GitHub con Power BI](service-tutorial-connect-to-github.md)
* [Crear las nuevas áreas de trabajo en Power BI](service-create-the-new-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](consumer/end-user-apps.md)
* [Conectarse a aplicaciones de Power BI para servicios externos](service-connect-to-services.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

