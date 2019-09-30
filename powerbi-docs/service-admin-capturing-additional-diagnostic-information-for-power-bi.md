---
title: Captura de información de diagnóstico adicional
description: Estas instrucciones ofrecen dos opciones posibles para recopilar manualmente la información de diagnóstico adicional desde el cliente web de Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ea1756b82efe6a68940ae3c5094eafc9c3ca4c7c
ms.sourcegitcommit: 57e45f291714ac99390996a163436fa1f76db427
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/26/2019
ms.locfileid: "71305866"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Captura de información de diagnóstico adicional para Power BI

En este artículo se proporcionan instrucciones para recopilar manualmente información de diagnóstico adicional desde el cliente web de Power BI.

1. Vaya a [Power BI](https://app.powerbi.com) con Microsoft Edge o Internet Explorer.

1. Presione **F12** para abrir las herramientas de desarrollo de Microsoft Edge.

   ![Captura de pantalla de la pestaña Elementos de las herramientas de desarrollo de Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Seleccione la pestaña **Red**. Obtendrá una lista del tráfico que ya se ha capturado.

   ![Captura de pantalla de la pestaña Red de las herramientas de desarrollo de Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Puede:

    * Buscar dentro de la ventana y reproducir cualquier problema que encuentre.

    * Ocultar y mostrar la ventana de herramientas de desarrollo en cualquier momento de la sesión con F12.

1. Para dejar de generar perfiles para la sesión, puede seleccionar el cuadrado rojo en la pestaña **Red** del área de herramientas de desarrollo.

   ![Captura de pantalla de la pestaña Red de las herramientas de desarrollo de Microsoft Edge con una llamada al botón Detener.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Seleccione el icono de disquete para exportar los datos como un archivo de almacenamiento HTTP (HAR).

   ![Captura de pantalla de la pestaña Red de las herramientas de desarrollo de Microsoft Edge con una llamada al icono de disquete.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Escriba un nombre de archivo y guarde el archivo HAR.

    El archivo HAR contendrá toda la información sobre las solicitudes de red entre la ventana del explorador y Power BI, por ejemplo:

    * Los identificadores de actividad de cada solicitud.

    * La marca de tiempo precisa de cada solicitud.

    * Cualquier información de error devuelta al cliente.

    Este seguimiento también contendrá los datos usados para completar los elementos visuales que se muestran en la pantalla.

1. Puede enviar el archivo HAR al soporte técnico para su revisión.

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
