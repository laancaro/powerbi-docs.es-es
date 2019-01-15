---
title: Orígenes de datos insertados para informes paginados en el servicio Power BI (versión preliminar)
description: En este artículo, obtendrá información sobre cómo crear y modificar un origen de datos insertado en un informe paginado en el servicio Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: d768edbbc57e52186fdb33e1aed9a3da76408963
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275603"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service-preview"></a>Creación de un origen de datos insertado para informes paginados en el servicio Power BI (versión preliminar)
En este artículo, obtendrá información sobre cómo crear y modificar un origen de datos insertado en un informe paginado en el servicio Power BI. Defina un origen de datos insertado en un único informe y úselo solo en dicho informe. Actualmente, los informes paginados que se publican en el servicio Power BI necesitan conjuntos de datos insertados y orígenes de datos insertados, y se pueden conectar a estos orígenes de datos:

- Azure SQL Database y Data Warehouse
- SQL Server
- SQL Server Analysis Services 

Los informes paginados se conectan a orígenes de datos locales mediante una puerta de enlace. Configure la puerta de enlace después de publicar el informe en el servicio Power BI. Obtenga más información sobre las [puertas de enlace de Power BI](service-gateway-getting-started.md). 

## <a name="create-an-embedded-data-source"></a>Creación de un origen de datos insertados
  
1. Abra el generador de informes.

1. En la barra de herramientas del panel Datos de informe, seleccione **Nuevo** > **Orígenes de datos**. Se abre el cuadro de diálogo **Propiedades del origen de datos**.

    ![Nuevo origen de datos](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
2.  En el cuadro de texto **Nombre**, escriba un nombre para el origen de datos o acepte el valor predeterminado.  
  
3.  Seleccione **Usar una conexión incrustada en el informe**.  
  
1.  En la lista **Seleccionar el tipo de conexión**, seleccione un tipo de origen de datos. 

1.  Especifique una cadena de conexión con el uso de alguno de estos métodos:  
  
    -   Escriba la cadena de conexión directamente en el cuadro de texto **Cadena de conexión**. 
  
    -   Seleccione el botón de expresión (**fx)** para crear una expresión que se evalúa como una cadena de conexión. En el cuadro de diálogo **Expresión**, escriba la expresión en el panel Expresión. Seleccione **Aceptar**. 
  
    -   Seleccione **Compilar** para abrir el cuadro de diálogo **Propiedades de conexión** para el origen de datos elegido en el paso 2.  
  
        Rellene los campos del cuadro de diálogo **Propiedades de conexión** según corresponda para el tipo de origen de datos. Las propiedades de conexión incluyen el tipo de origen de datos, el nombre del origen de datos y las credenciales que se van a usar. Después de especificar los valores de este cuadro de diálogo, seleccione **Probar conexión** para comprobar que el origen de datos está disponible y que las credenciales que especificó son correctas.  
  
4.  Seleccione  **Credenciales**.  
  
     Especifique las credenciales que se usarán para este origen de datos. El propietario del origen de datos elige el tipo de credenciales que se admite. Para más información, vea [Especificar información de credenciales y conexión para los orígenes de datos de informes](https://docs.microsoft.com/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources).
  
5.  Seleccione **Aceptar**.  
  
     El origen de datos aparece en el panel Datos de informe.  

## <a name="next-steps"></a>Pasos siguientes

- [Creación de un conjunto de datos insertado para un informe paginado en el servicio Power BI](paginated-reports-create-embedded-dataset.md)
- [¿Qué son los informes paginados en Power BI Premium? (versión preliminar)](paginated-reports-report-builder-power-bi.md)