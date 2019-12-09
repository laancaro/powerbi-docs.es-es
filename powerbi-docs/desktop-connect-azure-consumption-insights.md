---
title: Conexión a los datos de Azure Consumption Insights en Power BI Desktop
description: Conéctese fácilmente a Azure y obtenga información detallada sobre el consumo y el uso con Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 4125ff59f32de8453fe131685f0a05e1c45220c3
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "73876523"
---
# <a name="connect-to-azure-consumption-insights-data-in-power-bi-desktop"></a>Conexión a los datos de Azure Consumption Insights en Power BI Desktop

Puede usar Power BI Desktop para conectarse a Azure y obtener datos detallados sobre el uso del servicio Azure en la organización. Con estos datos, puede crear medidas e informes personalizados para comprender y analizar mejor el gasto derivado del uso de Azure.

> [!NOTE]
> Existe una compatibilidad limitada con Microsoft Azure Consumption Insights (beta). Para obtener nuevas funcionalidades, use el conector de [Azure Cost Management para Power BI](desktop-connect-azure-cost-management.md).

## <a name="connect-with-azure-consumption-insights"></a>Conexión con Azure Consumption Insights

Azure Consumption Insights le permite conectarse a cuentas de facturación de contratos de Azure Enterprise.

En esta sección, aprenderá a obtener los datos que necesita migrar mediante el conector de Azure Enterprise. También encontrará una asignación de *columnas de detalles de uso* disponible en la API **ACI** (Azure Consumption Insights).

Para usar de forma correcta el conector de **Azure Consumption Insights**, debe tener acceso a las características empresariales de Azure Portal.

Para usar el conector **Azure Consumption Insights** en **Power BI Desktop**: 

1. Desde la cinta **Inicio**, seleccione **Obtener datos**.

1. En las categorías de la izquierda, seleccione **Servicios en línea**.  

1. Seleccione **Microsoft Azure Consumption Insights (Beta)** . 

1. Seleccione **Conectar**.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

   En el cuadro de diálogo que aparece, escriba el **número de inscripción de Azure**.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

   * Puede obtener este número en [Azure Enterprise Portal](https://ea.azure.com), en la ubicación que se muestra en esta imagen:

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)

   Esta versión del conector solo admite las inscripciones empresariales desde https://ea.azure.com. Actualmente no se admiten las inscripciones de China.

   A continuación, proporcione la *clave de acceso* para conectarse.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

   * Puede encontrar la clave de acceso para la inscripción en [Azure Enterprise Portal](https://ea.azure.com).

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

Una vez que haya proporcionado la *clave de acceso* y seleccione **Conectar**, aparece una ventana **Navegador** en la que se muestran nueve tablas disponibles:

| Tabla        | Descripción |
|------------- | -------------------------------------------------------------|
| **Budgets** | Detalles de presupuesto para ver los costos o el uso reales frente a los objetivos de presupuesto existentes. |
| **MarketPlace** | Cargos de Azure Marketplace en función del uso. |
| **PriceSheets** | Tarifas aplicables por medidor en una inscripción. |
| **RICharges** | Cargos asociados a las instancias reservadas en los últimos 24 meses. |
| **RIRecommendations_Single** | Recomendaciones de compra de instancias reservadas según las tendencias de uso en una única suscripción durante los últimos 7, 30 o 60 días. |
| **RIRecommendations_Shared** | Recomendaciones de compra de instancias reservadas según las tendencias de uso de todas las suscripciones durante los últimos 7, 30 o 60 días. |
| **RIUsage** | Detalles de consumo de las instancias reservadas existentes en el último mes. |
| **Summaries** | Un resumen mensual de saldos, nuevas compras, cargos de servicio de Azure Marketplace, ajustes y cargos por el uso por encima del límite. |
| **UsageDetails** | Un desglose de cantidades consumidas y gastos de inscripción estimados. |

Puede seleccionar la casilla situada junto a cualquier tabla para ver una vista previa. Puede seleccionar una o más tablas activando la casilla situada junto a su nombre y, después, seleccionando **Cargar**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04b.png)

> [!NOTE]
> Las tablas *Summary* y *PriceSheet* solo están disponibles para la clave de API en el nivel de inscripción. Además, los datos de estas tablas son, de forma predeterminada, los datos del mes actual de las tablas *Usage* y *PriceSheet*. Las tablas *Summary* y *MarketPlace* no se limitan al mes actual.
>
>

Al seleccionar **Cargar**, los datos se cargan en **Power BI Desktop**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

Una vez cargados los datos seleccionados, se pueden ver las tablas y campos que ha seleccionado en el panel **Campos**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Uso de Azure Consumption Insights
Para usar el conector de **Azure Consumption Insights**, se accede a las características empresariales de Azure Portal.

Una vez cargados de forma correcta los datos mediante el conector de **Azure Consumption Insights**, puede crear medidas y columnas personalizadas propias mediante el **Editor de consultas**. También puede crear objetos visuales, informes y paneles que se pueden compartir en el **servicio Power BI**.

Con una consulta en blanco, puede recuperar una colección de consultas personalizadas de Azure de ejemplo. Puede realizar esta recuperación de dos maneras: 

En **Power BI Desktop**: 

1. Seleccione la cinta **Inicio**. 
2. Seleccione **Obtener datos** > **Consulta en blanco**. 

O bien, en el **Editor de consultas**: 

1. Haga clic con el botón derecho en el panel **Consultas** de la izquierda. 
2. Seleccione **Nueva consulta > Consulta en blanco** en el menú que aparece.

En la **barra de fórmulas**, escriba lo siguiente:

    = MicrosoftAzureConsumptionInsights.Contents

En la imagen siguiente se muestra una colección de ejemplos que aparece.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

Al trabajar con informes y crear consultas, puede:

* Para definir el número de meses a partir de la fecha actual, use *numberOfMonth*.
  * Usar un valor entre 1 y 36. Representar el número de meses, a partir de la fecha actual, que quiere importar. Se recomienda no obtener más de 12 meses de datos. Este límite evita restricciones de importación de consultas y umbrales de volumen de datos en Power BI.
* Para definir un intervalo de meses en un período de tiempo histórico, utilice *startBillingDataWindow* y *endBillingDataWindow*
* No use *numberOfMonth* junto con *startBillingDataWindow* o *endBillingDataWindow*

## <a name="migrate-from-the-azure-enterprise-connector"></a>Migración desde el conector de Azure Enterprise

Algunos clientes han creado objetos visuales mediante el *conector de Azure Enterprise (beta)* . En última instancia, se reemplazará por el conector de **Azure Consumption Insights**. El nuevo conector tiene características y mejoras que incluyen las siguientes:

* Orígenes de datos adicionales disponibles para *Resumen de saldos* y *Compras en Marketplace*
* Nuevos parámetros avanzados, como *startBillingDataWindow* y *endBillingDataWindow*
* Mejor rendimiento y capacidad de respuesta

En los pasos siguientes se muestra cómo realizar la transición al conector de **Azure Consumption Insights**. Estos pasos conservan el trabajo que ya ha realizado en la creación de paneles o informes personalizados.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Paso 1: Conexión a Azure con el nuevo conector
El primer paso consiste en usar el conector de **Azure Consumption Insights** que se ha descrito con detalle antes en este artículo. En este paso, seleccione **Obtener datos > Consulta en blanco** en la cinta de opciones de **Inicio** en **Power BI Desktop**.

### <a name="step-2-create-a-query-in-advanced-editor"></a>Paso 2: Creación de una consulta en el Editor avanzado
En el **Editor de consultas**, seleccione **Editor avanzado** en la sección **Consulta** de la cinta **Inicio**. En la ventana **Editor avanzado** que aparece, escriba esta consulta:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Tendrá que reemplazar el valor *enrollmentNumber* por el número de inscripción. Puede obtener el número desde [Azure Enterprise Portal.](https://ea.azure.com) El parámetro *numberOfMonth* es el número de meses de datos pasados que quiere retroceder a partir de la fecha actual. Utilice cero (0) para el mes actual.

Una vez que seleccione **Listo** en la ventana **Editor avanzado**, la vista previa se actualiza y los datos del intervalo de meses especificado aparecen en la tabla. Seleccione **Cerrar y aplicar** y vuelva.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Paso 3: Traslado de medidas y columnas personalizadas al nuevo informe
A continuación, tendrá que mover todas las columnas o medidas personalizadas que haya creado a la nueva tabla de detalles. Estos son los pasos que debe realizar.

1. Abra el Bloc de notas (u otro editor de texto).
2. Seleccione la medida que quiere mover y copie el texto del campo *Fórmula* y colóquelo en el Bloc de notas.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Cambie el nombre de *Query1* al nombre original de la tabla de detalles.
4. Para crear medidas de tabla y columnas personalizadas, haga clic con el botón derecho en la tabla y seleccione **Nueva medida**. Después, corte y pegue todas las medidas y las columnas almacenadas.

### <a name="step-4-relink-tables-that-had-relationships"></a>Paso 4: Nueva vinculación de las tablas que tenían relaciones
Muchos paneles tienen tablas adicionales que se usan para buscar o filtrar, como tablas de fechas o tablas que se usan para proyectos personalizados. Volver a establecer esas relaciones puede resolver la mayoría de los problemas restantes. Aquí se muestra cómo hacerlo.

- En la pestaña **Modelado** de **Power BI Desktop**, seleccione **Administrar relaciones** para que aparezca una ventana que le permita administrar las relaciones dentro del modelo. Vuelva a vincular las tablas según sea necesario.

    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Paso 5: Comprobación de los objetos visuales y ajuste del formato de los campos según sea necesario
En este punto, la mayor parte de los objetos visuales originales, tablas y exploraciones en profundidad deben funcionar según lo previsto. Pero es posible que sea necesario realizar algunos ajustes menores para dar formato a la apariencia y el funcionamiento de forma precisa. Tómese tiempo para revisar todos los paneles y objetos visuales para asegurarse de que tengan el aspecto deseado.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Uso de la API de Azure Consumption and Insights (ACI) para obtener datos de consumo
Azure también proporciona la [**API de Azure Consumption and Insights (ACI)** ](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/). Puede crear sus propias soluciones personalizadas para recopilar, crear informes y visualizar la información de consumo de Azure mediante la API de ACI.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Asignación de nombres y detalles de uso entre el portal, el conector y la API
Las columnas y los nombres de los detalles en Azure Portal son similares en la API y en el conector, aunque no siempre idénticos. Para ayudar a aclararlo, en la tabla siguiente se proporciona una asignación. También se indica si la columna está obsoleta. Para obtener más información y definiciones de términos, vea el [diccionario de datos de facturación de Azure](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail).

| Conector ACI / ContentPack ColumnName | Nombre de columna en la API de ACI | Nombre de columna en EA | Obsoleta / presente para compatibilidad con versiones anteriores |
| --- | --- | --- | --- |
| AccountName |accountName |Nombre de cuenta |No |
| AccountId |accountId | |Sí |
| AcccountOwnerId |accountOwnerEmail |AccountOwnerId |No |
| AdditionalInfo |additionalInfo |AdditionalInfo |No |
| AdditionalInfold | | |Sí |
| Consumed Quantity |consumedQuantity |Consumed Quantity |No |
| Consumed Service |consumedService |Consumed Service |No |
| ConsumedServiceId |consumedServiceId | |Sí |
| Costo |cost |ExtendedCost |No |
| Cost Center |costCenter |Cost Center |No |
| Fecha |fecha |Fecha |No |
| Día | |Día |No |
| DepartmentName |departmentName |Nombre de departamento |No |
| DepartmentID |departmentId | |Sí |
| Instance ID | | |Sí |
| InstanceId |instanceId |Instance ID |No |
| Ubicación | | |Sí |
| Meter Category |meterCategory |Meter Category |No |
| Meter ID | | |Sí |
| Medidor Nombre |meterName |Medidor Nombre |No |
| Meter Region |meterRegion |Meter Region |No |
| Meter Sub-Category |meterSubCategory |Meter Sub-Category |No |
| MeterId |meterId |Meter ID |No |
| Mes | |Mes |No |
| Producto |producto |Producto |No |
| ProductId |productId | |Sí |
| Grupo de recursos |resourceGroup |Grupo de recursos |No |
| Resource Location |resourceLocation |Resource Location |No |
| ResourceGroupId | | |Sí |
| ResourceLocationId |resourceLocationId | |Sí |
| ResourceRate |resourceRate |ResourceRate |No |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |No |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |No |
| ServiceInfo1Id | | |Sí |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |No |
| ServiceInfo2Id | | |Sí |
| Store Service Identifier |storeServiceIdentifier |Store Service Identifier |No |
| StoreServiceIdentifierId | | |Sí |
| Nombre de suscripción |subscriptionName |Nombre de suscripción |No |
| Etiquetas |etiquetas |Etiquetas |No |
| TagsId | | |Sí |
| Unit Of Measure |unitOfMeasure |Unit Of Measure |No |
| Año | |Año |No |
| SubscriptionId |subscriptionId |SubscriptionId |Sí |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |No |


## <a name="next-steps"></a>Pasos siguientes

Se puede conectar a muchos orígenes de datos distintos mediante Power BI Desktop. Para obtener más información, consulte los artículos siguientes:

* [Conexión a los datos de Azure Cost Management en Power BI Desktop](desktop-connect-azure-cost-management.md)
* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
