## Introducción

**CSS Flexbox (Flexible Box Layout)** es un modelo de diseño **unidimensional**.
A diferencia de **CSS Grid**, que trabaja en dos dimensiones, Flexbox está optimizado para distribuir elementos a lo largo de **un solo eje**, ya sea horizontal o vertical.
Permite controlar la **alineación, orden y tamaño** de los elementos dentro de un contenedor.

---

## ¿Por qué usar Flexbox?
Antes de Flexbox, se utilizaban técnicas como:

* **Floats:** originalmente diseñados para envolver texto alrededor de imágenes, no para crear estructuras completas de páginas.
* **Posicionamiento absoluto:** saca elementos del flujo normal del documento, lo que puede complicar la creación de diseños responsivos.
* **Tablas HTML:** pueden generar problemas de semántica y accesibilidad.

Flexbox permite:
* Controlar la alineación vertical y horizontal.
* Ordenar visualmente elementos sin modificar el HTML.
* Distribuir proporcionalmente el espacio disponible.
* Adaptar automáticamente los elementos a diferentes tamaños de pantalla.
* Organizar los elementos en filas o columnas.

---

# Conceptos básicos

Para trabajar con Flexbox es necesario conocer algunos conceptos:
* **Flex container:** elemento padre que utiliza `display: flex` y establece el contexto Flexbox.
* **Flex items:** elementos hijos directos del Flex container.
* **Main axis:** eje principal del contenedor. Es horizontal por defecto.
* **Cross axis:** eje perpendicular al eje principal.
* **Main start / Main end:** puntos de inicio y fin del eje principal.
* **Cross start / Cross end:** puntos de inicio y fin del eje cruzado.

![[Pasted image 20260812201124.png]]

![[Pasted image 20260812201138.png]]



---

# Implementación de Flexbox

Para convertir un elemento en un **Flex container**, se utiliza:

```css
.container {
    display: flex;
}
```

Los elementos hijos directos del contenedor se convierten automáticamente en **Flex items**.

---

## `flex-direction`

Determina la dirección en la que se organizan los elementos sobre el **eje principal**.

```css
.container {
    flex-direction: row | row-reverse | column | column-reverse;
}
```

![[Pasted image 20260812201217.png]]


Valores:

| Valor            | Descripción                                    |
| ---------------- | ---------------------------------------------- |
| `row`            | Elementos en una fila, de izquierda a derecha. |
| `row-reverse`    | Elementos en una fila, en orden inverso.       |
| `column`         | Elementos en una columna.                      |
| `column-reverse` | Elementos en una columna, en orden inverso.    |

![[Pasted image 20260812200741.png]]
![[Pasted image 20260812200844.png]]

---

# `flex-wrap`

Determina si los elementos pueden distribuirse en **múltiples líneas** cuando no existe suficiente espacio.

![[Pasted image 20260812201233.png]]

```css
.container {
    flex-wrap: nowrap | wrap | wrap-reverse;
}
```

| Valor          | Descripción                                                |
| -------------- | ---------------------------------------------------------- |
| `nowrap`       | Todos los elementos permanecen en una sola línea.          |
| `wrap`         | Los elementos pasan a una nueva línea cuando es necesario. |
| `wrap-reverse` | Los elementos pasan a nuevas líneas en dirección inversa.  |


---

# `justify-content`

Permite alinear y distribuir los elementos sobre el **eje principal**.

![[Pasted image 20260812201253.png]]

```css
.container {
    justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
}
```

Valores principales:

* **`flex-start`**: elementos al inicio del eje.
* **`flex-end`**: elementos al final del eje.
* **`center`**: elementos centrados.
* **`space-between`**: máximo espacio entre los elementos, con los extremos pegados a los bordes.
* **`space-around`**: espacio uniforme alrededor de los elementos, con la mitad del espacio en los extremos.
* **`space-evenly`**: espacio completamente uniforme entre los elementos y los extremos.

---

# `align-items`

Permite establecer la alineación de los elementos sobre el **eje cruzado**, es decir, el eje perpendicular al principal.

![[Pasted image 20260812201311.png]]

```css
.container {
    align-items: stretch | flex-start | flex-end | center | baseline;
}
```

Valores:

* **`stretch`**: valor predeterminado. Los elementos se estiran para ocupar el espacio disponible.
* **`flex-start`**: elementos al inicio del eje cruzado.
* **`flex-end`**: elementos al final del eje cruzado.
* **`center`**: elementos centrados en el eje cruzado.
* **`baseline`**: elementos alineados según la línea base de su texto.

---

# `align-content`

Alinea las **líneas de elementos** cuando existe más de una línea y estas no ocupan todo el espacio disponible en el eje cruzado.

![[Pasted image 20260812201329.png]]


```css
.container {
    align-content: center;
}
```

**Importante:** `align-content` solo tiene efecto cuando el contenedor tiene **varias líneas de Flex items**, por ejemplo, cuando se utiliza `flex-wrap: wrap`.

Si todos los elementos se encuentran en una única línea, esta propiedad no tiene efecto.

---

# `flex-grow`

Define la capacidad de un elemento para **crecer** cuando existe espacio disponible dentro del contenedor.

Recibe un valor numérico.

Su valor predeterminado es `0`, por lo que el elemento no crece para ocupar el espacio disponible.

```css
.item {
    flex-grow: 1;
}
```

Si todos los elementos tienen `flex-grow: 1`, el espacio disponible se distribuye proporcionalmente entre ellos.

Si un elemento tiene `flex-grow: 2` y los demás `flex-grow: 1`, ese elemento recibirá el doble de espacio proporcional que cada uno de los otros.

---

# `flex-shrink`

Define la capacidad de un elemento para **encogerse** cuando el espacio disponible del contenedor no es suficiente para mantener el tamaño de todos los elementos.

```css
.item {
    flex-shrink: 1;
}
```

---

# `flex-basis`

Define el **tamaño inicial** de un elemento antes de distribuir el espacio disponible.

```css
.item {
    flex-basis: 200px;
}
```

---

# `order`

Permite modificar el **orden de aparición** de los Flex items sin modificar el orden de los elementos en el HTML.

Recibe valores numéricos enteros.

```css
.item {
    order: 2;
}
```

Los elementos se ordenan de acuerdo con el valor de `order`. Cuanto menor sea el valor, antes aparecerá el elemento.

---
#ProgramaciónIII