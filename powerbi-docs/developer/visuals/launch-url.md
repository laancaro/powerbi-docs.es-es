---
title: Inicio de URL
description: Los objetos visuales de Power BI pueden abrir la dirección URL en una pestaña nueva
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1a7002c3b45f341c0cbc0db683bc4f8a113e21f9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424870"
---
# <a name="launch-url"></a>Inicio de URL

Iniciar URL permite abrir una nueva pestaña (o ventana) del explorador mediante la delegación del trabajo real a Power BI.

## <a name="sample"></a>Ejemplo

```typescript
   this.host.launchUrl('https://powerbi.microsoft.com');
```

## <a name="usage"></a>Usage (Uso)

Use la llamada API `host.launchUrl()`, y pase la dirección URL de destino como argumento de cadena:

```typescript
this.host.launchUrl('http://some.link.net');
```

## <a name="restrictions"></a>Restricciones

* Use solo rutas de acceso absolutas, no relativas. `http://some.link.net/subfolder/page.html` es correcto, pero `/page.html` no se abrirá.
* En la actualidad, solo se admiten los protocolos `http` y `https`. Evite `ftp`, `mailto` y similares.

## <a name="best-practices"></a>Procedimientos recomendados

1. En la mayoría de los casos, es mejor abrir solo un vínculo como respuesta a una acción explícita del usuario. Los usuarios deben entender fácilmente que al hacer clic en el vínculo o el botón se abrirá una pestaña nueva. Desencadenar una llamada a `launchUrl()` sin la acción de un usuario, o como un efecto secundario de otra acción, puede ser confuso o frustrante para el usuario.
2. Si el vínculo no es fundamental para el funcionamiento correcto del objeto visual, se recomienda proporcionar al autor del informe una manera de deshabilitar el vínculo y ocultarlo. Esto es especialmente relevante para los casos de uso especiales de Power BI, como insertar un informe en una aplicación de terceros o publicarlo en la web.
3. Evite activar una llamada a `launchUrl()` desde dentro de un bucle, la función `update` del objeto visual o cualquier otro código que se repita con frecuencia.

## <a name="step-by-step-example"></a>Ejemplo paso a paso

### <a name="adding-a-link-launching-element"></a>Adición de un elemento de inicio de vínculo

Las líneas siguientes se han agregado a la función `constructor` del objeto visual:

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

Y se ha agregado una función privada que crea y adjunta el elemento delimitador:

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

Por último, una entrada del archivo visual.less define el estilo del elemento de vínculo:

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="adding-a-toggling-mechanism"></a>Adición de un mecanismo de alternancia

Esto requiere agregar un objeto estático (vea el [tutorial sobre objetos estáticos](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties)), para que el autor del informe pueda alternar la visibilidad del elemento de vínculo (de forma predeterminada se establece en oculta).
Se ha agregado un objeto estático booleano `showHelpLink` a la entrada de los objetos `capabilities.json`:

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![Alternancia de inicio de URL](./media/launchurl-toggle.png)

Y, en la función `update` del objeto visual, se han agregado las líneas siguientes:

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

La clase `hidden` se define en visual.less para controlar la presentación del elemento.
