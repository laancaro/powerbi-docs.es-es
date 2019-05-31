---
title: Preguntas más frecuentes acerca de Power BI Embedded
description: Examinar una lista de las preguntas más frecuentes, y sus respuestas, acerca de Power BI Embedded.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 1bdc31d550573b926d45776307b8fcade95f0dc0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222170"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Preguntas más frecuentes acerca de Power BI Embedded

* Si tiene otras preguntas, [pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/).
* ¿Sigue teniendo problemas? Visite la [página de soporte técnico de Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>General

### <a name="what-is-power-bi-embedded"></a>¿Qué es Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) permite a los desarrolladores de aplicaciones insertar impactantes informes totalmente interactivos en sus aplicaciones sin tener que crear sus propias visualizaciones de datos y controles desde cero.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>¿Quién es la público objetivo de Power BI Embedded?

Los desarrolladores y compañías de software, también conocido como independientes de software (ISV), codificación de aplicaciones.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>¿En qué se diferencian Power BI Embedded del servicio Power BI?

Power BI es una solución de análisis de software como servicio que proporciona a las organizaciones una única vista de sus datos empresariales más importantes.

Microsoft desarrolló Power BI Embedded para ISV que desean insertar objetos visuales en sus aplicaciones para ayudar a sus clientes a tomar decisiones de análisis. Esto le ahorra ISV de tener que crear la solución de su propio análisis propios. [Análisis insertados](embedding.md) permite a los usuarios de empresa tener acceso a datos empresariales y ejecutar consultas en ellos para generar información dentro de la aplicación.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>¿En qué se diferencian Power BI Premium y Power BI Embedded?

Power BI Premium está dirigida a las empresas que desean una completa solución de BI que proporciona una vista única de su organización, asociados, clientes y proveedores de capacidad. Power BI Premium ayuda a las organizaciones a tomar decisiones. Power BI Premium es un producto SaaS que permite a los usuarios consuman contenido a través de aplicaciones móviles, aplicaciones desarrolladas internamente, o en el portal de Power BI.

Power BI Embedded es para los ISV que desean insertar objetos visuales en sus aplicaciones. Power BI Embedded ayuda a los clientes tomar decisiones. Dado que Power BI Embedded es para desarrolladores de aplicaciones, los clientes de la aplicación pueden consumir contenido almacenado en la capacidad de Power BI Embedded, incluidos todos los usuarios de dentro o fuera de la organización. No se puede compartir en Power BI Embedded contenido de la capacidad a través de un solo clic publicar en Web o con un solo clic a SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>¿A quiénes recomienda Microsoft comprar Power BI Premium y a quiénes Power BI Embedded?

Microsoft recomienda que las empresas compren Power BI Premium, un nivel empresarial, la solución de BI de autoservicio en la nube. Se recomienda que los ISV compren Power BI Embedded para sus componentes de análisis insertados con tecnología de nube. Sin embargo, un cliente tiene ninguna restricción sobre qué producto desea comprar.

Puede haber algunos casos donde un ISV (normalmente grande), además de insertar una aplicación, desea usar una SKU P para lograr las ventajas adicionales del servicio Power BI preempaquetado dentro de su organización. Es posible que algunas empresas decidan usar SKU A en Azure si solo les interesa la línea de creación de aplicaciones empresariales e inserción de análisis en ellas, pero no les interesa usar el servicio Power BI ya empaquetado.

### <a name="how-many-embed-tokens-can-i-create"></a>¿Cuántos tokens de inserción puedo crear?

Insertar tokens con licencia PRO están pensados para pruebas de desarrollo, por lo que la cuenta maestra de Power BI o [entidad de servicio](embed-service-principal.md) solo se puede generar un número limitado de tokens. Para realizar inserciones en un entorno de producción, [compre una capacidad](#technical). No hay ningún límite para cuántos tokens que puede generar cuando compra una capacidad de inserción. Vaya a [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) (Características disponibles) para comprobar el valor de uso que indica el porcentaje de uso actual de Power BI Embedded.

## <a name="technical"></a>Preguntas técnicas

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>¿En qué se diferencian las SKU A de Azure y las SKU EM de Office 365?

PowerBI.com es una empresa de Software como una solución de servicio (SaaS) con muchas capacidades como colaboración social, suscripción de correo electrónico y otras características. PowerBI.com ayuda a los ISV a administrar sus soluciones de análisis insertado contenido y configuración de nivel de inquilinos.

Power BI Embedded es una plataforma como servicio (PaaS) del conjunto de desarrolladores de API puede usar para crear una solución de análisis insertados.

Esta es una lista parcial de diferencias de características.

| Destacado | Power BI Embedded | Capacidad de Power BI Premium | Capacidad de Power BI Premium |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (SKU A) | (SKU EM) | (SKU P) |
| Inserción de artefactos desde un área de trabajo de la aplicación de Power BI | Capacidad de Azure | Capacidad de Office 365 | Capacidad de Office 365 |
| Consumir informes de Power BI en una aplicación insertada | Sí | Sí | Sí |
| Consumir informes de Power BI en SharePoint | No | Sí | Sí |
| Consumir informes de Power BI en Dynamics | No | Sí | Sí |
| Consumir informes de Power BI en Teams (excluye la aplicación móvil) | No | Sí | Sí |
| Acceso al contenido con una licencia gratuita de Power BI en Powerbi.com y Power BI Mobile | No | No | Sí |
| Acceso al contenido con una licencia gratuita de Power BI insertada en aplicaciones de MS Office | No | Sí | Sí |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI ahora ofrece tres SKU que se pueden insertar: SKU A, SKU EM y SKU P. ¿Cuál debo comprar para mi escenario?

|  |SKU A (Power BI Embedded)  |SKU EM (Power BI Premium)  |SKU P (Power BI Premium)  |
|---------|---------|---------|---------|
|Comprar  |Azure Portal |Office |Office |
|Casos de uso | Insertar contenido en su propia aplicación | <li> Insertar contenido en su propia aplicación <br><br><br> <li> Insertar contenido en aplicaciones de MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (se excluyen las aplicaciones móviles)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Insertar contenido en su propia aplicación <br><br><br> <li> Insertar contenido en aplicaciones de MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (se excluyen las aplicaciones móviles)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> Compartir contenido con usuarios de Power BI mediante el [servicio Power BI](https://powerbi.microsoft.com/)  |
|Facturación |Cada hora |Mensual |Mensualmente |
|Asignación  |Sin asignación |Anualmente  |Mensual o anual |
|Diferenciación |Elasticidad total: se puede escalar y reducir verticalmente, pausar y reanudar recursos en Azure Portal o a través de API  |Puede usar para insertar contenido en SharePoint Online y Microsoft Teams (excluye la aplicación móvil) |Combinar la inserción en aplicaciones y utilizar el servicio Power BI en la misma capacidad |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>¿Cuáles son los requisitos previos para crear una capacidad de PBIE en Azure?

* Inicie sesión en el directorio de su organización (no se admiten las cuentas de Microsoft).
* Debe tener un inquilino de Power BI, es decir, al menos un usuario en el directorio ha registrado en Power BI. 
* Debe tener una suscripción a Azure en el directorio de su organización.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>¿Cómo puedo supervisar el uso de funcionalidad de Power BI Embedded?

* Con el [portal de administración de Power BI](../service-admin-portal.md#power-bi-embedded).

* Mediante la descarga de la [aplicación de métricas](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) de Power BI.

* Con los [registros de diagnóstico de Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>¿Puede escalar automáticamente mi capacidad para ajustarse al consumo de mi aplicación?

Aunque hay no ahora de escalado automático, todas las API están disponibles para escalar en cualquier momento.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>¿Por qué al crear, escalar o reanudar una capacidad, esta pasa a un estado suspendido?

Aprovisionamiento de capacidad (escala/reanudar o crear) puede producir un error. Puede usar la obtención de detalles API para comprobar el estado de aprovisionamiento de una capacidad: [Capacities - Get Details](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails) (Capacidades: Obtener detalles).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>¿Puedo crear solo las capacidades de Power BI Embedded en una región específica?

Con la característica [Multi-Geo (versión preliminar)](embedded-multi-geo.md), puede adquirir una [capacidad de Power BI Embedded](azure-pbie-create-capacity.md) en una región distinta de la ubicación del inquilino principal de Power BI.

### <a name="how-can-i-find-my-pbi-tenant-region"></a>¿Cómo puedo encontrar mi región del inquilino PBI?

Puede usar el portal de PBI para buscar la región del inquilino de PBI.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > Acerca de Power BI

![Acerca de Power BI](media/embedded-faq/about-01.png)
![Región del inquilino](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>¿Qué admite el canal de proveedor de soluciones en la nube (CSP)?

* Puede crear PBIE en su inquilino con el tipo de suscripción de CSP.
* La cuenta de asociado puede iniciar sesión en el inquilino del cliente y adquirir PBIE para dicho inquilino especificando el usuario del inquilino de cliente como administrador de capacidad de Power BI.

### <a name="why-do-i-get-an-unsupported-account-message"></a>¿Por qué aparece un mensaje de cuenta no compatible?

Power BI requiere que se registre con una cuenta de la organización. No se admite al intentar iniciar sesión en Power BI mediante una cuenta de Microsoft.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>¿Puedo usar las API para crear y administrar las capacidades de Azure?

Sí, hay cmdlets de Powershell y API de REST de Azure Resource Manager puede usar para crear y administrar recursos PBIE.

* [API de REST](https://docs.microsoft.com/rest/api/power-bi-embedded/)
* [Cmdlets de PowerShell](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>¿Qué es el rol de capacidad dedicada de PBI Embedded en una solución de PBI Embedded?

Para [promueva su solución a producción](embed-sample-for-customers.md#move-to-production), debe asignar el contenido de Power BI (área de trabajo de aplicación) que usa la aplicación a una capacidad de Power BI Embedded (un SKU).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>¿En qué regiones de Azure está incrustado PBI disponible?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager). Consulte el administrador de disponibilidad de productos.

16 regiones disponibles (las mismas que Power BI)

* EE. UU. (6): Este de EE. UU., Este de EE. UU. 2, Centro y norte de EE. UU., Centro y sur de EE. UU., Oeste de EE. UU., Oeste de EE. UU. 2
* Europa (2): Europa del Norte, Europa Occidental
* Asia Pacífico (2): Sudeste Asiático, Asia Oriental
* Brasil (1): Sur de Brasil
* Japón (1): Este de Japón
* Australia (1): Sudeste de Australia
* India (1): Oeste de la India
* Canadá (1): Centro de Canadá
* Reino Unido (1): Sur de Reino Unido

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>¿Qué es modelo de autenticación del Power BI Embedded?

Power BI Embedded sigue usando Azure AD para la autenticación de usuario maestro (un usuario de Power BI Pro con licencia designado) o con [serviceprincipal](embed-service-principal.md) para autenticar la aplicación dentro de Power BI.  

 Un ISV puede implementar su propia autenticación y autorización para sus aplicaciones.

Puede usar el directorio existente si ya tiene un inquilino de Azure AD. También puede crear un nuevo inquilino de Azure AD para la seguridad del contenido de aplicación insertada.

Para obtener un token de AAD, puede usar una de las [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Existen bibliotecas de cliente para varias plataformas.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Mi aplicación ya usa AAD para la autenticación de usuario. ¿Cómo se puede usar esta identidad al autenticarse en Power BI en un escenario en el que el usuario posee los datos?

Es estándar en nombre del flujo de OAuth (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Deberá configurar la aplicación para que requiera permisos de Power BI service (con los ámbitos necesarios). Una vez que un token de usuario a la aplicación, basta con llamar a ADAL API AcquireTokenAsync mediante el acceso de usuario del token y especifique la dirección URL de recursos de Power BI como el identificador de recurso:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>¿Qué objeto que es el Id. de objeto de entidad de servicio?

El *Id. de objeto* desde la pantalla principal de una aplicación registrada es el identificador de objeto para la aplicación.

El objeto de identificador se encuentra en la *aplicación administrada en directorio local > propiedades* sección es el identificador de objeto de entidad de servicio debe usar. Este Id. de objeto es para hacer referencia a una entidad de servicio para las operaciones o realizar cambios en el objeto de entidad de servicio identificador. Como la aplicación de una entidad de servicio como un administrador a un área de trabajo.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>¿En qué se diferencia Power BI Embedded de otros servicios de Azure?

Debe tener una cuenta de Power BI antes de adquirir Power BI Embedded en Azure. La región de Power BI Embedded implementado determina su cuenta de Power BI. Administre su recurso de Power BI Embedded en Azure para:

* Escalar y reducir verticalmente
* Agregar administradores de capacidad
* Pausar y reanudar el servicio

Utilice PowerBI.com para asignar o desasignar áreas de trabajo a su capacidad de Power BI Embedded.

### <a name="what-are-the-supported-deploy-regions"></a>¿Cuáles son las admitidas implementa regiones?

Sudeste de Australia, Sur de Brasil, Centro de Canadá, Este de EE. UU. 2, India occidental, Japón Oriental, Centro y norte de EE. UU., Europa del Norte, Centro y Sur de EE. UU., Asia Suroriental, Sur de Reino Unido, Europa Occidental, Oeste de EE. UU. y Oeste de EE. UU. 2.

### <a name="what-content-pack-data-types-can-you-embed"></a>¿Qué tipos de datos del paquete de contenido puede insertar?

Le *no* incrustar **paneles** y **iconos** crea a partir de conjuntos de datos del paquete de contenido. Sin embargo, le *puede* incrustar **informes** crea a partir de un conjunto de datos del paquete de contenido.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>¿Qué es la diferencia entre el uso de vs de seguridad de nivel de fila (RLS). filtros de JavaScript?

Suele haber confusión en torno al usar RLS frente a filtros de JavaScript, porque es un método acerca de cómo controlar lo que puede ver un usuario específico y el otro es sobre la optimización de la vista del usuario.

En RLS, el desarrollador de ISV controla el filtrado de datos como parte de la creación del modelo y la generación de tokens de inserción. El usuario final ve solo lo que el ISV permite que vea el usuario. En este caso, el usuario puede elegir ver menos de lo que se filtra, pero no podrá omitir la configuración de RLS y ver más de lo que se permite.

Filtrado de lado cliente (JavaScript), el ISV puede decidir lo que ve el usuario final en la vista inicial, pero no pueden controlar los cambios que el usuario final puede aplicar a la propia vista. Puesto que el usuario del código de cliente de Javascript puede desencadenar el filtrado en el back-end de datos, no puede considerarse segura.

Para más información, consulte [RLS frente a los filtros de JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>¿Cómo se administran los permisos para las entidades de servicio con Power BI?

Una vez que habilite [serviceprincipal](embed-service-principal.md) para usar con Power BI, los permisos de AD de la aplicación no surten efecto ya. Los permisos de la aplicación se administrarán desde el portal de administración de Power BI.

Las entidades de servicio heredan de su grupo de seguridad los permisos correspondientes a todas las opciones de configuración del inquilino de Power BI. Para restringir los permisos, crear un grupo de seguridad dedicado para las entidades de servicio y agregarlo a la **excepto los grupos de seguridad específicos** lista para la configuración de Power BI pertinente, habilitada.

Esto es importante cuando se agrega la entidad de servicio como un **administrador** a la nueva área de trabajo. Puede administrar esta tarea a través de las [API](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) o con el servicio Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>¿Cuándo se usa un identificador de aplicación frente a un identificador de objeto de entidad de servicio?

El **[identificador de aplicación](embed-sample-for-customers.md#application-id)** se usa para crear el token de acceso cuando se pasa el identificador de aplicación para la autenticación.

Para hacer referencia a una entidad de servicio para operaciones o realizar cambios, use el **[identificador de objeto de entidad de servicio](embed-service-principal.md#how-to-get-the-service-principal-object-id)** ; por ejemplo, para aplicar una entidad de servicio como un administrador a un área de trabajo.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>¿Se puede administrar una puerta de enlace de datos local con la entidad de servicio?

No se puede administrar una puerta de enlace de datos local (puerta de enlace de datos) mediante la [entidad de servicio](embed-service-principal.md) como se hace con una cuenta maestra.

Con una cuenta maestra, puede instalar una puerta de enlace de datos, agregarle usuarios, conectarse a orígenes de datos y realizar otras tareas administrativas.

Con la entidad de servicio, puede configurar la [seguridad de nivel de fila (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview) mediante un origen de datos de conexión dinámica local de SQL Server Analysis Services (SSAS). De este modo puede administrar usuarios y su acceso a los datos de SSAS cuando se realiza la integración con **Power BI Embedded** mediante una entidad de servicio.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>¿Se puede iniciar sesión en el servicio Power BI con la entidad de servicio?

No, no se puede iniciar sesión en Power BI con la entidad de servicio.

Además, tampoco se puede consumir contenido como un usuario en las aplicaciones externas (insertadas como SaaS), solo cuando se genera un token de inserción.

### <a name="what-are-the-best-practices-to-improve-performance"></a>¿Cuáles son los procedimientos recomendados para mejorar el rendimiento?

[Procedimientos recomendados de rendimiento de Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licencias

### <a name="how-do-i-purchase-power-bi-embedded"></a>¿Cómo se adquiere Power BI Embedded?

Power BI Embedded está disponible a través de Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>¿Qué ocurre si ya he adquirido Power BI Premium y ahora deseo algunas Power BI Embedded en las ventajas de Azure?

Los clientes seguirán pagando conforme para las compras de Power BI Premium existentes hasta el final del término de contrato actual y, a continuación, en ese momento, pueden cambiar sus compras de Power BI Premium según sea necesario.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>¿Hay que comprar Power BI Premium para obtener acceso a Power BI Embedded?

No, Power BI Embedded incluye la capacidad basada en Azure que necesita para implementar y distribuir su solución a los clientes.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>¿Cuál es el compromiso de compra de Power BI Embedded?

Los clientes pueden cambiar su uso cada hora. No hay ningún compromiso mensual o anual para el servicio Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>¿Cómo se muestra el uso de Power BI Embedded en mi factura?

Power BI Embedded factura a un precio por hora predecible en función del tipo de nodos. Se le facturará siempre que el recurso esté activo, incluso si no hay ningún uso. Debe pausar el recurso para detener la facturación.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>¿Quién necesita una licencia de Power BI Pro para Power BI Embedded y por qué?

Necesita una licencia de Power BI Pro o [serviceprincipal](embed-service-principal.md) para usar las API de REST. Para agregar informes a un área de trabajo de Power BI, un analista que necesita una licencia de Power BI Pro o el servicio principal. Para administrar el inquilino de Power BI y la capacidad, se requiere un administrador tiene una licencia de Power BI Pro.

Dado que Power BI Embedded permite el uso de portal de Power BI para administrar y validar contenido insertado, la licencia de Power BI Pro es necesario para autenticar la aplicación en PowerBI.com para obtener acceso a los informes de los repositorios correctos.

Pero para [crear o editar informes insertados](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) dentro de la aplicación, el usuario final no necesita una licencia Pro, porque no es imprescindible ser un usuario de Power BI.

### <a name="can-i-get-started-for-free"></a>¿Puedo empezar de forma gratuita?

Sí, puede usar sus [créditos de Azure](https://azure.microsoft.com/free/) para Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>¿Puedo usar una versión de evaluación gratuita de Power BI Embedded en Azure?

Puesto que Power BI Embedded es una parte de Azure, es posible usar el servicio con el [crédito de 200 dólares que recibió al registrarse para Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>¿Power BI Embedded está disponible para nubes nacionales (Gobierno de EE. UU., Alemania, China)?

Power BI Embedded también está disponible para [nubes nacionales](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>¿Está Power BI Embedded disponible para entidades educativas y sin ánimo de lucro?

No hay ningún precios para entidades sin ánimo de lucro y educativas de Azure especial.

## <a name="power-bi-workspace-collection"></a>Colección de áreas de trabajo de Power BI

### <a name="what-is-power-bi-workspace-collection"></a>¿Qué es la colección de áreas de trabajo de Power BI?

**Colección de área de trabajo de BI de Power** (**Power BI Embedded** versión 1) es una solución basada en la **colección de área de trabajo de Power BI** recursos de Azure. Esta solución le permite crear aplicaciones de **Power BI Embedded** para sus clientes con contenido de Power BI en la solución **Colección de áreas de trabajo de Power BI**, API dedicadas y claves de colecciones de áreas de trabajo para autenticar la aplicación en Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>¿Puedo migrar de la colección de áreas de trabajo de Power BI a Power BI Embedded?

1. Puede usar la herramienta de migración para clonar el contenido de la **colección de áreas de trabajo de Power BI** en Power BI: https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Comience con la prueba de concepto de la aplicación de **Power BI Embedded** que usa el contenido de Power BI.

3. Cuando esté listo para producción, adquiera una capacidad dedicada de **Power BI Embedded** y asigne el contenido de Power BI (área de trabajo) a dicha capacidad.

    > [!Note]
    > Puede seguir usando la **colección de áreas de trabajo de Power BI** al compilar en paralelo con una solución de **Power BI Embedded**. Cuando esté listo, puede mover el cliente a la nueva solución de **Power BI Embedded** y retirar la solución **Colección de áreas de trabajo de Power BI**.

Para más información, vea [Migración de contenido de la colección de áreas de trabajo de Power BI a Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>¿Es la colección de área de trabajo de Power BI en una ruta de degradación?

Sí, pero los clientes que ya está usando el **colección de área de trabajo de Power BI** solución puede seguir usándolo hasta que la degradación. Los clientes también pueden crear colecciones de áreas de trabajo y cualquier aplicación de **Power BI Embedded** en las que todavía se use la solución **Colección de áreas de trabajo de Power BI**.

Sin embargo, esto también significa que no se agregan nuevas características a una **colección de área de trabajo de Power BI** soluciones. Le animamos a los clientes a planear su migración a la nueva **Power BI Embedded** solución.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>¿Cuándo se interrumpe el soporte para la colección de áreas de trabajo de Power BI?

Los clientes que ya usan la solución de las **colecciones de áreas de trabajo de Power BI** pueden seguir usándola hasta el final de junio de 2018 o hasta que finalice su contrato de soporte técnico.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>¿En qué regiones puedo crear una colección de área de trabajo de PBI?

Las regiones disponibles son Sudeste de Australia, Sur de Brasil, Centro de Canadá, Este de EE. UU. 2, Japón Oriental, Centro y norte de EE. UU., Europa del Norte, Centro y Sur de EE. UU., Asia Suroriental, Sur de Reino Unido, Europa Occidental, India occidental y Oeste de EE. UU.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>¿Por qué debo migrar de la Colección de áreas de trabajo de Power BI a Power BI Embedded?

Hay algunas nuevas **Power BI Embedded** sus características y funcionalidades que no se puede hacer con **colección de área de trabajo de Power BI**.

Algunas de las características son:
* Se admiten todos los orígenes de datos PBI. Solo dos **colección de área de trabajo de Power BI** se admiten orígenes de datos. 
* Las nuevas características como Preguntas y respuestas, actualizaciones, marcadores, inserción de paneles e iconos y menús personalizados solo se admiten en la solución **Power BI Embedded**.
* Modelo de facturación de capacidad.

## <a name="embedding-setup-tool"></a>Herramienta de configuración de inserción

### <a name="what-is-the-embedding-setup-tool"></a>¿Qué es la herramienta de configuración de inserción?

La [herramienta de configuración de inserción](https://aka.ms/embedsetup) permite empezar a trabajar rápidamente y descargar una aplicación de ejemplo para empezar con la inserción con Power BI.

### <a name="which-solution-should-i-choose"></a>¿Qué solución debería elegir?

* La [inserción para los clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Ejecute la solución de [inserción para los clientes](https://aka.ms/embedsetup/AppOwnsData).
* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Ejecute la solución de [inserción para la organización](https://aka.ms/embedsetup/UserOwnsData).

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>He descargado la aplicación de ejemplo, ¿qué solución debo elegir?

Si está trabajando con la experiencia de **inserción para los clientes**, guarde el archivo *PowerBI-Developer-Samples.zip* y descomprímalo. Después, abra la carpeta *PowerBI-Developer-Samples-master\App Owns Data* y ejecute el archivo *PowerBIEmbedded_AppOwnsData.sln*.

Si está trabajando con la experiencia de **inserción para la organización**, guarde el archivo *PowerBI-Developer-Samples.zip* y descomprímalo. Después, abra la carpeta *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* y ejecute el archivo *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>¿Cómo puedo editar mi aplicación registrada?

Para obtener información sobre cómo editar aplicaciones registradas en Azure AD, consulte [Inicio rápido: Actualización de una aplicación en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>¿Cómo puedo editar los datos o el perfil de usuario de Power BI?

[Aquí](https://docs.microsoft.com/power-bi/service-basic-concepts) encontrará información sobre cómo editar los datos de Power BI.

Para obtener más información, vea [Solución de problemas de una aplicación insertada](embedded-troubleshoot.md).

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)
