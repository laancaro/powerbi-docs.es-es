---
title: Área de trabajo de archivado de Power BI
description: Área de trabajo de archivado de Power BI después de administrar al inquilino de Office 365
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: d2eeab8241de06f9a4d0e654696173d076e01ad2
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292370"
---
# <a name="power-bi-archived-workspace"></a>Área de trabajo de archivado de Power BI

Con Power BI, cualquier usuario puede registrarse y empezar a usar el servicio en cuestión de minutos.  Más adelante, el departamento de TI de la organización puede optar por encargarse de la administración de Power BI por los usuarios de su organización.  Si esto sucede, podrá beneficiarse de la administración central de usuarios y permisos en su organización. También puede beneficiarse de la ventaja del inicio de sesión simplificado con el mismo nombre de usuario y la contraseña que usa para otros servicios de su organización.

Cualquier contenido creado antes de que el departamento de TI iniciara la administración de Power BI, se colocará en el área de trabajo de archivado de Power BI, a la que puede acceder desde el panel de navegación izquierdo de [Power BI](https://app.powerbi.com). Debería empezar a crear el contenido nuevo de Power BI en Mi área de trabajo, que está protegido y administrado por su departamento de TI de la organización.  El área de trabajo de archivado seguirá existiendo, pero existen restricciones sobre las acciones que puede realizar en el contenido del área de trabajo de archivado.  Para quitar estas restricciones, debe migrar el contenido del área de trabajo de archivado a Mi área de trabajo, que administra el departamento de TI.

## <a name="restrictions-in-your-archived-workspace"></a>Restricciones en el área de trabajo de archivado

Power BI no elimina el contenido de su área de trabajo de archivado. Puede continuar para obtener datos, crear informes y paneles y actualizar conjuntos de datos. Los usuarios existentes con los que comparte contenido podrán seguir viendo el contenido también en el área de trabajo de archivado. Sin embargo, existen algunas restricciones en el contenido en el área de trabajo de archivado:

* **OneDrive para la Empresa**: en los conjuntos de datos del área de trabajo de archivado, ya no puede obtener o actualizar datos desde OneDrive para la Empresa.  Si intenta conectarse a este origen, recibirá una advertencia.

* **Uso compartido de paneles**: No puede compartir paneles con otros usuarios desde el área de trabajo de archivado.  Los usuarios que ya tienen acceso podrán seguir viendo paneles compartidos si acceden a su área de trabajo de archivado.

* **Creación de grupos**: No puede crear grupos en el área de trabajo de archivado.

* **Acceso en aplicaciones móviles de Power BI**: a pesar de que aún puede seguir viendo contenido en la Web en el área de trabajo de archivado, este contenido ya no aparece en las aplicaciones móviles de Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migración de contenido en el área de trabajo de archivado

Para seguir usando Power BI, debe crear el nuevo contenido en Mi área de trabajo. También debe planear migrar contenido en el área de trabajo de archivado a Mi área de trabajo.  Dependencia de la migración de contenido del tipo de contenido:

* **Conjuntos de datos de Excel o Power BI Desktop**: migre estos conjuntos de datos cambiando del área de trabajo de archivado a Mi área de trabajo y vuelva a cargar el archivo de Excel o Power BI Desktop seleccionando el botón **Mis datos**.  Si establece la actualización programada, debe volver a configurar los valores para el nuevo conjunto de datos en Mi área de trabajo.

* **Otros conjuntos de datos**: cambie a Mi área de trabajo y, luego, seleccione el botón **Obtener datos** para volver a conectarse a los otros conjuntos de datos creados en el área de trabajo de archivado.  Es posible que necesite volver a especificar la información de conexión o de seguridad.

* **Informes**: los informes contenidos en archivos de Excel o Power BI Desktop se vuelven a crear automáticamente una vez que vuelva a cargar el archivo de Excel o Power BI Desktop correspondiente. Los informes instalados como parte de un paquete de contenido también se vuelven a crear una vez que se vuelve a establecer la conexión con dicho paquete. Si creó sus propios informes a través del servicio de Power BI, vuelva a crear dichos informes en Mi área de trabajo.

* **Paneles**: los paneles instalados como parte de los paquetes de contenido se vuelven a crear automáticamente cuando se vuelva a conectar al paquete de contenido en Mi área de trabajo. Si creó sus propios paneles mediante el servicio Power BI, vuelva a crear los paneles en Mi área de trabajo.

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

