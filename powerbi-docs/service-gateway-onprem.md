---
title: Puerta de enlace de datos local
description: Se trata de información general sobre la puerta de enlace de datos local para Power BI. Puede usar esta puerta de enlace para trabajar con orígenes de datos DirectQuery. También puede usar esta puerta de enlace para actualizar conjuntos de datos en la nube con datos locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 06/05/2018
ms.openlocfilehash: 8bdb249543d8d6b5b0cb7d75e3295adc751e5ab1
ms.sourcegitcommit: 9913c213d40b45ba83c6c3b3a7ef0b757800e3ad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2018
ms.locfileid: "52268352"
---
# <a name="on-premises-data-gateway"></a>Puerta de enlace de datos local

La puerta de enlace de datos local actúa como un puente, proporcionando la transferencia de datos rápida y segura entre los datos locales (datos que no están en la nube) y los servicios Power BI, Microsoft Flow, Logic Apps y PowerApps.

Puede usar una sola puerta de enlace con diferentes servicios al mismo tiempo. Si está usando Power BI y también PowerApps, puede usar una sola puerta de enlace para ambos. Depende de la cuenta con la que inicie sesión.

> [!NOTE]
> La puerta de enlace de datos local implementa la compresión de datos y el cifrado de transporte en todos los modos.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Limitaciones de conexiones activas de Analysis Services

Puede usar una conexión activa con instancias tabulares o multidimensionales.

| **Versión del servidor** | **SKU necesario** |
| --- | --- |
| 2012 SP1 CU4 o posterior |SKU Business Intelligence y Enterprise |
| 2014 |SKU Business Intelligence y Enterprise |
| 2016 |SKU estándar o superior |

* Las características de formato de nivel de celda y traducción no se admiten.
* Las acciones y los conjuntos con nombre no se exponen en Power BI, pero todavía puede conectarse a los cubos multidimensionales que también contengan acciones o conjuntos con nombre, y crear objetos visuales e informes.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>Descargar e instalar la puerta de enlace de datos local

Para descargar la puerta de enlace, seleccione **Puerta de enlace de datos** en el menú Descargas. Descargue la [Puerta de enlace de datos local](http://go.microsoft.com/fwlink/?LinkID=820925).

Tenga en cuenta que la puerta de enlace de datos local se actualiza volviendo a instalar la puerta de enlace, tal como se describe en esta sección. Siempre y cuando instale una versión más reciente de la puerta de enlace, las configuraciones existentes se mantendrán. Si instala la misma versión, se trata como una reinstalación completa y no se conserva la configuración.

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Instalar la puerta de enlace en modo personal

> [!NOTE]
> La versión Personal de la puerta de enlace solo funciona con Power BI.

Después de instalar la puerta de enlace personal, debe iniciar el **Asistente para configuración de Power BI Gateway - Personal**.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Después debe iniciar sesión en Power BI para registrar la puerta de enlace con el servicio en la nube.

![](media/service-gateway-onprem/personal-gateway-signin.png)

También debe proporcionar el nombre de usuario de Windows y la contraseña con la que se ejecutará el servicio de Windows. Puede especificar una cuenta de Windows diferente de su propia cuenta. El servicio de puerta de enlace se ejecutará con esta cuenta.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

Una vez completada la instalación, debe ir a los conjuntos de datos en Power BI y asegurarse de escribir las credenciales para los orígenes de datos locales.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Almacenar credenciales cifradas en la nube

Cuando agrega un origen de datos a la puerta de enlace, debe proporcionar las credenciales de ese origen de datos. Todas las consultas que se realicen al origen de datos se ejecutarán con estas credenciales. Las credenciales se cifran de forma segura mediante el cifrado asimétrico, para que no se puedan descifrar en la nube, antes de almacenarse en la nube. Las credenciales se envían a la máquina, que ejecuta la puerta de enlace, de forma local para descifrarse cuando se accede a los orígenes de datos.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

* [Azure Information Protection](https://docs.microsoft.com/microsoft-365/enterprise/protect-files-with-aip
) no se admite actualmente.
* [Access Online](https://products.office.com/en-us/access) no se admite actualmente.
* Los scripts de R solamente se admiten cuando la pasarela se ejecuta en modo personal.

## <a name="tenant-level-administration"></a>Administración de nivel de inquilino

Actualmente no hay un único lugar en el que los administradores de inquilinos puedan administrar todas las puertas de enlace que otros usuarios tengan instaladas y configuradas.  Si es un administrador de inquilinos, le recomendamos que solicite a los usuarios de la organización que le agreguen como administrador a cada puerta de enlace que instalen. Así, podrá administrar todas las puertas de enlace de la organización mediante la página Configuración de puerta de enlace o los [comandos de PowerShell](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters). 

## <a name="enabling-outbound-azure-connections"></a>Habilitar las conexiones salientes de Azure

La puerta de enlace de datos local se basa en Azure Service Bus para la conectividad de la nube y en consecuencia establece conexiones salientes a su región de Azure asociada. De forma predeterminada, esta es la ubicación de su inquilino de Power BI. Vea [¿Dónde se encuentra mi inquilino de Power BI?](https://powerbi.microsoft.com/en-us/documentation/powerbi-admin-where-is-my-tenant-located/)
Si un firewall está bloqueando las conexiones salientes, debe configurar el firewall para permitir conexiones salientes desde la puerta de enlace de datos local para su región de Azure asociada. Vea [Microsoft Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653) (Intervalos de IP del centro de datos de Microsoft Azure) para saber más sobre los intervalos de direcciones IP de cada centro de datos de Azure.
> [!NOTE]
> Los intervalos de direcciones IP pueden cambiar con el tiempo, así que asegúrese de descargar la información más reciente con regularidad. 

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas al instalar y configurar una puerta de enlace, asegúrese de consultar [Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md). Si cree que tiene un problema con el firewall, consulte la sección [Firewall o proxy](service-gateway-onprem-tshoot.md#firewall-or-proxy) del artículo de solución de problemas.

Si cree que tiene problemas de proxy, con la puerta de enlace, consulte [Configuración de proxy para la puerta de enlace de datos local](service-gateway-proxy.md).

## <a name="next-steps"></a>Pasos siguientes

[Administrar el origen de datos: Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Administrar el origen de datos: SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Administrar el origen de datos: SQL Server](service-gateway-enterprise-manage-sql.md)  
[Administrar el origen de datos: Oracle](service-gateway-onprem-manage-oracle.md)  
[Administrar el origen de datos: importación o actualización programada](service-gateway-enterprise-manage-scheduled-refresh.md)  
[Detalles sobre la puerta de enlace de datos local](service-gateway-onprem-indepth.md)  
[Puerta de enlace de datos local (modo personal): la nueva versión de la puerta de enlace personal](service-gateway-personal-mode.md)  
[Configuración de los valores del proxy para la puerta de enlace de datos local](service-gateway-proxy.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
