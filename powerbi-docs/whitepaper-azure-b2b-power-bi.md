---
title: Distribuir el contenido de Power BI a usuarios externos invitados mediante Azure Active Directory B2B
description: Notas del producto que se describen cómo usar Azure Active Directory B2B para distribuir Power BI a usuarios externos invitados
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 79b8ae80413cc54b065d12bf36ccb1651a670812
ms.sourcegitcommit: ec5b6a9f87bc098a85c0f4607ca7f6e2287df1f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051594"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuir el contenido de Power BI a usuarios externos invitados mediante Azure Active Directory B2B

**Resumen:** Se trata de un notas del producto describe cómo distribuir contenido a los usuarios fuera de la organización mediante la integración de Azure Active Directory negocio a negocio (B2B de Azure AD).

**Escritores de:** Lukasz Pawlowski, Kasper de Jonge

**Revisores técnicos:** ADAM Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Shenhav Maya, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> Para guardar o imprimir estas notas del producto, haga clic en **Imprimir** en el explorador y después en **Guardar como PDF**.

## <a name="introduction"></a>Introducción

Power BI ofrece a las organizaciones una vista de 360 grados de su negocio y mejora la capacidad de todos los usuarios de estas organizaciones a tomar decisiones inteligentes con datos. Muchas de estas organizaciones tengan relaciones de confianza y seguras con contratistas, los clientes y socios externos. Estas organizaciones necesitan proporcionar acceso seguro a los paneles de Power BI e informes a los usuarios de estos socios externos.

Power BI se integra con [Azure Active Directory negocio a negocio (B2B de Azure AD)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) para permitir una distribución segura de Power BI contenido para usuarios invitados de fuera de la organización, mientras todavía mantiene el control y que rigen el acceso a datos internos.

En este artículo se tratan los todos los detalles que necesita para comprender la integración de Power BI con Azure Active Directory B2B. Se explica su caso de uso más común, el programa de instalación, licencias y seguridad de nivel de fila.

> [!NOTE]
> En este artículo, nos referimos a Azure Active Directory como Azure AD y de negocio a negocio, como Azure AD B2B de Azure Active Directory.

## <a name="scenarios"></a>Escenarios

Contoso es un fabricante de automóviles y funciona con muchos proveedores distintos que proporcionarán con todos los materiales, componentes y servicios necesarios para ejecutar sus procesos de fabricación. Contoso desea optimizar sus planes a usar Power BI para supervisar las métricas clave de rendimiento de su cadena de suministro y la logística de la cadena de suministro. Contoso desea compartir con análisis de asociados de cadena de suministro externos de forma segura y administrable.

Contoso puede habilitar las experiencias siguientes para los usuarios externos mediante Power BI y Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc por compartir elementos

Contoso trabaja con un proveedor que crea radiadores para vehículos de Contoso. A menudo, necesita optimizar la confiabilidad de la radiadores utilizando los datos de todos los vehículos de Contoso. Un analista de Contoso usa Power BI para compartir un informe de confiabilidad radiador con un ingeniero de proveedor. El ingeniero recibe un correo electrónico con un vínculo para ver el informe.

Como se describió anteriormente, este ad-hoc de uso compartido se realiza por los usuarios empresariales según sea necesario. El vínculo enviado por Power BI para el usuario externo es un vínculo de invitación B2B de Azure AD. Cuando el usuario externo abre el vínculo, se les pide que unirse a la organización de Azure AD de Contoso como usuario invitado. Una vez aceptada la invitación, el vínculo abre el informe específico o el panel. El Administrador de Azure Active Directory delega el permiso para invitar a usuarios externos a la organización y elige qué pueden hacer los usuarios una vez que acepten la invitación, tal como se describe en la sección de gobierno de este documento. El analista de Contoso puede invitar a usuario invitado sólo porque el Administrador de Azure AD permite esa acción y el Power BI permitida a los usuarios de administrador para invitar a otros usuarios a ver el contenido en la configuración del inquilino de Power BI.

![Invitar a otros usuarios a Power BI con AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. El proceso comienza con un usuario interno de Contoso compartir un panel o un informe con un usuario externo. Si el usuario externo no es ya un invitado de Azure de Contoso AD, se invita. Se envía un correo electrónico a su dirección de correo electrónico que incluye una invitación a Azure de Contoso AD
2. El destinatario acepta la invitación a Contoso, Azure AD y se agrega como un usuario invitado en Azure de Contoso AD.
3. El destinatario, a continuación, se redirige al panel de Power BI, informes o aplicación, que son de solo lectura para el usuario.

El proceso se considera ad hoc, ya que los usuarios empresariales de Contoso realizan la acción de invitación según sea necesario para sus fines empresariales. Cada elemento compartido es un vínculo único puede tener acceso el usuario externo para ver el contenido.

Una vez que el usuario externo haya sido invitado a acceder a los recursos de Contoso, puede crearse una cuenta de la sombra para ellos en Azure AD de Contoso y no es necesario volver a ser invitado.  La primera vez que intenten obtener acceso a un recurso de Contoso como un panel de Power BI, se vayan a través de un proceso de consentimiento, que se canjea la invitación.  Si no se completan el consentimiento, no puede acceder a contenido de Contoso.  Si tienen problemas para canjear su invitación mediante el vínculo original proporcionado, Administrador de Azure AD puede reenviar un vínculo de invitación específicos para poder canjear.

### <a name="planned-per-item-sharing"></a>Planeada por compartir elementos

Contoso trabaja con un subcontratista para realizar análisis de confiabilidad de radiadores. Los subcontratistas tiene un equipo de 10 personas que necesitan tener acceso a los datos en el entorno de Power BI de Contoso. El Administrador de Azure AD de Contoso es complicado para invitar a todos los usuarios y controlar los cambios o adiciones como miembro del personal en el cambio de subcontratistas. El Administrador de Azure AD crea un grupo de seguridad para todos los empleados en el subcontratista. Con el grupo de seguridad, los empleados de Contoso pueden fácilmente administrar el acceso a informes y asegúrese de todo el personal de subcontratistas requiere tener acceso a todos los informes requeridos, paneles y aplicaciones de Power BI. El Administrador de Azure AD también puede evitar que se va a implicados en el proceso de invitación completamente eligiendo delegar derechos de invitación a un empleado de Contoso o en el subcontratista de confianza para garantizar la oportuno personal de administración.

Algunas organizaciones requieren más control sobre cuándo se agregan usuarios externos, está invitando muchos usuarios en una organización externa o muchas organizaciones externas. En estos casos, compartir planeada puede usar para administrar la escala de uso compartido, para aplicar las directivas organizativas e incluso delegar derechos a las personas de confianza para invitar y administrar los usuarios externos. B2B de Azure AD admite invitaciones planeadas para enviarse directamente [desde el portal de Azure por un administrador de TI](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator), o a través [PowerShell mediante la API del Administrador de invitaciones](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) donde un conjunto de usuarios puede ser invitado en uno acción. Utilizando la planeada invita a enfoque, la organización puede controlar quién puede invitar a usuarios e implementar procesos de aprobación. Capacidades de Azure AD avanzadas, como grupos dinámicos resulte más fácil de mantener la pertenencia a grupos de seguridad automáticamente.


![Los invitados que pueden ver el contenido del control](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. Las estrellas de proceso con un administrador de TI a invitar al usuario invitado manualmente o mediante la API proporcionado por Azure Active Directory
2. El usuario acepta la invitación a la organización.
3. Una vez que el usuario ha aceptado la invitación, un usuario de Power BI puede compartir con el usuario externo o un grupo de seguridad de en que ellos se encuentran un informe o panel. Al igual que con regular de uso compartido en Power BI el usuario externo recibe un correo electrónico con el vínculo al elemento.
4. Cuando los accesos de usuario externo que se pasa el vínculo, la autenticación en su directorio a Contoso Azure AD y usa para tener acceso al contenido de Power BI.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc o planeada de uso compartido de aplicaciones de Power BI

Contoso tiene un conjunto de informes y paneles que tienen que compartir con uno o varios proveedores. Para asegurarse de que todos los usuarios externos requiere tengan acceso a este contenido, lo se empaqueta como una aplicación de Power BI. O bien, los usuarios externos se agregan directamente a la lista de acceso de la aplicación o a través de grupos de seguridad. A continuación, un usuario de Contoso envía la dirección URL de la aplicación a todos los usuarios externos, por ejemplo, en un correo electrónico. Cuando los usuarios externos abran el vínculo, verán todo el contenido en una única fácil de navegar por la experiencia.

Uso de una aplicación de Power BI facilita a Contoso crear un Portal de inteligencia empresarial para sus proveedores. Una lista de acceso solo controla el acceso a todo el contenido necesario reducir la comprobación de pérdida de tiempo y permisos de nivel de elemento de configuración. B2B de Azure AD mantiene el acceso de seguridad mediante identity nativo del proveedor, por lo que los usuarios no necesitan credenciales de inicio de sesión adicionales. Si utiliza planeado invita con grupos de seguridad, administración de acceso a la aplicación como personal gira hacia o desde el proyecto se ha simplificado. Seguridad pertenencia a grupos manualmente o mediante [grupos dinámicos](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups), de modo que todos los usuarios externos de un proveedor se agregan automáticamente al grupo de seguridad adecuado.


![Control de contenido con AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. Se inicia el proceso por el usuario que se invita a la organización de Azure AD de Contoso a través del portal de Azure o PowerShell
2. El usuario puede agregarse a un grupo de usuarios en Azure AD. Se puede usar un grupo de usuarios estáticos o dinámicos, pero los grupos dinámicos ayudan a reducir el trabajo manual.
3. Los usuarios externos se concede acceso a la aplicación de Power BI a través del grupo de usuario. La aplicación debe enviarse directamente al usuario externo o colocada en un sitio de URL tienen acceso a. Power BI realiza un mayor esfuerzo para enviar un correo electrónico con el vínculo de la aplicación a los usuarios externos, pero al usar grupos de usuarios cuyos miembros pueden cambiar, Power BI no es capaz de enviar a todos los usuarios externos que se administran a través de grupos de usuarios.
4. Cuando el usuario externo tiene acceso a la dirección URL de aplicación de Power BI, se autentican en Azure de Contoso AD, la aplicación se instala para el usuario y el usuario puede ver todos los contenidos de los informes y paneles dentro de la aplicación.

Las aplicaciones también tienen una característica exclusiva que permite a los autores de la aplicación instalar la aplicación automáticamente para el usuario, por lo que está disponible cuando el usuario inicia sesión. Esta característica solo se instala automáticamente para los usuarios externos que ya forman parte de la organización de Contoso en el momento de la aplicación se publica o actualiza. Por lo tanto, se usa mejor con el enfoque de invitaciones planeadas y depende de la aplicación que se está publicando o actualizando después de que los usuarios se agregan a Azure de Contoso AD. Los usuarios externos siempre pueden instalar la aplicación mediante el vínculo de la aplicación.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Comentar y suscribirse a contenido a través de las organizaciones

Como Contoso sigue funcionando con sus contratistas o proveedores, los ingenieros externos necesitan trabajar estrechamente con los analistas de Contoso. Power BI proporciona varias características de colaboración que ayudan a los usuarios comunicarse sobre el contenido que pueden consumir. Panel de comentarios (y pronto de informes de comentarios) permite a los usuarios explicar los puntos de datos vean y se comuniquen con los autores de informes para formular preguntas.

Actualmente, los usuarios invitados externos pueden participar en los comentarios, dejar comentarios y lea las respuestas. Sin embargo, a diferencia de los usuarios internos, los usuarios invitados no pueden ser @mentioned y no recibirá notificaciones que ha recibido un comentario. Los usuarios invitados no pueden usar la característica de suscripciones en Power BI en el momento de escribir. En una próxima versión, se eliminará esas restricciones y el usuario invitado recibirá un correo electrónico cuando un comentario @mentions , o cuando se entrega una suscripción a su correo electrónico que contiene un vínculo al contenido de Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Tener acceso al contenido de las aplicaciones móviles de Power BI

En una próxima versión, cuando los usuarios de Contoso compartan informes o paneles con sus homólogos de invitado externos, Power BI enviará un correo electrónico del invitado. Cuando el usuario invitado abre el vínculo al informe o panel en su dispositivo móvil, se abrirá el contenido en las aplicaciones móviles nativas de Power BI en su dispositivo, si están instalados. El usuario invitado, a continuación, podrá navegar entre el contenido compartido con ellos en el inquilino externo y de vuelta a su propio contenido de su inquilino principal.

> [!NOTE]
> El usuario guest no puede abrir la aplicación móvil de Power BI y vaya inmediatamente al inquilino externo, deben comenzar con un vínculo a un elemento en el inquilino externo. Soluciones alternativas comunes se describen en la [distribuir vínculos al contenido de Power BI de la organización primaria](#distributing-links-to-content-in-the-parent-organizations-power-bi) sección más adelante en este documento.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Edición de toda la organización y administración de contenido de Power BI

Contoso y sus proveedores y los subcontratistas colaboran estrechamente cada vez más. A menudo un analista de subcontratista necesita visualizaciones de métricas o datos adicionales que se agregarán a un informe de que Contoso ha compartido con ellos. Los datos deben residir en el inquilino de Power BI de Contoso, pero los usuarios externos deben ser capaz de editar, crear nuevo contenido e incluso distribuirla a los usuarios adecuados.

Power BI proporciona una opción que permite **pueden editar y administrar el contenido de los usuarios externos invitados** en la organización. De forma predeterminada, los usuarios externos tienen una experiencia orientada a servicios de consumo de solo lectura. Sin embargo, esta nueva configuración permite al administrador de Power BI elegir qué usuarios externos pueden editar y administrar contenido dentro de su propia organización. Una vez que se permite, el usuario externo puede editar informes, paneles, publicar o actualizar aplicaciones, trabajar en las áreas de trabajo y conectarse a datos que tienen permiso para usar.

Este escenario se describe detalladamente en la sección Permitir externos a los usuarios editar y administrar el contenido de Power BI más adelante en este documento.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Relaciones de organización mediante Power BI y Azure AD B2B

Cuando todos los usuarios de Power BI son internos a la organización, no hay ninguna necesidad de usar Azure AD B2B. Sin embargo, una vez que dos o más organizaciones quieren colaborar en los datos e información, soporte técnico de Power BI para Azure AD B2B hace fácil y rentable para hacerlo.

A continuación se muestran las estructuras organizativas encontradas normalmente que son adecuadas para la colaboración B2B de Azure AD con otras organizaciones estilo en Power BI. B2B de Azure AD funciona bien en la mayoría de los casos, pero en algunas situaciones comunes enfoques alternativos trata al final de este documento son merece la pena considerar.

### <a name="case-1-direct-collaboration-between-organizations"></a>Caso 1: Colaboración entre organizaciones directa

Relación de Contoso con su proveedor radiador es un ejemplo de una colaboración entre organizaciones directa. Puesto que hay relativamente pocos usuarios de Contoso y sus proveedores que necesitan acceso a información de confiabilidad radiador, mediante Azure AD B2B en función de uso compartido externo es ideal. Es fácil de usar y fácil de administrar. Esto también es un patrón común en los servicios de consultoría donde un consultor que deba crear contenido para una organización.

![Compartir entre organizaciones](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Normalmente, este uso compartido ocurre inicialmente mediante Ad hoc por compartir elementos. Sin embargo, como el crecen de los equipos o profundizar en las relaciones, la planeada por compartir elementos enfoque se convierte en el método preferido para reducir la sobrecarga de administración. Además, el Ad hoc o planeada uso compartido de aplicaciones de Power BI, comentarios y suscribirse a contenido a través de las organizaciones, acceso al contenido de las aplicaciones móviles puede proceder en play y entre organizaciones de edición y administración de contenido de Power BI. Lo importante es que, si los usuarios de ambas organizaciones tienen licencias de Power BI Pro en sus respectivas organizaciones, puede usar las licencias de Pro en entornos de Power BI de los demás. Esto proporciona una ventaja licencias por puesto que la organización que invita no deba pagar por una licencia de Power BI Pro para los usuarios externos. Esto se explica con más detalle en la sección de licencias más adelante en este documento.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Caso 2: Primaria y sus subsidiarias o filiales

Algunas estructuras de organización son más complejas, incluidas las relaciones de proveedor de servicio administrada, sus empresas afiliadas o subsidiarias de propiedad total o parcialmente. Estas organizaciones tienen una organización principal como una sociedad de cartera, pero las organizaciones subyacentes operan autónoma punto y coma, a veces con diferentes requisitos regionales. Esto conduce a cada organización que tiene su propio entorno de Azure AD y usar inquilinos independientes de Power BI.

![Trabajar con subsidiarias](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


En esta estructura, la organización principal normalmente necesita compartir conocimientos sobre estandarizado para sus subsidiarias. Normalmente, este uso compartido ocurre uso compartido Ad hoc o planeada del enfoque de aplicaciones de Power BI tal como se muestra en la siguiente imagen, ya que permite la distribución de contenido autoritativo estandarizado a públicos amplios. En la práctica se utiliza una combinación de todos los escenarios mencionados anteriormente en este documento.

![Escenarios de combinación](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Esto sigue el proceso siguiente:

1. Los usuarios de cada filial están invitados a Azure de Contoso AD
2. A continuación, se publica la aplicación Power BI para permitir que estos usuarios acceso a los datos necesarios
3. Por último, los usuarios abran la aplicación a través de un vínculo que haya concedido para ver los informes

Varios desafíos importantes son que enfrentan las organizaciones en esta estructura:

- Cómo se distribuyen los vínculos al contenido de Power BI la organización primaria
- Cómo permitir que los usuarios subsidiarios tener acceso a origen de datos hospedado por la organización principal

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribuir los vínculos al contenido de Power BI la organización primaria

Normalmente se usan tres enfoques para distribuir los vínculos al contenido. La primera y la mayoría de basic es para enviar un vínculo a la aplicación a los usuarios requeridos o colocarlo en un sitio de SharePoint Online desde la que se puede abrir. Los usuarios, a continuación, pueden marcar el vínculo en sus exploradores para acelerar el acceso a los datos que necesitan.

El segundo enfoque se basa en la edición de toda la organización y la administración de capacidad de contenido de Power BI. La organización principal permite a los usuarios de las filiales tener acceso a su Power BI y controla qué pueden tener acceso a través de permiso. Esto proporciona acceso a Power BI página principal donde el usuario de la subsidiaria ve una lista completa de contenido compartido con ellos en el inquilino de la organización primaria. A continuación, se asigna la dirección URL para el entorno de Power BI de las organizaciones de los principales a los usuarios en las subsidiarias.

El último enfoque usa una aplicación de Power BI creada en el inquilino de Power BI para cada subsidiaria. La aplicación Power BI incluye un panel con [iconos configurados con la opción de vínculo externo](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink). Cuando el usuario presiona el mosaico, que se tomaron para el informe según corresponda, un panel o una aplicación en Power BI de la organización primaria. Este enfoque tiene la ventaja añadida de que la aplicación se puede instalar automáticamente para todos los usuarios de la subsidiaria y está disponible para ellos cada vez que inicie sesión en su propio entorno de Power BI. Una ventaja adicional de este enfoque es que funciona bien con las aplicaciones móviles de Power BI que pueden abrir el vínculo de forma nativa. También puede combinar con el segundo enfoque para habilitar más fácil cambiar entre entornos de Power BI.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Permitir que los usuarios subsidiarios tener acceso a orígenes de datos hospedados por la organización principal

A menudo los analistas de una subsidiaria deben crear su propio análisis con datos proporcionados por la organización primaria. En este caso, normalmente los orígenes de datos en la nube se usan para abordar el desafío.

El primer enfoque aprovecha [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) para crear un almacén de datos de nivel empresarial que satisface las necesidades de los analistas en el elemento primario y sus subsidiarias, tal como se muestra en la siguiente imagen. Contoso puede hospedar los datos y usar funcionalidades como seguridad de nivel de fila para garantizar que los usuarios en cada dependiente puede tener acceso a solo los datos. Los analistas de cada organización pueden tener acceso al almacén de datos a través de Power BI Desktop y publicar análisis resultante en sus respectivos inquilinos de Power BI.

![Cómo compartir se produce con los inquilinos de Power BI](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


El segundo enfoque aprovecha [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) para crear un almacén de datos relacionales para proporcionar acceso a datos. Esto funciona de forma similar al enfoque de Azure Analysis Services, aunque algunas funcionalidades como seguridad de nivel de fila puede ser más difíciles de implementar y mantener entre subsidiarias.

Los enfoques más sofisticados también son posibles, pero los pasos anteriores, sin duda el más común.

### <a name="case-3-shared-environment-across-partners"></a>Caso 3: Entorno compartido a través de asociados

Contoso puede escribir en una asociación con un competidor para crear un automóvil en conjunto en una línea de ensamblado compartida, pero para distribuir el vehículo en diversas marcas o en regiones diferentes. Esto requiere una amplia colaboración y co-propiedad de datos, inteligencia y análisis a través de las organizaciones. Esta estructura también es común en el sector de servicios de consultoría donde un equipo de consultores puede realizar análisis basados en el proyecto para un cliente.

![Entorno compartido a través de asociados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



En la práctica, estas estructuras son complejas, como se muestra en la siguiente imagen y requieran que el personal de mantenimiento. Para ser efectiva esta estructura se basa en la edición de toda la organización y la administración de capacidad de contenido de Power BI, ya que permite a las organizaciones a volver a usar Power BI Pro licencias adquiridas para sus respectivos inquilinos de Power BI.

![Las licencias y el contenido de la organización compartido](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Para establecer a un inquilino de Power BI compartido, debe crear un Azure Active Directory y al menos una cuenta de usuario de Power BI Pro debe adquirirse de un usuario en que active directory. Este usuario invita a los usuarios requeridos para la organización compartida. Lo importante es que, en este escenario, los usuarios de Contoso se tratan como los usuarios externos cuando funcionan dentro Power BI de la organización compartido.

El proceso es como sigue:

1. La organización compartido se establece como una nueva Azure Active Directory y al menos una cuenta de usuario se crea en la nueva organización. Ese usuario debe tener una licencia de Power BI Pro asignada a ellos.
2. Este usuario, a continuación, establece a un inquilino de Power BI y se invita a los usuarios requeridos de Contoso y la organización del asociado. El usuario también establece los recursos de datos compartidos, como Azure Analysis Services. Contoso y los usuarios del asociado pueden tener acceso a Power BI la organización compartida como usuarios invitados. Si se puede editar y administrar el contenido de Power BI los usuarios externos pueden usar Power BI en particular, usar áreas de trabajo, cargar o editar contenido y compartir informes. Por lo general, todos los recursos compartidos se almacenan y se obtiene acceso desde la organización compartida.
3. Dependiendo de cómo las partes acuerdan colaborar, es posible que cada organización desarrollar sus propios datos privados y análisis de uso de recursos de almacenamiento de datos compartido. Pueden distribuirlos de sus propios usuarios internos con sus inquilinos de Power BI internas.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Caso 4: Distribución a cientos o miles de socios comerciales externos

Ahora mientras Contoso crea un informe de confiabilidad radiador para un proveedor, Contoso desea crear un conjunto de informes estandarizados para cientos de proveedores. Esto permite a Contoso para asegurarse de que todos los proveedores poseen el análisis que necesitan para realizar mejoras o corregir los defectos de fabricación.

![Distribución a muchos de los socios comerciales](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Cuando una organización necesita distribuir datos normalizados y perspectivas para muchos usuarios/organizaciones externas, pueden usar Ad hoc o planeada compartir escenario de aplicaciones de Power BI para crear un Portal de BI rápidamente y sin costos de desarrollo extenso. Se trata el proceso de crear un portal de este tipo mediante una aplicación de Power BI en el caso práctico: Creación de un Portal de BI con Power BI + Azure AD B2B: paso a paso instrucciones más adelante en este documento.

Una variante común de este caso es cuando se trata de una organización compartir información con los consumidores, especialmente cuando se quieren para usar B2C de Azure con Power BI. Power BI no admite de forma nativa Azure B2C. Si va a evaluar las opciones para este caso, considere el uso alternativo Option 2 en los enfoques alternativos común la sección más adelante en este documento.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Caso práctico: Creación de un Portal de BI con Power BI + Azure AD B2B: instrucciones paso a paso

Integración de Power BI con Azure AD B2B proporciona una forma perfecta y sin problemas para proporcionar a los usuarios invitados con acceso seguro a su portal de BI de Contoso. Contoso puede configurar esta opción con tres pasos:

![Creación de un portal](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Crear portal de BI en Power BI

    La primera tarea para Contoso es crear su portal de BI en Power BI. Portal de BI de Contoso se compone de una colección de paneles diseñados específicamente y los informes que estará disponibles para muchos usuarios internos e invitados. Es la manera recomendada de hacerlo en Power BI crear una aplicación de Power BI. Obtenga más información sobre [aplicaciones en Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- Equipo de BI de Contoso crea un área de trabajo de aplicación en Power BI

    ![Área de trabajo de la aplicación](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Otros autores se agregan al área de trabajo

    ![Agregue a los autores](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Crear contenido dentro del área de trabajo

    ![Crear contenido dentro del área de trabajo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Ahora que el contenido se crea en un área de trabajo de aplicación, Contoso está listo para invitar a usuarios invitados en organizaciones de socios para consumir este contenido.

2. Invitar a usuarios externos

    Hay dos maneras de Contoso para invitar a usuarios invitados a su portal de BI en Power BI:

    * Invitaciones planeadas
    * Invitaciones ad hoc

    **Invitaciones planeadas**

    En este enfoque, Contoso invita a los usuarios invitados a su Azure AD antes de tiempo y, a continuación, distribuye el contenido de Power BI a ellos. Contoso puede invitar a los usuarios invitados de Azure portal o mediante PowerShell. Estos son los pasos para invitar a los usuarios invitados de Azure portal:

    - Administrador de Azure AD de Contoso se desplaza a **portal de Azure > Azure Active Directory > usuarios y grupos > todos los usuarios > nuevo usuario invitado**

    ![Usuario invitado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Agregar un mensaje de invitación para los usuarios invitados y haga clic en Invitar

    ![Agregar la invitación](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Para invitar a los usuarios invitados de Azure portal, necesita para administradores de Azure Active Directory del inquilino.

    Si Contoso desea invitar a muchos usuarios, puede hacerlo mediante PowerShell. Administrador de Azure AD de Contoso almacena las direcciones de correo electrónico de todos los usuarios invitados en un archivo CSV. Estos son [código de colaboración B2B de Azure Active Directory y ejemplos de PowerShell](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) e instrucciones.

    Después de la invitación, los usuarios invitados recibirán un correo electrónico con el vínculo de invitación.

    ![Vínculo de invitación](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Una vez que los usuarios invitados, haga clic en el vínculo, puede tener acceso a contenido en el inquilino de Azure AD de Contoso.

    > [!NOTE]
    > Es posible cambiar el diseño de la invitación por correo electrónico mediante la característica de personalización de marca de Azure AD, como se describe [aquí](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Invitaciones ad hoc**

    ¿Qué sucede si Contoso no conoce todos los usuarios invitados que desea invitar a antes de tiempo? O bien, ¿qué ocurre si desea que el analista de Contoso que creó el portal de BI distribuir contenido a los usuarios invitados su propio? También admitimos esta posibilidad en Power BI con invitaciones ad hoc.

    El analista puede agregar solo los usuarios externos a la lista de acceso de la aplicación cuando va a publicar. Los usuarios invitados Obtiene una invitación y una vez que lo hace, se redirige automáticamente el contenido de Power BI.

    ![Agregar usuario externo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Invitaciones se necesitan sólo la primera vez que un usuario externo se invita a su organización.


3. Distribuir contenido

    Ahora que el equipo de BI de Contoso ha creado el portal de BI e invitado a usuarios, puede distribuir su portal para sus usuarios finales mediante la concesión de acceso a los usuarios invitados a la aplicación y su publicación. Power BI completa automáticamente los nombres de los usuarios invitados que se agregaron anteriormente al inquilino de Contoso. Invitaciones ad hoc a otros usuarios invitados también se pueden agregar en este momento.

    > [!NOTE]
    > Si usa grupos de seguridad para administrar el acceso a la aplicación para usuarios externos, usar el enfoque planeado invita a y compartir el vínculo de la aplicación directamente con cada usuario externo que debe tener acceso a él. En caso contrario, el usuario externo no puede ser capaz de instalar o ver el contenido desde dentro de la aplicación. _

    Los usuarios invitados reciben un correo electrónico con un vínculo a la aplicación.

    ![Vínculo de invitación de correo electrónico](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Al hacer clic en este vínculo, se piden a los usuarios invitados para autenticarse con la identidad de su propia organización.

    ![Inicie sesión en la página](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Una vez que haya autenticado correctamente, se le redirigirá a la aplicación de BI de Contoso.

    ![Ver contenido compartido](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Los usuarios invitados pueden obtener posteriormente a la aplicación de Contoso haciendo clic en el vínculo del correo electrónico o el vínculo de marcadores. Contoso puede también resultará más fácil a los usuarios invitados mediante la adición de este vínculo a cualquier portal extranet existente que ya usan los usuarios invitados.

4. Pasos siguientes

    Con una aplicación de Power BI y Azure AD B2B, Contoso ha sido capaz de crear rápidamente un Portal de inteligencia empresarial para sus proveedores en una forma sin código. Esto simplifica distribuir análisis estandarizada para todos los proveedores que necesitara.

    Mientras que en el ejemplo se muestra cómo se puede distribuir un único informe común entre proveedores, Power BI puede ir mucho más allá. Para asegurarse de que cada socio solamente ve los datos pertinentes a sí mismos, seguridad de nivel de fila pueden agregarse fácilmente a los modelos de informe y datos. La seguridad de los datos para la sección socios externos más adelante en este documento describe este proceso en detalles.

    Los paneles e informes individuales a menudo deben insertarse en un portal existente. Esto también es posible volver a usar muchas de las técnicas que se muestra en el ejemplo. Sin embargo, en aquellas situaciones es posible que sea más fácil incrustar informes o paneles directamente desde un área de trabajo. El proceso de invitación y asignar permisos de seguridad para el requieren que los usuarios siguen siendo los mismos.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>En segundo plano: ¿Cómo es Lucy desde Supplier1 puede tener acceso a contenido de Power BI del inquilino de Contoso?

Ahora que hemos visto cómo Contoso es capaz de distribuir perfectamente el contenido de Power BI a usuarios invitados de organizaciones asociadas, echemos un vistazo a cómo funciona en segundo plano.

Cuando se invita Contoso [ lucy@supplier1.com ](mailto:lucy@supplier1.com) a su directorio, Azure AD crea un vínculo entre [ Lucy@supplier1.com ](mailto:Lucy@supplier1.com) y el inquilino de Azure AD de Contoso. Este vínculo permite a Azure AD debe saber que Lucy@supplier1.com puede tener acceso a contenido en el inquilino de Contoso.

Cuando intente acceder a la aplicación de Power BI de Contoso Lucy, Azure AD comprueba que Lucy, puede acceder al inquilino de Contoso y a continuación, proporciona un token que indica que Lucy está autenticada para tener acceso a contenido en el inquilino de Contoso de Power BI. Power BI usa este token para autorizar y asegúrese de que Lucy tiene acceso a la aplicación de Power BI de Contoso.

![Comprobación y la autorización](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Integración de Power BI con Azure AD B2B funciona con todas las direcciones de correo electrónico empresarial. Si el usuario no tiene una identidad de Azure AD, se pedirá a crearla. La siguiente imagen muestra el flujo detallado:

![Diagrama de flujo de integración](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Es importante para reconocer que la cuenta de Azure AD se usa o creada en la parte externa de Azure AD, esto le permitirá hacer posible que Lucy puede utilizar su propio nombre de usuario y contraseña y sus credenciales automáticamente dejará de funcionar en otros inquilinos cada vez que ella abandona la empresa cuando su organización también usa Azure AD.

## <a name="licensing"></a>Licencias

Contoso puede elegir uno de los tres métodos a los usuarios invitados de licencia de sus proveedores y organizaciones asociadas para tener acceso al contenido de Power BI.

> [!NOTE]
> _Nivel gratis de B2B de Azure AD es suficiente para usar Power BI con Azure AD B2B. Algunas características avanzadas de Azure AD B2B como grupos dinámicos requieren una licencia adicional. Consulte la documentación de Azure AD B2B para obtener más información:_ [_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Enfoque 1: Contoso usa Power BI Premium

Con este enfoque, Contoso adquiere la capacidad de Power BI Premium y asigna su contenido del portal de BI a esta capacidad. Esto permite a los usuarios invitados de organizaciones asociadas tener acceso a la aplicación de Power BI de Contoso sin ninguna licencia de Power BI.

Los usuarios externos también están sujetos al consumo de experiencias sola se ofrecen a los usuarios "Gratis" en Power BI al consumir contenido dentro de Power BI Premium.

Contoso también puede aprovechar otras funcionalidades de Power BI premium para sus aplicaciones como las frecuencias de actualización de una mayor capacidad dedicada y tamaños de modelo de gran tamaño.

![Funcionalidades adicionales](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Enfoque 2: Contoso asigna licencias de Power BI Pro a los usuarios invitados

Con este enfoque, Contoso asigna licencias pro a los usuarios invitados de asociado de las organizaciones, esto puede hacerse desde el centro de administración de Microsoft 365 de Contoso. Esto permite a los usuarios invitados de organizaciones asociadas tener acceso a la aplicación de Power BI de Contoso sin tener que adquirir una licencia a sí mismos. Esto puede ser adecuada para compartir con usuarios externos cuya organización no ha adoptado todavía Power BI.

> [!NOTE]
> _Licencia de pro de Contoso se aplica a los usuarios invitados sólo cuando tienen acceso a contenido en el inquilino de Contoso. Licencias de Pro habilitan el acceso a contenido que no está en una capacidad de Power BI Premium. Sin embargo, los usuarios externos con una licencia Pro están restringidos de forma predeterminada a una experiencia única de consumo. Esto puede cambiar el enfoque descrito en la_ _usuarios externos a la edición y administración de contenido de Power BI_ _sección más adelante en este documento._

![Información de licencia](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Enfoque 3: Los usuarios invitados traigan su propia licencia de Power BI Pro

Con este enfoque, el proveedor 1 asigna una licencia de Power BI Pro a Lucy. , A continuación, puede acceder a la aplicación de Power BI de Contoso con esta licencia. Puesto que Lucy puede usar su licencia de Pro de su propia organización al obtener acceso a un entorno externo de Power BI, este enfoque se denomina a veces _traiga su propia licencia_ (BYOL). Si ambas organizaciones usan Power BI, esto ofrece una ventaja de licencias para la solución general de análisis y minimiza la sobrecarga de asignación de licencias a usuarios externos.

> [!NOTE]
> _La licencia de pro que Lucy se concede al proveedor 1 se aplica a cualquier inquilino de Power BI donde Lucy es un usuario invitado. Licencias de Pro habilitan el acceso a contenido que no está en una capacidad de Power BI Premium. Sin embargo, los usuarios externos con una licencia Pro están restringidos de forma predeterminada a una experiencia única de consumo. Esto puede cambiar el enfoque descrito en la_ _usuarios externos a la edición y administración de contenido de Power BI_ _sección más adelante en este documento._

![Requisitos de licencia de Pro](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Seguridad de los datos para los asociados externos

Comúnmente al trabajar con varios proveedores externos, debe asegurarse de que cada proveedor vea datos sólo sobre sus propios productos de Contoso. Seguridad basada en usuario y seguridad de nivel de fila dinámica facilitan esta tarea realizar con Power BI.

### <a name="user-based-security"></a>Seguridad basada en usuario

Una de las características más eficaces de Power BI es la seguridad de nivel de fila. Esta característica permite a Contoso crear un único informe y conjunto de datos pero seguir aplicando las reglas de seguridad diferente para cada usuario. Para obtener una explicación detallada, consulte [seguridad de nivel de fila (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Integración de Power BI con Azure AD B2B permite a Contoso asignar las reglas de seguridad de nivel de fila a los usuarios invitados en cuanto son invitados al inquilino Contoso. Como hemos visto antes, Contoso puede agregar usuarios invitados a través de una planeadas o invitaciones ad hoc. Si Contoso desea aplicar la seguridad de nivel de fila, se recomienda encarecidamente utilizar invitaciones planeadas para agregar los usuarios invitados por delante de tiempo y asignarlas a los roles de seguridad antes de compartir el contenido. Si en su lugar usa Contoso invitaciones ad hoc, puede haber un breve período de tiempo donde los usuarios invitados no podrán ver ningún dato.

> [!NOTE]
> Este retraso al obtener acceso a datos protegidos por RLS cuando uso ad hoc invita puede dar lugar a admitir las solicitudes a su equipo de TI dado que los usuarios verán en blanco o interrumpe busca los informes o paneles al abrir un uso compartido de vínculo en el correo electrónico que reciben. Por lo tanto, se recomienda encarecidamente utilizar invitaciones planeadas en scenario.* *

Analicemos esto con un ejemplo.

Como se mencionó antes, Contoso tiene proveedores en todo el mundo, y desean para asegurarse de que los usuarios de sus organizaciones proveedoras obtengan información de datos de solo su territorio.  Pero los usuarios de Contoso pueden tener acceso a todos los datos. En lugar de crear varios informes diferentes, Contoso crea un único informe y filtra los datos en función del usuario que se ve.

![Contenido compartido](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Para asegurarse de que Contoso puede filtrar los datos en función de quién se conecta, se crean dos roles en Power BI desktop. Uno para filtrar todos los datos desde el SalesTerritory "Europa" y otra para "Norteamérica".

![Administración de roles](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Cada vez que los roles se definen en el informe, un usuario debe asignarse a un rol específico para que puedan obtener acceso a datos. La asignación de roles tiene lugar dentro del servicio Power BI ( **conjuntos de datos > seguridad** )

![Configuración de seguridad](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Esto abre una página en el equipo de BI de Contoso puede ver los dos roles creó.  Ahora el equipo de BI de Contoso puede asignar a usuarios a los roles.

![Seguridad de nivel de fila](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

En el ejemplo de Contoso es agregar un usuario en una organización asociada con la dirección de correo electrónico "[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)" a la función de Europa:

![Configuración de seguridad de nivel de fila](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Cuando esto se resuelve por Azure AD, Contoso puede ver el nombre aparece en la ventana ya se puede agregar:

![Mostrar funciones](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Ahora cuando este usuario abre la aplicación que se ha compartido con él, solo ve un informe con los datos de Europa:

![Visualización de contenido](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Seguridad de nivel de fila dinámica

Otro tema interesante es ver cómo la fila dinámica trabajo de nivel de seguridad (RLS) con Azure AD B2B.

En resumen, la seguridad de nivel de fila dinámica funciona mediante el filtrado de datos en el modelo basado en el nombre de usuario de la persona que se conecta a Power BI. En lugar de agregar varios roles para grupos de usuarios, definir los usuarios en el modelo. No se describirá el patrón en detalle aquí. Kasper de Jong ofrece una escritura detallada en todas las versiones de seguridad de nivel de fila en [hoja de referencia rápida de Power BI Desktop dinámica seguridad](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)y en [estas notas del producto](https://msdn.microsoft.com/library/jj127437.aspx) .

Echemos un vistazo a un pequeño ejemplo: Contoso tiene un informe sencillo en las ventas por grupos:

![Contenido de ejemplo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Ahora este informe debe compartirse con dos usuarios invitados y un usuario interno: el usuario interno puede ver todo el contenido, pero los usuarios invitados solo pueden ver los grupos que tienen acceso a. Esto significa que debemos filtraremos los datos solo para los usuarios invitados. Para filtrar los datos de forma adecuada, Contoso usa el patrón de RLS dinámica tal como se describe en la entrada de blog y notas del producto. Esto significa, Contoso agrega los nombres de usuario a los mismos datos:

![Ver los usuarios RLS en los propios datos](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

A continuación, Contoso crea el modelo de datos adecuado que filtra los datos correctamente con las relaciones correctas:

![Se muestran los datos adecuados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Para filtrar los datos automáticamente en función de quién ha iniciado sesión, Contoso debe crear un rol que se pasa en el usuario que se está conectando. En este caso, Contoso crea dos roles: el primero es el "securityrole" que filtra la tabla de usuarios con el nombre de usuario actual del usuario ha iniciado sesión en Power BI (Esto funciona incluso para los usuarios invitados de B2B de Azure AD).

![Administrar roles](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso también crea otro "AllRole" para que se pueden ver todo lo que sus usuarios internos: este rol no tiene ningún predicado de seguridad.

Después de cargar el archivo de Power BI desktop al servicio, Contoso puede asignar a los usuarios invitados a los "SecurityRole" usuarios internos y a la "AllRole"

Ahora, cuando los usuarios invitados abren el informe, solo ve los ventas de grupo A:

![Desde el grupo A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

En la matriz a la derecha puede ver el resultado de la función USERNAME() y USERPRINCIPALNAME() que ambos devuelven la que dirección de correo electrónico de los usuarios invitados.

Ahora se obtiene el usuario interno ver todos los datos:

![Todos los datos que se muestran](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Como puede ver, RLS dinámica funciona con usuarios internos o de invitado.

> [!NOTE]
> Este escenario también funciona cuando se usa un modelo en Azure Analysis Services. Normalmente, el servicio de análisis de Azure está conectado a la misma instancia de AD Azure como su Power BI: en ese caso, Azure Analysis Services también sabe que los usuarios invitados a través de Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Conexión a orígenes de datos locales

Power BI ofrece la capacidad de Contoso para sacar provecho de los orígenes de datos locales, como [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) o [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) directamente gracias a la [puerta de enlace de datos de un entorno local](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). Es posible incluso iniciar sesión esos orígenes de datos con las mismas credenciales que se usa con Power BI.

> [!NOTE]
> Al instalar una puerta de enlace para conectarse a su inquilino de Power BI, debe usar un usuario creado en el inquilino. Los usuarios externos no se pueden instalar una puerta de enlace y conectarlo a su inquilino. _

Para usuarios externos, esto podría ser más complicado porque los usuarios externos normalmente no se conocen a la red local AD. Power BI ofrece una solución alternativa para esto, ya que permite a los administradores de Contoso asignar los nombres de usuario externo a los nombres de usuario interno como se describe en [administrar el origen de datos: Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Por ejemplo, [ lucy@supplier1.com ](mailto:lucy@supplier1.com) pueden asignarse a [lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com).

![Asignación de nombres de usuario](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Este método es adecuado si Contoso tiene solo un puñado de usuarios o si Contoso puede asignar todos los usuarios externos a una sola cuenta interna. Para escenarios más complejos donde cada usuario tiene sus propias credenciales, hay un enfoque más avanzado que usa [atributos personalizados de AD](https://technet.microsoft.com/library/cc961737.aspx) para realizar la asignación, como se describe en [administrar el origen de datos: Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Esto permitiría que el Administrador de Contoso definir una asignación para todos los usuarios de Azure AD (también usuarios de B2B externos).  Estos atributos se pueden establecer a través del modelo de objeto de AD con scripts o código de modo que Contoso puede automatizar completamente la asignación en la invitación, o a un ritmo programado.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Permitir que los usuarios externos editar y administrar el contenido de Power BI

Contoso puede permitir que los usuarios externos contribuir con contenido dentro de la organización tal como se describe anteriormente en la toda la organización de edición y administración de la sección de contenido de Power BI.

> [!NOTE]
> Para editar y administrar el contenido de Power BI de su organización, el usuario debe tener una licencia de Power BI Pro en un área de trabajo que no sea de Mi área de trabajo. Los usuarios pueden obtener licencias de Pro, como se explica en la opción _Licensing__section de este documento._

El Portal de administración de Power BI proporciona el **permiten a los usuarios externos invitados edición y administración de contenido de la organización** configuración de inquilino. De forma predeterminada, la configuración se establece en deshabilitado, lo que significa que los usuarios externos obtención una experiencia limitada de solo lectura de forma predeterminada. La configuración se aplica a los usuarios con UserType establecido en invitado de Azure AD. En la tabla siguiente se describe los comportamientos de los usuarios experimentan según su UserType y cómo se configuran las opciones.

| **Tipo de usuario de Azure AD** | **Permitir que los usuarios invitados externos editar y administrar la configuración del contenido** | **Comportamiento** |
| --- | --- | --- |
| Invitado | Está deshabilitado para el usuario (valor predeterminado) | Por cada elemento vista única de consumo. Permite el acceso de solo lectura a informes, paneles y aplicaciones cuando se ven a través de una dirección URL que se envía al usuario invitado. Power BI Mobile apps proporcionan una vista de solo lectura al usuario invitado. |
| Invitado | Habilitada para el usuario | El usuario externo obtiene acceso a la experiencia de Power BI completa, aunque algunas características no están disponibles para ellos. El usuario externo debe iniciar sesión en Power BI con la dirección URL del servicio Power BI con la información del inquilino incluida. La obtiene de usuario pueden examinar la experiencia de inicio, un mi área de trabajo y en función de los permisos, ver y crear contenido. </br></br> Power BI Mobile apps proporcionan una vista de solo lectura al usuario invitado. |

> [!NOTE]
> Los usuarios externos de Azure AD también pueden establecerse al miembro UserType. Esto no se admite actualmente en Power BI.

En el portal de administración de Power BI, la configuración se muestra en la siguiente imagen.

![Configuración del administrador](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Los usuarios invitados obtención la experiencia predeterminada de solo lectura y que se puede editar y administrar el contenido. El valor predeterminado está deshabilitado, lo que significa que todos los usuarios invitados tienen la experiencia de solo lectura. El Administrador de Power BI puede habilitar a la configuración para todos los usuarios invitados de la organización o para grupos de seguridad específicos definidos en Azure AD. En la siguiente imagen, el Administrador de Contoso de Power BI crea un grupo de seguridad en Azure AD para administrar qué usuarios externos pueden editar y administrar el contenido en el inquilino de Contoso.

Para ayudar a los usuarios inicien sesión en Power BI, les proporciona la dirección URL del inquilino. Para buscar la dirección URL del inquilino, siga estos pasos.

1. ¿En el servicio Power BI, en el menú superior, seleccione Ayuda ( **?** ), a continuación, **sobre Power BI**.
2. Busque el valor junto a **dirección URL del inquilino**. Se trata de la dirección URL del inquilino puede compartir con los usuarios invitados.

    ![URL de inquilino](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Cuando se usa el permitir a los usuarios invitados externos para editar y administrar el contenido de la organización, los usuarios invitados especificado acceda a Power BI de su organización y ve cualquier contenido a los que tienen permiso. Puede obtener acceso a casa, vaya y aportar contenido a las áreas de trabajo, instalar aplicaciones donde se encuentran en la lista de acceso y tiene un mi área de trabajo. Pueden crear o ser administradores de áreas de trabajo que usen la nueva experiencia de área de trabajo.

> [!NOTE]
> Cuando se usa esta opción Asegúrese de revisar la sección de gobierno de este documento ya que la configuración de Azure AD predeterminado impedir que los usuarios invitados para usar determinadas características como los selectores de personas que pueden dar lugar a un reducido experience.* *

Para los usuarios invitados que habilita a través de los usuarios externos invitados permitir para editar y administrar el contenido de la configuración del inquilino de organización, algunas experiencias no están disponibles para ellos. Para actualizar o publicar informes, los usuarios invitados deben usar la web del servicio Power BI UI, incluidas obtener datos para cargar archivos de Power BI Desktop. Las siguientes experiencias no se admiten:

- Publicación directa desde Power BI Desktop en el servicio Power BI
- Los usuarios invitados no pueden usar Power BI Desktop para conectarse a conjuntos de datos de servicio en el servicio Power BI
- Áreas de trabajo clásicas asociadas a Grupos de Office 365: Los usuarios invitados no pueden crear ni ser administradores de estas áreas de trabajo. Pueden ser miembros.
- No se admite el envío de invitaciones ad hoc para listas de acceso al área de trabajo
- Power BI Publisher para Excel no se admite para usuarios invitados
- Los usuarios invitados no pueden instalar Power BI Gateway y conectarlo a la organización
- Los usuarios invitados no pueden instalar la publicación de aplicaciones para toda la organización
- Los usuarios invitados no pueden usar, crear, actualizar ni instalar paquetes de contenido de organización
- Los usuarios invitados no pueden usar Analizar en Excel
- Los usuarios invitados no pueden ser @mentioned en comentarios (esta funcionalidad se agregará en una próxima versión)
- Los usuarios invitados no pueden usar suscripciones (esta funcionalidad se agregará en una próxima versión)
- Los usuarios invitados que usen esta funcionalidad deben tener una cuenta profesional o educativa. Los usuarios invitados utilizando cuentas personales experimentan más limitaciones debido a restricciones de inicio de sesión.



## <a name="governance"></a>Gobernanza

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Configuración de AD Azure adicionales que afectan a las experiencias de Power BI relacionado con Azure AD B2B

Cuando el uso compartido de Azure AD B2B, el Administrador de Azure Active Directory controla los aspectos de la experiencia del usuario externo. Estos se controlan en la página de configuración de colaboración externa dentro de la configuración de Azure Active Directory para el inquilino.

Aquí encontrará detalles sobre la configuración:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> De forma predeterminada, los permisos de los usuarios invitados están limitados opción está establecida en Sí, por lo que los usuarios invitados en Power BI tienen una limitada experiencias especialmente rodear compartida donde las interfaces de usuario de selector de personas no funcionan para esos usuarios. Es importante trabajar con su administrador de Azure AD para establecerlo en No, tal como se muestra a continuación para garantizar un buen experience.* *

![Configuración de colaboración externa](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Invitaciones de invitados de control

Los administradores de Power BI pueden controlar el uso compartido externo solo para Power BI, visite el portal de administración de Power BI. Pero los administradores de inquilinos también pueden controlar el uso compartido externo con distintas directivas de Azure AD.  Estas directivas permiten a los administradores de inquilinos

- Desactivar invitaciones a los usuarios finales
- Solo los administradores y los usuarios del rol de Invitador invitado pueden invitar
- Pueden invitar administradores, el rol de Invitador invitado y miembros
- Todos los usuarios, incluidos a los invitados, pueden invitar

Puede leer más acerca de estas directivas en [delegación de invitaciones de colaboración B2B de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Todas las acciones de Power BI, los usuarios externos también son [audita en nuestro portal auditoría](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>Directivas de acceso condicional para usuarios invitados

Contoso puede aplicar directivas de acceso condicional para los usuarios invitados que acceder al contenido desde el inquilino de Contoso. Puede encontrar instrucciones detalladas de [acceso condicional para usuarios de colaboración B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Enfoques alternativos comunes

Aunque Azure AD B2B facilita compartir datos e informes en las organizaciones, existen varios otros enfoques que se usan con frecuencia y pueden ser superior en ciertos casos.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Opción alternativa 1: Crear usuarios de identidades duplicadas para asociados

Con esta opción, Contoso debía crear manualmente las identidades duplicadas para cada usuario del asociado en el inquilino de Contoso, tal como se muestra en la siguiente imagen. A continuación, en Power BI, Contoso puede compartir a las identidades asignadas los informes adecuados, paneles o aplicaciones.

![Los nombres y las asignaciones de configuración adecuadas](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Razones para elegir esta alternativa:

- Puesto que la identidad del usuario es controlada por su organización, los relacionados con el servicio como el correo electrónico, SharePoint, etc. también se encuentran dentro del control de su organización. Los administradores de TI puede restablecer las contraseñas, deshabilitar el acceso a las cuentas o auditar las actividades de estos servicios.
- Los usuarios que utilizan las cuentas personales de su negocio a menudo está restringido el acceso a determinados servicios por lo que necesite una cuenta de organización.
- Algunos servicios solo funcionan a través de los usuarios de su organización. Por ejemplo, usar Intune para administrar el contenido en los dispositivos personales o móviles de usuarios externos con B2B de Azure puede no ser posible.

Razones para no elegir esta alternativa:

- Los usuarios de organizaciones asociadas deben recordar dos conjuntos de credenciales, uno para tener acceso a contenido de su organización y el otro para tener acceso al contenido de Contoso. Se trata de una complicación para estos usuarios invitados y muchos usuarios invitados se sientan confundidos al esta experiencia.
- Contoso debe adquirir y asignar licencias por usuario a estos usuarios. Si un usuario necesita recibir correo electrónico o usar las aplicaciones de office, que necesitan las licencias correspondientes, incluidos Power BI Pro para editar y compartir el contenido de Power BI.
- Contoso podría aplicar las directivas de gobierno para usuarios externos en comparación con los usuarios internos y de autorización más estricta. Para lograr esto, Contoso debe crear una nomenclatura interna para los usuarios externos y es necesario educar sobre esta nomenclatura todos los usuarios de Contoso.
- Cuando el usuario abandona la organización, estos seguirán teniendo acceso a los recursos de Contoso hasta que el Administrador de Contoso elimina manualmente su cuenta
- Los administradores de Contoso tienen que administrar la identidad del invitado, incluida la creación, los restablecimientos de contraseña, etcetera.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Opción alternativa 2: Crear una aplicación personalizada de Power BI Embedded mediante la autenticación personalizada

Otra opción para Contoso consiste en crear su propia aplicación personalizada de Power BI embedded con autenticación personalizada (['Aplicación posee los datos'](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers)). Aunque muchas organizaciones no tienen el tiempo o los recursos para crear una aplicación personalizada para Power BI de distribuir contenido a sus asociados externos, para algunas organizaciones es el mejor enfoque y merece tenerlo en cuenta.

A menudo, las organizaciones tienen portales socio existentes que centralicen el acceso a todos los recursos de la organización para partners, proporcionan el aislamiento de recursos internos de la organización y proporcionan una experiencia simplificada de socios admitir muchos socios y los usuarios individuales.

![Muchos de los portales de asociado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

En el ejemplo anterior, los usuarios de cada inicio de sesión del proveedor al Portal de partners de Contoso que usa AAD como proveedor de identidades. Podría usar AAD B2B, B2C de Azure, las identidades nativas o federar con cualquier número de otros proveedores de identidades. El usuario podría iniciar sesión y tener acceso a una compilación portal asociado con la aplicación Web de Azure o una infraestructura similar.

Dentro de la aplicación web, los informes de Power BI se insertan desde una implementación de Power BI Embedded. La aplicación web pudiera agilizar el acceso a los informes y los servicios relacionados de una experiencia coherente, cuyo objetivo es facilitar a los proveedores interactuar con Contoso. Este entorno de portal deben estar aislado desde AAD interna de Contoso y entorno de Power BI interno de Contoso para asegurarse de proveedores no pudo obtener acceso a esos recursos. Por lo general, los datos se almacenarían en un almacén de datos independiente de asociado para garantizar el aislamiento de datos también. Este aislamiento tiene ventajas, ya que limita el número de usuarios externos con acceso directo a los datos de su organización, limitar los datos que potencialmente podrían estar disponibles para el usuario externo y la limitación de uso compartido accidental con usuarios externos.

Con Power BI Embedded, puede aprovechar el portal de licencias ventajoso, utilizando el token de la aplicación o el usuario maestro más capacidad premium adquirido en el modelo de Azure, que simplifica las cuestiones sobre la asignación de licencias a los usuarios finales y puede escalar verticalmente/reducir en función de lo esperado uso. El portal puede ofrecer un general una mayor calidad y una experiencia coherente puesto que los partners obtener acceso a un único portal diseñado con todas las necesidades de un socio en mente. Por último, puesto que las soluciones de Power BI Embedded basado normalmente están diseñadas para ser apto para multiempresa, resulta más fácil de garantizar el aislamiento entre organizaciones asociadas.

Razones para elegir esta alternativa:

- Crecen más fáciles de administrar como el número de organizaciones asociadas. Puesto que los asociados se agregan a un directorio independiente aislado de directorio AAD interna de Contoso, simplifica las tareas de gobierno de TI y ayuda a evita el uso compartido accidental de datos internos a los usuarios externos.
- Típico portales de socio alta son marca experiencias con experiencias coherentes entre los asociados y simplificados para satisfacer las necesidades de los socios típicos. Por lo tanto, Contoso puede ofrecer una mejor experiencia general a los socios comerciales mediante la integración de todos los servicios necesarios en un único portal.
- Licencias de los costos para escenarios avanzados, como el contenido de la edición dentro de la de Power BI Embedded está cubierto por Azure adquirido Power BI Premium y no requieren la asignación de licencias de Power BI Pro a los usuarios.
- Proporciona un mejor aislamiento entre los asociados si diseñado como una solución para varios inquilinos.
- El Portal de partners a menudo incluye otras herramientas para el socio más allá de los informes de Power BI, paneles y aplicaciones.

Razones para no elegir esta alternativa:

- Se requiere un esfuerzo significativo para crear, operar y mantener tal un portal de realizar una inversión importante en el tiempo y recursos.
- Tiempo para la solución es mucho más larga que el uso compartido de B2B desde una planeación cuidadosa y ejecución a través de varias secuencias de trabajo es obligatorio.
- Donde hay un número menor de socios probablemente es demasiado alto para justificar el esfuerzo necesario para esta alternativa.
- Colaboración con el uso compartido ad hoc es el escenario principal que se enfrenta su organización.
- Los informes y paneles son diferentes para cada socio comercial. Esta alternativa presenta la administración de la sobrecarga más allá de simplemente se comparten directamente con socios.



## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES

**¿Puede enviar Contoso una invitación que automáticamente se canjee para que el usuario es simplemente "listo"? ¿O el usuario siempre tiene que desplazarse a la dirección URL de canje?**

El usuario final siempre debe hacer clic a través de la experiencia de consentimiento para que pueden acceder a contenido.

Si se puede invitar a muchos usuarios invitados, se recomienda delegar esto de los administradores de AD Azure core por [adición de un usuario para el rol invitador de usuarios en la organización del recurso](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). Este usuario puede invitar a otros usuarios de la organización asociada con el inicio de sesión de interfaz de usuario, scripts de PowerShell, o las API. Esto reduce la carga administrativa en los administradores de Azure AD para invitar a o a enviar invitaciones a los usuarios de la organización del asociado.

**¿Puede forzar Contoso autenticación multifactor para usuarios invitados Si sus asociados no tienen la autenticación multifactor?**

Sí. Para obtener más información, consulte [acceso condicional para usuarios de colaboración B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**¿Cómo funciona la colaboración B2B cuando el asociado invitado utiliza la federación para agregar su propia autenticación local?**

Si el asociado tiene un inquilino de Azure AD que esté federado con la infraestructura de autenticación local, de forma local sesión único (SSO) se consigue automáticamente. Si el asociado no tiene un inquilino de Azure AD, puede crearse una cuenta de Azure AD para los nuevos usuarios.

**¿Se puede invitar a usuarios con cuentas de correo electrónico de consumidor?**

Invitar a usuarios invitados con cuentas de correo electrónico de consumidor se admite en Power BI. Esto incluye los dominios como hotmail.com, outlook.com y gmail.com. Sin embargo, los usuarios pueden experimentar limitaciones más allá de lo que los usuarios con trabajan o encontrar cuentas educativas.
