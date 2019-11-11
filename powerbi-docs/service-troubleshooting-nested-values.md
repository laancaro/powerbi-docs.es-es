---
title: Solución de problemas de valores anidados devueltos como texto en el servicio Power BI
description: Obtenga información sobre cómo corregir valores anidados que se convierten en una cadena cuando se usa una configuración de privacidad del origen de datos incorrecta
author: cpopell
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: ab40ca9c415dacf52f4d82eb2c157d57aef92f93
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871280"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Solución de problemas de valores anidados devueltos como texto en el servicio Power BI

## <a name="cause"></a>Causa

En el pasado, ha habido casos donde un informe de Power BI se actualiza correctamente en Power BI Desktop, pero en el servicio Power BI produce un error similar a "No se puede convertir el valor"[tabla]"al tipo Table". Una de las causas de este error es que, cuando el firewall de privacidad de datos almacena en búfer un origen de datos, los valores no escalares anidados (como tablas, registros, listas y funciones) se convierten automáticamente en valores de texto (por ejemplo, "[Tabla]" o "[Registro]").

Ahora que el servicio Power BI admite la configuración de los niveles de privacidad (o desactivar el Firewall completamente), estos errores pueden evitarse mediante la [configuración de privacidad del origen de datos](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) en el servicio Power BI como no privado.

A partir de la versión de junio de Power BI, cuando el firewall almacena en búfer una tabla, un registro o una lista anidadas, en lugar de convertir estos valores en texto en modo silencioso, se producirá el error siguiente: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Efecto en la carga y actualización

Aunque el cambio está motivado por el almacenamiento en búfer del firewall, su impacto se extiende también a la carga y actualización. Para solucionar el comportamiento del almacenamiento en búfer del firewall, también fue necesario cambiar el comportamiento de la carga de tablas y registros anidados en el modelo de Power BI y el modelo de datos de Excel en PQ para Excel. Antes, las tablas y los registros anidados se cargaban como valores de texto (por ejemplo, "[Tabla]" o "[Registro]"). Ahora se deberán tratar como errores, lo que dará como resultado un valor NULL en la tabla cargada y un incremento del recuento de errores en los resultados de la carga.

Puesto que estos errores solo se producen durante la carga y actualización, no aparecerán en el Editor de Power Query.

### <a name="before"></a>Antes

- Carga y actualización sin errores
- La tabla cargada contiene "[Tabla]", "[Registro]", etc.
 

### <a name="after"></a>Después

- Carga y actualización con errores
- La tabla cargada contiene valores NULL (en lugar de "[Tabla]", "[Registro]", etc).
 

## <a name="resolution"></a>Resolución

¿Está cargando una columna que contiene valores no escalares (por ejemplo, tablas, listas, registros, etc)?
Si es así, podrá eliminar los errores si elimina la columna.
Si no puede eliminar la columna, debe replicar el comportamiento anterior agregando una columna personalizada y usando una lógica similar a la del ejemplo siguiente:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

¿Se reproduce la incidencia en Power BI Desktop si establece todos los valores de la configuración de privacidad del origen de datos en Privado?
Si es así, debería ser capaz de resolver el error mediante la [configuración de privacidad del origen de datos](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) en el servicio Power BI para que sean no privados.
