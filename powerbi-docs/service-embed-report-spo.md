---
title: Insertar el elemento web de informes en SharePoint Online
description: Con el nuevo elemento web de informes de Power BI para SharePoint Online, puede insertar fácilmente informes de Power BI interactivos en páginas de SharePoint Online.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051262"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Insertar el elemento web de informes en SharePoint Online

Con el nuevo elemento web de informes de Power BI para SharePoint Online, puede insertar fácilmente informes de Power BI interactivos en páginas de SharePoint Online.

Cuando se usa el nuevo **insertar en SharePoint Online** opción, los informes insertados están completamente seguros, por lo que puede crear fácilmente portales internos seguros.

## <a name="requirements"></a>Requisitos

Para **insertar en SharePoint Online** informes funcione, es necesario lo siguiente:

* Una licencia de Power BI Pro o una [capacidad de Power BI Premium (EM o SKU P)](service-premium-what-is.md) con una licencia de Power BI.
* El elemento web de Power BI para SharePoint Online requiere [páginas modernas](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Insertar un informe
Para insertar un informe en SharePoint Online, debe obtener la dirección URL de informe y su uso con nuevo elemento web de Power BI del SharePoint en línea.

### <a name="get-a-report-url"></a>Obtener una dirección URL de informe

1. En Power BI, vea el informe.

2. Seleccione el **archivo** menú desplegable, seleccione **insertar en SharePoint Online**.

    ![Menú Abrir](media/service-embed-report-spo/powerbi-file-menu.png)

3. Copie la dirección URL de informe desde el cuadro de diálogo.

    ![Inserción de vínculo](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Agregar el informe de Power BI a una página de SharePoint Online

1. Abra la página de destino en SharePoint Online y seleccione **editar**.

    ![Página de ediciones de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    O bien, en Sharepoint Online, seleccione **+ nuevo** para crear una nueva página de sitio moderna.

    ![Nueva página de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Seleccione el **+** lista desplegable y, a continuación, seleccione el **Power BI**.

    ![Nuevo elemento web de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Seleccione **Agregar informe**.

    ![Nuevo informe de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Pegue la dirección URL de informe copiado previamente en el **vínculo de informe de Power BI** panel. El informe se carga automáticamente.

    ![Nuevas propiedades del elemento web de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Seleccione **Publicar** para que los cambios sean visibles para los usuarios de SharePoint Online.

    ![Informe de SharePoint cargado](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Concesión de acceso a los informes

Insertar un informe en SharePoint Online no asignar automáticamente a los usuarios permiso para ver el informe, debe establecer permisos para ver en Power BI.

> [!IMPORTANT]
> Asegúrese de revisar quién puede ver el informe en el servicio Power BI y de conceder acceso a los usuarios que no están en la lista.

Hay dos formas de proporcionar acceso a los informes en Power BI. Es la primera forma, si usa un grupo de Office 365 para crear el sitio de grupo SharePoint Online mostrar al usuario como miembro de la **área de trabajo de aplicación dentro del servicio Power BI** y **página de SharePoint**. Para obtener más información, vea [Administración de un área de trabajo de la aplicación](service-manage-app-workspace-in-power-bi-and-office-365.md).

La segunda consiste en Insertar un informe dentro de una aplicación y compartirlo directamente con los usuarios:  

1. El autor (debe ser un usuario Pro) crea un informe en un área de trabajo de aplicación. Para compartir con **usuarios gratuitos de Power BI**, el área de trabajo debe establecerse como un **área de trabajo Premium**.

2. El autor publica la aplicación y lo instala. El autor debe asegurarse de que instale la aplicación para tener acceso a la dirección URL de informe que se usa para insertar en SharePoint Online.

3. Ahora todos los usuarios finales también necesitan instalar la aplicación. También puede usar el **instala la aplicación automáticamente** característica, que se puede habilitar en el [portal de administración de Power BI](service-admin-portal.md), para que la aplicación instalada previamente para los usuarios finales.

   ![Instalar aplicación automáticamente](media/service-embed-report-spo/install-app-automatically.png)

4. El autor abre la aplicación y accede al informe.

5. El autor de la copia la dirección URL de informe desde el informe de la aplicación instalada. **No use la dirección URL del informe original desde el área de trabajo.**

6. Cree un sitio del equipo en SharePoint Online.

7. Agregue la URL del informe copiado previamente para el elemento web de Power BI.

8. Agregue todos los usuarios finales o grupos que van a consumir los datos en la página de SharePoint Online y en la aplicación de Power BI que creó.

    > [!NOTE]
    > **Los usuarios o grupos necesitan acceso a la página de SharePoint Online y al informe de la aplicación de Power BI para ver el informe en la página de SharePoint.**

Ahora el usuario final puede ir al sitio del equipo en SharePoint Online y ver los informes en la página.

## <a name="multi-factor-authentication"></a>Autenticación multifactor

Si el entorno de Power BI exige que inicie sesión con la autenticación multifactor, es posible que se le pida que inicie sesión con un dispositivo de seguridad para verificar su identidad. Esto ocurre si no han iniciado sesión SharePoint Online mediante la autenticación multifactor, pero su entorno de Power BI requiere un dispositivo de seguridad para validar una cuenta.

> [!NOTE]
> Azure Active Directory 2.0 no admite la autenticación multifactor, los usuarios verán un mensaje de error. Si el usuario inicia sesión de nuevo en SharePoint Online con su dispositivo de seguridad, podría ver el informe.

## <a name="web-part-settings"></a>Configurar el elemento web

A continuación se muestran los valores que puede ajustar para el elemento web de Power BI para SharePoint Online.

![Propiedades de elementos web del procedimiento almacenado](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propiedad | Descripción |
| --- | --- |
| Nombre de página |Establece la página de predeterminada del elemento web. Seleccione un valor en la lista desplegable. Si no se muestra ninguna página, el informe contiene una página o la dirección URL que pegó contiene un nombre de página. Quite la sección del informe de la dirección URL para seleccionar una página específica. |
| Pantalla |Ajusta cómo encaja el informe dentro de la página de SharePoint Online. |
| Mostrar panel de navegación |Muestra u oculta el panel de navegación de páginas. |
| Mostrar el panel de filtro |Muestra u oculta el panel de filtro. |

## <a name="reports-that-do-not-load"></a>Informes que no se cargan

Si el informe no se carga en el elemento web de Power BI, verá el mensaje siguiente:

![Este contenido no está disponible mensaje](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Normalmente, hay dos razones para este mensaje.

1. No tiene acceso a los informes.
2. El informe se eliminó.

Póngase en contacto con el propietario de la página de SharePoint Online para ayudar a resolver el problema.

## <a name="licensing"></a>Licencias

Los usuarios que ven un informe en SharePoint necesitan una **licencia de Power BI Pro** o el contenido debe estar en un área de trabajo que tenga una **[capacidad de Power BI Premium (SKU EM o P)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

* Error: "An error occurred, please try logging out and back in and then revisiting this page. (Se ha producido un error, intente cerrar la sesión y abrirla de nuevo, y vuelva a esta página). Id. de correlación: indefinido, estado de respuesta de http: 400, código de error: 10001,mensaje: Falta el token de actualización"
  
  Si recibe este error, intente uno de los pasos de solución de problemas que se indican a continuación.
  
  1. Cierre sesión en SharePoint e iníciela de nuevo. Asegúrese de cerrar todas las ventanas del explorador antes de iniciar sesión.

  2. Si su cuenta de usuario requiere autenticación multifactor (MFA), a continuación, inicie sesión en SharePoint con el dispositivo MFA (aplicación de teléfono, tarjeta inteligente, etcetera.).
  
  3. No se admiten las cuentas de invitado de Azure B2B. Los usuarios ven el logotipo de Power BI que muestra que el componente se está cargando, pero el informe no aparece.

* Power BI no admite los mismos idiomas localizados que SharePoint Online. En consecuencia, es posible que no vea una localización correcta en el informe insertado.

* Si utiliza Internet Explorer 10, pueden surgir problemas. Puede consultar el artículo [Exploradores compatibles con Power BI](consumer/end-user-browsers.md) y los [requisitos del sistema de Office 365](https://products.office.com/office-system-requirements#Browsers-section).

* El elemento web de Power BI no está disponible para [nubes nacionales](https://powerbi.microsoft.com/clouds/).

* El clásico SharePoint Server no es compatible con este elemento web.

* Los [filtros de URL](service-url-filters.md) no son compatibles con el elemento web de SPO.

## <a name="next-steps"></a>Pasos siguientes

* [Permitir o impedir la creación de páginas de sitio modernas por los usuarios finales](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Creación y distribución de una aplicación en Power BI](service-create-distribute-apps.md)  
* [Compartir un panel con compañeros y otros usuarios](service-share-dashboards.md)  
* [¿Qué es Power BI Premium?](service-premium-what-is.md)
* [Inserción de informes en un sitio web o portal seguro](service-embed-secure.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)