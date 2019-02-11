---
title: API de Power BI que usan una directiva de retención automática para datos en tiempo real
description: Obtenga información acerca de la directiva de retención automática en el servicio Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 246feb1cb15d1688cab044151b50ba62db45c453
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762407"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Directiva de retención automática para datos en tiempo real

La directiva de retención automática del servicio Power BI es un parámetro de cadena de consulta que habilita una directiva de retención predeterminada para limpiar de forma automática los datos antiguos y, al mismo tiempo, mantiene un flujo constante de datos nuevos en el panel. La primera directiva de retención se denomina *Primero en entrar, primero en salir (FIFO)*. Cuando se habilita, se recopilan los datos en una tabla hasta que se alcancen las 200.000 filas. Una vez que los datos superan las 200.000 filas, las filas más antiguas se eliminan del conjunto de datos. Esto mantiene entre 200.000 y 210.000 filas que contendrán solo los datos más recientes.  
  
<center>

![Directiva de retención](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Las directivas de retención se habilitan cuando se crean los conjuntos de datos. Lo único que debe hacer es agregar el parámetro de consulta de "directiva de retención predeterminada" a la llamada de los conjuntos de datos POST y establecer su valor en *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}