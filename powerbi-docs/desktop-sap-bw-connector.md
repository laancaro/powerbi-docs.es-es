---
title: Uso del conector de SAP Business Warehouse (BW) en Power BI Desktop
description: Uso del conector de SAP BW en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8e1f6c38af11c5bdf942a4dc3a20b4b5f0ec0601
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76038903"
---
# <a name="use-the-sap-business-warehouse-connector-in-power-bi-desktop"></a>Uso del conector de SAP Business Warehouse en Power BI Desktop

Con Power BI Desktop, puede acceder a los datos de *SAP Business Warehouse (BW)* .

Para información sobre cómo los clientes de SAP pueden beneficiarse al conectar Power BI a sus sistemas SAP BW existentes, consulte las [notas del producto de Power BI y SAP BW](https://aka.ms/powerbiandsapbw). Para información detallada sobre el uso de DirectQuery con SAP BW, consulte [DirectQuery y SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

A partir de la versión de junio de 2018 de Power BI Desktop y con disponibilidad general en octubre de 2018, puede usar el *conector de SAP BW* con una implementación que tiene mejoras significativas en cuanto al rendimiento y las funcionalidades. Microsoft desarrolló *Implementation 2.0* del conector de SAP BW. Seleccione la versión 1 del conector de SAP BW o Implementation 2.0 SAP Connector. En las siguientes secciones se describe la instalación de cada versión. Puede elegir uno u otro conector a la hora de conectarse a SAP BW desde Power BI Desktop.

Le recomendamos usar Implementation 2.0 SAP Connector siempre que sea posible.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Instalación de la versión 1 del conector de SAP BW

Le recomendamos usar Implementation 2.0 SAP Connector siempre que sea posible. En esta sección se describe la instalación de la versión 1 del conector de SAP BW.

1. Instale la biblioteca *SAP NetWeaver* en el equipo local. Puede obtener la biblioteca SAP Netweaver del administrador de SAP o directamente desde el [Centro de descarga de software de SAP](https://support.sap.com/swdc). Como el Centro de descarga de software de SAP cambia su estructura con frecuencia, no hay disponibles instrucciones más específicas para navegar por ese sitio. Por lo general, la biblioteca SAP NetWeaver se incluye en la instalación de las herramientas de cliente de SAP.

   Puede buscar la *nota de SAP #1025361* para obtener la ubicación de descarga de la versión más reciente. Asegúrese de que la arquitectura de la biblioteca SAP NetWeaver (de 32 o 64 bits) coincida con su instalación de Power BI Desktop. Instale todos los archivos incluidos en *SAP NetWeaver RFC SDK* según la nota de SAP.
2. En Power BI Desktop, seleccione **Obtener datos**. Entre las opciones de **Base de datos** se incluyen *Servidor de aplicaciones de SAP Business Warehouse* y *Servidor de mensajería de SAP Business Warehouse*.

   ![Opciones Obtener datos para SAP](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Instalación de Implementation 2.0 SAP Connector

Implementation 2.0 SAP Connector requiere SAP .NET Connector 3.0. Para obtener acceso a la descarga se necesita un usuario S válido. Póngase en contacto con su equipo de SAP Basis para obtener SAP .NET Connector 3.0.

Puede descargar [SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html) de SAP.

El conector viene en versiones de 32 y 64 bits. Elija la versión que coincida con la instalación de Power BI Desktop. Actualmente, en el sitio web muestra dos versiones para .NET 4.0 Framework:

* Conector de SAP para Microsoft .NET 3.0.22.0 para Windows de 32 bits (x86) en un archivo ZIP (6896 KB), 1 de junio de 2019
* Conector de SAP para Microsoft .NET 3.0.22.0 para Windows de 64 bits (x64) en un archivo ZIP (7180 KB), 1 de junio de 2019

Al instalar, en **Pasos de instalación opcionales**, asegúrese de seleccionar *Instalar ensamblados en GAC*.

![Pasos de instalación opcionales de SAP](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> La primera versión de la implementación de SAP BW requería archivos DLL de NetWeaver. Si usa Implementation 2.0 SAP Connector y no la primera versión, no necesita los archivos DLL de NetWeaver.

## <a name="version-1-sap-bw-connector-features"></a>Características de la versión 1 del conector de SAP BW

La versión 1 del conector de SAP BW de Power BI Desktop permite importar datos de los cubos del *servidor de SAP Business Warehouse*, o bien usar DirectQuery.

Para más información sobre el conector de SAP BW y cómo usarlo con DirectQuery, consulte [DirectQuery y SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

Al conectarse, debe especificar un **servidor**, un **número de sistema** y el **id. de cliente** para establecer la conexión.

![Configuración de la conexión del servidor de SAP](media/desktop-sap-bw-connector/sap_bw_3a.png)

También puede especificar otras dos **opciones avanzadas**: **código de idioma** y una **instrucción MDX** personalizada para ejecutarla en el servidor especificado.

![Información de conexión adicional](media/desktop-sap-bw-connector/sap_bw_4a.png)

Si no especifica una instrucción MDX, la configuración de conexión muestra la lista de cubos disponibles en el servidor. Puede explorar en profundidad y seleccionar elementos de los cubos disponibles, incluidas las dimensiones y medidas. Power BI muestra las consultas y los cubos que muestran las [interfaces de Open Analysis](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Al seleccionar uno o varios elementos del servidor, el cuadro de diálogo Navegador crea una vista previa de la tabla de salida.

![Vista previa de la tabla de SAP](media/desktop-sap-bw-connector/sap_bw_5.png)

El cuadro de diálogo **Navegador** también proporciona opciones de presentación:

* **Mostrar solo los elementos seleccionados**. De manera predeterminada, el cuadro de diálogo **Navegador** muestra todos los elementos.  esta opción es útil para comprobar el conjunto final de los elementos seleccionados. Un enfoque alternativo para ver los elementos seleccionados es seleccionar los nombres de columna en el área de vista previa.
* **Habilitar vistas previas de datos**. Este es el valor predeterminado. Muestra vistas previas de los datos. Si deshabilita las vistas previas de los datos se disminuirá la cantidad de llamadas de servidor, puesto que ya no solicita datos para las vistas previas.
* **Nombres técnicos**. SAP BW admite la noción de *nombres técnicos* para objetos dentro de un cubo. Los nombres técnicos permiten al propietario de un cubo mostrar *nombres descriptivos* para los objetos de un cubo, en lugar de mostrar solo los *nombres físicos* para tales objetos.

![Ventana Navegador](media/desktop-sap-bw-connector/sap_bw_6.png)

Después de seleccionar todos los objetos necesarios, puede decidir qué hacer a continuación si selecciona una de las opciones siguientes:

* Seleccione **Cargar** para cargar todo el conjunto de filas de la tabla de salida en el modelo de datos de Power BI Desktop. Se abre la vista **Informe**. Puede empezar a visualizar los datos o hacer otras modificaciones mediante las vistas **Datos** o **Relaciones**.
* Seleccione **Editar** para abrir el **Editor de consultas**. Especifique los pasos adicionales de transformación y filtrado de datos antes de que todo el conjunto de filas se lleve al modelo de datos de Power BI Desktop.

Además de importar datos desde los cubos de SAP BW, también puede importar datos desde una gran variedad de orígenes en Power BI Desktop y, luego, combinarlos en un único informe. Esta capacidad ofrece una amplia gama de escenarios interesantes para los informes y análisis de datos de SAP BW.

## <a name="using-implementation-20-sap-bw-connector"></a>Usar Implementation 2.0 del conector de SAP BW

Cree una conexión para usar Implementation 2.0 del conector de SAP BW. Siga estos pasos para crear una conexión.

1. Seleccione **Obtener datos**. Seleccione **Servidor de aplicaciones de SAP Business Warehouse** o **Servidor de mensajería de SAP Business Warehouse** y, luego, conéctese.

2. En el cuadro de diálogo de la conexión nueva, seleccione la implementación. La selección de **2.0** en **Implementación**, tal como se muestra en la imagen siguiente, habilita las opciones **Modo de ejecución**, **Tamaño del lote** y **Habilitar estructuras características**.

    ![Cuadro de diálogo de conexión de SAP](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Seleccione **Aceptar**. Después de este punto, la experiencia es la misma que se describe en [Características de la versión 1 del conector de SAP BW](#version-1-sap-bw-connector-features) para la versión 1 del conector de SAP BW.

### <a name="new-options-for-implementation-20"></a>Nuevas opciones de Implementation 2.0

Implementation 2.0 admite las siguientes opciones:

* *ExecutionMode* especifica la interfaz MDX que se usa para ejecutar consultas en el servidor. Son válidas las opciones siguientes:

  * `SapBusinessWarehouseExecutionMode.BasXml`
  * `SapBusinessWarehouseExecutionMode.BasXmlGzip`
  * `SapBusinessWarehouseExecutionMode.DataStream`

    El valor predeterminado es `SapBusinessWarehouseExecutionMode.BasXmlGzip`.

    Usar `SapBusinessWarehouseExecutionMode.BasXmlGzip` puede mejorar el rendimiento cuando se experimenta una latencia elevada para conjuntos de datos de gran tamaño.

* *BatchSize* especifica el número máximo de filas que se van a recuperar a la vez cuando se ejecute una instrucción MDX. Un número pequeño se traduce en más llamadas al servidor al recuperar un conjunto de datos grande. Un número elevado de filas puede mejorar el rendimiento, pero podría provocar problemas de memoria en el servidor de SAP BW. El valor predeterminado son 50 000 filas.

* *EnableStructures* indica si se reconocen las estructuras características. El valor predeterminado de esta opción es false. Afecta a la lista de objetos disponibles para la selección. No se admite en el modo de consulta nativa.

La opción *ScaleMeasures* ha quedado en desuso en esta implementación. Ahora, el comportamiento es el mismo que si *ScaleMeasures* se establece en false, lo que siempre muestra valores sin ajuste de escala.

### <a name="additional-improvements-for-implementation-20"></a>Mejoras adicionales en Implementation 2.0

En la lista siguiente se describen algunas de las mejoras adicionales que se incluyen en la nueva implementación:

* Rendimiento mejorado.
* Capacidad para recuperar varios millones de filas de datos y ajuste mediante el parámetro de tamaño del lote.
* Capacidad de cambiar los modos de ejecución.
* Compatibilidad con el modo comprimido. Es útil sobre todo en las conexiones de alta latencia o en conjuntos de datos de gran tamaño.
* Detección mejorada de las variables `Date`.
* [Experimental] Exposición de las dimensiones `Date` (tipo ABAP DATS) y `Time` (tipo ABAP TIMS) como fechas y horas respectivamente, y no como valores de texto.
* Tratamiento de excepciones mejorado. Ahora aparecen errores que se producen en las llamadas BAPI.
* Plegamiento de columnas en los modos BasXml y BasXmlGzip. Por ejemplo, si la consulta MDX generada recupera 40 columnas pero la selección actual solo necesita 10, esta solicitud se pasará al servidor para recuperar un conjunto de datos más pequeño.

### <a name="changing-existing-reports-to-use-implementation-20"></a>Modificar los informes existentes para usar Implementation 2.0

Solo es posible modificar los informes existentes para usar Implementation 2.0 en modo de importación. Siga estos pasos:

1. Abra un informe existente, seleccione **Editar consultas** en la cinta de opciones y, después, seleccione la consulta de SAP Business Warehouse que se va a actualizar.

1. Haga clic con el botón derecho en la consulta y seleccione **Editor avanzado**.

1. En el **Editor avanzado**, cambie la llamada `SapBusinessWarehouse.Cubes` como se muestra a continuación:

    Determine si la consulta ya contiene un registro de opciones, como en el ejemplo siguiente:

    ![fragmento de código de consulta](media/desktop-sap-bw-connector/sap_bw_9.png)

    Si es así, agregue la opción `Implementation` 2.0 y quite la opción `ScaleMeasures`, si aparece, tal como se muestra a continuación:

    ![fragmento de código de consulta](media/desktop-sap-bw-connector/sap_bw_10.png)

    Si la consulta no incluye ya un registro de opciones, agréguelo. Para la opción siguiente:

    ![fragmento de código de consulta](media/desktop-sap-bw-connector/sap_bw_11.png)

    Modifíquelo por:

    ![fragmento de código de consulta](media/desktop-sap-bw-connector/sap_bw_12.png)

Se ha hecho todo lo posible para que Implementation 2.0 del conector de SAP BW sea compatible con la versión 1, aunque puede haber algunas diferencias debido a los distintos modos de ejecución MDX de SAP BW. Para resolver cualquier discrepancia, intente cambiar de modo de ejecución.

## <a name="troubleshooting"></a>Solución de problemas

En esta sección se muestran situaciones de diagnóstico de problemas (y soluciones) para trabajar con el conector de SAP BW.

1. Los datos numéricos de SAP BW devuelven puntos en lugar de comas. Por ejemplo, 1,000,000 se devuelve como 1.000.000.

   SAP BW devuelve datos decimales con una `,` (coma) o un `.` (punto) como separador decimal. Para especificar cuál de esas opciones de SAP BW se debe usar para el separador decimal, el controlador que Power BI Desktop usa hace una llamada a `BAPI_USER_GET_DETAIL`. Esta llamada devuelve una estructura denominada `DEFAULTS`, que tiene un campo que se llama `DCPFM` y que almacena la *notación de formato decimal*. El campo toma uno de los valores siguientes:

   * " " (espacio) = el separador decimal es una coma: N.NNN,NN
   * "X" = el separador decimal es un punto: N,NNN.NN
   * "Y" = el separador decimal es N NNN NNN,NN

   Los clientes que han notificado este problema han detectado que la llamada a `BAPI_USER_GET_DETAIL` genera un error para un usuario determinado, que muestra los datos incorrectos, con un mensaje de error similar al siguiente:

   ```xml
    You are not authorized to display users in group TI:
        <item>
            <TYPE>E</TYPE>
            <ID>01</ID>
            <NUMBER>512</NUMBER>
            <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
            <LOG_NO/>
            <LOG_MSG_NO>000000</LOG_MSG_NO>
            <MESSAGE_V1>TI</MESSAGE_V1>
            <MESSAGE_V2/>
            <MESSAGE_V3/>
            <MESSAGE_V4/>
            <PARAMETER/>
            <ROW>0</ROW>
            <FIELD>BNAME</FIELD>
            <SYSTEM>CLNTPW1400</SYSTEM>
        </item>
   ```

   Para solucionar este error, los usuarios deben solicitar a su administrador de SAP que conceda al usuario de SAPBW que se usa en Power BI el derecho para ejecutar `BAPI_USER_GET_DETAIL`. También es necesario comprobar que el usuario tiene el valor `DCPFM` necesario, tal como se describió anteriormente en esta sección de solución de problemas.

2. Conectividad para consultas de SAP BEx
   
   Puede realizar consultas de BEx en Power BI Desktop. Para ello, habilite una propiedad específica, tal y como se muestra en la imagen siguiente:
   
   ![Habilitación de versión para acceso externo](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. En la ventana **Navegador** no se muestra una vista previa de los datos, proporcionándose en su lugar un mensaje de error *Referencia de objeto no definida a una instancia de un objeto*.
   
   Los usuarios de SAP necesitan acceso a módulos de la función BAPI para obtener metadatos y recuperar datos de InfoProviders de SAP BW. Entre estos módulos se incluyen:

   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   Para solucionar este problema, compruebe que el usuario tiene acceso a los diversos módulos MDPROVIDER y a `BAPI_IOBJ_GETDETAIL`. Para solucionar otros problemas o problemas similares, puede habilitar el seguimiento. **Seleccione Archivo** > **Opciones y configuración** > **Opciones**. En **Opciones**, seleccione **Diagnósticos** y, luego **Habilitar seguimiento**. Intente recuperar datos de SAP BW mientras el seguimiento está activo y examine el archivo de seguimiento para obtener más detalles.

## <a name="sap-bw-connection-support"></a>Compatibilidad con conexiones de SAP BW

En la tabla siguiente se detalla la compatibilidad actual para SAP BW.

|Producto  |Modo  |Autenticación  |Conector  |Biblioteca de SNC  |Admitido  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |Cualquiera         | Usuario / contraseña  | Servidor de aplicaciones | N/D  | Sí  |
|Power BI Desktop     |Cualquiera         | Windows          | Servidor de aplicaciones | sapcrypto + gsskrb5/gx64krb5  | Sí  |
|Power BI Desktop     |Cualquiera         | Windows a través de la suplantación | Servidor de aplicaciones | sapcrypto + gsskrb5/gx64krb5  | Sí  |
|Power BI Desktop     |Cualquiera         | Usuario / contraseña        | Servidor de mensajería | N/D  | Sí  |
|Power BI Desktop     |Cualquiera         | Windows        | Servidor de mensajería | sapcrypto + gsskrb5/gx64krb5  | Sí  |
|Power BI Desktop     |Cualquiera         | Windows a través de la suplantación | Servidor de mensajería | sapcrypto + gsskrb5/gx64krb5  | Sí  |
|Power BI Gateway     |Importación      | Igual que Power BI Desktop |         |   |   |
|Power BI Gateway     |DirectQuery | Usuario / contraseña        | Servidor de aplicaciones | N/D  | Sí  |
|Power BI Gateway     |DirectQuery | Windows a través de la suplantación (usuario fijo, sin SSO) | Servidor de aplicaciones | sapcrypto + gsskrb5/gx64krb5  | Sí  |
|Power BI Gateway     |DirectQuery | Uso de SSO mediante Kerberos para la opción consultas de DirectQuery | Servidor de aplicaciones | sapcrypto + gsskrb5/gx64krb5   | Sí  |
|Power BI Gateway     |DirectQuery | Usuario / contraseña        | Servidor de mensajería | N/D  | Sí  |
|Power BI Gateway     |DirectQuery | Windows a través de la suplantación (usuario fijo, sin SSO) | Servidor de mensajería | sapcrypto + gsskrb5/gx64krb5  | Sí  |
|Power BI Gateway     |DirectQuery | Uso de SSO mediante Kerberos para la opción consultas de DirectQuery | Servidor de mensajería | gsskrb5/gx64krb5  | No  |
|Power BI Gateway     |DirectQuery | Uso de SSO mediante Kerberos para la opción consultas de DirectQuery | Servidor de mensajería | sapcrypto  | Sí  |

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre SAP y DirectQuery, revise los siguientes recursos:

* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery y SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos de Power BI](desktop-directquery-data-sources.md)
* [Notas del producto de Power BI y SAP BW](https://aka.ms/powerbiandsapbw)
