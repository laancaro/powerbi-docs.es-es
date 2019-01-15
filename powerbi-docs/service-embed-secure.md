---
title: Inserción de informes en un sitio web o portal seguro
description: Con la función de inserción segura de Power BI, puede permitir que los usuarios inserten informes de forma fácil y segura en portales web internos.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2019
LocalizationGroup: Share your work
ms.openlocfilehash: b816b504d3eed3aa91eb25c0bb3c6189d3075d1f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285838"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Inserción de informes en un sitio web o portal seguro

La nueva opción **Insertar** segura para informes de Power BI permite a los usuarios insertar informes de forma fácil y segura en portales web internos, tanto **basados en la nube** u **hospedados en el entorno local**, como SharePoint 2019. Los informes insertados de esta manera respetan todos los permisos del elemento y la seguridad de los datos a través de la seguridad a nivel de fila (RLS). La característica está diseñada para permitir la inserción sin código en cualquier portal que acepte que se inserte una dirección URL o un iFrame.

La opción **Insertar** admite también la configuración de direcciones URL y [filtros de direcciones URL](service-url-filters.md). La opción **Insertar** le permite integrarse en portales con un enfoque de código reducido que requiere conocimientos básicos de HTML y JavaScript.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Cómo **insertar** informes de Power BI en portales

1. La nueva opción **Insertar** se encuentra disponible en el menú **Archivo** de informes del servicio Power BI.

    ![Opción de lista desplegable de opciones de inserción segura](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Seleccione la opción de inserción para abrir un cuadro de diálogo que ofrece un vínculo y un iFrame que permite insertar el informe de forma segura.

    ![Cuadro de diálogo con la opción Insertar](media/service-embed-secure/secure-embed-code-dialog.png)

3. Después de insertar la dirección URL en el portal web, o si abre directamente la dirección URL, el usuario se autentica antes de darle acceso al informe. Abajo vemos que el usuario ha no iniciado sesión en Power BI en la sesión del explorador. Cuando presiona **Iniciar sesión**, es posible que tenga que abrir una nueva ventana o pestaña del explorador. Compruebe los bloqueadores de elementos emergentes si se no le solicita que inicie sesión.

    ![Iniciar sesión para ver el informe](media/service-embed-secure/secure-embed-sign-in.png)

4. Cuando el usuario ha iniciado sesión, el informe se abre y muestra los datos, lo que permite a los usuarios navegar entre páginas y establecer filtros. El informe se muestra únicamente a los usuarios que tienen permiso para ver el informe en Power BI. También se aplican todas las reglas de seguridad de nivel de fila (RLS). Por último, el usuario debe tener la licencia correcta: necesita una licencia de Power BI Pro o el informe debe estar en un área de trabajo que tenga una capacidad de Power BI Premium. El usuario debe iniciar sesión cada vez que abra una nueva ventana del explorador, pero, tras iniciar sesión una vez, otros informes se cargan automáticamente.

    ![Informe de inserción](media/service-embed-secure/secure-embed-report.png)

5. Cuando se usa la opción de iFrame, conviene modificar el código HTML proporcionado para especificar el alto y ancho deseado para su ajuste en la página web del portal.

    ![Establecimiento del alto y ancho](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-access-to-reports"></a>Conceder acceso a los informes

La opción Insertar no permite a los usuarios ver el informe automáticamente. Los permisos para ver el informe se establecen en el servicio Power BI.

Para proporcionar acceso al informe dentro del servicio Power BI, puede compartirlo con los usuarios que requieren acceso al informe insertado. Si usa un grupo de Office 365, puede mostrar los usuarios como miembros del área de trabajo de la aplicación en el servicio Power BI. Para obtener más información, vea [Administración de un área de trabajo de la aplicación](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licencias

Los usuarios que ven el informe insertado necesitan una licencia de Power BI Pro o el contenido debe estar en un área de trabajo que tenga una [capacidad de Power BI Premium (SKU EM o P).](service-admin-premium-purchase.md)

## <a name="customize-your-embed-experience-using-url-settings"></a>Personalización de la experiencia de inserción con la configuración de direcciones URL

La dirección URL de inserción admite varios valores de entrada que le ayudarán a personalizar su experiencia del usuario. Si utiliza el iFrame proporcionado, asegúrese de actualizar la dirección URL en la configuración de origen de iFrame.

| Propiedad  | Descripción  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Puede usar el parámetro de cadena de consulta **pageName** para establecer la página del informe que se abre. El valor de **pageName** corresponde al final de la dirección URL del informe al verlo en el servicio Power BI, tal y como se muestra a continuación. |  |  |  |
| Filtros de direcciones URL  | Puede usar [filtros de direcciones URL](service-url-filters.md) en la dirección URL de inserción que recibió de la interfaz de usuario de Power BI para filtrar el contenido de la inserción. De este modo, puede compilar integraciones de código reducido con una experiencia básica de HTML y JavaScript.  |  |  |  |

## <a name="set-which-page-opens-when-the-report-is-embedded"></a>Establecimiento de la página que se abre al insertar el informe

El valor especificado en la configuración de *pageName* corresponde al final de la dirección URL del informe al verlo en el servicio Power BI.

1. Abra el informe del servicio Power BI en el explorador web y copie la dirección URL de la barra de direcciones.

    ![Sección del informe](media/service-embed-secure/secure-embed-report-section.png)

2. Anexe el valor de *pageName* a la dirección URL.

    ![Anexión de pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrado del contenido de informes con filtros de direcciones URL

Con algunas características avanzadas, puede utilizar [filtros de direcciones URL](service-url-filters.md) para crear otras experiencias de uso del informe. Por ejemplo, la dirección URL siguiente filtra el informe para mostrar los datos del sector energético.

El uso de **pageName** con [filtros de direcciones URL](service-url-filters.md) puede ser eficaz. Puede crear experiencias con HTML y JavaScript básicos.

Por ejemplo, aquí mostramos cómo puede agregar un botón a una página HTML:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Cuando se presiona, el botón llama a una función para actualizar el iFrame con una dirección URL actualizada, que incluye el filtro para el sector energético.

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

* El usuario debe iniciar sesión para ver el informe cada vez que abra una nueva ventana del explorador.

* Algunos exploradores requieren que se actualice la página después de iniciar sesión, especialmente cuando se usan los modos InPrivate o Incognito.

* Para lograr una experiencia de inicio de sesión único, utilice la opción Insertar en SharePoint Online o cree una integración personalizada con el enfoque de [usuario propietario de datos](developer/embed-sample-for-your-organization.md). Obtenga más información sobre el [usuario propietario de datos](developer/embed-sample-for-your-organization.md).

* La funcionalidad de autenticación automática que se incluye con la opción **Insertar** no funciona con la API de JavaScript para Power BI. Con la API de JavaScript para Power BI, use el enfoque de [usuario propietario de datos](developer/embed-sample-for-your-organization.md) en la inserción. Obtenga más información sobre el [usuario propietario de datos](developer/embed-sample-for-your-organization.md).

## <a name="next-steps"></a>Pasos siguientes

* [Formas de compartir el trabajo](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtros de direcciones URL](service-url-filters.md)

* [Elemento web de informes de SharePoint Online](service-embed-report-spo.md)

* [Publicación en Web](service-publish-to-web.md)