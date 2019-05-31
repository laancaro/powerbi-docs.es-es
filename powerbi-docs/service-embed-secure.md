---
title: Inserción de informes en un sitio web o portal seguro
description: Power BI inserta característica permite a los usuarios fácilmente e insertar informes de forma segura en los portales web interno.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222238"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Inserción de informes en un sitio web o portal seguro

Con el nuevo **Embed** informa de la opción para Power BI, puede insertar forma fácil y segura informes en los portales web interno. Estos portales pueden ser **basado en la nube** o **hospedadas localmente**, como SharePoint 2019. Informes insertados respeten todos los elemento permisos y seguridad de datos a través de [nivel de fila (RLS) seguridad](service-admin-rls.md). Proporciona sin código insertar en cualquier portal que acepta una dirección URL o un iFrame. 

El **Embed** opción admite [los filtros de URL](service-url-filters.md) y configuración de la URL. Permite integrar con los portales de utilizando un enfoque de poca cantidad de código que requiere solo HTML y JavaScript conocimientos básicos.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Cómo **insertar** informes de Power BI en portales

1. La nueva opción **Insertar** se encuentra disponible en el menú **Archivo** de informes del servicio Power BI.

    ![Opción de lista desplegable de opciones de inserción segura](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Seleccione el **Embed** opción para abrir un cuadro de diálogo que proporciona un vínculo y un iFrame que puede usar para insertar el informe de forma segura.

    ![Cuadro de diálogo con la opción Insertar](media/service-embed-secure/secure-embed-code-dialog.png)

3. Si un usuario abre una dirección URL de informe directamente, o uno incrustado en un portal web, el acceso de informes requiere autenticación. Si un usuario ha no iniciado sesión en Power BI en su sesión del explorador, aparecerá la siguiente pantalla. Cuando selecciona **inicio de sesión**, se puede abrir una nueva ventana del explorador o la pestaña. Hacer que comprueben de bloqueadores de elementos emergentes si no pedirá que inicie sesión.

    ![Iniciar sesión para ver el informe](media/service-embed-secure/secure-embed-sign-in.png)

4. Después de que el usuario ha iniciado sesión, se abre el informe muestra los datos y permite la navegación de página y la configuración del filtro. Solo los usuarios que tienen permiso de vista pueden ver el informe en Power BI. Todos los [nivel de fila (RLS) seguridad](service-admin-rls.md) también se aplican las reglas. Por último, el usuario debe tener la licencia correcta: necesita una licencia de Power BI Pro o el informe debe estar en un área de trabajo que tenga una capacidad de Power BI Premium. El usuario debe iniciar sesión cada vez que abran una nueva ventana del explorador. Sin embargo, cuando haya iniciado sesión, otros informes de cargan automáticamente.

    ![Informe de inserción](media/service-embed-secure/secure-embed-report.png)

5. Cuando se usa un iFrame, es posible que deba editar la **alto** y **ancho** para que quepan en la página web de su portal.

    ![Establecimiento del alto y ancho](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Conceder acceso a los informes

El **Embed** opción automáticamente no permite a los usuarios para ver el informe. Ver los permisos se establecen en el servicio Power BI.

En el servicio Power BI, puede compartir informes incrustados con usuarios que requieren acceso. Si usa un grupo de Office 365, puede enumerar el usuario como un miembro del área de trabajo de aplicación. Para obtener más información, vea cómo [administrar el área de trabajo de aplicación en Power BI y Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licencias

Para ver el informe insertado, los usuarios necesitan una licencia de Power BI Pro o el contenido debe estar en un área de trabajo que se encuentra en un [capacidad de Power BI Premium (EM o SKU P)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Personalización de la experiencia de inserción con la configuración de direcciones URL

Puede personalizar la experiencia del usuario mediante la configuración de la dirección URL entrada. En el iFrame proporcionado, puede actualizar la dirección de URL **src** configuración.

| Propiedad  | Descripción  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Puede usar el **pageName** parámetro de cadena para establecer qué página del informe para abrir consulta. Puede encontrar este valor al final de la dirección URL de informe al ver un informe en el servicio Power BI, tal como se muestra a continuación. |  |  |  |
| Filtros de direcciones URL  | Puede usar [los filtros de URL](service-url-filters.md) en la dirección URL que recibió de la interfaz de usuario de Power BI para filtrar el contenido de inserción. De este modo, puede compilar integraciones de código reducido con una experiencia básica de HTML y JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Conjunto de página que se abre para un informe incrustado 

Puede encontrar el **pageName** valor al final de la URL informe al ver un informe en el servicio Power BI.

1. Abra el informe desde el servicio Power BI en el explorador web y, a continuación, copie la dirección URL de la barra de direcciones.

    ![Sección del informe](media/service-embed-secure/secure-embed-report-section.png)

2. Anexe el valor de **pageName** a la dirección URL.

    ![Anexión de pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrado del contenido de informes con filtros de direcciones URL 

Puede usar [los filtros de URL](service-url-filters.md) para proporcionar vistas diferentes de informes. Por ejemplo, la dirección URL siguiente filtra el informe para mostrar los datos del sector energético.

El uso de **pageName** con [filtros de direcciones URL](service-url-filters.md) puede ser eficaz. Puede crear experiencias con HTML y JavaScript básicos.

Por ejemplo, este es un botón que puede agregar a una página HTML:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Cuando se selecciona, el botón llama a una función para actualizar el iFrame con una dirección URL actualizada, que incluye el filtro de la industria energética.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtrar](media/service-embed-secure/secure-embed-filter.png)

Puede agregar tantos botones como quiera para crear una experiencia personalizada de código reducido. 

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* No admite usuarios invitados externos con Azure B2B (negocio a negocio).

* La inserción segura funciona en informes publicados en el servicio Power BI.

* El usuario debe iniciar sesión ver el informe cada vez que abra una nueva ventana del explorador.

* Algunos exploradores requieren que actualice la página de inicio de sesión, especialmente cuando se usa en los modos de InPrivate o Incognito.

* Para lograr una experiencia de inicio de sesión único, use la inserción en la opción de SharePoint Online o crear una integración personalizada mediante el [usuario posee los datos](developer/embed-sample-for-your-organization.md) incrustación de método. 

* La funcionalidad de autenticación automática que se incluye con la opción **Insertar** no funciona con la API de JavaScript para Power BI. Para la API de JavaScript de Power BI, use el [usuario posee los datos](developer/embed-sample-for-your-organization.md) incrustación de método. 

## <a name="next-steps"></a>Pasos siguientes

* [Formas de compartir su trabajo en Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrar un informe con parámetros de cadena de consulta en la dirección URL](service-url-filters.md)

* [Insertar elemento web de informes en SharePoint Online](service-embed-report-spo.md)

* [Publicar en Web de Power BI](service-publish-to-web.md)