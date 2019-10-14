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
ms.openlocfilehash: 9824b3340da694c00784f34b0c6245cafbf69383
ms.sourcegitcommit: d02de4ca33d865aee3e3e764b98f221950cb0a10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2019
ms.locfileid: "72239923"
---
# <a name="publish-to-web-from-power-bi"></a>Publicar en la web de Power BI

Con la opción **Publicar en la web** de Power BI, puede insertar fácilmente visualizaciones de Power BI interactivas en línea, como en entradas de blog y sitios web, a través de correos o redes sociales, desde cualquier dispositivo. También puede editar, actualizar o dejar de compartir fácilmente los objetos visuales publicados.

> [!WARNING]
> Al usar la característica **Publicar en la web**, cualquier usuario podrá ver en Internet el informe o el objeto visual que publique. Esto no requiere autenticación e incluye la visualización de los datos de nivel de detalle que agregan los informes. Antes de publicar un informe, asegúrese de que está de acuerdo en compartir los datos y visualizaciones públicamente. No publique información confidencial o de propiedad. En caso de duda, compruebe las directivas de la organización antes de publicarlo.

>[!Note]
>Para insertar el contenido de forma segura en un sitio web o portal interno, utilice las opciones [Insertar](service-embed-secure.md) o [Insertar en SharePoint Online](service-embed-report-spo.md). Esto garantiza que se aplican todos los permisos y la seguridad de los datos cuando los usuarios ven sus datos internos.

## <a name="how-to-use-publish-to-web"></a>Cómo usar la característica Publicar en Web

**Publicar en la web** está disponible en informes que se pueden editar en áreas de trabajo personales o de grupo.  No está disponible para los informes que se comparten con usted o que dependen de la seguridad de nivel de fila para proteger los datos. Consulte la sección [**Limitaciones**](#limitations) más adelante para obtener una lista completa de los casos en los que no se admite **Publicar en la web**. Revise la **Advertencia** mencionada anteriormente en este artículo antes de usar la característica **Publicar en la web**.

El siguiente vídeo corto muestra cómo funciona esta característica. Luego, pruébelo usted mismo en los pasos siguientes.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

Los pasos siguientes describen cómo usar la característica **Publicar en Web**.

1. Abra un informe en el área de trabajo que puede editar y seleccione **Archivo > Publicar en la web**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Revise el contenido del cuadro de diálogo y seleccione **Crear código para insertar**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Revise la advertencia, tal como se muestra aquí, y confirme que los datos se pueden insertar en un sitio web público. Si es así, seleccione **Publicar**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. Aparece un cuadro de diálogo con un vínculo. Se puede enviar este vínculo en un correo, insertarlo en el código como un iFrame o pegarlo directamente en una página web o blog.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Si se ha creado previamente un código para insertar para un informe y se ha seleccionado **Publicar en la web**, no verá los cuadros de diálogo en los pasos 2 a 4. En su lugar, el cuadro de diálogo **Código para insertar** se muestra como sigue:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Solo se puede crear un código para insertar por informe.


## <a name="tips-and-tricks-for-view-modes"></a>Trucos y sugerencias para modos de vista

Al insertar contenido en una entrada de blog, normalmente debe ajustarlo en un tamaño de pantalla concreto.  Se puede ajustar el alto y el ancho de la etiqueta de iFrame según sea necesario. Sin embargo, deberá asegurarse de que el informe se ajusta en el área determinada del iFrame, por lo que también deberá establecer un Modo de vista adecuado al editar el informe.

En la tabla siguiente se proporcionan instrucciones sobre el modo de vista y cómo va a aparecer al insertarse.

| Modo de vista | Aspecto que tiene al insertarse |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Ajustar a la página** respeta el alto y ancho de la página del informe. Si se establece la página en proporciones *dinámicas*, como 16:9 o 4:3, el contenido se escalará para ajustarse en el iFrame. Cuando se inserta en un iFrame, el uso de **Ajustar a la página** puede dar como resultado un *formato de pantalla ancha*, en el que se muestra un fondo gris en las áreas del iFrame después de que el contenido se escale para ajustarlo en dicho iFrame. Para minimizar el formato de pantalla ancha, establezca el alto y ancho del iFrame adecuadamente. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Tamaño real** garantiza que el informe conserve su tamaño tal como está establecido en la página del informe. Esto puede causar que se muestren barras de desplazamiento en el iFrame. Establezca el alto y ancho de iFrame para evitar las barras de desplazamiento. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Ajustar al ancho** garantiza que el contenido se ajuste dentro del área horizontal del iFrame. Se sigue mostrando un borde, pero el contenido se escala para usar todo el espacio horizontal disponible. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Sugerencias y trucos para el ancho y alto de iFrame

Un código para insertar de **Publicar en la web** se parece a lo siguiente:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Puede editar el ancho y alto manualmente para asegurarse de que es precisamente como quiere que se ajuste a la página en la que lo está insertando.

Para lograr un ajuste más exacto, se puede intentar la adición de 56 píxeles al alto del iFrame para acomodar el tamaño actual de la barra inferior. Si la página del informe usa el tamaño dinámico, la siguiente tabla proporciona algunos tamaños que se pueden usar para obtener un ajuste sin formato de pantalla ancha.

| Proporción | Tamaño | Dimensiones (ancho x alto) |
| --- | --- | --- |
| 16:9 |Pequeño |640 x 416 px |
| 16:9 |Medio |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Pequeño |640 x 536 px |
| 4:3 |Medio |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="manage-embed-codes"></a>Administrar códigos para insertar

Después de crear un código para insertar de **Publicar en la web**, se pueden administrar los códigos desde el menú **Configuración** en Power BI. La administración de códigos para insertar incluye la capacidad de quitar el objeto visual o informe de destino de un código (lo que deja inutilizable el código para insertar), o la obtención del código para insertar.

1. Para administrar sus códigos para insertar de **Publicar en Web** , abra el engranaje de **Configuración** y seleccione **Administrar códigos para insertar**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Aparecen los códigos para insertar.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Se puede recuperar o eliminar un código para insertar. Si se elimina, se deshabilitan todos los vínculos a ese informe u objeto visual.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Si se selecciona **Eliminar**, se le solicita una confirmación.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Actualizaciones de informes y datos

Después de crear y compartir el código para insertar de **Publicar en la web**, el informe se actualiza con los cambios que realice y el vínculo del código para insertar se activa de forma inmediata. Cualquiera que abra el vínculo puede verlo. Sin embargo, después de esta acción inicial, las actualizaciones de los informes u objetos visuales pueden tardar aproximadamente una hora antes de convertirse en visibles para los usuarios. Para obtener más información, consulte la sección [**Cómo funciona**](#howitworks) más adelante en este artículo. 

## <a name="data-refresh"></a>Actualización de datos

Las actualizaciones de datos se reflejan automáticamente en el informe u objeto visual insertado. Los datos actualizados pueden tardar aproximadamente una hora en ser visibles desde los códigos para insertar. Para desactivar la actualización automática, seleccione **no actualizar** en la programación del conjunto de datos que usa el informe.  

## <a name="custom-visuals"></a>Objetos visuales personalizados

Los objetos visuales personalizados se admiten en **Publicar en Web**. Si usa **Publicar en la web**, los usuarios con los que comparta el objeto visual publicado no tendrán que habilitar los objetos visuales personalizados para ver el informe.

## <a name="limitations"></a>Limitaciones

La característica **Publicar en la web** se admite para la gran mayoría de los orígenes de datos e informes del servicio Power BI, aunque los siguientes no se admiten o no están disponibles actualmente con esta característica:

- Informes que usan la seguridad de nivel de fila.
- Informes que usan cualquier origen de datos de conexión dinámica, incluido Analysis Services Tabular hospedado en local, Analysis Service Multidimensional y Azure Analysis Services.
- Informes compartidos con usted directamente o a través de un paquete de contenido organizativo.
- Informes en un grupo en el que no es miembro de edición.
- Los objetos visuales "R" no se admiten actualmente en informes de **Publicar en la web**.
- Exportación de datos desde los objetos visuales de un informe que se ha publicado en la web.
- Objetos visuales de ArcGIS Maps for Power BI.
- Informes que contienen medidas DAX de nivel de informe.
- Modelos de consulta de datos de inicio de sesión único.
- [Información confidencial o de propiedad](#publish-to-web-from-power-bi).
- La funcionalidad de autenticación automática que se incluye con la opción **Insertar** no funciona con la API de JavaScript para Power BI. Con la API de JavaScript para Power BI, use el enfoque de [usuario propietario de datos](developer/embed-sample-for-your-organization.md) en la inserción.

## <a name="tenant-setting"></a>Configuración de inquilinos

Los administradores de Power BI pueden habilitar o deshabilitar la característica **Publicar en la web**. También pueden restringir el acceso a grupos específicos, lo que puede afectar a su capacidad para crear un código para insertar.

|Destacado |Habilitada para toda la organización |Deshabilitada para toda la organización |Grupos de seguridad específicos   |
|---------|---------|---------|---------|
|**Publicar en la web** en el menú **Archivo** del informe|Habilitada para todos|No visible para todos|Solo visible para usuarios o grupos autorizados.|
|**Administrar códigos para insertar** en **Configuración**|Habilitada para todos|Habilitada para todos|Habilitada para todos<br><br>Opción * **Eliminar** solo para usuarios o grupos autorizados.<br>* **Obtener código** habilitada para todos.|
|**Códigos de inserción** en el portal de administración|El estado será uno de los siguientes:<br>* Activo<br>* No admitido<br>* Bloqueado|El estado mostrará **Deshabilitado**|El estado será uno de los siguientes:<br>* Activo<br>* No admitido<br>* Bloqueado<br><br>Si el usuario no está autorizado en función de la configuración del inquilino, el estado mostrará **Infracción**.|
|Informes publicados existentes|Todos habilitados|Todos deshabilitados|Los informes continúan generándose para todos.|

## <a name="understanding-the-embed-code-status-column"></a>Descripción de la columna de estado de código para insertar

La página **Administrar códigos para insertar** incluye una columna de estado. De forma predeterminada, el estado de los códigos para insertar es **Activo**, pero también podría ser uno de los que se enumeran debajo.

| Estado | Descripción |
| --- | --- |
| **Activo** |El informe está disponible para que los usuarios de Internet lo vean e interactúen con él. |
| **Bloqueado** |El contenido del informe infringe las [Condiciones del servicio de Power BI](https://powerbi.microsoft.com/terms-of-service). Microsoft lo ha bloqueado. Si cree que el contenido se ha bloqueado por error, póngase en contacto con soporte técnico. |
| **No admitido** |El conjunto de datos del informe usa la seguridad de nivel de fila u otra configuración no admitida. Consulte la sección [**Limitaciones**](#limitations) para obtener una lista completa. |
| **Infracción** |El código para insertar está fuera de la directiva de inquilino definida. Esto ocurre normalmente cuando se ha creado un código para insertar y se ha cambiado la configuración del inquilino **Publicar en la web** para excluir al usuario que posee el código para insertar. Si la configuración del inquilino está deshabilitada o el usuario ya no tiene permiso para crear códigos para insertar, los códigos para insertar existentes se muestran con el estado **Infracción**. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Cómo informar de un problema con el contenido de Publicar en Web

Para informar de un problema relacionado con el contenido de **Publicar en la web** insertado en un sitio web o un blog, use el icono **Marca** en la barra inferior, tal como se muestra en la imagen siguiente. Se le pedirá que envíe un correo a Microsoft para explicar el problema. Microsoft evaluará el contenido basándose en las Condiciones del servicio de Power BI y tomará las medidas adecuadas.

Para notificar un problema, seleccione el icono **Marca** de la barra inferior del informe de **Publicar en la web** que se ve.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licencias y precios

Debe ser usuario de Microsoft Power BI para poder usar la características **Publicar en Web**. No es necesario que los visores del informe sean usuarios de Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Cómo funciona (detalles técnicos)

Cuando se crea un código para insertar mediante **Publicar en la web**, el informe se hace visible para los usuarios de Internet. Está disponible públicamente, por lo que se puede esperar que los espectadores compartan fácilmente el informe a través de redes sociales en el futuro. Cuando los usuarios ven el informe, ya sea con la dirección URL pública directa o insertado en una página web o un blog, Power BI almacena en caché la definición de informe y los resultados de las consultas necesarias para ver el informe. Esto garantiza que miles de usuarios simultáneos pueden ver el informe sin afectar al rendimiento.

La memoria caché es de larga duración, por lo que si se actualiza la definición de informe (por ejemplo, si cambia el modo de vista) o se actualizan los datos del informe, los cambios pueden tardar aproximadamente una hora en reflejarse en la versión del informe que ven los usuarios. Por lo tanto, se recomienda organizar el trabajo con antelación y crear el código para insertar de **Publicar en Web** solo cuando esté satisfecho con la configuración.

## <a name="next-steps"></a>Pasos siguientes

- [Elemento web de informes de SharePoint Online](service-embed-report-spo.md) 

- [Inserción de informes en un sitio web o portal seguro](service-embed-secure.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
