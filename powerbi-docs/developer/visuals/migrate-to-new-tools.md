---
title: Migración a powerbi-visuals-tools 3.x
description: Introducción a la versión nueva de powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cc554bff1cbd248ccd69a80ee47b60af981cdab1
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061831"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Migración a la versión nueva de powerbi-visuals-tools 3.x.x

A partir de la versión 3, las herramientas de objetos visuales de Power BI usan webpack para crear objetos visuales personalizados.
La versión nueva ofrece muchas oportunidades nuevas para que los desarrolladores creen objetos visuales:

* TypeScript v3.x.x de manera predeterminada. A partir de TypeScript 1.5, se cambió la nomenclatura. [Más información sobre los módulos de TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

* Se admiten los módulos de ES6. Ya no es necesario usar [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries); en cambio, use las importaciones de ES6.

* Se admiten las versiones nuevas de [D3v5](https://d3js.org/) y otras bibliotecas basadas en módulos de ES6.

* Tamaño de paquete reducido. Webpack use [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) para quitar el código no usado. Reduce el código de JS y, como resultado, se obtiene un mejor rendimiento en la carga de objetos visuales.

* Mejor rendimiento de la API.

* La biblioteca Globalize.js [se integra](migrate-to-new-tools.md#remove-globalizejs-library) en formatting-utils.

* Las herramientas usan [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) para mostrar el código base del objeto visual.

A continuación, se describen todos los pasos para la migración de la versión nueva de las herramientas de objetos visuales de Power BI.

## <a name="backward-compatibility"></a>Compatibilidad con versiones anteriores

Las herramientas nuevas guardan la compatibilidad con versiones anteriores del código base de los objetos visuales anteriores, pero es posible que se requieran algunos otros cambios para cargar bibliotecas externas.

Las bibliotecas, que admiten sistemas de módulos, se importarán como módulos de webpack. Todas las demás bibliotecas y el código fuente visual se ajustarán en un módulo.

Las variables globales como JQuery y Lodash que se usaron en las herramientas de pbiviz anteriores ya están obsoletas. Esto significa que si el código de objeto visual anterior se retransmite en variables globales, el objeto visual se puede dividir en este caso.

En la versión anterior de las herramientas de objetos visuales de Power BI era necesario definir una clase de objeto visual en el módulo `powerbi.extensibility.visual`.

## <a name="how-to-install-powerbi-visuals-tools"></a>Instalación de powerbi-visuals-tools

El conjunto de herramientas se puede instalar con la ejecución del comando.

```cmd
npm install -g powerbi-visuals-tools
```

El ejemplo del objeto visual sampleBarChart y los [cambios](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) correspondientes en `package.json`:

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Instalación de la API de objetos visuales personalizados de Power BI

La versión nueva de powerbi-visual-tools no incluye todas las versiones de API. En lugar de eso, el desarrollador debe instalar una versión específica del paquete [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api). La versión del paquete coincide con la versión de la API de los objetos visuales personalizados de Power BI y proporciona todas las definiciones de tipo de la API de objetos visuales personalizados de Power BI.

Para agregar `powerbi-visuals-api` a las dependencias del proyecto, ejecute el comando `npm install --save-dev powerbi-visuals-api`.
Y debe quitar el vínculo a definiciones de tipo de API anteriores. Porque los tipos de `powerbi-visuals-api` los incluye automáticamente webpack. Los cambios correspondientes están en [esta](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) línea de `package.json`.

## <a name="update-tsconfigjson"></a>Actualización de `tsconfig.json`

Para usar módulos externos, debe cambiar la opción `out` a `outDir`.
`"outDir": "./.tmp/build/",` en lugar de `"out": "./.tmp/build/visual.js",`.

Es necesario que los archivos de TypeScript se compilen en archivos de JavaScript por separado. Es por esto que ya no es necesario especificar el archivo visual.js como salida.

Además, también puede cambiar la opción `target` a `ES6` si quiere usar JavaScript moderno como salida. [Es opcional](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Actualización de las utilidades de objetos visuales personalizados

Si usa una de estas [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), también debe actualizarlas a la versión más reciente.

Ejecute el comando `npm install powerbi-visuals-utils-<UTILNAME> --save`. (Por ejemplo, `npm install powerbi-visuals-utils-dataviewutils --save`) para obtener la versión nueva con módulos externos de TypeScript.

Puede encontrar un ejemplo en el [repositorio](https://github.com/Microsoft/powerbi-visuals-mekkochart) de MekkoChart.
Este objeto visual usa todas las utilidades.

## <a name="remove-globalizejs-library"></a>Eliminación de la biblioteca Globalize.js

La versión nueva de [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) incluye globalize.js de manera inmediata.
No es necesario que incluya esta biblioteca de manera manual en el proyecto.
Todas las localizaciones necesarias se agregarán automáticamente al paquete final.

## <a name="fix-loading-external-libraries"></a>Corrección de la carga de bibliotecas externas

En cambio, incluya un archivo JS nuevo después de las bibliotecas en la matriz `externalJS` de `pbiviz.json`. Ejemplo:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importe las bibliotecas del origen. Ejemplo para `lodash-es`:

```JS
import * as _ from "lodash-es";
```

donde `_` es la variable global para la biblioteca `lodash`.

## <a name="changes-in-the-visuals-sources"></a>Cambios en los orígenes de objetos visuales

El cambio principal convierte módulos internos en módulos externos, porque no se pueden usar los módulos externos dentro de los módulos internos.

Esos cambios describen modificaciones que se han aplicado al gráfico de barras de ejemplo.

A continuación, se muestran las descripciones detalladas de los cambios:

1. Quite todas las definiciones de módulos desde cada archivo del [código fuente](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153).

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importe las definiciones de la API de objetos visuales personalizados de Power BI](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importe](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) las clases o interfaces necesarias desde el módulo interno `powerbi`.

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

4. [Importe](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) la biblioteca D3.js.

    ```typescript
    import * as d3 from "d3";
    ```

    O importe solo los módulos necesarios de la biblioteca d3.

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importe](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) las utilidades, clases e interfaces que se definen en el proyecto de objeto visual al archivo de origen principal.

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

La versión nueva de las herramientas permite que los desarrolladores importen estilo CSS, LESS directamente al código de TypeScript.

Por lo tanto, un compilador omitirá la [sección de estilos](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) anteriormente usados.

Para usar la hoja de estilo, abra el archivo .ts principal y agregue la línea siguiente:  

```typescript
import "./../style/visual.less";
```  

Los estilos CSS, LESS se compilarán automáticamente.  

### <a name="externaljs-section-in-pbivizjson"></a>Sección externalJS en pbiviz.json

Las herramientas [no requieren](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) una lista de `externalJS` para cargarse en el conjunto de objetos visuales, porque webpack incluye todas las bibliotecas importadas.

**La sección externalJS en pbivi.json debe estar vacía.**

Llame a los comandos `npm run package` típicos para crear el paquete de objetos visuales o `npm run start`, para iniciar el servidor de desarrollo.

## <a name="updating-d3js-library-to-version-5"></a>Actualización de la biblioteca D3.js a la versión 5

Con las herramientas nuevas, puede empezar a usar la versión nueva de la biblioteca D3.js.

Llamada a comandos para actualizar D3 en el proyecto de objeto visual

`npm install --save d3@5` para instalar la biblioteca D3.js nueva.

`npm install --save-dev @types/d3@5` para instalar las definiciones de tipo nuevas para D3.js.

Hay varios cambios importantes y es necesario modificar el código para usar la biblioteca D3.js nueva.

1. La interfaz `d3.Selection<T>` [se cambió](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) a `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

2. No es posible aplicar varios atributos con una sola llamada del método `attr`. [Debe pasar](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) cada atributo en una llamada distinta del método `attr`. También es [similar](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) para el método `style`.

3. En D3.js v4, se presenta el método de combinación nuevo. Este método se usa habitualmente para combinar las selecciones de entrada y actualización después de una combinación de datos. [Llame al método de combinación](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) para usar d3 correctamente.

[Más información](https://github.com/d3/d3/blob/master/CHANGES.md) sobre los cambios de la biblioteca D3.js.

## <a name="babel"></a>Babel

A partir de la versión 3.1, las herramientas usan Babel para compilar código JS moderno nuevo en ES5 anterior para admitir una amplia variedad de exploradores.

Esta opción está habilitada de manera predeterminada, pero es necesario importar de manera manual el paquete [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill).

Ejecute el comando para instalar el paquete

`npm install --save @babel/polyfill`

e importe el paquete en el punto de inicio del código de objeto visual (por lo general, es el archivo "src/visual.ts"):

`import "@babel/polyfill";`

Más información sobre Babel [en la documentación](https://babeljs.io/docs/en/).

Por último, ejecute [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) para mostrar el código base del objeto visual.  

![Estadísticas de código del objeto visual](./media/webpack-stats.png)
