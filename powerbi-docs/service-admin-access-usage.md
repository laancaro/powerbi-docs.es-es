---
title: Encontrar usuarios de Power BI que hayan iniciado sesión
description: Si es un administrador de inquilinos y desea ver quién ha iniciado sesión en Power BI, puede usar los informes de acceso y uso de Azure Active Directory para aumentar la visibilidad.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: f685a900465cc0f1b635aad7609aaae4356da6b3
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54284642"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar usuarios de Power BI que hayan iniciado sesión

Si es un administrador de inquilinos y desea ver quién ha iniciado sesión en Power BI, use los [informes de acceso y uso de Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) para aumentar la visibilidad.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Este informe de actividad ofrece información útil, pero no identifica el tipo de licencia que cada usuario posee. Use el Centro de administración de Office 365 para ver licencias.

## <a name="requirements"></a>Requisitos

Cualquier usuario (incluidos los no administradores) puede ver un informe de sus propios inicios de sesión, pero debe cumplir los requisitos siguientes para ver un informe para todos los usuarios.

* El inquilino debe tener una licencia de Azure AD Premium asociada.

* Debe tener alguno de los roles siguientes: administrador global, administrador de seguridad o lector de seguridad.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Uso de Azure Portal para ver los inicios de sesión

Para ver la actividad de inicio de sesión, siga estos pasos.

1. En **Azure Portal**, seleccione **Azure Active Directory**.

1. En **Supervisión**, seleccione **Inicios de sesión**.
   
    ![Inicios de sesión de Azure AD](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre la aplicación, por **Microsoft Power BI** o **Power BI Gateway** y seleccione **Aplicar**.

    **Microsoft Power BI** filtra la actividad de inicio de sesión relacionada con el servicio, donde **Power BI Gateway** filtra la actividad de inicio de sesión específica de la puerta de enlace de datos local.
   
    ![Filtrar inicios de sesión](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar los datos

Tiene dos opciones para exportar los datos de inicio de sesión: descargar un archivo csv o usar PowerShell. En la parte superior del informe de inicio de sesión, seleccione una de las siguientes opciones:

* **Descargar** para descargar un archivo csv con los datos filtrados actualmente.

* **Script** para descargar un script de PowerShell para los datos filtrados actualmente. Puede actualizar el filtro en el script según sea necesario.

![Descargar archivo csv o script](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Retención de datos

Los datos relacionados con el inicio de sesión están disponibles durante 30 días como máximo. Para más información, consulte las [directivas de retención de informes de Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Pasos siguientes

[Usar la auditoría dentro de su organización](service-admin-auditing.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

