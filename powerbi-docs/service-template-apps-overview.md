---
title: ¿Qué son las aplicaciones de plantilla de Power BI?
description: Este artículo es una introducción del programa de aplicaciones de plantilla de Power BI. Obtenga información sobre cómo crear aplicaciones de Power BI con poca o ninguna codificación, e implementarlas en cualquier cliente de Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/17/2019
ms.author: painbar
ms.openlocfilehash: 528c86a75e2f255ad502dbdf973a61cd9de693d4
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "75224148"
---
# <a name="what-are-power-bi-template-apps"></a>¿Qué son las aplicaciones de plantilla de Power BI?

Las nuevas *aplicaciones de plantilla* de Power BI permiten a los asociados de Power BI crear aplicaciones de Power BI con poca o ninguna codificación, e implementarlas en cualquier cliente de Power BI.  Este artículo es una introducción del programa de aplicaciones de plantilla de Power BI.

Las aplicaciones de plantilla reemplazan a los paquetes de contenido de servicio actuales. Como asociado de Power BI, crea contenido rápido para los clientes y lo publica usted mismo.  

Crea aplicaciones de plantillas que permiten a los clientes conectarse y crear instancias con sus propias cuentas. Como expertos de dominio, pueden desbloquear los datos de forma que sus usuarios empresariales puedan consumirlos fácilmente.  

Debe enviar las aplicaciones de plantilla a Cloud Partner Portal. Las aplicaciones estarán disponibles públicamente en el [Marketplace de aplicaciones de Power BI](https://app.powerbi.com/getdata/services) y en [Microsoft AppSource](https://appsource.microsoft.com/?product=power-bi). Le presentamos una visión de alto nivel de la experiencia pública de creación de aplicaciones de plantilla.

## <a name="power-bi-apps-marketplace"></a>Marketplace de aplicaciones de Power BI

Las aplicaciones de plantilla de Power BI permite que los usuarios de Power BI Pro o de Power BI Premium obtenga información inmediata a través de informes y paneles empaquetados previamente que se pueden conectar a orígenes de datos activos. Muchas aplicaciones de Power BI ya están disponibles en el [Marketplace de aplicaciones de Power BI](https://app.powerbi.com/getdata/services).

|  |
|     :---:      |
| [![Aplicación web de Microsoft Project](./media/service-template-apps-overview/project-web.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_msprojectonline.pbi-microsoftprojectwebapp) [![Aplicación web de Azure Backup](./media/service-template-apps-overview/azure-backup.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-azurebackup.pbi-azurebackup-template) [![Aplicación web Dynamic 365 Business Central - Sales](./media/service-template-apps-overview/dynamics-sales.png)](https://app.powerbi.com/groups/me/getapps/services/microsoftdynsmb.businesscentral_sales) [![Aplicación web Customer Satisfaction de Microsoft Forms Pro](./media/service-template-apps-overview/forms-pro.png)](https://app.powerbi.com/groups/me/getapps/services/msfp.formsprocustomersatisfaction) |
|  |

## <a name="process"></a>Proceso
El proceso general para desarrollar y enviar una aplicación de plantilla implica varias fases. Algunas fases pueden incluir más de una actividad al mismo tiempo.


| Fase | Power BI Desktop |  |Servicio Power BI  |  |Cloud Partner Portal  |
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

2. Cree un informe en Power BI Desktop. Use parámetros para poder guardarlo como un archivo que otros usuarios puedan utilizar. 

3. Cree un área de trabajo para la aplicación de plantilla en el inquilino en el servicio Power BI (app.powerbi.com). 

4. Importe el archivo .pbix y agregue contenido como un panel a la aplicación. 

5. Cree un paquete de prueba para probar la aplicación de plantilla dentro de la organización. 

6. Promueva la aplicación de prueba a preproducción con el fin de enviarla para la validación en AppSource y probarla fuera del inquilino. 

7. Envíe el contenido a la plataforma Cloud Partner para la publicación. 

8. "Publique" la oferta en AppSource y mueva la aplicación a producción en Power BI.

9. Ya puede empezar a desarrollar la próxima versión en la misma área de trabajo, en preproducción. 

## <a name="requirements"></a>Requisitos

Para crear la aplicación de plantilla, necesita permisos para crear una. Vea la [configuración de aplicaciones de plantilla en el portal de administración](service-admin-portal.md#template-apps-settings) de Power BI para obtener más información. 

Para publicar una aplicación de plantilla en el servicio Power BI y AppSource, debe cumplir los requisitos para [convertirse en anunciante de Cloud Marketplace](https://docs.microsoft.com/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Los envíos de aplicaciones de plantilla se administran en [Cloud Partner Portal](https://cloudpartner.azure.com). Use la misma cuenta de registro de Microsoft Developer Center para iniciar sesión. Debe tener una sola cuenta de Microsoft para sus ofertas de AppSource. Las cuentas no deben ser específicas de servicios u ofertas individuales.

## <a name="tips"></a>Recomendaciones 

- Asegúrese de que la aplicación incluye datos de ejemplo para que todos los usuarios puedan empezar a trabajar con un clic. 
- Examine con cuidado la aplicación mediante su instalación en el inquilino y en un inquilino secundario. Asegúrese de que los clientes solo ven lo que quiere que vean. 
- Use AppSource como almacén en línea para hospedar la aplicación. De este modo, todos los usuarios de Power BI podrán encontrar la aplicación. 
- Considere la posibilidad de ofrecer más de una aplicación de plantilla para escenarios únicos independientes. 
- Habilite la personalización de datos, por ejemplo admita la configuración personalizada de parámetros y conexiones mediante el instalador.

Vea [Sugerencias para crear aplicaciones de plantilla en Power BI](service-template-apps-tips.md) para obtener más sugerencias.

## <a name="known-limitations"></a>Limitaciones conocidas

| Característica | Limitación conocida |
|---------|---------|
|Contenido:  Conjuntos de datos   | Debe haber exactamente un conjunto de datos. Solo se permiten los conjuntos de datos creados en Power BI Desktop (archivos .pbix). <br>No se admiten: conjuntos de datos de otras aplicaciones de plantilla, conjuntos de datos de varias áreas de trabajo, informes paginados (archivos .rdl), libros de Excel. |
|Contenido: Paneles | No se admiten los iconos en tiempo real (en otras palabras, no se admiten para los conjuntos de datos de inserción o streaming). |
|Contenido: Flujos de datos | No se admiten: Flujos de datos |
|Contenido de archivos | Solo se admiten archivos PBIX. <br>No se admiten: archivos .rdl (informes paginados), libros de Excel.   |
| Orígenes de datos | Se permiten los orígenes de datos admitidos para la actualización de datos programada en la nube. <br>No se admiten: <li> DirectQuery</li><li>Conexiones dinámicas (no Azure AS).</li> <li>Orígenes de datos locales (no se admiten las puertas de enlace personales y empresariales)</li> <li>Tiempo real (no se admite para los conjuntos de datos de inserción)</li> <li>Modelos compuestos</li></ul> |
| Conjunto de datos: entre áreas de trabajo | No se admiten los conjuntos de datos entre áreas de trabajo  |
| Parámetros de consulta | No se admiten: los parámetros de tipo "Todo" o "Binario" bloquean la operación de actualización del conjunto de datos. |
| Objetos visuales personalizados | Solo se admiten los objetos visuales personalizados disponibles públicamente. No se admiten los [objetos visuales personalizados de la organización](developer/power-bi-custom-visuals-organization.md). |

## <a name="support"></a>Soporte técnico
Para obtener soporte técnico durante el desarrollo, use [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Supervisamos y administramos de forma activa este sitio. Los incidentes del cliente encuentran rápidamente la forma de llegar al equipo adecuado.

## <a name="next-steps"></a>Pasos siguientes

[Creación de una aplicación de plantilla](service-template-apps-create.md)
