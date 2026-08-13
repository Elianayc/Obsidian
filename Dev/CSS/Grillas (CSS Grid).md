**CSS Grid** es un sistema de diseño **bidimensional** que permite estructurar páginas web trabajando simultáneamente con **filas y columnas**.
A diferencia de métodos anteriores, como las tablas HTML, Grid permite crear diseños complejos de forma más sencilla y precisa.

---

## ¿Por qué usar CSS Grid y no tablas?

Aunque las tablas HTML fueron utilizadas históricamente para crear diseños, presentan algunas limitaciones:
- **Semántica incorrecta:** las tablas están diseñadas para representar datos tabulares, no para estructurar páginas.
- **Accesibilidad reducida:** los lectores de pantalla interpretan las tablas como datos, lo que puede generar confusión.
- **Rendimiento inferior:** las tablas requieren que el navegador cargue toda la estructura antes de mostrar el contenido.
- **Mantenimiento complicado:** modificar diseños basados en tablas implica realizar cambios extensos en el HTML.

CSS Grid permite:
- Separar claramente el **contenido (HTML)** de la **presentación (CSS)**.
- Crear diseños responsivos con mayor flexibilidad.
- Controlar la alineación y el espaciado.
- Reorganizar visualmente los elementos sin modificar el HTML.

---

# Conceptos básicos

Para trabajar con CSS Grid es importante conocer los siguientes conceptos:

- **Grid container:** elemento padre que establece el contexto de la cuadrícula.
	![[Pasted image 20260812201124.png|256]]

- **Grid item:** cualquier hijo directo del Grid container.
	![[Pasted image 20260812201138.png|255]]
	
- **Grid line:** líneas divisorias horizontales y verticales que forman la estructura de la cuadrícula.
	![[Pasted image 20260812202017.png|194]]

- **Grid track:** espacio comprendido entre dos líneas adyacentes, ya sea una fila o una columna.
	![[Pasted image 20260812202040.png|194]]

- **Grid cell:** unidad más pequeña de la cuadrícula, formada por la intersección de una fila y una columna.
  ![[Pasted image 20260812202202.png|201]]
  
- **Grid area:** área rectangular formada por cuatro Grid lines y que puede abarcar múltiples celdas.
  ![[Pasted image 20260812202147.png|201]]
  
- **Gap:** espacio existente entre filas y/o columnas.


---

# Implementación de una grilla
Para crear una cuadrícula, primero debemos convertir un elemento en un **Grid container** utilizando `display: grid`.

### HTML
```html
<div class="container">
    <div class="a">Item 1</div>
    <div class="b">Item 2</div>
    <div class="c">Item 3</div>
</div>
```

### CSS
```css
.container {
    display: grid;
    grid-template-columns: 200px 1fr 2fr;
    grid-template-rows: auto;
}
```

En este ejemplo se define una grilla con **tres columnas**:

- La primera tiene un ancho fijo de `200px`.
- La segunda ocupa `1fr` del espacio disponible.
- La tercera ocupa `2fr` del espacio disponible.

Las filas tienen un tamaño determinado automáticamente mediante `auto`.

---

# Unidades de medida para Grid
CSS Grid permite utilizar diferentes unidades para definir el tamaño de filas y columnas:

|Unidad|Descripción|
|---|---|
|`px`|Tamaño fijo.|
|`%`|Tamaño relativo al contenedor.|
|`fr`|Distribuye proporcionalmente el espacio disponible.|
|`auto`|El tamaño se determina según el contenido.|
|`min-content`|Se basa en el tamaño mínimo que necesita el contenido.|
|`max-content`|Se basa en el tamaño máximo que necesita el contenido.|
|`minmax(min, max)`|Establece un límite mínimo y máximo para el tamaño.|

---

# Función `repeat()`

La función `repeat()` permite definir patrones repetitivos de manera más sencilla.
```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(2, 100px 50px);
}
```

La siguiente definición:
```css
grid-template-columns: repeat(3, 1fr);
```

equivale a:
```css
grid-template-columns: 1fr 1fr 1fr;
```

Mientras que:
```css
grid-template-rows: repeat(2, 100px 50px);
```

equivale a:
```css
grid-template-rows: 100px 50px 100px 50px;
```

---

# Grillas por áreas

**Grid Areas** permite nombrar diferentes secciones de la cuadrícula y asignar elementos a ellas.
Esto facilita la creación y el mantenimiento de layouts complejos.

### HTML
```html
<div class="layout-areas">
    <div class="header">Header</div>
    <div class="sidebar">Sidebar</div>
    <div class="main">Contenido</div>
    <div class="footer">Footer</div>
</div>
```

### CSS
```css
.layout-areas {
    display: grid;
    grid-template-columns: 200px 1fr;
    grid-template-rows: 100px 1fr 50px;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
}

.header {
    grid-area: header;
}

.sidebar {
    grid-area: sidebar;
}

.main {
    grid-area: main;
}

.footer {
    grid-area: footer;
}
```

La cantidad de áreas definidas mediante `grid-template-areas` debe corresponder con la cantidad de filas y columnas establecidas mediante `grid-template-rows` y `grid-template-columns`.

---

# Espacios entre elementos

Para establecer espacios entre las celdas de una cuadrícula se pueden utilizar:

![[Pasted image 20260812201406.png]]

- `column-gap`: espacio entre columnas.
- `row-gap`: espacio entre filas.

```css
.grid {
    column-gap: 100px;
    row-gap: 10px;
}
```

En este ejemplo:
- Hay `100px` de espacio entre columnas.
- Hay `10px` de espacio entre filas.

---

# Alineación de elementos

CSS Grid proporciona diferentes propiedades para controlar la alineación y distribución de los elementos.

## `justify-content` y `align-content`

Permiten modificar la distribución de **todo el contenido de la cuadrícula en conjunto**.

```css
.container {
    justify-content: start | center | end | space-between | space-around | space-evenly;
    align-content: start | center | end | space-between | space-around | space-evenly;
}
```

- `justify-content`: controla la distribución sobre el **eje horizontal**.
- `align-content`: controla la distribución sobre el **eje vertical**.

---

## `justify-items` y `align-items`

Permiten posicionar los elementos **dentro de sus respectivas celdas**.

```css
.container {
    justify-items: start | center | end | stretch;
    align-items: start | center | end | stretch;
}
```

- `justify-items`: controla la alineación horizontal de los elementos dentro de sus celdas.
- `align-items`: controla la alineación vertical de los elementos dentro de sus celdas.

---

## `justify-self` y `align-self`

Permiten modificar la posición de **un elemento individual** dentro de su celda.

![[Pasted image 20260812201558.png]]

```css
.item {
    justify-self: start | center | end | stretch;
    align-self: start | center | end | stretch;
}
```

- `justify-self`: controla la alineación horizontal del elemento.
- `align-self`: controla la alineación vertical del elemento.

También existe la propiedad abreviada `place-self`, que permite establecer ambas:

```css
.item {
    place-self: center;
}
```

`place-self` permite establecer simultáneamente `align-self` y `justify-self`.


---
![[Pasted image 20260812201857.png]]

---
