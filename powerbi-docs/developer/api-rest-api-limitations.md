---
title: Limitaciones de la API de REST de Power BI
description: La API REST de Power BI tiene las siguientes limitaciones
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: ebca3dd6bcdbb831960da111fc167f59b5ab0623
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762016"
---
# <a name="power-bi-rest-api-limitations"></a>Limitaciones de la API de REST de Power BI  
  
**Para filas POST**
  
* 75 columnas como máximo
* 75 tablas como máximo
* Un máximo de 10.000 filas para cada solicitud POST de filas  
* 1.000.000 de filas agregadas por hora por cada conjunto de datos  
* Un máximo de 5 solicitudes POST de filas pendientes por cada conjunto de datos  
* 120 solicitudes POST de filas por minuto por cada conjunto de datos
* Si la tabla tiene 250 000 o más filas, 120 solicitudes de filas POST por hora por conjunto de datos
* Un máximo de 200.000 filas almacenadas por tabla en el conjunto de datos FIFO
* Un máximo de 5.000.000 de filas almacenadas por tabla en el conjunto de datos 'no hay directivas de retención'  
* 4.000 caracteres por valor para las columnas de cadena en la operación POST de filas
  
## <a name="see-also"></a>Vea también

[Restricciones y límites del servicio Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Información general sobre la API de REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/)