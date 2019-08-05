---
title: Modo de edición avanzada
description: Objetos visuales de Power BI con controles de interfaz de usuario avanzados
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 625105aed773bce5cf70932f092faf60ea001c2c
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425560"
---
# <a name="advanced-edit-mode"></a>Modo de edición avanzada

Los objetos visuales que requieren controles de interfaz de usuario avanzados pueden declarar la compatibilidad con el modo de edición avanzada.
Si se admite, en el modo de edición de informes, aparecerá un botón `Edit` en el menú del objeto visual.
Al hacer clic en el botón `Edit`, EditMode se establece en `Advanced`.
El objeto visual puede usar la marca EditMode para determinar si debe mostrar estos controles de interfaz de usuario.

De forma predeterminada, el objeto visual no admite el modo de edición avanzada.
Si se requiere otro comportamiento, se debe indicar de forma explícita en el archivo `capabilities.json` del objeto visual, mediante el establecimiento de la propiedad `advancedEditModeSupport`.

Los valores posibles son los siguientes:

- 0: NotSupported

- 1: SupportedNoAction

- 2: SupportedInFocus

## <a name="entering-advanced-edit-mode"></a>Acceso al modo de edición avanzada

El botón `Edit` será visible si:

 1: La propiedad `advancedEditModeSupport` de capabilities.json está establecida en `SupportedNoAction` o `SupportedInFocus`.

 2: El objeto visual se ve en el modo de edición de informes.

Si falta la propiedad `advancedEditModeSupport` en capabilities.json o está establecida en `NotSupported`, el botón "Editar" desaparecerá.

![Acceso al modo de edición](./media/edit-mode.png)

Cuando el usuario hace clic en `Edit`, el objeto visual obtendrá una llamada a update() con la propiedad EditMode establecida en `Advanced`.
Según el valor establecido en las funciones, se producirán las acciones siguientes:

* `SupportedNoAction`: el host no realiza más acciones.
* `SupportedInFocus`: el host muestra el objeto visual en modo de enfoque.

## <a name="exiting-advanced-edit-mode"></a>Salida del modo de edición avanzada

El botón `Back to report` será visible si:

1: la propiedad `advancedEditModeSupport` de capabilities.json está establecida en `SupportedInFocus`.
