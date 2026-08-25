Los **selectores CSS** se utilizan para aplicar estilos a determinados elementos HTML.

Existen tres tipos principales de selectores:

- [[Etiquetas]]
- **[[Clases]]**
- **[[IDs]]**

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

---
