Los **selectores CSS** se utilizan para aplicar estilos a determinados elementos HTML.

Existen tres tipos principales de selectores:

- **Etiquetas**
- **Clases**
- **IDs**

---

## Selector por etiqueta
Los selectores CSS pueden definirse utilizando el **tipo de elemento HTML** sobre el cual se aplicarán.

Por ejemplo:
```css
a {
    /* Formato CSS para todos los elementos a del documento HTML */
}
```

Este tipo de selector es el más **genérico**, ya que aplica el estilo sobre todos los elementos de la etiqueta especificada.

---

## Selector por clase

Cuando necesitamos que múltiples elementos posean el mismo estilo, podemos definir una **clase** en CSS y utilizar el atributo `class`, que poseen los elementos HTML, para aplicar dicho estilo a todos los elementos que lo necesiten.

Para definir una regla que se aplique a todos los elementos con determinado valor en el atributo `class`, el nombre de la regla debe comenzar con un **punto (`.`)**.

Ejemplo:

```css
.word {
    /* Formato CSS para los elementos con class="word" */
}
```

A diferencia del selector por `id`, una regla definida mediante una **clase** puede aplicarse a múltiples elementos.

---

## Selector por ID

El atributo `id` de un elemento HTML define un **identificador único** que no debe repetirse dentro del documento.

Esto permite identificar un elemento de manera que se puedan aplicar estilos específicamente sobre él.

Para definir una regla que se aplique a un determinado `id`, la regla debe comenzar con el símbolo **numeral (`#`)**.

Ejemplo:

```css
#el_id {
    ...
}
```

---

# Precedencia de declaraciones

Cuando existen distintas reglas que se aplican sobre el mismo elemento, se debe tener en cuenta la **precedencia** de las declaraciones.

### Propiedades diferentes

Si las reglas poseen propiedades diferentes, las propiedades se **combinan** y todas prevalecen.

### Propiedades iguales

Si las reglas poseen propiedades iguales, solo prevalece la **última definida**.

---

## Orden de precedencia

El mecanismo de precedencia de las reglas CSS se aplica de la siguiente manera:

1. Las reglas por **etiqueta** tienen menor precedencia, porque son más genéricas.
2. Las reglas por **clase** sobrescriben las reglas por etiqueta.
3. Las reglas por **ID** sobrescriben cualquier otra regla.

Por lo tanto:

**Etiqueta → Clase → ID**

---

# `!important`

Para resolver **colisiones entre reglas** que se aplican sobre un mismo elemento HTML, se puede utilizar la palabra `!important`.

Su objetivo es **interrumpir la precedencia** de las reglas CSS.

`!important` debe escribirse después del valor de la propiedad CSS que se quiere convertir en la más importante.

Ejemplo:
```css
p {
    color: red !important;
}
```

Debe aplicarse a **cada valor de propiedad** que se quiera establecer como `!important`.