---
title: Solución de problemas en el desarrollo de objetos visuales personalizados de Power BI
description: En este artículo se examinan algunos problemas comunes que pueden encontrarse al desarrollar o crear un objeto visual personalizado de Power BI.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: d6f3f654574e9cca081ae2f8191fd7b9fc017afd
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223568"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Solución de problemas de los objetos visuales personalizados de Power BI

## <a name="debug"></a>Depurar

**No se ha encontrado el comando de pbiviz (o errores similares)**

Si ejecuta `pbiviz` en la línea de comandos del terminal, verá la pantalla de ayuda. De lo contrario, no está instalado correctamente. Asegúrese de que tiene instalada al menos la versión 4.0 de NodeJS.

**No se puede encontrar el objeto visual de depuración en la pestaña Visualizaciones**

El objeto visual de depuración es similar a un icono de símbolo del sistema en la pestaña **Visualizaciones**.

![Selección del objeto visual](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Si no lo ve, asegúrese de que lo ha habilitado en la configuración de Power BI.

> [!NOTE]
> Actualmente, el objeto visual de depuración solo está disponible en el servicio Power BI y no está en Power BI Desktop ni en la aplicación móvil. El objeto visual empaquetado seguirá funcionando en todas partes.

**No puede ponerse en contacto con el servidor del objeto visual**

Ejecute el servidor del objeto visual con el comando `pbiviz start` en línea de comandos del terminal desde la raíz del proyecto del objeto visual. Si el servidor se está ejecutando, es probable que los certificados SSL no se hayan instalado correctamente.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información y respuestas a las preguntas, visite las [preguntas más frecuentes sobre objetos visuales personalizados de Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).