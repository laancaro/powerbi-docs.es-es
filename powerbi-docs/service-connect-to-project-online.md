---
title: Conexión a Project Online con Power BI
description: Project Online para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a6ada87813593fd0f06d7870fa1727bc35fe7d47
ms.sourcegitcommit: fe8a25a79f7c6fe794d1a30224741e5281e82357
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68324929"
---
# <a name="connect-to-project-web-app-with-power-bi"></a>Conexión a Project Web App con Power BI
Microsoft Project Web App es una solución flexible en línea para la administración de cartera de proyectos (PPM) y el trabajo diario. Project Web App permite a las organizaciones dar el primer paso, priorizar las inversiones de la cartera de proyectos y ofrecer el valor empresarial previsto. La aplicación de plantilla Project Web App para Power BI permite desbloquear información de Project Web App para facilitar la administración de proyectos, carteras y recursos.

Conéctese a la [aplicación de plantilla de Project Web App](https://appsource.microsoft.com/product/power-bi/pbi_msprojectonline.pbi-microsoftprojectwebapp) para Power BI.

## <a name="how-to-connect"></a>Cómo conectarse

   ![](media/service-connect-to-project-online/GetApps.png)
1. Seleccione **Aplicaciones** en el panel de navegación de la izquierda > seleccione **Obtener aplicaciones** en la esquina superior derecha.
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![](media/service-connect-to-project-online/AppSource.png)
3. En AppSource, seleccione la pestaña **Aplicaciones** y busque o seleccione **Microsoft Project Web App**.
   
4. Recibirá un mensaje que dice: **¿Quiere instalar esta aplicación de Power BI?** ; seleccione **Instalar**. 

   ![](media/service-connect-to-project-online/ProjectTile.png)
5. En el panel **Aplicaciones**, seleccione el icono **Microsoft Project Web App**. 
   
   ![](media/service-connect-to-project-online/getstarted.png)
6. En **Empezar a trabajar con la nueva aplicación**, seleccione **Conectar datos**.
   
   ![](media/service-connect-to-project-online/mproject.png)
7. En el cuadro de texto **Dirección URL de Project Web App**, escriba la dirección URL de Project Web App (PWA) a la que quiera conectarse.  Tenga en cuenta que puede diferir del ejemplo si tiene un dominio personalizado. En el cuadro de texto **Idioma del sitio de Project Web App**, escriba el número correspondiente a su idioma del sitio de Project Web App. Escriba "1" para inglés, "2" para francés, "3" para alemán, "4" para portugués (Brasil), "5" para portugués (Portugal) y "6" para español. 
   
   ![](media/service-connect-to-project-online/params.png)
8. En Método de autenticación, seleccione **oAuth2** \> **Iniciar sesión**. Cuando se le solicite, escriba las credenciales de Project Web App y siga el proceso de autenticación.

    
Tenga en cuenta que debe tener los permisos de Visor de carteras, Administrador de carteras o Administrador para la instancia de Project Web App a la que se está conectando.

9. Verá una notificación que indica que se están cargando los datos. Dependiendo del tamaño de la cuenta, puede tardar cierto tiempo. Después de que Power BI importe los datos, verá el contenido de la nueva área de trabajo. Es posible que tenga que actualizar el conjunto de datos para obtener las actualizaciones más recientes. 

Una vez que Power BI importe los datos, verá el informe con 13 páginas y el conjunto de datos en el panel de navegación de la izquierda. 

10. Cuando los informes estén listos, continúe y empiece a explorar los datos de Project Web App. La aplicación de plantilla incluye 13 informes muy completos y detallados con información general sobre carteras (6 páginas de informe), información general sobre recursos (5 páginas de informe) y el estado del proyecto (2 páginas de informe). 

   ![](media/service-connect-to-project-online/report1.png)
   
   ![](media/service-connect-to-project-online/report3.png)
   
   ![](media/service-connect-to-project-online/report2.png)

**¿Qué más?**

* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

**Expansión de la aplicación de plantilla**

Descargue el [archivo PBIT de GitHub](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) para seguir personalizando y actualizando el paquete de contenido.

## <a name="next-steps"></a>Pasos siguientes
[Introducción a Power BI](service-get-started.md)

[Obtener datos en Power BI](service-get-data.md)

