---
title: Registro de cambios del servidor de informes de Power BI
description: Este registro de cambios es para el servidor de informes de Power BI y enumera los elementos nuevos junto con las correcciones de errores de cada versión publicada.
ms.author: jaimeta
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.openlocfilehash: 71c2135092b0b9bb2b02f4559d40c0b10814a51f
ms.sourcegitcommit: e2c5d4561455c3a4806ace85defbc72e4d7573b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325725"
---
# <a name="changelog-for-power-bi-report-server"></a>Registro de cambios del servidor de informes de Power BI

Este registro de cambios es para el servidor de informes de Power BI y enumera los elementos nuevos junto con las correcciones de errores de cada versión publicada.

Para obtener información detallada sobre las nuevas características, consulte [Novedades en el servidor de informes de Power BI](whats-new.md). 

## <a name="september-2019"></a>Septiembre de 2019

- **Servidor de informes de Power BI**          
    - *Versión 1.6.7206.38019 (Compilación 15.0.1102.597), publicada el: 26 de septiembre de 2019*
        - Actualizaciones de seguridad
        - Correcciones de errores
           - Informes paginados
             - Corrección de incidencias de accesibilidad detectadas al usar Internet Explorer y Edge.
             - Corrección de incidencias de SAP HANA al probar la conexión.
             - Corrección de incidencias encontradas al proporcionar una lista de direcciones de correo electrónico.
             - Corrección de los informes de Power BI que usan un origen de datos de DirectQuery y la autenticación integrada.
             - Corrección de los informes paginados para que se representen con parámetros de filtro cuando la instantánea está habilitada.
             - Corrección de la ejecución doble de procedimientos almacenados durante la ejecución del informe.
             - Corrección de la cuenta de servicio predeterminada a la que se le conceden permisos de inicio de sesión de SQL Server cuando la cuenta de servicio personalizada está configurada para ejecutar Power BI Report Server.
             - Corrección de la obtención de acceso a los modelos que se actualizan en la zona horaria japonesa.
             - Corrección de los modelos obsoletos cuando se carga una nueva versión del informe durante la actualización.
             - Corrección de los valores de parámetro que contienen el carácter "&".
         - Programación
             - API web actualizada: /PowerBIReports({Id})/DataSources (PATCH) para permitir las actualizaciones de la cadena de conexión.
         
- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.73.5586.821 (septiembre de 2019), publicada: 26 de septiembre de 2019* (nueva compilación y versión)
    - Contiene los cambios necesarios para la conexión con Power BI Report Server (septiembre de 2019)


## <a name="may-2019"></a>Mayo de 2019

- **Servidor de informes de Power BI**          
    - *Versión 1.5.7074.36177 (compilación 15.0.1102.371), fecha de publicación: 21 de mayo de 2019*
        - Correcciones de errores
            - Informes paginados
                - Corrección para habilitar siempre la inserción de fuentes de PDF.
                - Corrección para establecer las cookies enviadas sobre HTTPS como seguras.
                - Corrección de incidencias con los elementos emergentes debido a errores de script.
                - Corrección de incidencias de visualización con la aplicación móvil en teléfonos con Android.
                - Corrección del navegador de tiempo del informe móvil para mostrar los números de semana correctos, independientemente del inicio del año fiscal.
                - Se ha agregado la propiedad configurable "RestrictedResourceMimeTypeForUpload" para que los administradores puedan especificar los tipos mime prohibidos.
         - Características
            - Se ha agregado compatibilidad con los objetos visuales de confianza a PBIRS.

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.69.5467.1801 (mayo de 2019), publicada el: 21 de mayo de 2019*
        - Correcciones de errores
            - Corrección para evitar la reentrada de credenciales durante la carga de PBIX a PBIRS.
            - Correcciones en la apertura de documentos con # en el nombre de archivo.
            - Se ha agregado un vínculo más sencillo para la navegación hacia atrás en la ventana de selección de PBIRS.
            - Corrección para el modo de Alto contraste en PBIRS para mostrar el botón Atrás, que muestra mensajes visuales de advertencia.
            - Correcciones de la interfaz de usuario en el panel de selección, escalado del lienzo.

    - *Versión: 2.69.5467.5201 (mayo de 2019), publicada el: 30 de julio de 2019*
        - Correcciones de errores
            - Corrección del registro de telemetría incorrecta

## <a name="january-2019"></a>Enero de 2019

- **Servidor de informes de Power BI**          
    - *Version 1.4.7024.16477 (Compilación 15.0.1102.299), publicada el: 28 de marzo de 2019*
        - Correcciones de errores
            - Informes de Power BI
                - Corrección del problema con las credenciales básicas al usar una consulta directa en SAP Hana y SAP BW
                - Error en la corrección de actualización de datos de fuente OData con "No se pudo cargar el archivo o ensamblado Microsoft.OData.Core.NetFX35.V7"

- **Servidor de informes de Power BI**            
    - *Versión 1.4.6969.7395 (compilación 15.0.1102.235), fecha de publicación: 30 de enero de 2019*
        - Correcciones de errores
            - Informes de Power BI
                - Corrección del problema con las credenciales básicas al usar una consulta directa
                - Corrección de las relaciones bidireccionales con los filtros de seguridad de nivel de fila aplicados
                - Corrección de datos obsoletos después de una actualización de modelo en un entorno de escalabilidad horizontal
                - Corrección de la barra de desplazamiento doble de tabla o matriz en Firefox 63 o posterior
                - Corrección del tamaño del icono de +/- de Internet Explorer
            - Informes paginados
                - Corrección del problema de actualización del uso de un origen de datos compartido de un informe

    - *Versión 1.4.6960.38798 (compilación 15.0.1102.222), fecha de publicación: 22 de enero de 2019*
        - Características
            - Informes de Power BI 
                - Compatibilidad con Seguridad de nivel de fila
                - Expandir y contraer encabezados de fila de matriz
                - Copiar y pegar entre archivos .pbix
                - Guías de alineación inteligente
                - Compatibilidad con el conector SAP BW 2.0
            - Administradores
                - Capacidad para definir qué extensiones de recursos se pueden cargar en el servidor de informes
                - Capacidad para restringir los esquemas de hipervínculos admitidos
            - Programación
                - Nueva API web: /PowerBIReports({Id})/DataModelRoles (GET)
                - Nueva API web: /PowerBIReports({Id})/DataModelRoleAssignments (GET y PUT)
                - Consulte el artículo sobre la [API de REST de Power BI Report Server](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) para obtener más detalles.
        - Correcciones de errores
            - Vulnerabilidad por inyección de HTML
            - Símbolo del Euro no visible al exportar a PDF
            - Guardar una contraseña con varios orígenes de datos en informes de Power BI invalida las contraseñas no modificadas.
            - Los objetos visuales muestran problemas en la aplicación de Power BI Mobile tras un tiempo de inactividad.

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.65.5313.1562 (enero de 2019), fecha de publicación: 30 de enero de 2019*
        - Los iconos de acceso directo y los anclados siguen estando después de desinstalar Power BI Report Server
        - Corrección para anclar Power BI Report Server en el menú de inicio proporcionando texto en negro sobre un icono negro

    - *Versión: 2.65.5313.1421 (enero de 2019), fecha de publicación: 22 de enero de 2019* (nueva compilación y nueva versión)
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (enero de 2019). 
    - *Versión: 2.65.5313.5141 (enero de 2019), fecha de publicación: 31 de julio de 2019* (nueva compilación y nueva versión)
        - Correcciones de errores
            - Corrección del registro de telemetría incorrecta

## <a name="august-2018"></a>Agosto de 2018

- **Servidor de informes de Power BI**
    - *Versión 1.3.6816.37243 (compilación 15.0.2.557), fecha de publicación: 30 de agosto de 2018*
        - Correcciones de errores
            - Se ha corregido un problema en el que el servidor se actualizaba desde versiones anteriores de PBI Report Server, pero no se actualizaba una redirección de enlace. Esto es lo que veían los clientes:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - El error de transferencia de la etiqueta de datos ya está corregido.
            
    - *Versión 1.3.6801.38816 (compilación 15.0.2.540), fecha de publicación: 15 de agosto de 2018*
        - Características
            - Compatibilidad de Direct Query de SSO de SAP HANA con Kerberos ya disponible para informes de Power BI
            - API de objeto visual personalizada incluida con la versión: versión 1.13.0
            - Los objetos visuales personalizados se revierten a una versión anterior compatible con la versión actual de la API de servidor (si está disponible)

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.61.5192.641 (agosto de 2018), fecha de publicación: 15 de agosto de 2018*
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (agosto de 2018)         
    - *Versión: 2.61.5192.7701 (agosto de 2018), fecha de publicación: 8 de agosto de 2019* (nueva compilación y versión)
        - Correcciones de errores
            - Corrección del registro de telemetría incorrecta
            
## <a name="march-2018"></a>Marzo de 2018

- **Servidor de informes de Power BI**
    - *Versión 1.2.6690.34729 (compilación 15.0.2.402), fecha de publicación: 27 de abril de 2018*
        - Correcciones de errores
            - Habilitar la migración de catálogos de SQL Server Reporting Services 2017
            - Para informes de Power BI (PBIX)
                - Los informes se pueden actualizar cuando un servidor está configurado para usar la autenticación personalizada
                - La modificación de las propiedades de un informe no restablece las credenciales del origen de datos
            - Para informes paginados (RDL)
                - El uso de `Lookup()` o de funciones derivadas, como `LookupSet()` y `MultiLookup()` en expresiones RDL ya no da como resultado `#Error`
                - Los informes vinculados respetan el tamaño de página del informe de destino al imprimir
                - Se pueden crear suscripciones para informes vinculados que usan parámetros en cascada
                - Los valores predeterminados de parámetros de varios valores pueden modificarse cuando se usa IE11
                - Se pueden editar las opciones de entrega de las suscripciones controladas por datos
                - Las suscripciones se pueden ver y editar mientras la suscripción se encuentra en ejecución
                - La definición de las credenciales del origen de datos no elimina las cadenas de conexión basadas en expresiones
            - Para los KPI
                - Las líneas de tendencia se actualizan cuando se actualizan los datos
            - Mejoras generales de la estabilidad

    - *Versión 1.2.6660.39920 (compilación 15.0.2.389), fecha de publicación: 28 de marzo de 2018*
        - Correcciones de errores
            - Para los informes de Power BI (PBIX), corrección para Exportar datos que no funcionan desde los objetos visuales de Power BI
            - Para los informes de Power BI (PBIX), corrección para los filtros de URL que no funcionan
            - Para los informes paginados (RDL), corrección para las imágenes que no se muestran correctamente en IE11 después de actualizar a la versión de marzo de Power BI Report Server

    - *Versión 1.2.6648.38132 (compilación 15.0.2.378), fecha de publicación: 19 de marzo de 2018*
        - Actualizaciones de seguridad
        - Mejoras de accesibilidad
        - Correcciones de errores
            - Para informes paginados (RDL), corrección de la visibilidad de los parámetros en un informe vinculado que se revierte después de editar sus propiedades
            - Corrección del portal web con autenticación de formularios personalizada que omite la cookie de expiración deslizante
            - Corrección para las exportaciones a Word que crean un alto de filas desigual si el contenido de la fila está vacío
            - Para informes paginados (RDL), corrección de la cadena de conexión basada en expresiones que se elimina cuando se cambia la credencial para el origen de datos
            - Corrección de la capacidad de usar KPI con valores de texto
            - Para informes paginados (RDL), corrección de la capacidad de asignar un nuevo conjunto de datos a un informe paginado existente (RDL)
            - Otras correcciones de estabilidad y facilidad de uso

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - Versión: 2.56.5023.1043 (marzo de 2018), fecha de publicación: 19 de marzo de 2018
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (marzo de 2018)

## <a name="october-2017"></a>Octubre de 2017

- **Servidor de informes de Power BI**
    - *Versión 1.1.6582.41691 (compilación 14.0.600.442), fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad
        - Correcciones de errores
            - Corrección del error que provocaba que GetParameters devolviese 400.
            - Corrección de la configuración de conjuntos de datos compartidos en informes paginados existentes (RDL).
            - Corrección de la excepción ExecutionNotFoundException al exportar informes con valores de parámetros distintos a PDF.

    - *Versión 1.1.6551.5155 (compilación 14.0.600.438), fecha de publicación: 11 de diciembre de 2017*
        - Correcciones de errores
            - Error al guardar los datos después de la actualización para determinados informes de Power BI Desktop.

    - *Versión 1.1.6530.30789 (compilación 14.0.600.437), fecha de publicación: 17 de noviembre de 2017*
        - Correcciones de errores
            - Corrección de los escenarios de autenticación básica 
            - Corrección del error por el que los días laborables no se podían seleccionar en la página de Suscripciones, Planes de actualización de caché e Instantáneas del historial en el Portal
            - En el caso de los informes paginados (RDL), corrección del error por el que, al tener expresiones en el cuadro de texto con la propiedad CanGrow establecida en false, los valores no muestran colores y las fuentes no son correctas
            - Para los informes de Power BI (PBIX), corrección del error por el que, al agregar leyendas al gráfico de líneas, se representa un objeto visual vacío

    - *Versión 1.1.6514.9163 (compilación 14.0.600.434), fecha de publicación: 1 de noviembre de 2017*
        - Correcciones de errores
            - Se han solucionado los problemas de confiabilidad de carga de los informes PBIX de más de 500 MB
            - Se ha corregido el problema de carga de datos de los informes PBIX de más de 1 GB

    - *Versión 1.1.6513.3500 (compilación 14.0.600.433), fecha de publicación: 31 de octubre de 2017*
        - Características
            - Compatibilidad con el modelo de datos insertados
            - Visualización de libros de Excel (con la integración de Office Online Server habilitada)
            - Actualización de datos programada (PBIX)
            - Compatibilidad con Direct Query
            - Compatibilidad con archivos de gran tamaño (hasta 2 GB)
            - API de REST pública
            - Compatibilidad con conjuntos de datos compartidos en Power BI Desktop (a través de oData)
            - Compatibilidad con parámetros de dirección URL para archivos PBIX
            - Mejoras de accesibilidad

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.51.4885.3981 (octubre de 2017), fecha de publicación: 10 de abril de 2018*
        - Actualizaciones de seguridad

    - *Versión: 2.51.4885.2501 (octubre de 2017), fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad

    - *Versión: 2.51.4885.1423 (octubre de 2017), fecha de publicación: 17 de noviembre de 2017*
        - Correcciones de errores
            - Corrección del error por el que Power BI Desktop de 32 bits no se puede ejecutar en sistemas operativos x86
            - Para los informes de Power BI (PBIX), corrección para mostrar las líneas de cuadrícula del eje X
            - Otras correcciones de errores menores

    - *Versión: 2.51.4885.1041 (octubre de 2017), fecha de publicación: 31 de octubre de 2017*
        - Características
            - Contiene los cambios necesarios para la conexión con Power BI Report Server (octubre de 2017)

## <a name="june-2017"></a>Junio de 2017

- **Servidor de informes de Power BI**
    - *Compilación 14.0.600.309, fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad

    - *Compilación 14.0.600.305, fecha de publicación: 19 de septiembre de 2017*  
        - Correcciones de errores
            - Actualización a la versión más reciente del [control Web de mapas de Bing](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Compilación 14.0.600.301, fecha de publicación: 11 de julio de 2017*
        - Correcciones de errores
            - La etiqueta `{{UserId}}` se resuelve en las credenciales almacenadas en lugar de ser el usuario el que ejecute el informe en los informes de Power BI
            - Algunas imágenes no se pueden representar en los informes del servidor de informes de Power BI
            - No se puede cambiar el nombre de un informe de Power BI en el servidor de informes de Power BI
            - No se pueden cargar los objetos visuales personalizados en la aplicación móvil de Power BI (es necesario volver a instalar la aplicación móvil para borrar la memoria caché local)

    - *Compilación 14.0.600.271, fecha de publicación: 12 de junio de 2017*
        - Versión inicial del servidor de informes de Power BI

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.47.4766.4901 (junio de 2017), fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad

## <a name="next-steps"></a>Pasos siguientes

[¿Qué es Power BI Report Server?](get-started.md)
[Información general de administrador](admin-handbook-overview.md)  
[Instalar un servidor de informes de Power BI](install-report-server.md)  
[Descarga del Generador de informes](https://www.microsoft.com/download/details.aspx?id=53613)  
[Descargar SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
