---
title: Adquirir y asignar licencias de Power BI Pro
description: Obtenga información sobre cómo adquirir y asignar licencias de Power BI Pro para que los usuarios puedan acceder a todo el contenido y las funcionalidades del servicio Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: quickstart
ms.date: 10/21/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0784976e1404247d69415bb398f83cbb73ab98a8
ms.sourcegitcommit: 35d763dfc75c229204d36fd8b35c1e860786b707
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52331928"
---
# <a name="purchase-and-assign-power-bi-pro-licenses"></a>Adquirir y asignar licencias de Power BI Pro

Power BI Pro es una licencia individual que permite acceder a todo el contenido y las funcionalidades del servicio Power BI, incluida la capacidad de compartir el contenido y colaborar con otros usuarios de Pro. Solo los usuarios de la versión Pro pueden publicar y consumir contenido en áreas de trabajo de las aplicaciones, compartir paneles y suscribirse a paneles e informes. Para obtener más información, vea [Características de Power BI por tipo de licencia](service-features-license-type.md).

En este artículo primero se explica cómo adquirir licencias de Power BI Pro en Office 365. Luego se explican las dos opciones disponibles para asignar esas licencias a usuarios individuales: Office 365 y Azure (se elige una opción).

## <a name="prerequisites"></a>Requisitos previos

Debe ser miembro del rol de [**administrador global** o **administrador de facturación**](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d?ui=en-US&rs=en-US&ad=US) en Office 365.

Para asignar licencias en Azure, debe ser propietario de la suscripción de Azure que usa Power BI para las búsquedas de Active Directory.

## <a name="purchase-licenses-in-office-365"></a>Adquirir licencias en Office 365

Siga estos pasos para adquirir licencias de Power BI Pro:

1. Abra el [centro de administración de Office 365](https://portal.office.com/adminportal/home#/homepage).

2. En el panel de navegación izquierdo, seleccione **Facturación**  > **Suscripciones**.

    ![Panel de navegación](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Seleccione **Agregar suscripciones** en la esquina superior derecha de la página **Suscripciones**.

    ![Suscripción](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Busque la oferta de suscripción que le interese:

    En **Enterprise Suite**, seleccione **Office 365 Enterprise E5**.

    ![suscripción a Office E5](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    En **Otros planes**, seleccione **Power BI Pro**.

    ![Suscripción a Power BI](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Mueva el puntero por encima del botón de puntos suspensivos (**...**) de la suscripción que quiera y seleccione **Comprar ahora**.

    ![Comprar ahora](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Elija **Pago mensual** o **Pagar un año completo** según sus preferencias de facturación.

7. En **How many users do you want?** (¿Cuántos usuarios quiere?), escriba el número de licencias que quiera y seleccione **Check out now** (Comprar ahora) para completar la transacción.

8. Compruebe que la suscripción adquirida aparece ahora en la página **Suscripciones**.

   ![Suscripción adquirida](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Para agregar más licencias después de la compra inicial, seleccione **Power BI Pro** en la página **Suscripciones** y luego seleccione **Agregar o quitar licencias**.

## <a name="assign-licenses-in-office-365"></a>Asignar licencias en Office 365

Siga estos pasos para asignar licencias de Power BI Pro a cuentas de usuario individuales:

1. Abra el [centro de administración de Office 365](https://portal.office.com/adminportal/home#/homepage).

2. En el panel de navegación izquierdo, expanda **Usuarios** y luego seleccione **Usuarios activos**.

    ![Usuarios activos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Seleccione un usuario y después, en **Licencias de productos**, seleccione **Editar**.

    ![Editar licencias de productos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. En **Power BI Pro**, **active** la opción y luego seleccione **Guardar**.

    ![Licencias de productos activadas](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. En la cuenta seleccionada, puede comprobar en **Estado** que se ha asignado correctamente la licencia de Power BI Pro.

    ![Comprobar el estado de la licencia](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

## <a name="assign-licenses-in-azure"></a>Asignar licencias en Azure

Siga estos pasos para asignar licencias de Power BI Pro a cuentas de usuario individuales:

1. Abra [Azure Portal](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. En la barra de navegación izquierda, seleccione **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. En **Azure Active Directory**, seleccione **Licencias**.

    ![Licencias](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. En **Licencias**, seleccione **Todos los productos** y luego **Power BI Pro** para mostrar la lista de usuarios con licencia.

    ![Licencias: Todos los productos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Seleccione **Asignar** para agregar una licencia de Power BI Pro a una cuenta de usuario adicional.

    ![Asignar licencia](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Pasos siguientes

Ahora que ya ha asignado las licencias, obtenga más información sobre Power BI Pro.

[Licencias de Power BI en la organización](service-admin-licensing-organization.md)

[Encontrar usuarios de Power BI que hayan iniciado sesión](service-admin-access-usage.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
