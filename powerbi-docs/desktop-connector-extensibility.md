---
title: Extensibilidad de los conectores en Power BI
description: 'Extensibilidad de los conectores: funcionalidades, características, configuración de seguridad y conectores certificados'
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412983"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidad de los conectores en Power BI

En Power BI, los clientes y desarrolladores pueden ampliar los orígenes de datos al que se conectan en muchos sentidos. Usan los conectores existentes y orígenes de datos genéricos (por ejemplo, ODBC, OData, Oledb, Web, CSV, XML, JSON). O bien, los desarrolladores crean extensiones de datos, denominadas **conectores personalizados**y hacerlos **conectores Certified**.

Actualmente, habilitar **conectores personalizados** mediante un menú que permite de forma segura a controlar el nivel de código personalizado que desea permitir que se ejecute en el sistema. Puede elegir todos los conectores personalizados o conectores únicamente certificadas y distribuido por Microsoft en la **obtener datos** cuadro de diálogo.

## <a name="custom-connectors"></a>Conectores personalizados

**Los conectores personalizados** puede incluir una amplia gama de posibilidades, comprendido entre pequeño API críticas para su negocio, servicios de gran tamaño específicas del sector que Microsoft todavía no ha publicado un conector para. Muchos conectores se distribuyen por el proveedor. Si tiene una necesidad de un conector de datos específica, póngase en contacto con un proveedor.

Para usar un **Custom Connector**, colocarlo en la  *\[documentos]\\Power BI Desktop\\conectores personalizados* carpeta y ajustar la configuración de seguridad, como se describe en la siguiente sección.

No es necesario ajustar la configuración de seguridad para usar **conectores certificados**.

## <a name="data-extension-security"></a>Seguridad de la extensión de datos

Para cambiar la configuración de seguridad de la extensión de datos, en **Power BI Desktop** seleccione **archivo > Opciones y configuración > Opciones > seguridad**.

![Controlar si desea cargar los conectores personalizados con las opciones de seguridad de la extensión de datos](media/desktop-connector-extensibility/data-extension-security-1.png)

En **Extensiones de datos**, puede seleccionar dos niveles de seguridad:

* (Recomendado) Permitir que solo se carguen las extensiones certificadas
* (No recomendado) Permitir que se cargue cualquier extensión sin previo aviso

Si planea usar **conectores personalizados** o conectores que han desarrollado usted o un tercero, debe seleccionar **"(Not Recommended) permitir cargar sin previo aviso cualquier extensión"** . No se recomienda esta configuración de seguridad a menos que confíe plenamente en los conectores personalizados. Porque, en el código allí puede controlar las credenciales, incluido el envío de ellos a través de HTTP y pasar por alto los niveles de privacidad.

En el **"(recomendado)"** seguridad establecer, si no hay conectores personalizados en el sistema, se produce un error que describe los conectores que no se pueden cargar debido a la seguridad.

![Un cuadro de diálogo describe los conectores personalizados que no se puede cargar debido a la configuración de seguridad, en este caso TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver el error y utilizar los conectores, cambiar la configuración de seguridad para el **"(Not Recommended) permitir cargar sin previo aviso cualquier extensión"** tal como se describe anteriormente. A continuación, reinicie **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Se considera un subconjunto limitado de las extensiones de datos **Certified**. Obtener acceso a los conectores certificados en el **obtener datos** cuadro de diálogo. Sin embargo, el desarrollador de terceros que se creó el conector es responsable de su mantenimiento y soporte técnico. Mientras que Microsoft distribuye los conectores, no es responsable de su rendimiento o la función continuado.

Si quiere certificar un conector personalizado, pídale a su proveedor que se ponga en contacto con dataconnectors@microsoft.com.
