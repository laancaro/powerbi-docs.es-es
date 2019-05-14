---
title: Rendimiento de la puerta de enlace monitoring (versión preliminar pública)
description: Este artículo proporciona información sobre cómo supervisar el rendimiento de las actividades de puerta de enlace de datos en el entorno local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535376"
---
# <a name="gateway-performance-monitoring-public-preview"></a>Rendimiento de la puerta de enlace monitoring (versión preliminar pública)

Para supervisar el rendimiento, los administradores de la puerta de enlace han confiado tradicionalmente en la supervisión manualmente los contadores de rendimiento a través de la herramienta Monitor de rendimiento de Windows. Ahora ofrecemos el registro de consultas adicionales y un [archivo de plantilla de PBI de rendimiento de puerta de enlace](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) para visualizar los resultados. Esta característica proporciona nuevas perspectivas sobre el uso de puerta de enlace y permite solucionar consultas con un rendimiento lento.

> [!NOTE]
> Esta característica está actualmente disponible solo para la puerta de enlace de datos de forma local en el modo estándar y no para el modo personal.

## <a name="enable-performance-logging"></a>Habilitar el registro de rendimiento

Para habilitar esta característica, realice los cambios siguientes en el *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* de archivos en la "\Program Files\On-puerta de enlace de datos local" carpeta:

1. Actualización **QueryExecutionReportOn** a _True_ para habilitar el registro adicional para las consultas ejecutadas con la puerta de enlace. Al habilitar esta opción crea el informe de ejecución de consulta y los archivos de informe de agregación de ejecución de consulta.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Actualización **SystemCounterReportOn** a _True_ para habilitar el registro adicional para la memoria y contadores de CPU del sistema. Al habilitar esta opción, crea el archivo de informe de agregación de contador del sistema.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Hay otros valores en el archivo de configuración que se puede actualizar según sea necesario.

    - **ReportFilePath**: Determina la ruta de acceso donde se almacenan los tres archivos de registro. De forma predeterminada, esta ruta de acceso es "\Users\PBIEgwService\AppData\Local\Microsoft\On-premises datos gateway\Report" o "Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On localmente datos gateway\Report", según la versión del sistema operativo. Si usa una cuenta de servicio para la puerta de enlace distinto _PBIEgwService_, reemplace esta parte de la ruta de acceso con el nombre de cuenta de servicio.
    - **ReportFileCount**: Determina el número de archivos de registro de cada tipo para conservar. El valor predeterminado es 10.
    - **ReportFileSizeInBytes**: Determina el tamaño del archivo que desea mantener. El valor predeterminado es 104857600.
    - **QuerExecutionAggregationTimeInMinutes**: Determina el número de minutos para el que se agrega la información de ejecución de consulta. El valor predeterminado es 5.
    - **SystemCounterAggregationTimeInMinutes**: Determina el número de minutos para el que se agregan los contadores del sistema. El valor predeterminado es 5.

1. Una vez realizados los cambios en el archivo de configuración, reinicie la puerta de enlace para estos valores de configuración surta efecto. Ahora empezará a ver los archivos de informe que se generan en la ubicación especificada para **ReportFilePath**.

    > [!NOTE]
    > Puede tardar hasta 10 minutos más la cantidad de tiempo establecido para **QuerExecutionAggregationTimeInMinutes** en el archivo de configuración hasta que los archivos de inicio que se muestran en la carpeta.

## <a name="understand-performance-logs"></a>Comprender los registros de rendimiento

Al activar esta característica, se creación tres nuevos archivos de registro:

- El informe de ejecución de consulta
- El informe de agregación de la ejecución de consulta
- El informe de agregación de contador del sistema

El informe de ejecución de consultas contiene información de ejecución de consulta detallada. Se capturan los siguientes atributos:

|Atributo |Descripción |
| ---- | ---- |
|**GatewayObjectId** |Identificador único para la puerta de enlace. |
|**RequestId** |Identificador único para una solicitud de la puerta de enlace. Podría ser el mismo para varias consultas. |
|**DataSource** |Contiene el tipo de origen de datos y el origen de datos. |
|**QueryTrackingId** |Identificador único para una consulta. |  
|**QueryExecutionEndTimeUTC** |Hora en que completó la ejecución de consultas. |
|**QueryExecutionDuration**(ms) |Duración de ejecución de una consulta. |
|**QueryType** |Tipo de consulta: por ejemplo, podría ser la consulta pasa una actualización de Power BI y DirectQuery o consultas de PowerApps y Microsoft Flow. |
|**DataProcessingEndTimeUTC** |Hora de las actividades, como la puesta en cola, recuperación de datos, compresión, procesamiento de datos y así sucesivamente completado de procesamiento de datos. |
|**DataProcessingDuration**(ms) |Duración de las actividades de procesamiento de datos, como la puesta en cola, recuperación de datos, la compresión, procesamiento de datos y así sucesivamente. |
|**Éxito** |Indica si la consulta se ha realizado correctamente o no. |
|**ErrorMessage** |Si se produjo un error en la consulta, indica el mensaje de error. |
| | |

El informe de agregación de la ejecución de consultas contiene información de consulta agregada a un intervalo de tiempo por **GatewayObjectId**, **DataSource**, **éxito**y **QueryType**. El valor predeterminado es 5 minutos, pero puede ajustar según se describe a continuación. Se capturan los siguientes atributos:

|Atributo |Descripción |
| ---- | ---- |
|**GatewayObjectId** |Identificador único para la puerta de enlace. |
|**AggregationStartTimeUTC** |Inicio de la ventana de tiempo para el que se agregaron los atributos de la consulta. |
|**AggregationEndTimeUTC** |Final de la ventana de tiempo para la consulta que se agregaron los atributos. |
|**DataSource** |Contiene el tipo de origen de datos y el origen de datos. |
|**Éxito** |Indica si la consulta se ha realizado correctamente o no. |
|**AverageQueryExecutionDuration**(ms) |Promedio de tiempo de ejecución de consulta para el período de tiempo de agregación. |
|**MaxQueryExecutionDuration**(ms) |Tiempo de ejecución de consulta máxima durante el período de tiempo de agregación. |
|**MinQueryExecutionDuration**(ms) |Tiempo de ejecución de consulta mínima para el período de tiempo de agregación. |
|**QueryType** |Tipo de consulta: por ejemplo, podría ser la consulta pasa una actualización de Power BI y DirectQuery o consultas de PowerApps y Microsoft Flow. |
|**AverageDataProcessingDuration**(ms) |Promedio de tiempo para las actividades de procesamiento de datos, como la puesta en cola, la recuperación de datos, la compresión, procesamiento de datos, y así sucesivamente para el período de tiempo de agregación. |
|**MaxDataProcessingDuration**(ms) |Tiempo máximo para las actividades de procesamiento de datos, como la puesta en cola, recuperación de datos, la compresión, procesamiento de datos y así sucesivamente para el período de tiempo de agregación. |
|**MinDataProcessingDuration**(ms) |Tiempo mínimo para las actividades de procesamiento de datos, como la puesta en cola, recuperación de datos, la compresión, procesamiento de datos y así sucesivamente para el período de tiempo de agregación. |
|**recuento** |Número de consultas. |
| | |

El informe de agregación de contador del sistema contiene los valores de contador del sistema se agregan a un intervalo de tiempo. El valor predeterminado es 5 minutos, pero puede ajustar según se describe a continuación. Se capturan los siguientes atributos:

|Atributo |Descripción |
| ---- | ---- |
|**GatewayObjectId** |Identificador único para la puerta de enlace. |
|**AggregationStartTimeUTC** |Inicio de la ventana de tiempo para el que se han agregado los contadores del sistema. |
|**AggregationEndTimeUTC** |Final de la ventana de tiempo para el sistema que se han agregado los contadores. |
|**CounterName** |Contadores del sistema, incluido el uso de CPU y memoria por la puerta de enlace, mashup y en general por la máquina que hospeda la puerta de enlace. |
|**Max** |Valor máximo para el contador del sistema para el período de tiempo de agregación. |
|**Min** |Valor mínimo para el contador del sistema para el período de tiempo de agregación. |
|**Average** |Valor medio del contador del sistema durante el período de tiempo de agregación. |
| | |

## <a name="visualize-gateway-performance"></a>Visualizar el rendimiento de la puerta de enlace

Ahora, puede visualizar los datos que se están en los archivos de registro.

1. Descargue el [plantilla PBI de rendimiento de puerta de enlace](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) y ábralo con Power BI desktop.

1. En el cuadro de diálogo que aparece, compruebe que la ruta de acceso de carpeta coincide con el valor de **ReportFilePath**.

    ![Elemento emergente para la ruta de acceso de carpeta](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Seleccione **carga**, y el archivo de plantilla comienza a cargar los datos de los archivos de registro. A continuación, se deben rellenar todos los objetos visuales con los datos de los informes.

1. Opcionalmente, guarde este archivo como un archivo PBIX y publicarlo en el servicio para las actualizaciones automáticas.

Además, puede personalizar este archivo de plantilla para satisfacer sus necesidades. Para obtener más información sobre las plantillas de Power BI, consulte este [entrada de Blog de Microsoft Power BI](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).