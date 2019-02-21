---
title: Sugerencias para crear aplicaciones de plantilla en Power BI (versión preliminar)
description: Sugerencias sobre la creación de consultas, modelos de datos, informes y paneles para crear aplicaciones de plantilla de calidad
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/05/2019
ms.author: maggies
ms.openlocfilehash: 282638c7c1c8a60ee93292602766d63fd0fe436e
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2019
ms.locfileid: "56250052"
---
# <a name="tips-for-authoring-template-apps-in-power-bi-preview"></a>Sugerencias para crear aplicaciones de plantilla en Power BI (versión preliminar)

Cuando se [crea la aplicación de plantilla](service-template-apps-create.md) en Power BI, parte del proceso es la logística para crear el área de trabajo, las pruebas y la producción. Pero la otra parte importante es, obviamente, la creación del informe y el panel. El proceso de creación se puede desglosar en cuatro componentes principales. Trabajar en estos componentes le ayudará a crear la mejor aplicación de plantilla posible:

* Mediante **consultas**, [conecta](desktop-connect-to-data.md) y [transforma](desktop-query-overview.md) los datos, y define [parámetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* En el **modelo de datos**, crea [relaciones](desktop-create-and-manage-relationships.md), [medidas](desktop-measures.md) y mejoras de preguntas y respuestas.  
* Las **[páginas de informes](desktop-report-view.md)** incluyen objetos visuales y filtros para proporcionar información sobre los datos.  
* Los **[paneles](consumer/end-user-dashboards.md)** y los [iconos](service-dashboard-create.md) ofrecen una visión general de la información incluida.  

Puede estar familiarizado con cada una de las partes de las características de Power BI existentes. Al compilar una aplicación de plantilla, hay aspectos adicionales que tener en cuenta para cada componente. Vea las secciones siguientes para obtener más detalles.

<a name="queries"></a>

## <a name="queries"></a>Consultas
Para las aplicaciones de plantilla, se usan consultas desarrolladas en Power BI Desktop para conectarse al origen de datos e importar datos. Estas consultas tienen que devolver un esquema coherente y son compatibles con la actualización de datos programada (no se admite DirectQuery).

### <a name="connect-to-your-api"></a>Conexión con la API
Para empezar, debe conectarse a la API desde Power BI Desktop para comenzar a generar las consultas.

Puede usar los conectores de datos que están disponibles de serie en Power BI Desktop para conectarse a su API. Puede usar el conector de datos web (Obtener datos -> Web) para conectarse a la API de REST o el conector de OData (Obtener datos -> Fuente OData) para conectarse a la fuente OData. Estos conectores solo funcionan de serie si la API es compatible con la autenticación básica.

> [!NOTE]
> Si la API usa cualquier otro tipo de autenticación, como OAuth 2.0 o la clave de la API web, tendrá que desarrollar un conector de datos propio para permitir que Power BI Desktop se conecte y autentique correctamente con la API. Para más información sobre cómo desarrollar un conector de datos propio para la aplicación de plantilla, consulte la [documentación sobre conectores de datos](https://aka.ms/DataConnectors). 
>
>

### <a name="consider-the-source"></a>Tenga en cuenta el origen
Las consultas definen los datos que se incluyen en el modelo de datos. Dependiendo del tamaño de su sistema, estas consultas también deben incluir filtros para asegurarse de que los clientes están tratando con un tamaño administrable que se ajusta a su escenario de negocio.

Las aplicaciones de plantilla de Power BI pueden ejecutar varias consultas en paralelo y para varios usuarios simultáneamente.  Planee con antelación la estrategia de simultaneidad y limitación, y pregúntenos cómo hacer que la aplicación de plantilla sea tolerante a errores.

### <a name="schema-enforcement"></a>Cumplimiento de esquema
Asegúrese de las consultas sean resistentes a los cambios en el sistema. Los cambios de esquema en la actualización pueden interrumpir el modelo. Si es posible que el origen devuelva un resultado de esquema nulo o que falta para algunas consultas, considere la posibilidad de devolver una tabla vacía o un mensaje de error personalizado que sea significativo.

### <a name="parameters"></a>Parámetros
Los [parámetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) en Power BI Desktop permiten a los usuarios proporcionar valores de entrada que permiten personalizar los datos recuperados por el usuario. Piense en los parámetros por adelantado para evitar la repetición del trabajo después de invertir tiempo en generar informes o consultas detallados.

> [!NOTE]
> Las aplicaciones de plantilla admiten todos los parámetros excepto Todos y Binario.
>

### <a name="additional-query-tips"></a>Sugerencias de consulta adicionales

* Asegúrese de que todas las columnas se escriben correctamente.
* Las columnas tienen nombres descriptivos (vea [Preguntas y respuestas](#qa)).  
* Para la lógica compartida, considere el uso de funciones o consultas.  
* En la actualidad, no se admiten niveles de privacidad en el servicio. Si recibe un mensaje sobre los niveles de privacidad, es posible que tenga que volver a escribir la consulta para usar rutas de acceso relativas.  

## <a name="data-models"></a>Modelos de datos

Un modelo de datos bien definido garantiza que los clientes puedan interactuar fácil e intuitivamente con la aplicación de plantilla. Cree el modelo de datos en Power BI Desktop.

> [!NOTE]
> Realizará gran parte de la modelización básica (escritura y nombres de columna) en las [consultas](#queries).
>


### <a name="qa"></a>Preguntas y respuestas
La modelización también afecta a la forma en que las preguntas y respuestas pueden proporcionar resultados para los clientes. Asegúrese de agregar sinónimos a columnas de uso frecuente y de asignar nombres correctos a las columnas en las [consultas](#queries).

### <a name="additional-data-model-tips"></a>Sugerencias del modelo de datos adicionales

Asegúrese de haber:
* Aplicado formato a todas las columnas de valores. Aplicado tipos en la consulta.  
* Aplicado formato a todas las medidas. 
* Establecido el resumen predeterminado. Especialmente "No resumir", cuando sea aplicable (por ejemplo, para valores únicos).  
* Establecido categorías de datos, cuando sea aplicable.  
* Establecido relaciones de datos, según sea necesario.  

## <a name="reports"></a>Informes
Las páginas de informe ofrecen información adicional sobre los datos incluidos en la aplicación de plantilla. Use las páginas de los informes para responder las preguntas empresariales clave que la aplicación de plantilla intenta solucionar. Cree el informe con Power BI Desktop.

> [!NOTE]
> Solo puede incluir un informe en una aplicación de plantilla, por lo que aproveche las ventajas de las distintas páginas para destacar secciones concretas del escenario.
>
>

### <a name="additional-report-tips"></a>Sugerencias para informes adicionales

* Use más de un objeto visual por página para el filtrado cruzado.  
* Alinee los objetos visuales cuidadosamente (sin superponerlos).  
* La página se establece en el modo de diseño "4:3" o "16:9".  
* Todas las agregaciones presentadas tienen sentido numérico (promedios y valores únicos).  
* La segmentación genera resultados racionales.  
* El logotipo está presente al menos en el informe superior.  
* Los elementos están en el esquema de color del cliente lo máximo posible.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Paneles
Los paneles son el principal punto de interacción de los clientes con la aplicación de plantilla. Debe incluir información general sobre el contenido incluido, especialmente las métricas importantes para el escenario de negocio.

Para crear un panel para la aplicación de plantilla, simplemente cargue el archivo PBIX a través de Obtener datos > Archivos, o bien publique directamente desde Power BI Desktop.

> [!NOTE]
> Las aplicaciones de plantilla actualmente requieren un único informe y conjunto de datos por aplicación de plantilla. No ancle contenido de varios informes o conjuntos de datos en el panel que se usa en la aplicación de plantilla.
>
>

### <a name="additional-dashboard-tips"></a>Sugerencias adicionales del panel

* Mantenga el mismo tema al anclar para que los iconos del panel sean coherentes.  
* Ancle un logotipo al tema, para que los consumidores sepan de dónde procede el paquete.  
* El diseño sugerido para funcionar con la mayoría de resoluciones de pantalla es de entre 5 y 6 iconos pequeños de ancho.  
* Todos los iconos del panel deben tener títulos y subtítulos adecuados.  
* Considere la posibilidad de crear agrupaciones en el panel para diferentes escenarios, ya sea de forma horizontal o vertical.  

## <a name="known-limitations"></a>Limitaciones conocidas

| Destacado | Limitación conocida |
|---------|---------|
|Contenido:  Conjuntos de datos   | Debe haber exactamente un conjunto de datos. Solo se permiten los conjuntos de datos creados en Power BI Desktop (archivos .pbix). <br>No se admiten: conjuntos de datos de otras aplicaciones de plantilla, conjuntos de datos de varias áreas de trabajo, informes paginados (archivos .rdl), libros de Excel. |
|Contenido: Informes     | Hasta un informe    |
| Contenido: Paneles | Un panel no vacío como máximo <br>No se admiten: iconos en tiempo real (en otras palabras, no se admite PushDataset o pubnub). |
| Contenido: Flujos de datos | No se admiten: Flujos de datos |
| Contenido de archivos | Solo se admiten archivos PBIX. <br>No se admiten: archivos .rdl (informes paginados), libros de Excel.   |
| Orígenes de datos | Se permiten los orígenes de datos admitidos para la actualización de datos programada en la nube. <br>No se admiten: <br>DirectQuery <br>Conexiones dinámicas (no Azure AS). <br>Orígenes de datos locales (no se admiten las puertas de enlace personales y empresariales) <br>Tiempo real (no se admite para PushDataset) <br>Modelos compuestos |
| Conjunto de datos: entre áreas de trabajo | No se admiten los conjuntos de datos entre áreas de trabajo  |
| Contenido: Paneles | No se admiten los iconos en tiempo real (en otras palabras, no se admite PushDataset o pubnub). |
| Parámetros de consulta | No se admiten: los parámetros de tipo "Todo" o "Binario" bloquean la operación de actualización del conjunto de datos. |
| Objetos visuales personalizados | Solo se admiten los objetos visuales personalizados disponibles públicamente. No se admiten los [objetos visuales personalizados de la organización](power-bi-custom-visuals-organization.md). |

## <a name="next-steps"></a>Pasos siguientes

[¿Qué son las aplicaciones de plantilla de Power BI? (versión preliminar)](service-template-apps-overview.md)
