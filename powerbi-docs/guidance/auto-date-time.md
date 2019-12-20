---
title: Guía sobre la fecha y hora automáticas en Power BI Desktop
description: Instrucciones para usar la funcionalidad de fecha y hora automáticas en Power BI Desktop.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 30bfacc1024035f0849440eec8b1c7051ff4d82a
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2019
ms.locfileid: "75002452"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Guía sobre la fecha y hora automáticas en Power BI Desktop

Este artículo se dirige a los modeladores de datos que desarrollan modelos compuestos o de importación en Power BI Desktop. Proporciona instrucciones, recomendaciones y consideraciones al usar la funcionalidad _Fecha y hora automáticas_ de Power BI Desktop en situaciones específicas. Para información general sobre la funcionalidad _Fecha y hora automáticas_, consulte [Fecha y hora automáticas en Power BI Desktop](../desktop-auto-date-time.md).

La opción _Fecha y hora automáticas_ ofrece inteligencia de tiempo cómoda, rápida y fácil de usar. Los autores de informes pueden trabajar con la inteligencia de tiempo al filtrar, agrupar y explorar los períodos de tiempo de calendario.

## <a name="considerations"></a>Consideraciones

En la lista con viñetas siguiente se describen las consideraciones (y posibles limitaciones) relacionadas con la opción _Fecha y hora automáticas_.

- **Se aplica a todos o a ninguno:** cuando la opción _Fecha y hora automáticas_ está habilitada, se aplica a todas las columnas de fechas en las tablas de importación que no son el lado &quot;varios&quot; de una relación. No se puede habilitar ni deshabilitar de manera selectiva columna por columna.
- **Solo períodos de calendario:** las columnas de año y trimestre se relacionan con los períodos de calendario. Significa que el año empieza el 1 de enero y finaliza el 31 de diciembre. No es posible personalizar la fecha de inicio (o finalización) del año.
- **Personalización:** no es posible personalizar los valores que se usan para describir los períodos de tiempo. Además, no es posible agregar otras columnas para describir otros períodos de tiempo, por ejemplo, semanas.
- **Filtrado de año:** los valores de la columnas **Quarter**, **Month** y **Day** no incluyen el valor de año. Por ejemplo, la columna **Month** contiene solo los nombres de los meses (es decir, enero, febrero, etc.). Los valores no son totalmente autodescriptivos y es posible que, en algunos diseños de informes, no comuniquen el contexto de filtro de año.

    Esta es la razón por la que es importante que los filtros o agrupaciones se lleven a cabo en la columna **Year**. Al explorar en profundidad mediante la jerarquía, se filtrará el año, a menos que el nivel **Year** se quite de manera intencional. Si no hay ningún filtro o grupo por año, una agrupación por mes, por ejemplo, resumiría los valores de todos los años correspondientes a ese mes.
- **Filtrado de fecha de una sola tabla:** como cada columna de fecha genera su propia tabla de fecha y hora automáticas (oculta), no es posible aplicar un filtro de tiempo a una tabla y hacer que lo propague a varias tablas de modelo. Filtrar de esta manera es un requisito de modelado común cuando se notifican varios asuntos (tablas de tipo de hechos), como las ventas y el presupuesto de ventas. Al usar la fecha y hora automáticas, el autor de informe deberá aplicar filtros a cada columna de fecha distinta.
- **Tamaño del modelo:** para cada columna de fecha que genera una tabla de fecha y hora automáticas oculta, generará un tamaño de modelo mayor y también ampliará la hora de actualización de los datos.

## <a name="recommendations"></a>Recomendaciones

Se recomienda mantener habilitada la opción _Fecha y hora automáticas_ solo al trabajar con períodos de tiempo de calendario y cuando tenga requisitos de modelo simplistas con respecto al tiempo. Usar esta opción también puede ser útil cuando se crean modelos ad hoc o se realiza la generación de perfiles o la exploración de datos.

Cuando el origen de datos ya define una tabla de dimensión de fecha, esta tabla se debe usar para definir de manera coherente la hora dentro de la organización. Seguramente será el caso si el origen de datos es un almacenamiento de datos. De lo contrario, puede generar tablas de fechas en el modelo si usa las funciones [CALENDAR](/dax/calendar-function-dax) o [CALENDARAUTO](/dax/calendarauto-function-dax) de DAX. Luego puede agregar columnas calculadas para admitir los requisitos conocidos de agrupación y filtrado de tiempo. Este enfoque de diseño puede permitirle crear una tabla de fechas única que se propague a todas las tablas de tipo de hechos, lo que posiblemente resulte en una tabla única para aplicar los filtros de tiempo. Para más información sobre cómo crear las tablas de fechas, lea el artículo [Configuración y uso de tablas de fechas en Power BI Desktop](../desktop-date-tables.md).

Si la opción _Fecha y hora automáticas_ no es pertinente para sus proyectos, le recomendamos deshabilitar la opción _Fecha y hora automáticas_ local. Esto garantizará que todos los archivos de Power BI Desktop nuevos que cree no habilitarán la opción _Fecha y hora automáticas_.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Fecha y hora automáticas en Power BI Desktop](../desktop-auto-date-time.md)
- [Configuración y uso de tablas de fechas en Power BI Desktop](../desktop-date-tables.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
