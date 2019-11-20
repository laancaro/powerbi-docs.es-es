---
title: Adquirir y asignar licencias de Power BI Pro
description: Aprenda a comprar y asignar licencias de Power BI Pro para que los usuarios puedan acceder a contenido y colaborar con colegas en el servicio Power BI.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 72a158e2dca32d2199fcd48e2cc37bf4c90778ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873541"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Compra y asignación de licencias de usuario de Power BI Pro

Power BI Pro es una licencia de usuario individual que permite a los usuarios leer e interactuar con informes y paneles que otros usuarios han publicado en el servicio Power BI, así como compartir contenido y colaborar con otros usuarios de Power BI Pro. Solo los usuarios con una licencia de usuario de Power BI Pro pueden publicar o compartir contenido con otros usuarios o consumir contenido creado por otros usuarios, a menos que el contenido se hospede en una capacidad Power BI Premium. Para obtener más información, vea [Características de Power BI por tipo de licencia](service-features-license-type.md).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Compra y asignación de licencias de usuario de Power BI Pro

En este artículo se explica cómo comprar licencias de usuario de Power BI Pro en el Centro de administración de Microsoft 365 y después se explican dos opciones que tienen los administradores para asignar esas licencias a usuarios individuales: en el Centro de administración de Microsoft 365 y en Azure Portal (elija una opción).

### <a name="prerequisites"></a>Requisitos previos

Para comprar y asignar licencias en el Centro de administración de Microsoft 365, debe ser miembro del rol **[Administrador global o Administrador de facturación](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** en Microsoft 365.

Para asignar licencias en Azure Portal, debe ser propietario de la suscripción a Azure que se usa en Power BI para las búsquedas de Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Compra de licencias en Microsoft 365

Siga estos pasos para comprar licencias de Power BI Pro en el Centro de administración de Microsoft 365:

1. Abra el [Centro de administración de Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. En el panel de navegación, seleccione **Facturación** > **Suscripciones**.

    ![Panel de navegación](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Seleccione **Agregar suscripciones** en la esquina superior derecha de la página **Suscripciones**.

    ![Suscripción](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Busque la oferta de suscripción que le interese:

    En **Enterprise Suite**, seleccione **Office 365 Enterprise E5**.

    ![suscripción a Office E5](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    En **Otros planes**, seleccione **Power BI Pro**.

    ![Suscripción a Power BI](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Mueva el puntero por encima del botón de puntos suspensivos ( **...** ) de la suscripción que quiera y seleccione **Comprar ahora**.

    ![Comprar ahora](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Elija **Pago mensual** o **Pagar un año completo** según sus preferencias de facturación.

7. En **How many users do you want?** (¿Cuántos usuarios quiere?), escriba el número de licencias que quiera y seleccione **Check out now** (Comprar ahora) para completar la transacción.

8. Compruebe que la suscripción adquirida aparece ahora en la página **Suscripciones**.

   ![Suscripción adquirida](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Para agregar más licencias después de la compra inicial, seleccione **Power BI Pro** en la página **Suscripciones** y luego seleccione **Agregar o quitar licencias**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Asignación de licencias en el Centro de administración de Microsoft 365

Siga estos pasos para asignar licencias de Power BI Pro a cuentas de usuario individuales:

1. Abra el [Centro de administración de Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. En el panel de navegación, expanda **Usuarios** y luego seleccione **Usuarios activos**.

    ![Usuarios activos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Seleccione un usuario y después, en **Licencias de productos**, seleccione **Editar**.

    ![Editar licencias de productos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. En **Power BI Pro**, **active** la opción y luego seleccione **Guardar**.

    ![Licencias de productos activadas](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. En la cuenta seleccionada, puede comprobar en **Estado** que se ha asignado correctamente la licencia de Power BI Pro.

    ![Comprobar el estado de la licencia](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Asignación de licencias en Azure Portal

Siga estos pasos para asignar licencias de Power BI Pro a cuentas de usuario individuales:

1. Abra [Azure Portal](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. En el panel de navegación, seleccione **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. En **Azure Active Directory**, seleccione **Licencias**.

    ![Licencias](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. En **Licencias**, seleccione **Todos los productos** y luego **Power BI Pro** para mostrar la lista de usuarios con licencia.

    ![Licencias: Todos los productos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Seleccione **Asignar** para agregar una licencia de Power BI Pro a una cuenta de usuario.

    ![Asignar licencia](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Pasos siguientes

Ahora que ya ha asignado las licencias, obtenga más información sobre Power BI Pro.

[Licencias de Power BI en la organización](service-admin-licensing-organization.md)

[Encontrar usuarios de Power BI que hayan iniciado sesión](service-admin-access-usage.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
