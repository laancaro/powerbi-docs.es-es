---
title: Uso del motor de proceso mejorado con flujos de datos
description: Más información sobre cómo usar el motor de proceso mejorado en Power BI Premium con flujos de datos
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 1d2bd150d33d95f2ec8759f9e876b3920eede3b6
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75840079"
---
# <a name="the-enhanced-compute-engine"></a>Motor de proceso mejorado

El motor de proceso mejorado de Power BI permite a los suscriptores de Power BI Premium usar su capacidad para optimizar el uso de flujos de datos. El uso del motor de proceso mejorado proporciona las siguientes ventajas:

* Reducción drástica del tiempo de actualización necesario para los pasos ETL de ejecución prolongada en entidades calculadas, como la realización de *combinaciones*, *distinciones*, *filtrados* y *agrupaciones*
* Realización de consultas DirectQuery sobre entidades (en febrero de 2020)

En las secciones siguientes se describe cómo habilitar el motor de proceso mejorado y se responde a preguntas habituales.


## <a name="using-the-enhanced-compute-engine"></a>Uso del motor de proceso mejorado

El motor de proceso mejorado está habilitado en la página **Configuración de capacidad** en el servicio Power BI, en la sección correspondiente a los **flujos de datos**. De forma predeterminada, el motor de proceso mejorado está **Apagado**. Para encenderlo, cambie la alternancia a **Encendido**, como se muestra en la siguiente imagen, y guarde la configuración. 

![Encendido del motor de proceso mejorado](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

Una vez que active el motor de proceso mejorado, vuelva a los flujos de datos y debería ver una mejora del rendimiento en cualquier entidad calculada que realice operaciones complejas, como *combinaciones* u operaciones de *agrupar por* para flujos de datos creados a partir de entidades vinculadas existentes en la misma capacidad. 

Para hacer el mejor uso del motor de proceso, debe dividir la etapa ETL en dos flujos de datos independientes de la siguiente manera:

* **Flujo de datos 1**: este flujo de datos solo debe ingerir todo lo necesario de un origen de datos y colocarlo en el flujo de datos 2.
* **Flujo de datos 2**: realice todas las operaciones ETL en este segundo flujo de datos, pero asegúrese de que hace referencia al flujo de datos 1, que debe estar en la misma capacidad. Asegúrese también de realizar primero las operaciones que se puedan plegar (filtrar, agrupar por, distinguir, combinar), antes que cualquier otra, para garantizar que se use el motor de proceso.

## <a name="common-questions-and-answers"></a>Preguntas y respuestas frecuentes

**Pregunta:** He habilitado el motor de proceso mejorado, pero las actualizaciones son más lentas. ¿Por qué?

**Respuesta:** Si habilita el motor de proceso mejorado, hay dos posibles explicaciones para los tiempos de actualización más lentos:

 - Cuando el motor de proceso mejorado está habilitado, requiere algo de memoria para que funcione correctamente. Por lo tanto, se reduce la memoria disponible para realizar una actualización, lo que aumenta la probabilidad de que las actualizaciones se puedan poner en cola, lo que a su vez reduce el número de flujos de datos que se pueden actualizar simultáneamente. Para solucionarlo, al habilitar el proceso mejorado, aumente la memoria asignada a los flujos de datos para asegurarse de que la memoria disponible para las actualizaciones de flujo de datos simultáneas siga siendo la misma.

 - Otro motivo por el que las actualizaciones pueden volverse más lentas es que el motor de proceso solo funciona sobre entidades existentes; si el flujo de datos hace referencia a un origen de datos que no es un flujo de datos, no verá ninguna mejora. No se producirá un aumento del rendimiento, ya que, en algunos escenarios de macrodatos, la lectura inicial de un origen de datos sería más lenta porque los datos deben pasarse al motor de proceso mejorado.  

**Pregunta:** No veo la alternancia del motor de proceso mejorado. ¿Por qué?

**Respuesta:** El motor de proceso mejorado se publica en etapas en regiones de todo el mundo. Está previsto que todas las regiones se admitan a finales de 2020.

**Pregunta:** ¿Cuáles son los tipos de datos admitidos en el motor de proceso?

**Respuesta:** El motor de proceso mejorado y los flujos de datos actualmente admiten los siguientes tipos de datos. Si el flujo de datos no utiliza uno de los siguientes tipos de datos, se produce un error durante la actualización:

* Fecha y hora
* Número decimal
* Texto
* Número entero
* Fecha/hora/zona
* Verdadero/Falso
* Fecha
* Hora

## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporciona información sobre el uso del motor de proceso mejorado para flujos de datos. Los siguientes artículos también pueden resultarle útiles:

* [Preparación de datos de autoservicio con flujos de datos](service-dataflows-overview.md)
* [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
* [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Recursos para desarrolladores sobre flujos de datos de Power BI](service-dataflows-developer-resources.md)

Para obtener más información sobre Power Query y la actualización programada, puede leer estos artículos:
* [Información general sobre consultas en Power BI Desktop](desktop-query-overview.md)
* [Configuración de la actualización programada](refresh-scheduled-refresh.md)

Para más información sobre Common Data Service, puede leer su artículo de introducción:
* [Introducción a Common Data Service](https://docs.microsoft.com/powerapps/common-data-model/overview)

