---
title: Filtro de un informe con parámetros de cadena de consulta en la URL
description: Filtre un informe con parámetros de cadena de consulta de URL, con la posibilidad incluso de filtrar más de un campo.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/25/2019
LocalizationGroup: Reports
ms.openlocfilehash: 9e2b1132e48e824b70ddb0e0d86bfed4efedff2f
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68623890"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Filtro de un informe con parámetros de cadena de consulta en la URL

Al abrir un informe en el servicio Power BI, cada página del informe tiene su propia URL única. Para filtrar esa página del informe, podría utilizar el panel Filtros del lienzo de informes.  También podría agregar parámetros de cadena de consulta a la dirección URL para filtrar previamente el informe. Es posible que tenga un informe que quiera prefiltrarlo para mostrarlo a sus compañeros. Una manera de filtrar es comenzar con la dirección URL predeterminada del informe, agregarle los parámetros de filtro y luego enviar por correo electrónico la nueva dirección URL completa.

![Informe de Power BI en el servicio](media/service-url-filters/power-bi-report2.png)

## <a name="uses-for-query-string-parameters"></a>Usos de los parámetros de cadena de consulta

Supongamos que está trabajando en Power BI Desktop. Ahora quiere crear un informe con vínculos a otros informes de Power BI, pero solo quiere mostrar parte de la información de los otros informes. En primer lugar, filtre los informes con parámetros de cadena de consulta y guarde las direcciones URL. Luego, cree una tabla en Desktop con estas nuevas direcciones URL de informe.  Por último, publique y comparta el informe.

Otro uso de los parámetros de cadena de consulta es para un usuario que va a crear una solución avanzada de Power BI.  Con DAX, crea un informe que genera una dirección URL de informe filtrada que se basa de forma dinámica en la selección que hace su cliente en el informe actual. Cuando los clientes seleccionan la dirección URL, solo ven la información que esperan. 

## <a name="query-string-parameter-syntax-for-filtering"></a>Sintaxis de parámetro de cadena de consulta para filtrar

Con los parámetros, puede filtrar el informe por uno o varios valores, aunque esos valores contengan espacios o caracteres especiales. La sintaxis básica es bastante sencilla: empiece con la dirección URL del informe, agregue un signo de interrogación y luego incorpore la sintaxis de filtro.

URL?filter=***Tabla***/***Campo*** eq '***valor***'

![Dirección URL con filtro](media/service-url-filters/power-bi-filter-urls7b.png)

* Los nombres de **Tabla** y **Campo** distinguen mayúsculas de minúsculas, pero **valor** no.
* Todavía se pueden seguir filtrando los campos que están ocultos en la vista de informes.

### <a name="reports-in-apps"></a>Informes en aplicaciones

Si desea agregar un filtro de dirección URL a un informe en una aplicación, el formato es un poco diferente. Los vínculos a los informes de una aplicación tienen un parámetro de consulta (ctid) que se agrega a la dirección URL. Separe los parámetros de consulta con una Y comercial (&). Mantenga "?filter=" y mueva el parámetro ctid al final de la dirección URL, precedido por una Y comercial (&). 

Al igual que en este ejemplo:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=*Table*/*Field* eq "*value*&"ctid=*ctid*

### <a name="field-types"></a>Tipos de campos

El tipo de campo puede ser un valor de número, fecha y hora o cadena y el tipo usado debe coincidir con el tipo establecido en el conjunto de datos.  Por ejemplo, especificar una columna de tabla de tipo "cadena" no funciona si está buscando un valor de fecha y hora o número en una columna de conjunto de datos establecida como una fecha; por ejemplo, Table/StringColumn eq 1.

* Las **cadenas** deben incluirse entre comillas simple, como en 'nombre de administrador'.
* Los **números** no requieren ningún formato especial. Consulte [Tipos de datos numéricos](#numeric-data-types) en este artículo para obtener más información.
* **Fechas y horas**: consulte [Tipos de datos de fecha](#date-data-types) en este artículo. 

Si le sigue sin quedar claro, siga leyendo.  

## <a name="filter-on-a-field"></a>Filtrado por un campo

Supongamos que la URL del informe es la siguiente.

![Dirección URL de inicio](media/service-url-filters/power-bi-filter-urls6.png)

Y que tenemos almacenes en Carolina del Norte, tal como vemos en nuestra visualización de mapas (arriba).

>[!NOTE]
>Este artículo se basa en el ejemplo de [análisis de minoristas](sample-datasets.md).
> 

Para filtrar el informe para que solo muestre los datos de tiendas de "NC" (Carolina del Norte), anexe la URL con lo siguiente:

?filter=Tienda/Territorio eq 'NC'

![Dirección URL con filtro](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* es un valor almacenado en el campo **Territorio** de la tabla **Almacén**.
> 

El informe se filtra por North Carolina; todas las visualizaciones de la página del informe solo muestran datos de Carolina del Norte.

![Informe filtrado para Carolina del Norte](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-multiple-fields"></a>Filtrado por varios campos

También puede filtrar por varios campos agregando parámetros adicionales a la dirección URL. Volvamos a nuestro parámetro de filtro original.

```
?filter=Store/Territory eq 'NC'
```

Para filtrar por otros campos, agregue "**and**" y otro campo en el mismo formato que el mostrado arriba. Este es un ejemplo.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/0sDGKxOaC8w?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="operators"></a>Operadores

Power BI admite muchos operadores además de "**and**". En la tabla siguiente se indican esos operadores junto con el tipo de contenido que admiten.

|operador  | definición | cadena  | número | Fecha |  Ejemplo|
|---------|---------|---------|---------|---------|---------|
|**and**     | y |  sí      | sí |  sí|  product/price le 200 and price gt 3.5 |
|**eq**     | es igual a |  sí      | sí   |  sí       | Address/City eq 'Redmond' |
|**ne**     | no igual |   sí      | sí  | sí        |  Address/City ne 'London' |
|**ge**     |  mayor o igual       | no | sí |sí |  product/price ge 10
|**gt**     | mayor que        |no | sí | sí  | product/price gt 20
|**le**     |   menor o igual      | no | sí | sí  | product/price le 100
|**lt**     |  menor que       | no | sí | sí |  product/price lt 20
|**in\*\***     |  incluido       | sí | sí |  sí | Student/Age in (27, 29)


\*\* Al usar **in**, los valores a la derecha de **in** pueden ser una lista separada por comas entre paréntesis o una sola expresión que devuelve una colección.

### <a name="numeric-data-types"></a>Tipos de datos numéricos

Un filtro de dirección URL de Power BI puede incluir números en los siguientes formatos.

|Tipo de número  |Ejemplo  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5 L o 5 l      |
|**double**     |   5,5 o 55e-1 o 0,55e+1 o 5D o 5d o 0,5e1D o 0,5e1d o 5,5D o 5,5d o 55e-1D o 55e-1d     |
|**decimal**     |   5 M o 5 m o 5,5 M o 5,5 m      |
|**float**     | 5 F o 5 f o 0,5e1 F o 0,5e-1 d        |

### <a name="date-data-types"></a>Tipos de datos de fecha

Power BI admite OData V3 y V4 para tipos de datos **Date** y **DateTimeOffset**. Para OData V3, las fechas deben escribirse entre comillas simples e ir precedidas de la palabra datetime. Las comillas simples y la palabra datetime no son necesarias en OData V4. 
  
Las fechas se representan con el formato EDM (2019-02-12T00:00:00): cuando especifica una fecha como "AAAA-MM-DD", Power BI la interpreta como “AAAA-MM-DDT00:00:00". Asegúrese de que el mes y el día están compuestos por dos dígitos: MM y DD.

Por qué importa esta distinción Imagine que crea un parámetro de cadena de consulta **Table/Date gt "2018-08-03"** .  La duda es si los resultados incluyen el 3 de agosto de 2018 o empiezan con el 4 de agosto 2018. Power BI convierte la consulta a **Table/Date gt "2018-08-03T00:00:00"** . Por lo tanto, los resultados incluyen cualquier fecha que tenga una parte de hora que no sea cero, ya que esas fechas serían mayores que **"2018-08-03T00:00:00".**

Hay otras diferencias entre V3 y V4. OData V3 no admite fechas, solo DateTime. Por lo tanto, si usa el formato V3, debe calificarlo con la fecha y hora completas. Los literales de fecha como "datetime"2019-05-20"" no se admiten en la notación V3. Pero solo se puede escribirla como "2019-05-20" en la notación V4. A continuación se muestran dos consultas de filtro equivalentes en V3 y V4:

- Formato OData V4: filter=Table/Date gt 2019-05-20
- Formato OData V3: filter=Table/Date gt datetime'2019-05-20T00:00:00'


## <a name="special-characters-in-url-filters"></a>Caracteres especiales en filtros de URL

Los espacios y los caracteres especiales requieren algún formato adicional. Si la consulta contiene espacios, guiones u otros caracteres no ASCII, anteponga a esos caracteres especiales un *código de escape* que empiece por un carácter de subrayado y una X ( **_x**) y luego el carácter **Unicode** de cuatro dígitos seguido de otro carácter de subrayado. Si el carácter Unicode tiene menos de cuatro caracteres, debe rellenarlo con ceros. Estos son algunos ejemplos.

|Identificador  |Unicode  | Codificación para Power BI  |
|---------|---------|---------|
|**Nombre de tabla**     | El espacio es 0x20        |  Table_x0020_Name       |
|**Columna**@**Número**     |   @ es 0x40     |  Column_x0040_Number       |
|**[Columna]**     |  [ es 0x0058 y ] es 0x0050       |  _x0058_Column_x0050_       |
|**Columna+Más**     | + es 0x2B        |  Column_x002B_Plus       |

Table_x0020_Name/Column_x002B_Plus eq 3 ![objeto visual de tabla que representa caracteres especiales](media/service-url-filters/power-bi-special-characters1.png)


Table_x0020_Special/_x005B_Column_x0020_Brackets_x005D_ eq '[C]' ![objeto visual de tabla que representa caracteres especiales](media/service-url-filters/power-bi-special-characters2.png)

## <a name="use-dax-to-filter-on-multiple-values"></a>Usar DAX para filtrar por varios valores

Otra manera de filtrar por varios campos es crear una columna calculada que concatene dos campos a un único valor. Después, puede filtrar por ese valor.

Por ejemplo, tenemos dos campos: Territorio y Cadena. En Power BI Desktop, [cree una nueva columna calculada](desktop-tutorial-create-calculated-columns.md) (Campo) denominada "TerritoryChain". Recuerde que el nombre del **campo** no puede contener espacios. Esta es la fórmula DAX para esa columna.

TerritoryChain = [Territorio] & " - " & [Cadena]

Publique el informe en el servicio Power BI y, luego, use la cadena de consulta de URL para filtrar y mostrar los datos de solo las tiendas Lindseys de Carolina del Norte.

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC – Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>Anclaje de un icono desde un informe filtrado

Una vez que se ha filtrado el informe con parámetros de cadena de consulta, puede anclar visualizaciones de ese informe al panel.  El icono del panel muestra los datos filtrados y, si se selecciona ese icono del panel, se abre el informe que se usó para crearlo.  Sin embargo, el filtrado que se hizo con la dirección URL no se guarda con el informe. Cuando se selecciona el icono del panel, el informe se abre con el estado sin filtrar.  Por tanto, los datos mostrados en el icono del panel no coinciden con los datos mostrados en la visualización del informe.

Esta discrepancia resulta útil cuando se quieren ver resultados diferentes: filtrados en el panel y sin filtrar en el informe.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

Hay un par de cosas que tener en cuenta al utilizar los parámetros de cadena de consulta.

* Cuando se usa el operador *in*, los valores a la derecha de *in* deben ser una lista separada por comas entre paréntesis.    
* En Power BI Report Server, puede [pasar parámetros de informes](https://docs.microsoft.com/sql/reporting-services/pass-a-report-parameter-within-a-url?view=sql-server-2017.md) incluyéndolos en una URL de informe. Estos parámetros de URL no tienen prefijo porque se pasan directamente al motor de procesamiento de informes.
* El filtrado de cadenas de consulta no funciona con [Publicar en la web](service-publish-to-web.md) ni [Exportar a PDF](consumer/end-user-pdf.md).
* La [inserción de un elemento web de informes en SharePoint Online](service-embed-report-spo.md) no admite los filtros de direcciones URL.
* El tipo de datos long es (2^53-1) debido a las limitaciones de Javascript.
* Los filtros de dirección URL de informe tienen un límite de diez expresiones (diez filtros conectados mediante AND).

## <a name="next-steps"></a>Pasos siguientes

[Anclar una visualización a un informe](service-dashboard-pin-tile-from-report.md)  
[Registrarse para obtener una evaluación gratuita](https://powerbi.microsoft.com/get-started/)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](http://community.powerbi.com/)
