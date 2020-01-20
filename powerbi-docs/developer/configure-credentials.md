---
title: Configuración de credenciales mediante programación para Power BI
description: Procedimientos para configurar credenciales mediante programación para Power BI para la automatización
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836594"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configuración de credenciales mediante programación para Power BI

Siga estos pasos para configurar las credenciales mediante programación para Power BI.

## <a name="configure-a-credential-flow-for-data-sources"></a>Configuración de un flujo de credenciales para orígenes de datos

1. Llame a [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) (Obtener orígenes de datos) para detectar los orígenes de datos del conjunto de datos. En el cuerpo de la respuesta de cada origen de datos se incluye el tipo, los detalles de conexión, la puerta de enlace y el identificador del origen de datos.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Compile la cadena de credenciales de acuerdo con los [Ejemplos de actualización de origen de datos](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) y en función del tipo de credenciales.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Compile los detalles de la credencial.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Llame a [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Actualizar origen de datos) para establecer las credenciales, mediante la puerta de enlace y el identificador del origen de datos del paso 1 y los detalles de la credencial del paso 4.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Flujo de credenciales del origen de datos local expirado

1. [Siga los pasos 1 y 2 del escenario anterior](#configure-a-credential-flow-for-data-sources).

2. Llame a [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Obtener puerta de enlace) para recuperar la clave pública de puerta de enlace.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Cifre la cadena de credenciales con clave pública de puerta de enlace. Diferentes versiones de puerta de enlace pueden tener distintos tamaños de clave pública.
    
    Vea el ejemplo en el código del SDK, disponible en el repositorio de GitHub PowerBI-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. Compile los detalles de las credenciales con credenciales cifradas.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Llame a [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Actualizar origen de datos) para establecer las credenciales.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configuración de un nuevo origen de datos para una puerta de enlace de datos

1. Instale la [puerta de enlace de datos local](https://powerbi.microsoft.com/gateway/) en el equipo.

2. Llame a [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Obtener puertas de enlace) para recuperar el identificador y la clave pública de la puerta de enlace.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Como en el escenario anterior, compile los detalles de la credencial mediante la clave pública de la puerta de enlace recuperada en el paso [Flujo de credenciales del origen de datos local expirado](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway).

4. Compile el cuerpo de la solicitud.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
    dataSourceType: "SQL",
    connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
    credentialDetails: credentialDetails,
    dataSourceName: "my sql datasource");
    ```

5. Llame a la API [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Crear origen de datos).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="troubleshooting"></a>Solución de problemas

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>No se ha encontrado ninguna puerta de enlace ni identificador de origen de datos al llamar a Get datasources

Este problema significa que el conjunto de datos no está enlazado a una puerta de enlace. Al crear un conjunto de datos, para cada conexión de nube se crea de forma automática un origen de datos sin credenciales en la puerta de enlace en la nube del usuario. Esta puerta de enlace se usa para almacenar las credenciales para las conexiones en la nube.

Después de crear el conjunto de datos, se realiza un enlace automático entre el conjunto de datos y una puerta de enlace adecuada, que contiene los orígenes de datos coincidentes para todas las conexiones. Si no hay ninguna puerta de enlace de este tipo o varias puertas de enlace adecuadas, se produce un error en el enlace automático.

Cree los orígenes de datos locales que faltan (si es necesario) y enlácelos manualmente a una puerta de enlace mediante [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) (Enlazar a puerta de enlace).

Para detectar las puertas de enlace que se pueden enlazar, use [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) (Detectar puertas de enlace).