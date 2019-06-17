---
title: Preguntas más frecuentes acerca de los objetos visuales personalizados de Power BI
description: Examinar una lista de las preguntas más frecuentes, y sus respuestas, acerca de los objetos visuales personalizados de Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 0fcb3451249c121281790dca77bd6008c39deaef
ms.sourcegitcommit: 24781cdab5fbe43fc14248db636169cc54ef6721
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66497929"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Preguntas más frecuentes acerca de los objetos visuales personalizados de Power BI

## <a name="organizational-custom-visuals"></a>Objetos visuales personalizados de organización

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>¿Cómo puede el administrador administrar los objetos visuales personalizados de organización?

En el portal de administración, en la pestaña "Objetos visuales personalizados de organización", el administrador puede ver y [administrar todos los objetos visuales personalizados de organización de la empresa](service-admin-portal.md#organizational-visuals): agregar, deshabilitar, habilitar y eliminar.
Ya no hay necesidad de compartir esos objetos visuales por correo electrónico o carpeta compartida. Una vez implementados en el repositorio de la organización, los usuarios pueden encontrarlos fácilmente e importarlos en sus informes directamente desde Power BI Desktop o el servicio correspondiente. Los objetos visuales personalizados de la organización se pueden encontrar en la tienda integrada (en el escritorio y en el servicio) en la pestaña *MI ORGANIZACIÓN*. Cuando el administrador carga una nueva versión del objeto visual personalizado de la organización, todos en la organización reciben la misma versión actualizada. Los autores de los informes no necesitan eliminar el objeto visual de sus informes para obtener la nueva versión de estos objetos visuales, ya que todos los informes que utilizan estos objetos se actualizan automáticamente. El mecanismo de actualización es similar a los objetos visuales de Marketplace.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Si un administrador carga un objeto visual personalizado desde el Marketplace público a la tienda de la organización, ¿se actualiza automáticamente cuando el proveedor actualiza el objeto visual en el Marketplace público?

No, no hay ninguna actualización automática desde el Marketplace público.
Es responsabilidad del administrador actualizar la versión de los objetos visuales personalizados de la organización.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>¿Hay una manera de deshabilitar la tienda de la organización?

No, los usuarios siempre ven la pestaña "MI ORGANIZACIÓN" en Power BI Desktop y en el servicio. El administrador puede deshabilitar o eliminar todos los objetos visuales personalizados de la organización del portal de administración y la tienda de la organización está vacía.
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>Si el administrador deshabilita los objetos visuales personalizados del portal de administración (configuración del inquilino), ¿los usuarios todavía tienen acceso a los objetos visuales personalizados de la organización?

Sí, si el administrador deshabilita los objetos visuales personalizados del portal de administración, esto no afecta a la tienda de la organización. Algunas organizaciones deshabilitan los objetos visuales personalizados y solo permiten los objetos visuales seleccionados manualmente que el administrador de Power BI ha importado y cargado en la tienda de la organización. La deshabilitación de los objetos visuales personalizados desde el portal de administración no se aplica en Power BI Desktop. Los usuarios de Desktop pueden seguir agregando y utilizando objetos visuales personalizados del Marketplace público en sus informes. Sin embargo, esos objetos visuales públicos personalizados dejan de representarse una vez publicados en el servicio Power BI y emiten un error apropiado. Al usar el servicio Power BI, no es posible importar objetos visuales personalizados desde el Marketplace público. Solo se pueden importar objetos visuales de la tienda de la organización porque la configuración personalizada de objetos visuales en el portal de administración se aplica en el servicio Power BI.

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>¿Por qué la tienda de la organización y los objetos visuales personalizados de la organización son una gran solución empresarial?

* Todos los usuarios obtienen la misma versión del objeto visual, que está controlada por el administrador de Power BI. Cuando el administrador actualiza la versión del objeto visual en el portal del administrador, todos los usuarios de la organización reciben la versión actualizada automáticamente.

* Ya no es necesario compartir archivos de objetos visuales por correo electrónico o carpetas compartidas. Un solo lugar, visible para todos los miembros que han iniciado sesión.

* Seguridad y compatibilidad, las nuevas versiones de los objetos visuales personalizados de la organización se actualizan automáticamente en todos los informes similares a los objetos visuales del Marketplace.

* Los usuarios de la organización que utilizan los objetos visuales personalizados de la organización deben iniciar sesión para ver y utilizar los objetos visuales personalizados de la organización, que son un elemento de seguridad para la organización.

* Los administradores pueden controlar qué objetos visuales personalizados estarán disponibles en la organización.

* Los administradores pueden habilitar o deshabilitar los objetos visuales para pruebas desde el portal de administración. Una mejor aplicación de la seguridad, ya que estos objetos visuales solo se permitirán a los miembros de la organización.

## <a name="certified-custom-visuals"></a>Objetos visuales personalizados certificados

### <a name="what-are-certified-custom-visuals"></a>¿Qué son los objetos visuales personalizados certificados?

Los objetos visuales personalizados certificados son objetos visuales en [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) que cumplen ciertos requisitos de código [especificados](power-bi-custom-visuals-certified.md) y que el equipo de Power BI ha probado.  Las pruebas realizadas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos. Pero Microsoft no es el autor de los objetos visuales personalizados de terceros, y se recomienda a los clientes que se pongan en contacto directamente con el autor para comprobar la funcionalidad de cada objeto visual.

### <a name="what-tests-are-done-during-the-certification-process"></a>¿Qué pruebas se realizan durante el proceso de certificación?

Las pruebas del proceso de certificación incluyen, pero no se limitan a: revisiones de código, análisis de código estático, pérdida de datos, pruebas de vulnerabilidad ante datos aleatorios o inesperados, pruebas de penetración, pruebas de acceso XSS, inserción de datos malintencionados, validación de la entrada y pruebas funcionales.
 
### <a name="do-you-certify-visuals-every-submission"></a>¿Se certifican los objetos visuales en cada envío?

Sí. Cada vez que se envía a Marketplace una nueva versión de un objeto visual certificado, la actualización de la versión del objeto visual se somete a las mismas comprobaciones de certificación.

Nota para desarrolladores: Si se va a enviar una actualización de la versión del objeto visual certificado, no es necesario enviar un correo electrónico independiente como [primera solicitud de certificación.](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification) La certificación de actualización de la versión se produce de forma automática y las infracciones que provocan un rechazo se envían en un correo electrónico para explicar los aspectos que se deben corregir. 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>¿Es posible que un objeto visual certificado deje de estar certificado con una nueva actualización?

No, no es posible. Un objeto visual certificado no puede dejar de estarlo con una nueva actualización. La actualización se rechaza.
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>¿Tengo que compartir el código en el repositorio público si voy a realizar el envío para el proceso de certificación?

No, no es necesario compartir el código de forma pública. Pero tendrá que asignarnos permisos de lectura para comprobar el código de los objetos visuales. Por ejemplo, repositorio privado en GitHub.
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>¿Es necesario [publicar](https://docs.microsoft.com/power-bi/developer/office-store) el objeto visual en [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) para certificarlo?

Sí. Publicar primero el objeto visual en Marketplace es un requisito obligatorio para la certificación.
Para certificar un objeto visual personalizado, debe estar en nuestros servidores. No podemos certificar objetos visuales privados.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>¿Cuánto se tarda en certificar el objeto visual?

Para la versión actualizada puede tardar hasta tres semanas. Para un envío nuevo (la primera certificación) puede tardar hasta cuatro semanas. 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>¿El proceso de certificación garantiza que no se produzca ninguna pérdida de datos?

Las pruebas realizadas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos. Pero Microsoft no es el autor de los objetos visuales personalizados de terceros y recomendamos a los clientes que se pongan en contacto directamente con el autor para comprobar la funcionalidad de cada objeto visual.
 
### <a name="are-uncertified-custom-visuals-safe-to-use"></a>¿Son seguros de usar los objetos visuales personalizados sin certificar?

Los objetos visuales personalizados sin certificar no tienen por qué ser inseguros.
Algunos objetos visuales no están certificados porque no cumplen con uno o varios de los [requisitos de certificación](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por ejemplo, conectarse a un servicio externo, como los objetos visuales de mapa o los objetos visuales que usan bibliotecas comerciales.
 
## <a name="visuals-with-additional-purchases"></a>Objetos visuales con compras adicionales

### <a name="what-is-a-visual-with-additional-purchases"></a>¿Qué es un objeto visual con compras adicionales?

Un objeto visual con compras adicionales es similar a los complementos de compra desde la aplicación (IAP) del Marketplace que tienen la etiqueta de precio **Es posible que se requiera una compra adicional**.

Los objetos visuales personalizados de IAP se pueden descargar de manera gratuita: los usuarios no pagan por descargarlos desde el Marketplace. Los objetos visuales de IAP ofrecen características avanzadas que se pueden comprar desde la aplicación.  

### <a name="whats-the-benefit-to-developers"></a>¿Cuál es la ventaja para los desarrolladores?

Los objetos visuales personalizados de IAP en AppSource serán visibles para los muchos visitantes diarios, lo que contribuirá a incrementar el tráfico y el conocimiento de los objetos visuales personalizados de IAP y de usted como desarrollador.

Si hasta hace poco administraba los objetos visuales a través de su sitio web, ahora puede enviarlos a AppSource. Esto aumentará el nivel de visibilidad de los objetos visuales de IAP dentro de la Comunidad de Power BI.

Gracias al sistema de reseñas y clasificaciones de AppSource, los objetos visuales disfrutan de un canal de comentarios directos de los clientes que usan el objeto visual personalizado de IAP.  

Una vez que el equipo de validación de AppSource aprueba el objeto visual de IAP, también puede enviarlo para su certificación, aunque esto es opcional.  

Una vez certificado el objeto visual personalizado de IAP, se puede exportar a PowerPoint e incluir en los correos electrónicos que reciban los usuarios al suscribirse a las páginas de informes. Actualmente, si se envían los objetos visuales de IAP al Marketplace, los objetos visuales personalizados de IAP también pueden certificarse y admitir un conjunto de características adicionales.  

### <a name="do-iap-visuals-need-to-be-certified"></a>¿Es necesario certificar los objetos visuales de IAP?

El proceso de certificación es opcional. Al igual que con los objetos visuales gratuitos, el desarrollador decide si certifica sus objetos visuales personalizados de IAP.

### <a name="what-is-changing-in-the-submission-process"></a>¿Qué cambia en el proceso de envío?

El proceso de envío de los objetos visuales personalizados de IAP al Marketplace es el mismo que para los objetos visuales gratuitos. El envío se lleva a cabo desde el panel del vendedor.  El único cambio en el proceso de envío es que los desarrolladores deben incluir el mensaje siguiente en las notas de desarrollador en el panel de vendedores: "Objeto visual con compra desde la aplicación". También se deberá proporcionar un token o una clave de licencia si es necesario para validar las características avanzadas o de pago.  

No habrá ninguna opción nueva en el panel de vendedores: *gratis con compras desde la aplicación*, deberá enviar los objetos visuales de IAP como *gratis*.

Incluya también una descripción larga en la que informe a los usuarios de qué características son gratuitas y cuáles requieren de una compra adicional para funcionar.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>¿Qué debo hacer antes de enviar mi objeto visual personalizado de IAP?

Si está trabajando en un objeto visual personalizado de IAP o ya tiene uno, asegúrese de que cumple con las directrices.  

Si tiene un logotipo en el objeto visual personalizado, compruebe que cumple con las directrices relativas a los logotipos (color, ubicación, tamaño y acción desencadenada).

En las directrices también encontrará notas sobre los procedimientos recomendados.  
> [!Note]
> Todos los objetos visuales gratuitos deben mantener las mismas características gratuitas proporcionadas anteriormente. Puede agregar características de pago avanzadas opcionales sobre las características gratuitas antiguas. Se recomienda enviar los objetos visuales de IAP con las características avanzadas como objetos visuales nuevos y no actualizar los objetos visuales gratuitos antiguos.

### <a name="can-i-get-my-iap-custom-visual-certified"></a>¿Puedo certificar mi objeto visual personalizado de IAP?

Sí, igual que los objetos visuales gratuitos.  Una vez que el equipo de AppSource apruebe el objeto visual personalizado de IAP, puede enviarlo para someterlo al proceso de certificación.

Para certificar el objeto visual, debe cumplir los requisitos de certificación; por ejemplo, el objeto visual no puede acceder a servicios externos para la validación de licencias.

Recuerde que la certificación es un proceso opcional, y usted decide si desea certificar su objeto visual de IAP.

## <a name="additional-questions"></a>Preguntas adicionales

### <a name="how-to-get-support"></a>¿Cómo obtener soporte técnico?

Si tiene alguna pregunta, problema o quiere hacer un comentario, no dude en ponerse en contacto con el equipo de soporte técnico de los objetos visuales personalizados: *pbicvsupport@microsoft.com*  .  

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, visite [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Solución de problemas con objetos visuales personalizados de Power BI).
