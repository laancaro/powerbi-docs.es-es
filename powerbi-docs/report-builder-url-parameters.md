---
title: 'Parámetros de dirección URL en informes paginados: Generador de informes de Power BI'
description: En este tema se describe los usos comunes de los parámetros de informe del Generador de informes paginados de Power BI, las propiedades que puede establecer y mucho más.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: bda35bfb4690d8109f7bd611e3d319278d235f33
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302667"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Parámetros de dirección URL en informes paginados en Power BI

Puede enviar comandos a informes paginados en Power BI agregando un parámetro a una dirección URL. Por ejemplo, es posible que haya visto el informe con un conjunto específico de valores de parámetro de informe. Para encapsular esta información en la dirección URL, use los parámetros de acceso URL predefinidos. Puede personalizar aún más el modo en que Power BI procesa el informe mediante la inserción de parámetros para representar formatos o para la apariencia de la barra de herramientas de informe. Después, pegue esta dirección URL directamente en un correo o una página web para que otros usuarios puedan ver el informe de la misma manera en el explorador. 

Estas son las acciones que puede realizar a través de los parámetros de acceso URL: 

- Enviar parámetros de informe a un informe. 
- Iniciar la exportación del contenido del informe en un formato de archivo compatible. 
- Ocultar o ver el panel de parámetros. 
- Especificar la configuración DeviceInfo. 

Para obtener una lista completa de los comandos y las configuraciones disponibles a través del acceso URL, vea  [Referencia de parámetros de acceso URL](#url-access-parameter-reference) más adelante en este artículo. 

## <a name="url-access-concepts"></a>Conceptos de acceso URL 

Las solicitudes URL a Power BI contienen parámetros que el servicio se encarga de procesar. La forma en que el servicio controla las solicitudes URL depende de los parámetros, los prefijos de parámetro y los tipos de elementos que se incluyen en la dirección URL. La función URL de informe paginado es compatible con la mayoría de los exploradores y las aplicaciones que admiten el direccionamiento de direcciones URL estándar. 

## <a name="url-access-syntax"></a>Sintaxis de acceso URL 

Las solicitudes URL pueden contener varios parámetros, que se enumeran en cualquier orden. Los parámetros están separados por una Y comercial (&). Los pares de nombre y valor están separados por un signo de igual (=). Por ejemplo:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>Descripción de la sintaxis 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

La URL del servicio web del inquilino de Power BI. Por ejemplo: 

**&** Se usa para separar los pares de nombre y valor de los parámetros de acceso URL.

**prefix** Prefijo para el parámetro de URL (por ejemplo, rp: or rdl:) que especifica una acción en el servicio Power BI. 

> [!NOTE]
> Los parámetros de informe necesitan un prefijo de parámetro y distinguen entre mayúsculas y minúsculas. 

**parameter** Nombre del parámetro. 

### <a name="value"></a>value 

Texto de la URL que corresponde al valor del parámetro que se está usando. 

Para obtener ejemplos de cómo pasar parámetros de informe en la URL, vea  [Pasar un parámetro de informe en una URL](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Referencia de parámetros de acceso URL

Puede usar los siguientes parámetros como parte de una URL para configurar la apariencia de los informes paginados en Power BI. En esta sección se enumeran los parámetros más comunes. Los parámetros no distinguen entre mayúsculas y minúsculas y empiezan con el prefijo de parámetro  `rdl:`  si están relacionados con el formato de salida.  

### <a name="report-commands-rdl"></a>Comandos de informe (`rdl:`) 

**Formato de exportación** Especifica el formato en el que se va a representar y exportar un informe. Valores disponibles: 
- PPTX (PowerPoint)
- MHTML 
- IMAGEN 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>Pasos siguientes

- [Pasar un parámetro de informe en una URL para un informe paginado en Power BI](report-builder-url-pass-parameters.md)
- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
