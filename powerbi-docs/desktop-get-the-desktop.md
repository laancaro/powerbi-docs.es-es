---
title: Obtener Power BI Desktop
description: Descarga e instalación de Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/09/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 444a6978b0fcf841f0d0a3b2d50cc70062389cba
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75222078"
---
# <a name="get-power-bi-desktop"></a>Obtener Power BI Desktop
Power BI Desktop le permite crear consultas, modelos e informes avanzados para visualizar datos. Con Power BI Desktop, puede crear modelos de datos, crear informes y compartir el trabajo mediante su publicación en el servicio Power BI. La descarga de Power BI Desktop es gratuita.

Puede obtener Power BI Desktop de dos maneras, que se describen en las secciones siguientes:

* [Instalarlo como una aplicación desde Microsoft Store](#install-as-an-app-from-the-microsoft-store).
* [Descargarlo directamente, como un archivo ejecutable que se descarga y se instala en el equipo](#download-power-bi-desktop-directly).

Con cualquiera de estos enfoques tendrá la versión más reciente de Power BI Desktop en el equipo, pero hay algunas diferencias que tener en cuenta y que se describen en las secciones siguientes.

## <a name="install-as-an-app-from-the-microsoft-store"></a>Instalar como una aplicación desde Microsoft Store
Hay varias maneras de acceder a la versión más reciente de Power BI Desktop desde Microsoft Store. 

1. Use una de las opciones siguientes para abrir la página **Power BI Desktop** de Microsoft Store:

   - Abra un explorador y vaya directamente a la [página de Power BI Desktop](https://aka.ms/pbidesktopstore) en Microsoft Store.

    - Desde el [servicio Power BI](https://docs.microsoft.com/power-bi/service-get-started), seleccione el icono **Descargar** de la esquina superior derecha y, después, seleccione **Power BI Desktop**.

      ![Descarga de Power BI Desktop desde el servicio Power BI](media/desktop-get-the-desktop/getpbid_downloads.png)

   - Vaya a la [página del producto Power BI Desktop](https://powerbi.microsoft.com/desktop/) y, después, seleccione **Descarga gratuita**.
  
2. Una vez en la página **Power BI Desktop** de Microsoft Store, seleccione **Instalar**.

     ![Obtención de Power BI Desktop desde Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Hay algunas ventajas si obtiene Power BI Desktop desde Microsoft Store:

* **Actualizaciones automáticas**: Windows descarga de forma automática la versión más reciente en segundo plano en cuanto esté disponible, por lo que la versión siempre estará actualizada.
* **Descargas de menor tamaño**: Microsoft Store garantiza que solo los componentes que hayan cambiado en cada actualización se descargarán en el equipo, lo que reduce el tamaño de las descargas para cada actualización.
* **No se necesitan privilegios de administrador**: cuando se descarga y se instala directamente el paquete, debe ser administrador para completar la instalación de forma correcta. Si obtiene Power BI Desktop en Microsoft Store, *no* se necesitan privilegios de administrador.
* **Habilitado para lanzamiento de TI**: a través de Microsoft Store para Empresas, Power BI Desktop se puede implementar más fácilmente (o *lanzarse*) para todos los usuarios de la organización.

* **Detección de idioma**: en la versión de Microsoft Store se incluyen todos los idiomas admitidos y se comprueba el idioma que se usa en el equipo cada vez que se inicie. Esta compatibilidad de idioma también afecta a la localización de los modelos creados en Power BI Desktop. Por ejemplo, las jerarquías de fechas integradas coinciden con el idioma que use Power BI Desktop al crear el archivo .pbix.

La consideración y limitaciones siguientes se aplican al instalar Power BI Desktop desde Microsoft Store:

* Si usa el conector de SAP, puede que necesite mover los archivos del controlador de SAP a la carpeta *Windows\System32*.
* La instalación de Power BI Desktop desde Microsoft Store no copia la configuración de usuario de la versión .exe. Es posible que tenga que volver a conectarse con los orígenes de datos recientes y volver a escribir las credenciales de origen de datos. 

> [!NOTE]
> La versión de Power BI Report Server de Power BI Desktop es una instalación distinta e independiente de las versiones descritas en este artículo. Para más información sobre la versión de Report Server de Power BI Desktop, vea [Creación de un informe de Power BI para Power BI Report Server](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="download-power-bi-desktop-directly"></a>Descarga directa de Power BI Desktop
  
  Para descargar el archivo ejecutable de Power BI Desktop desde el Centro de descarga, seleccione **Descargar** en la [página del Centro de descarga](https://www.microsoft.com/download/details.aspx?id=58494). Después, especifique un archivo de instalación de 32 bits o 64 bits para descargar.

  ![Especificación del archivo de instalación de Power BI Desktop](media/desktop-get-the-desktop/download-desktop-exe.png)

### <a name="install-power-bi-desktop-after-downloading-it"></a>Instalación de Power BI Desktop después de descargarlo
Se le pedirá que ejecute el archivo de instalación una vez que haya terminado de descargarlo.

A partir de la versión de julio de 2019, Power BI Desktop se distribuye como un único paquete de instalación .exe que contiene todos los idiomas admitidos, con un archivo .exe independiente para las versiones de 32 y 64 bits. Los paquetes. msi se suspendieron a partir de la versión de septiembre de 2019, en la que se requiere el archivo .exe para la instalación. Este enfoque hace que la distribución, las actualizaciones y la instalación (especialmente para los administradores) sean mucho más fáciles y cómodas. También puede usar parámetros de línea de comandos para personalizar el proceso de instalación, como se describe en [Uso de opciones de línea de comandos durante la instalación](#using-command-line-options-during-installation).

Después de iniciar el paquete de instalación, Power BI Desktop se instala como una aplicación y se ejecuta en el escritorio.

![Ejecución de la instalación de Power BI Desktop](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> No se admite la instalación de la versión descargada (MSI) (en desuso) y la versión de Microsoft Store de Power BI Desktop en el mismo equipo (lo que a veces se denomina instalación *en paralelo*). Desinstale manualmente Power BI Desktop antes de descargarlo de Microsoft Store.
> 

## <a name="using-power-bi-desktop"></a>Uso de Power BI Desktop
Cuando inicie Power BI Desktop, se muestra una pantalla de bienvenida.

![Pantalla de bienvenida de Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Si usa Power BI Desktop por primera vez (es decir, la instalación no es una actualización), se le pedirá que rellene un formulario o que inicie sesión en el servicio Power BI para poder continuar.

En ella, puede comenzar a crear modelos de datos o informes y compartirlos después con otros usuarios en el servicio Power BI. Consulte la sección [Pasos siguientes](#next-steps) para obtener vínculos a guías que le ayudarán a empezar a usar Power BI Desktop.

## <a name="minimum-requirements"></a>Requisitos mínimos
En la lista siguiente, se proporcionan los requisitos mínimos para ejecutar Power BI Desktop:

* Windows 7 y Windows Server 2008 R2 o posterior
* .NET 4.5
* Internet Explorer 10 o posterior
* Memoria (RAM): Al menos 1 GB disponible; se recomienda 1,5 GB o más.
* Pantalla: se recomienda al menos 1440 x 900 o 1600 x 900 (16:9). No se recomiendan resoluciones inferiores a 1024x768 o 1280x800, ya que ciertos controles (por ejemplo, para cerrar la pantalla de inicio) solo se muestran en resoluciones superiores a estas.
* Configuración de la pantalla de Windows: si establece la configuración de pantalla para cambiar el tamaño del texto, las aplicaciones u otros elementos en más de 100 %, es posible que no vea algunos cuadros de diálogo con los que debe interactuar para seguir usando Power BI Desktop. Si se produce este problema, compruebe la configuración de la pantalla en **Configuración** > **Sistema** > **Pantalla** en Windows y use el control deslizante para devolver la configuración de pantalla al 100 %.
* CPU: se recomienda un procesador x86 de 32 o 64 bits de 1 gigahercio (GHz) o superior.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Nuestra intención es que su experiencia con Power BI Desktop sea magnífica. Como es posible que en ocasiones surja algún problema con Power BI Desktop, en esta sección se incluyen soluciones o sugerencias para solucionar esos problemas. 

### <a name="using-command-line-options-during-installation"></a>Uso de opciones de línea de comandos durante la instalación 

Al instalar Power BI Desktop, puede establecer propiedades y opciones con modificadores de la línea de comandos. Estas opciones son especialmente útiles para los administradores que administran o facilitan la instalación de Power BI Desktop entre organizaciones. Estas opciones se aplican a las instalaciones .msi y .exe. 


|Opción de línea de comandos  |Comportamiento  |
|---------|---------|
|-q, -quiet, -s, -silent     |Instalación silenciosa         |
|-passive     |Solo se muestra la barra de progreso durante la instalación         |
|-norestart     |Se suprime el requisito de reinicio del equipo         |
|-forcerestart     |Se reinicia el equipo después de la instalación sin preguntar         |
|-promptrestart     |Se pregunta al usuario si es necesario reiniciar el equipo (valor predeterminado)         |
|-l<>, -log<>     |Se registra la instalación en un archivo concreto, con el archivo especificado en <>         |
|-uninstall     |Se desinstala Power BI Desktop         |
|-repair     |Se repara la instalación (o se instala si no está instalada actualmente)         |
|-package, -update     |Se instala Power BI Desktop (valor predeterminado, siempre y cuando no se especifique -uninstall o -repair)         |

También puede usar los siguientes parámetros de sintaxis, que se especifican con una sintaxis *propiedad = valor*:

|Parámetro  |Significado  |
|---------|---------|
|ACCEPT_EULA     |Requiere un valor de 1 para aceptar automáticamente el CLUF.         |
|ENABLECXP     |Un valor de 1 realiza la inscripción en el programa de experiencia del usuario que captura la telemetría sobre el uso del producto.         |
|INSTALLDESKTOPSHORTCUT     |Un valor de 1 agrega un acceso directo al escritorio.         |
|INSTALLLOCATION     |Ruta de acceso al archivo de instalación.         |
|LANGUAGE     |El código de configuración regional (por ejemplo, en-US, de-DE, pr-BR) para forzar el idioma predeterminado de la aplicación. Si no se especifica el idioma, Power BI Desktop muestra el idioma del sistema operativo Windows. Puede cambiar esta configuración en el cuadro de diálogo **Opciones**.         |
|REG_SHOWLEADGENDIALOG     |Un valor de 0 deshabilita la presentación del cuadro de diálogo que aparece antes de haber iniciado sesión en Power BI Desktop.         |

Por ejemplo, puede ejecutar Power BI Desktop con las opciones y parámetros siguientes para realizar la instalación sin interfaz de usuario y con el idioma alemán: 

```-quiet LANG=de-DE ACCEPT_EULA=1```

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Instalación de Power BI Desktop en máquinas remotas

Si va a implementar Power BI Desktop para los usuarios con una herramienta que requiere un archivo de Windows Installer (archivo .msi), puede extraerlo del archivo .exe del instalador de Power BI Desktop. Use una herramienta de terceros, como el conjunto de herramientas de WiX.

> [!NOTE]
> Al ser un producto de terceros, las opciones del conjunto de herramientas de WiX podrían cambiar sin previo aviso. Consulte su documentación para obtener la información más actualizada y póngase en contacto con su lista de distribución de correo de usuarios si necesita ayuda.

1. En el equipo donde ha descargado el instalador de Power BI Desktop, instale la versión más reciente del [conjunto de herramientas de WiX](https://wixtoolset.org/).
2. Abra una ventana de línea de comandos como administrador y vaya a la carpeta donde haya instalado el conjunto de herramientas de WiX.
3. Ejecute el siguiente comando: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Por ejemplo:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

    La carpeta de salida contiene una carpeta denominada *AttachedContainer*, que incluye los archivos .msi.


### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problemas al usar versiones anteriores de Power BI Desktop

Es posible que algunos usuarios encuentren un mensaje de error similar al siguiente al usar una versión no actualizada de Power BI Desktop: 

*No se pudo restaurar la base de datos guardada en el modelo* 

Si se actualiza a la versión actual de Power BI Desktop, normalmente se soluciona este problema.

### <a name="disabling-notifications"></a>Deshabilitar las notificaciones
Se recomienda actualizar a la versión de Power BI Desktop más reciente para aprovechar los avances en las características, el rendimiento, la estabilidad y otras mejoras. Puede que algunas organizaciones no deseen que los usuarios actualicen a cada nueva versión. Puede deshabilitar las notificaciones modificando el registro con los pasos siguientes:

1. En el Editor del Registro, vaya a la clave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop**.
2. Cree un entrada **REG_DWORD** en la clave con el nombre siguiente: **DisableUpdateNotification**.
3. Establezca el valor de esa nueva entrada en **1**.
4. Reinicie el equipo para que el cambio surta efecto.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>Power BI Desktop se carga con una pantalla parcial

En determinadas circunstancias, incluidas determinadas configuraciones de resolución de pantalla, algunos usuarios pueden ver que Power BI Desktop representa el contenido con áreas negras extensas. Esta incidencia suele ser el resultado de las actualizaciones recientes del sistema operativo que afectan a cómo se representan los elementos, en lugar de un resultado directo de cómo Power BI Desktop presenta el contenido. Siga estos pasos para resolver la incidencia:

1. Presione la tecla **Inicio** y escriba *borrosa* en la barra de búsqueda que aparece.
2. En el cuadro de diálogo que aparece, seleccione la opción: **Corregir las aplicaciones que están borrosas.**
3. Reinicie Power BI Desktop.

Este problema se puede resolver tras la publicación de las actualizaciones de Windows posteriores. 
 

## <a name="next-steps"></a>Pasos siguientes
Una vez que haya instalado Power BI Desktop, vea el contenido siguiente a fin de obtener ayuda para ponerse en marcha rápidamente:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Información general sobre consultas en Power BI Desktop](desktop-query-overview.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Conectarse a los datos en Power BI Desktop](desktop-connect-to-data.md)
* [Combinar datos y darles forma en Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)   

