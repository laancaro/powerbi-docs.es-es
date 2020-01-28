---
title: Resolver problemas al iniciar Power BI Desktop
description: Resolver problemas al iniciar Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 67c83f2cc0eb81e90f447961ed178a04e97e050e
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160912"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Solución de problemas de apertura de Power BI Desktop

En Power BI Desktop, es posible que los usuarios que tengan instaladas y ejecuten versiones anteriores de *puertas de enlace de datos locales de Power BI* no puedan abrir Power BI Desktop, debido a las restricciones de directiva administrativa que las puertas de enlace locales de Power BI aplican a las canalizaciones con nombre en el equipo local.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Solución de problemas relacionados con la puerta de enlace de datos local y Power BI Desktop

Tiene tres opciones para solucionar el problema asociado a la puerta de enlace de datos local y habilitar la apertura de Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Solución 1: Instalar la versión más reciente de la puerta de enlace de datos local de Power BI

La versión más reciente de la puerta de enlace de datos local de Power BI no impone restricciones de canalización con nombre en el equipo local y permite abrir Power BI Desktop correctamente. Si necesita seguir usando la puerta de enlace de datos local de Power BI, la solución recomendada es actualizarla. Puede descargar la [versión más reciente de la puerta de enlace de datos local de Power BI](https://go.microsoft.com/fwlink/?LinkId=698863). El vínculo es un vínculo de descarga directa al ejecutable de instalación.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Solución 2: Desinstalar o detener el servicio Microsoft de la puerta de enlace de datos local de Power BI

Puede desinstalar la puerta de enlace de datos local de Power BI si ya no la necesita. O bien, puede detener el servicio Microsoft de la puerta de enlace de datos local de Power BI, que quita la restricción de la directiva y permite que se abra Power BI Desktop.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Solución 3: Ejecutar Power BI Desktop con privilegios de administrador

En su lugar, puede iniciar correctamente Power BI Desktop como administrador, lo que también permite la apertura correcta de Power BI Desktop. Se sigue recomendando instalar la versión más reciente de la puerta de enlace de datos local de Power BI, como se ha descrito anteriormente.

Power BI Desktop se ha diseñado como una arquitectura multiproceso, y algunos de estos procesos se comunican mediante canalizaciones con nombre de Windows. Puede haber otros procesos que interfieran con estas canalizaciones con nombre. La razón más común para este tipo de interferencias es la seguridad, incluidas las situaciones donde firewalls o software antivirus podrían bloquear las canalizaciones o redirigir el tráfico a un puerto específico. La apertura de Power BI Desktop con privilegios de administrador puede resolver ese problema. Si no puede abrir con privilegios de administrador, pida a este que determine qué reglas de seguridad impiden a las canalizaciones con nombre comunicarse correctamente. A continuación, incluya Power BI Desktop en la lista de permitidos y sus subprocesos correspondientes.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Resolver problemas al conectarse a SQL Server

Al intentar conectarse a una base de datos de SQL Server, es posible que encuentre un mensaje de error similar al siguiente texto:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

A menudo puede resolver el problema si abre Power BI Desktop como administrador antes de establecer la conexión a SQL Server.

Después de abrir Power BI Desktop como administrador y de establecer la conexión, los archivos DLL necesarios se registrarán correctamente. Después de eso no será necesario abrir Power BI Desktop como administrador.

## <a name="get-help-with-other-launch-issues"></a>Obtener ayuda con otros problemas de inicio

Nos esforzamos por abarcar todos los problemas posibles que se producen con Power BI Desktop. Revisamos con regularidad los problemas que pueden afectar a muchos clientes y los incluimos en nuestros artículos.

Si el problema al abrir Power BI Desktop no está relacionado con la puerta de enlace de datos local o si las soluciones anteriores no funcionan, puede enviar una incidencia al equipo de *soporte técnico de Power BI* (<https://support.powerbi.com>) para facilitar la identificación y resolución del problema.

Si encuentra otros problemas en el futuro con Power BI Desktop, es útil activar el seguimiento y recopilar archivos de registro. Los archivos de registro ayudan a aislar e identificar el problema. Para activar el seguimiento, elija **Archivo** > **Opciones y configuración** > **Opciones**, seleccione **Diagnóstico** y, a continuación, seleccione **Habilitar seguimiento**. Se debe ejecutar Power BI Desktop para poder establecer esta opción, pero resulta útil para futuros problemas relacionados con la apertura de Power BI Desktop.
