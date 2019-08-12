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
ms.openlocfilehash: 7d5d743dda31d05df0beb528648c5a43ffc6b335
ms.sourcegitcommit: 32a44dd17a44ccfd4a2d86a0d235251c2fda1c5c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702106"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidad de los conectores en Power BI

En Power BI, los clientes y desarrolladores pueden extender de muchas maneras los orígenes de datos a los que se conectan. Usan conectores existentes y orígenes de datos genéricos (como ODBC, OData, OLEDB, Web, CSV, XML y JSON). O bien, los desarrolladores crean extensiones de datos, a las que se hace referencia como **conectores personalizados**, y las convierten en **conectores certificados**.

Actualmente, los **conectores personalizados** se habilitan mediante un menú que permite controlar de forma segura el nivel de código personalizado que se desea permitir que se ejecute en el sistema. Puede elegir todos los conectores personalizados o solo los conectores certificados y distribuidos por Microsoft en el cuadro de diálogo **Obtener datos**.

## <a name="custom-connectors"></a>Conectores personalizados

Los **conectores personalizados** pueden incluir una amplia gama de posibilidades, desde pequeñas API críticas para el negocio, hasta servicios de gran tamaño específicos del sector para los que Microsoft aún no ha publicado un conector. Muchos conectores los distribuye un proveedor. Póngase en contacto con alguno si necesita un conector de datos específico.

Para usar un **conector personalizado**, colóquelo en la carpeta *\[Documentos]\\Power BI Desktop\\Conectores personalizados* y ajuste la configuración de seguridad como se describe en la sección siguiente.

No es necesario ajustar la configuración de seguridad para usar **conectores certificados**.

## <a name="data-extension-security"></a>Seguridad de la extensión de datos

Para cambiar la configuración de seguridad de la extensión de datos, en **Power BI Desktop**, seleccione **Archivo > Opciones y configuración > Opciones > Seguridad**.

![Controle si quiere cargar los conectores personalizados con las opciones de seguridad de la extensión de datos](media/desktop-connector-extensibility/data-extension-security-1.png)

En **Extensiones de datos**, puede seleccionar dos niveles de seguridad:

* (Recomendado) Permitir que solo se carguen las extensiones certificadas
* (No recomendado) Permitir que se cargue cualquier extensión sin previo aviso

Si planea usar **conectores personalizados** o conectores que usted o un tercero haya desarrollado, debe seleccionar **(No recomendado) Permitir que se cargue cualquier extensión sin previo aviso**. No se recomienda esta configuración de seguridad a menos que confíe totalmente en los conectores personalizados. Por ello, el código empleado puede controlar las credenciales, incluido su envío a través de HTTP, e ignorar los niveles de privacidad.

En la configuración de seguridad **(Recomendado)** , si hay conectores personalizados en el sistema, obtendrá el error "El conector que se indica a continuación no se ha certificado y no podemos comprobar si es seguro usarlo" seguido de una lista de conectores que no se pueden cargar de forma segura.

![Un cuadro de diálogo describe los conectores personalizados que no se pueden cargar debido a la configuración de seguridad, en este caso TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver el error sin cambiar la seguridad, quite los conectores no firmados de la carpeta "Conectores personalizados".

Para resolver el error y usar esos conectores, cambie la configuración de seguridad al valor **(No recomendado) Permitir que se cargue cualquier extensión sin previo aviso**, como se ha explicado anteriormente. Después, reinicie **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Un subconjunto limitado de extensiones de datos se considera **Certificado**. Acceda a los conectores certificados en el cuadro de diálogo **Obtener datos**. Sin embargo, el desarrollador externo que creó el conector es responsable de su mantenimiento y soporte técnico. Aunque Microsoft distribuye los conectores, no es responsable de su rendimiento ni de su funcionalidad continuada.

Si quiere certificar un conector personalizado, pídale a su proveedor que se ponga en contacto con dataconnectors@microsoft.com.
