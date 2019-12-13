---
title: Informes paginados en el servicio Power BI
description: Documentación en la que se describen los informes paginados y cómo visualizarlos en el servicio Power BI
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: a66189707bc6b688be012eeb59881ce4a8517ea1
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830467"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Informes paginados en el servicio Power BI
Ha aprendido sobre los [informes de Power BI](end-user-reports.md), que son los tipos de informes que es más probable que encuentre. Pero hay otro tipo de informes llamados *informes paginados*. Los diseñadores de *informes* pueden compartir los informes paginados en un área de trabajo de una capacidad Premium o en una aplicación de esa área de trabajo. 

## <a name="what-is-a-paginated-report"></a>¿Qué es un informe paginado?

Estos informes se llaman *paginados* porque tienen el formato adecuado para caber en una página impresa. Una de las ventajas es que muestran todos los datos en una tabla, incluso si esta abarca varias páginas. Los informes paginados a veces se denominan de "píxel perfecto", porque los *diseñadores* de informes pueden controlar con exactitud el diseño de página del informe.

Cuando los diseñadores de *informes* crean un informe paginado, lo que en realidad crean es una *definición de informe*. No contiene los datos. Especifica de dónde se obtienen los datos, qué datos se obtienen y cómo mostrar los datos. Al ejecutar el informe, el procesador de informes toma la definición de informe, recupera los datos y los combina con el diseño del informe para generar el informe. A veces, el informe muestra datos predeterminados. Otras veces es necesario especificar parámetros antes de que el informe pueda mostrar los datos. 

   ![Parámetros del informe](./media/end-user-paginated-report/power-bi-report-parameters.png)

Y este suele ser el alcance de la interacción: establecer los parámetros. Si es un analista de facturación, puede usar los informes paginados para crear o imprimir facturas. Si es un jefe de ventas, puede usarlos para ver los pedidos por tienda o vendedor. 

Este informe paginado simple genera beneficios por año después de seleccionar el parámetro **Año**. 

![Informe de parámetro simple](./media/end-user-paginated-report/power-bi-report-simple.png)

Comparado con los informes paginados, los informes de Power BI son mucho más interactivos. Los informes de Power BI permiten las notificaciones ad hoc y admiten muchos más tipos de objetos visuales, como los objetos visuales personalizados.

## <a name="identify-a-paginated-report"></a>Identificar un informe paginado

En las listas de contenido y en la página de llegada Inicio, los informes paginados se pueden identificar por el icono ![icono de informe paginado](media/end-user-paginated-report/power-bi-report-icon.png).  Un informe paginado se puede compartir con el usuario directamente o como parte de una [aplicación de Power BI](end-user-apps.md). Si el diseñador de *informes* le ha dado permisos, podrá volver a compartir el informe paginado y suscribirse usted mismo y suscribir a otros usuarios.

![lista de informes en la que se muestran distintos iconos](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>Interactuar con un informe paginado

La forma de interactuar con un informe paginado es diferente de la de otros informes. Puede hacer cosas como imprimir, marcar, exportar y comentar, pero hay menos interactividad. A menudo, los informes paginados requieren la intervención del usuario para rellenar el lienzo del informe.  En otras ocasiones, el informe muestra datos predeterminados y puede especificar parámetros para ver otros datos.

### <a name="print-a-paginated-report"></a>Imprimir un informe paginado

Los informes *paginados* tienen el formato adecuado para caber en una página y para imprimirse correctamente. Lo que ve en el explorador es lo que verá al imprimirlos. Además, si el informe tiene una tabla grande, se imprimirá toda la tabla, aunque abarque varias páginas. 

Los informes paginados pueden tener muchas páginas. Por ejemplo, este informe tiene 563 páginas. Cada una de ellas está diseñada con precisión, con una página por factura y encabezados y pies de página que se repiten. Al imprimir este informe, verá saltos de página entre las facturas.

   ![Primera página de un informe paginado de Tailspin Toys](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Navegar por el informe paginado

En este informe de pedidos de ventas hay tres parámetros: Tipo de negocio, Distribuidor y Número de pedido. 

![informe con tres parámetros](./media/end-user-paginated-report/power-bi-parameter.png)

Para cambiar la información que se muestra, introduzca valores nuevos para los tres parámetros y seleccione **Ver informe**. Aquí hemos seleccionado **Specialty bike shop**, **Alpine Ski House** y el número de pedido **SO46085**. Al seleccionar **Ver informe**, se actualiza el lienzo del informe con este nuevo pedido de ventas.

![cambiar los parámetros](./media/end-user-paginated-report/power-bi-order.png)

Se muestra el nuevo pedido de ventas con los parámetros que hemos seleccionado. 

![un nuevo pedido de ventas](./media/end-user-paginated-report/power-bi-new-order.png)

Algunos informes paginados tienen muchas páginas.  Use los controles de página para navegar por el informe. 

![controles de página](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>Exportar el informe paginado
Dispone de una serie de opciones para exportar los informes paginados: PDF, Word, XML, PowerPoint, Excel, etc. Al exportarlos se conserva todo el formato posible. Los informes paginados exportados a Excel, Word, PowerPoint, MHTML y PDF, por ejemplo, conservan el formato de "píxel perfecto". 

![un nuevo pedido de ventas](./media/end-user-paginated-report/power-bi-exporting.png)

![cuatro tipos de exportación diferentes](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Suscribirse al informe paginado
Al suscribirse a un informe paginado, Power BI le enviará un correo electrónico con el informe como adjunto. En la configuración de la suscripción, elija la frecuencia con la que quiere recibir los correos electrónicos: diaria, semanal, mensual o cada hora. La suscripción contiene un archivo adjunto con la salida completa del informe, de hasta 25 MB. Exporte todo el informe o seleccione los parámetros con antelación. Elija uno de los numerosos tipos de datos adjuntos diferentes: Excel, PDF, PowerPoint, etc.  

![Formatos para la suscripción](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

- Un informe paginado puede aparecer en blanco hasta que seleccione parámetros y seleccione **Ver informe**.

- Si no tiene ningún informe paginado, podría ser porque nadie ha compartido con usted este tipo de informe. También podría ser porque el administrador del sistema no le ha habilitado los informes paginados. 

 

## <a name="next-steps"></a>Pasos siguientes
- [Informes de Power BI](end-user-reports.md)
- ¿Tiene más preguntas? Consulte la [Comunidad de Power BI](https://community.powerbi.com/).

