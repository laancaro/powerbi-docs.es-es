---
title: Creación de un certificado SSL
description: Instrucciones de la solución alternativa para crear certificados manualmente en el servidor para desarrolladores
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425445"
---
# <a name="creating-ssl-certificate"></a>Creación de un certificado SSL

Ejecute el siguiente comando para generar el certificado mediante el cmdlet New-SelfSignedCertificate de PowerShell en Windows 8 o posterior.

La herramienta requiere la instalación de OpenSSL para **Windows** **7**. La utilidad de `openssll` debe estar disponible desde la línea de comandos.

Para instalar OpenSSL, visite [https://www.openssl.org](https://www.openssl.org) o [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries).

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Creación de certificados (Mac OS X)

Normalmente, las utilidades de OpenSSL están disponibles en los sistemas operativos Mac OS X o Linux.

De lo contrario, se pueden instalar desde

el administrador de paquetes *Brew*

```cmd
brew install openssl
brew link openssl --force
```

o mediante *MacPorts*.

```cmd
sudo port install openssl
```

Después de la instalación de OpenSSL para generar un nuevo certificado, llame a:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Creación de certificados (Linux)

Las utilidades de OpenSSL no están disponibles en el sistema operativo Linux, pero puede instalarlas con los siguientes comandos.

Para el administrador de paquetes *APT*:

```cmd
sudo apt-get install openssl
```

Para *Yellowdog Updater*:

```cmd
yum install openssl
```

Para *Redhat Package Manager*:

```cmd
rpm install openssl
```

Si OpenSSL ya está disponible en el sistema operativo, llame a

```cmd
pbiviz --create-cert
```

para generar un nuevo certificado.

También puede obtenerlo en [https://www.openssl.org](https://www.openssl.org) o [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries).

## <a name="generate-certificate-manually"></a>Generación manual de certificados

Puede especificar certificados generados mediante cualquier herramienta.

Si tiene OpenSSL instalado en el sistema, puede ejecutar el siguiente comando para generar un nuevo certificado.

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Normalmente, los certificados de servidor web correspondientes a PowerBI-visuals-tools se encuentran en

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

para la instancia global de las herramientas

o bien

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

para la instancia local de estas.

Si usa el formato PEM, debe guardar el archivo de certificado como `PowerBICustomVisualTest_public.cer` y PrivateKey como `PowerBICustomVisualTest_public.key`.
Si usa el formato PFX. guarde el archivo de certificado como `PowerBICustomVisualTest_public.pfx`.

Si el archivo de certificado PFX requiere una frase de contraseña, debe especificarla en

```cmd
\PowerBI-visuals-tools\config.json
```

en la sección del servidor:

```cmd
"server":{
    "root":"webRoot",
    "assetsRoute":"/assets",
    "privateKey":"certs/PowerBICustomVisualTest_private.key",
    "certificate":"certs/PowerBICustomVisualTest_public.crt",
    "pfx":"certs/PowerBICustomVisualTest_public.pfx",
    "port":"8080",
    "passphrase":"YOUR PASSPHRASE"
}
```
