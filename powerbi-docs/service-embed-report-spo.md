---
title: Insertar el elemento web de informes en SharePoint Online
description: Con el nuevo elemento web de informes de Power BI para SharePoint Online, puede insertar fácilmente informes de Power BI interactivos en páginas de SharePoint Online.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 12/18/2019
ms.openlocfilehash: d1ac9238e361a0889e52838eb0b3c3889c1cccf7
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "75221721"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Insertar el elemento web de informes en SharePoint Online

Con el nuevo elemento web de informes de Power BI para SharePoint Online, puede insertar fácilmente informes de Power BI interactivos en páginas de SharePoint Online.

Con la nueva opción **Insertar en SharePoint Online**, los informes insertados están completamente seguros para que pueda crear fácilmente portales internos seguros.

## <a name="requirements"></a>Requisitos

Para que los informes de **Insertar en SharePoint Online** funcionen, se necesita lo siguiente:

* Una licencia de Power BI Pro o una [capacidad Power BI Premium (EM o P SKU)](service-premium-what-is.md) con una licencia de Power BI.
* El elemento web de Power BI para SharePoint Online requiere [páginas modernas](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).
* Para consumir un informe insertado, los usuarios deben iniciar sesión en el servicio Power BI para activar su licencia de Power BI.

## <a name="embed-your-report"></a>Insertar un informe
Para insertar un informe en SharePoint Online, se debe obtener la dirección URL del informe y usarla con el elemento web de Power BI de SharePoint Online.

### <a name="get-a-report-url"></a>Obtención e una dirección URL del informe

1. En Power BI, vea el informe.

2. Seleccione el menú desplegable **Archivo** y luego seleccione **Insertar en SharePoint Online**.

    ![Menú Abrir](media/service-embed-report-spo/powerbi-file-menu.png)

3. Copie la dirección URL del informe desde el cuadro de diálogo.

    ![Inserción de vínculo](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Agregar el informe de Power BI a una página de SharePoint Online

1. Abra la página de destino en SharePoint Online y seleccione **Editar**.

    ![Página de ediciones de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    O bien, seleccione **+ Nuevo** en SharePoint Online para crear una nueva página de sitio moderna.

    ![Nueva página de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Seleccione el menú desplegable **+** y, después, seleccione el elemento web **Power BI**.

    ![Nuevo elemento web de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Seleccione **Agregar informe**.

    ![Nuevo informe de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Pegue la dirección URL del informe copiado previamente en el panel **Vínculo de informe de Power BI**. El informe se carga automáticamente.

    ![Nuevas propiedades del elemento web de SharePoint](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Seleccione **Publicar** para que los cambios sean visibles para los usuarios de SharePoint Online.

    ![Informe de SharePoint cargado](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Concesión de acceso a los informes

Insertar un informe en SharePoint Online no da a los usuarios permiso para ver el informe de forma automática: se necesitan establecer permisos de vista en Power BI.

> [!IMPORTANT]
> Asegúrese de revisar quién puede ver el informe en el servicio Power BI y de conceder acceso a los usuarios que no están en la lista.

Hay dos formas de proporcionar acceso a los informes en Power BI. La primera, si se usa un grupo de Office 365 para compilar el sitio de grupo de SharePoint Online, es enumerar a los usuarios como miembros del **área de trabajo en el servicio Power BI** y la **página de SharePoint**. Para más información, consulte [Administración de un área de trabajo](service-manage-app-workspace-in-power-bi-and-office-365.md).

La segunda consiste en insertar un informe en una aplicación y compartirla directamente con los usuarios:  

1. El autor, que debe ser un usuario Pro, crea un informe en un área de trabajo. Para compartirla con *usuarios gratuitos de Power BI*, el área de trabajo debe establecerse como un *área de trabajo Premium*.

2. El autor publica la aplicación y la instala. El autor debe instalar la aplicación para que tenga acceso a la dirección URL del informe que se usa para la inserción en SharePoint Online.

3. Ahora todos los usuarios finales también necesitan instalar la aplicación. También se puede usar la característica **Instalar la aplicación automáticamente**, que se puede habilitar en el [portal de administración de Power BI](service-admin-portal.md), con el fin de tener la aplicación preinstalada para los usuarios finales.

   ![Instalar aplicación automáticamente](media/service-embed-report-spo/install-app-automatically.png)

4. El autor abre la aplicación y accede al informe.

5. El autor copia la dirección URL del informe insertado desde el informe que ha instalado la aplicación. No use la dirección URL del informe original desde el área de trabajo.

6. Cree un sitio del equipo en SharePoint Online.

7. Agregue la dirección URL del informe copiada anteriormente en el elemento web de Power BI.

8. Agregue todos los usuarios finales o grupos que van a consumir los datos en la página de SharePoint Online y en la aplicación de Power BI que creó.

    > [!NOTE]
    > **Los usuarios o grupos necesitan acceso a la página de SharePoint Online y al informe de la aplicación de Power BI para ver el informe en la página de SharePoint.**

Ahora el usuario final puede ir al sitio del equipo en SharePoint Online y ver los informes en la página.

## <a name="multi-factor-authentication"></a>Autenticación multifactor

Si el entorno de Power BI exige que inicie sesión con la autenticación multifactor, es posible que se le pida que inicie sesión con un dispositivo de seguridad para verificar su identidad. Esto ocurre si no se ha iniciado sesión en SharePoint Online mediante la autenticación multifactor, pero el entorno de Power BI requiere un dispositivo de seguridad para validar una cuenta.

> [!NOTE]
> Power BI no admite todavía la autenticación multifactor con Azure Active Directory 2.0: los usuarios verán un mensaje de error. Si el usuario inicia sesión de nuevo en SharePoint Online con su dispositivo de seguridad, podría ver el informe.

## <a name="web-part-settings"></a>Configurar el elemento web

Debajo se muestran la configuración que se puede ajustar para el elemento web de Power BI en SharePoint Online.

![Propiedades de elementos web del procedimiento almacenado](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propiedad | Descripción |
| --- | --- |
| Nombre de página |Establece la página predeterminada del elemento web. Seleccione un valor en la lista desplegable. Si no se muestra ninguna página, el informe contiene una página o la dirección URL que pegó contiene un nombre de página. Quite la sección del informe de la dirección URL para seleccionar una página específica. |
| Mostrar |Regula cómo se ajusta el informe en la página de SharePoint Online. |
| Mostrar panel de navegación |Muestra u oculta el panel de navegación de páginas. |
| Mostrar panel de filtros |Muestra u oculta el panel de filtro. |

## <a name="reports-that-do-not-load"></a>Informes que no se cargan

Si el informe no se carga en el elemento web de Power BI, puede que se vea el mensaje siguiente:

![Mensaje que muestra que este contenido no está disponible.](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Normalmente, hay dos razones para este mensaje.

1. No se tiene acceso a los informes.
2. El informe se eliminó.

Póngase en contacto con el propietario de la página de SharePoint Online para que le ayude a resolver la incidencia.

## <a name="licensing"></a>Licencias

Los usuarios que ven un informe en SharePoint necesitan una **licencia de Power BI Pro** o el contenido debe estar en un área de trabajo que tenga una **[capacidad de Power BI Premium (SKU EM o P)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

* Error: "An error occurred, please try logging out and back in and then revisiting this page. (Se ha producido un error, intente cerrar la sesión y abrirla de nuevo, y vuelva a esta página). Id. de correlación: indefinido, estado de respuesta de http: 400, código de error: 10001,mensaje: Falta el token de actualización"
  
  Si recibe este error, intente uno de los pasos de solución de problemas que se indican a continuación.
  
  1. Cierre sesión en SharePoint e iníciela de nuevo. Asegúrese de cerrar todas las ventanas del explorador antes de iniciar sesión.

  2. Si la cuenta de usuario requiere autenticación multifactor (MFA), inicie sesión en SharePoint con el dispositivo de MFA (aplicación de teléfono, tarjeta inteligente, etc.).
  
  3. No se admiten las cuentas de invitado de Azure B2B. Los usuarios ven el logotipo de Power BI que muestra que el componente se está cargando, pero el informe no aparece.

* Power BI no admite los mismos idiomas localizados que SharePoint Online. En consecuencia, es posible que no vea una localización correcta en el informe insertado.

* Si utiliza Internet Explorer 10, pueden surgir problemas. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->

* El elemento web de Power BI no está disponible para [nubes nacionales](https://powerbi.microsoft.com/clouds/).

* El clásico SharePoint Server no es compatible con este elemento web.

* Los [filtros de URL](service-url-filters.md) no son compatibles con el elemento web de SPO.

## <a name="next-steps"></a>Pasos siguientes

* [Permitir o impedir la creación de páginas de sitio modernas por los usuarios finales](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Creación y distribución de una aplicación en Power BI](service-create-distribute-apps.md)  
* [Compartir un panel con compañeros y otros usuarios](service-share-dashboards.md)  
* [¿Qué es Power BI Premium?](service-premium-what-is.md)
* [Inserción de informes en un sitio web o portal seguro](service-embed-secure.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
