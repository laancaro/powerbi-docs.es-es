---
title: ¿Qué es Power BI?
description: 'Información general de Power BI y cómo encajan entre sí las distintas partes: Power BI Desktop, servicio Power BI, Power BI Mobile, Report Server y Power BI Embedded.'
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: b1efe45d52b5a7a18a86407b41e8af287d3c8260
ms.sourcegitcommit: b717118c44499c8fd8f57534a275f2f78aacc0f1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2019
ms.locfileid: "55971657"
---
# <a name="what-is-power-bi"></a>¿Qué es Power BI?
**Power BI** es una colección de servicios de software, aplicaciones y conectores que funcionan conjuntamente para convertir orígenes de datos sin relación entre sí en información coherente, interactiva y atractiva visualmente. Sus datos pueden ser una hoja de cálculo de Excel o una colección de almacenes de datos híbridos locales y basados en la nube. **Power BI** le permite conectarse fácilmente a sus orígenes de datos, visualizar y descubrir qué es importante y compartir eso con cualquiera o con todas las personas que desee.

![Diagrama en el que se muestran los orígenes de entrada para Power BI](media/power-bi-overview/power-bi-input-new.png)

**Power BI** puede ser sencillo y rápido; capaz de crear información rápida a partir de una hoja de cálculo de Excel o una base de datos local. Sin embargo, **Power BI** también es estable y tiene una funcionalidad apta para empresas, listo para un modelado exhaustivo y un análisis en tiempo real, así como para un desarrollo personalizado. De este modo, puede ser su informe personal y herramienta de visualización. También puede hacer las veces de motor de decisión y análisis para los proyectos del grupo, las divisiones o empresas completas.

## <a name="the-parts-of-power-bi"></a>Las partes de Power BI
Power BI consta de una aplicación de escritorio de Windows denominada **Power BI Desktop**, un servicio SaaS (*software como servicio*) en línea denominado **servicio Power BI**, y **aplicaciones móviles** de Power BI para dispositivos Windows, iOS y Android.

![Power BI Desktop, servicio, dispositivos móviles](media/power-bi-overview/power-bi-blocks.png)

Estos tres elementos, **Power BI Desktop**, el **servicio** y el destinado a **aplicaciones móviles**, están diseñados para permitir a los usuarios crear, compartir y utilizar información empresarial de la forma que les resulte más eficaz para su rol.

Un cuarto elemento, **Power BI Report Server**, le permite publicar informes de Power BI en un servidor de informes local, tras crearlos en Power BI Desktop. Obtenga más información sobre el [servidor de informes de Power BI](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>Adaptación de Power BI a su rol
Es posible que la forma en que utilice Power BI dependa de su rol en un proyecto o equipo. Por tanto, otras personas con otros roles podrían utilizar Power BI de un modo distinto, lo cual es normal.

Por ejemplo, podría utilizar principalmente el **servicio Power BI**. Pero su compañero de trabajo, dedicado a procesar los números y crear informes empresariales, podría usar ampliamente **Power BI Desktop** para crear informes y, a continuación, publicarlos en el servicio Power BI, donde puede verlos. Otra compañera que se dedica a las ventas podría utilizar principalmente la aplicación para móviles de Power BI para supervisar el progreso de sus cuotas de venta y profundizar en los detalles de los nuevos clientes potenciales.

Si es un desarrollador, puede usar las API de Power BI para insertar datos en conjuntos de datos o para insertar informes y paneles en sus propias aplicaciones personalizadas. ¿Tiene alguna idea de un nuevo objeto visual? Compílelo usted mismo y compártalo con los demás.  

También podría utilizar cada elemento de **Power BI** en distintos momentos, en función de su objetivo o su rol en un proyecto determinado.

Quizás use **Power BI Desktop** para crear informes para su propio equipo sobre estadísticas de involucración del cliente. También es posible que vea el progreso de fabricación e inventario en un panel en tiempo real del servicio. Su modo de usar Power BI puede basarse en la característica o servicio de Power BI que es la mejor herramienta para su situación. Cada una de las partes de Power BI está a su disposición, razón por la cual es tan flexible y atractivo.

Examine los documentos que pertenecen al rol:
- Power BI para [***diseñadores***](desktop-what-is-desktop.md)
- Power BI para [***consumidores***](consumer/end-user-consumer.md)
- Power BI para [***desarrolladores***](developer/what-can-you-do.md)
- Power BI para [***administradores***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>El flujo de trabajo en Power BI
Un flujo de trabajo común en Power BI comienza con la conexión a orígenes de datos y la compilación de un informe en **Power BI Desktop**. A continuación, publica dicho informe de **Power BI Desktop** en el **servicio Power BI** y lo comparte para que los usuarios finales del **servicio** y los **dispositivos móviles** puedan ver e interactuar con el informe.
Este flujo de trabajo es habitual y muestra cómo los tres elementos principales de Power BI se complementan entre sí.

Esta es una [comparación de Power BI Desktop y el servicio Power BI](service-service-vs-desktop.md) detallada.

¿Pero qué ocurre si no está listo para pasarse a la nube y desea conservar los informes protegidos por un firewall corporativo?  Siga leyendo.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Publicar informes en almacenamiento local con el servidor de informes de Power BI
Cree, implemente y administre Power BI, informes paginados y móviles de forma local con el intervalo de herramientas y servicios que proporciona el servidor de informes de Power BI.

![Diagrama del entorno local](media/power-bi-overview/power-bi-report-server2.png)

Power BI Report Server es una solución que se implemente detrás del firewall y luego entrega los informes a los usuarios deseados de maneras diferentes, ya sea para visualizarlos en un explorador web, en un dispositivo móvil o como correo electrónico. Además, como Power BI Report Server es compatible con Power BI en la nube, puede pasarse a la nube cuando esté listo. 

Obtenga más información sobre el [servidor de informes de Power BI](report-server/get-started.md).

## <a name="next-steps"></a>Pasos siguientes
[Inicio de sesión, obtención de datos y más información sobre el servicio Power BI](service-the-new-power-bi-experience.md)   
[Tutorial: Introducción al servicio Power BI](service-get-started.md)
[Guía de inicio rápido: Conectarse a los datos en Power BI Desktop](desktop-quickstart-connect-to-data.md)