---
title: Conectarse a una base de datos de Oracle
description: Pasos y descargas que se necesitan para conectar Oracle a Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7c91095cf321fed56a0cb1c3c6bd1113f380a524
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878505"
---
# <a name="connect-to-an-oracle-database"></a>Conectarse a una base de datos de Oracle
Para conectarse a una base de datos de Oracle con **Power BI Desktop**, el software cliente de Oracle correcto debe estar instalado en el equipo donde se ejecuta Power BI Desktop. El software cliente de Oracle que usa depende de la versión que Power BI Desktop que tiene instalada: puede ser la versión de **32 bits** o la de **64 bits**.

**Versiones compatibles**: Oracle 9 y versiones posteriores, software cliente de Oracle 8.1.7 y versiones posteriores.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinación de versión instalada de Power BI Desktop
Para determinar la versión de Power BI Desktop instalada, seleccione **Archivo > Ayuda > Acerca de** y, luego, revise la línea **Versión:** . En la siguiente imagen, hay instalada una versión de 64 bits de Power BI Desktop:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Instalación del cliente de Oracle
En el caso de las versiones de **32 bits** de Power BI Desktop, use el vínculo siguiente para descargar e instalar el cliente de **32 bits** de Oracle:

* [Oracle Data Access Components (ODAC) de 32 bits con Oracle Developer Tools para Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

En el caso de las versiones de **64 bits** de Power BI Desktop, use el vínculo siguiente para descargar e instalar el cliente de **64 bits** de Oracle:

* [ODAC 12c versión 4 (12.1.0.2.4) de 64 bits para Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Conectarse a una base de datos de Oracle
Una vez que instale el controlador cliente de Oracle que corresponda, puede conectarse a una base de datos de Oracle. Siga estos pasos para establecer la conexión:

1. En la ventana Obtener datos, seleccione **Base de datos > Base de datos de Oracle**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. En el cuadro de diálogo **Base de datos de Oracle** que aparece, proporcione el nombre del servidor y, luego, seleccione **Conectar**. Si es necesario un SID, puede especificarlo con el formato siguiente: *NombreServidor/SID*, donde SID es el nombre único de la base de datos. Si el formato *NombreServidor/SID* no funciona, pruebe a usar *NombreServidor/NombreServicio*, donde NombreServicio es el alias que se usa al conectarse.


   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Si tiene problemas para conectarse en este paso, pruebe a usar el siguiente formato en el campo Nombre del servidor: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))
   
3. Si quiere importar datos con una consulta de base de datos nativa, puede ingresar la consulta en el cuadro **Instrucción SQL**, que está disponible si se expande la sección **Opciones avanzadas** del cuadro de diálogo **Base de datos de Oracle**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Una vez que escriba la información de la base de datos de Oracle en el cuadro de diálogo Base de datos de Oracle (incluida toda información opcional, como un SID o una consulta de base de datos nativa), seleccione **Aceptar** para conectarse.
5. Si la base de datos de Oracle necesita credenciales del usuario de la base de datos, ingréselas en el cuadro de diálogo cuando se le solicite hacerlo.


## <a name="troubleshooting"></a>Solución de problemas

Si ha descargado Power BI Desktop desde Microsoft Store, es posible que no pueda conectarse a bases de datos de Oracle debido a un problema con el controlador de Oracle. En tal caso, recibirá el mensaje de error "No se ha configurado la referencia del objeto". Para solucionarlo, realice una de las siguientes acciones:

* Descargue Power BI Desktop desde https://powerbi.microsoft.com/desktop.

* Para usar la versión disponible en Microsoft Store, copie el archivo oraons.dll que encontrará en _12.X.X\client_X_ en _12.X.X\client_X\bin_, en su equipo local. La X representa el directorio y los números de versión.

Si se muestra el mensaje *Referencia de objeto no establecida* en Power BI Gateway al conectarse a una base de datos de Oracle, es posible que pueda resolver el problema siguiendo las instrucciones que se encuentran en el artículo [Administrar el origen de datos: Oracle](service-gateway-onprem-manage-oracle.md).
