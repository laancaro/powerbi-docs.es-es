---
title: ¿Qué son las aplicaciones de plantilla de Power BI?
description: Este artículo es una introducción del programa de aplicaciones de plantilla de Power BI. Obtenga información sobre cómo crear aplicaciones de Power BI con poca o ninguna codificación, e implementarlas en cualquier cliente de Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: tebercov
ms.openlocfilehash: c05b53a5fd61d348b6d304b17123d5f2497ab647
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408213"
---
# <a name="what-are-power-bi-template-apps"></a>¿Qué son las aplicaciones de plantilla de Power BI?

Las nuevas *aplicaciones de plantilla* de Power BI permiten a los asociados de Power BI crear aplicaciones de Power BI con poca o ninguna codificación, e implementarlas en cualquier cliente de Power BI.  Este artículo es una introducción del programa de aplicaciones de plantilla de Power BI.

Las aplicaciones de plantilla reemplazan a los paquetes de contenido de servicio actuales. Como asociado de Power BI, crea contenido rápido para los clientes y lo publica usted mismo.  

Crea aplicaciones de plantillas que permiten a los clientes conectarse y crear instancias con sus propias cuentas. Como expertos de dominio, pueden desbloquear los datos de forma que sus usuarios empresariales puedan consumirlos fácilmente.  

Debe enviar las aplicaciones de plantilla a Cloud Partner Portal. Después, las aplicaciones pasan a estar disponibles de forma pública en la galería de aplicaciones de Power BI (app.powerbi.com/getdata/services) y en Microsoft AppSource (appsource.microsoft.com). Le presentamos una visión de alto nivel de la experiencia pública de creación de aplicaciones de plantilla.  

## <a name="process"></a>Proceso
El proceso general para desarrollar y enviar una aplicación de plantilla implica varias fases. Algunas fases pueden incluir más de una actividad al mismo tiempo.


| Fase | Power BI Desktop |  |Servicio Power BI  |  |Cloud Partner Portal  |
|---|--------|--|---------|---------|---------|
| **Uno** | Crear un modelo de datos y un informe en un archivo .pbix. |  | Crear un área de trabajo. Importar el archivo .pbix. Crear un panel complementario.  |  | Registrarse como asociado. |
| **Dos** |  |  | Crear un paquete de prueba y ejecutar la validación interna.        |  | |
| **Tres** | |  | Promover el paquete de prueba a preproducción para la validación fuera del inquilino de Power BI y enviarlo a AppSource.  |  | Con el paquete de preproducción, crear una oferta de aplicación de plantilla de Power BI e iniciar el proceso de validación. |
| **Cuatro** | |  | Promover el paquete de preproducción a producción. |  | Publicar |

## <a name="before-you-begin"></a>Antes de empezar

Para crear la aplicación de plantilla, necesita permisos para crear una. Vea la configuración de aplicaciones de plantilla en el portal de administración de Power BI para obtener más información. 

Para publicar una aplicación de plantilla en el servicio Power BI y AppSource, debe cumplir los requisitos para [convertirse en anunciante de Cloud Marketplace](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Pasos generales

Estos son los pasos generales. 

1. [Revise los requisitos](#requirements) para asegurarse de que los cumple. 

1. Cree un informe en Power BI Desktop. Use parámetros para poder guardarlo como un archivo que otros usuarios puedan utilizar. 

1. Cree un área de trabajo para la aplicación de plantilla en el inquilino en el servicio Power BI (app.powerbi.com). 

1. Importe el archivo .pbix y agregue contenido como un panel a la aplicación. 

1. Cree un paquete de prueba para probar la aplicación de plantilla dentro de la organización. 

1. Promueva la aplicación de prueba a preproducción con el fin de enviarla para la validación en AppSource y probarla fuera del inquilino. 

1. Envíe el contenido a la plataforma Cloud Partner para la publicación. 

1. "Publique" la oferta en AppSource y mueva la aplicación a producción en Power BI.
2. Ya puede empezar a desarrollar la próxima versión en la misma área de trabajo, en preproducción. 

## <a name="requirements"></a>Requisitos

Para crear la aplicación de plantilla, necesita permisos para crear una. Vea la [configuración de aplicaciones de plantilla en el portal de administración](service-admin-portal.md#template-apps-settings) de Power BI para obtener más información. 

Para publicar una aplicación de plantilla en el servicio Power BI y AppSource, debe cumplir los requisitos para [convertirse en anunciante de Cloud Marketplace](https://docs.microsoft.com/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Los envíos de aplicaciones de plantilla se administran en [Cloud Partner Portal](https://cloudpartner.azure.com). Use la misma cuenta de registro de Microsoft Developer Center para iniciar sesión. Debe tener una sola cuenta de Microsoft para sus ofertas de AppSource. Las cuentas no deben ser específicas de servicios u ofertas individuales.

## <a name="tips"></a>Sugerencias 

- Asegúrese de que la aplicación incluye datos de ejemplo para que todos los usuarios puedan empezar a trabajar con un clic. 
- Examine con cuidado la aplicación mediante su instalación en el inquilino y en un inquilino secundario. Asegúrese de que los clientes solo ven lo que quiere que vean. 
- Use AppSource como almacén en línea para hospedar la aplicación. De este modo, todos los usuarios de Power BI podrán encontrar la aplicación. 
- Considere la posibilidad de ofrecer más de una aplicación de plantilla para escenarios únicos independientes. 
- Habilite la personalización de datos, por ejemplo admita la configuración personalizada de parámetros y conexiones mediante el instalador.

Vea [Sugerencias para crear aplicaciones de plantilla en Power BI](service-template-apps-tips.md) para obtener más sugerencias.

## <a name="support"></a>Soporte técnico
Para obtener soporte técnico durante el desarrollo, use [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Supervisamos y administramos de forma activa este sitio. Los incidentes del cliente encuentran rápidamente la forma de llegar al equipo adecuado.

## <a name="next-steps"></a>Pasos siguientes

[Creación de una aplicación de plantilla](service-template-apps-create.md)
