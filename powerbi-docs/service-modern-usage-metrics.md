---
title: Supervisión de las métricas de uso en la nueva experiencia de área de trabajo
description: Cómo ver, guardar y usar métricas de uso en la nueva experiencia de área de trabajo para paneles e informes de Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/22/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: d3f359ad4c968407dff143458b65954844f9a22d
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76829291"
---
# <a name="monitor-usage-metrics-in-the-new-workspace-experience"></a>Supervisión de las métricas de uso en la nueva experiencia de área de trabajo

Conocer cómo se usa el contenido le ayuda a demostrar su impacto y a priorizar sus esfuerzos. Las métricas de uso pueden mostrarle que un segmento considerable de la organización utiliza a diario uno de sus informes y también que un panel que creó no lo está viendo nadie. Este tipo de comentario es muy valioso a la hora de dirigir los esfuerzos de trabajo que realiza.

Si crea informes en áreas de trabajo modernas, tiene acceso a informes de métricas de uso mejorados que le permiten descubrir cómo se usan esos informes en toda la organización y quién los usa. También puede identificar problemas de rendimiento de alto nivel. Los informes de uso mejorados de la experiencia de área de trabajo moderna reemplazan a los informes de métricas de uso existentes documentados en [Supervisar las métricas de uso de paneles e informes de Power BI](service-usage-metrics.md).

![Nuevo informe de métricas de uso](media/service-modern-usage-metrics/power-bi-modern-usage-metrics.png)

> [!NOTE]
> Solo se pueden ejecutar informes de métricas de uso en el servicio Power BI. Sin embargo, si guarda un informe de métricas de uso o lo ancla a un panel, puede abrirlo e interactuar con ese informe en dispositivos móviles.

## <a name="prerequisites"></a>Requisitos previos

- Para ejecutar los datos de métricas de uso y acceder a ellos se necesita una licencia de Power BI Pro. Sin embargo, la característica de métricas de uso permite capturar información de uso de todos los usuarios, sea cual sea la licencia que tengan asignada.
- Para acceder a las métricas de uso mejoradas de un informe, el informe debe residir en un área de trabajo moderna y se debe tener acceso de edición a ese informe.
- El administrador de Power BI debe tener habilitadas las métricas de uso para creadores de contenido. Asimismo, es posible que este también haya habilitado la recopilación de datos por usuario en dichas métricas. Obtenga información sobre cómo [habilitar estas opciones en el portal de administración](service-admin-portal.md#control-usage-metrics).

## <a name="create--view-an-improved-usage-metrics-report"></a>Creación y visualización de un informe de métricas de uso mejorado

Solo los usuarios con permisos de administrador, miembro o colaborador pueden ver el informe de métricas de uso mejorado. Los permisos de espectador no son suficientes. Si es al menos colaborador en un área de trabajo moderna en la que reside el informe, puede usar el siguiente procedimiento para mostrar las métricas de uso mejoradas:

1. Abra el área de trabajo que contiene el informe cuyas métricas de uso quiere analizar.
2. desde una de las listas de contenido del área de trabajo, abra el menú contextual del informe y seleccione **Ver informe de métricas de uso**. Como alternativa, abra el informe, abra el menú contextual en la barra de comandos y, luego, seleccione **Métricas de uso**.

    ![Selección de Métricas de uso](media/service-modern-usage-metrics/power-bi-modern-view-usage-metrics.png)

1. La primera vez que lo haga, Power BI creará el informe de métricas de uso y le informará cuando esté listo.

    ![El informe de métricas de uso está listo](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-ready.png)

1. Para ver los resultados, seleccione **Ver métricas de uso**.
2. Si es la primera vez que lo hace, Power BI podría abrir el informe de métricas de uso anterior. Para mostrar el informe de métricas de uso mejorado, en la esquina superior derecha, cambie el botón de alternancia de Nuevo informe de uso a **Activado**.

    ![Cambio al informe de métricas de uso moderno](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-on.png)

    > [!NOTE]
    > Solo puede ver el botón de alternancia de Nuevo informe de uso si el informe reside en un área de trabajo moderna. Las áreas de trabajo heredadas no ofrecen informes de métricas de uso mejorados.

## <a name="about-the-improved-usage-metrics-report"></a>Acerca del informe de métricas de uso mejorado

Cuando se muestra el informe de métricas de uso mejorado siguiendo el procedimiento anterior, Power BI genera un informe precompilado con métricas de uso para ese contenido durante los últimos 30 días. Este informe es muy similar a los informes de Power BI con los que ya está familiarizado. Podrá segmentarlo en función de cómo han obtenido acceso sus usuarios finales: si ha sido a través de la Web o de una aplicación móvil, etc. A medida que los informes evolucionan, evolucionará igualmente el informe de métricas de uso, que se actualiza a diario con nuevos datos.

> [!NOTE]
> Los informes de métricas de uso no aparecen en las listas de contenido Recientes, Áreas de trabajo, Favoritos ni en otras. Tampoco se pueden agregar a una aplicación. Si ancla un icono desde un informe de métricas de uso a un panel, dicho panel no se podrá agregar a una aplicación.

### <a name="usage-metrics-report-dataset"></a>Conjunto de datos del informe de métricas de uso

El informe de métricas de uso mejorado se basa en un conjunto de datos de informe de métricas de uso, que Power BI crea automáticamente la primera vez que se inicia el informe de métricas de uso mejorado. Luego, Power BI actualiza este conjunto de datos diariamente. Aunque no puede cambiar la programación de actualización, puede actualizar las credenciales que usa Power BI para actualizar los datos de métricas de uso. Esto puede ser necesario para reanudar la actualización programada si las credenciales expiraron o si quitó el usuario que inició primero el informe de métricas de uso desde el área de trabajo en la que reside el conjunto de datos.

### <a name="usage-metrics-report-pages"></a>Páginas del informe de métricas de uso

El informe de métricas de uso mejorado incluye las siguientes páginas:

- **Uso de informes**: proporciona información sobre las vistas de informes y las personas que los ven, como por ejemplo, cuántos usuarios vieron el informe por fecha.
- **Rendimiento del informe**: muestra los tiempos habituales de apertura del informe desglosados por método de consumo y tipo de explorador.
- **P+F**: proporciona respuestas a preguntas más frecuentes, como qué es un "espectador" y qué es una "vista".

### <a name="which-metrics-are-reported"></a>¿Qué métricas se incluyen en el informe?

| **Page** | **Métrica** | **Descripción** |
| --- | --- | --- |
| Uso de informes | Vistas de informes | Cada vez que alguien abre un informe, se registra una vista del informe. Tenga en cuenta que la definición de una vista difiere de los informes de métricas de uso anteriores. Cambiar las páginas del informe ya no se considera una vista adicional. |
| Uso de informes | Espectadores únicos | Un espectador es alguien que abrió el informe al menos una vez durante el período de tiempo (en función de la cuenta de usuario de AAD). |
| Uso de informes | Visualización de la tendencia | La tendencia de la vista refleja los cambios en el recuento de vistas con el tiempo. En ella se compara la primera mitad del período seleccionado con la segunda mitad. |
| Uso de informes | Segmentación de fecha | Puede cambiar el período en la página de uso del informe para calcular, por ejemplo, las tendencias de semana en semana o cada dos semanas. En la esquina inferior izquierda de la página de uso del informe, puede determinar la fecha más antigua y más reciente en que los datos de uso están disponibles para el informe seleccionado. |
| Uso de informes | Clasificación | Según el recuento de vistas, la clasificación muestra la popularidad de un informe en comparación con todos los demás informes de la organización.   |
| Uso de informes | Vistas de informe por día | Número total de vistas por día. |
| Uso de informes | Espectadores únicos por día | Número total de usuarios diferentes que han visto el informe (según la cuenta de usuario de AAD). |
| Uso de informes | Método de distribución | Cómo obtuvieron los usuarios acceso al informe, por ejemplo, por ser miembros de un área de trabajo, por tener el informe compartido con ellos o por instalar una aplicación. |
| Uso de informes | Segmentación de la plataforma | Si se ha tenido acceso al informe a través del servicio Power BI (powerbi.com), Power BI Embedded o un dispositivo móvil. |
| Uso de informes | Usuarios con vistas de informe | Muestra la lista de usuarios que abrieron el informe ordenada por el recuento de vistas. |
| Uso de informes | Páginas | Si el informe tiene más de una página, se segmenta el informe por las páginas que se han visto. Si ve una opción de lista de "En blanco", significa que recientemente se ha agregado una página del informe (en un plazo de 24 horas, aparece el nombre real de la nueva página en la lista de segmentación) o se han eliminado páginas del informe. "En blanco" captura estos tipos de situaciones. |
| Rendimiento de informe | Tiempo habitual de apertura | El tiempo habitual de apertura del informe se corresponde con el percentil 50 del tiempo que se tarda en abrir el informe. En otras palabras, es el tiempo por debajo del cual se han completado el 50 % de las acciones de apertura del informe. La página de rendimiento del informe también desglosa el tiempo habitual de apertura de un informe por método de consumo y tipo de explorador.   |
| Rendimiento de informe | Tendencia de tiempo de apertura | La tendencia del tiempo de apertura refleja los cambios en el rendimiento de apertura del informe con el tiempo. En ella se comparan los tiempos de apertura del informe de la primera mitad del período seleccionado con los tiempos de apertura de la segunda mitad. |
| Rendimiento de informe | Segmentación de fecha | Puede cambiar el período en la página de rendimiento del informe para calcular, por ejemplo, las tendencias de semana en semana o cada dos semanas. En la esquina inferior izquierda de la página de rendimiento del informe, puede determinar la fecha más antigua y más reciente en que los datos de uso están disponibles para el informe seleccionado. |
| Rendimiento de informe | Rendimiento diario | El rendimiento del 10 %, 50 % y 90 % de las acciones de apertura del informe calculado para cada día. |
| Rendimiento de informe | Rendimiento de 7 días | El rendimiento del 10 %, 50 % y 90 % de las acciones de apertura del informe calculado en los últimos 7 días para cada fecha. |
| Rendimiento de informe | Método de consumo | Cómo abrieron los usuarios el informe, por ejemplo, si lo hicieron a través del servicio Power BI (powerbi.com), Power BI Embedded o un dispositivo móvil. |
| Rendimiento de informe | Exploradores | Explorador que usan los usuarios para abrir el informe, como Firefox, Edge y Chrome. |

## <a name="update-usage-metrics-report-credentials"></a>Actualización de las credenciales de los informes de métricas de uso

Use el procedimiento siguiente para hacerse cargo de un conjunto de datos de informe de métricas de uso y actualizar las credenciales.

1. Abra el área de trabajo que contiene el informe para el que desea actualizar el conjunto de datos del informe de métricas de uso.
2. En la barra negra del encabezado de la parte superior, seleccione el icono de **Configuración** y, luego, seleccione **Configuración**.

    ![Selección de Configuración](media/service-modern-usage-metrics/power-bi-settings-settings.png)

3. Cambie a la pestaña **Conjuntos de datos**.

1. Seleccione el conjunto de datos de informe de métricas de uso. 

    ![Selección del conjuntos de datos de métricas de uso](media/service-modern-usage-metrics/power-bi-select-usage-metrics.png)
    
    Si no es el propietario actual del conjunto de datos, debe asumir la propiedad antes de poder actualizar las credenciales del origen de datos. 
    
5. Seleccione el botón **Tomar control** y, luego, en el cuadro de diálogo **Tomar el control de la configuración del conjunto de datos**, seleccione de nuevo **Tomar control**.

1. En **Credenciales del origen de datos**, seleccione **Editar credenciales**.

    ![Editar credenciales](media/service-modern-usage-metrics/power-bi-usage-metrics-edit-credentials.png)

2. En el cuadro de diálogo **Configure Usage Metrics Report** (Configurar informe de métricas de uso), seleccione **Iniciar sesión**.

    ![Selección de Iniciar sesión](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-configure.png)

1. Complete la secuencia de inicio de sesión y observe la notificación de que el origen de datos se actualizó correctamente.

    > [!NOTE]
    > El conjunto de datos de informe de métricas de uso contiene datos de uso de los últimos 30 días. Pueden transcurrir hasta 24 horas hasta que se importen nuevos datos de uso. No se puede desencadenar una actualización manual mediante la interfaz de usuario de Power BI.


## <a name="disable-usage-metrics-reports"></a>Deshabilitación de los informes de métricas de uso

Los informes de métricas de uso son una característica que el administrador de Power BI u Office 365 puede activar o desactivar. Los administradores tienen control granular sobre qué usuarios tienen acceso a las métricas de uso. Estas están activas de manera predeterminada para todos los usuarios de la organización. Consulte [Control de métricas de uso](service-admin-portal.md#control-usage-metrics) en el artículo del portal de administrador para obtener más información sobre estas opciones.

> [!NOTE]
> Solo los administradores del inquilino de Power BI pueden ver el portal de administración y editar la configuración.

## <a name="exclude-user-information-from-usage-metrics-reports"></a>Exclusión de información de usuario de los informes de métricas de uso

Los datos por usuario están habilitados de forma predeterminada en las métricas de uso, mientras que el informe de métricas incluye información sobre la cuenta del consumidor de contenido. Si los administradores no desean exponer esta información a algunos o todos los usuarios, pueden deshabilitar los datos por usuario en las métricas de uso para creadores de contenido en la configuración del inquilino del portal de administración de Power BI para grupos de seguridad especificados o toda la organización, con el fin de excluir información de usuario del informe de uso.

1. En la pestaña **Configuración de inquilinos** en el portal de administración, en **Configuración de auditoría y uso**, expanda **Datos por usuario en las métricas de uso para creadores de contenido** y seleccione **Deshabilitado**.

2. Decida si **Eliminar todos los datos por usuario existentes del contenido de las métricas de uso actuales** y seleccione **Aplicar**.

    ![Deshabilitación de las métricas por usuario](media/service-modern-usage-metrics/power-bi-admin-disable-per-user-metrics.png)

Si se excluye la información del usuario, el informe de uso hace referencia a los usuarios como Sin nombre.

Al deshabilitar las métricas de uso para toda la organización, los administradores pueden utilizar la opción Elimine todo el contenido existente de las métricas de uso para eliminar todos los iconos de informes y paneles existentes que se crearon mediante los informes de métricas de uso. Esta opción permite eliminar todos los accesos a los datos de métricas de uso de todos los usuarios de la organización que ya los puedan estar usando. La eliminación del contenido de las métricas de uso existentes es irreversible.

> [!NOTE]
> Solo los administradores del inquilino de Power BI pueden ver el portal de administración y configurar la opción de datos por usuario en métricas de uso para creadores de contenido.

## <a name="customize-the-usage-metrics-report"></a>Personalización del informe de métricas de uso

Para profundizar en los datos del informe, o para crear los suyos propios con el conjunto de datos subyacente, tiene varias opciones:

- **[Hacer una copia del informe](#create-a-copy-of-the-usage-report) en el servicio Power BI.**   Use **Guardar una copia** para crear una instancia independiente del informe de métricas de uso, que puede personalizar para satisfacer sus necesidades específicas.
- **[Conectarse al conjunto de datos](#create-a-new-usage-report-in-power-bi-desktop) con un nuevo informe.**   Para cada área de trabajo, el conjunto de datos tiene el nombre "Informe de métricas de uso", como se explicó anteriormente en la sección [Conjunto de datos del informe de métricas de uso](#usage-metrics-report-dataset). Puede usar Power BI Desktop para crear informes de métricas de uso personalizados según el conjunto de datos subyacente.
- **[Usar Analizar en Excel](#analyze-usage-data-in-excel).**   También puede aprovechar las funciones dinámicas, los gráficos y las características de segmentación de datos de Microsoft Excel 2010 SP1 o posterior para analizar los datos de uso de Power BI. Más información sobre la característica [Analizar en Excel](service-analyze-in-excel.md).

### <a name="create-a-copy-of-the-usage-report"></a>Creación de una copia del informe de uso

Cuando crea una copia del informe de uso precompilado de solo lectura, Power BI crea una instancia modificable de dicho informe. A primera vista, parece exactamente el mismo. Sin embargo, ahora podrá abrir el informe en la vista Edición; agregar nuevas visualizaciones, filtros y páginas; modificar o eliminar visualizaciones existentes, y mucho más. Power BI guarda el nuevo informe en el área de trabajo actual.

1. En el nuevo informe de métricas de uso, seleccione el menú **Más opciones** (...) y, luego, seleccione **Guardar una copia**.

    ![Guardado de una copia del informe](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-save.png)

2. En el cuadro de diálogo **Guardar el informe**, escriba un nombre y, luego, seleccione **Guardar**.

    Power BI crea un informe de Power BI editable, lo guarda en el área de trabajo actual y abre la copia del informe. 

3. Seleccione el menú **Más opciones** (...) y, luego, seleccione **Editar** para cambiar a la vista de edición. 

    Por ejemplo, puede cambiar filtros, agregar nuevas páginas, crear visualizaciones, dar formato a las fuentes y colores, etc.

1. El nuevo informe se guarda en la pestaña Informes del área de trabajo actual y se agrega también a la lista de contenido reciente.

    ![El nuevo informe en la pestaña Informes](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-new-report.png)

### <a name="create-a-new-usage-report-in-power-bi-desktop"></a>Creación de un informe de uso en Power BI Desktop

Puede crear un informe de uso en Power BI Desktop, según el conjunto de datos de informe de métricas de uso. Para establecer una conexión con el conjunto de datos de informe de métricas de uso y crear su propio informe, debe haber iniciado sesión en el servicio Power BI en Power BI Desktop. 

1. Abra Power BI Desktop.

2. Si no ha iniciado sesión en el servicio Power BI, en el menú **Archivo**, seleccione **Iniciar sesión**.

1. Para conectarse al conjunto de datos de informe de métricas de uso, en la cinta de opciones de **Inicio** seleccione **Obtener datos**.

4. En el panel izquierdo, seleccione **Power Platform** y, luego, seleccione **Conjuntos de datos de Power BI** > **Conectar**.

    ![Obtener datos > Power Platform](media/service-modern-usage-metrics/power-bi-desktop-get-data.png)

1. Desplácese hasta el conjunto de datos deseado o escriba *Informe de métricas de uso* en el cuadro de búsqueda. 

6. En la columna Área de trabajo, compruebe que selecciona el conjunto de datos correcto y, luego, seleccione **Crear**. 

    ![Selección del conjunto de datos de informe de métricas de uso](media/service-modern-usage-metrics/power-bi-desktop-select-usage-metrics.png)

7. Compruebe la lista Campos en Power BI Desktop, que le proporciona acceso a las tablas, columnas y medidas del conjunto de datos seleccionado.

    ![Visualización de la lista de campos del informe de métricas de uso](media/service-modern-usage-metrics/power-bi-desktop-fields-list.png)

1. Ahora puede crear y compartir informes de uso personalizados, todo ello desde el mismo conjunto de datos de informe de métricas de uso.

### <a name="analyze-usage-data-in-excel"></a>Análisis de los datos de uso en Excel

Al conectarse a los datos de uso en Excel, puede crear tablas dinámicas que utilicen las medidas predefinidas. Tenga en cuenta que las tablas dinámicas de Excel no admiten la agregación mediante arrastrar y colocar de campos numéricos al conectarse a un conjunto de datos de Power BI.

1. En primer lugar, si aún no lo ha hecho, [cree una copia del informe de métricas de uso](#create-a-copy-of-the-usage-report). 

2. Abra el nuevo informe de métricas de uso, seleccione el menú **Más opciones** (...) y seleccione **Analizar en Excel**.

    ![Analizar en Excel](media/service-modern-usage-metrics/power-bi-export-excel.png)

1. Si aparece el cuadro de diálogo **Para empezar, necesita algunas actualizaciones de Excel**, seleccione **Descargar** e instale las actualizaciones más recientes para la conectividad de Power BI o seleccione **Ya instalé estas actualizaciones**.

    ![Actualizaciones de Excel](media/service-modern-usage-metrics/power-bi-excel-updates.png)

    > [!NOTE]
    > Algunas organizaciones podrían tener reglas de directiva de grupo que impiden la instalación de las actualizaciones necesarias de Analizar en Excel en Excel. Si no puede instalar las actualizaciones, consulte con su administrador.

1. En el cuadro de diálogo del explorador que le pregunta qué desea hacer con el archivo report.odc de métricas de uso, seleccione **Abrir**.

    ![Apertura del archivo .odc](media/service-modern-usage-metrics/power-bi-open-odc-file.png)

1. Power BI inicia Excel. Compruebe el nombre de archivo y la ruta de acceso del archivo .odc y, luego, seleccione **Habilitar**.

    ![Aviso de seguridad de Excel](media/service-modern-usage-metrics/power-bi-excel-security-notice.png)

1. Ahora que Excel está abierto y tiene una tabla dinámica vacía, puede arrastrar campos a los cuadros de filas, columnas, filtros y valores y crear vistas personalizadas en los datos de uso.

    ![Tabla dinámica de Excel](media/service-modern-usage-metrics/power-bi-pivottable-excel.png)

## <a name="usage-metrics-in-national-clouds"></a>Métricas de uso en nubes nacionales

Power BI está disponible en nubes nacionales independientes. Estas nubes ofrecen los mismos niveles de seguridad, privacidad, cumplimiento y transparencia que la versión global de Power BI, junto con un modelo único para la normativa local sobre la entrega de servicios, la residencia de datos, el acceso y el control. Dado que se trata de un modelo único para las regulaciones locales, las métricas de uso no están disponibles en las nubes nacionales. Para obtener más información, consulte el tema relativo a las [nubes nacionales](https://powerbi.microsoft.com/clouds/).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Es importante comprender que se pueden producir diferencias al comparar el informe de métricas de uso mejorado con su predecesor. En particular, las métricas de uso del informe ahora se basan en los datos de actividad recopilados del servicio Power BI. Las versiones anteriores del informe de métricas de uso se basaban en la telemetría del cliente, que no siempre coincide con las métricas de uso recopiladas del servicio. Además, el informe de métricas de uso mejorado usa una definición diferente de lo que es una "vista". Una vista es un evento de apertura de informe, como se registra en el servicio cada vez que alguien abre un informe. Cambiar las páginas del informe ya no se considera una vista adicional.

> [!NOTE]
> Dado que el informe de métricas de uso mejorado se basa en los datos de actividad recopilados del servicio Power BI, las métricas de uso ahora coinciden con los recuentos agregados de actividades de los registros de auditoría y registros de actividad. El número de actividades por exceso o por detecto debido a conexiones de red incoherentes, bloqueadores de anuncios u otros problemas del lado cliente ya no se sesgan los recuentos de espectadores y vistas.

Además de las diferencias anteriores entre los informes de métricas de uso antiguos y mejorados, tenga en cuenta las siguientes limitaciones de la versión preliminar:

- Las métricas de uso del panel todavía se basan en la versión anterior de los informes de métricas de uso.
- Los informes de métricas de uso mejorados solo están disponibles para informes de áreas de trabajo modernas. Los informes de áreas de trabajo heredadas solo admiten la versión anterior de los informes de métricas de uso.
- Las métricas de rendimiento de los informes se basan en la telemetría del cliente. Algunos tipos de vistas no se incluyen en las medidas de rendimiento. Por ejemplo, cuando un usuario selecciona un vínculo a un informe en un mensaje de correo electrónico, la vista se contabiliza en el uso del informe, pero no hay ningún evento en las métricas de rendimiento.
- Las métricas de rendimiento del informe no están disponibles para informes paginados. En la pestaña Páginas de la página uso del informe, así como en los gráficos de la página de rendimiento del informe, no se muestran datos de estos tipos de informes.
- El enmascaramiento de usuario no funciona como se esperaba al usar grupos anidados. Si su organización ha deshabilitado los datos por usuario en métricas de uso para creadores de contenido en la configuración del inquilino del portal de administración, solo se enmascaran los miembros del nivel superior. Los miembros de los subgrupos siguen estando visibles.
- La inicialización del conjunto de datos de informe de métricas de uso puede tardar unos minutos, lo que hace que se muestre un informe de métricas de uso en blanco porque la interfaz de usuario de Power BI no espera a que termine la actualización. Compruebe el historial de actualización en la configuración del conjunto de datos de informe de métricas de uso para comprobar que la operación de actualización se realizó correctamente.
- La inicialización del conjunto de datos de informe de métricas de uso podría dar error debido a que se encontró que el tiempo de espera se había agotado durante la actualización. Consulte la sección de solución de problemas a continuación para resolver este problema.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

Además de las consideraciones y limitaciones anteriores, las siguientes preguntas y respuestas sobre las métricas de uso pueden ser útiles para los usuarios y los administradores:

**P:** No puedo ejecutar métricas de uso en un informe.

**R:** Solo puede ver métricas de uso de los informes de los que sea propietario o para los que tenga permisos de edición.

**P:** ¿Por qué no puedo ver el botón de conmutación activado del nuevo informe de uso en la esquina superior derecha del informe de métricas de uso existente?

**R:** El informe de métricas de uso mejorado solo está disponible para los informes de áreas de trabajo modernas.

**P:** ¿Qué período de tiempo incluye el informe?

**R:** El informe de uso se basa en los datos de actividad de los últimos 30 días, excluidas las actividades del día actual. Puede reducir el período de tiempo mediante la segmentación de datos de fecha de la página de uso del informe, por ejemplo, para analizar solo los datos de la semana pasada.

**P:** ¿Cuándo se ven los datos de actividad más recientes?

**R:** El informe de uso incluye los datos de actividad hasta el último día completado en función de la zona horaria UTC. Los datos que se muestran en el informe también dependen de la hora de actualización del conjunto de datos. Power BI actualiza el conjunto de datos una vez al día.

**P:** Los datos no parecen actualizados.

**R:** Tenga en cuenta que los nuevos datos de actividad pueden tardar hasta 24 horas en aparecer en el informe de uso.

**P:** ¿Cuál es el origen de datos de los datos de uso?

**R:** El conjunto de datos de informe de métricas de uso importa datos de un almacén interno de métricas de uso de Power BI mediante un conector de datos de métricas de uso personalizado. Puede actualizar las credenciales del conector de datos de métricas de uso en la página de configuración del conjunto de datos de informe de métricas de uso.

**P:** ¿Cómo puedo conectarme a los datos? ¿O cambiar el informe predeterminado?

**R:** Puede crear una copia del informe de uso previamente generado de solo lectura. La copia del informe se conecta al mismo conjunto de datos de informe de métricas de uso y permite editar los detalles del informe.

**P:** ¿Qué es un "espectador" y qué es una "vista"?

**R:** Un espectador es alguien que abrió el informe al menos una vez durante el período. Una vista es un evento de apertura de un informe. Cada vez que alguien abre un informe, se registra una vista del informe.

Tenga en cuenta que la definición de una vista difiere de los informes de métricas de uso anteriores. Cambiar las páginas del informe ya no se considera una vista adicional.

**P:** ¿Cómo se calcula la "tendencia de la vista"?

**R:** La tendencia de la vista refleja los cambios en el recuento de vistas con el tiempo. En ella se compara la primera mitad del período seleccionado con la segunda mitad. Puede cambiar el período mediante la segmentación de datos de fecha en la página de uso del informe para calcular, por ejemplo, las tendencias de semana en semana o cada dos semanas.

**P:** ¿Qué significa "distribución" y "plataforma"?

**R:** La distribución muestra cómo los espectadores obtuvieron acceso a un informe: compartido directamente, mediante el acceso al área de trabajo o por medio de una aplicación.

La plataforma indica la tecnología que usa un espectador para abrir un informe: a través de PowerBI.com, Mobile o Embedded.

**P:** ¿Cómo funciona la clasificación del informe?

**R:** Según el recuento de vistas, la clasificación muestra la popularidad de un informe en comparación con todos los demás informes de la organización.

**P:** ¿Quiénes son los "usuarios sin nombre"?

**R:** Su organización puede decidir excluir la información de usuario del informe de uso. Si se excluye, el informe de uso hace referencia a los usuarios como Sin nombre.

**P:** ¿Cuál es el "tiempo habitual de apertura del informe"?

**R:** El tiempo habitual de apertura del informe se corresponde con el percentil 50 del tiempo que se tarda en abrir el informe. En otras palabras, es el tiempo por debajo del cual se han completado el 50 % de las acciones de apertura del informe. La página de rendimiento del informe también desglosa el tiempo habitual de apertura de un informe por método de consumo y tipo de explorador.

**P:** ¿Cómo se calcula la "tendencia de hora de apertura?

**R:** La tendencia del tiempo de apertura refleja los cambios en el rendimiento de apertura del informe con el tiempo. En ella se comparan los tiempos de apertura del informe de la primera mitad del período seleccionado con los tiempos de apertura de la segunda mitad. Puede cambiar el período mediante la segmentación de datos de fecha en la página rendimiento del informe para calcular, por ejemplo, las tendencias de semana en semana o cada dos semanas.

**P:**  Hay cuatro informes en la versión anterior del informe de métricas de uso, pero la versión mejorada solo muestra tres.

**R:**  El informe de métricas de uso mejorado solo incluye los informes que se han abierto en los últimos 30 días, mientras que la versión anterior cubre los últimos 90 días. Si un informe no se incluye en el informe de métricas de uso mejorado, es probable que no se haya usado en más de 30 días.

## <a name="troubleshoot-delete-the-dataset"></a>Solución de problemas: Eliminación del conjunto de datos

Si sospecha de problemas de coherencia o de actualización de datos, puede que tenga sentido eliminar el conjunto de datos de informe de métricas de uso existente. Después, puede volver a ejecutar Ver métricas de uso para generar un nuevo conjunto de datos con sus informes de métricas de uso mejorados asociados. Siga estos pasos.

### <a name="delete-the-dataset"></a>Eliminación del conjunto de datos

1. Abra el área de trabajo que contiene el informe para el que desea restablecer el conjunto de datos de informe de métricas de uso.

2. En la barra negra del encabezado de la parte superior, seleccione el icono de **Configuración** y, luego, seleccione **Configuración**.

    ![Selección de Configuración](media/service-modern-usage-metrics/power-bi-settings-settings.png)

3. Cambie a la pestaña **Conjuntos de datos** y seleccione el conjunto de datos de informe de métricas de uso. 

    ![Conjunto de datos de métricas de uso](media/service-modern-usage-metrics/power-bi-settings-usage-report-dataset.png)

5. Copie los identificadores de área de trabajo y conjunto de datos de la dirección URL que se muestra en la barra de direcciones del explorador.

    ![Dirección URL del conjunto de datos de métricas de uso](media/service-modern-usage-metrics/power-bi-usage-metrics-url.png)

1. En el explorador, vaya a [https://docs.microsoft.com/rest/api/power-bi/datasets/deletedatasetingroup](https://docs.microsoft.com/rest/api/power-bi/datasets/deletedatasetingroup) y seleccione el botón **Probar**.

    ![Eliminación del conjunto de datos Probar](media/service-modern-usage-metrics/power-bi-delete-dataset-try-it.png)

1. Inicie sesión en Power BI, pegue el identificador del área de trabajo en el cuadro de texto **groupId** y el identificador del conjunto de datos en el cuadro de texto **datasetId** y, luego, seleccione **Ejecutar**. 

    ![Prueba de la API REST](media/service-modern-usage-metrics/power-bi-rest-api-try-it.png)

1. En el botón **Ejecutar**, compruebe que el servicio devuelve un código de respuesta de **200**. Ese código indica que el conjunto de datos y sus informes de métricas de uso asociados se han eliminado correctamente.

    ![Código de respuesta 200](media/service-modern-usage-metrics/power-bi-response-code-200.png)

### <a name="create-a-fresh-usage-metrics-report"></a>Creación de un informe de métricas de uso nuevo

1. De vuelta en el servicio Power BI, verá que el conjunto de datos ha desaparecido.

    ![Sin informe de métricas de uso](media/service-modern-usage-metrics/power-bi-no-usage-metrics-dataset.png)

2. Si sigue viendo el informe de métricas de uso en la lista de informes, actualice el explorador.

3. [Cree un informe de métricas de uso nuevo](#create--view-an-improved-usage-metrics-report).

## <a name="next-steps"></a>Pasos siguientes

[Administración de Power BI en el portal de administración](service-admin-portal.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
