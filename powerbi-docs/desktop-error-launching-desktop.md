---
title: Resolver problemas al iniciar Power BI Desktop
description: Resolver problemas al iniciar Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f527fa17ab242f6835ca99a3ff3ef3e2525a001f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277144"
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Resolver problemas cuando no Power BI Desktop no se inicia
En **Power BI Desktop**, es posible que los usuarios que tengan instaladas y ejecuten versiones anteriores de **puertas de enlace de datos locales de Power BI** no puedan iniciar Power BI Desktop, debido a las restricciones de directiva administrativa que las puertas de enlace locales de Power BI aplican a las canalizaciones con nombre en el equipo local. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Solución de problemas relacionados con la puerta de enlace de datos local y Power BI Desktop
Existen tres opciones para solucionar el problema asociado a la puerta de enlace de datos local y habilitar el inicio de Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Solución 1: Instalar la versión más reciente de la puerta de enlace de datos local de Power BI
La versión más reciente de la puerta de enlace de datos local de Power BI no impone restricciones de canalización con nombre en el equipo local y permite iniciar Power BI Desktop correctamente. Si necesita seguir usando la puerta de enlace de datos local de Power BI, esta es la solución recomendada. Puede descargar la versión más reciente de la puerta de enlace de datos local de Power BI desde [esta ubicación](https://go.microsoft.com/fwlink/?LinkId=698863). Tenga en cuenta que el vínculo es un vínculo de descarga directa al ejecutable de instalación.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Solución 2: Desinstalar o detener el servicio Windows de la puerta de enlace de datos local de Power BI
Si ya no necesita la puerta de enlace de datos local de Power BI, puede desinstalarla, o bien detener el servicio Windows de la puerta de enlace de datos local de Power BI, para quitar la restricción de directiva y permitir el inicio de Power BI Desktop.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Solución 3: Ejecutar Power BI Desktop con privilegios de administrador
Como alternativa, puede iniciar correctamente Power BI Desktop como administrador. Se sigue recomendando instalar la versión más reciente de la puerta de enlace de datos local de Power BI, como se ha descrito anteriormente en este artículo.

Es importante tener en cuenta que Power BI Desktop se ha diseñado como una arquitectura multiproceso, y que algunos de estos procesos se comunican mediante canalizaciones con nombre de Windows. Puede haber otros procesos que interfieran con estas canalizaciones con nombre. La razón más común para este tipo interferencias es la seguridad, incluidas las situaciones donde firewalls o software antivirus podrían estar bloqueando las canalizaciones o redirigiendo el tráfico a un puerto específico. El inicio de Power BI Desktop con privilegios de administrador puede resolver ese problema. Si no es posible iniciar con privilegios de administrador, póngase en contacto con el administrador para determinar qué reglas de seguridad se están aplicando que impiden que las canalizaciones con nombre se comuniquen correctamente, e incluya Power BI Desktop en una lista blanca con sus respectivos subprocesos.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Resolver problemas al conectarse a SQL Server
Si recibe un mensaje de error similar al siguiente, al conectarse a una base de datos de SQL Server puede resolver a menudo el problema iniciando **Power BI Desktop** como administrador y, después, estableciendo la conexión de SQL Server:

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

Después de iniciar Power BI Desktop como administrador y de establecer la conexión, los archivos DLL necesarios se registrarán correctamente. Después de eso no será necesario iniciar Power BI Desktop como administrador.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Ayuda con otros problemas al iniciar Power BI Desktop
Nos esforzamos por abarcar todos los problemas posibles que se producen con **Power BI Desktop**. Revisamos con regularidad los problemas que pueden afectar a muchos clientes y los incluimos en nuestros artículos.

Si el problema al iniciar **Power BI Desktop** no está relacionado con la puerta de enlace de datos local o si las soluciones anteriores no funcionan, puede enviar una incidencia al equipo de [soporte técnico de Power BI](https://support.powerbi.com) (https://support.powerbi.com) para facilitar la identificación y resolución del problema.

Para otros problemas que puedan surgir en el futuro con **Power BI Desktop** (esperamos que no haya ninguno o muy pocos), resulta útil activar el seguimiento y recopilar los archivos de registro, para aislar e identificar mejor el problema. Para activar el seguimiento, seleccione **Archivo > Opciones y configuración > Opciones** y, a continuación, seleccione **Diagnósticos** y, finalmente, **Habilitar seguimiento** en *Opciones de diagnóstico*. Somos conscientes de que se debe ejecutar **Power BI Desktop** para poder establecer esta opción ya que es más útil para futuros problemas relacionados con el inicio de **Power BI Desktop**.

