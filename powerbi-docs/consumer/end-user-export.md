---
title: Exportar datos desde un objeto visual de Power BI
description: Exportar datos de un objeto visual de informe y panel visual y verlo en Excel.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 4/9/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: d4384db8e05a69b138e76377e7c7b845867fa881
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "61063854"
---
# <a name="export-data-from-visual"></a>Exportar datos de visual
Si desea ver los datos que se usan para crear un objeto visual, [puede mostrar dichos datos en Power BI](end-user-show-data.md) o exportarlos a Excel. La opción para exportar los datos requiere un tipo determinado o la licencia y editar los permisos para el contenido. Si no se puede exportar, póngase en contacto con el Administrador de Power BI. 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Desde un objeto visual en un panel de Power BI

1. Iniciar en el panel de Power BI. Vamos a usar el panel desde el ***ejemplo de Marketing y venta*** app. También puede [descargar esta aplicación desde AppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282).

    ![](media/end-user-export/power-bi-dashboard.png)

2. Mantenga el mouse sobre un objeto visual para mostrar el botón de puntos suspensivos (...) y haga clic para mostrar el menú Acción.

    ![](media/end-user-export/power-bi-dashboard-export-visual.png)

3. Seleccione **exportar a Excel**.

4. Lo que sucede después depende de qué explorador esté utilizando. Se le pedirá que guarde el archivo o puede ver un vínculo al archivo exportado en la parte inferior del explorador. 

    ![](media/end-user-export/power-bi-export-browser.png)

5. Abra el archivo en Excel.  

    ![](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>Desde un objeto visual en un informe
Puede exportar datos desde un objeto visual en un informe como .xlsx (Excel) o archivo .csv formato. 

1. En un panel, seleccione un icono para abrir el informe subyacente.  En este ejemplo, seleccionamos el mismo objeto visual anterior, *% de desviación de Total de unidades de YTD*. 

    ![](media/end-user-export/power-bi-export-report.png)

    Puesto que este icono se creó desde el *ejemplo de Marketing y ventas* informes, que es el informe que se abre. Y, se abrirá la página que contiene el objeto visual de icono seleccionado. 

2. Seleccione el icono en el informe. Tenga en cuenta la **filtros** panel a la derecha. Este objeto visual tiene filtros aplicados. Para más información acerca de los filtros, consulte [utilizar filtros en un informe](end-user-report-filter.md).

    ![](media/end-user-export/power-bi-export-filters.png)


3. Seleccione los puntos suspensivos en la esquina superior derecha de la visualización. Elija **exportar datos**.

    ![](media/end-user-export/power-bi-export-report2.png)

4. Verá las opciones para exportar datos de resumen o de datos subyacente. Si usas el *ejemplo de marketing y ventas* app, **datos subyacentes** estará deshabilitada. Pero puede encontrar informes donde ambas opciones están habilitadas. Esta es una explicación de la diferencia.

    **Datos resumidos**: seleccione esta opción si desea exportar los datos para lo que ve en el objeto visual.  Este tipo de exportación muestra solo los datos que se usan para crear el objeto visual. Si el objeto visual tiene filtros aplicados, también se filtrarán los datos que exporta. Por ejemplo, para este objeto visual, la exportación incluirá solo datos de 2014 y la región central y solamente los datos de cuatro de los fabricantes: VanArsdel, Natura, Aliqui y Prirum.
  

    **Los datos subyacentes**: seleccione esta opción si desea exportar los datos para lo que ve en el objeto visual **plus** datos adicionales del conjunto de datos subyacente.  Esto puede incluir los datos contenidos en el conjunto de datos, pero no se utiliza en el objeto visual. 

    ![](media/end-user-export/power-bi-export-report3.png)

5. Lo que sucede después depende de qué explorador esté utilizando. Se le pedirá que guarde el archivo o puede ver un vínculo al archivo exportado en la parte inferior del explorador. 

    ![](media/end-user-export/power-bi-export-edge.png)


7. Abra el archivo en Excel. Comparar la cantidad de datos exportados a los datos que se exportan desde el mismo objeto visual en el panel. La diferencia es que esta exportación incluye **datos subyacentes**. 

    ![](media/end-user-export/power-bi-underlying.png)

