---
title: Títulos basadas en expresiones en Power BI Desktop
description: Creación de títulos dinámicos en Power BI Desktop que cambian en función de expresiones mediante programación, utilizando el formato condicional mediante programación
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769741"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Títulos basadas en expresiones en Power BI Desktop

Puede crear dinámico, personalizar títulos para los objetos visuales de Power BI. Mediante la creación de expresiones de análisis de datos (DAX) en función de los campos, variables u otros elementos mediante programación, pueden ajustar automáticamente los títulos de los objetos visuales según sea necesario. Estos cambios se basan en filtros, las selecciones, u otras interacciones del usuario y las configuraciones.

![Opción de formato condicional de captura de pantalla de Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Creación dinámicos títulos, a veces denominado *basadas en expresiones títulos*, es sencillo. 

## <a name="create-a-field-for-your-title"></a>Crear un campo para el título

El primer paso para crear un título de la expresión es crear un campo en el modelo que se usará para el título. 

Hay todo tipo de forma creativa para que el título de visual refleje lo que desea que diga o desea express. Echemos un vistazo a un par de ejemplos.

Puede crear una expresión que cambie en función del contexto de filtro que recibe el objeto visual para el nombre de la marca del producto. La siguiente imagen muestra la fórmula DAX para este tipo de campo.

![Captura de pantalla de fórmula](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Otro ejemplo es usar un título dinámico que cambia en función de lenguaje o la referencia cultural del usuario. Puede crear los títulos específicos del idioma en una medida DAX mediante la `USERCULTURE()` función. Esta función devuelve el código de la referencia cultural del usuario, según el sistema operativo o la configuración del explorador. Puede usar la siguiente instrucción switch DAX para seleccionar el valor traducido correcto. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

O bien, puede recuperar la cadena de una tabla de búsqueda que contiene todas las traducciones. Coloque esa tabla en el modelo. 

Se trata de un par de ejemplos que puede utilizar para crear títulos dinámicos, basadas en expresiones para los objetos visuales en Power BI Desktop. Lo que puede hacer con los títulos están limitados solo por su imaginación y el modelo.


## <a name="select-your-field-for-your-title"></a>Seleccione el campo del título

Después de crear la expresión DAX para el campo que se crea en el modelo, deberá aplicarla al título del objeto visual.

Para seleccionar el campo y aplicarlo, vaya a la **visualizaciones** panel. En el **formato** área, seleccione **título** para mostrar las opciones de título para el objeto visual. 

Cuando haga clic en **texto de título**, aparece un menú contextual que le permite seleccionar ***fx* formato condicional**. Cuando se selecciona ese elemento de menú, un **texto de título** aparece el cuadro de diálogo. 

![Captura de pantalla de título cuadro de diálogo de texto](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Desde esa ventana, puede seleccionar el campo que ha creado para que utilice para el título.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Hay algunas limitaciones en la implementación actual de los títulos basadas en expresiones para los objetos visuales:

* Basadas en expresiones de formato no se admite en objetos visuales de Python, los objetos visuales R o el objeto visual de Influenciadores clave.
* El campo que se crea para el título debe ser un tipo de datos de cadena. Actualmente no se admiten las medidas que devuelven números o fecha y hora (o cualquier otro tipo de datos).

## <a name="next-steps"></a>Pasos siguientes

En este artículo se describe cómo crear expresiones de DAX que convierten los títulos de los objetos visuales en los campos dinámicos que pueden cambiar cuando los usuarios interactúan con los informes. Encontrará los siguientes artículos útil también.

* [Usar la obtención de detalles entre informes en Power BI Desktop](desktop-cross-report-drill-through.md)
* [Uso de la obtención de detalles en Power BI Desktop](desktop-drillthrough.md)