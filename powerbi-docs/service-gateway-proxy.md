---
title: Configuración de los valores del proxy para la puerta de enlace de datos local
description: Información sobre la configuración de proxy para la puerta de enlace de datos local.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: ef554d7190709565610336169b4883d71970f822
ms.sourcegitcommit: b25ae650643b0a62f33d7c1741307137b9cec316
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34799565"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Configuración de los valores del proxy para la puerta de enlace de datos local
El entorno de trabajo puede requerir que pase por un proxy para acceder a Internet. Esto puede impedir que la puerta de enlace de datos local se conecte al servicio.

## <a name="does-your-network-use-a-proxy"></a>¿Usa su red un proxy?
La siguiente entrada de superuser.com describe cómo puede intentar determinar si tiene un proxy en la red.

[¿Cómo sé qué servidor proxy estoy usando? (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Ubicación del archivo de configuración y configuración predeterminada
La información de proxy se configura dentro de un archivo de configuración de .NET. La ubicación, y los nombres de archivo, será diferentes dependiendo de la puerta de enlace que esté usando.

### <a name="on-premises-data-gateway"></a>Puerta de enlace de datos local
Hay dos archivos de configuración principales que participan en la puerta de enlace de datos local.

**Configuración**

El primero es para las pantallas de configuración, que en realidad configuran la puerta de enlace. Si tiene problemas para configurar la puerta de enlace, este es el archivo al que tendrá que recurrir.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Servicio de Windows**

El segundo es para el servicio de Windows real, que interactúa con el servicio Power BI y controla las solicitudes.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>Configuración de proxy
La configuración de proxy predeterminada es la siguiente.

    <system.net>
        <defaultProxy useDefaultCredentials="true" />
    </system.net>

La configuración predeterminada funciona con la autenticación de Windows. Si el proxy usa otra forma de autenticación, debe cambiar la configuración. Si no está seguro, póngase en contacto con el administrador de la red. No se recomienda la autenticación de proxy básica y cualquier intento de usarla puede provocar errores de autenticación de proxy que resulten en la configuración incorrecta de la puerta de enlace. Use un mecanismo de autenticación de proxy más seguro para resolver.

Además de usar las credenciales predeterminadas, puede agregar un elemento <proxy> para definir la configuración del servidor proxy con más detalle. Por ejemplo, puede especificar que la puerta de enlace de datos local use siempre el proxy incluso para los recursos locales estableciendo el parámetro bypassonlocal en false. Esto puede ayudar a solucionar situaciones en las que quiere realizar un seguimiento de todas las solicitudes https que se originan en una puerta de enlace de datos local en los archivos de registro de proxy. La configuración del ejemplo siguiente especifica que todas las solicitudes deben pasar por un proxy específico con la dirección IP 192.168.1.10.

    <system.net>
        <defaultProxy useDefaultCredentials="true">
            <proxy  
                autoDetect="false"  
                proxyaddress="http://192.168.1.10:3128"  
                bypassonlocal="false"  
                usesystemdefault="true"
            />  
        </defaultProxy>
    </system.net>

Para más información acerca de la configuración de los elementos de proxy para los archivos de configuración de .NET, consulte [<defaultProxy> (Elemento, Configuración de red)](https://msdn.microsoft.com/library/kd3cf2ex.aspx).

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Cambiar la cuenta de servicio de la puerta de enlace de un usuario de dominio
Al configurar los ajustes de proxy para utilizar las credenciales predeterminadas, como se explicó anteriormente, pueden producirse problemas de autenticación con el proxy. Esto se debe a que la cuenta de servicio predeterminada es el servicio SID y no un usuario de dominio autenticado. Puede cambiar la cuenta de servicio de la puerta de enlace para permitir la autenticación correcta con el servidor proxy.

> [!NOTE]
> Se recomienda que use una cuenta de servicio administrada para evitar tener que restablecer las contraseñas. Obtenga información acerca de cómo crear una [cuenta de servicio administrada](https://technet.microsoft.com/library/dd548356.aspx) dentro de Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Cambio de la cuenta de servicio de puerta de enlace de datos local
1. Cambie la cuenta de servicio de Windows del **servicio de puerta de enlace de datos local**.
   
    La cuenta predeterminada para este servicio es *NT SERVICE\PBIEgwService*. Podrá cambiarlo a una cuenta de usuario de dominio en su dominio de Active Directory. También puede utilizar una cuenta de servicio administrada para evitar tener que cambiar la contraseña.
   
    Puede cambiar la cuenta en la pestaña **Inicio de sesión** de las propiedades del servicio de Windows.
2. Reinicie el **servicio de puerta de enlace de datos local**.
   
    Desde un símbolo del sistema de administrador, emita los siguientes comandos.
   
        net stop PBIEgwService
   
        net start PBIEgwService
3. Inicie el **configurador de la puerta de enlace de datos local**. Puede seleccionar el botón de inicio de Windows y buscar la *puerta de enlace de datos local*.
4. Inicie sesión en Power BI.
5. Restaure la puerta de enlace con su clave de recuperación.
   
    Esto permitirá a la nueva cuenta de servicio descifrar las credenciales almacenadas para los orígenes de datos.
    
> [!NOTE]
> Al cambiar la cuenta de servicio directamente mediante el panel de control de servicios, no actualiza las ACL de manera automática. Debe asegurarse de que la nueva cuenta de servicio tiene acceso a los archivos y la carpeta de instalación. Puede encontrar la carpeta de instalación de la puerta de enlace en C:Archivos de programa\Puerta de enlace de datos local. 
> 

## <a name="next-steps"></a>Pasos siguientes
[Puerta de enlace de datos local (modo personal)](service-gateway-personal-mode.md)
[Información de firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

