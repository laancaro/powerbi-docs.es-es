---
title: Introducción al servicio Power BI
description: Introducción al servicio Power BI en línea (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 007819ead82f558efa8179a49dfba9454558dfbb
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995200"
---
# <a name="tutorial-get-started-with-the-power-bi-service-apppowerbicom"></a>Tutorial: Introducción al servicio Power BI (app.powerbi.com)
Este tutorial le ayudará a empezar a trabajar con el *servicio Power BI*. Para entender cómo encaja el servicio Power BI con otras ofertas de Power BI, le recomendamos que primero lea [¿Qué es Power BI?](power-bi-overview.md).

![Relación entre Power BI Desktop, el servicio y la aplicación móvil](media/service-get-started/power-bi-components.png)

En este tutorial, realizaremos los siguientes pasos:

> [!div class="checklist"]
> * Buscar contenidos de introducción para el servicio Power BI.
> * Iniciar sesión en la cuenta de Power BI en línea (o bien registrarse, si todavía no tiene una).
> * Abrir el servicio Power BI.
> * Obtener algunos datos y abrirlos en la vista de informe.
> * Usar esos datos para crear visualizaciones y guardarlos como un informe.
> * Crear un panel anclando iconos desde el informe.
> * Agregar otra visualización al panel mediante la herramienta de lenguaje natural Preguntas y respuestas.
> * Limpiar los recursos mediante la eliminación del conjunto de datos, el informe y el panel.

## <a name="sign-up-for-the-power-bi-service"></a>Suscribirse al servicio Power BI
Si no tiene una cuenta de Power BI, [regístrese para obtener una versión de prueba gratuita de Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web) antes de empezar.

Después de conseguir una cuenta, escriba *app.powerbi.com* en el explorador para abrir el servicio Power BI. 

Si quiere obtener ayuda para Power BI Desktop, consulte [Introducción a Power BI Desktop](desktop-getting-started.md). Si desea obtener ayuda con Power BI en el móvil, consulte [Aplicaciones de Power BI para dispositivos móviles](consumer/mobile/mobile-apps-for-mobile-devices.md).

> [!TIP]
> ¿Prefiere un curso autodidáctico? [Inscríbase en el curso sobre análisis y visualización de datos en EdX](http://aka.ms/edxpbi).

Visite nuestra [lista de reproducción en YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). Aquí tiene un vídeo que le resultará útil para empezar con el servicio Power BI:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-the-power-bi-service"></a>¿Qué es el servicio Power BI?
Para hacer referencia al servicio Microsoft Power BI en ocasiones se usa el término Power BI en línea o, simplemente, la URL (app.powerbi.com). Power BI es un servicio que le permite a mantenerse al día con la información más importante para usted. Además, los *paneles* del servicio Power BI le ayudan a tomar el pulso de su empresa. Los paneles muestran *iconos*, que puede seleccionar para abrir *informes* y seguir explorando. Conéctese a varios *conjuntos de datos* para reunir todos los datos relevantes en un solo lugar. ¿Necesita ayuda para comprender los bloques de creación que conforman Power BI? Vea [Conceptos básicos para los diseñadores en el servicio Power BI](service-basic-concepts.md).

Si tiene datos importantes en archivos de Excel o CSV, puede crear un panel de Power BI para mantenerse informado en cualquier lugar y compartir recomendaciones con otros usuarios.  ¿Tiene una suscripción a una aplicación de SaaS como Salesforce?  Arranque con ventaja conectándose a Salesforce para crear automáticamente un panel a partir de los datos, o bien [compruebe todas las demás aplicaciones de SaaS](service-get-data.md) a las que pueda conectarse. Si forma parte de una organización, vea si se ha publicado alguna [aplicación](service-create-distribute-apps.md) para usted.

Obtenga información sobre todas las demás formas de [obtener datos para Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Paso 1: Obtener datos
Este es un ejemplo de obtención de datos de un archivo CSV. ¿Desea seguir este tutorial? [Descarga del archivo CSV de ejemplos financieros](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Inicie sesión en Power BI](http://www.powerbi.com/). ¿No tiene una cuenta? No se preocupe, puede registrarse para obtener una versión de prueba gratuita.
2. Power BI se abre en el explorador. Seleccione **Obtener datos** en la parte inferior de la barra de navegación de la izquierda.

    Se abre la página **Obtener datos**.   

3. En la sección **Crear contenido**, seleccione **Archivos**. 
   
   ![Obtención de archivos](media/service-get-started/gs1.png)
4.  Seleccione **Archivo local**.
   
     ![Pantalla Obtener datos > Archivos](media/service-get-started/gs2.png)

5. Busque el archivo en el equipo y elija **Abrir**.

5. En este tutorial, se seleccionará **Importar** para agregar el archivo Excel como un conjunto de datos, que después se puede usar para crear informes y paneles. Si selecciona **Cargar**, se carga todo el libro de Excel en Power BI, donde lo puede abrir y editar en Excel en línea.
   
   ![Selección de Importar](media/service-get-started/power-bi-import.png)
6. Una vez preparado el conjunto de datos, seleccione **Ver conjunto de datos** para abrirlo en el editor de informes. 

    ![Cuadro de diálogo Su conjunto de datos está listo](media/service-get-started/power-bi-gs.png)

    Como todavía no se ha creado ninguna visualización, el lienzo del informe está en blanco.

    ![Lienzo de informe en blanco](media/service-get-started/power-bi-report-editor.png)

7. Observe que en la barra de navegación superior hay una opción **Vista de lectura**. Como tiene esta opción, significa que actualmente se encuentra en la vista de edición. 

    ![Opción Vista de lectura](media/service-get-started/power-bi-editing-view.png)

    En la vista de edición puede crear y modificar los informes, ya que es el *propietario* del informe. Es decir, es un *creador*. Cuando comparte el informe con compañeros de trabajo, ellos solo pueden interactuar con el informe en la vista de lectura; son los *consumidores*. Obtenga más información sobre la [vista de lectura y de edición](consumer/end-user-reading-view.md).
    
    Una excelente manera de familiarizarse con el editor de informes es [dar un paseo](service-the-report-editor-take-a-tour.md).
 

## <a name="step-2-start-exploring-your-dataset"></a>Paso 2: Empezar a explorar el conjunto de datos
Ahora que se ha conectado a los datos, empiece a explorar.  Cuando encuentre algo interesante, puede crear un panel para supervisarlo y ver cómo cambia con el tiempo. Veamos cómo funciona eso.
    
1. En el editor de informes, use el panel **Campos** situado en el lado derecho de la página para crear una visualización. Seleccione las casillas **Ventas brutas** y **Fecha**.
   
   ![Lista de campos](media/service-get-started/fields.png)

    Power BI analiza los datos y crea una visualización. Si primero ha seleccionado **Fecha**, verá una tabla. Si primero ha seleccionado **Ventas brutas**, verá un gráfico. 

2. Cambie a una forma diferente de mostrar los datos. Veamos estos datos como un gráfico de líneas. En el panel **Visualizaciones**, seleccione el icono de gráfico de líneas.
   
   ![Editor de informes con el gráfico de líneas seleccionado](media/service-get-started/gettingstart5new.png)

3. Este gráfico parece interesante, así que lo vamos a *anclar* a un panel. Mantenga el mouse sobre la visualización y seleccione el icono Anclar. Al anclar esta visualización, se almacena en el panel y se mantiene actualizada para que pueda comprobar el valor más reciente de un vistazo.
   
   ![Icono de anclaje](media/service-get-started/pinnew.png)

4. Como se trata de un informe nuevo, se le pide que lo guarde antes de poder anclar una visualización a un panel. Asigne un nombre al informe (por ejemplo, *Ventas históricas*) y, después, seleccione **Guardar y continuar**. 
   
   ![Cuadro de diálogo Guardar informe](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. Ancle el gráfico de líneas al panel nuevo y asígnele el nombre *Ejemplo financiero para el tutorial*. 
   
   ![Asignación de un nombre para el informe](media/service-get-started/power-bi-pin.png)
   
6. Seleccione **Anclar**.
   
    Un mensaje de confirmación (junto a la esquina superior derecha) indica que la visualización se ha agregado al panel como un icono.
   
    ![Cuadro de diálogo Anclado al panel](media/service-get-started/power-bi-pin-success.png)

7. Seleccione **Ir al panel** para ver el gráfico de líneas que ha anclado como un icono al panel nuevo. Para mejorar el aspecto del panel aún más, agregue más iconos de visualización y [cambie el nombre o el tamaño, la vinculación y la posición de los iconos](service-dashboard-edit-tile.md).
   
   ![Panel con una visualización anclada](media/service-get-started/power-bi-new-dashboard.png)
   
8. Seleccione el nuevo icono en el panel para volver al informe. Power BI le devuelve al editor de informes en la vista de lectura. Para volver a la vista de edición, seleccione **Editar informe** en la barra de navegación superior. Una vez que esté en la vista de edición, puede seguir explorando y anclando iconos. 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>Paso 3:  Continuar la exploración con Preguntas y respuestas (consultas en lenguaje natural)
1. Para realizar una exploración rápida de los datos, formule una pregunta en el cuadro de Preguntas y respuestas. El cuadro de Preguntas y respuestas se encuentra en la parte superior del panel (**Pregunte algo sobre sus datos**) y en la barra de navegación superior del informe (**Hacer una pregunta**). Por ejemplo, escriba *qué segmento obtuvo más ingresos* en el cuadro Preguntas y respuestas.
   
   ![Lienzo Preguntas y respuestas](media/service-get-started/powerbi-qna.png)

2. Preguntas y respuestas busca una respuesta y la presenta en forma de una visualización. Seleccione el icono de anclaje ![Icono de anclaje](media/service-get-started/pbi_pinicon.png) para mostrar esta visualización en el panel.
3. Ancle la visualización al panel **Ejemplo financiero para el tutorial**.
   
    ![Cuadro de diálogo Anclar al panel](media/service-get-started/power-bi-pin2.png)

4. Vuelva al panel, donde verá el icono nuevo.

   ![Panel con el gráfico anclado](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>Limpieza de recursos
Ahora que ya hemos finalizado el tutorial, podemos eliminar el conjunto de datos, el informe y el panel. 

1. Seleccione **Mi área de trabajo** en la barra de navegación izquierda.
2. Seleccione la pestaña **Conjuntos de datos** y, luego, busque el conjunto de datos que ha importado en el tutorial.  
3. Seleccione el botón de puntos suspensivos (...) > **Eliminar**.

    ![Eliminación del conjunto de datos](media/service-get-started/power-bi-delete.jpg)

    Al eliminar el conjunto de datos, Power BI también elimina el informe y el panel. 


## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Conexión a los servicios en línea que usa con Power BI](service-connect-to-services.md)

