---
title: Preguntas más frecuentes acerca de los objetos visuales personalizados de Power BI
description: Examinar una lista de las preguntas más frecuentes, y sus respuestas, acerca de los objetos visuales personalizados de Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223085"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Preguntas más frecuentes acerca de los objetos visuales personalizados de Power BI

## <a name="organizational-custom-visuals"></a>Objetos visuales personalizados de organización

**¿Cómo puede el administrador administrar los objetos visuales personalizados de organización?**

En el portal de administración, en la pestaña "Objetos visuales personalizados de organización", el administrador puede ver y [administrar todos los objetos visuales personalizados de organización de la empresa](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): agregar, deshabilitar, habilitar y eliminar.
Ya no hay necesidad de compartir esas imágenes por correo electrónico o carpeta compartida. Una vez implementados en el repositorio de organización, los usuarios de la organización pueden detectarlos fácilmente e importarlos en sus informes directamente desde Power BI Desktop o el servicio correspondiente. Los objetos visuales personalizados de la organización se pueden encontrar en la tienda integrada (en Desktop y en el servicio) en la pestaña "MI ORGANIZACIÓN". Cuando el administrador carga una nueva versión del objeto visual personalizado de la organización, todos en la organización reciben la misma versión actualizada. Los autores de los informes no necesitan eliminar el objeto visual de sus informes para obtener la nueva versión de estos objetos visuales, ya que todos los informes que utilizan estos objetos se actualizan automáticamente. El mecanismo de actualización es similar a los objetos visuales de Marketplace.

**Si un administrador carga un objeto visual personalizado desde el Marketplace público a la tienda de la organización, ¿se actualiza automáticamente una vez que un proveedor actualiza el objeto visual en el Marketplace público?**

No, no hay ninguna actualización automática del Marketplace público.
Es responsabilidad del administrador actualizar la versión de los objetos visuales personalizados de la organización si lo desea.

**¿Hay una manera de deshabilitar la tienda de la organización?**

No, los usuarios siempre ven la pestaña "MI ORGANIZACIÓN" en Power BI Desktop y en el servicio. El administrador puede deshabilitar o eliminar todos los objetos visuales personalizados de la organización del portal de administración y la tienda de la organización está vacía.
  
**Si el administrador deshabilita los objetos visuales personalizados del portal de administración (configuración del inquilino), ¿los usuarios todavía tienen acceso a los objetos visuales personalizados de la organización?**

Sí, si el administrador deshabilita los objetos visuales personalizados del portal de administración, esto no afecta a la tienda de la organización. Algunas organizaciones deshabilitan los objetos visuales personalizados y solo permiten los objetos visuales seleccionados manualmente que el administrador de Power BI ha importado y cargado en la tienda de la organización. La deshabilitación de los objetos visuales personalizados desde el portal de administración no se aplica en Power BI Desktop. Los usuarios de Desktop todavía pueden agregar y utilizar objetos visuales personalizados del Marketplace público en sus informes. Sin embargo, esos objetos visuales públicos personalizados dejan de representarse una vez publicados en el servicio Power BI y emiten un error apropiado. Al utilizar el servicio Power BI, no es posible importar objetos visuales personalizados desde el Marketplace público. Solo se pueden importar objetos visuales de la tienda de la organización porque la configuración personalizada de objetos visuales en el portal de administración se aplica en el servicio Power BI.

**¿Por qué la tienda de la organización y los objetos visuales personalizados de la organización son una gran solución empresarial?**

* Todos los usuarios obtienen la misma versión del objeto visual, que está controlada por el administrador de Power BI. Cuando el administrador actualiza la versión del objeto visual en el portal del administrador, todos los usuarios de la organización reciben la versión actualizada automáticamente.

* Ya no es necesario compartir archivos de objetos visuales por correo electrónico o carpetas compartidas. Un solo lugar, visible para todos los miembros que han iniciado sesión.

* Seguridad y compatibilidad, las nuevas versiones de los objetos visuales personalizados de la organización se actualizan automáticamente en todos los informes similares a los objetos visuales del Marketplace.

* Los usuarios de la organización que utilizan los objetos visuales personalizados de la organización deben iniciar sesión para ver y utilizar los objetos visuales personalizados de la organización, que son un elemento de seguridad para la organización.

* Los administradores pueden controlar qué objetos visuales personalizados estarán disponibles en la organización.

* Los administradores pueden habilitar o deshabilitar los objetos visuales para pruebas desde el portal de administración. Una mejor aplicación de la seguridad, ya que estos objetos visuales solo se permitirán a los miembros de la organización.

## <a name="certified-custom-visuals"></a>Objetos visuales personalizados certificados

**¿Qué son los objetos visuales personalizados certificados?**

Los objetos visuales personalizados certificados son objetos visuales en [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) que cumplen con ciertos requisitos de código [especificados](power-bi-custom-visuals-certified.md) y que el equipo de Power BI ha probado.  Las pruebas realizadas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos; sin embargo, Microsoft no es el autor de los objetos visuales personalizados de terceros, por lo que aconsejamos a los clientes que se pongan en contacto directamente con el autor para comprobar la funcionalidad de dicho objeto visual.

## <a name="next-steps"></a>Pasos siguientes

Para obtener información sobre cómo solucionar problemas, visite [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Solución de problemas con objetos visuales personalizados de Power BI).
