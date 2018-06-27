---
title: Uso de objetos visuales personalizados de organización en Power BI
description: Uso, administración y creación de objetos visuales personalizados de organización en Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: bc4dcc26ac2007e482b396139d572018c8a3acd3
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34291912"
---
# <a name="using-organization-custom-visuals-in-power-bi"></a>Uso de objetos visuales personalizados de organización en Power BI

Puede utilizar los objetos visuales personalizados en Power BI para crear un único tipo de objeto visual adaptado a sus necesidades o a las informaciones de datos que trata de transmitir. Por lo general, son los desarrolladores quienes crean estos objetos visuales personalizados cuando la gran cantidad de objeto visuales incluidos en Power BI no satisface del todo sus necesidades. 

En algunas organizaciones, los objetos visuales personalizados son incluso más importantes: pueden ser necesarios para transmitir datos o informaciones particulares que son exclusivos de la organización, pueden tener requisitos especiales de datos o pueden poner de relieve métodos empresariales privados. Estas organizaciones tienen que desarrollar objetos visuales personalizados, compartirlos en toda su organización y asegurarse de que reciben un mantenimiento adecuado. Los objetos visuales personalizados de Power BI permiten a las organizaciones hacer exactamente eso.

La siguiente imagen muestra el proceso por el cual los objetos visuales de la organización en Power BI van desde la administración, pasando por el desarrollo y el mantenimiento, hasta llegar al analista de datos.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Los objetos visuales de la organización se implementan y administran mediante el Administrador de Power BI desde el portal de administración. Una vez implementados en el repositorio de organización, los usuarios de la organización pueden detectarlos fácilmente e importarlos en sus informes directamente desde Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Uso de objetos visuales personalizados de organización

Para obtener más información sobre cómo utilizar los objetos visuales personalizados de organización en los informes que ha creado, consulte el siguiente artículo: [Learn more about importing organizational visuals into your reports](power-bi-custom-visuals.md) (Más información sobre la importación de elementos visuales de organización en sus informes).
 
## <a name="administering-organizational-custom-visuals"></a>Administración de objetos visuales personalizados de organización

Para obtener más información sobre cómo administrar, implementar y administrar objetos visuales personalizados en su organización, consulte el siguiente artículo: [Learn more about deployment and management of organization custom visuals](https://go.microsoft.com/fwlink/?linkid=866790) (Más información sobre la implementación y la administración de objetos visuales personalizados de organización).

> [!WARNING]
> Un objeto visual personalizado podría contener código que presente riesgos para la seguridad o la privacidad. Asegúrese de que confía en el autor y el origen de cualquier objeto visual personalizado antes de implementarlo en el repositorio de la organización. 
> 

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones
 
Hay varias consideraciones y limitaciones que debe tener en cuenta.
 
Administrador:

* No se admiten objetos visuales personalizados heredados (por ejemplo, los objetos visuales personalizados que no se basan en las nuevas API con control de versiones)

* Si se elimina un objeto visual personalizado del repositorio, los informes existentes que usen el objeto visual eliminado dejarán de representarlo. La operación de eliminación del repositorio no es reversible. Para deshabilitar temporalmente un objeto visual personalizado, use la característica "Deshabilitar".
 
Usuario final:

* No se admite la colección de áreas de trabajo de Power BI para objetos visuales de organización.

* Los objetos visuales de Visio, PowerApps y GlobeMap del Marketplace de AppSource no se representarán si se implementan a través del repositorio de la organización.
