---
title: Sugerencias y trucos para hacer preguntas con Preguntas y respuestas
description: Sugerencias y trucos para hacer preguntas con Preguntas y respuestas en Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 42460930c3e5406c9a3822c75084d641fd9255bf
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292347"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Sugerencias para hacer preguntas con Preguntas y respuestas de Power BI
## <a name="words-and-terminology-that-qa-recognizes"></a>Palabras y terminología que reconoce Preguntas y respuestas
La lista de palabras clave de esta página no es exhaustiva.  La mejor forma de ver si Power BI reconoce una palabra clave es probar a escribirla en el cuadro de pregunta.  Si la palabra o término aparece atenuado, Power BI no lo reconoce.

La siguiente lista usa el tiempo verbal presente, pero se reconocen todos los tiempos verbales en la mayoría de los casos. Por ejemplo, "es" incluye **son**, **era**, **fueron**, **será**, **tiene**, **tenía**, **tendrá**, **hacer**, **hace**, **hizo**.********  Y "ordenar" incluye **ordenado** y **ordenando**.  Además, Power BI reconoce e incluye versiones de una palabra en singular y plural. 

> [!NOTE]
> Preguntas y respuestas está disponible igualmente en la aplicación [Microsoft Power BI para iOS en dispositivos iPad, iPhone y iPod Touch](mobile/mobile-apps-ios-qna.md).
>  


|Categoría  |Palabras clave  |Columna3  |
|---------|---------|---------|
|**Agregados**     | total, suma, cantidad, número, recuento, promedio, máximo, mínimo, menor, más grande, más pequeño, más alto, mayor, máximo, máx., mayor, menor, más pequeño, mínimo, mín          |
|     |         |         
**Artículos**     |  un, una, el, la              |
|     |         |         
|**En blanco y booleano**     |   en blanco, vacío, null, con el prefijo "no", una cadena vacía, texto vacío, true, t, false, f          |
|     |         |         |
|**Comparaciones**     |   vs, frente a, en comparación con            |
|     |         |         |
|**Conjunciones**     |  y, o, cada, con, frente a, y, pero, ni, junto con, además       |         
|          |         |
|**Contracciones**     |  Preguntas y respuestas reconoce casi todas las contracciones, pruébelo.  Por ejemplo: al o del          |
|        |         |
|**Fechas**     |       Power BI reconoce la mayoría de los términos de fecha (día, semana, mes, año, trimestre, década...) y las fechas escritas en muchos formatos diferentes (véalo a continuación). Power BI también reconoce las siguientes palabras clave: NombreMes, días 1-31, década. Ejemplos: 3 de enero de 1995, 3 enero 1995, 03 ene 1995, 3 ene 1995, el 3 de enero, enero de 1995, 01-1995, 01/1995, nombres de meses.         |
|        |         |
|**Fechas relativas**     |   hoy, ahora, hora actual, ayer, mañana, actual, después, las próximas, último, anterior, hace, antes de ahora, después, a más tardar, de, en, desde ahora, después de ahora, en el futuro, pasado, último, anterior, sobre, hace N días, de hoy en N días, una vez, dos veces.|
|    |  Ejemplo: número de pedidos en los 6 últimos días.  |            |
|        |         |
|**Igualdad (intervalo)**     |   en, igual a, =, después, es más que, en, entre, antes  |
|  |Ejemplos: ¿El año de pedido es antes de 2012? ¿El precio es entre 10 y 20? ¿John es mayor de 40? ¿Total de ventas en 200-300?              |
|        |         |
|**Igualdad (valor)**     |   es, igual, igual a, en, de, para, está en |
|   | Ejemplos: ¿Qué productos son verdes? La fecha de pedido es igual a 2012. ¿La edad de John es 40? ¿El total de ventas no es igual a 200? Fecha de pedido de 1/1/2016. ¿10 en el precio? ¿Verde para color? ¿10 en el precio?              |
|        |         |
|**Nombres**     |       Si una columna del conjunto de datos contiene la frase "nombre" (por ejemplo, NombreEmpleado), Preguntas y respuestas comprende que los valores de esa columna son nombres. Puede hacer preguntas como "qué empleados se llaman Robert".          |
|        |         |
**Pronombres**  | él, a él, su, ella, a ella, suyo, ellos, de ellos, este, estos, ese, esos
|**Comandos de consulta**     |    ordenado, ordenar por, dirección, agrupar, agrupar por, de, mostrar, enumerar, darme, nombre, solo, organizar, clasificar, comparar, con, por orden alfabético, ascendente, descendente, orden             |
|        |         |
|**Intervalo**     |      mayor, más, más grande, superior, sobre, >, menos, más pequeño, menor, bajo, <, al menos, no menor que, > =, como máximo, no más de, <=, en, entre, en el intervalo de, desde, más adelante, anteriormente, antes, después, en, más tarde que, después, desde, a partir de, terminando con           |
|        |         |
**Horas**  |a. m., p. m., en punto, mediodía, medianoche, hora, minuto, segundo, hh:mm:ss  |
|  |  Ejemplos: 10 p. m., 10:35 p. m., 10:35:15 p. m., 10 en punto, mediodía, medianoche, hora, minuto, segundo.  |
|  |  |
|**Principales N**     |     (orden, clasificación): superior, inferior, primero, último, siguiente, más antiguo, más reciente, siguiente            |
|        |         |
|**Tipos de objeto visual**     |  todos los tipos de objeto visual nativos en Power BI.  Si es una opción en el panel Visualizaciones, puede incluirla en la pregunta.  La excepción a esto son los [objetos visuales personalizados](../power-bi-custom-visuals.md) que haya agregado manualmente en el panel Visualización.  |
|  |  Ejemplo: mostrar distritos por mes y el total de ventas como gráfico de barras               |
|        |         |
|**Qu (relación, calificado)**  | cuándo, dónde, qué, a quién, quién, cuántos, cuánto, cuántas veces, con qué frecuencia, importe, número, cantidad, cuánto tiempo, qué                |

## <a name="qa-helps-you-phrase-the-question"></a>Preguntas y respuestas le ayuda a formular la pregunta
Preguntas y respuestas hará todo lo posible para comprender y responder a la pregunta que se le pida. Puede hacerlo de varias maneras. En todas ellas, puede aceptar la acción en su totalidad o en parte, o bien, rechazarla. A medida que escribe su pregunta, Preguntas y respuestas:

* completa automáticamente las palabras y preguntas. Usa diversas estrategias, como la opción de Autocompletar palabras reconocidas y preguntas usadas previamente que devolvieron respuestas válidas. Si hay más de una opción de Autocompletar, se muestra en una lista desplegable.
* corrige la ortografía.
* proporciona una vista previa de la respuesta en forma de una visualización. La visualización se actualiza a medida que escribe y edita la pregunta (no espera a que presione ENTRAR).
* sugiere términos de reemplazo de los conjuntos de datos subyacentes cuando mueve el mouse en el cuadro de pregunta.
* redefine la pregunta en función de los datos de los conjuntos de datos subyacentes. Preguntas y respuestas reemplaza las palabras utilizadas con sinónimos de los conjuntos de datos subyacentes. Leyendo la redefinición, sabrá si Preguntas y respuestas comprendió su pregunta o no. 
* atenúa palabras que no comprende.

## <a name="dont-stop-now"></a>No se detenga ahora
Cuando Preguntas y respuestas muestre los resultados, mantenga el curso de la conversación. Use las características interactivas de la visualización y de Preguntas y respuestas para obtener más información.

## <a name="next-steps"></a>Pasos siguientes
Volver a [Preguntas y respuestas en Power BI](end-user-q-and-a.md)  

[Power BI: Conceptos básicos](end-user-basic-concepts.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](http://community.powerbi.com/)

