---
title: Preguntas más frecuentes sobre objetos visuales de Power BI
description: Exploración de una lista de las preguntas más frecuentes, y sus respuestas, acerca de los objetos visuales de Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 01fe7056c844a9eed96356e478cc23d5593809bd
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75759069"
---
# <a name="power-bi-visuals-faq"></a>Preguntas más frecuentes de objetos visuales de Power BI

## <a name="organizational-power-bi-visuals"></a>Objetos visuales de Power BI de la organización

El portal de administración permite administrar objetos visuales de Power BI para la organización.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>¿Cómo puede gestionar el administrador los objetos visuales de Power BI de la organización?

En el portal de administración, en la pestaña *Objetos visuales de la organización*, el administrador puede ver y [administrar todos los objetos visuales de Power BI de la organización de la empresa](../service-admin-portal.md#organizational-visuals). Esto incluye agregar, deshabilitar, habilitar y eliminar objetos visuales de Power BI.

Los usuarios de la organización pueden encontrar fácilmente objetos visuales de Power BI e importarlos a sus informes directamente desde Power BI Desktop o desde el servicio Power BI.

Cuando el administrador carga una nueva versión del objeto visual de Power BI de la organización, todos en la organización reciben la misma versión actualizada. Todos los informes que usan objetos visuales de Power BI se actualizan automáticamente.

Los usuarios pueden encontrar los objetos de Power BI en la tienda integrada de la organización en Power BI Desktop o en el servicio Power BI, en la pestaña *MI ORGANIZACIÓN*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Si un administrador carga un objeto visual de Power BI desde el Marketplace público a la tienda de la organización, ¿se actualiza automáticamente cuando el proveedor actualiza el objeto visual en el Marketplace público?

No, no hay ninguna actualización automática desde el Marketplace público. Es responsabilidad del administrador actualizar la versión de los objetos visuales de Power BI la organización.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>¿Hay una manera de deshabilitar la tienda de la organización?

No, los usuarios siempre ven la pestaña *MI ORGANIZACIÓN* en Power BI Desktop y en el servicio de Power BI. Si un administrador deshabilita o elimina todos los objetos visuales de Power BI de la organización del portal de administración, el almacén de la organización quedará vacío.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Si el administrador deshabilita los objetos visuales de Power BI del portal de administración (configuración del inquilino), ¿los usuarios todavía tienen acceso a los objetos visuales de Power BI de la organización?

Sí, si el administrador deshabilita los objetos visuales de Power BI del portal de administración, esto no afecta a la tienda de la organización.

Algunas organizaciones deshabilitan los objetos visuales de Power BI y solo permiten los objetos visuales seleccionados manualmente que el administrador de Power BI ha importado y cargado en la tienda de la organización.

La deshabilitación de los objetos visuales de Power BI desde el portal de administración no se aplica en Power BI Desktop. Los usuarios de Desktop pueden seguir agregando y utilizando objetos visuales de Power BI del Marketplace público en sus informes. Sin embargo, esos objetos visuales públicos de Power BI dejan de representarse una vez publicados en el servicio Power BI y generan un error apropiado. 

Cuando se aplica la configuración de objetos visuales de Power BI en el portal de administración, los usuarios del servicio Power BI no pueden importar los objetos visuales de Power BI desde el Marketplace público. Solo se pueden importar los objetos visuales de la tienda de la organización.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>¿Cuáles son las ventajas de los objetos visuales de Power BI en la tienda de la organización?

* Todos los usuarios obtienen la misma versión del objeto visual, que está controlada por el administrador de Power BI. Cuando el administrador actualiza la versión del objeto visual en el portal del administrador, todos los usuarios de la organización reciben la versión actualizada automáticamente.

* No es necesario compartir archivos de objetos visuales por correo electrónico ni por carpetas compartidas. Las ofertas de la tienda de la organización son visibles para todos los miembros que han iniciado sesión.

* Seguridad y compatibilidad, las nuevas versiones de los objetos visuales de Power BI de la organización se actualizan automáticamente en todos los informes.

* Los administradores pueden controlar qué objetos visuales de Power BI estarán disponibles en toda la organización.

* Los administradores pueden habilitar o deshabilitar los objetos visuales para pruebas desde el portal de administración.

## <a name="certified-power-bi-visuals"></a>Objetos visuales de Power BI certificados

### <a name="what-are-certified-power-bi-visuals"></a>¿Qué son los objetos visuales de Power BI certificados?

Los objetos visuales de Power BI certificados son objetos visuales de Power BI que cumplen ciertos [requisitos](power-bi-custom-visuals-certified.md) y que cuentan con la certificación de Microsoft.

En el [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals), los objetos visuales de Power BI certificados tiene un distintivo amarillo que indica que están certificados.

Microsoft no es autor de los objetos visuales de Power BI de terceros. Recomendamos a los clientes que se pongan en contacto directamente con el autor para comprobar la funcionalidad de los objetos visuales de terceros.

### <a name="what-tests-are-done-during-the-certification-process"></a>¿Qué pruebas se realizan durante el proceso de certificación?

Las pruebas del proceso de certificación incluyen, pero no se limitan a: 
* Revisiones de código
* Análisis de código estático
* Pérdida de datos
* Pruebas de vulnerabilidad ante datos aleatorios o inesperados
* Pruebas de penetración
* Pruebas de acceso XSS
* Inserción de datos malintencionados
* Validación de la entrada
* Pruebas funcionales
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>¿El objeto visual de Power BI se certifica nuevamente con cada envío (actualización)?

Sí. Cada vez que se envía a Marketplace una nueva versión de un objeto visual certificado, la actualización de la versión del objeto visual se somete a las mismas comprobaciones de certificación.

La certificación de la actualización de la versión es automática. Si hay una infracción que hace que se rechace la actualización, se envía un correo electrónico al desarrollador para explicar lo que se debe corregir.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>¿Puede un objeto visual de Power BI certificado perder su certificación después de una nueva actualización?

No, no es posible. Un objeto visual certificado no puede perder su certificación con una actualización nueva. La actualización se rechaza.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>¿Necesito compartir mi código en un repositorio público si estoy certificando mi objeto visual de Power BI?

No, no es necesario compartir el código de forma pública.

Proporcione permisos de lectura para comprobar el código del objeto visual de Power BI. Por ejemplo, mediante el uso de un repositorio privado en GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>¿Un certificado visual de Power BI certificado debe estar en el Marketplace?

Sí. Los objetos visuales privados no se certifican.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>¿Cuánto se tarda en certificar el objeto visual?

La certificación de un objeto visual de Power BI nuevo (la primera certificación) puede tardar hasta cuatro semanas. 

La certificación de una versión actualizada de un objeto visual de Power BI puede tardar hasta tres semanas. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>¿El proceso de certificación garantiza que no habrá ninguna pérdida de datos?

Las pruebas realizadas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos. 

Microsoft no es autor de los objetos visuales de Power BI de terceros. Recomendamos a los clientes que se pongan en contacto directamente con el autor para comprobar la funcionalidad de los objetos visuales de Power BI de terceros.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>¿Es seguro usar los objetos visuales de Power BI sin certificar?

Los objetos visuales de Power BI sin certificar no tienen por qué ser inseguros.

Algunos objetos visuales no están certificados porque no cumplen con uno o varios de los [requisitos de certificación](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por ejemplo, conectarse a un servicio externo, como los objetos visuales de mapa o los objetos visuales que usan bibliotecas comerciales.
 
## <a name="visuals-with-additional-purchases"></a>Objetos visuales con compras adicionales

### <a name="what-is-a-visual-with-additional-purchases"></a>¿Qué es un objeto visual con compras adicionales?

Un objeto visual con compras adicionales es similar a los complementos de compras desde la aplicación (IAP). Estos complementos incluyen una etiqueta de precio **Es posible que se requiera una compra adicional**.

Los objetos visuales de Power BI de IAP son objetos visuales de Power BI gratuitos y que se pueden descargar. Los usuarios no pagan nada por descargar estos objetos visuales de Power BI desde el Marketplace.

Los objetos visuales de IAP ofrecen características avanzadas que se pueden comprar desde la aplicación.  

### <a name="what-is-changing-in-the-submission-process"></a>¿Qué cambia en el proceso de envío?

El proceso de envío de los objetos visuales de Power BI de IAP al Marketplace es el mismo que para los objetos visuales de Power BI gratuitos. Puede enviar un objeto visual de Power BI para certificarlo mediante el [Centro de partners](https://docs.microsoft.com/partner-center/).


Cuando registre el objeto visual de Power BI, vaya a la pestaña *Configuración del producto* y active la casilla *Mi producto necesita la compra de un servicio*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>¿Qué debo hacer antes de enviar mi objeto visual de Power BI de IAP?

Si trabaja en un objeto visual de Power BI de IAP, asegúrese de que cumple con las [directrices](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Los objetos visuales de Power BI gratuitos con una característica de IAP agregada deben mantener las mismas características gratuitas ofrecidas anteriormente. Puede agregar características de pago avanzadas opcionales sobre las características gratuitas antiguas. Se recomienda enviar el objeto visual de Power BI de IAP con las características avanzadas como un nuevo objeto visual de Power BI y no actualizar el anterior que era gratis.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>¿Es necesario certificar los objetos visuales de Power BI de IAP?

El proceso de [certificación](power-bi-custom-visuals-certified.md) es opcional. Es el desarrollador el que decide si certifica o no su objeto visual de Power BI de IAP.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>¿Puedo obtener la certificación de mi objeto visual de Power BI de IAP?

Sí, una vez que el equipo de AppSource aprueba el objeto visual de Power BI de IAP, puede enviar el objeto visual de Power BI para su [certificación](power-bi-custom-visuals-certified.md).

La certificación es un proceso opcional y usted decide si desea certificar su objeto visual de IAP.

## <a name="additional-questions"></a>Preguntas adicionales

### <a name="how-to-get-support"></a>¿Cómo obtener soporte técnico?

Si tiene alguna pregunta, problema o quiere hacer un comentario, no dude en ponerse en contacto con el equipo de soporte técnico de los objetos visuales de Power BI en pbicvsupport@microsoft.com.  

## <a name="next-steps"></a>Pasos siguientes

Para más información, visite [Solución de problemas de los objetos visuales de Power BI](power-bi-custom-visuals-troubleshoot.md).
