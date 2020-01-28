---
title: Cambio de cadenas de conexión de origen de datos con PowerShell
description: 'Cambio de cadenas de conexión de origen de datos mediante API en PowerShell: Power BI Report Server.'
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2019
ms.author: maggies
ms.openlocfilehash: 5cdf29c71ef3e5f8dc02799945cf76ccc518dabe
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953749"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Cambio de cadenas de conexión de origen de datos en informes de Power BI con PowerShell: Power BI Report Server


Puede cambiar las cadenas de conexión de origen de datos en informes de Power BI en Power BI Report Server mediante API en PowerShell. 

> [!NOTE]
> Actualmente, esta funcionalidad solo funciona para DirectQuery. La compatibilidad con la importación y la actualización de datos estará disponible próximamente.

1. Instale los commandlets de PowerShell de Power BI Report Server. Busque los commandlets y las instrucciones de instalación en [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

2. Capture la información del origen de datos existente para el archivo de Power BI a través de commandlets de PowerShell:

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Para ver información del primer origen de datos contenido en el informe de Power BI: 

    ```powershell
    $dataSources[0]
    ```

3. Actualice la información de conexión y las credenciales según sea necesario. Si al actualizar la cadena de conexión y el origen de datos se usan las credenciales almacenadas, debe proporcionar la contraseña de la cuenta. 

    Para actualizar una cadena de conexión de origen de datos:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Para cambiar el tipo de credencial del origen de datos:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    Para cambiar el nombre de usuario y la contraseña del origen de datos:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Vuelva a guardar las credenciales actualizadas en el servidor.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Pasos siguientes

[Orígenes de datos de informes paginados en Power BI Report Server](connect-data-sources.md) 

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
