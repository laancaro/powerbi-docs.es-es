---
title: Conexión a IntelliBoard con Power BI
description: IntelliBoard para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: c397ec0f302ec558e0277c92a871a94dd7f28e87
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Conexión a IntelliBoard con Power BI
IntelliBoard ofrece acceso simplificado a los datos del sistema de administración de aprendizaje Moodle mediante los servicios de informes. El paquete de contenido de IntelliBoard para Power BI ofrece análisis adicional, incluidas las métricas de sus cursos, los usuarios registrados, el rendimiento general y la actividad LMS.

Conéctese al [paquete de contenido de IntelliBoard](https://app.powerbi.com/getdata/services/intelliboard) para Power BI.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. En el cuadro **Servicios** , seleccione **Obtener**.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Seleccione **IntelliBoard** y, a continuación, **Conectar**.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Seleccione **OAuth 2** y, a continuación, **Iniciar sesión**. Cuando se le solicite, proporcione las credenciales de IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. Una vez conectado, se cargarán automáticamente un panel, un informe y un conjunto de datos. Una vez completado, los mosaicos se actualizarán con los datos de su cuenta de IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](power-bi-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](service-dashboard-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o actualizarlo a petición mediante **Actualizar ahora**.

## <a name="whats-included"></a>Qué se incluye
El paquete de contenido incluye datos de las tablas siguientes:  

    - Activity (Actividad)  
    - Agents (Agentes)  
    - Auth (Autor)  
    - Países  
    - CoursesProgress (Progreso de cursos)  
    - Enrollments (Inscripciones)
    - Lang (Idioma)  
    - Platform (Plataforma)  
    - Totals (Totales)  
    - UsersProgress (Progreso de usuarios)    

## <a name="system-requirements"></a>Requisitos del sistema
Se requiere una cuenta de IntelliBoard con permisos para las tablas anteriores para crear una instancia de este paquete de contenido.

## <a name="next-steps"></a>Pasos siguientes
[Introducción a Power BI](service-get-started.md)

[Power BI: Conceptos básicos](service-basic-concepts.md)

