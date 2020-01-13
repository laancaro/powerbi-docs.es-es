---
title: Conexión a un almacén de Snowflake Computing en Power BI Desktop
description: Conexión y uso sencillos de un almacén de Snowflake Computing en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 23d66994e88204f56ee937a4f7887225e48a5e2f
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75304276"
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Conectarse a Snowflake en Power BI Desktop
En Power BI Desktop, puede conectarse a un almacén de **Snowflake** Computing y usar los datos subyacentes como cualquier otro origen de datos en Power BI Desktop. 

> [!NOTE]
> También *debe* instalar el **controlador ODBC de Snowflake** en equipos que usan el conector de **Snowflake**, con la arquitectura que coincide con la instalación de **Power BI Desktop**, de 32 bits o 64 bits. Siga el siguiente vínculo y [descargue el controlador ODBC de Snowflake adecuado](https://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Conectar a un almacén de Snowflake Computing
Seleccione **Obtener datos** en la cinta **Inicio** para conectarse a un almacén de **Snowflake** Computing en Power BI Desktop. Seleccione **Base de datos** en las categorías de la izquierda para que se muestre **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

En la ventana **Snowflake** que aparece, escriba o pegue en el cuadro el nombre de su almacén de Snowflake Computing y seleccione **Aceptar**. Tenga en cuenta que puede elegir **Importar** datos directamente a Power BI o puede usar **DirectQuery**. Puede obtener más información acerca de cómo [usar DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Cuando se le pida, escriba su nombre de usuario y contraseña.

![](media/desktop-connect-snowflake/connect_snowflake_4.png)

> [!NOTE]
> Una vez que haya escrito su nombre de usuario y contraseña para un servidor **Snowflake** determinado, Power BI Desktop usa esas mismas credenciales en los intentos de conexión posteriores. Si quiere modificar dichas credenciales, vaya a **Archivo > Opciones y configuración > Configuración de origen de datos**.
> 
> 

Si quiere usar la opción cuenta de Microsoft, pida al administrador de Snowflake que se ponga en contacto con Snowflake para saber cómo unirse a la versión preliminar privada de esta característica.

![Tipo de autenticación de la cuenta de Microsoft en el conector Snowflake.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Una vez que se haya conectado correctamente, aparece la ventana **Navegador**, en la que se muestran los datos disponibles en el servidor, desde donde puede seleccionar uno o varios elementos para importar y usar en **Power BI Desktop**.

![Error ODBC 28000 que causa un error de conexión.](media/desktop-connect-snowflake/connect_snowflake_5.png)

Puede **Cargar** la tabla seleccionada, que muestra la tabla completa en **Power BI Desktop**, o bien puede **Editar** la consulta, que abre **Editor de consultas** para que pueda filtrar y refinar el conjunto de datos que desea utilizar y, a continuación, cargar ese conjunto de datos refinado en **Power BI Desktop**.

## <a name="next-steps"></a>Pasos siguientes
Hay todo tipo de datos a los que puede conectarse con Power BI Desktop. Para obtener más información sobre orígenes de datos, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

