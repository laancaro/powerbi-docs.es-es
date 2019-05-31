---
title: 'Tutorial: Conectarse a un repositorio de GitHub con Power BI'
description: En este tutorial, nos conectaremos a datos reales en el servicio de GitHub con Power BI. Power BI creará automáticamente paneles e informes.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578620"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Tutorial: Conectarse a un repositorio de GitHub con Power BI
En este tutorial, nos conectaremos a datos reales en el servicio de GitHub con Power BI. Power BI creará automáticamente paneles e informes. Conecta con el repositorio público de contenido de Power BI (también conocido como un *repositorio*) y obtener respuestas a preguntas como: ¿Cuántas personas contribuyen al contenido público de Power BI? ¿Quiénes contribuyen en mayor medida? ¿Qué día de la semana ha habido más contribuciones? Y otras preguntas. 

![Informe de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

En este tutorial, realizaremos los siguientes pasos:

> [!div class="checklist"]
> * Registrar una cuenta de GitHub, si aún no hay una 
> * Iniciar sesión en la cuenta de Power BI (o registrar una, si aún no la hay)
> * Abrir el servicio Power BI
> * Buscar la aplicación de GitHub
> * Indicar la información del repositorio de GitHub público de Power BI
> * Ver el panel y el informe con datos de GitHub
> * Eliminar la aplicación limpiando los recursos

Si no está registrado en Power BI, [regístrese para obtener una evaluación gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, se necesita una cuenta de GitHub, si aún no tiene una. 

- Registrarse para obtener un [cuenta de GitHub](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Cómo conectarse
1. Inicie sesión en el servicio Power BI (https://app.powerbi.com)). 
2. En el panel de navegación izquierdo, seleccione **Aplicaciones** y, después, **Obtener aplicaciones**.
   
   ![Obtener aplicaciones en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Seleccione **aplicaciones**, tipo **GitHub** en el cuadro de búsqueda > **obtenerla ahora**.
   
   ![Obtener GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. En **instalar esta aplicación de Power BI?** seleccione **instalar**.
5. En **está lista la nueva aplicación**, seleccione **ir a la aplicación**.
6. En **empezar a trabajar con la nueva aplicación**, seleccione **conectar datos**.

    ![Empezar a trabajar con la nueva aplicación](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. Escriba el nombre del repositorio y el propietario del repositorio. La dirección URL de este repositorio es https://github.com/MicrosoftDocs/powerbi-docs, por lo que **Propietario del repositorio** es **MicrosoftDocs** y **Repositorio**, **powerbi-docs**. 
   
    ![Nombre del repositorio de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Escriba las credenciales de GitHub que ha creado. Puede que Power BI omita este paso si ya ha iniciado sesión en GitHub en el explorador. 

6. Para **método de autenticación**, mantener **oAuth2** seleccionado \> **sesión**.

7. Siga las pantallas de autenticación de GitHub. Conceda permisos de Power BI a los datos de GitHub.
   
   Ahora, Power BI se puede conectar a GitHub y a los datos.  Los datos se actualizan una vez al día.

8. Una vez que Power BI importe los datos, vea el contenido de la nueva área de trabajo de GitHub. 
9. En la barra de navegación izquierdo, seleccione la flecha situada junto al nombre del área de trabajo. Verá que el área de trabajo contiene un panel y un informe. 

    ![Aplicación en el panel de navegación izquierdo](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Seleccione los puntos suspensivos (...) junto al nombre del panel > **cambiar el nombre de** > tipo **panel de GitHub**.
 
    ![Icono de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Haga clic en el icono de navegación global para minimizar la navegación de la izquierda y, así, disponer de más espacio.

    ![Icono de navegación global](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Seleccione el panel de GitHub.
    
    El panel de GitHub contiene datos activos, por lo que los valores que aparecen pueden ser diferentes.

    ![Panel de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Hacer una pregunta

1. Coloque el cursor en **formular una pregunta acerca de los datos**. Power BI ofrece **preguntas para empezar**. 

1. Seleccione **son de cuántos usuarios hay**.
 
    ![Son de cuántos usuarios hay](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Entre ellos **cuántos** y **se encuentran los usuarios**, tipo **extraer solicitudes por**. 

     Power BI crea un gráfico de barras que muestra el número de solicitudes de incorporación de cambios por persona.

    ![¿Existen cuántas solicitudes de incorporación de cambios por usuario](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Seleccione el pin para anclarlo al panel, a continuación, **salir de preguntas y respuestas**.

## <a name="view-the-github-report"></a>Ver el informe de GitHub 

1. En el panel de GitHub, seleccione el gráfico de columnas **las solicitudes de incorporación de cambios por mes** para abrir el informe relacionado.

    ![Solicitudes de incorporación de cambios mediante el gráfico de columna del mes](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Seleccione un nombre de usuario en el **solicitudes de extracción Total por usuario** gráfico. En este ejemplo, vemos que la mayoría de sus horas eran en febrero.

    ![Resaltado del informe de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Seleccione la pestaña **Tarjeta perforada** para ver la siguiente página en el informe. 
 
    ![Tarjeta perforada del informe de GitHub en Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Aparentemente los martes a las 3 p.m. es el mejor momento y el día de la semana para *confirma*, cuando las personas del repositorio en su trabajo.

## <a name="clean-up-resources"></a>Limpieza de recursos

Ahora que ya hemos finalizado el tutorial, podemos eliminar la aplicación de GitHub. 

1. Seleccione **Aplicaciones** en la barra de navegación izquierda.
2. Mantenga el puntero sobre el icono de GitHub y seleccione la papelera (**Eliminar**).

    ![Eliminar la aplicación de GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, nos hemos conectado a un repositorio público de GitHub y hemos obtenido datos, a los que Power BI ha dado formato de panel y de informe. Explorando ese panel y ese informe, hemos hallado respuesta a algunas preguntas sobre los datos. Ahora podemos pasar a obtener más información sobre cómo conectarnos a otros servicios, como Salesforce, Microsoft Dynamics y Google Analytics. 
 
> [!div class="nextstepaction"]
> [Conexión a los servicios que usa](service-connect-to-services.md)


