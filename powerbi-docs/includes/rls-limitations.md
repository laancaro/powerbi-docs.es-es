---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: davidi
ms.openlocfilehash: 6d1a239954a64da1c92cc68b56912e6f4ab67228
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "74882784"
---
## <a name="limitations"></a>Limitaciones

Esta es una lista de las limitaciones actuales para la seguridad de nivel de fila en los modelos en la nube.

* Si anteriormente definió roles y reglas en el servicio Power BI, debe volver a crearlos en Power BI Desktop.

* Solo puede definir RLS en los conjuntos de datos creados con Power BI Desktop. Si quiere habilitar RLS para conjuntos de datos creados con Excel, debe convertir primero los archivos en archivos de Power BI Desktop (PBIX). [Más información](../desktop-import-excel-workbooks.md)

* Solo se admiten conexiones de importación y de DirectQuery. Las conexiones dinámicas con Analysis Services se controlan en el modelo local.

## <a name="known-issues"></a>Problemas conocidos

Hay un problema conocido en el que se produce un mensaje de error al intentar publicar un informe publicado anteriormente desde Power BI Desktop. El escenario es el siguiente.

1. Ana tiene un conjunto de datos publicado en el servicio Power BI y ha configurado RLS.

1. Ana actualiza el informe en Power BI Desktop y vuelve a publicarlo.

1. Ana recibe un error.

**Solución alternativa:** vuelva a publicar el archivo de Power BI Desktop desde el servicio Power BI hasta que se solucione este problema. Para ello, seleccione **Obtener datos** > **Archivos**.
