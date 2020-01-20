---
title: ¿Qué es Power BI Desktop?
description: Obtenga información sobre Power BI Desktop y sobre cómo empezar a usarlo.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 12/16/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: bd95dfcc5d621b5ae4988e187d7cc6d9478feb58
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731187"
---
# <a name="what-is-power-bi-desktop"></a>¿Qué es Power BI Desktop?

*Power BI Desktop* es una aplicación gratuita que se puede instalar en el equipo local y que permite conectarse a los datos, transformarlos y visualizarlos. Con Power BI Desktop, puede conectarse a varios orígenes de datos diferentes y combinarlos (lo que se suele denominar *modelado*) en un modelo de datos. Este modelo de datos permite compilar objetos visuales y colecciones de objetos visuales que se pueden compartir como informes con otras personas de dentro de la organización. La mayoría de los usuarios que trabajan en proyectos de inteligencia empresarial usan Power BI Desktop para crear informes y luego usan el *servicio Power BI* para compartir los informes con otros.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Los usos más comunes de Power BI Desktop son los siguientes:

* Conectar a datos
* Transformar y limpiar datos, para crear un modelo de datos
* Crear objetos visuales, como gráficos o grafos, que proporcionan representaciones visuales de los datos
* Crear informes que son colecciones de objetos visuales, en una o varias páginas de informes
* Compartir informes con otros usuarios mediante el servicio Power BI

Los usuarios que suelen ser responsables de esas tareas se suelen considerar *analistas de datos* (a los que a veces se hace referencia con el término *analistas*) o profesionales de inteligencia empresarial (a menudo conocidos como *creadores de informes*). Pero muchas personas que no se consideran analistas ni creadores de informes usan Power BI Desktop para crear informes atractivos o para extraer datos de varios orígenes y crear modelos de datos que luego pueden compartir con sus compañeros de trabajo y organizaciones.

En Power BI Desktop hay tres vistas disponibles, que se seleccionan en el lado izquierdo del lienzo. Las vistas, que se muestran en el orden en que aparecen, son las siguientes:
* **Informe**: en esta vista se crean informes y objetos visuales y es donde se pasa la mayor parte del tiempo de creación.
* **Datos**: en esta vista se ven las tablas, las medidas y los demás datos que se usan en el modelo de datos asociado al informe y se transforman los datos para usarlos de la mejor manera posible en el modelo del informe.
* **Modelo**: en esta vista se ven y se administran las relaciones entre las tablas del modelo de datos.

En la imagen siguiente se muestran las tres vistas tal como aparecen en el lado izquierdo del lienzo:

![Vistas de Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop-07.png)
 

## <a name="connect-to-data"></a>Conectar a datos
Para empezar a trabajar con Power BI Desktop, el primer paso es conectarse a los datos. Hay muchos orígenes de datos distintos a los que es posible conectarse desde Power BI Desktop. 

Para conectarse a los datos:

1. En la cinta **Inicio**, seleccione **Obtener datos** > **Más**. 

   Aparece la ventana **Obtener datos**, que muestra muchas categorías a las que Power BI Desktop puede conectarse.

   ![Obtener datos en Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

2. Cuando se selecciona un tipo de datos, se le pide información, como la dirección URL y las credenciales, necesaria para que Power BI Desktop se conecte al origen de datos en su nombre.

   ![Conexión a una base de datos SQL Server en Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

3. Una vez conectado a uno o más orígenes de datos, puede que quiera transformar los datos para que le resulten útiles.

## <a name="transform-and-clean-data-create-a-model"></a>Transformación y limpieza de datos y creación de un modelo

En Power BI Desktop, puede limpiar y transformar los datos con el [Editor de Power Query](https://docs.microsoft.com/power-bi/desktop-query-overview) integrado. Con el Editor de Power Query, puede realizar modificaciones en los datos, como cambiar un tipo de datos, quitar columnas o combinar datos de varios orígenes. Es como esculpir: se empieza con un gran bloque de barro (o datos), luego se quitan trozos o se agregan otros según sea necesario, hasta que los datos adoptan la forma deseada. 

Para iniciar el Editor de Power Query:

- Seleccione **Editar consultas** > **Editar consultas** en la cinta **Inicio**.

   Aparece la ventana **Editor de Power Query**.

   ![Editor de Power Query de Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Cada paso que se da para transformar datos (como cambiar el nombre de una tabla, transformar un tipo de datos o eliminar una columna) se registra con el Editor de Power Query. Cada vez que esta consulta se conecta al origen de datos, se ejecutan esos pasos de modo que los datos siempre tengan la forma especificada.

En la imagen siguiente se muestra la ventana **Editor de Power Query** de una consulta a la que se ha dado forma y se ha convertido en un modelo.

 ![Ventana Editor de Power Query](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Una vez que los datos tienen la forma deseada, puede crear objetos viduales. 

## <a name="create-visuals"></a>Creación de objetos visuales 

Una vez que se tiene un modelo de datos, se pueden arrastrar *campos* al lienzo del informe para crear *objetos visuales*. Un objeto visual es una representación gráfica de los datos del modelo. Hay muchos tipos diferentes de objetos visuales entre los que elegir en Power BI Desktop. En el siguiente objeto visual se muestra un gráfico de columna simple. 

![Un objeto visual en Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

Para crear o cambiar un objeto visual: 

- En el panel **Visualizaciones**, seleccione el icono del objeto visual. 

   ![Panel Visualizaciones de Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

   Si ya tiene un objeto visual seleccionado en el lienzo del informe, cambia al tipo seleccionado. 

   Si no hay ningún objeto visual seleccionado en el lienzo, se crea un nuevo objeto visual en función de la selección.


## <a name="create-reports"></a>Crear informes

Lo más frecuente es que quiera crear una colección de objetos visuales que muestre diversos aspectos de los datos usados para crear el modelo en Power BI Desktop. A una colección de objetos visuales, en un archivo de Power BI Desktop, se le denomina *informe*. Un informe puede tener una o varias páginas, al igual que un archivo de Excel puede tener uno o varias hojas de cálculo. 

Con Power BI Desktop, puede crear informes complejos y de gran riqueza visual mediante los datos de varios orígenes, todo en un informe que se puede compartir con otros usuarios de la organización.

En la siguiente imagen se ve la primera página de un informe de Power BI Desktop denominado **Información general**, como se observa en la pestaña situada en la parte inferior de la imagen. 

![Informe de ejemplo de Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Compartir informes

Una vez que está listo para compartir con otras personas, puede *publicar* el informe en el servicio Power BI y ponerlo a disposición de cualquier persona de la organización que tenga una licencia de Power BI. 

Para publicar un informe de Power BI Desktop: 

1. Seleccione **Publicar** en la cinta **Inicio**.

   ![Publicación de un informe desde Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

   Power BI Desktop se conecta al servicio Power BI con la cuenta de Power BI. 

2. Power BI le pide que seleccione la ubicación del servicio Power BI donde quiere compartir el informe, como el área de trabajo propia, un área de trabajo de equipo o alguna otra ubicación del servicio Power BI. 

   Debe tener una licencia de Power BI para compartir informes en el servicio Power BI.


## <a name="next-steps"></a>Pasos siguientes

Para empezar a trabajar con Power BI Desktop, lo primero que necesita es descargar e instalar la aplicación. Hay dos maneras de obtener Power BI Desktop:

* [Obtener Power BI Desktop de Microsoft Store](https://aka.ms/pbidesktopstore)
* [Descargar Power BI Desktop desde la Web](https://docs.microsoft.com/power-bi/desktop-get-the-desktop#download-power-bi-desktop-directly)

