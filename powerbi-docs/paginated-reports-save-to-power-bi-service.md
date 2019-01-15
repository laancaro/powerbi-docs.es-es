---
title: Publicación de un informe paginado en el servicio Power BI (versión preliminar)
description: En este tutorial, aprenderá a publicar un informe paginado en el servicio Power BI cargándolo desde el equipo local.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: 76ec5c140fc90dcf71a76bc6ca13a860e3474c37
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280960"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service-preview"></a>Publicación de un informe paginado en el servicio Power BI (versión preliminar)

En este artículo, se ofrece información sobre cómo publicar un informe paginado en el servicio Power BI cargándolo desde el equipo local. Puede cargar informes paginados en Mi área de trabajo o en cualquier otra área de trabajo, siempre que tenga capacidad Premium. Busque el icono de diamante ![Icono de diamante de capacidad Premium de Power BI](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto al nombre del área de trabajo. 

Si el origen de datos del informe es local, entonces deberá [crear una puerta de enlace](#create-a-gateway-to-an-on-premises-data-source) después de cargar el informe.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Adición de un área de trabajo a una capacidad Premium

Si el área de trabajo no tiene el icono de diamante ![Icono de diamante de capacidad Premium de Power BI](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto al nombre, deberá agregar el área de trabajo a una capacidad Premium. 

1. Seleccione **Áreas de trabajo**, seleccione el botón de puntos suspensivos (**...**) junto al nombre del área de trabajo y después seleccione **Editar área de trabajo**.

    ![Selección de Editar área de trabajo](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. En el cuadro de diálogo **Editar área de trabajo**, expanda **Avanzado** y después establezca la opción **Capacidad dedicada** en **Activado**.

    ![Selección de Capacidad dedicada](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Es posible que no pueda cambiar esta configuración. Si no puede, póngase en contacto con el administrador de capacidad Premium de Power BI para que le conceda derechos de asignación para agregar el área de trabajo a una capacidad Premium.


## <a name="upload-a-paginated-report"></a>Carga de un informe paginado

1. Cree el informe paginado en el generador de informes y guárdelo en el equipo local.

1. Abra el servicio Power BI en un explorador y vaya al área de trabajo Premium en el que desea publicar el informe. Observe el icono de diamante ![Icono de diamante de capacidad Premium de Power BI](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto al nombre. 

1. Seleccione **Obtener datos**.

    ![Obtener datos en Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. En el cuadro **Archivos** , seleccione **Obtener**.

    ![Obtener archivos en Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Seleccione **Archivo local** > busque el informe paginado > **Abrir**.

    ![Selección de Archivo local](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Seleccione **Continuar** > **Editar credenciales**.

    ![Selección de Editar credenciales](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configure las credenciales > **Iniciar sesión**.

    ![Editar credenciales](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   El informe aparece en la lista de informes.

    ![Informe paginado en la lista Informes](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecciónelo para abrirlo en el servicio Power BI. Si tiene parámetros, debe seleccionarlos para poder ver el informe.
 
    ![Selección de parámetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Creación de una puerta de enlace

Al igual que cualquier otro informe de Power BI, si el origen de datos del informe es local, debe crear una puerta de enlace o conectarse a ella para acceder a los datos.

1. Junto al nombre del informe, seleccione **Administrar**.

   ![Administración del informe paginado](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Consulte el artículo del servicio Power BI [Instalación de una puerta de enlace](service-gateway-install.md) para obtener detalles y conocer los pasos siguientes.

### <a name="gateway-limitations"></a>Limitaciones de la puerta de enlace

Actualmente, las puertas de enlace no admiten parámetros de varios valores.


## <a name="next-steps"></a>Pasos siguientes

- [Visualización de un informe paginado en el servicio Power BI](paginated-reports-view-power-bi-service.md)
- [¿Qué son los informes paginados en Power BI Premium? (versión preliminar)](paginated-reports-report-builder-power-bi.md)

