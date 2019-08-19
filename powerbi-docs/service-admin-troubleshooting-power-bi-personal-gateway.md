---
title: Solución de problemas de Power BI Gateway (modo personal)
description: Solución de problemas de Power BI Gateway (modo personal)
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: db74f38dac655ee4d3eac8722a1cd3f70b5ab1a3
ms.sourcegitcommit: 9665bdabce3bfc31f68dd8256b135bfd56f60589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68832583"
---
# <a name="troubleshooting-power-bi-gateway-personal-mode"></a>Solución de problemas de Power BI Gateway (modo personal)

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

En las secciones siguientes se examinan algunos problemas comunes que se pueden producir al usar la puerta de enlace de datos local (modo personal) de Power BI.

## <a name="update-to-the-latest-version"></a>Actualizar a la versión más reciente

La versión actual de la puerta de enlace para uso personal es la puerta de enlace de datos local (modo personal). Actualice la instalación para usar esa versión.

Si la versión de la puerta de enlace no está actualizada, pueden aparecer muchos problemas. Es una buena práctica general asegurarse de que tiene la versión más reciente. Si no ha actualizado la puerta de enlace durante un mes o más, considere la posibilidad de instalar la versión más reciente. Después, compruebe si puede reproducir el problema.

## <a name="installation"></a>Instalación
**La puerta de enlace (modo personal) funciona en las versiones de 64 bits:** Si la máquina es una versión de 32 bits, no puede instalar la puerta de enlace (modo personal). El sistema operativo debe ser una versión de 64 bits. Instale una versión de 64 bits de Windows o instale la puerta de enlace (modo personal) en una máquina de 64 bits.

**La puerta de enlace (modo personal) no se puede instalar como servicio, aunque el usuario sea administrador local del equipo:** Se puede producir un error en la instalación si el usuario está en el grupo de administradores locales del equipo, pero la directiva de grupo no permite que ese nombre de usuario inicie sesión como servicio. Asegúrese de que la directiva de grupo permite a un usuario iniciar sesión como servicio. Estamos trabajando para solucionar este problema. Para obtener más información, vea el artículo sobre la [adición del derecho de inicio de sesión como servicio a una cuenta](https://technet.microsoft.com/library/cc739424.aspx).

**Se agotó el tiempo de espera de la operación:** este mensaje es frecuente si el equipo (máquina física o máquina virtual) en el que se instala la puerta de enlace (modo personal) tiene un procesador de un solo núcleo. Cierre todas las aplicaciones, desactive todos los procesos que no sean esenciales e intente realizar la instalación de nuevo.

**La puerta de enlace de administración de datos o el conector de Analysis Services no se pueden instalar en el mismo equipo que la puerta de enlace (modo personal):** si ya tiene instalado un conector de Analysis Services o una puerta de enlace de administración de datos, debe desinstalar primero el conector o la puerta de enlace. Después, intente instalar la puerta de enlace (modo personal).

> [!NOTE]
> Si detecta un problema durante la instalación, los registros de instalación pueden proporcionar información para ayudarle a resolverlo. Para obtener más información, vea [Registros de instalación](#SetupLogs).
> 
> 

 **Configuración de proxy:** puede que encuentre problemas con la configuración de la puerta de enlace (modo personal) si su entorno requiere el uso de un proxy. Para obtener más información sobre cómo configurar la información de proxy, vea [Configuración de proxy para la puerta de enlace de datos local](/data-integration/gateway/service-gateway-proxy).

## <a name="schedule-refresh"></a>Programar actualización
**Error: Falta la credencial almacenada en la nube.**

Es posible que reciba este error en la configuración del \<conjunto de datos\> si tiene una actualización programada y después desinstala y vuelve a instalar la puerta de enlace (modo personal). Si desinstala una puerta de enlace (modo personal), las credenciales del origen de datos para un conjunto de datos que se configuró para la actualización se quitan del servicio Power BI.

**Solución:** En Power BI, vaya a la configuración de actualización de un conjunto de datos. En **Administrar orígenes de datos**, para cualquier origen de datos con un error, seleccione **Editar credenciales**. Luego, vuelva a iniciar sesión en el origen de datos.

**Error: Las credenciales proporcionadas para el conjunto de datos no son válidas. Actualice las credenciales a través de una actualización o en el cuadro de diálogo Configuración de origen de datos para continuar.**

**Solución:** Si recibe un mensaje de credenciales, puede significar que:

* Los nombres de usuario y las contraseñas que usa para iniciar sesión en los orígenes de datos no estén actualizados. En Power BI, vaya a la configuración de actualización de un conjunto de datos. En **Administrar orígenes de datos**, seleccione **Editar credenciales** para actualizar las credenciales del origen de datos.
* En una consulta única, los mashups entre un origen en la nube y uno local no se actualizan en la puerta de enlace (modo personal) si uno de los orígenes usa OAuth para la autenticación. Un ejemplo de este problema es un mashup entre CRM Online y una instancia de SQL Server local. Se produce un error en el mashup porque CRM Online requiere OAuth.
  
  Se trata de un problema conocido que se está examinando. Para solucionar el problema, tenga una consulta independiente para el origen en la nube y el origen local. Después, use una consulta de combinación o de datos anexados para combinarlos.

**Error: Origen de datos no admitido.**

**Solución:** Si recibe un mensaje de origen de datos no admitido en la configuración de **Programar actualización**, podría indicar que: 

* El origen de datos no se admite actualmente para la actualización en Power BI. 
* El libro de Excel no contiene un modelo de datos, solo datos de la hoja de cálculo. Actualmente, Power BI solo admite la actualización si el libro de Excel cargado contiene un modelo de datos. Al importar datos mediante Power Query en Excel, elija la opción **Cargar** para cargar los datos en un modelo de datos. Esta opción garantiza la importación de los datos en un modelo de datos. 

**Error: [No se pueden combinar los datos] &lt;parte de la consulta&gt;/&lt;…&gt;/&lt;…&gt; está accediendo a orígenes de datos con niveles de privacidad que no se pueden usar juntos. Vuelva a generar esta combinación de datos.**

**Solución:** Este error se debe a las restricciones de nivel de privacidad y a los tipos de orígenes de datos que usa.

**Error: Error de origen de datos: no se puede convertir el valor "\[Table\]" al tipo Table.**

**Solución:** Este error se debe a las restricciones de nivel de privacidad y a los tipos de orígenes de datos que usa.

**Error: No hay suficiente espacio para esta fila.**

**Solución:** Este error se produce si tiene una sola fila que ocupe más de 4 MB. Busque la fila en el origen de datos e intente filtrarla o reducir su tamaño.

## <a name="data-sources"></a>Orígenes de datos
**Falta el proveedor de datos:** La puerta de enlace (modo personal) solo funciona en versiones 64 bits. Para que los proveedores de datos se puedan instalar en el mismo equipo que la puerta de enlace (modo personal), se requiere una versión de 64 bits. Por ejemplo, si el origen de datos del conjunto de datos es Microsoft Access, debe instalar al proveedor ACE de 64 bits en el mismo equipo en el que instaló la puerta de enlace (modo personal). 

>[!NOTE]
>Si tiene una versión de Excel de 32 bits, no puede instalar un proveedor ACE de la versión de 64 bits en el mismo equipo.

**La autenticación de Windows no es compatible con la base de datos de Access:** Power BI actualmente solo admite la autenticación anónima en la base de datos de Access.

**Error: Error de inicio de sesión al escribir las credenciales de un origen de datos:** Si obtiene un error como este al escribir las credenciales de Windows para un origen de datos: 

  ![Mensaje de error de credenciales de Windows](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

Es posible que todavía se encuentre en una versión anterior de la puerta de enlace (modo personal). 

**Solución:** Para obtener más información, vea el artículo sobre la [instalación de la versión más reciente de Power BI Gateway (modo personal)](https://powerbi.microsoft.com/gateway/).

**Error: Error de inicio de sesión al seleccionar la autenticación de Windows para un origen de datos mediante ACE OLEDB:** Si obtiene el siguiente error al especificar las credenciales del origen de datos para un origen de datos mediante un proveedor ACE OLEDB:

![Mensaje de error de credenciales de origen de datos](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Power BI no admite actualmente la autenticación de Windows para un origen de datos mediante el proveedor ACE OLEDB.

**Solución:** Para solucionar este error, seleccione **Autenticación anónima**. En el caso de un proveedor ACE OLEDB heredado, las credenciales anónimas equivalen a las de Windows.

## <a name="tile-refresh"></a>Actualización de iconos
Si obtiene un error al actualizar los mosaicos del panel, vea [Solución de problemas de errores de icono](refresh-troubleshooting-tile-errors.md).

## <a name="tools-for-troubleshooting"></a>Herramientas de solución de problemas
### <a name="refresh-history"></a>Actualizar historial
Con **Actualizar historial**, puede ver los errores que se han producido y buscar datos útiles en caso de que tenga que crear una solicitud de soporte técnico. Puede ver tanto las actualizaciones programadas como las actualizaciones a petición. A continuación se muestra cómo acceder a **Actualizar historial**.

1. En el panel de navegación de Power BI, seleccione un conjunto de datos en **Conjuntos de datos**. Abra el menú y seleccione **Programar actualización**.

   ![Selección de Programar actualización](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. En **Configuración de...** , seleccione **Actualizar historial**. 

   ![Selección de Actualizar historial](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![Información de Actualizar historial](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Registros de eventos
Varios registros de eventos pueden proporcionar información. Los dos primeros, **Puerta de enlace de administración de datos** y **PowerBIGateway**, están presentes si es administrador del equipo. Si no es administrador y usa la puerta de enlace de datos local (modo personal), verá las entradas de registro en el **registro de aplicaciones**.

Los registros **Data Management Gateway** y **PowerBIGateway** están presentes en el área de **Registros de aplicaciones y servicios**.

![Registros de puerta de enlace de administración de datos y PowerBIGateway](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Seguimiento de Fiddler
[Fiddler](http://www.telerik.com/fiddler) es una herramienta gratuita de Telerik que supervisa el tráfico HTTP. Puede ver la comunicación con el servicio Power BI desde el equipo cliente. Es posible que esta comunicación muestre errores y otra información relacionada.

![Seguimiento de Fiddler](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Registros de instalación
Si no se puede instalar la puerta de enlace (modo personal), verá un vínculo para mostrar el registro de instalación. El registro de instalación puede mostrar información detallada sobre el error. Estos registros son registros de instalación de Windows, también conocidos como registros MSI. Pueden ser bastante complejos y difíciles de leer. Normalmente el error resultante está al final, pero determinar su causa no es fácil. Podría ser el resultado de errores en un registro diferente. También podría ser el resultado de un error que aparece más arriba en el registro.

![Vínculo al registro de instalación](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

O bien, puede ir a la carpeta Temp (%temp%) y buscar los archivos que empiezan por *Power\_BI\_* .

> [!NOTE]
> Si va a %temp%, es posible que acabe en una subcarpeta de Temp. Los archivos de *Power\_BI\_* se encuentran en la raíz del directorio Temp. Puede que tenga que subir un nivel o dos.
> 
> 

![Carpeta Temp](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Pasos siguientes
- [Configuración de los valores del proxy para la puerta de enlace de datos local](/data-integration/gateway/service-gateway-proxy)- [Actualización de datos](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [Solución de problemas de errores de icono](refresh-troubleshooting-tile-errors.md)  
- [Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md) 
 
¿Tiene más preguntas? Pruebe a preguntar a la [comunidad de Power BI](http://community.powerbi.com/).

