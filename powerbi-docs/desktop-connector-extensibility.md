---
title: Extensibilidad de los conectores en Power BI
description: 'Extensibilidad de los conectores: funcionalidades, características, configuración de seguridad y conectores certificados'
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: bba674df9864697199a274698a1b17320b8ccd80
ms.sourcegitcommit: 9d6f37fd32b965592bd7b108dea87b8e53b11334
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/18/2018
ms.locfileid: "40256301"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidad de los conectores en Power BI

En Power BI, los clientes y los desarrolladores pueden ampliar de varias maneras los orígenes de datos a los que se pueden conectar, por ejemplo, mediante el uso de conectores existentes y orígenes de datos genéricos (como ODBC, OData, Oledb, web, CSV, XML, JSON). Además de estos orígenes de datos, los desarrolladores pueden crear extensiones de datos, que se conocen como **conectores personalizados**, y certificar los conectores para que sean se conviertan en **conectores certificados**.

Actualmente, la capacidad de usar **conectores personalizados** se habilita mediante un conmutador de características. Antes de migrar esta característica de la disponibilidad beta a la general, se ha agregado un menú que permite controlar de forma segura el nivel de código personalizado que quiere permitir que se ejecute en el sistema: todos los conectores personalizados o bien solo los conectores certificados y distribuidos por Microsoft en el cuadro de diálogo **Obtener datos**.

## <a name="custom-connectors"></a>Conectores personalizados

Los **conectores personalizados** pueden incluir una amplia gama de posibilidades, desde pequeñas API fundamentales para el negocio, hasta servicios de gran tamaño específicos del sector para los que Microsoft aún no ha publicado un conector. Muchos conectores son distribuidos por el propio proveedor, así que si necesita uno en concreto, debe ponerse en contacto con un proveedor.

Para usar un **conector personalizado**, colóquelo en la carpeta *\[Documentos]\\Power BI Desktop\\Conectores personalizados* y ajuste la configuración de seguridad como se describe en la sección siguiente.

No es necesario ajustar la configuración de seguridad para usar **conectores certificados**.

## <a name="data-extension-security"></a>Seguridad de la extensión de datos

Para cambiar la configuración de seguridad de la extensión de datos, en **Power BI Desktop**, seleccione **Archivo > Options and Settings (Opciones y configuración) > Opciones > Seguridad**.

![Controle si quiere poder cargar los conectores personalizados con las opciones de seguridad de la extensión de datos](media/desktop-connector-extensibility/data-extension-security-1.png)

En **Extensiones de datos**, puede seleccionar dos niveles de seguridad:

* (Recomendado) Permitir que solo se carguen las extensiones certificadas
* (No recomendado) Permitir que se cargue cualquier extensión sin previo aviso

Si planea usar **conectores personalizados** o conectores que usted o un tercero haya desarrollado y distribuya, debe seleccionar **"(Not Recommended) Allow any extension to load without warning"** (No recomendado) Permitir que se cargue cualquier extensión sin previo aviso. No se recomienda esta configuración de seguridad a menos que piense ejecutar **conectores personalizados**.

Con la configuración de seguridad **"(Recomendado)"**, si hay conectores personalizados en el sistema, se muestra un error que describe los conectores que no se pueden cargar debido a la seguridad.

![Un cuadro de diálogo describirá los conectores personalizados que no se pueden cargar debido a la configuración de seguridad, en este caso TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver el error y usar esos conectores, debe cambiar la configuración de seguridad al valor **"(No recomendado)"**, como se ha explicado anteriormente, y reiniciar **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Un subconjunto limitado de extensiones de datos se considera **certificado**, y dichos conectores certificados están disponibles en el cuadro de diálogo **Obtener datos**, pero el responsable del mantenimiento y el soporte técnico sigue siendo el desarrollador que ha creado el conector. Aunque Microsoft distribuye estos conectores, no es responsable de su rendimiento ni de su funcionalidad continuada.

Si quiere certificar un conector personalizado, pídale a su proveedor que se ponga en contacto con dataconnectors@microsoft.com.
