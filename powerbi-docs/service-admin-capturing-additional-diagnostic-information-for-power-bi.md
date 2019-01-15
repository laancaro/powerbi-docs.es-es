---
title: Captura de información de diagnóstico adicional
description: Captura de información de diagnóstico adicional
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: b38e1e73b9829b4b86237f826b4245a6b95cfa36
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292945"
---
# <a name="capturing-additional-diagnostic-information"></a>Captura de información de diagnóstico adicional
## <a name="capturing-additional-diagnostic-information-for-power-bi"></a>Captura de información de diagnóstico adicional para Power BI
Estas instrucciones ofrecen dos opciones posibles para recopilar manualmente la información de diagnóstico adicional desde el cliente web de Power BI.  Debe seguir solo una de estas opciones.

## <a name="network-capture---edge--internet-explorer"></a>Captura de red: Edge e Internet Explorer
1. Vaya a [Power BI](https://app.powerbi.com) con Microsoft Edge o Internet Explorer.
2. Abra las herramientas de desarrollo de Edge presionando F12.
3. Se abrirá la ventana Herramientas de desarrollo: 
   
   ![Herramientas de desarrolladores](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)
4. Cambie a la pestaña Red. Obtendrá una lista del tráfico que ya se ha capturado. 
   
   ![Pestaña de red perimetral](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)
5. Puede buscar dentro de la ventana y reproducir cualquier problema que encuentre. Puede ocultar y mostrar la ventana de herramientas de desarrollo en cualquier momento de la sesión si presiona F12.
6. Para detener la captura, puede seleccionar el cuadrado rojo en la pestaña Red del área de herramientas de desarrollo.
   
   ![Detener la captura](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)
7. Seleccione el icono de disquete para **Exportar como HAR**
   
   ![Exportar el archivo](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)
8. Escriba un nombre de archivo y guarde el archivo HAR.
   
    El archivo HAR contendrá toda la información sobre las solicitudes de red entre la ventana del explorador y Power BI.  Esto incluye los identificadores de actividad para cada solicitud, la marca de tiempo precisa para cada solicitud y cualquier información de error devuelta al cliente.  Este seguimiento también contendrá los datos usados para completar los elementos visuales que se muestran en la pantalla.
9. Puede enviar el archivo HAR al soporte técnico para su revisión.

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)

