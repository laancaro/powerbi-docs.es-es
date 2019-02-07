---
title: Compatibilidad de Power BI Premium para grandes conjuntos de datos
description: Power BI Premium ahora admite conjuntos de datos de hasta 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 941d4bc3d66ce8e636f730d5757b7215c978d582
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794830"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Compatibilidad de Power BI Premium para grandes conjuntos de datos

Power BI Premium admite cargas de archivos de Power BI Desktop (.pbix) de hasta 10 GB de tamaño. Una vez que se carga, un conjunto de datos se puede actualizar hasta un tamaño de 12 GB. Para utilizar un conjunto de datos grande, publíquelo en un área de trabajo asignada a la capacidad Premium.
 
## <a name="best-practices"></a>Procedimientos recomendados

En esta sección, se describen los procedimientos recomendados para trabajar con grandes conjuntos de datos.

**Los modelos grandes pueden consumir muchos recursos** de su capacidad. Se recomienda al menos una SKU P1 para cualquier modelo superior a 1 GB. Aunque publicar modelos grandes en las áreas de trabajo respaldadas por SKU hasta A3 puede funcionar, actualizarlos no lo hará.

La tabla siguiente describe las SKU recomendadas para diversos tamaños de .pbix:

   |SKU  |Tamaño de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | hasta 10 GB   |

La SKU A4 de Power BI Embedded es igual a SKU P1, A5 = P2 y A6 = P3. Tenga en cuenta que la publicación de grandes modelos para A y SKU EM podría devolver errores que no son específicos del error de limitación de tamaño de modelo en la capacidad compartida. Los errores de actualización de modelos grandes en A y SKU EM es probable que apunten a errores relativos a los tiempos de espera. Estamos trabajando para mejorar los mensajes de error para estos escenarios.

**Los archivos .pbix representan datos en un estado muy comprimido**. Los datos probablemente se expandirán varias veces al cargarse en memoria y, a partir de ahí, podrían expandirse varias veces más durante la actualización de datos.

**La actualización programada de conjuntos de datos grandes puede tardar mucho tiempo** y hacer un uso muy intensivo de los recursos. Por lo tanto, no programe demasiadas actualizaciones superpuestas. Observe también que el tiempo de espera para los trabajos de actualización programada se ha duplicado a cuatro horas para todos los conjuntos de datos de esta capacidad. Se recomienda la [actualización incremental](service-premium-incremental-refresh.md), ya que es más rápida y fiable y consume menos recursos.

**La carga inicial de informes de grandes conjuntos de datos puede tardar mucho tiempo** si ha pasado un tiempo desde la última vez que se utilizó el conjunto de datos, porque el modelo se debe cargar en la memoria de su capacidad Premium. Una barra de carga para los informes de carga larga muestra el progreso de carga.

**Si elimina el área de trabajo de capacidad Premium**, el modelo y todos los informes y paneles asociados no funcionarán.

**Aunque las restricciones de memoria y tiempo por consulta son mucho mayores en la capacidad Premium**, es muy recomendable utilizar filtros y segmentaciones para que los objetos visuales muestren únicamente lo necesario.

**Pasos siguientes**

[¿Qué es Power BI Premium?](service-premium.md)
[Notas de la versión de Power BI Premium](service-premium-release-notes.md)
[Notas del producto Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[Notas del producto: Planning a Power BI Enterprise Deployment (Planeación de una implementación de Power BI Enterprise)](https://aka.ms/pbienterprisedeploy)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
