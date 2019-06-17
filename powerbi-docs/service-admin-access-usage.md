---
title: Encontrar usuarios de Power BI que hayan iniciado sesión
description: Si es un administrador de inquilinos y quiere ver quién ha iniciado sesión en Power BI, se pueden usar los informes de acceso y uso de Azure Active Directory para aumentar la visibilidad.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 7149d8601aa7a834f91a8d98f3a7a9deac7bf43b
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721321"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar usuarios de Power BI que hayan iniciado sesión

Si es un administrador de inquilinos y quiere ver quién ha iniciado sesión en Power BI, use los [informes de acceso y uso de Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) para aumentar la visibilidad.

> [!NOTE]
> El informe de **Inicios de sesión** ofrece información útil, pero no identifica el tipo de licencia que cada usuario tiene. Use el Centro de administración de Microsoft 365 para ver licencias.

## <a name="requirements"></a>Requisitos

Cualquier usuario (incluidos los no administradores) puede ver un informe de sus propios inicios de sesión, pero debe cumplir los requisitos siguientes para ver un informe para todos los usuarios.

* El inquilino debe tener una licencia de Azure AD Premium asociada.

* Debe tener alguno de los roles siguientes: administrador global, administrador de seguridad o lector de seguridad.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Uso de Azure Portal para ver los inicios de sesión

Para ver la actividad de inicio de sesión, siga estos pasos.

1. En **Azure Portal**, seleccione **Azure Active Directory**.

1. En **Supervisión**, seleccione **Inicios de sesión**.
   
    ![Captura de pantalla de la interfaz de usuario de Azure con las opciones de Azure Active Directory y de Inicios de sesión resaltadas.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre la aplicación, por **Microsoft Power BI** o **Power BI Gateway** y seleccione **Aplicar**.

    **Microsoft Power BI** filtra la actividad de inicio de sesión relacionada con el servicio, mientras que **Power BI Gateway** filtra la actividad de inicio de sesión específica de la puerta de enlace de datos local.
   
    ![Captura de pantalla del filtro de Inicios de sesión con el campo Aplicaciones resaltado.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar los datos

También se puede [descargar un informe de inicio de sesión](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) en cualquiera de los dos formatos: un archivo CSV o un archivo JSON.

![Captura de pantalla del botón de descarga.](media/service-admin-access-usage/download-sign-in-data-csv.png)

En la parte superior del informe de **Inicios de sesión**, seleccione **Descargar** y luego seleccione una de las opciones siguientes:

* **CSV** para descargar un archivo CSV con los datos filtrados actualmente.

* **JSON** para descargar un archivo JSON con los datos filtrados actualmente.

## <a name="data-retention"></a>Retención de datos

Los datos relacionados con el inicio de sesión están disponibles durante 30 días como máximo. Para obtener más información, consulte las [directivas de retención de informes de Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Pasos siguientes

[Usar la auditoría dentro de su organización](service-admin-auditing.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)