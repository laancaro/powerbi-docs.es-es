---
title: Notificaciones de interrupción del servicio
description: Obtenga información sobre cómo recibir notificaciones por correo electrónico cuando se produzca una interrupción o degradación del servicio Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: mblythe
ms.openlocfilehash: 0bb78e29cc3e9b9792d5916050179703281aa01a
ms.sourcegitcommit: 850e7883e21190151684e32f4d957beecd08e959
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2019
ms.locfileid: "68366758"
---
# <a name="service-interruption-notifications"></a>Notificaciones de interrupción del servicio

Es fundamental tener información sobre la disponibilidad de las aplicaciones empresariales críticas. Power BI proporciona una notificación de incidentes para que pueda recibir mensajes de correo electrónico si se produce una interrupción o degradación del servicio. Aunque el Acuerdo de Nivel de Servicio (SLA) del 99,9 % de Power BI hace que estas repeticiones sean poco frecuentes, queremos asegurarnos de que esté informado. En la captura de pantalla siguiente se muestra el tipo de correo electrónico que recibirá si habilita las notificaciones:

![Correo electrónico de notificación de actualización](media/service-interruption-notifications/refresh-notification-email.png)

En este momento, se envían mensajes de correo electrónico para los siguientes _escenarios de confiabilidad_:

- Confiabilidad de apertura del informe
- Confiabilidad de actualización del modelo
- Confiabilidad de actualización de consultas

Una vez que se ha resuelto un incidente, recibirá un correo electrónico de seguimiento.

> [!NOTE]
> En la actualidad, esta característica solo está disponible para capacidades dedicadas en Power BI Premium. No está disponible para la capacidad compartida.

## <a name="enable-notifications"></a>Habilitación de notificaciones

Un administrador de inquilinos de Power BI habilita las notificaciones en el portal de administración:

1. Identifique o cree un grupo de seguridad habilitado para correo electrónico que deba recibir notificaciones.

1. En el portal de administración, seleccione **Configuración de inquilinos**. En **Configuración de ayuda y soporte técnico**, expanda **Recepción de notificaciones por correo electrónico sobre interrupciones o incidentes en el servicio**.

1. Habilite las notificaciones, escriba un grupo de seguridad y seleccione **Aplicar**.

    ![Habilitación de notificaciones del servicio](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI envía notificaciones desde la cuenta no-reply-powerbi@microsoft.com. Asegúrese de que esta cuenta esté en la lista de permitidas para que las notificaciones no terminen en una carpeta de correo no deseado.

## <a name="next-steps"></a>Pasos siguientes

[Opciones de soporte técnico de Power BI Pro y Power BI Premium](service-support-options.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)