---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560957"
---
## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES
**Pregunta:** ¿Qué ocurre si tengo roles y reglas creados previamente para un conjunto de datos en el servicio Power BI? ¿Seguirán funcionando si no hago nada?  
**Respuesta:** No, los objetos visuales no se representarán correctamente. Tendrá que volver a crear los roles y las reglas en Power BI Desktop y, después, publicarlos en el servicio Power BI.

**Pregunta:** ¿Puedo crear estos roles para orígenes de datos de Analysis Services?  
**Respuesta:** Puede hacerlo si importa los datos a Power BI Desktop. Si usa una conexión dinámica, no podrá configurar RLS en el servicio Power BI. Esto se define en el modelo local de Analysis Services.

**Pregunta:** ¿Puedo usar RLS para limitar las columnas o medidas accesibles por mis usuarios?  
**Respuesta:** No, si un usuario tiene acceso a una fila de datos determinada, puede ver todas las columnas de datos de esa fila.

**Pregunta:** ¿Permite RLS ocultar datos detallados pero dar acceso a datos resumidos en objetos visuales?  
**Respuesta:** No, aunque proteja las filas de datos individuales, los usuarios siempre pueden ver los detalles o los datos resumidos.

