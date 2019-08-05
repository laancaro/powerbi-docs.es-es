---
title: Introducción a las pruebas unitarias
description: Cómo escribir pruebas unitarias para un proyecto de objetos visuales de Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 4b16eaad9b541bf6e5d8df49ffda99d9bbd5bbf2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424548"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>Tutorial: Adición de pruebas unitarias en proyectos de objetos visuales de Power BI

En este tutorial se describen los conceptos básicos de la escritura de pruebas unitarias para los objetos visuales de Power BI.

En este tutorial, tendremos en cuenta lo siguiente:

* Cómo usar karma.js de Test Runner, marco de pruebas: jasmine.js
* Cómo usar el paquete powerbi-visuals-utils-testutils
* Cómo ayuda el establecimiento de objetos ficticios y emulaciones a simplificar las pruebas unitarias de objetos visuales de Power BI

## <a name="prerequisites"></a>Requisitos previos

* Tener un proyecto de objetos visuales de Power BI
* Haber configurado el entorno de Node.JS

## <a name="install-and-configure-karmajs-and-jasmine"></a>Instalación y configuración de karma.js y Jasmine

Agregue las bibliotecas necesarias a package.json en la sección `devDependencies`:

```json
"@babel/polyfill": "^7.2.5",
"@types/d3": "5.5.0",
"@types/jasmine": "2.5.37",
"@types/jasmine-jquery": "1.5.28",
"@types/jquery": "2.0.41",
"@types/karma": "3.0.0",
"@types/lodash-es": "4.17.1",
"coveralls": "3.0.2",
"istanbul-instrumenter-loader": "^3.0.1",
"jasmine": "2.5.2",
"jasmine-core": "2.5.2",
"jasmine-jquery": "2.1.1",
"jquery": "3.1.1",
"karma": "3.1.1",
"karma-chrome-launcher": "2.2.0",
"karma-coverage": "1.1.2",
"karma-coverage-istanbul-reporter": "^2.0.4",
"karma-jasmine": "2.0.1",
"karma-junit-reporter": "^1.2.0",
"karma-sourcemap-loader": "^0.3.7",
"karma-typescript": "^3.0.13",
"karma-typescript-preprocessor": "0.4.0",
"karma-webpack": "3.0.5",
"puppeteer": "1.17.0",
"style-loader": "0.23.1",
"ts-loader": "5.3.0",
"ts-node": "7.0.1",
"tslint": "^5.12.0",
"webpack": "4.26.0"
```

Consulte la descripción siguiente para obtener más información sobre el paquete.

Guarde `package.json` y ejecútelo en la línea de comandos en la ubicación de `package.json`:

```cmd
npm install
```

El administrador de paquetes instalará todos los nuevos paquetes agregados a `package.json`

Para ejecutar pruebas unitarias, es necesario definir el archivo config de Test Runner y `webpack`. El ejemplo de config se encuentra aquí

Ejemplo de `test.webpack.config.js`:

```typescript
const path = require('path');
const webpack = require("webpack");

module.exports = {
    devtool: 'source-map',
    mode: 'development',
    optimization : {
        concatenateModules: false,
        minimize: false
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: /node_modules/
            },
            {
                test: /\.json$/,
                loader: 'json-loader'
            },
            {
                test: /\.tsx?$/i,
                enforce: 'post',
                include: /(src)/,
                exclude: /(node_modules|resources\/js\/vendor)/,
                loader: 'istanbul-instrumenter-loader',
                options: { esModules: true }
            },
            {
                test: /\.less$/,
                use: [
                    {
                        loader: 'style-loader'
                    },
                    {
                        loader: 'css-loader'
                    },
                    {
                        loader: 'less-loader',
                        options: {
                            paths: [path.resolve(__dirname, 'node_modules')]
                        }
                    }
                ]
            }
        ]
    },
    externals: {
        "powerbi-visuals-api": '{}'
    },
    resolve: {
        extensions: ['.tsx', '.ts', '.js', '.css']
    },
    output: {
        path: path.resolve(__dirname, ".tmp/test")
    },
    plugins: [
        new webpack.ProvidePlugin({
            'powerbi-visuals-api': null
        })
    ]
};
```

Ejemplo de `karma.conf.ts`:

```typescript
"use strict";

const webpackConfig = require("./test.webpack.config.js");
const tsconfig = require("./test.tsconfig.json");
const path = require("path");

const testRecursivePath = "test/visualTest.ts";
const srcOriginalRecursivePath = "src/**/*.ts";
const coverageFolder = "coverage";

process.env.CHROME_BIN = require("puppeteer").executablePath();

import { Config, ConfigOptions } from "karma";

module.exports = (config: Config) => {
    config.set(<ConfigOptions>{
        mode: "development",
        browserNoActivityTimeout: 100000,
        browsers: ["ChromeHeadless"], // or Chrome to use locally installed Chrome browser
        colors: true,
        frameworks: ["jasmine"],
        reporters: [
            "progress",
            "junit",
            "coverage-istanbul"
        ],
        junitReporter: {
            outputDir: path.join(__dirname, coverageFolder),
            outputFile: "TESTS-report.xml",
            useBrowserName: false
        },
        singleRun: true,
        plugins: [
            "karma-coverage",
            "karma-typescript",
            "karma-webpack",
            "karma-jasmine",
            "karma-sourcemap-loader",
            "karma-chrome-launcher",
            "karma-junit-reporter",
            "karma-coverage-istanbul-reporter"
        ],
        files: [
            "node_modules/jquery/dist/jquery.min.js",
            "node_modules/jasmine-jquery/lib/jasmine-jquery.js",
            {
                pattern: './capabilities.json',
                watched: false,
                served: true,
                included: false
            },
            testRecursivePath,
            {
                pattern: srcOriginalRecursivePath,
                included: false,
                served: true
            }
        ],
        preprocessors: {
            [testRecursivePath]: ["webpack", "coverage"]
        },
        typescriptPreprocessor: {
            options: tsconfig.compilerOptions
        },
        coverageIstanbulReporter: {
            reports: ["html", "lcovonly", "text-summary", "cobertura"],
            dir: path.join(__dirname, coverageFolder),
            'report-config': {
                html: {
                    subdir: 'html-report'
                }
            },
            combineBrowserReports: true,
            fixWebpackSourcePaths: true,
            verbose: false
        },
        coverageReporter: {
            dir: path.join(__dirname, coverageFolder),
            reporters: [
                // reporters not supporting the `file` property
                { type: 'html', subdir: 'html-report' },
                { type: 'lcov', subdir: 'lcov' },
                // reporters supporting the `file` property, use `subdir` to directly
                // output them in the `dir` directory
                { type: 'cobertura', subdir: '.', file: 'cobertura-coverage.xml' },
                { type: 'lcovonly', subdir: '.', file: 'report-lcovonly.txt' },
                { type: 'text-summary', subdir: '.', file: 'text-summary.txt' },
            ]
        },
        mime: {
            "text/x-typescript": ["ts", "tsx"]
        },
        webpack: webpackConfig,
        webpackMiddleware: {
            stats: "errors-only"
        }
    });
};
```

Puede modificar esta configuración si es necesario.

Algunos valores de `karma.conf.js`:

* La variable `recursivePathToTests` ubica el lugar del código de las pruebas.

* La variable `srcRecursivePath` ubica el código JS de salida después de la compilación.

* La variable `srcCssRecursivePath` ubica el CSS de salida después de compilar el archivo LESS con estilos.

* La variable `srcOriginalRecursivePath` ubica el código fuente del objeto visual.

* `coverageFolder`: variable que determina un lugar en el que se va a crear el informe de cobertura.

Algunas propiedades de config:

* `singleRun: true`: pruebas que se ejecutan en el sistema de CI. Y es suficiente para una sola vez.
Puede cambiar a `false` para depurar las pruebas. Karma mantendrá el explorador en ejecución y le permitirá usar la consola para la depuración.

* `files: [...]`: en esta matriz, puede establecer los archivos que se van a cargar en el explorador.
Normalmente, hay archivos de código fuente, casos de prueba, bibliotecas (Jasmine, utilidades de prueba). Puede agregar otros archivos a la lista si es necesario.

* `preprocessors`: en esta sección de config se definen las acciones que se ejecutan antes de la ejecución de pruebas unitarias. Hay precompilación de typescript para JS y preparación de archivos del mapa de origen y se genera el informe de cobertura de código. Puede deshabilitar `coverage` para depurar las pruebas. La cobertura genera código adicional para comprobar el código de la cobertura de la prueba y complicará las pruebas de depuración.

**Descripción de todas las configuraciones que puede encontrar en la [documentación](https://karma-runner.github.io/1.0/config/configuration-file.html) de karma.js**

Para un uso conveniente, puede agregar el comando de prueba a `scripts`:

```json
{
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "typings":"node node_modules/typings/dist/bin.js i",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "pretest": "pbiviz package --resources --no-minify --no-pbiviz --no-plugin",
        "test": "karma start"
    }
    ...
}
```

Por lo tanto, está listo para empezar a escribir las pruebas unitarias.

## <a name="simple-unit-test-for-check-dom-element-of-the-visual"></a>Prueba unitaria simple para comprobar el elemento DOM del objeto visual

Para probar el objeto visual, debemos crear una instancia de objeto visual.

### <a name="creating-visual-instance-builder"></a>Creación del generador de instancias de objeto visual

Agregue el archivo `visualBuilder.ts` a la carpeta `test` con el código siguiente:

```typescript
import {
    VisualBuilderBase
} from "powerbi-visuals-utils-testutils";

import {
    BarChart as VisualClass
} from "../src/visual";

import  powerbi from "powerbi-visuals-api";
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class BarChartBuilder extends VisualBuilderBase<VisualClass> {
    constructor(width: number, height: number) {
        super(width, height);
    }

    protected build(options: VisualConstructorOptions) {
        return new VisualClass(options);
    }

    public get mainElement() {
        return this.element.children("svg.barChart");
    }
}
```

Hay un método `build` para crear una instancia del objeto visual. `mainElement` es un método get, que devuelve una instancia del elemento DOM "root" del objeto visual. El captador es opcional, pero facilita la escritura de la prueba unitaria.

Por lo que tenemos el generador de una instancia de objeto visual. Vamos a escribir el caso de prueba. Será un caso de prueba para comprobar los elementos SVG que se crean al mostrar el objeto visual.

### <a name="creating-typescript-file-to-write-test-cases"></a>Creación de un archivo typescript para escribir casos de prueba

Agregue el archivo `visualTest.ts` para los casos de prueba con estos códigos:

```typescript
import powerbi from "powerbi-visuals-api";

import { BarChartBuilder } from "./VisualBuilder";

import {
    BarChart as VisualClass
} from "../src/visual";

import VisualBuilder = powerbi.extensibility.visual.test.BarChartBuilder;

describe("BarChart", () => {
    let visualBuilder: VisualBuilder;
    let dataView: DataView;

    beforeEach(() => {
        visualBuilder = new VisualBuilder(500, 500);
    });

    it("root DOM element is created", () => {
        expect(visualBuilder.mainElement).toBeInDOM();
    });
});
```

Hay llamadas de varios métodos.

* El método [`describe`](https://jasmine.github.io/api/2.6/global.html#describe) describe el caso de prueba. En un contexto de Jasmine Framework, a menudo se denomina conjunto o grupo de especificaciones.

* Se llamará al método `beforeEach` antes de cada llamada del método `it`, que se define dentro del método [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach).

* `it` define una especificación única. El método [`it`](https://jasmine.github.io/api/2.6/global.html#it) debe contener uno o varios `expectations`.

* [`expect`](https://jasmine.github.io/api/2.6/global.html#expect): método que crea una expectativa para una especificación. Una especificación se realizará correctamente si se superan todas las expectativas sin errores.

* `toBeInDOM`: es uno de los métodos de buscadores de coincidencias. En la [documentación](https://jasmine.github.io/api/2.6/matchers.html) de Jasmine Framework se puede leer sobre los buscadores de coincidencias existentes.

**Obtenga más información sobre Jasmine Framework en la [documentación](https://jasmine.github.io/) oficial.**

Después, puede ejecutar la prueba unitaria escribiendo un comando en la herramienta de línea de comandos.

Esta prueba comprueba que se ha creado el elemento SVG raíz de los objetos visuales.

### <a name="launch-unit-tests"></a>Inicio de pruebas unitarias

Para ejecutar la prueba unitaria, puede escribir este comando en la herramienta de línea de comandos.

```cmd
npm run test
```

`karma.js` ejecuta el explorador Chrome y ejecutará el caso de prueba.

![Inicio de KarmaJS en Chrome](./media/karmajs-chrome.png)

> [!NOTE]
> Google Chrome debe instalarse localmente.

En la línea de comandos, obtendrá el siguiente resultado:

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 12:24:30.850:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 12:24:31.059:INFO [launcher]: Starting browser Chrome
23 05 2017 12:24:33.160:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#2meR6hjXFmsE_fjiAAAA with id 5875251
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.194 secs / 0.011 secs)

=============================== Coverage summary ===============================
Statements   : 27.43% ( 65/237 )
Branches     : 19.84% ( 25/126 )
Functions    : 43.86% ( 25/57 )
Lines        : 20.85% ( 44/211 )
================================================================================
```

### <a name="how-to-add-static-data-for-unit-tests"></a>Cómo agregar datos estáticos para pruebas unitarias

Cree el archivo `visualData.ts` en la carpeta `test`. Con estos códigos:

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;

import {
    testDataViewBuilder,
    getRandomNumbers
} from "powerbi-visuals-utils-testutils";

export class SampleBarChartDataBuilder extends TestDataViewBuilder {
    public static CategoryColumn: string = "category";
    public static MeasureColumn: string = "measure";

    public constructor() {
        super();
        ...
    }

    public getDataView(columnNames?: string[]): DataView {
        let dateView: any = this.createCategoricalDataViewBuilder([
            ...
        ],
        [
            ...
        ], columnNames).build();

        // there's client side computed maxValue
        let maxLocal = 0;
        this.valuesMeasure.forEach((item) => {
                if (item > maxLocal) {
                    maxLocal = item;
                }
        });
        (<any>dataView).categorical.values[0].maxLocal = maxLocal;
    }
}
```

La clase `SampleBarChartDataBuilder` se amplía `TestDataViewBuilder` e implementa el método `getDataView`abstracto.

Al colocar datos en cubos de campos de datos, Power BI genera un objeto `dataview` categórico basado en los datos.

![Cubos de campos](./media/fields-buckets.png)

En las pruebas unitarias, no tiene funciones principales de Power BI para reproducirlo. Sin embargo, debe asignar los datos estáticos al objeto `dataview` categórico. Y la clase `TestDataViewBuilder` le ayudará en ello.

[Más información sobre DataViewMapping](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md)

En el método `getDataView`, solo tiene que llamar al método `createCategoricalDataViewBuilder` con los datos.

En `sampleBarChart` el archivo [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) del objeto visual, tenemos unos objetos dataRoles y dataViewMapping:

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": "Measure"
    }
],
"dataViewMappings": [
    {
        "conditions": [
            {
                "category": {
                    "max": 1
                },
                "measure": {
                    "max": 1
                }
            }
        ],
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "select": [
                    {
                        "bind": {
                            "to": "measure"
                        }
                    }
                ]
            }
        }
    }
],
```

Para generar la misma asignación, debe establecer los siguientes parámetros en el método `createCategoricalDataViewBuilder`:

```typescript
([
    {
        source: {
            displayName: "Category",
            queryName: SampleBarChartData.ColumnCategory,
            type: ValueType.fromDescriptor({ text: true }),
            roles: {
                Category: true
            },
        },
        values: this.valuesCategory
    }
],
[
    {
        source: {
            displayName: "Measure",
            isMeasure: true,
            queryName: SampleBarChartData.MeasureColumn,
            type: ValueType.fromDescriptor({ numeric: true }),
            roles: {
                Measure: true
            },
        },
        values: this.valuesMeasure
    },
], columnNames)
```

Donde `this.valuesCategory` es la matriz de categorías

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

y `this.valuesMeasure`, la matriz de medida para cada categoría. Ejemplo:

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

Ahora puede usar la clase `SampleBarChartDataBuilder` en la prueba unitaria.

La clase `ValueType` se define en el paquete `powerbi-visuals-utils-testutils`. Y el método `createCategoricalDataViewBuilder` requiere la biblioteca `lodash`.

Agregue estos paquetes a las dependencias.

En`package.json`, en la sección `devDependencies`

```json
"lodash-es": "4.17.1",
"powerbi-visuals-utils-testutils": "2.2.0"
```

Llamar a

```cmd
npm install
```

para instalar la biblioteca `lodash-es`.

Ahora puede volver a ejecutar la prueba unitaria. Debe obtener esta salida:

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 16:19:58.346:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 16:19:58.394:INFO [launcher]: Starting browser Chrome
23 05 2017 16:19:59.873:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#NcNTAGH9hWfGMCuEAAAA with id 3551106
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (1.266 secs / 1.052 secs)

=============================== Coverage summary ===============================
Statements   : 56.72% ( 135/238 )
Branches     : 32.54% ( 41/126 )
Functions    : 66.67% ( 38/57 )
Lines        : 52.83% ( 112/212 )
================================================================================
```

Además, debe ver el explorador Chrome iniciado con el objeto visual.

![La prueba unitaria se inicia en Chrome](./media/karmajs-chrome-ut-runned.png)

Aumente la atención en el resumen de la cobertura. Abra `coverage\index.html` para obtener más información sobre la cobertura de código actual

![Índice de cobertura de la prueba unitaria](./media/code-coverage-index.png)

O en el ámbito de la carpeta `src`

![Cobertura de la carpeta src](./media/code-coverage-src-folder.png)

En el ámbito del archivo, puede examinar el código fuente. Las utilidades `Coverage` marcarían el fondo de las filas en rojo si no se ejecutara un código durante la ejecución de pruebas unitarias.

![Convergencia de código del archivo visual.ts](./media/code-coverage-visual-src.png)

> [!IMPORTANT]
> Sin embargo, la cobertura de código no significa que tenga una buena cobertura de funcionalidad de objeto visual. Una prueba unitaria simple proporciona más del 96 % de la cobertura en `src\visual.ts`.

## <a name="next-steps"></a>Pasos siguientes

Cuando el objeto visual esté listo, puede enviarlo a publicación.

[Más información sobre la publicación de objetos visuales en AppSource](../office-store.md)
