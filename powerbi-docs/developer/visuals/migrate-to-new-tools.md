---
title: Migración a powerbi-visuals-tools versión 3.x
description: Introducción a la versión nueva de powerbi-visuals-tools
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818833"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migración a la nueva versión de powerbi-visuals-tools 3.*x*

A partir de la versión 3, las herramientas de objetos visuales de Power BI (powerbi-visuals-tools o `pbiviz`) usan webpack para crear objetos visuales personalizados.
La nueva versión ofrece a los desarrolladores muchas mejoras en la creación de objetos visuales:

- TypeScript 3.*x* se usa de forma predeterminada. A partir de TypeScript 1.5, se cambió la nomenclatura. [Más información sobre los módulos de TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

- Se admiten los módulos de ECMAScript 6 (ES6). Ahora puede usar las importaciones de ES6, en lugar de [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries).

- Se admiten las versiones nuevas de documentos controlados por datos ([D3v5](https://d3js.org/)) y otras bibliotecas basadas en módulos de ES6.

- Tamaño de paquete reducido. Webpack usa [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) para quitar el código no usado. Reduce el código JavaScript y ofrece un mejor rendimiento en la carga de objetos visuales.

- Mejor rendimiento de la API.

- La biblioteca Globalize.js [se integra](migrate-to-new-tools.md#remove-the- globalizejs-library) en FormattingUtils.

- Las herramientas de objetos visuales de Power BI usan [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) para mostrar el código base del objeto visual.

En este artículo se describen todos los pasos para la migración a la versión nueva de las herramientas de objetos visuales de Power BI.

## <a name="backward-compatibility"></a>Compatibilidad con versiones anteriores

Las herramientas nuevas guardan la compatibilidad con las versiones anteriores del código base de los objetos visuales anteriores, pero es posible que se requieran algunos cambios adicionales para cargar bibliotecas externas.

Las bibliotecas que admiten sistemas de módulos se importarán como módulos de webpack. El resto de las bibliotecas y el código fuente para el objeto visual se encapsulan en un módulo.

Las variables globales como JQuery y Lodash que se usaron en las herramientas de objetos visuales de Power BI anteriores ya están obsoletas. Si el código anterior para el objeto visual se basa en variables globales, es probable que este no funcione con las nuevas herramientas.

En la versión anterior de las herramientas de objetos visuales de Power BI era necesario definir una clase de objeto visual en el módulo `powerbi.extensibility.visual`. Con la nueva versión de las herramientas, en su lugar debe definir una clase de objeto visual en el archivo TypeScript (.ts) principal. Normalmente, ese archivo es `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>Instalación de powerbi-visuals-tools

Ejecute este comando para instalar las nuevas herramientas:

```cmd
npm install -g powerbi-visuals-tools
```

El código siguiente procede del archivo `package.json` en el [repositorio visual sampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15), una vez actualizado el proyecto de objeto visual para que funcione con las nuevas herramientas:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Instalación de la API de objetos visuales personalizados de Power BI

La versión nueva de powerbi-visual-tools no incluye todas las versiones de API. En su lugar, debe instalar una versión específica del paquete [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api). Elija la versión del paquete que coincida con la versión de API de los objetos visuales personalizados de Power BI. El paquete proporciona todas las definiciones de tipo para la API de objetos visuales personalizados de Power BI.

Agregue `powerbi-visuals-api` a las dependencias del proyecto de un proyecto mediante la ejecución de este comando:

```cmd
npm install --save-dev powerbi-visuals-api
```

Quite también los vínculos a las definiciones de tipo de API anteriores, ya que WebPack incluye automáticamente los tipos de `powerbi-visuals-api`. Los cambios correspondientes se encuentran en [package. json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) y [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>Actualización de tsconfig.json

Para usar módulos externos, cambie la opción `out` a `outDir`. Por ejemplo, use `"outDir": "./.tmp/build/",` en lugar de `"out": "./.tmp/build/visual.js",`.

Este cambio es necesario porque los archivos TypeScript se compilarán en archivos JavaScript por separado. Este es el motivo por el que ya no es necesario especificar el archivo visual.js como salida.

Además, puede cambiar la opción `target` a `ES6` si quiere usar JavaScript moderno como salida. Este cambio es [opcional](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Actualización de las utilidades de objetos visuales personalizados

Si usa uno de los paquetes de [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), también debe realizar la actualización a la versión más reciente. Para ello, ejecute este comando:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Por ejemplo, para obtener la versión nueva con módulos externos de TypeScript, ejecute: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Para obtener un ejemplo de un objeto visual que utiliza todos los paquetes de `powerbi-visuals-utils`, consulte el [repositorio de MekkoChart](https://github.com/Microsoft/powerbi-visuals-mekkochart).

## <a name="remove-the-globalizejs-library"></a>Eliminación de la biblioteca Globalize.js

La versión nueva de [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) incluye Globalize.js. No es necesario que incluya esta biblioteca de manera manual en el proyecto. Todas las localizaciones necesarias se agregarán automáticamente al paquete final.

## <a name="configure-loading-of-external-libraries"></a>Configuración de la carga de bibliotecas externas

Incluya nuevos archivos JavaScript después de las bibliotecas en la matriz `externalJS` de `pbiviz.json`. Por ejemplo:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importe las bibliotecas en el código fuente. Por ejemplo, use esta instrucción para `lodash-es`:

```JS
import * as _ from "lodash-es";
```

En el ejemplo anterior, `_` es la variable global de la biblioteca de `lodash`.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Realización de cambios en los orígenes de los objetos visuales

El cambio principal que debe realizar es convertir los módulos internos en externos. No se pueden usar módulos externos dentro de internos.

Esta es una descripción detallada de los cambios que se deben realizar. Las modificaciones se describen en el contexto de la muestra de código de objeto visual personalizado del gráfico de barras:

1. Quite todas las definiciones de módulos desde cada archivo del [código fuente](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3):

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importe las definiciones de la API de objetos visuales personalizados de Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importe las clases o interfaces necesarias](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) desde el módulo interno `powerbi`.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importe la biblioteca D3.js.](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    También puede importar solo los módulos necesarios de la biblioteca D3:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importe las utilidades, clases e interfaces que se definen en el proyecto de objeto visual](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) al archivo de origen principal:

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importación de estilos CSS

La versión nueva de las herramientas permite importar estilos `CSS` y `Less` directamente en el código TypeScript. El compilador omite ahora la [sección de estilos](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) que se usó anteriormente.

Para usar la hoja de estilo, abra el archivo TypeScript (.ts) principal y agregue la línea siguiente:  

```typescript
import "./../style/visual.less";
```  

Los estilos `CSS` y `Less` se compilarán automáticamente.

### <a name="externaljs-section-in-pbivizjson"></a>Sección externalJS en pbiviz.json

Las herramientas [no requieren una lista de bibliotecas de `externalJS`](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) que cargar en la agrupación de objetos visuales, ya que WebPack incluye todas las bibliotecas importadas.

> [!NOTE]
> En `pbiviz.json`, deje la sección `externalJS` vacía.

Use el comando `npm run package` habitual para crear el paquete de objetos visuales, o bien `npm run start` para iniciar el servidor de desarrollo.

## <a name="update-the-d3js-library-to-version-5"></a>Actualización de la biblioteca D3.js a la versión 5

Con las herramientas nuevas de objetos visuales, puede empezar a usar la versión nueva de la biblioteca D3.js. Ejecute estos comandos para actualizar D3 en el proyecto de objeto visual:

- `npm install --save d3@5` para instalar la biblioteca D3.js nueva.

- `npm install --save-dev @types/d3@5` para instalar las definiciones de tipo nuevas para D3.js.

> [!IMPORTANT]
> En la versión 5 de D3 se han presentado varios cambios importantes.

Modifique el código para que funcione con el nuevo D3.js:

- La interfaz `d3.Selection<T>` [se cambió](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) a `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- No es posible aplicar varios atributos con una sola llamada del método `attr`. En su lugar, debe [pasar cada atributo de una llamada independiente](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) a `attr`. Realice [llamadas independientes al método `style`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) también.

- La versión 4 de D3.js presentó el nuevo método `merge`. Este método se usa habitualmente para combinar las selecciones `enter` y `update` tras una operación de combinación de datos. Para usar D3 correctamente, [llame al método `merge`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[Obtenga más información](https://github.com/d3/d3/blob/master/CHANGES.md) sobre los cambios de la biblioteca D3.js.

## <a name="install-babel-and-core-js"></a>Instalación de Babel y core-js

A partir de la versión 3.1, las herramientas de objetos visuales usan Babel para compilar código JavaScript moderno en ECMAScript 5 (ES5) anterior para admitir una amplia variedad de exploradores.

La opción de Babel está habilitada de manera predeterminada, pero es necesario importar de manera manual el paquete [`core-js`](https://www.npmjs.com/package/core-js). Ejecute este comando para instalar el paquete:

```cmd
npm install --save core-js
```

Cuando termine, importe el paquete en el punto de inicio del código del objeto visual. Normalmente, se trata del archivo "src/visual.ts".

```JS
import "core-js/stable";
```

Más información sobre Babel [en la documentación](https://babeljs.io/docs/en/).
