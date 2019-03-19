---
title: Instrucciones para objetos visuales de Power BI
description: Aprenda a publicar objetos visuales personalizados en AppSource para que otros usuarios puedan descubrirlos y comprarlos para usarlos.
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 03/10/2019
ms.openlocfilehash: 02ce5146a154583d784de8030a0b0ec84740fcb3
ms.sourcegitcommit: 8fda7843a9f0e8193ced4a7a0e5c2dc5386059a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58175488"
---
# <a name="guidelines-for-power-bi-visuals"></a>Instrucciones para objetos visuales de Power BI

## <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Instrucciones para objetos visuales de Power BI con compras adicionales

Hasta hace poco, Marketplace (AppSource) solo aceptaba objetos visuales de Power BI que eran gratuitos. Esta directiva se ha modificado (diciembre de 2018) para que también se puedan enviar objetos visuales a AppSource con una etiqueta de precio "Es posible que se requiera una compra adicional". 

Los objetos visuales con la etiqueta “Es posible que se requiera una compra adicional” son similares a los complementos de compra desde la aplicación (IAP) de la Tienda Office. Los desarrolladores también pueden enviar estos objetos visuales para que se certifiquen después de que el equipo de AppSource los apruebe, así como después de asegurarse de que cumplen con los requisitos de certificación. Para obtener más información sobre los requisitos, consulte [Objetos visuales certificados](../power-bi-custom-visuals-certified.md).

> [!NOTE]
> Para que se certifique el objeto visual, no puede acceder a servicios o recursos externos.

>[!IMPORTANT]  
> Si actualiza el objeto visual de gratuito a "Es posible que se requiera una compra adicional", los usuarios deben recibir el mismo nivel de funcionalidad gratuita que antes de la actualización. Puede agregar características de pago avanzadas opcionales además de las características gratuitas existentes. Se recomienda enviar los objetos visuales de IAP con las características avanzadas como objetos visuales nuevos y no actualizar los objetos visuales gratuitos antiguos.


## <a name="what-changed-in-the-submission-process"></a>¿Qué ha cambiado en el proceso de envío?

Los desarrolladores cargan sus objetos visuales de IAP en AppSource mediante el panel de vendedores, tal y como han estado realizando con los objetos visuales gratuitos. Para indicar que el objeto visual enviado tiene características de IAP, los desarrolladores deben escribir “Objeto visual con compra desde la aplicación” en las notas del panel de vendedores. Además, los desarrolladores tienen que proporcionar un token o una clave de licencia para que el equipo de validación pueda validar las características de IAP. Una vez que el objeto visual se valide y apruebe, en la lista de AppSource de los estados de los objetos visuales de IAP se indica “Es posible que se requiera una compra adicional” en las opciones de los precios.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>¿Qué es un objeto visual de Power BI con características de IAP?

Un objeto visual de IAP es un objeto visual **gratuito** que ofrece **características gratuitas**. También tiene algunas características avanzadas para las que pueden aplicarse cargos adicionales que las activen. En la descripción del objeto visual, los desarrolladores deben indicar a los usuarios qué características requieren compras adicionales para que funcionen. Actualmente, Microsoft no proporciona API nativas que admitan comprar aplicaciones y complementos.

Los desarrolladores pueden usar cualquier sistema de pago de terceros para estas compras. Para obtener más información, consulte [nuestra directiva de almacenamiento](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads).

> [!NOTE]
> Las marcas de agua no se permiten en las características gratuitas ni los objetos visuales gratuitos. Las marcas de agua solo pueden usarse en las características de pago que se usan sin una licencia válida. Se recomienda mostrar una ventana emergente con toda la información relacionada con la licencia si se usan las características de pago avanzadas sin una licencia válida.  

## <a name="logo-guidelines"></a>Instrucciones para los logotipos

En esta sección se describen las especificaciones para agregar logotipos en objetos visuales.

> [!IMPORTANT]
> Los logotipos se permiten **solo en el modo de edición**. Los logotipos **no** se pueden mostrar en el modo de visualización.

![Definiciones](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![Cosas a tener en cuenta](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![Cosas que hay que evitar](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![Tamaño y formato](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![Márgenes y tamaño](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![Modo de edición](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Procedimientos recomendados

### <a name="visual-landing-page"></a>Página de aterrizaje del objeto visual

Use la página de aterrizaje para aclarar a los usuarios cómo pueden utilizar el objeto visual y dónde deben comprar la licencia. No incluya vídeos que se reproduzcan de forma automática. Agregue solo material que ayude a mejorar la experiencia del usuario, por ejemplo, información o vínculos a los detalles de la compra y cómo usar las características de IAP.

### <a name="license-key-and-token"></a>Token y clave de licencia

Para mayor comodidad del usuario, agregue campos relacionados con el token o la clave de licencia en la parte superior del panel de formato.

## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES

Para obtener más información sobre los objetos visuales, consulte las [preguntas más frecuentes sobre objetos visuales con compras adicionales](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Pasos siguientes

Aprenda a publicar objetos visuales personalizados en [AppSource](office-store.md) para que otros usuarios puedan descubrirlos y usarlos.
