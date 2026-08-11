Una **regla CSS** es un conjunto de propiedades asociadas con un **selector**.

---
### Sintaxis de una regla CSS

La estructura general es:
```css
selector {
    propiedad_a: valor;
    ...
    propiedad_k: valor;
    ...
    propiedad_z: valor;
}
```

Por ejemplo, la siguiente regla hace que cada párrafo sea amarillo sobre un fondo negro:
```css
p {
    color: yellow;
    background-color: black;
}
```

---

# Consideraciones al definir reglas

## Unidades
Cuando una propiedad representa un número, se debe indicar la **unidad** en la que se expresa.
Entre el número y la unidad **no puede existir un espacio**.

**Ejemplo**:
```css
p {
    font-size: 10px;
}
```

---

## Colores
Para definir un color se puede utilizar:

- El **nombre del color** (`red`, `green`, `blue`, etc.).
- Su **código hexadecimal** (`#FF0000`, `#00FF00`, `#0000FF`, etc.).
- La **notación RGB**, especificando las componentes:
    - Rojo (R).
    - Verde (G).
    - Azul (B).

**Ejemplo**:
```css
p {
    color: yellow;
    background-color: #EEEEEE;
    border-color: rgb(255, 0, 0);
}
```

---

## Aplicar una regla a varios elementos
Para aplicar el mismo formato a más de un elemento diferente, se pueden especificar varios elementos separados por **comas**.

**Ejemplo**:
```css
th, td {
    border-style: solid;
    border-color: red;
}
```

La regla se aplica tanto a los elementos `<th>` como a los elementos `<td>`.

---

# Jerarquía
Las reglas CSS pueden aplicarse teniendo en cuenta la relación entre los elementos **padre e hijo**.

El selector descendiente permite particularizar el estilo de los elementos hijos sin alterar los atributos del elemento padre.

**Ejemplo**:
```css
/* aplica a todos los elementos p */
p {
    font-size: 24px;
}

/* aplica a todos los elementos strong */
strong {
    font-family: arial;
}

/* aplica a todos los elementos strong cuyo padre sea un elemento p */
p strong {
    color: green;
    background-color: black;
}
```

**En este caso**:
- `p` → se aplica a todos los elementos `<p>`.
- `strong` → se aplica a todos los elementos `<strong>`.
- `p strong` → se aplica a los elementos `<strong>` que se encuentran dentro de un `<p>`.

---
