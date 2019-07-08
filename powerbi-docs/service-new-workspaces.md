---
title: Organización del trabajo en las nuevas áreas de trabajo en Power BI
description: Obtenga información sobre las nuevas áreas de trabajo, que son colecciones de paneles e informes creadas para proporcionar métricas clave a su organización.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a3982716ac2eb64f7512ba6ef606af299f1c5f46
ms.sourcegitcommit: 8dee40f07d284ec84a8afa0100359f146e1dd88b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67418660"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organización del trabajo en las nuevas áreas de trabajo en Power BI

 Las *áreas de trabajo* son lugares donde se colabora con compañeros para crear colecciones de paneles, informes e informes paginados. La nueva experiencia de áreas de trabajo le ayuda a administrar mejor el acceso al contenido. En este artículo se describen las nuevas áreas de trabajo y cómo se diferencian de las áreas de trabajo clásicas.  Al igual que con las áreas de trabajo clásicas, se siguen utilizando para crear y distribuir aplicaciones. Obtenga información sobre cómo [crear una nueva experiencia de áreas de trabajo](service-create-the-new-workspaces.md).

La nueva experiencia de áreas de trabajo ha alcanzado la disponibilidad general (GA) y ahora es el área de trabajo predeterminada. Aún puede continuar creando y utilizando [áreas de trabajo clásicas](service-create-workspaces.md) en función de los grupos de Office 365. 

> [!NOTE]
> Para imponer la seguridad de nivel de fila (RLS) para los usuarios que exploran el contenido en un área de trabajo, use el rol Visor. Si el rol Visor aún no está disponible en el inquilino, continúe usando las [áreas de trabajo clásicas](service-create-workspaces.md) y seleccione la opción **Los miembros solo pueden ver contenido de Power BI**. También puede publicar una aplicación de Power BI a los usuarios o distribuir contenido mediante el uso compartido.

Con las nuevas áreas de trabajo puede hacer lo siguiente:

- Asignar roles de área de trabajo a grupos de usuarios: grupos de seguridad, listas de distribución, grupos de Office 365 y usuarios.
- Crear un área de trabajo en Power BI sin crear un grupo de Office 365.
- Usar roles de las áreas de trabajo más granulares para flexibilizar la administración de permisos en un área de trabajo.
- Los administradores de Power BI pueden controlar quién puede crear áreas de trabajo en Power BI.

Cuando crea una de las nuevas áreas de trabajo, no crea un grupo de Office 365 subyacente, asociado. Toda la administración del área de trabajo se realiza en Power BI, no en Office 365. En la nueva experiencia de áreas de trabajo, ahora puede agregar un grupo de Office 365 en la lista de acceso del área de trabajo para seguir administrando el acceso de los usuarios al contenido a través de grupos de Office 365.

## <a name="administering-new-workspace-experience-workspaces"></a>Administración de áreas de trabajo de la nueva experiencia de áreas de trabajo
La administración de las áreas de trabajo de la nueva experiencia de áreas de trabajo está ahora en Power BI. Los administradores de Power BI deciden qué usuarios de una organización pueden crear áreas de trabajo. También pueden administrar y recuperar áreas de trabajo. Para ello necesitan usar el portal de administración de Power BI o los cmdlets de PowerShell. Para las áreas de trabajo clásicas basadas en grupos de Office 365, la administración continúa ocurriendo en el portal de administración de Office 365 y en Azure Active Directory.

En **Configuración del área de trabajo**, en el portal de administración, los administradores pueden usar la opción Creación de áreas de trabajo (nueva experiencia de áreas de trabajo) para permitir que todos los usuarios de una organización (o ninguno de ellos) creen nuevas áreas de trabajo de experiencia de áreas de trabajo. También pueden restringir la creación de estas áreas a miembros de grupos de seguridad específicos.

> [!NOTE]
> La opción Creación de áreas de trabajo (nueva experiencia de áreas de trabajo) establece de forma predeterminada que solo los usuarios que pueden crear grupos de Office 365 puedan crear las nuevas áreas de trabajo en Power BI. Asegúrese de establecer un valor en el portal de administración de Power BI para garantizar que los usuarios apropiados puedan crear nuevas áreas de trabajo de experiencia de áreas de trabajo.

![Configuración del área de trabajo en el portal de administración](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

La [lista de áreas de trabajo está disponible](service-admin-portal.md#workspaces) en el portal de administración de Power BI. 

![Lista de áreas de trabajo](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Nuevas áreas de trabajo en paralelo con las áreas de trabajo clásicas

Las áreas de trabajo nuevas y actualizadas y las áreas de trabajo clásicas existentes coexisten en paralelo y puede crear cualquiera de ellas. La nueva experiencia de áreas de trabajo es el tipo de área de trabajo predeterminado. Power BI sigue enumerando todos los grupos de Office 365 de los que el usuario es miembro en Power BI para evitar cambiar los flujos de trabajo existentes. Para información sobre cómo crear una nueva área de trabajo, lea [Creación de nuevas áreas de trabajo](service-create-the-new-workspaces.md). Para información sobre cómo crear un área de trabajo clásica, lea [Creación de áreas de trabajo clásicas](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Roles en las nuevas áreas de trabajo

Para conceder acceso a una nueva área de trabajo, agregue grupos de usuarios o individuos a uno de los roles de área de trabajo: visores, miembros, colaboradores o administradores. Todos los miembros de un grupo de usuarios obtienen el rol que haya definido. Si un usuario está en varios grupos de usuarios, obtiene el nivel de permiso mayor proporcionado por los roles que se les asignan.

Los roles le permiten administrar quién puede hacer qué en un área de trabajo, para que los equipos puedan colaborar. Las nuevas áreas de trabajo le permiten asignar roles a usuarios y grupos de usuarios: grupos de seguridad, grupos de Office 365 y listas de distribución. 

Al asignar roles a un grupo de usuarios, cada uno de ellos tiene acceso al contenido. Si anida grupos de usuarios, todos los usuarios contenidos tienen permiso. Un usuario que se encuentra en varios grupos de usuarios con distintos roles obtiene el nivel de permiso mayor concedido a ellos. 

Las nuevas áreas de trabajo ofrecen cuatro roles: administradores, miembros, colaboradores y visores.

|Funcionalidad   | Administrador  | Miembro  | Colaborador  | Visor |
|---|---|---|---|---|
| Actualizar y eliminar el área de trabajo.  | X  |   |   |   | 
| Agregar o quitar usuarios, incluidos otros administradores.  | X  |   |   |   |
| Agregar miembros u otros usuarios con permisos inferiores.  |  X | X  |   |   |
| Publicar y actualizar una aplicación. |  X | X  |   |   |
| Compartir un elemento o compartir una aplicación. |  X | X  |   |   |
| Permitir que otros usuarios vuelvan a compartir elementos. |  X | X  |   |   |
| Crear, editar y eliminar contenido en el área de trabajo.  |  X | X  | X  |   |
| Publicar informes en el área de trabajo, eliminar contenido.  |  X | X  | X  |   |
| Ver un elemento. |  X | X  | X  | X  |
 
 
## <a name="licensing"></a>Licencias
Todos los usuarios que agregue a un área de trabajo en la capacidad compartida necesitan una licencia de Power BI Pro. En el área de trabajo, estos usuarios pueden colaborar en paneles e informes que planee publicar para un público más amplio, o incluso para toda la organización. 

Si quiere distribuir contenido a otros usuarios dentro de la organización, puede asignar licencias de Power BI Pro a los usuarios o colocar el área de trabajo en una capacidad de Power BI Premium.

Cuando el área de trabajo está en una capacidad de Power BI Premium, los usuarios con el rol Visor pueden acceder al área de trabajo incluso si no tienen una licencia de Power BI Pro. Sin embargo, si asigna un rol superior a estos usuarios, como Administrador, Miembro o Colaborador, no podrán acceder al área de trabajo. Se les pedirá que inicien una prueba Pro cuando intenten acceder al área de trabajo. Para aprovechar la capacidad del rol Visor para los usuarios sin licencias Pro, asegúrese de que los usuarios de dicho rol no están en otros roles de área de trabajo, ya sea individualmente o a través de un grupo de usuarios. 

> [!NOTE]
> La publicación de informes en la nueva experiencia de áreas de trabajo tiene el cumplimiento más estricto de las reglas de licencia existentes. Los usuarios que intentan publicar desde Power BI Desktop u otras herramientas cliente sin una licencia Pro ven el error "Solo los usuarios con licencias de Power BI Pro pueden publicar en esta área de trabajo.".

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>¿En qué se diferencian las áreas de trabajo nuevas y las actuales?

Con las nuevas áreas de trabajo, algunas características se están rediseñando. Estos son algunos de los cambios que puede esperar que sean definitivos. 

* La creación de estas áreas de trabajo no creará grupos de Office 365, como sí los crean las áreas de trabajo clásicas. Sin embargo, ahora puede usar un grupo de Office 365 para proporcionar a los usuarios acceso al área de trabajo mediante la asignación de un rol. 
* En las áreas de trabajo clásicas solo puede agregar usuarios individuales a las listas de miembros y administradores. En las áreas de trabajo nuevas, puede agregar varios grupos de seguridad de AD, listas de distribución o grupos de Office 365 a estas listas para facilitar la administración de usuarios. 
- Puede crear un paquete de contenido de la organización desde un área de trabajo clásica, pero no desde las áreas de trabajo nuevas.
- Puede consumir un paquete de contenido de la organización desde un área de trabajo clásica. pero no desde las áreas de trabajo nuevas.

## <a name="workspace-contact-list"></a>Lista de contactos del área de trabajo
La nueva característica **Lista de contactos** le permite especificar qué usuarios reciben una notificación sobre los problemas que se producen en el área de trabajo. De forma predeterminada, se notifica a cualquier usuario o grupo especificado como administrador del área de trabajo, pero puede personalizar la lista. Los usuarios o grupos que aparecen en la lista de contactos se mostrarán en la interfaz de usuario (IU) para ayudar a los usuarios a obtener ayuda relacionada con el área de trabajo. 

Lea más sobre la [configuración de la lista de contactos del área de trabajo](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>Área de trabajo: OneDrive
La característica Área de trabajo: OneDrive permite configurar un grupo de Office 365 cuyo almacenamiento de archivos de la biblioteca de documentos de SharePoint esté disponible para los usuarios del área de trabajo. El grupo debe crearse fuera de Power BI. 

Power BI no sincroniza los permisos de los usuarios o grupos que están configurados para tener acceso al área de trabajo con la pertenencia al grupo de Office 365. El procedimiento recomendado es administrar el acceso al área de trabajo a través del mismo grupo de Office 365 cuyo almacenamiento de archivos se define en esta configuración. 

Obtenga información sobre cómo [establecer Área de trabajo: OneDrive y acceder a esta característica](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>Auditoría
Power BI audita las siguientes actividades para nuevas áreas de trabajo de experiencia de áreas de trabajo.

| Nombre descriptivo |   Nombre de operación |
|---|---|
| Carpeta de Power BI creada | CreateFolder |
| Carpeta de Power BI eliminada | DeleteFolder |
| Carpeta de Power BI actualizada | UpdateFolder |
| Acceso a la carpeta de Power BI actualizado| UpdateFolderAccess |

Lea más sobre la [auditoría de Power BI](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Limitaciones que se deben tener en cuenta:

- Las áreas de trabajo pueden contener un máximo de 1000 conjuntos de datos o 1000 informes por cada conjunto de datos. 
- Una persona con una licencia de Power BI Pro puede ser miembro de 1000 áreas de trabajo como máximo.
- Power BI Publisher para Excel no se admite.

## <a name="workspace-features-that-work-differently"></a>Características del área de trabajo que funcionan otra forma

Algunas características funcionan de manera diferente en las áreas de trabajo actuales y en las áreas de trabajo nuevas. Estas diferencias son intencionadas, basadas en los comentarios recibidos de los clientes, y permiten un enfoque más flexible para la colaboración con las áreas de trabajo:

- Cumplimiento de licencias: la publicación de informes en la nueva experiencia de áreas de trabajo aplica las reglas de licencia existentes que requieren una licencia de Power BI Pro para los usuarios que colaboran en áreas de trabajo o comparten contenido con otros usuarios en el servicio Power BI. Los usuarios sin una licencia Pro ven el error "Solo los usuarios con licencias de Power BI Pro pueden publicar en esta área de trabajo.".
- Posibilidad de que los miembros puedan volver a compartir o no: se ha reemplazado por el rol de Colaborador
- Áreas de trabajo de solo lectura: en lugar de conceder a los usuarios acceso de solo lectura a un área de trabajo, se asigna a los usuarios el rol Visor, que permite un acceso similar al de solo lectura al contenido de un área de trabajo.
- Los usuarios sin una licencia Pro pueden acceder al área de trabajo si esta tiene una capacidad de Power BI Premium, incluso si los usuarios solo tienen el rol Visor.
- Para permitir que los usuarios con el rol Visor exporten datos, asegúrese de que tengan permiso de compilación en los conjuntos de datos en el área de trabajo. Obtenga más información sobre [Permiso de compilación para conjuntos de datos](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).
- Ausencia del botón **Abandonar área de trabajo**.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

**¿Afecta la disponibilidad general de la nueva experiencia de áreas de trabajo a los vínculos a contenido existente?**

No. Los vínculos a los elementos existentes de las áreas de trabajo clásicas no se ven afectados por la nueva experiencia de áreas de trabajo. La disponibilidad general (GA) de la nueva experiencia de áreas de trabajo cambia el área de trabajo predeterminada que se crea, pero no cambia las áreas de trabajo existentes. 

**¿Se actualizan las áreas de trabajo existentes a la nueva experiencia de áreas de trabajo con disponibilidad general?**

No. La disponibilidad general de la nueva experiencia de áreas de trabajo solo cambia el tipo de área de trabajo predeterminado a la nueva experiencia de áreas de trabajo. Las áreas de trabajo clásicas existentes que se basan en grupos de Office 365 permanecen sin cambios.

**¿Las áreas de trabajo siguen creándose automáticamente para los grupos de Office 365?**

Sí. Dado que se admiten ambos tipos de áreas de trabajo en paralelo, seguimos enumerando todos los grupos de Office 365 a los que el usuario tiene acceso en la lista de áreas de trabajo.

## <a name="next-steps"></a>Pasos siguientes
* [Crear las nuevas áreas de trabajo en Power BI](service-create-the-new-workspaces.md)
* [Crear las áreas de trabajo clásicas](service-create-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](service-create-distribute-apps.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
