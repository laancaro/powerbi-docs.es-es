---
title: 'Power BI para clientes de la Administración Pública de Estados Unidos: información general'
description: Los clientes de la Administración Pública de Estados Unidos pueden agregar una suscripción de Power BI Pro a su plan gubernamental de Office 365. Obtenga información sobre cómo registrarse y revisar la disponibilidad de características en esta descripción del servicio.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: 26dabde3846ec33e2f5910de75fb8165cce6513a
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160774"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI para clientes de la Administración Pública de Estados Unidos
Este artículo está destinado a los clientes de la Administración Pública de Estados Unidos que implementan Power BI como parte de un plan de Office 365 Administración Pública. Los planes de la Administración Pública están diseñados para las necesidades únicas de las organizaciones que deben cumplir los estándares de cumplimiento y seguridad de Estados Unidos. El servicio Power BI diseñado para los clientes de la Administración Pública de Estados Unidos es distinto de la versión comercial del servicio Power BI. Las funcionalidades y diferencias en las características se describen en las siguientes secciones.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Adición de Power BI a su plan de Office 365 Administración Pública

Antes de que pueda obtener una suscripción a Power BI para la Administración Pública de Estados Unidos y asignar licencias a los usuarios, debe inscribirse en un plan de Office 365 Administración Pública. Si su organización ya tiene un plan de Office 365 Administración Pública, vaya directamente a la sección sobre cómo [adquirir una suscripción a Power BI Pro para la Administración Pública](#purchase-a-power-bi-pro-government-subscription).

### <a name="enroll-in-office-365-government-plan"></a>Inscripción en el plan de Office 365 Administración Pública

Si es un nuevo cliente, debe validar la idoneidad de la organización antes de registrarse en un plan de la Administración Pública.  Para comenzar, complete el [formulario de validación de idoneidad de Office 365 para la Administración Pública](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Para asegurarse de que selecciona el plan correcto para su organización, consulte las [descripciones del servicio Office 365 Administración Pública de Estados Unidos](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Si ya ha implementado Power BI en un entorno comercial y desea migrar a la nube de la Administración Pública de Estados Unidos, deberá agregar una nueva suscripción a Power BI Pro a su plan de Office 365 Administración Pública. A continuación, replique los datos comerciales en el servicio Power BI para la Administración Pública de Estados Unidos, quite las asignaciones de licencias comerciales de las cuentas de usuario y, a continuación, asigne una licencia de Power BI Pro para la Administración Pública a las cuentas de usuario.
>
>

### <a name="government-cloud-instances"></a>Instancias en la nube de la Administración Pública
Office 365 proporciona diversos entornos para que los organismos gubernamentales cumplan requisitos de cumplimiento variables. Consulte las descripciones del servicio vinculadas para obtener detalles específicos sobre lo que proporciona cada entorno.

* [Government Community Cloud (GCC) de Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) está diseñado para el gobierno federal, estatal y local.

* [Government Community Cloud High (GCC-High) de Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) está diseñado para las agencias federales, el sector de la defensa, la industria aeroespacial y otras organizaciones que contienen información sin clasificar controlada. Este entorno es idóneo para organizaciones de seguridad nacional y empresas con datos del reglamento internacional sobre el tráfico de armas (ITAR) o requisitos de Defense Federal Acquisition Regulations Supplement (DFARS).

* El [entorno DoD de Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) está diseñado exclusivamente para el Departamento de Defensa de Estados Unidos. 

### <a name="purchase-a-power-bi-pro-government-subscription"></a>Adquisición de una suscripción a Power BI Pro para la Administración Pública

Una vez que haya implementado Office 365, puede agregar una suscripción a Power BI. Siga las instrucciones paso a paso en [Inscripción de una organización de la Administración Pública de Estados Unidos](service-govus-signup.md#existing-office-government-cloud-customers) para comprar el servicio Power BI Pro para la Administración Pública. Compre licencias suficientes para todos los usuarios que necesiten usar Power BI y, a continuación, asigne dichas licencias a cuentas de usuario individuales.

> [!IMPORTANT]
> Power BI para la Administración Pública no está disponible como licencia gratuita. Se debe asignar una licencia de Pro a cada usuario para obtener acceso a Government Community Cloud. Si una cuenta de usuario tiene asignada una licencia gratuita, tiene autorización para obtener acceso solo a la nube comercial y surgirán problemas de autenticación y acceso. Para revisar las diferencias entre los tipos de licencia, consulte [Características del servicio Power BI por tipo de licencia](service-features-license-type.md).
>
>

## <a name="connect-to-power-bi-for-us-government"></a>Conexión a Power BI para la Administración Pública de Estados Unidos

Use una dirección URL para conectarse a Power BI para la Administración Pública de Estados Unidos que sea distinta de la utilizada por los usuarios comerciales. Para iniciar sesión en Power BI, use las direcciones URL siguientes:

| Dirección URL de la versión comercial | Dirección URL de la versión de la Administración Pública de Estados Unidos | Dirección URL del gobierno de EE. UU. para GCC High |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

Es posible que su cuenta se aprovisione en más de una nube. En ese caso, al usar Power BI Desktop, puede elegir a qué nube conectarse cuando inicie sesión.

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Conectividad entre los servicios de nube de administración pública y de Azure globales

Azure se distribuye entre varias nubes. De forma predeterminada, puede habilitar las reglas de firewall para abrir una conexión a una instancia específica de la nube, pero las redes entre nubes son diferentes.  Para la comunicación entre servicios de la nube pública y servicios de Government Community Cloud, debe configurar reglas de firewall específicas. Por ejemplo, si desea obtener acceso a instancias en la nube pública de SQL a partir de su implementación de nube de la Administración Pública de Power BI, necesita una regla de firewall en SQL. Configure reglas de firewall específicas en SQL para permitir conexiones a la nube de Azure Government para los centros de datos siguientes:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

En la nube pública, hay disponibles intervalos IP. Para obtener los intervalos IP en la nube de la Administración Pública de Estados Unidos, descargue el archivo [Rangos de direcciones IP y etiquetas de servicio de Azure: nube del gobierno estadounidense](https://www.microsoft.com/download/details.aspx?id=57063). 

Para configurar firewalls en SQL, siga los pasos que se recogen en [Creación y administración de reglas de firewall de IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilidad de características de Power BI

Para adaptarse a los requisitos de los clientes en la nube de la Administración Pública, existen algunas diferencias entre los planes de la Administración Pública y los planes comerciales. Consulte la siguiente tabla para ver qué características están disponibles en cada entorno de la Administración Pública.

|Característica |   |GCC |GCC-High |DoD|
|------|------|------|------|------|
|Administración|Licencias gratuitas|No disponible|No disponible|No disponible|
|  |Establecimiento de límites de almacenamiento de datos|Disponible|Disponible|Disponible|
|  |Uso de grupos de Active Directory para compartir y del control de acceso|Disponible|Disponible|Disponible|
|  |Auditoría a través del centro de administración de seguridad y cumplimiento de Office 365|Disponible|Disponible|Disponible|
|  |Uso compartido con usuarios externos|Disponible|Disponible|Disponible|
|  |Métricas de uso para informes y paneles|No disponible|No disponible|No disponible|
|  |Azure B2B entre GCC y la nube comercial|No disponible|No disponible|No disponible|
|Creación de informes|Creación y visualización de paneles e informes|Disponible|Disponible|Disponible|
|  |Actualización de datos programada|Disponible|Disponible|Disponible|
|  |Paneles de equipo actualizables|Disponible|Disponible|Disponible|
|  |Informes paginados|Disponible solo en USGov Texas y USGov Virginia |Disponible|En la hoja de ruta|
|  |Aplicaciones plantilla|No disponible|No disponible|No disponible|
|Conectar a datos|Importación de datos e informes de Excel|Disponible|Disponible|Disponible|
|  |Importación de datos desde archivos CSV|Disponible|Disponible|Disponible|
|  |Importación de datos de archivos de Power BI Desktop|Disponible|Disponible|Disponible|
|  |Conectividad con CDS|No disponible|No disponible|No disponible|
|  |Conector de Azure Data Lake Storage Gen2|No disponible|No disponible|No disponible|
|Administración de datos|Puerta de enlace de administración de datos|Disponible|Disponible|Disponible|
|  |Cifrado de datos en Azure SQL|Disponible|Disponible|Disponible|
|  |Cifrado de datos en Blob Storage para Power BI|Disponible|Disponible|Disponible|
|Integración entre productos|Inserción en SharePoint Online mediante el elemento web de Power BI|No disponible|No disponible|No disponible|
|  |Inserción en SharePoint Online mediante el elemento web de Embed|Disponible|Disponible|Disponible|
|  |Flujos de datos y funciones de IA|No disponible|No disponible|No disponible|
|  |Conectividad de Power Automate para alertas orientadas a datos|No disponible|No disponible|No disponible|
|  |Pestaña de Power BI en Teams|No disponible|No disponible|No disponible|
|  |Automated Machine Learning|No disponible|No disponible|No disponible|
|  |Cognitive Services|No disponible|No disponible|No disponible|
|  |Aprendizaje automático de Azure|No disponible|No disponible|No disponible|

## <a name="next-steps"></a>Pasos siguientes

* [Registro en Power BI para la Administración Pública de Estados Unidos](service-govus-signup.md)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Power BI US Government Demo</a> (Demostración de Power BI para la Administración Pública de Estados Unidos)
* [Introducción al servicio Power BI](service-get-started.md)
* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)

