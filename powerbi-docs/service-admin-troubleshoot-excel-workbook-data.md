---
title: 'Error: Datos no encontrados en el libro de Excel'
description: 'Error: Datos no encontrados en el libro de Excel'
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 04/30/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1976567029454445f625ff400fb1d87ae6c01219
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "74698426"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Error: Datos no encontrados en el libro de Excel

>[!NOTE]  
>Este artículo es aplicable a Excel 2007 y versiones posteriores.

Al importar un libro de Excel en Power BI, es posible que vea el siguiente error:

*Error: No pudimos encontrar ningún dato con el formato de tabla. Para importar desde Excel en el servicio Power BI, debe aplicar a los datos el formato de tabla. Seleccione todos los datos que quiera de la tabla y presione Ctrl+T.*

![No se pudieron encontrar datos del libro](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

## <a name="quick-solution"></a>Solución rápida
1. Edite el libro en Excel.
2. Seleccione el rango de celdas que contienen los datos. La primera fila debe contener los encabezados de columna (los nombres de columna).
3. Presione **Ctrl + T** para crear una tabla.
4. Guarde el libro.
5. Regrese a Power BI y vuelva a importar el libro, o bien, si trabaja en Excel 2016 y guardó el libro en OneDrive para la Empresa, en Excel, haga clic en Archivo > Publicar.

## <a name="details"></a>Detalles
### <a name="cause"></a>Causa
En Excel se puede crear una **tabla** fuera de un rango de celdas, lo que facilita ordenar, filtrar y dar formato a datos.

Cuando se importa un libro de Excel, Power BI busca estas tablas y las importa en un conjunto de datos; si no encuentra ninguna tabla, mostrará este mensaje de error.

### <a name="solution"></a>Solución
1. Abra el libro en Excel. 
    >[!NOTE]
    >Las imágenes que aparecen aquí son de Excel 2013. Si usa otra versión, la apariencia puede ser levemente distinta, pero los pasos son los mismos.
    
    ![Abrir libro](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. Seleccione el rango de celdas que contienen los datos. La primera fila debe contener los encabezados de columna (los nombres de columna):
   
    ![Seleccionar rango de celdas](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. En la cinta de opciones, en la ficha **INSERTAR** , haga clic en **Tabla**. (O bien, como un método abreviado, presione **Ctrl + T**).
   
    ![Insertar tabla](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. Verá el siguiente cuadro de diálogo. Asegúrese de que la opción **La tabla tiene encabezados** esté activada y, a continuación, seleccione **Aceptar**:
   
    ![Crear tabla](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. Ahora los datos tienen el formato de una tabla:
   
    ![Datos con formato de tabla](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. Guarde el libro.
7. Regrese a Power BI. En la parte inferior del panel izquierdo, seleccione Obtener datos.
   
    ![Obtener datos](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. En el cuadro **Archivos** , seleccione **Obtener**.
   
    ![Obtención de archivos](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. Vuelva a importar el libro de Excel. Esta vez, la importación debe encontrar la tabla sin problemas.
   
    Si la importación sigue sin funcionar, háganoslo saber haciendo clic en **Comunidad** en el menú Ayuda:
   
    ![Vínculo de la comunidad](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)
