---
title: Publicar en la web de Power BI
description: Con la característica Publicar en la web de Power BI, puede insertar fácilmente visualizaciones de Power BI interactivas en línea, como en publicaciones de blog y sitios web, a través de mensajes de correo electrónico o redes sociales, en cualquier dispositivo.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051579"
---
# <a name="publish-to-web-from-power-bi"></a>Publicar en la web de Power BI

Con Power BI **publicar en web** opción, puede insertar fácilmente visualizaciones de Power BI interactivas en línea, como en publicaciones de blog, sitios Web, a través de mensajes de correo electrónico o redes sociales, desde cualquier dispositivo. También puede editar, actualizar o dejar de compartir fácilmente los objetos visuales publicados.

> [!WARNING]
> Cuando usas **publicar en web**, cualquier persona en Internet puede ver el informe publicado o el objeto visual. Esto no requiere autenticación e incluye la visualización de datos de nivel de detalle los informes agregados. Antes de publicar un informe, asegúrese de que pasa nada para que pueda compartir los datos y visualizaciones públicamente. No publique información confidencial o de propiedad. En caso de duda, compruebe las directivas de la organización antes de publicarlo.

>[!Note]
>Para insertar el contenido de forma segura en un sitio web o portal interno, utilice las opciones [Insertar](service-embed-secure.md) o [Insertar en SharePoint Online](service-embed-report-spo.md). Esto garantiza que se aplican todos los permisos y la seguridad de los datos cuando los usuarios ven sus datos internos.

## <a name="how-to-use-publish-to-web"></a>Cómo usar la característica Publicar en Web

**Publicar en web** está disponible para los informes en las áreas de trabajo personales o de grupo se puede editar.  No está disponible para los informes compartidos con usted, o que depender de seguridad de nivel de fila para proteger los datos. Consulte la [ **limitaciones** ](#limitations) sección para obtener una lista completa de los casos donde **publicar en web** no se admite. Revise el **advertencia** anteriormente en este artículo antes de usar **publicar en web**.

La siguiente *vídeo de corta duración* muestra cómo funciona esta característica. A continuación, pruébelo usted mismo en los pasos siguientes.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

Los pasos siguientes describen cómo usar la característica **Publicar en Web**.

1. Abra un informe en el área de trabajo que puede editar y seleccione **archivo > Publicar en web**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Revise el cuadro de diálogo de contenido y seleccione **crear código para insertar**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Revise la advertencia, como se muestra aquí y confirme que los datos son pueden insertar en un sitio Web público. Si es así, seleccione **publicar**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. Aparece un cuadro de diálogo con un vínculo. Puede enviar este vínculo en un correo electrónico, insertarlo en el código como un iFrame o péguelo directamente en una página web o blog.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Si ha creado previamente un código para insertar un informe y seleccionar **publicar en web**, no verá los cuadros de diálogo en los pasos 2 a 4. En su lugar, el **incrustar código** aparece el cuadro de diálogo:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Solo se puede crear un código para insertar por informe.


## <a name="tips-and-tricks-for-view-modes"></a>Sugerencias y trucos para los modos de vista

Al insertar contenido dentro de una entrada de blog, normalmente debe ajustarse a un tamaño de pantalla específico.  Puede ajustar el alto y el ancho de la etiqueta de iFrame según sea necesario. Sin embargo, deberá asegurarse de que el informe quepa dentro del área determinada del iFrame, por lo que también deberá establecer un modo de vista adecuado al editar el informe.

En la tabla siguiente se proporcionan instrucciones sobre el modo de vista y cómo va a aparecer al insertarse.

| Modo de vista | Aspecto que tiene al insertarse |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Ajustar a la página** respetará el ancho y alto de página del informe. Si establece su página en proporciones "Dinámicas" como 16:9 o 4:3 su contenido se escalará para ajustarse al iFrame. Cuando se insertan en un iFrame, opción **ajustar a la página** puede dar lugar a **formato letterbox**, donde un fondo gris se muestra en las áreas de iFrame después del contenido como escala para ajustarse al iFrame. Para minimizar formato letterbox, establezca el alto y el ancho del iFrame adecuadamente. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Tamaño real** garantiza que el informe conserve su tamaño tal como está establecido en la página de informe. Esto puede dar lugar a que las barras de desplazamiento aparezcan en el iFrame. Establece el alto del iFrame y ancho para evitar las barras de desplazamiento. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Ajustar al ancho** garantiza que el contenido se ajuste dentro del área horizontal del iFrame. Todavía se muestra un borde, pero el contenido se escala para usar todo el espacio horizontal disponible. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Sugerencias y trucos para el ancho y alto de iFrame

Un **publicar en web** incrustar código es similar al siguiente:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Puede editar el ancho y alto manualmente para asegurarse de que es precisamente cómo desea que se ajuste en la página donde se está insertando.

Para lograr un ajuste más perfecto, puede intentar agregar 56 píxeles a la altura de iFrame para acomodar el tamaño actual de la barra inferior. Si la página de informes usa el tamaño dinámico, la siguiente tabla proporciona algunos tamaños que puede usar para obtener un ajuste sin formato letterbox.

| Proporción | Tamaño | Dimensiones (ancho x alto) |
| --- | --- | --- |
| 16:9 |Pequeño |640 x 416 px |
| 16:9 |Medio |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Pequeño |640 x 536 px |
| 4:3 |Medio |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="manage-embed-codes"></a>Administrar códigos para insertar

Una vez que cree un **publicar en web** código para insertar, puede administrar sus códigos desde el **configuración** menú de Power BI. Administrar códigos para insertar incluye la capacidad para quitar el objeto visual de destino o el informe para un código (inutilizable el código para insertar), u obtener el código para insertar.

1. Para administrar sus códigos para insertar de **Publicar en Web** , abra el engranaje de **Configuración** y seleccione **Administrar códigos para insertar**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Aparecen los códigos para insertar.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Puede recuperar o eliminar un código para insertar. Si lo elimina, deshabilita todos los vínculos a ese informe u objeto visual.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Si selecciona **eliminar**, se le pide confirmación.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Actualizaciones de informes y datos

Después de crear su **publicar en web** código para insertar y recurso compartido, el informe se actualiza con los cambios que realice y el vínculo código para insertar se activa inmediatamente y cualquier persona que abra el vínculo puede verlo. Sin embargo, después de la acción inicial, las actualizaciones de los informes u objetos visuales pueden tardar aproximadamente una hora antes de convertirse en visible para los usuarios. Si necesita que las actualizaciones estén disponibles inmediatamente, puede eliminar el código para insertar y crear uno nuevo. Para obtener más información, consulte el [ **cómo funciona** ](#howitworks) sección más adelante en este artículo. 

## <a name="data-refresh"></a>Actualización de datos

Las actualizaciones de datos se reflejan automáticamente en el informe u objeto visual insertado. Los datos actualizados pueden tardar aproximadamente una hora en ser visibles desde los códigos para insertar. Para deshabilitar la actualización automática, puede seleccionar **no se actualizan** según la programación del conjunto de datos utiliza el informe.  

## <a name="custom-visuals"></a>Objetos visuales personalizados

Los objetos visuales personalizados se admiten en **Publicar en Web**. Cuando usas **publicar en web**, los usuarios con los que comparta el objeto visual publicado no es necesario habilitar objetos visuales personalizados ver el informe.

## <a name="limitations"></a>Limitaciones

**Publicar en web** es compatible con la mayoría de los datos de orígenes y los informes en el servicio Power BI, sin embargo, las siguientes son **no actualmente admite ni está disponible** con **publicar en web** :

- Informes que usan la seguridad de nivel de fila.
- Informes que usan cualquier origen de datos de conexión dinámica, incluido Analysis Services Tabular hospedado en local, Analysis Service Multidimensional y Azure Analysis Services.
- Informes compartidos con usted directamente o a través de un paquete de contenido organizativo.
- Informes en un grupo en el que no es miembro de edición.
- Los objetos visuales "R" no se admiten actualmente en **publicar en web** informes.
- Exportar datos desde los objetos visuales en un informe, que se ha publicado en la web.
- ArcGIS Maps for Power BI elementos visuales.
- Informes que contienen medidas DAX de nivel de informe.
- Modelos de consulta de datos de inicio de sesión único.
- [Proteger información confidencial o propia](#publish-to-web-from-power-bi).
- La funcionalidad de autenticación automática que se incluye con la opción **Insertar** no funciona con la API de JavaScript para Power BI. Con la API de JavaScript para Power BI, use el enfoque de [usuario propietario de datos](developer/embed-sample-for-your-organization.md) en la inserción. Obtenga más información sobre el [usuario propietario de datos](developer/embed-sample-for-your-organization.md).

## <a name="tenant-setting"></a>Configuración de inquilinos

Los administradores de Power BI pueden habilitar o deshabilitar la **publicar en web** característica. También puede restringir el acceso a grupos específicos, lo que pueden afectar a su capacidad para crear un código para insertar.

|Destacado |Habilitada para toda la organización |Deshabilitada para toda la organización |Grupos de seguridad específicos   |
|---------|---------|---------|---------|
|**Publicar en web** en la sección del informe **archivo** menú|Habilitada para todos|No visible para todos|Solo visible para usuarios o grupos autorizados.|
|**Administrar códigos para insertar** en **Configuración**|Habilitada para todos|Habilitada para todos|Habilitado para todos.<br><br>Opción * **Eliminar** solo para usuarios o grupos autorizados.<br>* **Obtener código** habilitada para todos.|
|**Códigos de inserción** en el portal de administración|El estado será uno de los siguientes:<br>* Activo<br>* No admitido<br>* Bloqueado|El estado mostrará **Deshabilitado**|El estado será uno de los siguientes:<br>* Activo<br>* No admitido<br>* Bloqueado<br><br>Si el usuario no está autorizado en función de la configuración del inquilino, el estado mostrará **Infracción**.|
|Informes publicados existentes|Todos habilitados|Todos deshabilitados|Los informes continúan generándose para todos.|

## <a name="understanding-the-embed-code-status-column"></a>Descripción de la columna de estado de código para insertar

El **administrar códigos para insertar** página incluye una columna de estado. Códigos para insertar de forma predeterminada, están **Active**, pero también podría ser uno de los Estados que se enumeran a continuación.

| Estado | Descripción |
| --- | --- |
| **Activo** |El informe está disponible para que los usuarios de Internet lo vean e interactúen con él. |
| **Bloqueado** |El contenido del informe infringe el [del servicio de Power BI términos](https://powerbi.microsoft.com/terms-of-service). Microsoft lo bloqueó. Si cree que el contenido se ha bloqueado por error, póngase en contacto con soporte técnico. |
| **No admitido** |El conjunto de datos del informe usa la seguridad de nivel de fila u otra configuración no admitida. Consulte la [ **limitaciones** ](#limitations) sección para obtener una lista completa. |
| **Infracción** |El código para insertar está fuera de la directiva de inquilino definida. Esto suele ocurrir cuando se creó un código para insertar y, a continuación, el **publicar en web** se cambió la configuración de inquilino para excluir el usuario al que pertenece el código para insertar. Si se deshabilita la configuración del inquilino o el usuario ya no se permite crear códigos para insertar, mostrar códigos para insertar existentes un **infracción** estado. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Cómo informar de un problema con el contenido de Publicar en Web

Para informar de un problema relacionado con **publicar en web** contenido insertado en un sitio Web o blog, use el **marca** icono en la barra inferior, como se muestra en la siguiente imagen. Se le pedirá que envíe un correo electrónico a Microsoft que explica su preocupación. Microsoft evaluará el contenido basándose en las condiciones del servicio Power BI y tomar las medidas adecuadas.

Para notificar un problema, seleccione el **marca** icono en la parte inferior de la **publicar en web** ve de informes.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licencias y precios

Debe ser usuario de Microsoft Power BI para poder usar la características **Publicar en Web**. Los visores del informe no es necesario que los usuarios de Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Cómo funciona (detalles técnicos)

Cuando se crea un código para insertar mediante **publicar en web**, el informe se hace visible a los usuarios de Internet. Está disponible públicamente, por lo que puede esperar a que los lectores compartan fácilmente el informe a través de medios sociales en el futuro. Cuando los usuarios ven el informe, ya sea con la dirección URL pública directa o insertado en una página web o un blog, Power BI almacena en caché la definición de informe y los resultados de las consultas necesarias para ver el informe. Esto garantiza que miles de usuarios simultáneos pueden ver el informe sin afectar al rendimiento.

La memoria caché es de larga duración, por lo que si se actualiza la definición de informe (por ejemplo, si cambia el modo de vista) o actualización los datos del informe, puede tardar aproximadamente una hora antes de que los cambios se reflejan en la versión del informe que permite ver los usuarios. Por lo tanto, se recomienda organizar el trabajo con antelación y crear el código para insertar de **Publicar en Web** solo cuando esté satisfecho con la configuración.

## <a name="next-steps"></a>Pasos siguientes

- [Elemento web de informes de SharePoint Online](service-embed-report-spo.md) 

- [Inserción de informes en un sitio web o portal seguro](service-embed-secure.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
