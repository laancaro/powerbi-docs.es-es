---
title: 'Uso compartido de un panel vinculado a un archivo de Excel en OneDrive: Power BI'
description: Lea información sobre cómo compartir paneles conectados a un libro de Excel en OneDrive para la Empresa con iconos anclados desde ese libro.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 7157ddd66c651519f59eb964f5fcf95eb127943c
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721434"
---
# <a name="share-a-power-bi-dashboard-that-links-to-an-excel-file-in-onedrive"></a>Comparta un panel de Power BI que contiene vínculos a un archivo de Excel en OneDrive
En Power BI, puede [conectarse a libros de Excel en OneDrive para la Empresa](service-excel-workbook-files.md) y anclar iconos a un panel de ese libro. Cuando comparta ese panel o cree un paquete de contenido que lo incluya:

* Sus compañeros podrán ver los iconos sin necesidad de tener permisos para el propio libro. Por lo tanto, puede crear un paquete de contenido y saber que sus compañeros podrán ver los iconos creados desde el libro de Excel en OneDrive.
* Al hacer clic en el icono, se abre el libro en Power BI. El libro solo se abrirá si sus compañeros tienen como mínimo [permisos de lectura](https://support.office.com/article/Share-documents-or-folders-in-Office-365-1fe37332-0f9a-4719-970e-d2578da4941c) para el libro en OneDrive para la Empresa.

## <a name="share-a-dashboard-that-contains-workbook-tiles"></a>Compartir un panel que contiene iconos del libro
Para compartir un panel vinculado a un libro de Excel en OneDrive para la Empresa, consulte [Compartir un panel](service-share-dashboards.md). La diferencia es que tendrá la opción de modificar los permisos para el libro de Excel vinculado antes de compartirlo.

  ![Cuadro de diálogo Compartir panel](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_share_workbk.png)

1. Escriba las direcciones de correo electrónico de sus compañeros.
2. Para permitir que sus compañeros vean el libro de Excel de Power BI, seleccione **Ir a OneDrive para la Empresa para establecer permisos de libro**.
3. En OneDrive, [modifique los permisos](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) según sea necesario.
4. Seleccione **Compartir**.

>[!NOTE]
>Sus compañeros no podrán anclar los iconos adicionales de ese libro ni realizar cambios en el libro de Excel de Power BI.
> 
> 

## <a name="create-an-organizational-content-pack-with-a-dashboard-that-contains-workbook-tiles"></a>Crear un paquete de contenido organizativo con un panel que contiene iconos de libro
Cuando [publica un paquete de contenido](service-organizational-content-pack-create-and-publish.md), concede acceso a compañeros o grupos individuales. Cuando publique un paquete de contenido que contenga vínculos del libro, tendrá la opción de modificar los permisos para el libro de Excel vinculado antes de la publicación.

1. En la pantalla **Crear paquete de contenido** , escriba las direcciones de correo electrónico, asigne un título y una descripción al paquete de contenido y cargue una imagen.
2. Seleccione el panel o informe que esté vinculado al libro de Excel en OneDrive para la Empresa.
   
    ![Libro de Excel en un paquete de contenido](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_contpack_workbk.png)
3. Seleccione **Ir a OneDrive para la Empresa para establecer permisos de libro**.
4. En OneDrive, [modifique los permisos](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) según sea necesario.
5. Seleccione **Publicar**.

## <a name="share-a-dashboard-from-a-power-bi-workspace"></a>Compartir un panel de un área de trabajo de Power BI
El uso compartido de un panel de un área de trabajo de Power BI es similar al uso compartido de un panel de su propia área de trabajo, excepto en que los archivos se encuentran en un sitio de área de trabajo de Office 365, en lugar de su OneDrive para la Empresa privado. Modifique los permisos del libro de Excel antes de compartir el panel con personas de fuera del área de trabajo.

![Compartir desde OneDrive](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_onedriveshare.png)

## <a name="next-steps"></a>Pasos siguientes
* [Anclar un icono a un panel de Power BI desde Excel](service-dashboard-pin-tile-from-excel.md)
* [Conceptos básicos para los diseñadores en el servicio Power BI](service-basic-concepts.md)
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

