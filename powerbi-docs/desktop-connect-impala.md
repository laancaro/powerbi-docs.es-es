---
title: Conectarse a una base de datos de Impala en Power BI Desktop
description: Conectarse fácilmente a una base de datos de Impala y usarla en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0befceba2651ad4f8f414d3669c5830c07ece06d
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514206"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Conectarse a una base de datos de Impala en Power BI Desktop
En Power BI Desktop, puede conectarse a una base de datos de **Impala** y usar los datos subyacentes como con cualquier otro origen de datos en Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Conectarse a una base de datos de Impala
Para conectarse a una base de datos de **Impala**, siga estos pasos: 

1. Seleccione **Obtener datos** en la cinta **Inicio** de Power BI Desktop. 

2. Seleccione **Base de datos** en las categorías de la izquierda. Verá **Impala**.

    ![Obtener datos](media/desktop-connect-impala/connect_impala_2.png)

3. En la ventana **Impala** que aparece, escriba o pegue en el cuadro el nombre de su servidor Impala. Después, seleccione **Aceptar**. Puede **importar** datos directamente a Power BI o puede usar **DirectQuery**. Obtenga más información sobre cómo [usar DirectQuery](desktop-use-directquery.md).

    ![Ventana de Impala](media/desktop-connect-impala/connect_impala_3a.png)

4. Cuando se le pida, escriba sus credenciales o conéctese de forma anónima. El conector de Impala admite Anonymous, Basic (nombre de usuario + contraseña) y la autenticación de Windows.

    ![Conector de Impala](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > Una vez que haya escrito su nombre de usuario y contraseña para un servidor **Impala** determinado, Power BI Desktop usa esas mismas credenciales en los intentos de conexión posteriores. Si quiere modificar dichas credenciales, vaya a **Archivo > Opciones y configuración > Configuración de origen de datos**.


5. Después de conectarse, se abre una ventana del **navegador** y muestra los datos que están disponibles en el servidor. Seleccione los elementos de estos datos para importarlos y usarlos en **Power BI Desktop**.

    ![Ventana Navegador](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones
Hay algunas limitaciones y consideraciones que se deben tener en cuenta con el conector de **Impala**:

* El conector de Impala se admite en la puerta de enlace de datos local, con cualquiera de los tres mecanismos de autenticación compatibles.

## <a name="next-steps"></a>Pasos siguientes
Hay muchos orígenes de datos distintos a los que puede conectarse con Power BI Desktop. Para obtener más información sobre los orígenes de datos, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

