---
title: Estructura de proyecto de objeto visual de Power BI
description: En el artículo se describe una estructura de proyectos de objeto visual
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542102"
---
# <a name="power-bi-visual-project-structure"></a>Estructura de proyecto de objeto visual de Power BI

Después de ejecutar el nuevo `<visual project name>` de pbiviz, la herramienta crea una estructura básica de archivos y carpetas en la carpeta `<visual project name>`.

## <a name="visual-project-structure"></a>Estructura de proyecto de objeto visual

![Estructura de proyecto de objeto visual](./media/visual-project-structure.png)

* `.vscode`: contiene la configuración del proyecto para VS Code. Para configurar el área de trabajo, edite el archivo `.vscode/settings.json`. Obtenga más información [sobre la configuración de VS Code en la documentación](https://code.visualstudio.com/docs/getstarted/settings)

* La carpeta `assets` solo contiene el archivo `icon.png`. La herramienta usa este archivo como un icono del objeto visual en el panel Visualización de Power BI.

    ![El panel Visualizaciones](./media/visualization-pane-analytics-tab.png)

* La carpeta `node_modules` contiene todos los paquetes [instalados por el administrador de paquetes de Node](https://docs.npmjs.com/files/folders.html).

* La carpeta `src` contiene el código fuente del objeto visual. De forma predeterminada, la herramienta crea dos archivos:

  * `visual.ts`: el código fuente principal del objeto visual.

  * `settings.ts`: el código de configuración para el objeto visual. Las clases del archivo simplifican el [trabajo con las propiedades del objeto visual](./objects-properties.md#properties).

* La carpeta `style` contiene el archivo `visual.less` con estilos para el objeto visual.

* El archivo `capabilities.json` contiene las propiedades principales y la configuración del objeto visual. Permite que el objeto visual declare características admitidas, objetos, propiedades y asignación de vistas de datos.

    Obtenga más información [sobre las funciones en la documentación](./capabilities.md).

* `package-lock.json` se genera automáticamente para las operaciones en las que npm modifica el árbol `node_modules`, o bien `package.json`.

    Obtenga más información [sobre `package-lock.json` en la documentación oficial de NPM](https://docs.npmjs.com/files/package-lock.json).

* `package.json` describe el paquete del proyecto. Normalmente contiene información sobre el proyecto, sus autores, la descripción y las dependencias del proyecto.

    Obtenga más información [sobre `package.json` en la documentación oficial de NPM](https://docs.npmjs.com/files/package.json.html).

* `pbiviz.json` contiene los metadatos del objeto visual. En este archivo se especifican los metadatos del objeto visual.

    Contenido típico del archivo:

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    , donde

  * `name`: el nombre interno del objeto visual.

  * `displayName`: el nombre del objeto visual en la interfaz de usuario de Power BI.

  * `guid`: identificador único del objeto visual.

  * `visualClassName`: el nombre de la clase principal para el objeto visual. Power BI crea la instancia de esta clase para empezar a usar el objeto visual en informes de Power BI.

  * `version`: el número de versión del objeto visual.

  * `author`: contiene el nombre del autor y el correo electrónico de contacto.

  * `icon` en `assets`: ruta de acceso al archivo de icono para el objeto visual.

  * `externalJS` contiene las rutas de acceso de las bibliotecas de JS que se usan en el objeto visual.

    > [!IMPORTANT]
    > En la versión más reciente de la herramienta 3.x.x o superior ya no se usa `externalJS`.

  * `style` es la ruta de acceso a los archivos de estilo.

  * `capabilities` es la ruta de acceso al archivo `capabilities.json`.

  * `dependencies` es la ruta de acceso al archivo `dependencies.json`. `dependencies.json` contiene información sobre los paquetes de R que se usan en los objetos visuales basados en R.

  * `stringResources` es una matriz de rutas de acceso a archivos con localizaciones.

  Obtenga más información [sobre la localización en objetos visuales en la documentación](./localization.md)

* `tsconfig.json` es un archivo de configuración para TypeScript.

    Obtenga más información [sobre la configuración de TypeScript en la documentación oficial](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    `tsconfig.json` en la sección `files` debe contener la ruta de acceso al archivo *.ts donde se encuentra la clase principal del objeto visual especificado en la propiedad `visualClassName` del archivo `pbiviz.json`.

* El archivo `tslint.json` contiene la configuración de TSLint.

    Obtenga más información [sobre la configuración de TSLint en la documentación oficial](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>Pasos siguientes

* Obtenga más información [sobre el concepto de objeto visual](./power-bi-visuals-concept.md) para comprender mejor la interacción entre el objeto visual, el usuario y Power BI.

* Comience a desarrollar objetos visuales de Power BI propios desde cero [con la guía paso a paso](./custom-visual-develop-tutorial.md).
