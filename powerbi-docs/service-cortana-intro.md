---
title: 'Uso de Cortana para buscar y ver informes y paneles: Power BI'
description: Use Cortana con Power BI para obtener respuestas a partir de los datos. Actualmente funciona con informes y paneles.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: b0109798336797eee93f738f15af71c00f818bf8
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73853657"
---
# <a name="find-and-view-your-power-bi-data-with-cortana-for-power-bi"></a>Busque y vea datos de Power BI con Cortana para Power BI
Use Cortana en los dispositivos Windows 10 para obtener respuestas instantáneas a sus preguntas empresariales importantes. Mediante la integración con Power BI, Cortana puede recuperar información clave directamente de los informes y paneles de Power BI. Basta con la versión de Windows 10 de noviembre de 2015 o una posterior, Cortana, Power BI y acceso a un conjunto de datos como mínimo.

> [!IMPORTANT]
> La integración con Cortana estará en desuso próximamente en Power BI. A partir del 11 de junio, Cortana ya no funcionará con ningún panel o informe.

![Campo de búsqueda de Cortana](media/service-cortana-intro/power-bi-cortana-searchbox.png)

## <a name="preview-the-new-cortana-dashboard-search-experience-for-windows-10"></a>Obtener vista previa de la nueva experiencia de búsqueda en *paneles* de Cortana para Windows 10
Durante un tiempo ha podido [usar Cortana para recuperar determinados tipos de páginas de informe](service-cortana-answer-cards.md). Ahora hemos agregado una **nueva experiencia**: la posibilidad de recuperar también paneles. Pruébelo y [envíenos sus comentarios en Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). Al final, la *nueva experiencia* se ampliará para que incluya también las búsquedas de Cortana para los informes.  Una de las ventajas principales de la nueva experiencia es que no es necesario hacer nada especial para configurarla. No tiene que realizar ninguna habilitación ni configuración en Cortana ni en Windows 10. Simplemente funciona.

> [!NOTE]
> Y, si eso no es así, consulte el [artículo de solución de problemas](service-cortana-troubleshoot.md) para obtener ayuda.
> 
> 

La tecnología subyacente usa el [servicio Microsoft Azure Search](https://docs.microsoft.com/azure/search/). Este servicio de búsqueda proporciona funcionalidades adicionales como clasificación inteligente, corrección de errores y autocompletar.

Ambas experiencias de Cortana pueden existir simultáneamente.

## <a name="cortana-for-power-bi-documentation"></a>Documentación de Cortana para Power BI
Existen cuatro documentos que le indican cómo configurar y usar Cortana para Power BI.

**Artículo 1** (este): comprender cómo funcionan conjuntamente Cortana y Power BI

**Artículo 2**: [buscar informes de Power BI: habilitar la integración de Cortana - Power BI - Windows](service-cortana-enable.md)

**Artículo 3**: [para realizar búsquedas en informes de Power BI, cree *tarjetas de respuestas de Cortana*](service-cortana-answer-cards.md) especiales

**Artículo 4**: [solucionar problemas](service-cortana-troubleshoot.md)

## <a name="how-cortana-and-power-bi-work-together"></a>Cómo funcionan conjuntamente Cortana y Power BI
Al usar Cortana para formular una pregunta, Power BI puede ser uno de los lugares donde Cortana busque respuestas. En Power BI, Cortana puede encontrar respuestas con datos enriquecidos de los informes de Power BI (que contienen un tipo especial de página de informe denominada *tarjeta de respuestas de Cortana*) y de los paneles de Power BI.

Si Cortana encuentra una coincidencia, muestra el nombre del panel o la página de informe directamente en la pantalla de Cortana. Este panel o página de informe se puede abrir en Power BI. Las páginas de informe también se pueden explorar directamente en Cortana: son interactivas.

![página de informe interactiva que se muestra en Cortana](media/service-cortana-intro/power-bi-report-cortana-s.png)

### <a name="cortana-and-dashboards-the-new-experience"></a>Cortana y los paneles (una *nueva experiencia*)
Cortana puede encontrar respuestas en los paneles que posee y en los paneles que se han compartido con usted. Formule preguntas a Cortana mediante títulos, palabras clave, nombres de propietario, nombres de área de trabajo, nombres de aplicaciones y mucho más.

La pregunta debe contener al menos dos palabras para que Cortana encuentre una respuesta. Por tanto, si busca en un panel con un nombre con una sola palabra (Marketing), agregue la palabra "mostrar" o "Power BI" o el nombre del propietario a la pregunta, como por ejemplo "mostrar Marketing" y "ejemplo de michele hart". 

Si el título del panel tiene más de una palabra, Cortana solo devuelve ese panel si la búsqueda coincide con al menos dos de las palabras o con una de las palabras más el nombre del propietario. Para un panel con el nombre "Ejemplo de rentabilidad del cliente": 

* "mostrarme cliente" *no* devuelve un resultado de panel de Power BI.   
* expresiones como "mostrarme rentabilidad cliente", "r cliente", "e cliente", "ejemplo rentabilidad", "ejemplo de michele hart", "mostrar ejemplo rentabilidad cliente" y "mostrarme r cliente" *sí* devuelven un resultado de Power BI.
* Agregar las palabras "powerbi" cuenta como una de las dos palabras requeridas, por lo que "ejemplo de powerbi" *devuelve* un resultado de Power BI. 
  
    ![Búsqueda de Cortana con al menos 2 palabras](media/service-cortana-intro/power-bi-cortana-2-words.png)

### <a name="cortana-and-reports"></a>Cortana y los informes
 Cortana puede encontrar respuestas en los informes que tienen [páginas diseñadas específicamente para que las muestre Cortana](service-cortana-answer-cards.md). Solo tiene que formular preguntas mediante el título o las palabras clave de alguna de estas páginas de informe especiales.  

La tecnología subyacente para los informes usa [Preguntas y respuestas de Power BI](power-bi-tutorial-q-and-a.md).

Cuando formula una pregunta en Cortana, Power BI responde a partir de las páginas de informe diseñadas específicamente para Cortana. Las posibles respuestas dependen de Cortana en ese momento, de las *tarjetas de respuestas* que haya creado directamente en Power BI.  Para explorar más detalladamente una respuesta, abra un resultado en Power BI.

> [!NOTE]
> Para que Cortana pueda buscar respuestas en los informes de Power BI, deberá [habilitar esta característica con el servicio Power BI y configurar Windows para que se comunique con Power BI](service-cortana-enable.md).  
> 
> 

## <a name="using-cortana-to-get-answers-from-power-bi"></a>Uso de Cortana para obtener respuestas de Power BI
1. Inicie Cortana. Hay muchas maneras diferentes de *abrir* Cortana: seleccione el icono de Cortana en la barra de tareas (en la imagen de abajo), use comandos de voz o pulse el icono de búsqueda en el dispositivo móvil de Windows.
   
     ![](media/service-cortana-intro/power-bi-cortana-searchbox.png)
2. Cuando esté listo Cortana, escriba o formule en voz alta su pregunta en la barra de búsquedas. Cortana mostrará los resultados disponibles. Si hay un panel de Power BI que coincida con la pregunta, aparecerá en **Mejor coincidencia** o **Power BI**.
   
     ![La búsqueda de Cortana encuentra el panel de Power BI](media/service-cortana-intro/power-bi-cortana-search-hr.png "Cortana encuentra un panel de Power BI")
   
   > [!NOTE]
   > Actualmente solo se admite el inglés.
   > 
   > 
3. Seleccione el panel para abrirlo en Cortana.

    ![Seleccionar el panel de Power BI](media/service-cortana-intro/power-bi-cortana-dashboard.png "Seleccionar el panel de Power BI")

    Puede cambiar el diseño mediante la [edición de la *vista de teléfono* del panel](service-create-dashboard-mobile-phone-view.md). 

1. Desde Cortana también puede abrir el panel en el servicio Power BI o en Power Bi Mobile. Para abrir el panel en el servicio Power BI, seleccione **Abrir en la Web**. 
   
   ![Abrir el panel desde Cortana](media/service-cortana-intro/power-bi-dashboard-opens.png "Abrir el panel desde Cortana")   
4. Ahora vamos a usar Cortana para buscar un informe. Es necesario tener un [informe que tenga una página con una tarjeta de respuestas de Cortana](service-cortana-answer-cards.md). En este ejemplo, un informe denominado "Cortana-New-Stores" contiene una página de tarjeta de respuestas de Cortana llamada "cortana stores".  
   
     Escriba o formule en voz alta su pregunta en la barra de búsqueda de Cortana. Cortana mostrará los resultados disponibles. Si hay una página de informe de Power BI que coincida con la pregunta, aparecerá en **Mejor coincidencia** o **Power BI**. Y en este ejemplo, el archivo .pbix (y la copia de seguridad) que se usó para crear la tarjeta de respuestas también aparece en **Documentos**.
   
     ![Búsqueda de un informe](media/service-cortana-intro/power-bi-cortana-search3-m.png "búsqueda de un informe") 
5. Seleccione la página de informe **Cortana stores** para que aparezca en la ventana de Cortana.
   
    ![Se abre la página de informe en Cortana](media/service-cortana-intro/power-bi-report-cortana-opens.png "Se abre la página de informe en Cortana")   
   
    Recuerde que una *tarjeta de respuestas* es un tipo especial de página del informe de Power BI creada por el propietario de un conjunto de datos.  Para más información, consulte el artículo sobre la [creación de una tarjeta de respuestas de Cortana](service-cortana-answer-cards.md).
6. Eso no es todo. Interactúe con las visualizaciones en la tarjeta de respuestas como lo haría en Power BI.
   
   * Por ejemplo, seleccione un elemento en una visualización para aplicar un filtro cruzado y resaltar las demás visualizaciones en la tarjeta de respuestas.
     
     ![](media/service-cortana-intro/power-bi-cortana-filtered-new.png)
   * O bien, use lenguaje natural para filtrar los resultados en su lugar.  Por ejemplo, pregunte por "los almacenes de Cortana para Lindseys" y vea la tarjeta con el filtro, que muestra solo los datos de la cadena Lindseys.
     
     ![Filtro cruzado en Cortana](media/service-cortana-intro/power-bi-cortana-filtered-2.png "Filtro cruzado en Cortana")
7. Continúe explorando. Desplácese hasta la parte inferior de la ventana de Cortana y seleccione **Abrir en Power BI**.
   
     ![](media/service-cortana-intro/power-bi-cortana-open-new.png)
8. Se abre la página de informe en Power BI.    
     ![Abrir el informe desde Cortana](media/service-cortana-intro/power-bi-cortana-open2.png "CoSe abre la tarjeta de respuestas de Cortana en la búsqueda de Cortana

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
* Cortana no tiene acceso a las tarjetas de Cortana que no se hayan [habilitado para Power BI](service-cortana-enable.md).
* ¿Sigue sin conseguir que Cortana funcione con Power BI?  Pruebe el [solucionador de problemas de Cortana](service-cortana-troubleshoot.md).
* Cortana para Power BI actualmente solo está disponible en inglés.
* Cortana para Power BI solo está disponible en dispositivos móviles de Windows.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/).
Comentarios [Envíenos sus comentarios en Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi).

## <a name="next-steps"></a>Pasos siguientes
[Habilitar la integración de Windows, Cortana y Power BI para informes](service-cortana-enable.md)

