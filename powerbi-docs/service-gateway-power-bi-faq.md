---
title: 'Preguntas más frecuentes sobre la puerta de enlace de datos local: Power BI'
description: Estas son las preguntas más frecuentes sobre la puerta de enlace de datos local para Power BI. Aquí se reúnen en un solo lugar las preguntas más frecuentes sobre la puerta de enlace que se usa en Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 99a03f88ed5f6585ca8ed6d64f396e70cdd046e5
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68272755"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Preguntas más frecuentes sobre la puerta de enlace de datos local: Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Pregunta:** ¿Necesito actualizar la puerta de enlace personal?  
**Respuesta:** No, puede seguir usando la puerta de enlace personal para Power BI.

**Pregunta:** ¿Hay algún permiso necesario especial para instalar la puerta de enlace y administrarla en el servicio Power BI?
**Respuesta:** No se requieren permisos especiales.

**Pregunta:** ¿Puedo cargar libros de Excel con modelos de datos de Power Pivot que se conectan a orígenes de datos locales? ¿Necesito una puerta de enlace para este escenario?  
**Respuesta:** Sí, puede cargar el libro. Y no, no necesita una puerta de enlace. Sin embargo, dado que los datos residen en el modelo de datos de Excel, los informes de Power BI basados en el libro de Excel no serán dinámicos. Para actualizar los informes de Power BI, deberá volver a cargar un libro actualizado cada vez. O bien, use la puerta de enlace con la actualización programada.

**Pregunta:** Si los usuarios comparten paneles con una conexión DirectQuery, ¿los otros usuarios podrán ver los datos aunque que no tengan los mismos permisos?  
**Respuesta:** Para un panel conectado a Analysis Services, los usuarios sólo verán los datos a los que tienen acceso. Si los usuarios no tienen los mismos permisos, no podrán ver ningún dato. Para otros orígenes de datos, todos los usuarios compartirán las credenciales especificadas por el administrador para ese origen de datos.

**Pregunta:** ¿Por qué no puedo conectarme a mi servidor de Oracle?  
**Respuesta:** Es posible que tenga que instalar el cliente de Oracle y configurar el archivo tnsnames.ora con la información correcta del servidor. Se trata de una instalación independiente fuera de la puerta de enlace. Para obtener más información, consulte [Instalación del cliente de Oracle](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Pregunta:** ¿Funcionará la puerta de enlace con ExpressRoute?  
**Respuesta:** Sí. Para obtener más información acerca de ExpressRoute y Power BI, consulte [Power BI y ExpressRoute](service-admin-power-bi-expressroute.md).

**Pregunta:** Estoy usando scripts de R. ¿Está admitido?
**Respuesta:** Los scripts de R solo son compatibles con el modo personal.

## <a name="analysis-services-in-power-bi"></a>Analysis Services en Power BI

**Pregunta:** ¿Puedo usar msdmpump.dll para crear asignaciones personalizadas de nombres de usuario efectivos para Analysis Services?  
**Respuesta:** No. Esa capacidad no se admite en este momento.

**Pregunta:** ¿Puedo usar la puerta de enlace para la conexión a una instancia multidimensional (OLAP)?  
**Respuesta:** Sí. La puerta de enlace de datos local admite conexiones dinámicas a los modelos tabular y multidimensional de Analysis Services.

**Pregunta:** ¿Qué ocurre si instalo la puerta de enlace en un equipo en un dominio distinto del de mi servidor local que usa la autenticación de Windows?  
**Respuesta:** No hay nada seguro en este caso. Todo depende de la relación de confianza entre los dos dominios. Si los dos dominios diferentes están en un modelo de dominio de confianza, la puerta de enlace podría ser capaz de conectarse al servidor de Analysis Services y se podría resolver el nombre de usuario efectivo. Si no es así, se puede producir un error de inicio de sesión.

**Pregunta:** ¿Cómo puedo averiguar qué nombre de usuario efectivo se pasa a mi servidor de Analysis Services local?  
**Respuesta:** Respondemos en el [artículo de solución de problemas](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Pasos siguientes

* [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

