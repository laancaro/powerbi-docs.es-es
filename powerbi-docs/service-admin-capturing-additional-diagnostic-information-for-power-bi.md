---
title: Capturar información de diagnóstico adicional
description: Estas instrucciones ofrecen dos opciones posibles para recopilar manualmente la información de diagnóstico adicional desde el cliente web de Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100221"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Capturar información de diagnóstico adicional para Power BI

Este artículo proporcionan instrucciones para recopilar manualmente la información de diagnóstico adicional desde el cliente web de Power BI.

1. Vaya a [Power BI](https://app.powerbi.com) con Microsoft Edge o Internet Explorer.

1. Presione **F12** para abrir las herramientas de desarrollo de Microsoft Edge.

   ![Ficha elementos de captura de pantalla de Microsoft Edge Developer tools.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Seleccione la pestaña **Red**. Obtendrá una lista del tráfico que ya se ha capturado.

   ![Pestaña red de captura de pantalla de Microsoft Edge Developer tools.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Puede:

    * Busque dentro de la ventana y reproducir cualquier problema que puede encontrarse.

    * Ocultar y mostrar ventana de herramientas del desarrollador en cualquier momento durante la sesión presionando F12.

1. Para detener la sesión de generación de perfiles, puede seleccionar el cuadrado rojo en el **red** área de herramientas de ficha del desarrollador.

   ![Pestaña de red de captura de pantalla de Microsoft Edge Developer tools con una llamada fuera el botón Detener.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Seleccione el icono de disquete para exportar los datos como un archivo de almacenamiento HTTP (HAR).

   ![Pestaña de red de captura de pantalla de Microsoft Edge Developer tools con una llamada con el icono de disquete.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Escriba un nombre de archivo y guarde el archivo HAR.

    El archivo HAR contendrá toda la información sobre las solicitudes de red entre la ventana del explorador y Power BI incluidas:

    * Los identificadores de actividad para cada solicitud.

    * La marca de tiempo precisa para cada solicitud.

    * Cualquier información de error devuelto al cliente.

    Este seguimiento también contendrá los datos usados para completar los elementos visuales que se muestran en la pantalla.

1. Puede enviar el archivo HAR al soporte técnico para su revisión.

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
