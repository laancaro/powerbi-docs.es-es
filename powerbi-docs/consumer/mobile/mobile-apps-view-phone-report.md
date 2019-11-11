---
title: Ver informes de Power BI optimizados para el teléfono
description: Lea sobre la interacción con páginas de informe que se optimizan para visualizarse en las aplicaciones de teléfono de Power BI.
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: mshenhav
ms.openlocfilehash: f8dba41a15390e4b52227c7daaa603daf7c08939
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870533"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Ver informes de Power BI optimizados para el teléfono

Se aplica a:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Teléfono Android](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone |Teléfonos Android |

Cuando se ve un informe de Power BI en el teléfono, Power BI comprueba si dicho informe se ha optimizado para teléfonos. Si es así, Power BI abre automáticamente el informe optimizado en vista vertical.

![Informe en modo vertical](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Si no existe un informe optimizado para teléfono, el informe se abrirá en la vista horizontal no optimizada. Incluso en un informe optimizado, si gira el teléfono hacia un lado, el informe se abre en una vista no optimizada con el diseño del informe original. Si solo se optimizan algunas páginas, verá un mensaje en vista vertical, que indica que el informe está disponible en horizontal.

![Página de informe no optimizada](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Las restantes características de los informes de Power BI funcionan en los informes optimizados para teléfono. Lea más acerca de lo que puede hacer en:

* [Informes sobre iPhone](mobile-reports-in-the-mobile-apps.md). 
* [Informes de teléfonos Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrado de la página del informe en un teléfono
Si un informe optimizado para el teléfono tiene filtros definidos, cuando vea el informe en un teléfono, podrá usar esos filtros. El informe se abre en el teléfono, filtrado por los valores que se filtran en el informe en Internet. Verá un mensaje que indica que hay filtros activos en la página. Puede cambiar los filtros en el teléfono.Puede cambiar los filtros en el teléfono.

1. Pulse el icono de filtro ![Icono de filtro en el teléfono](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) en la parte inferior de la página. 
2. Use el filtrado básico o avanzado para ver los resultados que le interesan.
   
    ![Filtro avanzado de informes de teléfono de Power BI](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Objetos visuales de resaltado cruzado
Los objetos visuales de resaltado cruzado en vista vertical funcionan igual que en el servicio Power BI y en los teléfonos en vista horizontal: al seleccionar los datos de un objeto visual, se resaltan los datos relacionados en los demás objetos visuales de la página.

Lea más sobre el [filtrado y resaltado en Power BI](../../power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Seleccionar objetos visuales
En los informes de teléfono cuando se selecciona un objeto visual, el informe de teléfono resalta ese objeto visual y se centra en él, lo que neutraliza los gestos del lienzo.

Con el objeto visual seleccionado, puede hacer tareas como desplazarse dentro del objeto visual. Para anular la selección de un objeto visual, solo tiene que tocar en cualquier lugar fuera del área visual.

## <a name="open-visuals-in-focus-mode"></a>Abrir objetos visuales en modo de enfoque
Los informes de teléfono también ofrecen un modo de enfoque: se obtiene una vista más amplia de un solo objeto visual y se explora con más facilidad.

* En un informe para móviles, pulse los puntos suspensivos ( **...** ) en la esquina superior derecha de un objeto visual > **Ampliar al modo enfocado**.
  
    ![Ampliar al modo enfocado](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Lo que se hace en el modo de enfoque se trasmite al lienzo del informe y viceversa. Por ejemplo, si resalta un valor en un objeto visual y después vuelve al informe completo, este se filtra por el valor resaltado en el objeto visual.

Algunas acciones solo son posibles en el modo de enfoque debido a restricciones de tamaño de pantalla:

* **Explorar en profundidad** la información que se muestra en un objeto visual. A continuación encontrará más información acerca de la [exploración en profundidad y el rastreo agrupando datos](mobile-apps-view-phone-report.md#drill-down-in-a-visual).
* **Ordene** los valores del objeto visual.
* **Revertir**: borre los pasos de exploración tomados en un objeto visual y revierta a la definición establecida cuando se creó el informe.
  
    Para borrar todas las exploraciones de un objeto visual, pulse los puntos suspensivos ( **...** ) > **Revert** (Revertir).
  
    ![Revertir](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Revertir está disponible en el nivel de informe, donde borra la exploración de todos los objetos visuales, o en el nivel de objeto visual, donde quita la exploración del objeto visual seleccionado.   

## <a name="drill-down-in-a-visual"></a>Exploración en profundidad en un objeto visual
Si los niveles de jerarquía se definen en un objeto visual, es posible profundizar en la información detallada que se muestran en dicho objeto y, después, realizar una copia de seguridad. Se puede [agregar una exploración en profundidad a un objeto visual](../end-user-drill.md) tanto en el servicio Power BI como en Power BI Desktop.

Hay pocos tipos de exploración en profundidad:

### <a name="drill-down-on-a-value"></a>Exploración en profundidad de un valor
1. Pulse durante un tiempo (pulse y mantenga) en un punto de datos de un objeto visual.
2. Aparece la información sobre herramientas y, si la jerarquía está definida, el pie de página de la información sobre herramientas muestra la flecha hacia abajo y hacia arriba para explorar en profundidad.
3. Pulse en la flecha hacia abajo para explorar en profundidad

    ![Pulsado en Explorar en profundidad](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Pulse en la flecha hacia arriba para resumir.

### <a name="drill-to-next-level"></a>Exploración al nivel siguiente
1. En un informe de un móvil, pulse los puntos suspensivos ( **...** ) en la esquina superior derecha > **Ampliar al modo enfocado**.
   
    ![Ampliar al modo enfocado](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    En este ejemplo, las barras muestran los valores de los estados.
2. Pulse el icono de exploración ![Icono de exploración](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) en la parte inferior izquierda.
   
    ![Modo de exploración](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Pulse **Mostrar siguiente nivel** o **Expandir al nivel siguiente**.
   
    ![Expandir al nivel siguiente](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Ahora las barras muestran los valores de las ciudades.
   
    ![Niveles expandidos](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Si pulsa la flecha de la esquina superior izquierda, devuelve el informe para móviles con los valores expandidos en el nivel inferior.
   
    ![Expandido al nivel inferior](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Para volver al nivel original, puntee vuelve a pulsar los puntos suspensivos ( **...** ) > **Revert** (Revertir).
   
    ![Revertir](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Obtención de detalles de un valor
La obtención de detalles conecta valores de una página de informe con otras páginas de informe. Al obtener detalles de un punto de datos a otra página de informe, los valores del punto de datos se usan para filtrar la página cuyos detalles se han obtenido, o está en el contexto de los datos seleccionados.
Los autores de informes pueden [definir la obtención de detalles](https://docs.microsoft.com/power-bi/desktop-drillthrough) al crear el informe.

1. Pulse durante un tiempo (pulse y mantenga) en un punto de datos de un objeto visual.
2. Aparece la información sobre herramientas y, si la obtención de detalles está definida, el pie de página de la información sobre herramientas muestra la flecha de obtención de detalles.
3. Pulse en la flecha para obtener detalles

    ![Pulsado en Obtener detalles](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Seleccione la página de informe cuyos detalles se van a obtener

    ![Seleccionar página del informe](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Use el botón Atrás en el encabezado de la aplicación para volver a la página desde la que ha empezado.


## <a name="next-steps"></a>Pasos siguientes
* [Crear informes optimizados para las aplicaciones de teléfono de Power BI](../../desktop-create-phone-report.md)
* [Create a phone view of a dashboard in Power BI (Crear una vista de teléfono de un panel en Power BI)](../../service-create-dashboard-mobile-phone-view.md)
* [Crear objetos visuales con capacidad de respuesta optimizados para cualquier tamaño](../../visuals/desktop-create-responsive-visuals.md)
* ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

