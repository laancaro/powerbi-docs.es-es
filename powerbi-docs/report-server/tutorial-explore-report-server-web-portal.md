---
title: 'Tutorial: Exploración de Power BI Report Server en una máquina virtual'
description: En este tutorial, va a crear una máquina virtual con Power BI Report Server ya instalado y explorará también el portal web.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: tutorial
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 38985014407a4d64998e25f6944f57aedcc67309
ms.sourcegitcommit: aa8045e42b979206c600bce4a8d17de1f0620462
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34445012"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Tutorial: Exploración del portal web de Power BI Report Server en una máquina virtual
En este tutorial, creara una máquina virtual de Azure con Power BI Report Server ya instalado, para que pueda experimentar con la visualización, edición y administración de KPI e informes paginados y de Power BI de ejemplo.

![Portal web de Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

A continuación se indican las tareas que se realizarán en este tutorial:

> [!div class="checklist"]
> * Crear una máquina virtual y conectarse a ella
> * Iniciar y explorar en el portal web de Power BI Report Server
> * Etiquetar un elemento favorito
> * Ver y editar un informe de Power BI
> * Ver, administrar y editar un informe paginado
> * Ver un libro de Excel en Excel Online

Para este tutorial, necesita una suscripción a Azure. Si no tiene una suscripción, [cree una cuenta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de comenzar.

## <a name="create-a-power-bi-report-server-vm"></a>Creación de una máquina virtual de Power BI Report Server

Por suerte, el equipo de Power BI ha creado una máquina virtual que se incluye con Power BI Report Server ya instalado.

1. En Azure Marketplace, abra [Power BI Report Server](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview).  

2. Seleccione **Obtenerlo ahora**.
3. Para aceptar los términos de uso y la directiva de privacidad del proveedor, seleccione **Continuar**.

    ![Creación de una máquina virtual de Power BI Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-virtual-machine-create.png)

4. En el **Paso 1 Aspectos básicos**, en **Nombre de VM**, escriba **reportservervm**.

5. Cree un nombre de usuario y una contraseña.

6. En **Grupo de recursos**, mantenga **Crear nuevo** y escriba **reportserverresourcegroup**.

    Si realiza los pasos de este tutorial más de una vez, necesitará proporcionar al grupo de recursos un nombre diferente. No puede usar el mismo nombre de grupo de recursos dos veces en la misma suscripción. 

7. Mantenga los demás valores predeterminados > **Aceptar**.

    ![Asignación de nombre a la máquina virtual y al grupo de recursos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

8. En el **Paso 2 Configuración**, mantenga los valores predeterminados > **Aceptar**.

9. En el **Paso 3 Resumen** > **Aceptar**.

10. En el **Paso 4**, revise los términos de uso y la directiva de privacidad > **Crear**.

    El proceso de **envío de la implementación para Power BI Report Server** tarda varios minutos.

## <a name="connect-to-your-virtual-machine"></a>Conexión a la máquina virtual

1. En el panel de navegación izquierdo de Azure, seleccione **Máquinas virtuales**. 

2. En el cuadro **Filtrar por nombre**, escriba "report". 

3. Seleccione la máquina virtual denominada **REPORTSERVERVM**.

    ![Visualización de la máquina virtual](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. En la máquina virtual REPORTSERVERVM, seleccione **Conectar**.

    ![Conexión a la máquina virtual](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. En el cuadro de diálogo Conexión a Escritorio remoto, seleccione **Conectar**.

6. Escriba el nombre y la contraseña creados para la máquina virtual > **Aceptar**.

7. El siguiente cuadro de diálogo indica que no se puede identificar la identidad del equipo remoto. Seleccione **Sí**.

   Ya está, ahora se abrirá la nueva máquina virtual.

## <a name="power-bi-report-server-on-the-vm"></a>Power BI Report Server en la máquina virtual

Cuando se abre la máquina virtual, estos son los elementos que puede ver en el escritorio.

![Se inicia la máquina virtual de Power BI Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-start-vm-numbered.png)

|Número  |Qué significa  |
|---------|---------|
|![Número 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Inicia SQL Server Data Tools para crear informes paginados (.RDL) |
|![Número 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Ejemplo de informes de Power BI (.PBIX)  |
|![Número 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Vínculos a documentación de Power BI Report Server   |
|![Número 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Inicia Power BI Desktop optimizado para Power BI Report Server (marzo de 2018)  |
|![Número 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Abre el portal web de Power BI Report Server en el explorador   |

Haga doble clic en el icono del **portal web de Report Server**. El explorador abre http://localhost/reports/browse. En el portal web, verá varios archivos agrupados por tipo. 

![Portal web del servidor de informes de Power BI](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Número  |Qué significa  |
|---------|---------|
|![Número 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Se crean los KPI en el portal web |
|![Número 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Informes de Power BI (.PBIX)  |
|![Número 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Informes móviles creados en el Publicador de informes móviles de SQL Server  |
|![Número 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Informes paginados creados en el Generador de informes o en SQL Server Data Tools  |
|![Número 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Libros de Excel   | 
|![Número 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Orígenes de datos de informes paginados | 


## <a name="tag-your-favorites"></a>Etiquetado de favoritos
Puede etiquetar los informes y KPI que desee como favoritos. Son más fáciles de encontrar porque están recopilados en una única carpeta de Favoritos, en el portal web y en las aplicaciones móviles de Power BI. 

1. Seleccione los puntos suspensivos (**…**) en la esquina superior derecha del KPI **Margen de beneficio** > **Agregar a Favoritos**.
   
    ![Agregar a Favoritos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Seleccione **Favoritos** en la cinta de opciones del portal web para verlo junto con sus otros favoritos en la página Favoritos del portal web.
   
    ![Ver favoritos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Seleccione **Examinar** para volver al portal web.
   
## <a name="view-items-in-list-view"></a>Visualización de elementos en la vista de lista
De forma predeterminada, el portal web muestra su contenido en la vista de iconos.

Puede cambiar a la vista de lista, donde resulta fácil mover o eliminar varios elementos a la vez. 

1. Seleccione **Iconos** > **Lista**.
   
    ![Cambiar de vista](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Vuelva a la vista Iconos: seleccione **Lista** > **Iconos**.

## <a name="power-bi-reports"></a>Informes de Power BI

Puede visualizar informes de Power BI en el portal web e interactuar con ellos, así como iniciar Power BI Desktop directamente desde el portal web.

### <a name="view-power-bi-reports"></a>Visualización de informes de Power BI

1. En el portal web, en **Informes de Power BI**, seleccione **Informe de información general de cliente de ejemplo**. El informe se abre en el explorador.

1. Seleccione el bloque de Estados Unidos en el gráfico de rectángulos para ver cómo se resaltan los valores relacionados en los otros objetos visuales.

    ![Informe de Power BI resaltado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Edición en Power BI Desktop

1. Seleccione **Edición en Power BI Desktop**.

1. Seleccione **Permitir** para permitir que este sitio web abra un programa en el equipo. 

     El informe se abre en Power BI Desktop. Tenga en cuenta el nombre de la barra superior, "Power BI Desktop (marzo de 2018)". Se trata de la versión optimizada para Power BI Report Server.

    ![Power BI Desktop](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-desktop.png)

     Use la versión de Power BI Desktop instalada en la máquina virtual. No puede pasar entre dominios para cargar un informe.

3. En el panel Campos, expanda la tabla Clientes y arrastre el campo Ocupación a los filtros de nivel de informe.

    ![Arrastrar un campo al panel Filtros](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Guarde el informe.

1. Vuelva al informe en el explorador y seleccione el icono **Actualizar**.

    ![Icono de actualización del explorador](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Expanda el panel **Filtros** de la derecha para ver el filtro **Ocupación** agregado. Seleccione **Profesional**.

    ![Informe filtrado de Power BI](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Seleccione **Examinar** para volver al portal web.

## <a name="paginated-rdl-reports"></a>Informes paginados (.RDL)

Puede ver y administrar informes paginados e iniciar el Generador de informes desde el portal web.

### <a name="manage-a-paginated-report"></a>Administración de un informe paginado

1. En el portal web, en **Informes paginados**, seleccione los puntos suspensivos (...) que están al lado de **Pedido de venta** > **Administrar**.

1. Seleccione **Parámetros**, cambie el valor predeterminado de **SalesOrderNumber** por **SO50689** > **Aplicar**.

   ![Definición de los parámetros de informe](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Seleccione **Examinar** para volver al portal web.

### <a name="view-a-paginated-report"></a>Visualización de un informe paginado

1. Seleccione **Pedido de ventas** en el portal web.
 
3.  Podrá verlo abierto en el parámetro **Pedido** establecido, **SO50689**. 

    ![Parámetro de informe paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    Puede cambiar ese parámetro aquí, junto con otros parámetros, sin cambiar los valores predeterminados.

1. Seleccione **Pedido** **SO48339** > **Ver informe**.

4. Verá que se trata de la página 1 de 2. Seleccione la flecha derecha para ver la segunda página. La tabla continúa en esa página.

    ![Página 2 de 2 del informe paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Seleccione **Examinar** para volver al portal web.

### <a name="edit-a-paginated-report"></a>Edición de un informe paginado

Puede editar informes paginados en el Generador de informes, y puede iniciar el Generador de informes directamente desde el explorador.

1. En el portal web, seleccione el botón de puntos suspensivos (...) junto a **Pedido de ventas** > **Editar en el Generador de informes**.

1. Seleccione **Permitir** para permitir que este sitio web abra un programa en el equipo.

1. El informe de pedido de ventas se abre en la vista de diseño en el Generador de informes.

    ![Vista Diseño, informe paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Seleccione **Ejecutar** para obtener una vista previa del informe.

    ![Vista previa de un informe paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Cierre el Generador de informes y vuelva al explorador.

## <a name="view-excel-workbooks"></a>Edición de libros de Excel

Puede ver libros de Excel en Excel Online en Power BI Report Server e interactuar con ellos. 

1. Seleccione el libro de Excel **Office Liquidation Sale.xlsx**. Puede que se le soliciten credenciales. Seleccione **Cancelar**. 
    Se abre en el portal web.
1. Seleccione **Dispositivo** en la segmentación.

    ![Excel Online en el portal web](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Seleccione **Examinar** para volver al portal web.

## <a name="clean-up-resources"></a>Limpieza de recursos

Ahora que ya ha completado este tutorial, elimine el grupo de recursos, la máquina virtual y todos los recursos relacionados. 

- Para ello, seleccione el grupo de recursos de la máquina virtual y luego seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha creado una máquina virtual con Power BI Report Server. Ha probado parte de la funcionalidad del portal web y ha abierto un informe de Power BI y un informe paginado en sus editores correspondientes. Esta máquina virtual tiene instalados orígenes de datos de SQL Server Analysis Services, por lo que puede probar a crear sus propios informes paginados y de Power BI con los mismos orígenes de datos. 

Para más información sobre la creación de informes para Power BI Report Server, siga leyendo.

> [!div class="nextstepaction"]
> [Creación de un informe de Power BI para Power BI Report Server](./quickstart-create-powerbi-report.md)



