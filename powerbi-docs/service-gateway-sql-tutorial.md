---
title: 'Tutorial: Conexión a datos locales en SQL Server'
description: Obtenga información sobre cómo usar SQL Server como un origen de datos de la puerta de enlace, incluida la forma de actualizar los datos.
author: mgblythe
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: tutorial
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 91b6ee8971004a014b188f94142e90914ae3a3b7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881547"
---
# <a name="refresh-data-from-an-on-premises-sql-server-database"></a>Actualización de los datos desde una base de datos local de SQL Server

En este tutorial, explorará cómo actualizar un conjunto de datos de Power BI desde una base de datos relacional que existe en el entorno local de su red local. En concreto, en este tutorial se usa una base de datos de ejemplo de SQL Server, a la que debe acceder Power BI mediante una puerta de enlace de datos local.

En este tutorial, realizaremos los siguientes pasos:

> [!div class="checklist"]
> * Crear y publicar un archivo de Power BI Desktop (.pbix) que importe datos desde una base de datos local de SQL Server.
> * Configurar las opciones del conjunto de datos y el origen de datos en Power BI para la conectividad de SQL Server mediante una puerta de enlace de datos.
> * Configurar una programación de actualización para asegurarse de que el conjunto de datos de Power BI tiene datos recientes.
> * Realizar una actualización a petición del conjunto de datos.
> * Revisar el historial de actualizaciones para analizar los resultados de los ciclos de actualización anteriores.
> * Eliminar los artefactos que se han creado en este tutorial para limpiar los recursos.

## <a name="prerequisites"></a>Requisitos previos

- Si aún no tiene una, regístrese para obtener una [prueba gratuita de Power BI](https://app.powerbi.com/signupredirect?pbi_source=web) antes de comenzar.
- [Instale Power BI Desktop](https://powerbi.microsoft.com/desktop/) en un equipo local.
- [Instale SQL Server](/sql/database-engine/install-windows/install-sql-server) en un equipo local y restaure la [base de datos de ejemplo desde una copia de seguridad](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak). Para obtener más información sobre AdventureWorks, vea [Configuración e instalación de AdventureWorks](/sql/samples/adventureworks-install-configure).
- [Instale una puerta de enlace de datos local](service-gateway-onprem.md) en el mismo equipo local que SQL Server (en producción, normalmente sería otro equipo).

> [!NOTE]
> Si no es un administrador de puerta de enlace y no quiere instalar una puerta de enlace, póngase en contacto con un administrador de puerta de enlace de su organización. Esa persona puede crear la definición del origen de datos necesaria para conectar el conjunto de datos con la base de datos de SQL Server.

## <a name="create-and-publish-a-power-bi-desktop-file"></a>Creación y publicación de un archivo de Power BI Desktop

Use el procedimiento siguiente para crear un informe básico de Power BI con la base de datos de ejemplo AdventureWorksDW. Publique el informe en el servicio Power BI, de forma que tenga un conjunto de datos en Power BI que, después, pueda configurar y actualizar en los siguientes pasos.

1. En Power BI Desktop, en la pestaña **Inicio**, seleccione **Obtener datos** \> **SQL Server**.

2. En el cuadro de diálogo **Base de datos de SQL Server**, escriba los nombres del **Servidor** y la **Base de datos (opcional)** , asegúrese de que el **Modo Conectividad de datos** sea **Importar** y después seleccione **Aceptar**.

    ![Base de datos SQL Server](./media/service-gateway-sql-tutorial/sql-server-database.png)

3. Verifique sus **credenciales** y luego seleccione **Conectar**.

    > [!NOTE]
    > Si no puede autenticarse, asegúrese de seleccionar el método de autenticación correcto y use una cuenta con acceso a la base de datos. En entornos de prueba, puede usar la autenticación de base de datos con un nombre de usuario explícito y una contraseña. En entornos de producción, se suele usar la autenticación de Windows. Consulte [Solución de problemas de escenarios de actualización](refresh-troubleshooting-refresh-scenarios.md) y póngase en contacto con el administrador de base de datos para obtener más ayuda.

1. Si aparece el cuadro de diálogo **Compatibilidad con cifrado**, seleccione **Aceptar**.

2. En el cuadro de diálogo **Navegador**, seleccione la tabla **DimProduct** y después seleccione **Cargar**.

    ![Navegador de origen de datos](./media/service-gateway-sql-tutorial/data-source-navigator.png)

3. En la vista **Informe** de Power BI Desktop del panel **Visualizaciones**, seleccione **Gráfico de columnas apiladas**.

    ![Gráfico de columnas apiladas](./media/service-gateway-sql-tutorial/stacked-column-chart.png)

4. Con el gráfico de columnas seleccionado en el lienzo de informes, en el panel **Campos**, seleccione los campos **EnglishProductName** y **ListPrice**.

    ![Panel Campos](./media/service-gateway-sql-tutorial/fields-pane.png)

5. Arrastre **EndDate** a **Filtros de nivel de informe** y, en **Filtrado básico**, seleccione solo la casilla **(En blanco)** .

    ![Filtros de nivel de informe](./media/service-gateway-sql-tutorial/report-level-filters.png)

    Ahora el gráfico debería parecerse al siguiente.

    ![Gráfico de columnas finalizado](./media/service-gateway-sql-tutorial/finished-column-chart.png)

    Fíjese en que los cinco productos de **Road-250** se muestran con el precio de venta más alto. Esto cambiará al actualizar los datos y el informe más adelante en este tutorial.

6. Guarde el informe con el nombre "AdventureWorksProducts.pbix".

7. En la pestaña **Inicio**, seleccione **Publicar** \> **Mi área de trabajo** \> **Seleccionar**. Inicie sesión en el servicio Power BI si se le pide que lo haga.

8. En la pantalla **Correcto**, seleccione **Abrir "AdventureWorksProducts.pbix" en Power BI**.

    [Publicar en Power BI](./media/service-gateway-sql-tutorial/publish-to-power-bi.png)

## <a name="connect-a-dataset-to-a-sql-server-database"></a>Conexión de un conjunto de datos con una base de datos de SQL Server

En Power BI Desktop, se conecta directamente a la base de datos local de SQL Server, pero el servicio Power BI requiere que una puerta de enlace de datos actúe como un puente entre la nube y la red local. Siga estos pasos para agregar la base de datos local de SQL Server como un origen de datos a una puerta de enlace y luego conecte el conjunto de datos a este origen de datos.

1. Inicie sesión en Power BI. En la esquina superior derecha, seleccione el icono de engranaje de configuración y después seleccione **Configuración**.

    ![Configuración de Power BI](./media/service-gateway-sql-tutorial/power-bi-settings.png)

2. En la pestaña **Conjuntos de datos**, seleccione el conjunto de datos **AdventureWorksProducts** para que pueda conectarse a la base de datos local de SQL Server mediante una puerta de enlace de datos.

3. Expanda **Conexión de puerta de enlace** y compruebe que aparece al menos una puerta de enlace. Si no tiene una puerta de enlace, consulte la sección [Requisitos previos](#prerequisites) anteriormente en este tutorial para obtener un vínculo a la documentación del producto a fin de instalar y configurar una puerta de enlace.

    ![Conexión de puerta de enlace](./media/service-gateway-sql-tutorial/gateway-connection.png)

4. En **Acciones**, expanda el botón de alternancia para ver los orígenes de datos y seleccione el vínculo **Agregar a la puerta de enlace**.

    ![Agregar origen de datos a la puerta de enlace](./media/service-gateway-sql-tutorial/add-data-source-gateway.png)

    > [!NOTE]
    > Si no es un administrador de puerta de enlace y no quiere instalar una puerta de enlace, póngase en contacto con un administrador de puerta de enlace de su organización. Esa persona puede crear la definición del origen de datos necesaria para conectar el conjunto de datos con la base de datos de SQL Server.

5. En la página de administración **Puertas de enlace**, en la pestaña **Configuración de origen de datos**, escriba y compruebe la información siguiente y seleccione **Agregar**.

    | Opción | Valor |
    | --- | --- |
    | Nombre del origen de datos | AdventureWorksProducts |
    | Tipo de origen de datos | SQL Server |
    | Servidor | El nombre de la instancia de SQL Server, por ejemplo, SQLServer01 (debe ser idéntico al especificado en Power BI Desktop). |
    | Base de datos | El nombre de la base de datos de SQL Server, por ejemplo, AdventureWorksDW (debe ser idéntico al especificado en Power BI Desktop). |
    | Método de autenticación | Windows o Básico (normalmente, Windows). |
    | Nombre de usuario | La cuenta de usuario que utilice para conectarse a SQL Server. |
    | Contraseña | La contraseña de la cuenta que use para conectarse a SQL Server. |

    ![Configuración del origen de datos](./media/service-gateway-sql-tutorial/data-source-settings.png)

6. En la pestaña **Conjuntos de datos**, vuelva a expandir la sección **Conexión de puerta de enlace**. Seleccione la puerta de enlace de datos que ha configurado, que muestra un **Estado** de ejecución en el equipo en el que la ha instalado, y seleccione **Aplicar**.

    ![Actualización de la conexión de la puerta de enlace](./media/service-gateway-sql-tutorial/update-gateway-connection.png)

## <a name="configure-a-refresh-schedule"></a>Configuración de una programación de actualización

Ahora que ha conectado el conjunto de datos en Power BI con la base de datos local de SQL Server mediante una puerta de enlace de datos, siga estos pasos para configurar una programación de actualización. Actualizar el conjunto de datos de forma programada le ayuda a garantizar que los informes y los paneles tienen los datos más recientes.

1. En el panel de navegación, abra **Mi área de trabajo** \> **Conjuntos de datos**. Seleccione los puntos suspensivos ( **. . .** ) del conjunto de datos **AdventureWorksProducts** y seleccione **Programar actualización**.

    > [!NOTE]
    > Asegúrese de seleccionar los puntos suspensivos del conjunto de datos **AdventureWorksProducts** y no los del informe que tiene el mismo nombre. En el menú contextual del informe **AdventureWorksProducts** no se incluye la opción **Programar actualización**.

2. En la sección **Actualización programada**, en **Mantener los datos actualizados**, establezca la actualización en **Activada**.

3. Seleccione una **Frecuencia de actualización** adecuada (**Diaria** en este ejemplo) y, después, en **Hora**, seleccione **Agregar otra hora** para especificar la hora de actualización que quiera (6:30 y 18:30 en este ejemplo).

    ![Configuración de actualización programada](./media/service-gateway-sql-tutorial/configure-scheduled-refresh.png)

    > [!NOTE]
    > Puede configurar hasta ocho franjas de tiempo diarias si el conjunto de datos se encuentra en una capacidad compartida, o hasta 48 franjas de tiempo en Power BI Premium.

4. Deje activada la casilla **Enviarme correos electrónicos para notificarme los errores de actualización** y seleccione **Aplicar**.

## <a name="perform-an-on-demand-refresh"></a>Realización de una actualización a petición

Ahora que ha configurado una programación de actualización, Power BI actualiza el conjunto de datos en la siguiente hora programada, dentro de un margen de 15 minutos. Si quiere actualizar los datos antes, por ejemplo, para probar la configuración del origen de datos y la puerta de enlace, realice una actualización a petición con la opción **Actualizar ahora**, situada en el menú del conjunto de datos del panel de navegación. Las actualizaciones a petición no afectan a la próxima actualización programada, pero cuentan para el límite diario de actualizaciones, que se ha mencionado en la sección anterior.

Con fines meramente ilustrativos, simule un cambio en los datos de ejemplo al actualizar la tabla DimProduct de la base de datos AdventureWorksDW mediante SQL Server Management Studio (SSMS).

```sql

UPDATE [AdventureWorksDW].[dbo].[DimProduct]
SET ListPrice = 5000
WHERE EnglishProductName ='Road-250 Red, 58'

```

Ahora, siga estos pasos para que los datos actualizados puedan pasar por la conexión de puerta de enlace al conjunto de datos y a los informes en Power BI.

1. En el panel de navegación del servicio Power BI, seleccione y expanda **Mi área de trabajo**.

2. En **Conjuntos de datos**, en el conjunto de datos **AdventureWorksProducts**, seleccione los puntos suspensivos ( **. . .** ) y seleccione **Actualizar ahora**.

    ![Actualizar ahora](./media/service-gateway-sql-tutorial/refresh-now.png)

    Fíjese en la esquina superior derecha en que Power BI se está preparando para realizar la actualización solicitada.

3. Seleccione **Mi área de trabajo \> Informes \> AdventureWorksProducts**. Vea cómo fluyen los datos actualizados y el producto con el precio de venta más alto es ahora **Road-250 rojo, 58**.

    ![Gráfico de columnas actualizado](./media/service-gateway-sql-tutorial/updated-column-chart.png)

## <a name="review-the-refresh-history"></a>Revisión del historial de actualización

Es una buena idea comprobar los resultados de los ciclos de actualización anteriores de forma periódica en el historial de actualizaciones. Las credenciales de la base de datos pueden haber expirado o la puerta de enlace seleccionada puede haber quedado sin conexión cuando tenía que realizarse una actualización programada. Siga estos pasos para examinar el historial de actualizaciones y compruebe si hay problemas.

1. En la esquina superior derecha de la interfaz de usuario de Power BI, seleccione el icono de engranaje de configuración y después seleccione **Configuración**.

2. Cambie a **Conjuntos de datos** y seleccione el conjunto de datos que quiera examinar (por ejemplo, **AdventureWorksProducts**).

3. Seleccione el vínculo **Actualizar historial** para abrir el cuadro de diálogo **Actualizar historial**.

    ![Vínculo del historial de actualizaciones](./media/service-gateway-sql-tutorial/refresh-history-link.png)

4. En la pestaña **Programado**, observe las actualizaciones programadas anteriormente y a petición con las horas de **Inicio** y **Finalización** y un **Estado** de **Completado**, que indica que Power BI ha realizado correctamente las actualizaciones. En el caso de las actualizaciones erróneas, puede ver el mensaje de error y examinar los detalles de este.

    ![Detalles del historial de actualizaciones](./media/service-gateway-sql-tutorial/refresh-history-details.png)

    > [!NOTE]
    > La pestaña OneDrive solo es pertinente para los conjuntos de datos conectados a archivos de Power BI Desktop, libros de Excel o archivos CSV en OneDrive o SharePoint Online, como se explica con más detalles en [Actualizar datos en Power BI](refresh-data.md).

## <a name="clean-up-resources"></a>Limpieza de recursos

Si no quiere volver a usar los datos de ejemplo, quite la base de datos de SQL Server Management Studio (SSMS). Si no quiere usar el origen de datos de SQL Server, quítelo de la puerta de enlace de datos. Considere también la posibilidad de desinstalar la puerta de enlace de datos si solo la ha instalado para completar este tutorial. También debería eliminar el conjunto de datos AdventureWorksProducts y el informe AdventureWorksProducts que Power BI ha creado al cargar el archivo AdventureWorksProducts.pbix.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, hemos examinado cómo importar datos de una base de datos local de SQL Server a un conjunto de datos de Power BI y cómo actualizar este conjunto de datos de forma programada y a petición para mantener actualizados los informes y los paneles que usan este conjunto de datos en Power BI. Ahora puede obtener más información sobre cómo administrar las puertas de enlace de datos y los orígenes de datos en Power BI. También es una buena idea consultar el artículo conceptual Actualizar datos en Power BI.

- [Administración de una puerta de enlace de datos local](/data-integration/gateway/service-gateway-manage)
- [Administrar el origen de datos: importación o actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md)
- [Actualizar datos en Power BI](refresh-data.md)
