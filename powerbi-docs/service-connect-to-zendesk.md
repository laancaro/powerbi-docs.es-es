---
title: Conexión a Zendesk con Power BI
description: Zendesk para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: afcaae9499aa1c7e1461030cfa6b5d7b35a47188
ms.sourcegitcommit: e8d924ca25e060f2e1bc753e8e762b88066a0344
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37136028"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Conexión a Zendesk con Power BI
El paquete de contenido de Zendesk ofrece un panel de Power BI y un conjunto de informes de Power BI que proporcionan información acerca de los volúmenes de vales y el rendimiento del agente. Puede usar el panel y los informes proporcionados, o bien personalizarlos para resaltar la información que más le interesa.  Los datos se actualizarán automáticamente una vez al día. 

Conéctese al [paquete de contenido de Zendesk](https://app.powerbi.com/getdata/services/zendesk) o lea más sobre la [integración de Zendesk ](https://powerbi.microsoft.com/integrations/zendesk)con Power BI.

>[!NOTE]
>Se necesita una cuenta de administrador de Zendesk para conectarse. Consulte más detalles sobre los [requisitos](#Requirements) a continuación.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.
   
   ![](media/service-connect-to-zendesk/pbi_getdata.png)
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![](media/service-connect-to-zendesk/pbi_getservices.png) 
3. Seleccione **Zendesk** \> **Obtener.**
   
   ![](media/service-connect-to-zendesk/zendesk.png)
4. Proporcione la dirección URL asociada a su cuenta. Esta tendrá el formato **https://company.zendesk.com**. Vea los detalles sobre cómo [buscar estos parámetros](#FindingParams) a continuación.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskconnect.png)
5. Cuando se le solicite, escriba sus credenciales de Zendesk.  Seleccione **oAuth 2** como el mecanismo de autenticación y haga clic en **Iniciar sesión**. Siga el flujo de autenticación de Zendesk. (Si ya inició sesión en Zendesk con el explorador, no se le solicitarán las credenciales).
   
   > [!NOTE]
   > Este paquete de contenido requiere conectarse con una cuenta de administrador de Zendesk. 
   > 
   > 
   
   ![](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Haga clic en **Permitir** para permitir que Power BI tenga acceso a los datos de Zendesk.
   
   ![](media/service-connect-to-zendesk/zendesk2.jpg)
7. Haga clic en **Conectar** para comenzar el proceso de importación. Una vez que Power BI importe los datos, verá un nuevo panel, el informe y el conjunto de datos en el panel de navegación izquierdo. Los nuevos elementos se marcan con un asterisco amarillo \*.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskdash.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](power-bi-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](service-dashboard-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o actualizarlo a petición mediante **Actualizar ahora**.

## <a name="whats-included"></a>Qué se incluye
El paquete de contenido de Power BI incluye datos sobre lo siguiente:  

* Usuarios (usuarios finales y agentes)  
* Organizaciones  
* Grupos  
* Vales  

También existe un conjunto de medidas calculadas, como el promedio de tiempo de espera y los vales resueltos en los últimos 7 días. Se incluye una lista completa en el paquete de contenido.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Requisitos del sistema
Se necesita una cuenta de administrador de Zendesk para acceder al paquete de contenido de Zendesk. Si es un agente o un usuario final y está interesado en ver sus datos de Zendesk, agregue una sugerencia y revise el conector de Zendesk en [Power BI Desktop](desktop-connect-to-data.md).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Búsqueda de parámetros
La dirección URL de Zendesk coincidirá con la dirección URL que usa para iniciar sesión en su cuenta de Zendesk. Si no está seguro de su dirección URL de Zendesk, puede usar la [ayuda de inicio de sesión](https://www.zendesk.com/login/) de Zendesk.

## <a name="troubleshooting"></a>Solución de problemas
Si tiene problemas para conectarse, compruebe la dirección URL de Zendesk y confirme que está usando una cuenta de administrador de Zendesk.

## <a name="next-steps"></a>Pasos siguientes
* [¿Qué es Power BI?](power-bi-overview.md)
* [Obtener datos](service-get-data.md)

