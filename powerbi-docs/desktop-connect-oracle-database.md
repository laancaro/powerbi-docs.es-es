---
title: Conectarse a una base de datos de Oracle
description: Pasos y descargas que se necesitan para conectar Oracle a Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c2290963db54f150eed8176c2820c59f8f138666
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223329"
---
# <a name="connect-to-an-oracle-database"></a>Conectarse a una base de datos de Oracle
Para conectarse a una base de datos de Oracle con Power BI Desktop, en el equipo donde se ejecute Power BI Desktop debe estar instalado el software cliente de Oracle correcto. El software cliente de Oracle que use depende de la versión que Power BI Desktop que haya instalado: 32 bits o 64 bits.

Versiones de Oracle compatibles: 
- Oracle 9 y versiones posteriores
- Software cliente de Oracle 8.1.7 y versiones posteriores

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinación de versión instalada de Power BI Desktop
Para determinar la versión de Power BI Desktop instalada, seleccione **Archivo** > **Ayuda** > **Acerca de** y, luego, revise la línea **Versión**. En la siguiente imagen, hay instalada una versión de 64 bits de Power BI Desktop:

![Versión de Power BI Desktop](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Instalación del cliente de Oracle
- Para la versión de 32 bits de Power BI Desktop, [descargue e instale el cliente de Oracle de 32 bits](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html).

- Para la versión de 64 bits de Power BI Desktop, [descargue e instale el cliente de Oracle de 64 bits](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html).

## <a name="connect-to-an-oracle-database"></a>Conectarse a una base de datos de Oracle
Después de instalar el controlador cliente de Oracle que corresponda, puede conectarse a una base de datos de Oracle. Siga estos pasos para establecer la conexión:

1. Desde la pestaña **Inicio**, seleccione **Obtener datos**. 

2. En la ventana **Obtener datos** que aparece, seleccione **Más** (si es necesario), seleccione **Base de datos** > **Base de datos de Oracle** y después **Conectar**.
   
   ![Conexión a la base de datos Oracle](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. En el cuadro de diálogo **Base de datos de Oracle** que aparece, proporcione el nombre del **servidor** y seleccione **Aceptar**. Si se requiere un SID, especifíquelo con el formato siguiente: *NombreDeServidor/SID*, donde *SID* es el nombre único de la base de datos. Si el formato *NombreDeServidor/SID* no funciona, use *NombreDeServidor/NombreDeServicio*, donde *NombreDeServicio* es el alias que se usa para conectarse.


   ![Escriba el nombre del servidor de Oracle](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Si en este paso tiene problemas para conectarse, pruebe a usar el formato siguiente en el campo **Servidor**: *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=nombre_host)(PORT=número_puerto))(CONNECT_DATA=(SERVICE_NAME=nombre_servicio)))*
   
3. Si quiere importar datos con una consulta de base de datos nativa, incluya la consulta en el cuadro **Instrucción SQL**, que aparece al expandir la sección **Opciones avanzadas** del cuadro de diálogo **Base de datos de Oracle**.
   
   ![Expansión de Opciones avanzadas](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Una vez que haya escrito la información de la base de datos de Oracle en el cuadro de diálogo **Base de datos de Oracle** (incluida toda información opcional, como un SID o una consulta de base de datos nativa), seleccione **Aceptar** para conectarse.
5. Si la base de datos de Oracle necesita credenciales del usuario de la base de datos, ingréselas en el cuadro de diálogo cuando se le solicite hacerlo.


## <a name="troubleshooting"></a>Solución de problemas

Si ha descargado Power BI Desktop desde Microsoft Store, es posible que no pueda conectarse a bases de datos de Oracle debido a un problema con el controlador de Oracle. Si se produce este problema, el mensaje de error que se devuelve es: *Referencia a objeto no establecida*. Para solucionar el problema, siga uno de estos pasos:

* Descargue Power BI Desktop desde el [Centro de descarga](https://www.microsoft.com/download/details.aspx?id=58494) en lugar de Microsoft Store.

* Si quiere usar la versión disponible en Microsoft Store: en el equipo local, copie el archivo oraons.dll de _12.X.X\client_X_ en _12.X.X\client_X\bin_, donde _X_ representa los números de versión y directorio.

Si ve el mensaje de error *Referencia de objeto no establecida* en Power BI Gateway al conectarse a una base de datos de Oracle, siga las instrucciones de [Administración del origen de datos: Oracle](service-gateway-onprem-manage-oracle.md).
