---
title: Elementos visuales personalizados en Power BI
description: Visualizaciones personalizadas en Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 3fd2f3e47c9b6dd2144ed5a66d45e65a00c5b92e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051258"
---
# <a name="custom-visuals-in-power-bi"></a>Elementos visuales personalizados en Power BI

Al crear o editar un informe de Power BI, puede usar muchos tipos diferentes de objetos visuales. Aparecen los iconos para estos objetos visuales en el **visualizaciones** panel. Estos objetos visuales están empaquetados previamente al descargar [Power BI Desktop](https://powerbi.microsoft.com/desktop/) o abra el [servicio Power BI](https://app.powerbi.com).

![visualizaciones](media/power-bi-custom-visuals/power-bi-visualizations.png)

Sin embargo, no está limitado a este conjunto de objetos visuales. Si selecciona el botón de puntos suspensivos (...) en la parte inferior, otra fuente de objetos visuales de informes, se convierte en disponible -*objetos visuales personalizados*.

Los desarrolladores crear elementos visuales personalizados con el SDK de los objetos visuales personalizados. Estos objetos visuales permiten a los usuarios verán que sus datos de forma que mejor se adapte a su negocio. Los autores de informes, a continuación, pueden importar los archivos visuales personalizados en sus informes y utilizarlos como lo harían los demás objetos visuales de Power BI. Los objetos visuales personalizados son ciudadanos de primera clase en Power BI y se pueden filtrar, resaltado, editado, compartidos y así sucesivamente.

Los objetos visuales personalizados se implementan de tres maneras:

* Archivos de objetos visuales personalizados
* Objetos visuales de la organización
* Objetos visuales de Marketplace

## <a name="custom-visual-files"></a>Archivos de objetos visuales personalizados

Los objetos visuales personalizados son paquetes que contienen código para representar los datos que se reciben. Cualquier persona puede crear un objeto visual personalizado y empaquetarlo como un único `.pbiviz` archivo, que puede importarse en un informe de Power BI.

> [!WARNING]
> Un objeto visual personalizado podría contener código con riesgos de privacidad o seguridad. Asegúrese de que confía en el autor y el origen del objeto visual personalizado antes de importarla a un informe.

## <a name="organizational-visuals"></a>Objetos visuales de la organización

Administradores de Power BI aprobación e implementación los objetos visuales personalizados en su organización, lo que los autores de informes fácilmente pueden detectar, actualizar y usar. Los administradores pueden administrar fácilmente (por ejemplo, versión de actualización, habilitar o deshabilitar) estos objetos visuales.

 [Obtenga más información sobre objetos visuales de organización](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Objetos visuales de Marketplace

Miembros de la Comunidad y Microsoft han aportado sus objetos visuales personalizados para beneficio pública y los han publicado los [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) marketplace. Puede descargar estos objetos visuales de agregan a los informes de Power BI. Microsoft ha probado y aprobado estos objetos visuales personalizados para la funcionalidad y calidad.

¿Qué es [AppSource](developer/office-store.md)? Es el lugar donde puede encontrar las aplicaciones, complementos y extensiones para el software de Microsoft. [AppSource](https://appsource.microsoft.com/) conecta millones de usuarios de productos como Office 365, Azure, Dynamics 365, Cortana y Power BI, con soluciones que les ayudan a realizar el trabajo más eficazmente, insightfully y atractiva que antes.

### <a name="certified-visuals"></a>Objetos visuales certificados

Los objetos visuales son objetos visuales de marketplace que han superado las pruebas de calidad rigurosa adicionales y se admiten en escenarios adicionales, como certificados por Power BI [suscripciones de correo electrónico](https://docs.microsoft.com/power-bi/service-report-subscribe), y [exportar a PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
Para ver la lista de objetos visuales personalizados certificados o para enviar su propia lista, consulte [Certified custom visuals](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified) (Objetos visuales personalizados certificados).

¿Es un desarrollador web interesado en crear sus propias visualizaciones y agregarlas a AppSource? Consulte [desarrollar un objeto visual personalizado de Power BI](developer/custom-visual-develop-tutorial.md) y aprenda cómo [publicar objetos visuales personalizados en AppSource](https://docs.microsoft.com/power-bi/developer/office-store).

### <a name="import-a-custom-visual-from-a-file"></a>Importar un objeto visual personalizado de un archivo

1. Seleccione el botón de puntos suspensivos en la parte inferior de la **visualizaciones** panel.

    ![visualizaciones2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. En la lista desplegable, seleccione **Importar desde archivo**.

    ![importar desde archivo](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. En el menú Abrir archivo, seleccione el `.pbiviz` archivo que desea importar y, a continuación, seleccione **abierto**. Icono del objeto visual personalizado se agrega a la parte inferior de la **visualizaciones** panel y ahora está disponible para su uso en el informe.

    ![cv importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importación de objetos visuales de la organización

1. Seleccione el botón de puntos suspensivos en la parte inferior de la **visualizaciones** panel.

    ![organización visual 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. En el menú desplegable, seleccione **Importar de Marketplace**.

    ![organización visual 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Seleccione **MI ORGANIZACIÓN** en el menú de la pestaña superior.

    ![organización visual 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Desplácese por la lista hasta que encuentre el objeto visual que desea importar.

    ![organización visual 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Seleccione **agregar** para importar el objeto visual personalizado. El icono se agrega a la parte inferior de la **visualizaciones** panel y ahora está disponible para su uso en el informe.

    ![organización visual 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Descargar o importar objetos visuales personalizados desde Microsoft AppSource

Tiene dos opciones para descargar e importar objetos visuales personalizados: desde dentro de Power BI y de la [sitio Web de AppSource](https://appsource.microsoft.com/).

### <a name="import-custom-visuals-from-within-power-bi"></a>Importar objetos visuales personalizados desde Power BI

1. Seleccione el botón de puntos suspensivos en la parte inferior de la **visualizaciones** panel.

    ![visualizaciones 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. En el menú desplegable, seleccione **Importar de Marketplace**.

    ![organización visual 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Desplácese por la lista hasta que encuentre el objeto visual que desea importar.

    ![importar objeto visual](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Para obtener más información sobre uno de los objetos visuales, resáltelo y selecciónelo.

    ![Seleccionar](media/power-bi-custom-visuals/power-bi-select.png)

5. En dicha página puede ver capturas de pantalla, vídeos, descripción detallada, etc.

    ![Sinóptico](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Desplácese hacia abajo para ver las opiniones.

    ![Opiniones](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Seleccione **agregar** para importar el objeto visual personalizado. El icono se agrega a la parte inferior de la **visualizaciones** panel y ahora está disponible para su uso en el informe.

    ![objeto visual importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Descargar e importar objetos visuales personalizados desde Microsoft AppSource

1. Vaya a [Microsoft AppSource](https://appsource.microsoft.com) y seleccione la pestaña **Aplicaciones**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Vaya a la [página de resultados de aplicaciones](https://appsource.microsoft.com/marketplace/apps), donde puede ver las aplicaciones principales de cada categoría, entre ellas *Power BI apps* (Aplicaciones de Power BI). Estamos buscando objetos visuales personalizados, así que vamos a seleccionar **objetos visuales de Power BI** en la lista de navegación izquierdo para limitar los resultados.

    ![Objetos visuales de AppSource](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. AppSource muestra un icono para cada objeto visual personalizado.  Cada icono tiene una instantánea visual personalizada con una breve descripción y un vínculo de descarga. Para ver información más detallada, seleccione el icono.

    ![Objeto visual Select personalizado](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. En dicha página puede ver capturas de pantalla, vídeos, descripción detallada, etc. Seleccione **obtenerla ahora** para descargar el objeto visual personalizado y, a continuación, acepte los términos de uso.

    ![Obtener AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Seleccione el vínculo para descargar el objeto visual personalizado.

    ![Descargar](media/power-bi-custom-visuals/powerbi-custom-download.png)

    La página de descarga también incluye instrucciones sobre cómo importar el objeto visual personalizado en Power BI Desktop y el servicio Power BI.

    También puede descargar un informe de ejemplo que incluye el objeto visual personalizado y muestra sus funcionalidades.

    ![Probar muestra](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Guardar el `.pbiviz` de archivo y, a continuación, abra Power BI.

7. Importar el `.pbiviz` archivo en el informe. (consulte la sección [Importar un objeto visual personalizado de un archivo](#import-a-custom-visual-from-a-file) anterior).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* Un objeto visual personalizado se agrega a un informe específico cuando se importa. Si desea usar el objeto visual en otro informe, debe importarlo también en dicho informe. Cuando se guarda un informe con un objeto visual personalizado mediante la opción **Guardar como** , se guarda una copia del objeto visual personalizado con el nuevo informe.

* Si no ve una **visualizaciones** panel, lo que significa que no tiene informes permisos de edición.  Solo se pueden agregar objetos visuales personalizados a los informes que puede editar, no a los informes que se han compartido con usted.

## <a name="troubleshoot"></a>Solucionar problemas

Para solucionar problemas, consulte [solución de problemas de los objetos visuales personalizados de Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES

Para obtener más información y respuestas a las preguntas, visite las [preguntas más frecuentes sobre objetos visuales personalizados de Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

## <a name="next-steps"></a>Pasos siguientes

* [Visualizaciones en informes de Power BI](visuals/power-bi-report-visualizations.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/).
