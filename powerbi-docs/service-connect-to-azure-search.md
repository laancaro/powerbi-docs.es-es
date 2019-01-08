---
title: Conexión a Azure Search con Power BI
description: Azure Search para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: c6794fd08255dc3d63381549e7ee068631d49697
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008957"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Conexión a Azure Search con Power BI
Azure Search Traffic Analytics permite supervisar y comprender el tráfico al servicio Azure Search. El paquete de contenido de Azure Search para Power BI proporciona información detallada sobre los datos de búsqueda, que incluye la búsqueda, la indexación, las estadísticas del servicio y la latencia de los últimos 30 días. Puede encontrar más detalles en la [entrada de blog de Azure](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

Conéctese al [paquete de contenido de Azure Search](https://app.powerbi.com/getdata/services/azure-search) para Power BI.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Seleccione **Azure Search**\>**Obtener**.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Proporcione el nombre de la cuenta de Table Storage donde está almacenado el análisis de Azure Search.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Seleccione **Clave** como mecanismo de autenticación y proporcione la clave de cuenta de almacenamiento. Haga clic en **Iniciar sesión** e inicie el proceso de carga.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Cuando se complete la carga, aparecerán un nuevo panel, un informe y un modelo en el panel de navegación. Seleccione el panel para ver los datos importados.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](consumer/end-user-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

## <a name="system-requirements"></a>Requisitos del sistema
El paquete de contenido de Azure Search requiere que Azure Search Traffic Analytics esté habilitado en la cuenta.

## <a name="troubleshooting"></a>Solución de problemas
Asegúrese de que el nombre de la cuenta de almacenamiento esté correctamente indicada junto con la clave de acceso completa. El nombre de la cuenta de almacenamiento debe corresponder a la cuenta configurada con Azure Search Traffic Analytics.

## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](power-bi-overview.md)

[Power BI: Conceptos básicos](consumer/end-user-basic-concepts.md)

