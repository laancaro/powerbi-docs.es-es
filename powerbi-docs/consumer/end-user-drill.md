---
title: Explorar en profundidad y resumir en un objeto visual
description: En este artículo se muestra cómo explorar en profundidad en un objeto visual en el servicio Microsoft Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b200ec86db339e42a708c3db042df06b9513cc6e
ms.sourcegitcommit: f34acbf9fb1ab568fd89773aaf412a847f88dd34
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589509"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Modo de exploración en un objeto visual de Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

En este artículo se muestra cómo explorar en profundidad en un objeto visual en el servicio Microsoft Power BI. El uso del rastreo agrupando y desagrupando puntos de datos le permite explorar en profundidad sus detalles. 

## <a name="drill-requires-a-hierarchy"></a>El modo detallado necesita una jerarquía

Cuando un objeto visual tiene una jerarquía, se puede explorar en profundidad para mostrar detalles adicionales. Por ejemplo, es posible que tenga un objeto visual que examine el número de medallas olímpicas mediante una jerarquía formada por deporte, disciplina y evento. De forma predeterminada, en el objeto visual se muestra el número de medallas por deporte, como gimnasia, esquí, deportes acuáticos, etc. Pero, como tiene una jerarquía, al seleccionar uno de los elementos visuales (como una barra, línea o burbuja) se mostraría una imagen cada vez más detallada. Al seleccionar el elemento **aquatics** se mostrarían los datos de natación, buceo y waterpolo.  Al seleccionar el elemento **diving** se mostrarían los detalles de los eventos de trampolín, plataforma y salto sincronizado.

Las fechas son un tipo único de jerarquía.  A menudo, los diseñadores de informes agregan jerarquías de fecha a los objetos visuales. Una jerarquía de fecha común es la que contiene el año, el trimestre, el mes y el día. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Averiguar qué objetos visuales se pueden explorar
¿No está seguro de qué objetos visuales de Power BI contienen una jerarquía? Mantenga el cursor sobre un objeto visual. Si ve una combinación de estos controles de detalle en la parte superior, el control visual tiene una jerarquía.

![Captura de pantalla de los iconos de exploración.](./media/end-user-drill/power-bi-drill-icons.png)  

## <a name="learn-how-to-drill-down-and-up"></a>Más información sobre cómo explorar en profundidad y resumir

En este ejemplo, se usará un gráfico de rectángulos que tiene una jerarquía formada por territorio, ciudad, código postal y nombre de la tienda. El gráfico de rectángulos, antes de la exploración, examina las unidades totales vendidas este año por territorio. 

![Captura de pantalla del gráfico de rectángulos y sus filtros.](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>Dos maneras de acceder a las características de exploración

Tiene dos maneras de acceder a las características de exploración en profundidad, resumen y expansión para los objetos visuales que tienen jerarquías. Pruébelas y use la que más le guste.

- Primera: mantenga el mouse sobre un objeto visual para ver y usar los iconos.  

    ![Captura de pantalla del ejemplo al mantener el puntero.](./media/end-user-drill/power-bi-hover.png)

- Segunda: haga clic con el botón derecho en un objeto visual para mostrar el menú y usarlo.

    ![Captura de pantalla del ejemplo al hacer clic con el botón derecho.](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>Rutas de exploración

### <a name="drill-down-all-fields-at-once"></a>Rastreo desagrupando datos de todos los campos a la vez
![El icono de exploración en profundidad](./media/end-user-drill/power-bi-drill-icon3.png)

Existen varias formas de explorar el objeto visual. Al seleccionar el icono de explorar en profundidad accede al nivel siguiente en la jerarquía. Si va a examinar el nivel **Territory** (Territorio) para Kentucky y Tennessee, puede explorar en profundidad hasta el nivel de ciudad de los dos estados, después el nivel de código postal y, por último, el nivel de nombre de la tienda de los dos estados. Cada paso de la ruta muestra información nueva.

![Diagrama que muestra la ruta de exploración](./media/end-user-drill/power-bi-drill-path.png)

Seleccione el icono de exploración ![Icono de exploración](./media/end-user-drill/power-bi-drill-icon5.png) hasta que retroceda a "Unidades totales de este año por territorio".

### <a name="expand-all-fields-at-once"></a>Expandir todos los campos a la vez
![El icono Expandir](./media/end-user-drill/power-bi-drill-icon6.png)

**Expandir** agrega un nivel de jerarquía adicional a la vista actual. Por tanto, si está mirando el nivel **Territory** (Territorio), puede expandir y agregar City (Ciudad), Postal Code (Código postal) y Name (Nombre) al gráfico de rectángulos. Cada paso de la ruta muestra la misma información y agrega un nivel de información nueva.

![Diagrama que muestra la ruta de expansión](./media/end-user-drill/power-bi-expand-path.png)

También puede elegir si quiere explorar en profundidad o expandir solo un campo a la vez.


### <a name="drill-down-one-field-at-a-time"></a>Rastrear desagrupando datos un solo campo a la vez


1. Seleccione el icono de explorar en profundidad para activarlo ![Captura de pantalla del icono para activar/desactivar la opción de rastrear desagrupando datos en modo activado.](./media/end-user-drill/power-bi-drill-icon2.png).

    Ahora tiene la opción de explorar en profundidad **un solo campo a la vez** si selecciona un elemento visual. Barras, burbujas y hojas son ejemplos de elementos visuales.

    ![Captura de pantalla del objeto visual con flecha que apunta al icono de activación o desactivación de explorar en profundidad en modo activado.](media/end-user-drill/power-bi-drill-icon-selected.png)

    Si no activa la opción de explorar en profundidad, la selección de un elemento visual (como una barra, burbuja u hoja) no explorará en profundidad, sino que aplicará un filtro cruzado a los otros gráficos de la página del informe.

1. Seleccione el nodo hoja para **TN**. Ahora en el gráfico de rectángulos se muestran todos los territorios de Tennessee que tienen una tienda.

    ![Captura de pantalla del gráfico de rectángulos que muestra datos solo de TN.](media/end-user-drill/power-bi-drill-down-one.png)

1. En este momento, puede hacer lo siguiente:

    1. Seguir profundizando para Tennessee.

    1. Explorar en profundidad para una ciudad determinada de Tennessee.

    1. Expanda en su lugar.

    Sigamos rastreando desagrupando datos de un solo campo a la vez.  Seleccione **Knoxville, TN**. El gráfico de rectángulos muestra ahora el código postal de la tienda en Knoxville.

    ![Captura de pantalla del gráfico de rectángulos que muestra datos solo del código postal 37919.](media/end-user-drill/power-bi-drill-two.png)

    Observe que el título cambia a medida que realiza la exploración en profundidad y vuelve a agruparlos de nuevo.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandir todo y expandir un campo a la vez

Tener un gráfico de rectángulos que nos muestra solo un código postal no es muy informativo.  A continuación se *expandirá* un nivel en la jerarquía.  

1. Con el gráfico de rectángulos activo, seleccione el icono de *expandir* ![Captura de pantalla del icono de expandir](./media/end-user-drill/power-bi-drill-icon6.png). El gráfico de rectángulos muestra ahora dos niveles de la jerarquía: código postal y nombre de la tienda.

    ![Captura de pantalla del gráfico de rectángulos que muestra el código postal y el nombre de la tienda](./media/end-user-drill/power-bi-expand-one.png)

1. Para ver los cuatro niveles de jerarquía de datos para Tennessee, haga clic en la flecha arriba de exploración hasta llegar al segundo nivel **Total units this year by territory and city** (Unidades totales este año por territorio y ciudad) del gráfico de rectángulos.

    ![Captura de pantalla del gráfico de rectángulos que muestra todos los datos de TN.](media/end-user-drill/power-bi-expand-two.png)

1. Asegúrese de que el rastreo desagrupando datos sigue activado, ![Captura de pantalla del icono para activar/desactivar la opción de rastrear desagrupando datos en modo activado.](./media/end-user-drill/power-bi-drill-icon2.png) y seleccione el icono de *expandir* ![Captura de pantalla del icono de expandir](./media/end-user-drill/power-bi-drill-icon6.png). Ahora, en el gráfico de rectángulos se muestra el mismo número de hojas (cuadros), pero cada hoja tiene detalles adicionales. En lugar de mostrar solo la ciudad y el estado, también muestra el código postal.

    ![Captura de pantalla del gráfico visual que muestra la ciudad, el estado y el código postal.](./media/end-user-drill/power-bi-expand-three.png)

1. Haga clic en el icono de *expandir* una vez más para mostrar los cuatro niveles de jerarquía de detalle para Tennessee en el gráfico de rectángulos. Mantenga el mouse sobre un nodo hoja para ver más detalles.

    ![Captura de pantalla del gráfico de rectángulos que muestra información sobre herramientas con datos específicos de la hoja.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>Mostrar los datos a medida que se explora
Use **Permite mostrar datos** para obtener un visión en segundo plano. Cada vez que explore en profundidad o expanda, **Permite mostrar datos** muestra los datos que se usan para crear el objeto visual. Esto puede ayudarle a entender el funcionamiento conjunto de las jerarquías, explorar en profundidad y expandir para crear objetos visuales. 

En la esquina superior derecha, seleccione los puntos suspensivos (...) y, después, **Permite mostrar datos**. 

![Captura de pantalla del menú de puntos suspensivos.](./media/end-user-drill/power-bi-ellipses.png)

En la tabla siguiente se muestran los resultados de explorar en profundidad todos los campos a la vez desde territorio hasta nombre de la tienda.  


![Captura de pantalla en la que se muestran datos de los cuatro niveles de exploración en profundidad.](./media/end-user-drill/power-bi-show-data.png)

Observe que los totales son los mismos para **City** (Ciudad), **PostalCode** (Código postal) y **Name** (Nombre). Esto no siempre será así.  Pero para estos datos, solo hay una tienda en cada código postal y en cada ciudad.  



## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones
De forma predeterminada, el modo detallado no filtrará otros objetos visuales en un informe. Pero el diseñador del informe puede cambiar este comportamiento predeterminado. A medida que explore en profundidad, compruebe si los demás objetos visuales de la página realizan filtrado cruzado o resaltado cruzado.


## <a name="next-steps"></a>Pasos siguientes

[Objetos visuales en informes de Power BI](../visuals/power-bi-report-visualizations.md)

[Informes de Power BI](end-user-reports.md)

[Power BI: Conceptos básicos](end-user-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
