---
title: Usar SAP HANA en Power BI Desktop
description: Usar SAP HANA en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753131"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Conexión a bases de datos de SAP HANA en Power BI Desktop

Con Power BI Desktop, ahora puede acceder a las bases de datos de *SAP HANA* . Para usar SAP HANA, el controlador ODBC de SAP HANA debe instalarse en el equipo cliente local para que la conexión de datos SAP HANA de Power BI Desktop funcione correctamente. Puede descargar las herramientas del cliente de SAP HANA desde [SAP Development Tools](https://tools.hana.ondemand.com/#hanatools), que contiene el controlador ODBC necesario. También puede obtenerlo en el [Centro de descarga de software de SAP](https://support.sap.com/en/my-support/software-downloads.html). En el portal de software, busque el *cliente de SAP HANA* para equipos Windows. Como el Centro de descarga de software de SAP cambia su estructura con frecuencia, no hay disponibles instrucciones más específicas para navegar por ese sitio.

Para conectarse a una base de datos SAP HANA, seleccione **Obtener datos**, elija **Base de datos** > **Base de datos SAP HANA** y, luego, seleccione **Conectar**:

![Base de datos SAP HANA, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Al conectarse a una base de datos SAP HANA, especifique el nombre del servidor. Después, en el menú desplegable y en el cuadro de entrada, especifique el puerto.

En esta versión, se admite SAP HANA en el modo [DirectQuery](desktop-directquery-sap-hana.md) en Power BI Desktop y en el servicio Power BI. Se pueden publicar y cargar informes que usan SAP HANA en el modo DirectQuery en el servicio Power BI. También se pueden publicar y cargar informes en el servicio Power BI si no usa SAP HANA en el modo DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Características compatibles con SAP HANA

Esta versión tiene muchas funciones para SAP HANA, tal como se muestra en la lista siguiente:

* El conector de Power BI para SAP HANA usa el controlador ODBC de SAP para proporcionar la mejor experiencia de uso.

* SAP HANA admite las opciones Importación y DirectQuery.

* Power BI admite modelos de información de HANA, como vistas analíticas y de cálculo, y ha optimizado la navegación.

* Con SAP HANA también puede usar la característica SQL directo para conectarse a las tablas de filas y columnas.

* Power BI incluye la navegación optimizada para modelos HANA.

* Power BI admite las variables y los parámetros de entrada de SAP HANA.

* Power BI admite las vistas de cálculo basadas en contenedores HDI.

  * La compatibilidad con las vistas de cálculo basadas en contenedores HDI está en versión preliminar pública en la versión de agosto de 2019 de Power BI Desktop. Para acceder a las vistas de cálculo basadas en contenedores HDI en Power BI, asegúrese de que los usuarios de la base de datos de HANA que usa con Power BI tengan permiso para acceder al contenedor del entorno de ejecución HDI que almacena las vistas a las que quiera obtener acceso. Para conceder este acceso, cree un rol que permita el acceso al contenedor HDI. Después, asigne el rol al usuario de la base de datos de HANA que va a usar con Power BI. (Este usuario también debe tener permiso de lectura de las tablas del sistema en el esquema de \_SYS\_BI, como es habitual). Consulte la documentación oficial de SAP para obtener instrucciones detalladas sobre cómo crear y asignar roles de base de datos. [Esta entrada de blog de SAP](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) puede ser un buen punto de partida.

  * Actualmente hay algunas limitaciones en las variables de HANA adjuntas a las vistas de cálculo basadas en HDI. Estas limitaciones se deben a errores en el lado de HANA.
  
    En primer lugar, no es posible aplicar una variable de HANA a una columna compartida de una vista de cálculo basada en contenedores HDI. Para corregir esta limitación, realice la actualización a HANA 2, versión 37.02 y posteriores, o bien a HANA 2, versión 42 y posteriores. En segundo lugar, los valores predeterminados de varias entradas para variables y parámetros no se muestran en la interfaz de usuario de Power BI. Un error en SAP HANA provoca esta limitación, pero SAP todavía no ha anunciado una corrección.

## <a name="limitations-of-sap-hana"></a>Limitaciones de SAP HANA

También existen algunas limitaciones en el uso de SAP HANA, tal como se muestra debajo:

* Las cadenas NVARCHAR se truncan a una longitud máxima de 4000 caracteres Unicode.
* No se admite SMALLDECIMAL.
* No se admite VARBINARY.
* Las fechas válidas son entre 12/30/1899 y 31/12/9999.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre DirectQuery y SAP HANA, consulte los siguientes recursos:

* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos de Power BI](power-bi-data-sources.md)
* [Habilitación del cifrado para SAP HANA](desktop-sap-hana-encryption.md)
