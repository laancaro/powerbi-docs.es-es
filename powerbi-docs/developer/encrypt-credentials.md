---
title: Cifrado de credenciales
description: 'Tutorial: Cifrado de credenciales para orígenes de datos de puerta de enlace local'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836623"
---
# <a name="encrypt-credentials"></a>Cifrado de credenciales

Cuando se llama a [Crear origen de datos](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) o [Actualizar origen de datos](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) en una **puerta de enlace empresarial local** mediante la [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), el valor de credenciales se debe cifrar con la clave pública de la puerta de enlace.

En el ejemplo de código siguiente se muestra cómo cifrar las credenciales en .NET.

Las credenciales proporcionadas para el método EncodeCredentials siguiente deben estar en uno de los formatos siguientes en función de su tipo:

**Credenciales básicas o de Windows**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Credenciales de clave**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**Credenciales de OAuth2**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Credenciales anónimas**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Credenciales de cifrado**

Cifre el valor de las credenciales mediante la clave pública de la puerta de enlace. Diferentes versiones de puerta de enlace pueden tener distintos tamaños de clave pública.

Vea el ejemplo en el código del SDK, disponible en el repositorio de GitHub PowerBI-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)