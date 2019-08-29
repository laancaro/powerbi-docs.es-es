---
title: Usar SAP HANA en Power BI Desktop
description: Usar SAP HANA en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f40ed1b3950ace0b3cb362a22670e98c3ef83112
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985674"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Usar SAP HANA en Power BI Desktop
Con Power BI Desktop, ahora puede acceder a las bases de datos de **SAP HANA** . Para usar **SAP HANA**, el controlador ODBC de SAP HANA debe instalarse en el equipo cliente local para que la conexión de datos **SAP HANA** de Power BI Desktop funcione correctamente. Puede descargar el controlador ODBC de SAP HANA desde el [Centro de descarga de software de SAP](https://support.sap.com/swdc). Desde allí, busque el CLIENTE de SAP HANA para equipos Windows. Puesto que el **Centro de descarga de software de SAP** cambia su estructura con frecuencia, no hay disponibles instrucciones más específicas para navegar por ese sitio.

Para conectarse a una base de datos **SAP HANA**, seleccione **Obtener datos > Base de datos > Base de datos SAP HANA** tal como se muestra en esta imagen:

![](media/desktop-sap-hana/sap-hana-1.png)

Al conectarse a una base de datos SAP HANA, especifique el nombre del servidor y el puerto con el formato *servidor:puerto*. En la imagen siguiente se muestra un ejemplo en un servidor denominado *ServerXYZ* y el puerto *30015*.

![](media/desktop-sap-hana/sap-hana-2.png)

En esta versión, la opción **SAP HANA** del modo [DirectQuery](desktop-directquery-sap-hana.md) solo se admite en Power BI Desktop y en el servicio Power BI, mientras que los informes que usen **SAP HANA** en el modo DirectQuery se pueden publicar y cargar en el servicio Power BI. También puede publicar y cargar informes en el servicio Power BI si no usa **SAP HANA** en el modo DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Características compatibles con SAP HANA
Esta versión tiene muchas funcionalidades para **SAP HANA**, tal como se muestra en la lista siguiente:

* El conector de Power BI para **SAP HANA** usa el controlador ODBC de SAP para proporcionar la mejor experiencia de uso
* **SAP HANA** es compatible con las opciones Importación y DirectQuery
* Power BI admite modelos de información de HANA (como vistas analíticas y de cálculo) y ha optimizado la navegación
* Con **SAP HANA** también puede usar la característica SQL directo para conectarse a las tablas de filas y columnas
* Incluye la navegación optimizada para modelos HANA
* Power BI es compatible con las variables y los parámetros de entrada **SAP HANA**
* Vistas de cálculo basadas en contenedores HDI
  * La compatibilidad con las vistas de cálculo basadas en contenedores HDI está en versión preliminar pública en la versión de agosto de 2019 de Power BI Desktop. Para tener acceso a las vistas de cálculo basadas en contenedores HDI en Power BI, asegúrese de que los usuarios de la base de datos de HANA que usa con Power BI tengan permiso para acceder al contenedor del entorno de ejecución HDI que almacena las vistas a las que quiera obtener acceso. Para conceder este acceso, debe crear un rol que permita el acceso al contenedor HDI y asignar el rol al usuario de la base de datos de HANA que va a usar con Power BI (este usuario también debe tener permiso para leer contenido de las tablas del sistema en el esquema de BI \_SYS\_, según lo habitual). Consulte la documentación oficial de SAP para obtener instrucciones detalladas sobre cómo crear y asignar roles de base de datos. [Esta entrada de blog de SAP](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.sap.com%2F2018%2F01%2F24%2Fthe-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user%2F&data=02%7C01%7Cv-adbold%40microsoft.com%7Cf7e0a405fe334598ba0608d7096ef5b4%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636988244476739316&sdata=PuRu61GPRYp34mLuGbQk6gdbRikdgbxfqo8q1RBQtm0%3D&reserved=0) puede ser un buen punto de partida.
  * Tenga en cuenta que actualmente hay algunas limitaciones en las variables de HANA adjuntas a las vistas de cálculo basadas en HDI. Estas limitaciones se deben a errores en el lado de HANA y se solucionarán en futuras versiones de SAP HANA. En primer lugar, no es posible aplicar una variable de HANA a una columna compartida de una vista de cálculo basada en contenedores HDI. Esta limitación se puede corregir realizando la actualización a HANA 2, versión 37.02 y posteriores, o bien a HANA 2, versión 42 y posteriores. En segundo lugar, los valores predeterminados de varias entradas para variables y parámetros no se muestran en la interfaz de usuario de Power BI. Sin embargo, esto también se debe a un error en SAP HANA; SAP todavía no ha anunciado una corrección.

## <a name="limitations-of-sap-hana"></a>Limitaciones de SAP HANA
También existen algunas limitaciones en el uso de **SAP HANA**, como se muestra a continuación:

* Las cadenas NVARCHAR se truncan a la longitud máxima de 4000 caracteres Unicode
* No se admite SMALLDECIMAL
* No se admite VARBINARY
* Las fechas válidas se sitúan entre 12/30/1899 y 31/12/9999


## <a name="next-steps"></a>Pasos siguientes
Para más información sobre DirectQuery y SAP HANA, revise los siguientes recursos:

* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [Habilitación del cifrado para SAP HANA](desktop-sap-hana-encryption.md)


