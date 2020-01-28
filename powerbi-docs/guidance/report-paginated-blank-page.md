---
title: Eliminación de páginas en blanco al imprimir informes paginados
description: Instrucciones para el diseño de informes paginados a fin de evitar las páginas en blanco durante su impresión.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 76d1631b95c30d5ae56ced5d64e5174f6f9db759
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76041874"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Eliminación de páginas en blanco al imprimir informes paginados

Este artículo está dirigido a usted como autor de informes que diseña [informes paginados](../paginated-reports-report-builder-power-bi.md) de Power BI. Proporciona recomendaciones para ayudarle a evitar las páginas en blanco al exportarse su informe a un formato de página en disco, como PDF o Microsoft Word, o imprimirse.

## <a name="page-setup"></a>Configurar página

Las propiedades de tamaño de página del informe determinan la orientación, las dimensiones y los márgenes de la página. Obtenga acceso a estas propiedades de informe de las siguientes maneras:

- Usando el informe **Página de propiedades**: haga clic con el botón derecho en el área gris oscuro fuera del lienzo del informe y, a continuación, seleccione _Propiedades de informe_.
- Usando el panel [**Propiedades**](../paginated-reports-report-design-view.md#4-properties-pane): haga clic en el área gris oscuro fuera del lienzo del informe para seleccionar el objeto de informe. Asegúrese de que el panel **Propiedades** está abierto.

La página **Configurar página** del informe **Página de propiedades** proporciona una interfaz descriptiva para ver y actualizar las propiedades de configuración de página.

![En la imagen se muestra la ventana Propiedades de informe, resaltando la página Configurar página.](media/report-paginated-blank-page/report-page-setup-properties.png)

Asegúrese de que todas las propiedades de tamaño de página están correctamente configuradas:

|Propiedad|Recomendación|
|---------|---------|
|Unidades de página|Seleccione las unidades pertinentes (pulgadas o centímetros).|
|Orientación|Seleccione la opción correcta (vertical u horizontal).|
|Tamaño de papel|Seleccione un tamaño de papel o asigne valores de ancho y alto personalizados.|
|Margins|Establezca los valores adecuados para los márgenes izquierdo, derecho, superior e inferior.|
|||

## <a name="report-body-width"></a>Ancho del cuerpo del informe

Las propiedades de tamaño de página determinan el espacio disponible para los objetos del informe. Los objetos del informe pueden ser regiones de datos, visualizaciones de datos u otros elementos de informe.

Un motivo habitual por el que se generan páginas en blanco es que el ancho del cuerpo del informe _supera el espacio de página disponible_.

Solo puede ver y establecer el ancho del cuerpo del informe mediante el panel **Propiedades**. En primer lugar, haga clic en cualquier parte de un área vacía del cuerpo del informe.

![En la imagen se muestra el panel Propiedades, resaltando la propiedad Ancho del cuerpo del informe.](media/report-paginated-blank-page/report-body-properties-width.png)

Asegúrese de que el valor de ancho no supera el ancho de página disponible. Déjese guiar por la siguiente fórmula:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> No es posible reducir el ancho del cuerpo del informe cuando ya hay objetos de informe en el espacio que desea quitar. Primero debe cambiar su posición o tamaño antes de reducir el ancho.
>
> Además, el ancho del cuerpo del informe puede aumentar de forma automática al agregar nuevos objetos o cambiar el tamaño o la posición de los objetos existentes. El diseñador de informes siempre amplía el cuerpo para adaptarlo a la posición y el tamaño de sus objetos contenidos.

## <a name="report-body-height"></a>Alto del cuerpo del informe

Otro motivo por el que se genera una página en blanco es que hay un exceso de espacio en el cuerpo del informe, después del último objeto.

Le recomendamos que reduzca siempre el alto del cuerpo para quitar los espacios finales.

![En la imagen se muestra un diseño de informe. El espacio que hay debajo de la región de datos Tablix se resalta y se marca como innecesario.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Opciones de salto de página

Cada región y visualización de datos tiene opciones de salto de página. Puede obtener acceso a estas opciones en su página de propiedades, o bien en el panel **Propiedades**.

Asegúrese de que la propiedad **Agregar un salto de página después** no está habilitada innecesariamente.

![En la imagen se muestra una ventana de propiedades de Tablix. La propiedad "Agregar un salto de página después" está habilitada.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Consumir el espacio en blanco del contenedor

Si el problema de la página en blanco persiste, también puede intentar deshabilitar la propiedad **ConsumeContainerWhitespace** del informe. Solo puede establecerse en el panel **Propiedades**.

![En la imagen se muestra el panel Propiedades, resaltando la propiedad ConsumeContainerWhitespace.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

De forma predeterminada, está habilitada. Indica si debe consumirse el espacio en blanco mínimo de los contenedores, como el cuerpo del informe o un rectángulo. Solo se ve afectado el espacio en blanco a la derecha y debajo del contenido.

## <a name="printer-paper-size"></a>Tamaño del papel de la impresora

Por último, si imprime el informe en papel, asegúrese de que la impresora tiene el papel correcto cargado. El tamaño del papel físico debe corresponder al [tamaño del papel del informe](#page-setup).

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [¿Qué son los informes paginados en Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- [Paginación en informes paginados de Power BI](../paginated-reports-pagination.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com)
