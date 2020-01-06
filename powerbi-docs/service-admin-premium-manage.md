---
title: Configuración y administración de capacidades en Power BI Premium
description: Obtenga información sobre cómo puede administrar Power BI Premium y habilitar el acceso a contenido para toda la organización.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/17/2019
LocalizationGroup: Premium
ms.openlocfilehash: e60aed5b538eab3b630f42a665d96256cc07879c
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "74700105"
---
# <a name="configure-and-manage-capacities-in-power-bi-premium"></a>Configuración y administración de capacidades en Power BI Premium

La administración de Power BI Premium implica la creación, administración y supervisión de las capacidades Premium. En este artículo se brindan instrucciones detalladas. Si necesita información general sobre las capacidades, consulte [Administración de las capacidades Premium](service-premium-capacity-manage.md).

Aprenda a administrar las capacidades de Power BI Premium y Power BI Embedded, que ofrecen recursos dedicados para su contenido.

![Pantalla de configuración de la capacidad de Power BI](media/service-admin-premium-manage/premium-capacity-management.png)

La *capacidad* es el núcleo de las ofertas Power BI Premium y Power BI Embedded. Es un conjunto de recursos reservados para uso exclusivo por parte de la organización. Tener capacidad dedicada le permite publicar paneles, informes y conjuntos de datos para los usuarios de su organización sin tener que adquirir licencias por usuario para ellos. También ofrece un rendimiento confiable y continuo del contenido hospedado en la capacidad. Para más información, consulte [What is Power BI Pro?](service-premium.md) (¿Qué es Power BI Premium?).

## <a name="manage-capacity"></a>Administración de capacidad

Cuando haya adquirido los nodos de capacidad en Office 365, configure la capacidad en el portal de administración de Power BI. Las capacidades de Power BI Premium se administran en la sección de **configuración de la capacidad** del portal.

![Configuración de la capacidad en el portal de administración](media/service-admin-premium-manage/admin-portal-premium.png)

Para administrar una capacidad, seleccione el nombre de la misma. Después de hacerlo, irá a la pantalla de administración de la capacidad.

![Seleccione el nombre de la capacidad para abrir la pantalla de asignación de capacidad](media/service-admin-premium-manage/capacity-assignment.png)

Si no se han asignado áreas de trabajo a la capacidad, verá un mensaje que le permite [asignar una área de trabajo a la capacidad](#assign-a-workspace-to-a-capacity).

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>Configuración de una nueva capacidad (Power BI Premium)

El portal de administración muestra el número de *núcleos virtuales* que ha utilizado y que aún están disponibles. El número total de núcleos virtuales se basa en las SKU Premium que ha adquirido. Por ejemplo, si compra una P3 y una P2, habrá 48 núcleos disponibles (32 de P3 y 16 de P2).

![Núcleos virtuales usados y disponibles para Power BI Premium](media/service-admin-premium-manage/admin-portal-v-cores.png)

Si tiene núcleos virtuales disponibles, puede configurar la nueva capacidad siguiendo los pasos siguientes.

1. Seleccione **Configurar nueva capacidad**.

1. Otorgue un nombre a la capacidad.

1. Defina quién es el administrador de esta capacidad.

1. Seleccione el tamaño de la capacidad. Las opciones disponibles dependen de cuántos núcleos virtuales disponibles haya. No se puede seleccionar una opción mayor que lo que hay disponible.

    ![Tamaños de capacidad Premium disponibles](media/service-admin-premium-manage/premium-capacity-size.png)

1. Seleccione **Configurar**.

    ![Configuración de una nueva capacidad](media/service-admin-premium-manage/set-up-capacity.png)

Los administradores de capacidad, así como los administradores de Power BI y los administradores globales de Office 365, podrán ver posteriormente la capacidad en el portal de administración.

### <a name="capacity-settings"></a>Configuración de la capacidad

1. En la pantalla de administración de la capacidad Premium, bajo **Acciones**, seleccione el **icono de engranaje** para revisar y actualizar la configuración. 

    ![Acciones de capacidad en el área de administración de la capacidad](media/service-admin-premium-manage/capacity-actions.png)

1. Puede ver quiénes son los administradores del servicio, la SKU o el tamaño de la capacidad, y en qué región está.

    ![Configuración de la capacidad](media/service-admin-premium-manage/capacity-settings.png)

1. También puede cambiar el nombre de una capacidad o eliminarla.

    ![Botones Eliminar y Aplicar para la configuración de la capacidad en Power BI Premium](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> La configuración de la capacidad de Power BI Embedded se administra en Microsoft Azure Portal.

### <a name="change-capacity-size"></a>Cambiar tamaño de capacidad

Los administradores de Power BI y los administradores globales de Office 365 pueden cambiar la capacidad de Power BI Premium. Los administradores de capacidad que no sean administradores de Power BI o administradores globales de Office 365 no tendrán esta opción.

1. Seleccione **Cambiar tamaño de capacidad**.

    ![Cambio del tamaño de capacidad de Power BI Premium](media/service-admin-premium-manage/change-capacity-size.png)

1. En la pantalla **Cambiar tamaño de capacidad**, aumente o reduzca la capacidad, según corresponda.

    ![Menú desplegable de Cambio de tamaño de capacidad en Power BI Premium](media/service-admin-premium-manage/change-capacity-size2.png)

    Los administradores pueden crear, cambiar el tamaño y eliminar nodos libremente, siempre y cuando tengan el número necesario de núcleos virtuales.

    Las SKU P no se pueden reducir a SKU EM. Al mantener el puntero sobre cualquier opción deshabilitada, verá una explicación.

### <a name="manage-user-permissions"></a>Administración de permisos de usuario

Puede asignar administradores de capacidad adicionales, así como asignar los usuarios que tengan permisos de *asignación de capacidad*. Los usuarios que tengan permisos de asignación pueden asignar un área de trabajo a una capacidad, siempre que sean administradores de esa área de trabajo. También pueden asignar *Mi área de trabajo* personal a la capacidad. Los usuarios con permisos de asignación no tienen acceso al portal de administración.

> [!NOTE]
> Para Power BI Embedded, los administradores de capacidad se definen en Microsoft Azure Portal.

En **Permisos de usuario**, expanda **Usuarios con permisos de asignación** y, a continuación, agregue usuarios o grupos según corresponda.

![Permisos de usuario de capacidad](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>Asignación de un área de trabajo a una capacidad

Hay dos maneras de asignar un área de trabajo a una capacidad: en el portal de administración y desde el área de trabajo.

### <a name="assign-from-the-admin-portal"></a>Asignación desde el portal de administración

Los administradores de capacidad, junto con los administradores de Power BI y los administradores globales de Office 365 pueden asignar en masa áreas de trabajo en la sección de administración de la capacidad Premium del portal de administración. Al administrar una capacidad, se muestra una sección **Áreas de trabajo** que permite asignar áreas de trabajo.

![Área de asignación de áreas de trabajo en administración de la capacidad](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. Seleccione **Asignar áreas de trabajo**. Esta opción está disponible en varios lugares.

1. Seleccione una opción para **Aplicar a**.

    ![Asignar áreas de trabajo](media/service-admin-premium-manage/assign-workspaces.png)

   | Selección | Descripción |
   | --- | --- |
   | **Áreas de trabajo por usuarios** | Al asignar áreas de trabajo por usuario o grupo, todas las áreas de trabajo que pertenecen a esos usuarios se asignan a la capacidad Premium, incluida el área de trabajo personal del usuario. Estos usuarios obtendrán automáticamente permisos de asignación de área de trabajo.<br>Esto incluye las áreas de trabajo ya asignadas a una capacidad diferente. |
   | **Áreas de trabajo específicas** | Escriba el nombre de un área de trabajo específica para asignar a la capacidad seleccionada. |
   | **Áreas de trabajo de toda la organización** | La asignación de las áreas de trabajo de toda una organización a la capacidad Premium asigna todas las áreas de trabajo y Mis áreas de trabajo, en una organización, a esta capacidad Premium. Además, todos los usuarios actuales y los futuros tendrán permiso para reasignar las áreas de trabajo individuales a esta capacidad. |
   | | |

1. Seleccione **Aplicar**.

### <a name="assign-from-workspace-settings"></a>Asignación desde la configuración del área de trabajo

También se puede asignar un área de trabajo a una capacidad Premium desde la configuración del área de trabajo. Para mover un área de trabajo a una capacidad, debe tener permisos de administrador sobre esa área de trabajo, así como permisos de asignación de capacidad para esa capacidad. Tenga en cuenta que los administradores de áreas de trabajo siempre pueden quitar un área de trabajo de la capacidad Premium.

1. Para editar un área de trabajo seleccione el icono de puntos suspensivos **(. . .)** y, después, seleccione **Editar área de trabajo**.

    ![Edición del área de trabajo desde el menú contextual de puntos suspensivos](media/service-admin-premium-manage/edit-app-workspace.png)

1. En **Editar área de trabajo**, expanda **Avanzado**.

1. Seleccione la capacidad a la que desea asignar esta área de trabajo.

    ![Menú desplegable de selección de la capacidad](media/service-admin-premium-manage/app-workspace-advanced.png)

1. Seleccione **Guardar**.

Una vez guardada, el área de trabajo y todo lo que contiene se mueve a la capacidad Premium sin que los usuarios finales experimenten ninguna interrupción.

## <a name="power-bi-report-server-product-key"></a>Clave de producto del servidor de informes de Power BI

En la pestaña **Configuración de la capacidad** del portal de administración de Power BI, tendrá acceso a la clave de producto de Power BI Report Server. Esta opción solo estará disponible para los administradores globales o los usuarios a quienes se haya asignado el rol de administrador del servicio Power BI, si ha comprado una SKU de Power BI Premium.

![Clave de Power BI Report Server en Configuración de la capacidad](media/service-admin-premium-manage/pbirs-product-key.png)

Al seleccionar **Clave del servidor de informes de Power BI**, se mostrará un cuadro de diálogo con su clave de producto. Puede copiarla y usarla en la instalación.

![Clave de producto del servidor de informes de Power BI](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

Para más información, consulte [Instalar un servidor de informes de Power BI](report-server/install-report-server.md).

## <a name="next-steps"></a>Pasos siguientes

[Administración de las capacidades Premium](service-premium-capacity-manage.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
