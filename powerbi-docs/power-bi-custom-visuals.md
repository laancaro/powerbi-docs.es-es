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
ms.openlocfilehash: 23436fb8e21e1be3a863986a773d7d969da65122
ms.sourcegitcommit: 24781cdab5fbe43fc14248db636169cc54ef6721
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66498036"
---
# <a name="custom-visuals-in-power-bi"></a>Elementos visuales personalizados en Power BI

Al crear o editar un informe de Power BI, puede usar muchos tipos diferentes de objetos visuales. Los iconos para estos objetos visuales aparecen en el panel **Visualizaciones**. Al descargar [Power BI Desktop](https://powerbi.microsoft.com/desktop/) o abrir el [servicio Power BI](https://app.powerbi.com), estos objetos visuales están previamente empaquetados.

![visualizaciones](media/power-bi-custom-visuals/power-bi-visualizations.png)

Pero no está limitado a este conjunto de objetos visuales. Si selecciona el botón de puntos suspensivos (...) de la parte inferior, aparece otra fuente de objetos visuales de informes: los *objetos visuales personalizados*.

Los desarrolladores crean objetos visuales personalizados con el SDK de objetos visuales personalizados. Estos objetos visuales permiten a los usuarios empresariales ver sus datos de una forma que se adapta mejor a su negocio. Los creadores de informes pueden así importar los archivos de objetos visuales personalizados en sus informes y usarlos como harían con cualquier otro objeto visual de Power BI. A los objetos visuales personalizados se les concede la máxima prioridad en Power BI y se pueden filtrar, resaltar, editar, compartir, etc.

Los objetos visuales personalizados se implementan de tres maneras:

* Archivos de objetos visuales personalizados
* Objetos visuales de la organización
* Objetos visuales de Marketplace

## <a name="custom-visual-files"></a>Archivos de objetos visuales personalizados

Los objetos visuales personalizados son paquetes que contienen código para representar los datos que se les proporcionan. Cualquiera puede crear un objeto visual personalizado y empaquetarlo como un archivo `.pbiviz` único, que después se puede importar en un informe de Power BI.

> [!WARNING]
> Un objeto visual personalizado podría contener código que presente riesgos para la seguridad o la privacidad. Asegúrese de que confía en el autor y el origen del objeto visual personalizado antes de importarlo al informe.

## <a name="organizational-visuals"></a>Objetos visuales de la organización

Los administradores de Power BI aprueban e implementan los objetos visuales personalizados en su organización, que los autores de informes pueden detectar, actualizar y usar con facilidad. Los administradores pueden administrar fácilmente (por ejemplo, actualizar la versión, habilitar o deshabilitar) estos objetos visuales.

 [Más información sobre objetos visuales de la organización](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Objetos visuales de Marketplace

Los miembros de la comunidad y Microsoft han aportado sus objetos visuales personalizados para el beneficio del público y los han publicado en el Marketplace de [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Puede descargar estos objetos visuales y agregarlos a los informes de Power BI. Microsoft ha probado y aprobado la funcionalidad y calidad de todos estos objetos visuales personalizados.

¿Qué es [AppSource](developer/office-store.md)? Es el lugar donde puede encontrar aplicaciones, complementos y extensiones para el software de Microsoft. AppSource conecta millones de usuarios de productos como Office 365, Azure, Dynamics 365, Cortana y Power BI con soluciones que les ayudan a realizar su trabajo de forma más eficaz, minuciosa y atractiva que antes.

### <a name="certified-visuals"></a>Objetos visuales certificados

Los objetos visuales certificados por Power BI son objetos visuales de Marketplace que han superado rigurosas pruebas de calidad adicionales y se admiten en escenarios adicionales, como [suscripciones de correo electrónico](service-report-subscribe.md) y [exportación a PowerPoint](service-publish-to-powerpoint.md).
Para ver la lista de objetos visuales personalizados certificados o para enviar su propia lista, consulte [Certified custom visuals](power-bi-custom-visuals-certified.md) (Objetos visuales personalizados certificados).

¿Es un desarrollador web interesado en crear sus propias visualizaciones y agregarlas a AppSource? Vea [Desarrollo de objetos visuales personalizados de Power BI](developer/custom-visual-develop-tutorial.md) y vea cómo [publicar objetos visuales personalizados en AppSource](developer/office-store.md).

### <a name="import-a-custom-visual-from-a-file"></a>Importar un objeto visual personalizado de un archivo

1. Seleccione los puntos suspensivos en la parte inferior del panel **Visualizaciones**.

    ![visualizaciones2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. En la lista desplegable, seleccione **Importar desde archivo**.

    ![importar desde archivo](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. En el menú **Abrir** archivo, seleccione el archivo `.pbiviz` que quiere importar y luego **Abrir**. El icono del objeto visual personalizado se agrega a la parte inferior del panel **Visualizaciones** y ya se puede usar en el informe.

    ![cv importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importación de objetos visuales de la organización

1. Seleccione los puntos suspensivos en la parte inferior del panel **Visualizaciones**.

    ![organización visual 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. En el menú desplegable, seleccione **Importar de Marketplace**.

    ![organización visual 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Seleccione **MI ORGANIZACIÓN** en el menú de la pestaña superior.

    ![organización visual 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Desplácese por la lista hasta que encuentre el objeto visual que desea importar.

    ![organización visual 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Seleccione **Agregar** para importar el objeto visual personalizado. Su icono se agrega a la parte inferior del panel **Visualizaciones** y ya se puede usar en el informe.

    ![organización visual 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Descargar o importar objetos visuales personalizados desde Microsoft AppSource

Tiene dos opciones para descargar e importar objetos visuales personalizados; desde Power BI y desde el [sitio web de AppSource](https://appsource.microsoft.com/).

### <a name="import-custom-visuals-from-within-power-bi"></a>Importar objetos visuales personalizados desde Power BI

1. Seleccione los puntos suspensivos en la parte inferior del panel **Visualizaciones**.

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

7. Seleccione **Agregar** para importar el objeto visual personalizado. Su icono se agrega a la parte inferior del panel **Visualizaciones** y ya se puede usar en el informe.

    ![objeto visual importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Descargar e importar objetos visuales personalizados desde Microsoft AppSource

1. Vaya a [Microsoft AppSource](https://appsource.microsoft.com) y seleccione la pestaña **Aplicaciones**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Vaya a la [página de resultados de aplicaciones](https://appsource.microsoft.com/marketplace/apps), donde puede ver las aplicaciones principales de cada categoría, entre ellas *Power BI apps* (Aplicaciones de Power BI). Para buscar objetos visuales personalizados se selecciona **Power BI visuals** (Objetos visuales de Power BI) en la lista de navegación de la izquierda para restringir los resultados.

    ![Objetos visuales de AppSource](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. AppSource muestra un icono para cada objeto visual personalizado.  Cada icono tiene una instantánea del objeto visual personalizado con una descripción breve y un vínculo de descarga. Para ver información más detallada, seleccione el icono.

    ![Objeto visual Select personalizado](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. En dicha página puede ver capturas de pantalla, vídeos, descripción detallada, etc. Seleccione **Obtener ahora** para descargar el objeto visual personalizado y después acepte los Términos de uso.

    ![Obtener AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Seleccione el vínculo para descargar el objeto visual personalizado.

    ![Descargar](media/power-bi-custom-visuals/powerbi-custom-download.png)

    En la página de descarga también se incluyen instrucciones para importar el objeto visual personalizado en Power BI Desktop y el servicio Power BI.

    También puede descargar un informe de ejemplo que incluye el objeto visual personalizado y muestra sus funcionalidades.

    ![Probar muestra](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Guarde el archivo `.pbiviz` y luego abra Power BI.

7. Importe el archivo `.pbiviz` en el informe. (consulte la sección [Importar un objeto visual personalizado de un archivo](#import-a-custom-visual-from-a-file) anterior).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* Un objeto visual personalizado se agrega a un informe específico cuando se importa. Si desea usar el objeto visual en otro informe, debe importarlo también en dicho informe. Cuando se guarda un informe con un objeto visual personalizado mediante la opción **Guardar como** , se guarda una copia del objeto visual personalizado con el nuevo informe.

* Si no ve un panel **Visualizaciones**, significa que no tiene permisos de edición de informe.  Solo se pueden agregar objetos visuales personalizados a los informes que puede editar, no a los informes que solo se han compartido con usted.

## <a name="troubleshoot"></a>Solucionar problemas

Para solucionar problemas, vea [Solución de problemas de los objetos visuales personalizados de Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES

Para obtener más información y respuestas a las preguntas, visite las [preguntas más frecuentes sobre objetos visuales personalizados de Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

## <a name="next-steps"></a>Pasos siguientes

* [Visualizaciones en informes de Power BI](visuals/power-bi-report-visualizations.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/).
