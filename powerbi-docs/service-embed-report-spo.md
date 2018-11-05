---
title: Insertar el elemento web de informes en SharePoint Online
description: Con el nuevo elemento web de informes de Power BI para SharePoint Online, puede insertar fácilmente informes de Power BI interactivos en páginas de SharePoint Online.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 10/20/2018
ms.openlocfilehash: e336323863dfacc8c74f2dc1f721231d58d03834
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100781"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Insertar el elemento web de informes en SharePoint Online

Con el nuevo elemento web de informes de Power BI para SharePoint Online, puede insertar fácilmente informes de Power BI interactivos en páginas de SharePoint Online.

Con la nueva opción **Insertar en SharePoint Online**, los informes insertados están completamente seguros para que pueda crear fácilmente portales internos seguros.

## <a name="requirements"></a>Requisitos

Hay algunos requisitos para que la opción **Insertar en SharePoint Online** funcione.

* Necesita una licencia de Power BI Pro o una [capacidad Power BI Premium (EM o P SKU)](service-premium.md#premium-capacity-nodes) con una licencia de Power BI.
* El elemento web de Power BI para SharePoint Online requiere [páginas modernas](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Insertar un informe

Para insertar el informe en SharePoint Online, primero debe obtener la dirección URL del informe y luego usarla con el nuevo elemento web de Power BI en SharePoint Online.

### <a name="get-a-url-to-your-report"></a>Obtener la dirección URL del informe

1. Vea el informe en el servicio Power BI.

2. Seleccione el elemento de menú **Archivo**.

3. Seleccione **Insertar en SharePoint Online**.

    ![Menú Abrir](media/service-embed-report-spo/powerbi-file-menu.png)

4. Copie la dirección URL del cuadro de diálogo.

    ![Inserción de vínculo](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Agregar el informe de Power BI a una página de SharePoint Online

1. Abra la página que desee en SharePoint Online y seleccione **Editar**.

    ![Página de ediciones de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    O bien, seleccione **+ Nuevo** en SharePoint Online para crear una nueva página de sitio moderna.

    ![Nueva página de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Seleccione **+** y seleccione el elemento web **Power BI**.

    ![Nuevo elemento web de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Seleccione **Agregar informe**.

    ![Nuevo informe de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)

4. Pegue la dirección URL del informe en el panel de propiedades. Esta dirección URL de informe es la dirección URL que copió en los pasos anteriores. El informe se carga automáticamente.

    ![Nuevas propiedades del elemento web de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Seleccione **Publicar** para que los cambios sean visibles para los usuarios de SharePoint Online.

    ![Informe de SharePoint cargado](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="granting-access-to-reports"></a>Conceder acceso a los informes

Insertar un informe en SharePoint Online no da a los usuarios permiso para ver el informe de forma automática. Los permisos para ver el informe se establecen en el servicio Power BI.

> [!IMPORTANT]
> Asegúrese de revisar quién puede ver el informe en el servicio Power BI y de conceder acceso a los usuarios que no están en la lista.

Hay dos formas de proporcionar acceso al informe dentro del servicio Power BI. Si usa un grupo de Office 365 para compilar el sitio de grupo de SharePoint Online, los usuarios aparecen como miembros del **área de trabajo de la aplicación en el servicio Power BI** y la **página de SharePoint**. De este modo se asegura de que los usuarios puedan ver el contenido de ese grupo. Para más información, consulte [Creación y distribución de una aplicación en Power BI](service-create-distribute-apps.md).

Además, puede compartir un informe directamente con los usuarios insertando el informe en una aplicación. La aplicación debe estar preinstalada para que el informe se inserte. Puede configurar la aplicación para que se preinstale mediante la función **Instala la aplicación automáticamente**.

   ![Instala la aplicación automáticamente](media/service-embed-report-spo/install-app-automatically.png)

> [!NOTE]
> **El usuario necesita acceso tanto a la página de SharePoint como al informe para ver el informe en la página de SharePoint.**

## <a name="multi-factor-authentication"></a>Autenticación multifactor

Si el entorno de Power BI exige que inicie sesión con la autenticación multifactor, es posible que se le pida que inicie sesión con un dispositivo de seguridad para verificar su identidad. Esto ocurre si no ha iniciado sesión en SharePoint Online mediante la autenticación multifactor, pero el entorno de Power BI requiere una cuenta validada por un dispositivo de seguridad.

> [!NOTE]
> La autenticación multifactor no es compatible todavía con Azure Active Directory 2.0. Los usuarios reciben un mensaje que indica *error*. Si el usuario inicia sesión de nuevo en SharePoint Online con su dispositivo de seguridad, podría ver el informe.

## <a name="web-part-settings"></a>Configurar el elemento web

A continuación, se muestra una descripción de las opciones que se pueden ajustar para el elemento web de Power BI para SharePoint Online.

![Propiedades de elementos web del procedimiento almacenado](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propiedad | Descripción |
| --- | --- |
| Nombre de la página |Establece la página predeterminada que se muestra en el elemento web. Seleccione un valor en la lista desplegable. Si no se muestra ninguna página, el informe contiene una página o la dirección URL que pegó contiene un nombre de página. Quite la sección del informe de la dirección URL para seleccionar una página específica. |
| Mostrar |Opción para ajustar el informe en la página de SharePoint Online. |
| Mostrar el panel de navegación |Muestra u oculta el panel de navegación de páginas. |
| Mostrar el panel de filtro |Muestra u oculta el panel de filtro. |

## <a name="reports-that-do-not-load"></a>Informes que no se cargan

Puede que el informe no se cargue en el elemento web de Power BI y aparezca el mensaje siguiente.

*Este contenido no está disponible.*

![Mensaje de informe no encontrado](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Normalmente, hay dos razones para este mensaje.

1. No tiene acceso al informe.
2. El informe se eliminó.

Póngase en contacto con el propietario de la página de SharePoint Online para ayudarle a resolver el problema.

## <a name="licensing"></a>Licencias

Los usuarios que ven un informe en SharePoint necesitan una **licencia de Power BI Pro** o el contenido debe estar en un área de trabajo que tenga una **[capacidad de Power BI Premium (SKU EM o P)](service-admin-premium-purchase.md)**.

## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

* Error: "An error occurred, please try logging out and back in and then revisiting this page. Correlation id: undefined, http response status: 400, server error code 10001, message: Missing refresh token" ("Se ha producido un error, intente cerrar la sesión y abrirla de nuevo, y vuelva a esta página. Id. de correlación: no definido, estado de respuesta http: 400, código de error de servidor 10001, mensaje: falta token de actualización")
  
  Si recibe este error, intente uno de los pasos de solución de problemas que se indican a continuación.
  
  1. Cierre sesión en SharePoint e iníciela de nuevo. Asegúrese de cerrar todas las ventanas del explorador antes de iniciar sesión.

  2. Si la cuenta de usuario requiere autenticación multifactor (MFA), asegúrese de iniciar sesión en SharePoint con el dispositivo de autenticación multifactor (aplicación de teléfono, tarjeta inteligente, etc.)
  
  3. No se admiten las cuentas de invitado de Azure B2B. Los usuarios ven el logotipo de Power BI que muestra que el componente se está cargando, pero el informe no aparece.

* Power BI no admite los mismos idiomas localizados que SharePoint Online. En consecuencia, es posible que no vea una localización correcta en el informe insertado.

* Si utiliza Internet Explorer 10, pueden surgir problemas. Puede consultar el artículo [Exploradores compatibles con Power BI](consumer/end-user-browsers.md) y los [requisitos del sistema de Office 365](https://products.office.com/office-system-requirements#Browsers-section).

* El elemento web de Power BI no está disponible en las [nubes soberanas](https://powerbi.microsoft.com/en-us/clouds/).

* El clásico SharePoint Server no es compatible con este elemento web.

* Los [filtros de URL](service-url-filters.md) no son compatibles con el elemento web de SPO.

## <a name="next-steps"></a>Pasos siguientes

[Permitir o impedir la creación de páginas de sitio modernas por los usuarios finales](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
[Creación y distribución de una aplicación en Power BI](service-create-distribute-apps.md)  
[Compartir un panel con compañeros y otros usuarios](service-share-dashboards.md)  
[¿Qué es Power BI Premium?](service-premium.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)