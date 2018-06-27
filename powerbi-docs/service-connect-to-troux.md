---
title: Conexión a Troux con Power BI
description: Troux para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: dbf3831264a354ec96a38751dfa7a3719c5c9f2a
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "34247950"
---
# <a name="connect-to-troux-for-power-bi"></a>Conexión a Troux para Power BI
El paquete de contenido de Troux permite visualizar el repositorio de arquitectura de empresa de maneras completamente nuevas directamente en Power BI. El paquete de contenido ofrece un conjunto de información sobre las capacidades empresariales, las aplicaciones que ofrecen estas capacidades y las tecnologías compatibles con dichas aplicaciones que pueden se pueden personalizar totalmente con Power BI.

Conéctese al [paquete de contenido de Troux](https://app.powerbi.com/getdata/services/troux) para Power BI.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.
   
   ![](media/service-connect-to-troux/getdata.png)
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![](media/service-connect-to-troux/services.png)
3. Seleccione **Troux** \> **Obtener**.
   
   ![](media/service-connect-to-troux/troux.png)
4. Especifique la dirección URL de OData de Troux. Vea los detalles sobre [cómo encontrar esos parámetros](#FindingParams) a continuación.
   
   ![](media/service-connect-to-troux/params.png)
5. En **Método de autenticación**, seleccione **Básico** , proporcione el nombre de usuario y la contraseña (distingue mayúsculas de minúsculas), y haga clic en **Iniciar sesión**.
   
    ![](media/service-connect-to-troux/creds.png)
6. Tras la aprobación, el proceso de importación se iniciará automáticamente. Cuando haya finalizado, aparecerá un nuevo panel, informes y modelo en el panel de navegación. Seleccione el panel para ver los datos importados.
   
     ![](media/service-connect-to-troux/dashboard.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](power-bi-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](service-dashboard-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o actualizarlo a petición mediante **Actualizar ahora**.

## <a name="system-requirements"></a>Requisitos del sistema
Se requiere acceso a la fuente de OData de Troux y a Troux 9.5.1 o posterior.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Búsqueda de parámetros
El equipo de atención al cliente puede proporcionarle una dirección URL de fuente de OData de Troux única para usted

## <a name="troubleshooting"></a>Solución de problemas
Si ve un error de tiempo de espera después de proporcionar las credenciales, intente conectarse de nuevo.

## <a name="next-steps"></a>Pasos siguientes
[Introducción a Power BI](service-get-started.md)

[Obtener datos en Power BI](service-get-data.md)

