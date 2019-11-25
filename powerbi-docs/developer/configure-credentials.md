---
title: Configuración de credenciales mediante programación para Power BI
description: Procedimientos para configurar credenciales mediante programación para Power BI para la automatización
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: 73ef45b5dbed8535b13aa557cb52929d4eea0e46
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265590"
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

3. Cifre la cadena de credenciales con la clave pública de puerta de enlace mediante el algoritmo de cifrado RSA.

    Use la clase auxiliar siguiente para el cifrado:

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

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
