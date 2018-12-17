---
title: ¿Qué es un panel y cómo se abre?
description: Los paneles son una característica clave del servicio Power BI.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 732e3fcc05ee48135fb0b62d462ef8abcfae96be
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280521"
---
# <a name="dashboards-for-power-bi-service-consumers"></a>Panel para los consumidores del servicio Power BI

Un ***panel*** de Power BI tiene una sola página, a menudo denominada lienzo, que usa visualizaciones para contar una historia. Dado que se limita a una sola página, un panel bien diseñado contiene únicamente los elementos más importantes de esa historia.

![panel](media/end-user-dashboards/power-bi-dashboard2.png)

Las visualizaciones que se ven en el panel se denominan *iconos* y están *ancladas* al panel de informes. Si no está familiarizado con Power BI, puede obtener una buena base leyendo [Conceptos básicos de Power BI](end-user-basic-concepts.md).

> [!NOTE]
> Los paneles son una característica del servicio Power BI pero no están disponibles en Power BI Desktop. No se pueden crear paneles en dispositivos móviles, pero se pueden [ver y compartir](mobile/mobile-apps-view-dashboard.md).
> 
> 

Las visualizaciones de un panel proceden de informes y cada informe se basa en un conjunto de datos. De hecho, una manera de pensar en un panel es como vía de entrada a los informes y conjuntos de datos subyacentes. La selección de una visualización lleva al informe (y al conjunto de datos) utilizado para crearla.

![Diagrama que muestra la relación entre paneles, informes, conjuntos de datos](media/end-user-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Ventajas de los paneles
Los paneles son una magnífica manera de supervisar su empresa, buscar respuestas y ver las métricas más importantes de un vistazo. Las visualizaciones de un panel pueden proceder de un conjunto de datos subyacente o de varios y de un informe subyacente o de varios. Un panel combina datos locales y procedentes de la nube, lo que proporciona una vista consolidada, independientemente de donde residen los datos.

Un panel no es simplemente una bonita imagen: es algo muy interactivo y personalizable, y los iconos se actualizarán según van cambiando los datos subyacentes.

## <a name="dashboards-versus-reports"></a>Paneles frente a informes
Los informes suelen confundirse con paneles, ya que son igualmente lienzos con visualizaciones. Pero hay algunas diferencias importantes.

| **Funcionalidad** | **Paneles** | **Informes** |
| --- | --- | --- |
| Páginas |Una página |Una o varias páginas |
| Orígenes de datos |Uno o varios informes y uno o varios conjuntos de datos por cada panel |Un único conjunto de datos por informe |
| Disponible en Power BI Desktop |No |Sí, se pueden crear y ver informes en Desktop |
| Anclaje |Se pueden anclar visualizaciones existentes (iconos) solo desde el panel actual en los demás paneles |Se pueden anclar visualizaciones (como iconos) en cualquiera de los paneles Se pueden anclar páginas de informes completas en cualquiera de los paneles |
| Suscribirse |No es posible suscribirse a un panel |Es posible suscribirse a páginas de informes |
| Filtrado |No es posible filtrar ni segmentar |Numerosas formas de filtrar, resaltar y segmentar |
| Establecimiento de alertas |Se pueden crear alertas para enviarlas por correo electrónico cuando se cumplen determinadas condiciones |No |
| Destacado |Se puede establecer un panel como panel "destacado" |No es posible crear un informe destacado |
| Consultas en lenguaje natural |Disponible en el panel |No disponible en los informes |
| Se puede cambiar el tipo de visualización |No. De hecho, si el propietario de un informe cambia el tipo de visualización en el informe, la visualización anclada en el panel no se actualizará |Sí |
| Se pueden ver campos y tablas del conjunto de datos subyacentes |No. Se pueden exportar datos pero no se pueden ver tablas ni campos en el panel |Sí. Se pueden ver tablas, campos y valores del conjunto de datos |
| Se pueden crear visualizaciones |Se limita a agregar widgets al panel mediante "Agregar icono" |Se pueden crear muchos tipos diferentes de objetos visuales, agregar objetos visuales personalizados, editarlos, etc. con permisos de edición |
| Personalización |Se puede hacer una serie de cosas con las visualizaciones (iconos) como mover y organizar, cambiar el tamaño, agregar vínculos, cambiar el nombre, eliminar y mostrar en pantalla completa, pero los datos y visualizaciones en sí son de solo lectura |En la Vista de lectura, se puede publicar, insertar, filtrar, exportar, descargar como .pbix, ver contenido relacionado, generar códigos QR, analizar en Excel, etc.  En la Vista de edición, se puede hacer todo lo que se ha mencionado hasta ahora y mucho más. |

## <a name="dashboard-creators-and-dashboard-consumers"></a>Creadores de paneles y consumidores de paneles
En función de su rol, es posible que sea alguien que crea paneles para su propio uso o para compartir con compañeros de trabajo. Desea información sobre cómo crear y compartir paneles. O bien, es posible que sea alguien que recibe los paneles de otras personas. Desea información sobre cómo comprender e interactuar con el panel.

Estos son algunos de los temas, por rol, que le ayudarán a comenzar.

Power BI Pro es necesario tanto para compartir un panel como para ver un panel compartido.

### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Si va a recibir y consumir paneles
* Familiarícese con los paneles viendo uno de nuestros [paneles de ejemplo](../sample-tutorial-connect-to-the-samples.md).
* Obtenga información acerca de los [iconos de panel](end-user-tiles.md) y lo que ocurre al seleccionar uno.
* ¿Desea realizar un seguimiento de un icono de panel individual y recibir un mensaje de correo electrónico al alcanzar un umbral determinado? [Cree alertas en iconos](end-user-alerts.md).
* Diviértase preguntando a su panel. Aprenda a utilizar [Preguntas y respuestas de Power BI](end-user-q-and-a.md) para formular una pregunta sobre los datos y recibir una respuesta en forma de visualización.

> [!TIP]
> Si no encuentra lo que está buscando aquí, utilice la tabla de contenido de la izquierda.
> 

## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](../power-bi-overview.md)  
[Power BI: Conceptos básicos](end-user-basic-concepts.md)  