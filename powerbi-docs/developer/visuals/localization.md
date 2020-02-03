---
title: Información sobre las asignaciones de vistas de datos en objetos visuales de Power BI
description: En este artículo se describe cómo transforma Power BI los datos antes de pasarlos en objetos visuales.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ad63a1b97c744e8614e584874c4d896a85598e48
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819132"
---
# <a name="add-the-locale-in-power-bi-for-custom-visuals"></a>Agregar la configuración regional en Power BI para los objetos visuales personalizados

Los objetos visuales pueden recuperar la configuración regional de Power BI para localizar su contenido en el idioma relevante.

Obtenga más información sobre los [idiomas y países o regiones admitidos para Power BI](./../../supported-languages-countries-regions.md)

Por ejemplo, para obtener la configuración regional en el objeto visual Gráfico de barras de ejemplo.

![Localización en el objeto visual Gráfico de barras de ejemplo](media/locale-in-samplebarchart.png)

Cada uno de estos gráficos de barras se ha creado con una configuración regional diferente (inglés, euskera e hindi) y se muestran en la información sobre herramientas.

> [!NOTE]
> El administrador de localización del código del objeto visual es compatible a partir de la API 1.10.0.

## <a name="get-the-locale"></a>Obtener la configuración regional

El `locale` se pasa como una cadena durante la inicialización del objeto visual. Si se cambia una configuración regional en Power BI, se volverá a generar el objeto visual con la configuración regional nueva. Encontrará el código de ejemplo completo en SampleBarChart con la configuración regional.

El constructor BarChart ahora tiene un miembro de configuración regional, del que se crean instancias en el constructor con la instancia de configuración regional de host.

```typescript
private locale: string;
...
this.locale = options.host.locale;
```

Configuraciones regionales admitidas:

Cadena de configuración regional | Idioma
--------------|----------------------
ar-SA | العربية (árabe)
bg-BG | български (búlgaro)
ca-ES | català (catalán)
cs-CZ | čeština (checo)
da-DK | dansk (danés)
de-DE | deutsch (alemán)
el-GR | ελληνικά (griego)
en-US | english (inglés)
es-ES | servicio español (español)
et-EE | eesti (estonio)
eU-ES | euskal (euskera)
fi-FI | suomi (finés)
fr-FR | français (francés)
gl-ES | galego (gallego)
he-IL | עברית (hebreo)
hi-IN | हिन्दी (hindi)
hr-HR | hrvatski (croata)
hu-HU | magyar (húngaro)
id-ID | Bahasa Indonesia (indonesio)
it-IT | italiano (italiano)
ja-JP | 日本の (japonés)
kk-KZ | Қазақ (kazajo)
ko-KR | 한국의 (coreano)
lt-LT | lietuvos (lituano)
lv-LV | Latvijas (letón)
ms-MY | bahasa melayu (malayo)
nb-NO | norsk (noruego)
nl-NL | nederlands (neerlandés)
pl-PL | polski (polaco)
pt-BR | português (portugués)
pt-PT | português (portugués)
ro-RO | românesc (rumano)
ru-RU | русский (ruso)
sk-SK | slovenský (eslovaco)
sl-SI | slovenski (esloveno)
sr-Cyrl-RS | српски (serbio)
sr-Latn-RS | srpski (serbio)
sv-SE | svenska (sueco)
th-TH | ไทย (tailandés)
tr-TR | Türk (turco)
uk-UA | український (ucraniano)
vi-VN | tiếng Việt (vietnamita)
zh-CN | 中国 (chino simplificado)
zh-TW | 中國 (chino tradicional)

> [!NOTE]
> En Power BI Desktop, la propiedad de configuración regional contendrá el idioma de Power BI Desktop instalado.

## <a name="localizing-the-property-pane-for-custom-visuals"></a>Localizar el panel de propiedades de los objetos visuales personalizados

Los campos del panel de propiedades se pueden localizar para ofrecer una experiencia más integrada y coherente. Hace que el objeto visual personalizado se comporte como cualquier otro objeto visual básico de Power BI.

Por ejemplo, un objeto visual personalizado no localizado que se haya creado con el comando `pbiviz new` mostrará los campos siguientes en el panel de propiedades:

![Localización en el panel de propiedades](media/property-pane.png)

Tanto los datos de categoría como los datos de medida se definen en el archivo capabilities.json como `displayName`.

## <a name="how-to-localize-capabilities"></a>Cómo localizar funcionalidades

En primer lugar, agregue una clave de nombre para mostrar a cada nombre para mostrar que desee localizar en las funcionalidades. En este ejemplo:

```json
{
    "dataRoles": [
        {
            "displayName": "Category Data",
            "displayNameKey": "VisualCategoryDataNameKey1",
            "name": "category",
            "kind": "Grouping"
        },
        {
            "displayName": "Measure Data",
            "displayNameKey": "VisualMeasureDataNameKey2",
            "name": "measure",
            "kind": "Measure"
        }
    ]
}
```

Después, agregue un directorio llamado stringResources. El directorio contendrá los distintos archivos de recursos de cadena en función de las configuraciones regionales que desee que admita el objeto visual. En este directorio deberá agregar un archivo JSON para cada configuración regional que quiera admitir. Estos archivos contienen la información de configuración regional y los valores de las cadenas localizadas para cada clave displayNameKey que desee reemplazar.

En nuestro ejemplo, supongamos que queremos admitir el árabe y el hebreo. Tendremos que agregar dos archivos JSON del siguiente modo:

![Cadenas de localización en la carpeta de recursos de cadenas](media/stringresources-files.png)

Cada archivo JSON define una configuración regional (este archivo tiene que ser una de las configuraciones regionales de la lista anterior), con los valores de cadena de las claves de nombres para mostrar que quiere. En nuestro ejemplo, el archivo de recursos de cadenas del hebreo tendrá el siguiente aspecto:

```json
{
    "locale": "he-IL",
    "values": {
        "VisualCategoryDataNameKey1": "קטגוריה",
        "VisualMeasureDataNameKey2": "יחידות מידה"
    }
}
```

A continuación se describen todos los pasos necesarios para usar el administrador de localización.

> [!NOTE]
> Actualmente, no se admite la localización para depurar el objeto visual de desarrollo

## <a name="setup-environment"></a>Entorno de configuración

### <a name="desktop"></a>Escritorio

Para el uso en el escritorio, descargue la versión localizada de Power BI Desktop en https://powerbi.microsoft.com.

### <a name="web-service"></a>Servicio web

Si usa el cliente web (explorador) en el servicio, cambie el idioma en la configuración:

![Localización en un servicio web](media/webservice-settings.png)

## <a name="resource-file"></a>Archivo de recursos

Agregue un archivo resources.resjson a una carpeta que tenga el nombre de la configuración regional que va a usar dentro de la carpeta stringResources. En nuestro ejemplo es en-US y ru-RU.

![El nuevo archivo resjson](media/new-resjson.png)

Después, agregue todas las cadenas de localización que va a usar en el archivo resources.resjson que ha agregado en el paso anterior.

```json
{
    ...
    "Role_Legend": "Обозначения",
    "Role_task": "Задача",
    "Role_StartDate": "Дата начала",
    "Role_Duration": "Длительность"
    ...
}
```

Este ejemplo es la versión en-US del archivo resources.resjson:

```json
{
    ...
    "Role_Legend": "Legend",
    "Role_task": "Task",
    "Role_StartDate": "Start date",
    "Role_Duration": "Duration"
    ...
}
```

Nueva instancia de localizationManager Cree una instancia de localizationManager en el código del objeto visual tal y como se indica a continuación.

```typescript
private localizationManager: ILocalizationManager;

constructor(options: VisualConstructorOptions) {
    this.localizationManager = options.host.createLocalizationManager();
}
```

## <a name="localizationmanager-usage-sample"></a>Ejemplo de uso de localizationManager

Ahora puede llamar a la función getDisplayName del administrador de localización con el argumento de clave de cadena que ha definido en resources.resjson para obtener la cadena necesaria en cualquier parte del código:

```typescript
let legend: string = this.localization.getDisplayName("Role_Legend");
```

Devuelve "Legend" para en-US y "обозначения" para ru-RU

## <a name="next-steps"></a>Pasos siguientes

* [Obtenga información sobre cómo usar las utilidades de formato para proporcionar formatos localizados](utils-formatting.md)
