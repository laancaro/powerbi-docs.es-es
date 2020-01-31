---
title: Always Encrypted en Power BI Report Server
description: En este artículo se explica la compatibilidad con Always Encrypted en Power BI Report Server al usar los tipos de orígenes de datos de Microsoft SQL Server y Microsoft Azure SQL Database.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76710215"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted en Power BI Report Server

En este artículo se explica la compatibilidad con Always Encrypted en Power BI Report Server al usar los tipos de orígenes de datos de Microsoft SQL Server y Microsoft Azure SQL Database. Para obtener más información sobre las funciones de Always Encrypted en SQL Server, vea el artículo [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Aislamiento de usuarios de Always Encrypted

En este momento, si un usuario tiene acceso al informe, Power BI Report Server no restringe el acceso a las columnas Always Encrypted incluidas en este.  Por lo tanto, si al servidor se le ha concedido acceso a las claves de cifrado de columna a través de la clave maestra de columna, los usuarios podrán consultar todas las columnas de los informes a los que puedan acceder.

## <a name="always-encrypted-column-usage"></a>Uso de las columnas Always Encrypted

### <a name="key-storage-strategies"></a>Estrategias de almacenamiento de claves

|Almacenamiento  |Admitido  |
|---------|---------|
|Almacén de certificados de Windows | Sí |
|Azure Key Vault | No |
| Cryptography Next Generation (CNG) | No |

### <a name="certificate-storage-and-access"></a>Almacenamiento y acceso de certificados

La cuenta que requiere acceso al certificado es la cuenta de servicio. El certificado se debe almacenar en el almacén de certificados del equipo local. Para más información, consulte:

- [Configuración de la cuenta de servicio de Report Server](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- Sección [Hacer que los certificados estén disponibles para aplicaciones y usuarios](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) del artículo de SQL Server "Creación y almacenamiento de claves maestras de columna para Always Encrypted".

### <a name="column-encryption-strategy"></a>Estrategia de cifrado de columnas

En Power BI Report Server, la estrategia de cifrado de columnas puede ser *determinista* o *aleatoria*. En la tabla siguiente se indican las diferencias, en función de la estrategia que use.

|Uso  |Determinista  |Aleatorio  |
|---------|---------|---------|
|Se puede leer tal cual en los resultados de una consulta, por ejemplo, las instrucciones SELECT. | Sí  | Sí  |
|Se puede usar como una entidad Agrupar dentro de la consulta. | Sí | No |
|Se puede usar como un campo agregado, excepto para COUNT y DISTINCT. | No, excepto para COUNT y DISTINCT. | No |
|Se puede usar como un parámetro de informe. | Sí | No |

Obtenga más información sobre las [diferencias entre el cifrado determinista y el aleatorio](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Uso de parámetros

El uso de parámetros solo se aplica al cifrado determinista.

**Parámetro de un solo valor**.  Puede usar un parámetro de un solo valor en una columna Always Encrypted.

**Parámetro de varios valores**. No puede usar un parámetro de varios valores con más de un valor en una columna Always Encrypted.

**Parámetros en cascada**. Puede usar parámetros en cascada con Always Encrypted si se cumple *todo* lo siguiente:

- Todas las columnas Always Encrypted deben estar cifradas con una estrategia determinista.
- Todos los parámetros que se usan en las columnas Always Encrypted son parámetros de un solo valor.
- En todas las comparaciones de SQL se usa el operador Es igual a (=).

## <a name="datatype-support"></a>Compatibilidad con tipos de datos

| Tipo de datos SQL | Admite el campo de lectura. | Admite el uso como elemento Agrupar por. | Agregaciones admitidas (COUNT, DISTINCT, MAX, MIN, SUM, etc.) | Admite el filtrado a través de la igualdad mediante parámetros. | Notas |
| --- | --- | --- | --- | --- | --- |
| int | Sí | Sí | COUNT, DISTINCT | Sí, como valor Integer. |   |
| FLOAT | Sí | Sí | COUNT, DISTINCT | Sí, como valor Float. |   |
| NVARCHAR | Sí | Sí | COUNT, DISTINCT | Sí, como valor Text. | El cifrado determinista debe usar una intercalación de columna con un criterio de ordenación binario 2 para columnas de caracteres. Vea el artículo de SQL Server [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) para obtener más información al respecto.  |
| varchar | Sí | Sí | COUNT, DISTINCT | No |   |
| Decimal | Sí | Sí | COUNT, DISTINCT | No |   |
| NUMERIC | Sí | Sí | COUNT, DISTINCT | No |   |
| datetime | Sí | Sí | COUNT, DISTINCT | No |   |
| datetime2 | Sí | Sí | COUNT, DISTINCT | Sí, como valor Date/Time. | Se admite si la columna no tiene ninguna precisión de milisegundos (es decir, no es datetime2(0)). |

## <a name="aggregation-alternatives"></a>Alternativas de agregación

Actualmente, las únicas agregaciones admitidas en las columnas Always Encrypted deterministas son las que usan directamente el operador Es igual a (=). Esta limitación de SQL Server se debe a la naturaleza de las columnas Always Encrypted. Los usuarios deben realizar la agregación en el informe, en lugar de la base de datos.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted en cadenas de conexión

Tendrá que habilitar Always Encrypted en la cadena de conexión de un origen de datos de SQL Server. Obtenga más información sobre cómo habilitar [Always Encrypted en consultas de la aplicación](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Pasos siguientes

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) en SQL Server y Azure SQL Database

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

