---
title: Instrucciones para objetos visuales de Power BI
description: Obtenga más información sobre cómo publicar objetos visuales personalizados en Microsoft AppSource para que otros usuarios puedan descubrirlos y comprarlos para usarlos.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 07/16/2019
ms.openlocfilehash: 6bf7610a010a72248a3d2fdd96718eea513a68da
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000098"
---
# <a name="guidelines-for-power-bi-visuals"></a>Instrucciones para objetos visuales de Power BI
Antes de [publicar](https://docs.microsoft.com/power-bi/developer/office-store) el objeto visual de Power BI en Microsoft AppSource para que otros usuarios lo descubran y lo usen, asegúrese de seguir las instrucciones para crear una gran experiencia para los usuarios.

## <a name="power-bi-visuals-with-additional-purchases"></a>Objetos visuales de Power BI con compras adicionales

Puede enviar objetos visuales de Power BI que sean gratuitos a Marketplace (Microsoft AppSource). También puede enviar objetos visuales de Power BI a Microsoft AppSource con una etiqueta de precio "Es posible que se requiera una compra adicional". Los objetos visuales de Power BI con la etiqueta "Es posible que se requiera una compra adicional" son similares a los complementos de compra desde la aplicación (IAP) de la Tienda Office. 

Al igual que un objeto visual de Power BI gratuito, un objeto visual de Power BI de IAP también se puede certificar. Antes de enviar el objeto visual de Power BI de IAP para la certificación, asegúrese de que cumple los [requisitos de certificación](../power-bi-custom-visuals-certified.md). 

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>¿Qué es un objeto visual de Power BI con características de IAP?

Un objeto visual de Power BI de IAP es un objeto visual *gratuito* que ofrece *características gratuitas*. También tiene algunas características avanzadas para las que se pueden aplicar cargos adicionales. En la descripción del objeto visual de Power BI, los desarrolladores deben indicar a los usuarios qué características requieren compras adicionales para que funcionen. Actualmente, Microsoft no proporciona API nativas que admitan comprar aplicaciones y complementos.

Los desarrolladores pueden usar cualquier sistema de pago de terceros para estas compras. Para obtener más información, consulte [nuestra directiva de almacenamiento](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads).


>[!IMPORTANT]  
> Si actualiza el objeto visual de Power BI de gratuito a "Es posible que se requiera una compra adicional", los usuarios deben recibir el mismo nivel de funcionalidad gratuita que antes de la actualización. Puede agregar características de pago avanzadas opcionales además de las características gratuitas existentes.

### <a name="watermarks"></a>Marcas de agua

Puede utilizar marcas de agua para que los clientes sigan usando las características avanzadas de IAP sin pagar. 

Las marcas de agua se pueden usar para mostrar toda la funcionalidad del objeto visual de Power BI, antes de que se realice una compra. 

* Las marcas de agua solo pueden usarse en las características de pago que se usan sin una licencia válida.
* No se permiten marcas de agua en objetos visuales de Power BI con una etiqueta de precio *gratis*.
* No se permiten marcas de agua en los objetos visuales de IAP cuando el usuario usa las características gratuitas. 

### <a name="pop-up-window"></a>Ventana emergente

Puede usar una ventana emergente para explicar cómo comprar una licencia, al usar una licencia no válida (o expirada) con el objeto visual de Power BI de IAP.

### <a name="submission-process"></a>Proceso de envío

Siga el [proceso de envío](office-store.md#submitting-to-appsource) y, luego, vaya a la pestaña *Configuración del producto* y active la casilla *Mi producto necesita la compra de un servicio*.

Una vez que el objeto visual de Power BI se valide y apruebe, en la lista de Microsoft AppSource de los estados de los objetos visuales de Power BI de IAP se indica "Es posible que se requiera una compra adicional" en las opciones de precio.

>[!NOTE]
>Si el objeto visual de Power BI ya se envió mediante el [Panel de vendedores](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) y quiere agregar una característica de IAP, tiene que escribir en las notas del Panel de vendedores "Objeto visual con compra desde la aplicación". También tiene que proporcionar un token o una clave de licencia para que el equipo de validación pueda validar las características de IAP.

## <a name="context-menu"></a>Menú contextual
El menú contextual es el que se muestra cuando el usuario mantiene el mouse sobre un objeto visual.
En todos los objetos visuales de Power BI se debe habilitar el menú contextual para ofrecer una experiencia unificada. Consulte [este artículo](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md) para obtener información sobre cómo agregar un menú contextual.

## <a name="commercial-logo"></a>Logotipo comercial
En esta sección se describen las especificaciones para agregar logotipos comerciales en los objetos visuales de Power BI. Los logotipos comerciales no son obligatorios. Si se agregan, deben seguir estas instrucciones.

> [!NOTE]
> * En este artículo, la palabra "logotipo comercial" se refiere a todo icono de empresa comercial, como se describe en las imágenes siguientes.
> * En este artículo, el logotipo comercial de Microsoft solo se usa como ejemplo. Use su propio logotipo comercial con el objeto visual de Power BI.

> [!IMPORTANT]
> Los logotipos comerciales *solo se admiten en el modo de edición*. Los logotipos comerciales *no* se pueden mostrar en el modo de visualización.

### <a name="commercial-logo-type"></a>Tipo de logotipo comercial

Hay tres tipos de logotipos comerciales:
* **Logotipo**: un logotipo se compone de dos elementos indivisibles, que son un icono y un nombre.

    ![Logotipo de Microsoft](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **Símbolo**: un gráfico sin texto.

    ![Símbolo de Microsoft](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **Logotipo sencillo**: un logotipo sin icono, compuesto solamente de texto.

    ![Símbolo de Microsoft](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>Color del logotipo comercial

Cuando se usa un logotipo comercial, el color del logotipo debe ser gris (color hexadecimal #C8C8C8). No agregue efectos como degradados al logotipo comercial.

* **Logotipo**

    ![Símbolo de Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **Símbolo**: un gráfico sin texto.

    ![Símbolo de Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **Logotipo sencillo**: un logotipo sin icono, compuesto solamente de texto.

    ![Símbolo de Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * Si el objeto visual de Power BI contiene un gráfico, considere la posibilidad de agregar al logotipo un fondo blanco con márgenes de 10 px.
> * Se recomienda agregar una sombra paralela (de color negro con un 30 % de opacidad) al logotipo.

### <a name="commercial-logo-size"></a>Tamaño del logotipo comercial

Un objeto visual de Power BI requiere dos logotipos comerciales, uno para los iconos grandes y otro para los pequeños. Coloque el logotipo en un cuadro de límite situado en la esquina superior o inferior derecha, con márgenes de 4 px.

En la tabla siguiente se describen las consideraciones de tamaño para los objetos visuales de Power BI.

|  |Objeto visual de Power BI pequeño  |Objeto visual de Power BI grande  |
|---------|---------|---------|
|*Ancho del logotipo*    |Hasta 240 px         |Más de 240 px         |
|*Alto del logotipo*     |Hasta 160 px         |Más de 160 px         |
|*Tamaño del cuadro de límite*     |40 x 15 px         |101 x 30 px         |
|*Ejemplo de logotipo comercial*     |![Símbolo de Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Logotipo de Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*Ejemplo de cuadro de límite*    |![ejemplo de logotipo pequeño](media/guidelines-powerbi-visuals/small-logo-box.png)         |![ejemplo de logotipo grande](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>Comportamiento del logotipo comercial

Los logotipos comerciales solo se admiten en el modo de edición. Al hacer clic en ellos, un logotipo comercial solo puede incluir la funcionalidad siguiente:

* Al hacer clic en el logotipo comercial, se redirige al usuario al sitio web.

* Al hacer clic en el logotipo comercial, se abre una ventana emergente con información adicional. La ventana emergente se debe dividir en dos secciones:
    * Un área de marketing que puede incluir el logotipo comercial, un objeto visual y valoraciones de mercado.
    * Un área de información que puede incluir información y vínculos.    


### <a name="things-to-avoid"></a>Cosas que hay que evitar

* Los logotipos comerciales no se pueden mostrar en el modo de visualización.

* Un logotipo comercial animado puede mostrar la animación durante cinco segundos como máximo.

* Si el objeto visual de Power BI incluye iconos informativos (i) en modo de lectura, deben cumplir con el color, el tamaño y la ubicación del logotipo comercial, como se ha descrito antes.

* Evite utilizar un logotipo comercial multicolor o negro. El logotipo comercial debe ser gris (color hexadecimal #C8C8C8).

    ![Logotipo multicolor no autorizado](media/guidelines-powerbi-visuals/no-color-logo.png) ![Logotipo negro no autorizado](media/guidelines-powerbi-visuals/black-logo.png)

* Un logotipo comercial con efectos como degradados o sombras fuertes.

    ![Estilo de logotipo no autorizado](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>Procedimientos recomendados

Al publicar un objeto visual de Power BI, tenga en cuenta las recomendaciones siguientes para proporcionar a los usuarios una gran experiencia.

### <a name="visual-landing-page"></a>Página de aterrizaje del objeto visual

Use la página de aterrizaje para aclarar a los usuarios cómo pueden utilizar el objeto visual de Power BI y dónde deben comprar la licencia. No incluya vídeos que se reproduzcan de forma automática. Agregue solo material que ayude a mejorar la experiencia del usuario, por ejemplo, información o vínculos a los detalles de la compra y cómo usar las características de IAP.

### <a name="license-key-and-token"></a>Token y clave de licencia

Para mayor comodidad del usuario, agregue campos relacionados con el token o la clave de licencia en la parte superior del panel de formato.

## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES

Para obtener más información sobre los objetos visuales de Power BI, vea [Preguntas más frecuentes sobre objetos visuales de Power BI con compras adicionales](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre cómo publicar el objeto visual de Power BI en [Microsoft AppSource](office-store.md) para que otros usuarios lo puedan descubrir y comprar.