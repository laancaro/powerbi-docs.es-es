---
title: Usar DirectQuery en Power BI Desktop
description: Usar DirectQuery (también denominado conexión dinámica) en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d8432ae10afab6cbf12c017a8f315fd55825212d
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427240"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Usar DirectQuery en Power BI Desktop
Con *Power BI Desktop*, cuando se conecta al origen de datos, siempre es posible importar una copia de los datos en Power BI Desktop. Para algunos orígenes de datos, existe un enfoque alternativo: conectarse directamente al origen de datos mediante DirectQuery.

## <a name="supported-data-sources"></a>Orígenes de datos admitidos
Para obtener una lista completa de los orígenes de datos que admiten DirectQuery, consulte [Orígenes de datos compatibles con DirectQuery](power-bi-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Cómo conectarse con DirectQuery
Si usa **Obtener datos** para conectarse a un origen de datos compatible con DirectQuery, el cuadro de diálogo de conexión le permite seleccionar cómo quiere conectarse. Por ejemplo, en Power BI Desktop, en la cinta **Inicio**, seleccione **Obtener datos** > **SQL Server**. En el cuadro de diálogo **Base de datos de SQL Server**, el **Modo Conectividad de datos** muestra opciones **Importación** y **DirectQuery**:

![Opciones Importar y DirectQuery, cuadro de diálogo Base de datos de SQL Server, Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

Estas son las diferencias entre usar **Importar** y **DirectQuery**:

- **Importación**: las tablas y columnas seleccionadas se importan en Power BI Desktop. A medida que crea una visualización o interactúa con ella, Power BI Desktop usa los datos importados. Para ver los cambios de datos subyacentes desde la importación inicial o la actualización más reciente, debe actualizar los datos, lo que importa de nuevo el conjunto de datos completo.

- **DirectQuery**: no se importan ni copian datos en Power BI Desktop. En el caso de los orígenes relacionales, las tablas y columnas seleccionadas aparecen en la lista **Campos**. En el caso de los orígenes multidimensionales como SAP Business Warehouse, las dimensiones y medidas del cubo seleccionado aparecen en la lista **Campos**. Mientras crea o interactúa con una visualización, Power BI Desktop consulta el origen de datos subyacente, lo que significa que siempre está viendo los datos actuales.

Existen muchas transformaciones de datos y modelado de datos disponibles al usar DirectQuery, aunque con algunas limitaciones. Al crear o interactuar con una visualización, debe consultar el origen subyacente. El tiempo necesario para actualizar el objeto visual depende del rendimiento del origen de datos subyacente. Si los datos necesarios para atender la solicitud se solicitaron recientemente, Power BI Desktop usa datos recientes para reducir el tiempo necesario para mostrar la visualización. Si selecciona**Actualizar** en la cinta **Inicio**, se asegurará de que todas las visualizaciones se actualicen con los datos actuales.

En el artículo [Power BI y DirectQuery](desktop-directquery-about.md) se describe DirectQuery detalladamente. Para obtener más información sobre las ventajas, limitaciones y consideraciones importantes al utilizar DirectQuery, consulte las siguientes secciones.

## <a name="benefits-of-using-directquery"></a>Ventajas del uso de DirectQuery
El uso de DirectQuery ofrece varias ventajas:

- DirectQuery permite crear visualizaciones en conjuntos de datos muy grandes, en los que de otro modo sería imposible importar primero todos los datos con agregación previa.
- Los cambios en los datos subyacentes pueden requerir una actualización de datos. Para algunos informes, la necesidad de mostrar los datos actuales puede requerir grandes transferencias de datos, de modo que sería inviable volver a importar datos. Por el contrario, los informes de DirectQuery siempre usan los datos actuales.
- La limitación del conjunto de datos a 1 GB *no* se aplica a DirectQuery.

## <a name="limitations-of-directquery"></a>Limitaciones de DirectQuery
Actualmente, existen algunas limitaciones en el uso de DirectQuery:

- Si la consulta del **Editor de consultas** es demasiado compleja, se produce un error. Para corregir el error debe eliminar el paso problemático en el **Editor de consultas** o *importar* los datos, en lugar de usar DirectQuery. En el caso de los orígenes multidimensionales, como SAP Business Warehouse, no hay **Editor de consultas**.

- Las funcionalidades de inteligencia de tiempo no están disponibles en DirectQuery. Por ejemplo, no se admite el tratamiento especial de columnas de fecha (año, trimestre, mes, día, etc.) en el modo DirectQuery.

- Para asegurarse de que las consultas enviadas al origen de datos subyacente tienen un rendimiento aceptable, se aplican limitaciones a las expresiones DAX que se permiten en las medidas.

- Hay un límite de 1 millón de filas para devolver datos cuando se usa DirectQuery, a menos que se utilice una capacidad premium. El límite no afecta a las agregaciones o cálculos utilizados para crear el conjunto de datos devuelto mediante DirectQuery. Solo afecta a las filas devueltas. Las capacidades premium pueden establecer límites máximos de filas, tal y como se describe en [esta publicación](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/). 

    Por ejemplo, puede agregar 10 millones de filas a la consulta que se ejecuta en el origen de datos. La consulta devuelve con precisión los resultados de esa agregación a Power BI mediante DirectQuery si el número de filas de datos de Power BI devueltos es inferior a un millón. Si se devuelve más de 1 millón filas desde DirectQuery, Power BI devuelve un error (a menos que esté en la capacidad premium y el recuento de filas esté por debajo del límite del conjunto de administradores).

## <a name="important-considerations-when-using-directquery"></a>Consideraciones importantes al utilizar DirectQuery
Deben tenerse en cuenta los tres puntos siguientes al usar DirectQuery:

- **Carga y rendimiento**: todas las solicitudes de DirectQuery se envían a la base de datos de origen, por lo que el tiempo necesario para actualizar un objeto visual depende de cuánto tiempo tarda ese origen de back-end en responder con los resultados de la consulta (o consultas). El tiempo de respuesta recomendado (con la devolución de los datos solicitados) para usar DirectQuery con objetos visuales es de cinco segundos o menos; el tiempo de respuesta máximo recomendado es de 30 segundos, y nada más. Así, la experiencia de un usuario que utiliza el informe acaba por ser demasiado mala. Después de que se publique un informe en el servicio Power BI, se agotará el tiempo de espera de cualquier consulta que tarde más de unos minutos y el usuario recibirá un error.
  
    También se debe tener en cuenta la carga en la base de datos de origen, en función del número de usuarios de Power BI que utilizarán el informe publicado. El uso de **Seguridad de nivel de fila** (RLS) también puede tener un impacto significativo. Un icono del panel no RLS compartido por varios usuarios da como resultado una sola consulta a la base de datos. Aunque el uso de RLS en un icono del panel, normalmente significa que la actualización de un icono requiere una consulta *por usuario*, lo que aumenta significativamente la carga en la base de datos de origen y puede afectar al rendimiento.
  
    Power BI crea consultas que son tan eficaces como sea posible. Aunque, en determinadas situaciones, la consulta generada puede no ser lo suficientemente eficiente para evitar una actualización en la que se produciría un error. Un ejemplo de esta situación se produce cuando una consulta generada recupera un número excesivamente grande de filas desde el origen de datos de back-end. En este caso, se produce el siguiente error:

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Esta situación puede producirse con un gráfico simple que incluye una columna de cardinalidad muy alta, con la opción de agregación establecida en **No resumir**. El objeto visual solo ha de tener columnas de cardinalidad inferior a un millón o se deben aplicar los filtros adecuados.

- **Seguridad**: de forma predeterminada, todos los usuarios que utilizan un informe publicado se conectan al origen de datos de back-end con las credenciales indicadas después de la publicación en el servicio Power BI. Este proceso es el mismo para los datos que se importan: todos los usuarios ven los mismos datos, independientemente de las reglas de seguridad definidas en el origen de back-end.

    Los clientes que quieran seguridad por usuario implementada con orígenes de DirectQuery deben usar RLS o configurar la autenticación restringida de Kerberos en el origen. Kerberos no está disponible para todos los orígenes. [Más información sobre RLS](service-admin-rls.md). [Más información sobre Kerberos en DirectQuery](service-gateway-sso-kerberos.md).

- **Características admitidas**: Algunas características de Power BI Desktop no se admiten en el modo DirectQuery o tienen algunas limitaciones. Además, hay algunas funcionalidades en el servicio Power BI (como *Conclusiones rápidas*) que no están disponibles para los conjuntos de datos que utilizan DirectQuery. A la hora de determinar si usar DirectQuery, debe tener en cuenta estas limitaciones de características.

## <a name="publish-to-the-power-bi-service"></a>Publicación en el servicio Power BI
Los informes creados mediante DirectQuery se pueden publicar en el servicio Power BI.

Si el origen de datos usado no necesita la **puerta de enlace de datos local** (**Azure SQL Database**, **Azure SQL Data Warehouse** o **Redshift**), se deben proporcionar credenciales para que el servicio Power BI muestre el informe publicado. Siga estas instrucciones para proporcionar las credenciales:

1. Inicie sesión en [Power BI](https://www.powerbi.com/).
2. En el servicio Power BI, seleccione el icono de engranaje **Configuración** y elija el elemento de menú **Configuración**.

    ![Configuración, servicio Power BI](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. En la página **Configuración** del servicio Power BI, seleccione la pestaña **Conjuntos de datos**, elija el conjunto de datos que usa DirectQuery y seleccione **Editar credenciales**.

4. Agregue las credenciales. De lo contrario, se producirá un error al abrir un informe publicado o explorar un conjunto de datos creado con una conexión de DirectQuery.

Para crear una conexión de orígenes de datos que no sean **Azure SQL Database**, **Azure SQL Data Warehouse**, **Redshift** o **Snowflake Data Warehouse** y que usen DirectQuery, instale una **puerta de enlace de datos local** y registre el origen de datos. Para obtener más información, consulte [¿Qué es una puerta de enlace de datos local?](service-gateway-onprem.md)

## <a name="next-steps"></a>Pasos siguientes
Para más información acerca de DirectQuery, revise los siguientes recursos:

- [Uso de DirectQuery en Power BI](desktop-directquery-about.md)
- [Orígenes de datos compatibles con DirectQuery](power-bi-data-sources.md)
- [DirectQuery y SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
- [¿Qué es una puerta de enlace de datos local?](service-gateway-onprem.md)
