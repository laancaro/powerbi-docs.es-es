---
title: 'Administrar el origen de datos: Analysis Services'
description: Cómo administrar la puerta de enlace de datos local y los orígenes de datos que pertenecen a esa puerta de enlace. Esto es para Analysis Services en modo tabular y multidimensional.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93475f6476f8baad73229473bd3ce60db68a320b
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271640"
---
# <a name="manage-your-data-source---analysis-services"></a>Administrar el origen de datos: Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Una vez que haya [instalado la puerta de enlace de datos local](/data-integration/gateway/service-gateway-install), tendrá que [agregar orígenes de datos](service-gateway-data-sources.md#add-a-data-source) que se puedan usar con ella. En este artículo se describe cómo trabajar con puertas de enlace y orígenes de datos de Analysis Services que se usan para la actualización programada o para conexiones dinámicas.

Para obtener más información sobre cómo configurar una conexión dinámica a Analysis Services, [vea este vídeo](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be).

> [!NOTE]
> Si tiene un origen de datos de Analysis Services, deberá instalar la puerta de enlace en un equipo unido al mismo bosque o dominio que el servidor de Analysis Services.

## <a name="add-a-data-source"></a>Elegir un origen de datos

Para obtener información sobre cómo agregar un origen de datos, vea [Adición de un origen de datos](service-gateway-data-sources.md#add-a-data-source). Seleccione Analysis Services para **Tipo de origen de datos** si se conecta a un servidor tabular o multidimensional.

![Adición del origen de datos de Analysis Services](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Después, deberá rellenar la información del origen de datos que incluye el **Servidor** y la **Base de datos**. La puerta de enlace usará el **nombre de usuario** y la **contraseña** que especifique para conectarse a la instancia de Analysis Services.

> [!NOTE]
> La cuenta de Windows que especifique debe tener permisos de administrador del servidor para la instancia con la que se va a conectar. Si la contraseña de la cuenta se configura para caducar, los usuarios podrían obtener un error de conexión si no se actualiza la contraseña para el origen de datos. Para más información sobre cómo se almacenan las credenciales, vea [Almacenamiento de credenciales cifradas en la nube](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Rellene la configuración del origen de datos](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Seleccione **Agregar** después de que lo haya rellenado todo. Ahora puede usar este origen de datos para la actualización programada o las conexiones dinámicas en una instancia de Analysis Services que sea local. Si se realiza correctamente, verá el mensaje *Conexión correcta* .

![Representación del estado de conexión](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configuración avanzada

Opcionalmente, puede configurar el nivel de privacidad del origen de datos. Esto controla cómo se pueden combinar los datos. Solo se usa para la actualización programada. No se aplica a las conexiones dinámicas. Para más información sobre los niveles de privacidad del origen de datos, vea [Niveles de privacidad (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Establecimiento del nivel de privacidad](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Nombres de usuario con Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Cada vez que un usuario interactúa con un informe conectado a Analysis Services, el nombre de usuario efectivo se envía a la puerta de enlace y después al servidor de Analysis Services local. La dirección de correo electrónico, con la que inicia sesión en Power BI, es lo que se pasará a Analysis Services como usuario efectivo. Se pasa en la propiedad de conexión [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth). Esta dirección de correo debe coincidir con un Nombre principal de usuario (UPN) definido en el dominio de Active Directory local. El UPN es una propiedad de una cuenta de Active Directory. Por lo tanto, esa cuenta de Windows debe estar presente en una función de Analysis Services. Si no se encuentra una coincidencia en Active Directory, el inicio de sesión no será correcto. Para más información sobre Active Directory y los nombres de usuario, vea [Atributos de nombres de usuario](https://msdn.microsoft.com/library/ms677605.aspx).

También puede [asignar el nombre de inicio de sesión de Power BI con un UPN de directorio local](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources).

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Asignación de nombres de usuario a orígenes de datos de Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

Power BI permite asignar nombres de usuario a orígenes de datos de Analysis Services. Puede configurar reglas para asignar un nombre de usuario que ha iniciado sesión con Power BI a un nombre que se pasa para EffectiveUserName en la conexión de Analysis Services. La función de asignación de nombres de usuario es una excelente solución alternativa cuando su nombre de usuario en AAD no coincide con un UPN en su Active Directory local. Por ejemplo, si su dirección de correo es nancy@contoso.onmicrsoft.com, podría asignarla a nancy@contoso.com y ese valor se pasaría a la puerta de enlace.

Puede asignar nombres de usuario para Analysis Services de dos maneras diferentes:

* Reasignación manual del usuario
* Búsqueda de propiedad de Active Directory local para reasignar los UPN de AAD a los usuarios de Active Directory (asignación de búsqueda de AD)

Aunque es posible realizar la asignación manual mediante el segundo enfoque, llevaría mucho tiempo y sería difícil de mantener. Es especialmente difícil cuando la coincidencia de patrones no es suficiente, como cuando los nombres de dominio son diferentes entre AAD y AD local, o bien cuando los nombres de cuenta de usuario son diferentes entre AAD y AD. Por lo tanto, no se recomienda la asignación manual con el segundo enfoque.

En las dos secciones siguientes, se describen estos dos enfoques por orden.

### <a name="manual-user-name-re-mapping"></a>Reasignación manual de nombres de usuario

Para orígenes de datos de Analysis Services, puede configurar reglas personalizadas de nombre principal de usuario (UPN). Esto le ayudará si los nombres de inicio de sesión del servicio Power BI no coinciden con su UPN de directorio local. Por ejemplo, si inicia sesión en Power BI mediante john@contoso.com, pero su directorio local UPN es john@contoso.local, puede configurar una regla de asignación para que john@contoso.local se pase a Analysis Services.

Para llegar a la pantalla de asignación de UPN, haga lo siguiente.

1. Vaya al **icono de engranaje** y seleccione **Administrar puertas de enlace**.
2. Expanda la puerta de enlace que contiene el origen de datos de Analysis Services. O bien, si no ha creado el origen de datos de Analysis Services, puede hacerlo en este momento.
3. Seleccione el origen de datos y luego elija la ficha **Usuario**.
4. Seleccione **Asignar nombres de usuario**.

    ![Pantalla de asignación de UPN](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Verá entonces opciones para agregar reglas, así como una prueba para un usuario determinado.

> [!NOTE]
> Puede cambiar involuntariamente un usuario que no quería. Por ejemplo, si su **Reemplazar (valor original)** es <em>@contoso.com</em> y su **Por (nombre)** es <em>@contoso.local</em>, todos los usuarios con un inicio de sesión que contenga <em>@contoso.com</em> se reemplazarán por <em>@contoso.local</em>. Además, si su **Reemplazar (nombre original)** es <em>dave@contoso.com</em> y su **Por (nombre)** es <em>dave@contoso.local</em>, un usuario con el inicio de sesión de v-dave@contoso.com se enviaría como v-dave<em>@contoso.local</em>.

### <a name="ad-lookup-mapping"></a>Asignación de búsqueda de AD

Para realizar una búsqueda de la propiedad de AD local para reasignar los UPN de AAD a los usuarios de Active Directory, siga los pasos descritos en esta sección. Para comenzar, revisemos su funcionamiento.

En el **servicio Power BI** ocurre lo siguiente:

* Para cada consulta de un usuario de AAD de Power BI a un servidor SSAS local, se pasa una cadena de UPN, como: firstName.lastName@contoso.com

> [!NOTE]
> Las asignaciones manuales de UPN definidas en la configuración del origen de datos de Power BI se siguen aplicando *antes* de enviar la cadena de nombre de usuario a la puerta de enlace de datos local.

En la puerta de enlace de datos local con asignación de usuario personalizado configurable, siga estos pasos:

1. Localice la instancia de Active Directory que quiere buscar (automática o configurable).
2. Busque el atributo de la persona de AD (como *Correo electrónico*) en función de la cadena del UPN entrante ("firstName.lastName@contoso.com") del **servicio Power BI**.
3. Si se produce un error en la búsqueda de AD, intenta utilizar el UPN que se ha pasado como EffectiveUser a SSAS.
4. Si la búsqueda de AD se realiza correctamente, recupera *UserPrincipalName* de esa persona de AD.
5. Pasa el correo electrónico *UserPrincipalName* como *EffectiveUser* a SSAS, como <em>Alias@corp.on-prem.contoso</em>.

Para configurar la puerta de enlace para realizar la búsqueda de AD:

1. [Descargue e instale la puerta de enlace más reciente](/data-integration/gateway/service-gateway-install).

2. En la puerta de enlace, debe cambiar el **servicio de puerta de enlace de datos local** para que se ejecute con una cuenta de dominio (en lugar de con una cuenta de servicio local; en caso contrario, la búsqueda de AD no funcionará correctamente en el runtime). Vaya a la [aplicación de puerta de enlace de datos local](/data-integration/gateway/service-gateway-app) en el equipo y, después, vaya a **Configuración del servicio > Cambiar cuenta de servicio**. Asegúrese de que tiene la clave de recuperación para esta puerta de enlace, ya que necesitará restaurarla en el mismo equipo, a menos que desee crear una nueva puerta de enlace en su lugar. Para que el cambio se aplique, habrá que reiniciar el servicio de puerta de enlace.

3. Vaya a la carpeta de instalación de la puerta de enlace, *C:\Archivos de programa\Puerta de enlace de datos local* como administrador, para asegurarse de que tiene permisos de escritura, y abra el archivo *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Edite los dos valores de configuración siguientes según *sus* configuraciones de atributos de Active Directory para los usuarios de AD. Los valores de configuración que se muestran a continuación son solo ejemplos: es necesario especificarlos según la configuración de Active Directory. Estas configuraciones distinguen mayúsculas de minúsculas, por lo que asegúrese de que coinciden con los valores de Active Directory.

    ![Configuración de Azure Active Directory](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Si no se proporciona ningún valor para la configuración de ADServerPath, la puerta de enlace usa el valor predeterminado de catálogo global. También puede especificar varios valores para ADServerPath. Cada valor debe estar separado por un punto y coma, como en el ejemplo siguiente.

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    La puerta de enlace analiza los valores de ADServerPath de izquierda a derecha hasta que encuentra una coincidencia. Si no se encuentra ninguna coincidencia, se usa el UPN original. Asegúrese de que la cuenta que ejecuta el servicio de puerta de enlace (PBIEgwService) tiene permisos de consulta en todos los servidores de AD que especifique en ADServerPath.

    La puerta de enlace admite dos tipos de ADServerPath, como se muestra en los ejemplos siguientes.

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Reinicie el servicio de **puerta de enlace de datos local** para que se aplique el cambio en la configuración.

### <a name="working-with-mapping-rules"></a>Trabajar con reglas de asignación

Para crear una regla de asignación, escriba un valor para **Nombre original** y **Nuevo nombre** y, a continuación, seleccione **Agregar**.

| Campo | Descripción |
| --- | --- |
| Reemplazar (nombre original) |Dirección de correo electrónico con la que inició sesión en Power BI. |
| Por (nuevo nombre) |Valor por el que se desea reemplazarla. El resultado de la sustitución es lo que se pasará a la propiedad *EffectiveUserName* para la conexión de Analysis Services. |

![Creación de una regla de asignación](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Cuando seleccione un elemento en la lista, puede reordenarlo utilizando los **iconos angulares**, o eliminar la entrada mediante el botón **Eliminar**.

![Reordenación de un elemento en la lista](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>Uso del carácter comodín (\*)

Puede usar un carácter comodín para su cadena **Reemplazar (nombre original)** . Únicamente se puede usar solo y no puede ir acompañado de ninguna otra parte de la cadena. Así, podrá usar todos los usuarios y pasar un valor único al origen de datos. Esto es útil si quiere que todos los usuarios de su organización usen el mismo usuario en su entorno local.

### <a name="test-a-mapping-rule"></a>Prueba de una regla de asignación

Puede validar un nombre original para que se reemplace especificando un valor para **Nombre original** y seleccionando **Probar regla**.

![Prueba de una regla de asignación](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> Las reglas que se guardan tardarán unos minutos antes de que el servicio empiece a usarlas. En el explorador, la regla funcionará inmediatamente.

### <a name="limitations-for-mapping-rules"></a>Limitaciones de las reglas de asignación

La asignación es para el origen de datos específico que se está configurando. No es una configuración global. Si tiene varios orígenes de datos de Analysis Services, tendrá que asignar los usuarios para cada origen de datos.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticación a un origen de datos de Analysis Services activo

Cada vez que un usuario interactúa con Analysis Services, el nombre de usuario efectivo se envía a la puerta de enlace y después al servidor de Analysis Services local. El nombre principal de usuario (UPN), normalmente la dirección de correo con la que inicia sesión en la nube, es lo que se pasará a Analysis Services como usuario efectivo. El UPN se pasa en la propiedad de conexión EffectiveUserName. Esta dirección de correo debe coincidir con un UPN definido en el dominio de Active Directory local. El UPN es una propiedad de una cuenta de Active Directory. Por tanto, esa cuenta de Windows debe estar presente en un rol de Analysis Services para tener acceso al servidor. Si no se encuentra una coincidencia en Active Directory, el inicio de sesión no será correcto.

Analysis Services también puede proporcionar filtrado basado en esta cuenta. El filtrado puede realizarse con seguridad basada en roles o bien con seguridad de nivel de fila.

## <a name="role-based-security"></a>Seguridad basada en roles

Los modelos proporcionan seguridad basada en roles de usuario. Los roles para un proyecto de modelo determinado se definen durante la creación en SQL Server Data Tools – Business Intelligence (SSDT-BI), o después de que se implementa un modelo, mediante SQL Server Management Studio (SSMS). Los roles contienen miembros por nombre de usuario o grupo de Windows. Los roles definen los permisos que un usuario tiene para consultar o realizar acciones en el modelo. La mayoría de los usuarios pertenecerá a un rol con permisos de lectura. Otros roles están diseñados para los administradores con permisos para procesar elementos, administrar funciones de bases de datos y administrar otros roles.

## <a name="row-level-security"></a>Seguridad de nivel de fila

La seguridad de nivel de fila es específica de la seguridad de nivel de fila de Analysis Services. Los modelos pueden proporcionar seguridad dinámica de nivel de fila. A diferencia de tener al menos un rol al que pertenezcan usuarios, la seguridad dinámica no es necesaria para cualquier modelo tabular. En un nivel avanzado, la seguridad dinámica define el acceso de lectura a datos de un usuario delimitado a una fila particular en una tabla específica. Similar a lo que ocurre con los roles, la seguridad dinámica de nivel de fila se basa en el nombre de usuario de Windows de un usuario.

La capacidad de los usuarios para consultar y ver datos de un modelo está determinada, en primer lugar, por los roles a los que pertenece su cuenta de usuario de Windows y, en segundo lugar, por la seguridad dinámica de nivel de fila, si está configurada.

La implementación de la seguridad dinámica de nivel de fila y de roles en los modelos queda fuera del ámbito de este artículo. Puede obtener más información en [Roles (SSAS tabular)](https://msdn.microsoft.com/library/hh213165.aspx) y [Roles de seguridad (Analysis Services - Datos multidimensionales)](https://msdn.microsoft.com/library/ms174840.aspx) en MSDN. Y, para ver una descripción más detallada de la seguridad de los modelos tabulares, descargue y lea el [documento técnico Securing the Tabular BI Semantic Model](https://msdn.microsoft.com/library/jj127437.aspx) (Protección del modelo semántico tabular de BI).

## <a name="what-about-azure-active-directory"></a>¿Qué pasa con Azure Active Directory?

Los servicios en la nube de Microsoft dejan la autenticación de los usuarios a cargo de [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis). Azure Active Directory es el inquilino que contiene grupos de nombres de usuario y seguridad. Normalmente, la dirección de correo con la que un usuario inicia sesión coincide con el UPN de la cuenta.

¿Cuál es mi rol de Active Directory local?

Para que Analysis Services determine si un usuario que se conecta a él pertenece a un rol con permisos para leer los datos, el servidor debe convertir el nombre de usuario efectivo pasado de AAD a la puerta de enlace y de ahí al servidor de Analysis Services. El servidor de Analysis Services pasa el nombre de usuario efectivo a un controlador de dominio (DC) de Windows Active Directory. El controlador de dominio de Active Directory, a su vez, valida que el nombre de usuario efectivo es un UPN válido en una cuenta local y devuelve el nombre de usuario de Windows de ese usuario al servidor de Analysis Services.

No se puede usar EffectiveUserName en un servidor de Analysis Services que no esté unido a un dominio. El servidor de Analysis Services debe estar unido a un dominio para evitar errores de inicio de sesión.

### <a name="how-do-i-tell-what-my-upn-is"></a>¿Cómo sé cuál es mi UPN?

Es posible que no sepa cuál es su UPN y que no sea un administrador de dominio. Puede utilizar el siguiente comando en la estación de trabajo para averiguar el UPN de la cuenta.

    whoami /upn

El resultado será similar a una dirección de correo electrónico, pero se trata del UPN correspondiente a la cuenta de dominio. Si va a usar un origen de datos de Analysis Services para las conexiones dinámicas, y no coincide con la dirección de correo electrónico con la que inicia sesión en Power BI, puede consultar la sección sobre [asignación de nombres de usuario](#mapping-usernames-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizar un servidor de Active Directory local con Azure Active Directory

Querrá que las cuentas de Active Directory locales coincidan con Azure Active Directory si va a usar conexiones dinámicas de Analysis Services. Al igual que el UPN debe coincidir entre las cuentas.

Los servicios en la nube solo conocen las cuentas de Azure Active Directory. No importa si ha agregado una cuenta en su Active Directory local, si no existe en AAD, no se puede usar. Hay diferentes formas para hacer coincidir las cuentas de Active Directory locales con Azure Active Directory.

1. Puede agregar manualmente cuentas a Azure Active Directory.

   Puede crear una cuenta en Azure Portal o en el Centro de administración de Microsoft 365, y el nombre de la cuenta coincide con el UPN de la cuenta de Active Directory local.

2. Puede usar la herramienta [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) para sincronizar las cuentas locales para el inquilino de Azure Active Directory.

   La herramienta Azure AD Connect proporciona opciones para la sincronización de directorios y la configuración de autenticación, como la sincronización de hash de contraseña, la autenticación de paso a través y la federación. Si no es un administrador de inquilinos o un administrador de dominio local, tendrá que ponerse en contacto con el administrador de TI para configurarlo.

El uso de Azure AD Connect garantiza que el UPN coincida entre AAD y Active Directory local.

> [!NOTE]
> La sincronización de cuentas con la herramienta Azure AD Connect creará cuentas nuevas dentro de su inquilino de AAD.

## <a name="using-the-data-source"></a>Uso del origen de datos

Después de haber creado el origen de datos, estará disponible para usarse con conexiones dinámicas o a través de una actualización programada.

> [!NOTE]
> El nombre del servidor y de la base de datos deben coincidir entre Power BI Desktop y el origen de datos dentro de la puerta de enlace de datos local.

El vínculo entre el conjunto de datos y el origen de datos dentro de la puerta de enlace se basa en el nombre del servidor y en el nombre de la base de datos. Estos tienen que coincidir. Por ejemplo, si proporciona una dirección IP para el nombre del servidor, dentro de Power BI Desktop, tendrá que usar la dirección IP del origen de datos dentro de la configuración de la puerta de enlace. Si usa *SERVIDOR\INSTANCIA*, en Power BI Desktop, tendrá que usar lo mismo dentro del origen de datos configurado para la puerta de enlace.

Este es el caso tanto para conexiones dinámicas como para actualización programada.

### <a name="using-the-data-source-with-live-connections"></a>Uso del origen de datos con conexiones dinámicas

Tendrá que asegurarse de que el nombre del servidor y de la base de datos coinciden entre Power BI Desktop y el origen de datos configurado para la puerta de enlace. También necesitará asegurarse de que el usuario aparece en la pestaña **Usuarios** del origen de datos para poder publicar conjuntos de datos de conexiones dinámicas. La selección, para conexiones dinámicas, se produce dentro de Power BI Desktop al importar los datos por primera vez.

Después de publicar, ya sea desde Power BI Desktop o desde **Obtener datos**, los informes deben empezar a funcionar. La conexión puede tardar varios minutos en poderse usar después de crear el origen de datos dentro de la puerta de enlace.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Uso del origen de datos con actualización programada

Si aparece en la pestaña **Usuarios** del origen de datos configurado dentro de la puerta de enlace y los nombres del servidor y de la base de datos coinciden, verá la puerta de enlace como una opción para usar con la actualización programada.

![Representación de los usuarios](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Limitaciones de conexiones activas de Analysis Services

Puede usar una conexión activa con instancias tabulares o multidimensionales.

| **Versión del servidor** | **SKU necesario** |
| --- | --- |
| 2012 SP1 CU4 o posterior |SKU Business Intelligence y Enterprise |
| 2014 |SKU Business Intelligence y Enterprise |
| 2016 |SKU estándar o superior |

* Las características de formato de nivel de celda y traducción no se admiten.
* Las acciones y los conjuntos con nombre no se exponen en Power BI, pero todavía puede conectarse a los cubos multidimensionales que también contengan acciones o conjuntos con nombre, y crear objetos visuales e informes.

## <a name="next-steps"></a>Pasos siguientes

* [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot)
* [Solución de problemas de puertas de enlace: Power BI](service-gateway-onprem-tshoot.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

