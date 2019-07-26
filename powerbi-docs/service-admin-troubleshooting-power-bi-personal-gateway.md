---
title: Solución de problemas de Power BI Gateway - Personal
description: Solución de problemas de Power BI Gateway - Personal
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 7827ce359022eccfb75798b08da164b7504c84df
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271825"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Solución de problemas de Power BI Gateway - Personal

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

En las secciones siguientes se examinan algunos problemas comunes que se pueden producir al usar Power BI Gateway - Personal.

## <a name="update-to-the-latest-version"></a>Actualizar a la versión más reciente

La versión actual de la puerta de enlace para uso personal es la **puerta de enlace de datos local (personal)** . Actualice la instalación para usar esa versión.

Si la versión de la puerta de enlace no está actualizada, pueden aparecer muchos problemas.  Es una buena práctica general asegurarse de que tiene la versión más reciente. Si no ha actualizado la puerta de enlace durante un mes o más, considere la posibilidad de instalar la versión más reciente. Después, compruebe si puede reproducir el problema.

## <a name="installation"></a>Instalación
**La puerta de enlace personal es de 64 bits**: si el equipo es de 32 bits, no puede instalar la puerta de enlace personal. El sistema operativo debe ser una versión de 64 bits. Instale una versión de 64 bits de Windows o instale la puerta de enlace personal en un equipo de 64 bits.

**No se puede instalar la puerta de enlace personal como servicio, aunque sea un administrador local del equipo**: se puede producir un error en la instalación si el usuario está en el grupo de administradores locales del equipo, pero la directiva de grupo no permite que ese nombre de usuario inicie sesión como un servicio. Por ahora, asegúrese de que la directiva de grupo permite a un usuario iniciar sesión como un servicio. Estamos trabajando para solucionar este problema. [Más información](https://technet.microsoft.com/library/cc739424.aspx)

**La operación ha agotado el tiempo de espera**: este mensaje es frecuente si el equipo (físico o máquina virtual) en el que se instala la puerta de enlace personal tiene un procesador de un solo núcleo. Cierre todas las aplicaciones y desactive todos los procesos que no sean esenciales. Luego, intente realizar la instalación de nuevo.

**La puerta de enlace de administración de datos o Analysis Services Connector no pueden instalarse en el mismo equipo que la puerta de enlace personal**: si ya tiene instalada una instancia de Analysis Services Connector o puerta de enlace de administración de datos, primero debe desinstalar el conector o la puerta de enlace. Después, intente instalar la puerta de enlace personal.

> [!NOTE]
> Si detecta un problema durante la instalación, los registros de instalación pueden proporcionar información para ayudarle a resolverlo. Para más información, vea [Registros de instalación](#SetupLogs).
> 
> 

 **Configuración de proxy** Puede ver problemas con la configuración de la puerta de enlace personal si el entorno necesita el uso de un proxy. Para más información sobre cómo configurar la información de proxy, vea [Configurar parámetros proxy para la puerta de enlace de datos local](/data-integration/gateway/service-gateway-proxy).

## <a name="schedule-refresh"></a>Programar actualización
**Error: Falta la credencial almacenada en la nube.**

Es posible que reciba este error en la configuración del \<conjunto de datos\> si tiene una actualización programada y, después, desinstala y vuelve a instalar la puerta de enlace personal. Si desinstala una puerta de enlace personal, las credenciales del origen de datos para un conjunto de datos que se ha configurado para la actualización se quitan del servicio Power BI.

**Solución:** En Power BI, vaya a la configuración de actualización de un conjunto de datos. En Administrar orígenes de datos, para cualquier origen de datos con un error, seleccione **Editar credenciales** y vuelva a iniciar la sesión en el origen de datos.

**Error: Las credenciales proporcionadas para el conjunto de datos no son válidas. Actualice las credenciales a través de una actualización o en el cuadro de diálogo Configuración de origen de datos para continuar.**

**Solución**: Si recibe un mensaje de credenciales, puede significar que:

* Tiene que asegurarse de que los nombres de usuario y las contraseñas para el inicio de sesión en los orígenes de datos estén actualizados. En Power BI, vaya a la configuración de actualización de un conjunto de datos. En Administrar orígenes de datos, seleccione **Editar credenciales** para actualizar las credenciales del origen de datos.
* Los mashups entre un origen en la nube y uno local, en una sola consulta, no se pueden actualizar en la puerta de enlace personal si uno de los orígenes usa OAuth para la autenticación. Un ejemplo de este problema es un mashup entre CRM Online y un servidor SQL Server local. Se produce un error en el mashup porque CRM Online requiere OAuth.
  
  Se trata de un problema conocido y que se está examinando. Para solucionar el problema, tenga una consulta independiente para el origen en la nube y el origen local. Después, use una consulta de combinación o de datos anexados para combinarlos.

**Error: Origen de datos no admitido.**

**Solución:** si recibe un mensaje de origen de datos no admitido en la configuración de Programar actualización, puede tener el significado que se indica a continuación: 

* El origen de datos no se admite actualmente para la actualización en Power BI. 
* El libro de Excel no contiene un modelo de datos, solo datos de la hoja de cálculo. Actualmente, Power BI solo admite la actualización si el libro de Excel cargado contiene un modelo de datos. Al importar datos mediante Power Query en Excel, asegúrese de elegir la opción para cargar los datos en el modelo de datos. Esta opción garantiza la importación de los datos en un modelo de datos. 

**Error: [No se pueden combinar los datos] &lt;parte de la consulta&gt;/&lt;…&gt;/&lt;…&gt; está accediendo a orígenes de datos con niveles de privacidad que no se pueden usar juntos. Vuelva a generar esta combinación de datos.**

**Solución**: Este error se debe a las restricciones de nivel de privacidad y a los tipos de orígenes de datos que usa.

**Error: Error de origen de datos: no se puede convertir el valor "\[Table\]" al tipo Table.**

**Solución**: Este error se debe a las restricciones de nivel de privacidad y a los tipos de orígenes de datos que usa.

**Error: No hay suficiente espacio para esta fila.**

Este error se produce si tiene una sola fila que ocupe más de 4 MB. Busque la fila del origen de datos e intente filtrarla o reducir su tamaño.

## <a name="data-sources"></a>Orígenes de datos
**Falta el proveedor de datos**: la puerta de enlace personal es solo para versiones de 64 bits. Para que los proveedores de datos se puedan instalar en el mismo equipo que la puerta de enlace personal, se requiere una versión de 64 bits. Por ejemplo, si el origen de datos del conjunto de datos es Microsoft Access, debe instalar al proveedor ACE de 64 bits en el mismo equipo en el que instaló la puerta de enlace personal.  

>[!NOTE]
>Si tiene la versión de Excel de 32 bits, no puede instalar un proveedor ACE de la versión de 64 bits en el mismo equipo.

**No se admite la autenticación de Windows en la base de datos de Access**: actualmente, Power BI solo admite la autenticación anónima para la base de datos de Access. Estamos trabajando para habilitar la autenticación de Windows para la base de datos de Access.

**Error de inicio de sesión al especificar las credenciales de un origen de datos**: si recibe un error como este al escribir las credenciales de Windows para un origen de datos, es posible que aún tenga una versión anterior de la puerta de enlace personal. [Instale la versión más reciente de Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Error: Error de inicio de sesión al seleccionar la autenticación de Windows para un origen de datos mediante ACE OLEDB**: si se muestra el siguiente error al especificar las credenciales de origen de datos para un origen de datos mediante el proveedor ACE OLEDB:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

En la actualidad Power BI no admite la autenticación de Windows para un origen de datos mediante el proveedor ACE OLEDB.

**Solución:** Para solucionar este error, puede seleccionar la **autenticación anónima**. Para el proveedor ACE OLEDB heredado, las credenciales anónimas equivalen a las de Windows.

## <a name="tile-refresh"></a>Actualización de iconos
Si recibe un error relacionado con la actualización de los iconos de panel, consulte el artículo siguiente.

[Solución de problemas de errores de icono](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Herramientas de solución de problemas
### <a name="refresh-history"></a>Actualizar historial
**Actualizar historial** ayuda a ver qué errores se han producido y proporciona datos útiles en caso de que tenga que crear una solicitud de soporte técnico. Puede ver tanto las actualizaciones programadas como las actualizaciones a petición. A continuación se muestra cómo acceder a **Actualizar historial**.

1. En el panel de navegación de Power BI, en **Conjuntos de datos**, seleccione un conjunto de datos &gt; menú Abrir &gt; **Programar actualización**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. En **Configuración de...** , seleccione **Actualizar historial**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Registros de eventos
Varios registros de eventos pueden proporcionar información. Los dos primeros, **Puerta de enlace de administración de datos** y **PowerBIGateway**, están presentes si es administrador del equipo.  Si no es administrador y usa la puerta de enlace personal, verá las entradas de registro dentro del registro **Aplicación**.

Los registros **Data Management Gateway** y **PowerBIGateway** están presentes en el área de **Registros de aplicaciones y servicios**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Seguimiento de Fiddler
[Fiddler](http://www.telerik.com/fiddler) es una herramienta gratuita de Telerik que supervisa el tráfico HTTP. Puede ver la comunicación con el servicio Power BI desde el equipo cliente. Esta comunicación puede mostrar errores y otra información relacionada.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Registros de instalación
Si no se puede instalar la **puerta de enlace personal**, verá un vínculo para mostrar el registro de instalación. El registro de instalación puede mostrar información detallada sobre el error. Estos registros son registros de instalación de Windows, también conocidos como registros MSI. Pueden ser bastante complejos y difíciles de leer. Normalmente el error resultante está al final, pero determinar su causa no es fácil. Podría ser el resultado de errores en un registro diferente, o de un error que aparece más arriba en el registro.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

O bien, puede ir a la **carpeta Temp** (%temp%) y buscar los archivos que empiezan por**Power\_BI\_** .

> [!NOTE]
> Si va a %temp%, es posible que llegue a una subcarpeta de archivos temporales. Los archivos de **Power\_BI\_** están en la raíz del directorio temporal.  Puede que tenga que subir un nivel o dos.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Pasos siguientes
[Configuración de los valores del proxy para la puerta de enlace de datos local](/data-integration/gateway/service-gateway-proxy)  
[Actualización de datos](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[Solución de problemas de errores de icono](refresh-troubleshooting-tile-errors.md)  
[Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md)  
¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

