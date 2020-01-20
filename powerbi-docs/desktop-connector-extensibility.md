---
title: Extensibilidad de los conectores en Power BI
description: 'Extensibilidad de los conectores: funcionalidades, características, configuración de seguridad y conectores certificados'
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: b604ade56335e65b25501eb9fe3d3c2fd185a6f0
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761415"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidad de los conectores en Power BI

Power BI puede conectarse a los datos mediante conectores existentes y orígenes de datos genéricos, como ODBC, OData, OLE DB, web, CSV, XML y JSON. O bien, los desarrolladores pueden habilitar nuevos orígenes de datos con extensiones de datos personalizadas denominados *conectores personalizados*. Microsoft ha certificado y distribuido algunos conectores personalizados como *conectores certificados*.

Para usar conectores personalizados no certificados que usted o un tercero hayan desarrollado, debe ajustar la configuración de seguridad de Power BI Desktop para permitir la carga de extensiones sin validación ni advertencia. Puesto que este código puede controlar credenciales, incluido su envío a través de HTTP, así como omitir niveles de privacidad, solo debería usar esta configuración de seguridad si confía plenamente en los conectores personalizados.

Otra opción que tiene el desarrollador es firmar el conector con un certificado y proporcionar la información que se necesita para usarlo sin cambiar la configuración de seguridad. Para obtener más información, vea [Acerca de los conectores de terceros de confianza](desktop-trusted-third-party-connectors.md).

## <a name="custom-connectors"></a>Conectores personalizados

Los conectores personalizados no certificados pueden abarcar desde pequeñas API críticas para el negocio hasta servicios de gran tamaño específicos del sector para los que Microsoft no ha publicado ningún conector. Muchos conectores son distribuidos por proveedores. Si necesita un conector de datos concreto, póngase en contacto con el proveedor. 

Para usar un conector personalizado no certificado, coloque el archivo *.pq*, *.pqx*, *.m* o *.mez* del conector en la carpeta *\[Documentos]\\Power BI Desktop\\Conectores personalizados*. Si la carpeta no existe, créela.

Ajuste la configuración de seguridad de las extensiones de datos de la siguiente manera:

En Power BI Desktop, seleccione **Archivo** > **Opciones y configuración** > **Opciones** > **Seguridad**.

En **Extensiones de datos**, seleccione **(Opción no recomendada) Permitir que se cargue cualquier extensión sin ninguna validación ni advertencia**. Seleccione **Aceptar** y reinicie Power BI Desktop. 

![Habilitación de conectores personalizados no certificados en las opciones de seguridad de las extensiones de datos](media/desktop-connector-extensibility/data-extension-security-1.png)

La configuración de seguridad predeterminada de las extensiones de datos de Power BI Desktop es **(Opción recomendada) Permitir solo la carga de extensiones certificadas por Microsoft y otras extensiones de terceros que sean de confianza**. Con este valor, si hay conectores personalizados no certificados en el sistema, aparece el cuadro de diálogo **Conectores no certificados** en el inicio de Power BI Desktop y en él se enumeran los conectores que no se pueden cargar de forma segura.

![Cuadro de diálogo Conectores no certificados](media/desktop-connector-extensibility/data-extension-security-2.png)

Para solucionar el error, puede cambiar la configuración de seguridad de **Extensiones de datos** o quitar los conectores no certificados de la carpeta *Conectores personalizados*.

## <a name="certified-connectors"></a>Conectores certificados

Un subconjunto limitado de extensiones de datos se considera *certificado*. Aunque Microsoft distribuye los conectores, no es responsable de su rendimiento ni de su funcionalidad continuada. El desarrollador ajeno que ha creado el conector es responsable de su mantenimiento y soporte técnico. 

En Power BI Desktop, los conectores de terceros certificados aparecen en la lista del cuadro de diálogo **Obtener datos** junto con los conectores genéricos y comunes. No es necesario ajustar la configuración de seguridad para usar los conectores certificados.

Si quiere certificar un conector personalizado, pida al proveedor que se ponga en contacto con dataconnectors@microsoft.com.
