Todos los elementos HTML son interpretados como **cajas rectangulares**. Comprender el modelo de caja es fundamental para crear diseños complejos y controlar la alineación y distribución de los elementos.

Los elementos de tipo **línea (inline)** ocupan el ancho necesario según su contenido, mientras que los elementos de tipo **bloque (block)** ocupan, por defecto, el 100% del ancho disponible de su elemento contenedor.

---

## Width y Height

CSS permite controlar el tamaño de la caja mediante:

- `width`: define el **ancho**.
    
- `height`: define el **alto**.
    

Estas propiedades:

- No admiten valores negativos.
    
- Cuando se expresan en porcentaje, se calculan en relación con el elemento padre.
    

Cuando un elemento tiene un ancho o alto fijo y su contenido supera las dimensiones de la caja, el contenido puede desbordarse y superponerse con otros elementos.

Para controlar este comportamiento se utiliza la propiedad `overflow`.

### Overflow

Permite controlar qué sucede cuando el contenido excede las dimensiones de la caja.

|Valor|Descripción|
|---|---|
|`visible`|Valor predeterminado. El contenido excedente permanece visible.|
|`hidden`|Oculta el contenido que excede la caja.|
|`scroll`|Genera barras de desplazamiento en ambos ejes, aunque no sean necesarias.|
|`auto`|Genera barras de desplazamiento únicamente cuando son necesarias.|

---

# Áreas del Box Model

Cada caja está compuesta por cuatro áreas:

1. **Contenido (content)**
    
2. **Relleno (padding)**
    
3. **Borde (border)**
    
4. **Margen (margin)**
    

```text
┌──────────────────────────────────────┐
│               Margin                 │
│  ┌────────────────────────────────┐  │
│  │             Border             │  │
│  │  ┌──────────────────────────┐  │  │
│  │  │          Padding         │  │  │
│  │  │  ┌────────────────────┐  │  │  │
│  │  │  │      Content       │  │  │  │
│  │  │  └────────────────────┘  │  │  │
│  │  └──────────────────────────┘  │  │
│  └────────────────────────────────┘  │
└──────────────────────────────────────┘
```

---

## Área de contenido

Es el área donde se encuentra el **contenido real del elemento**.

Puede contener:

- Texto.
    
- Imágenes.
    
- Videos.
    
- Otros elementos.
    

Sus dimensiones se establecen mediante `width` y `height`.

También se pueden aplicar estilos sobre esta área, como colores o imágenes de fondo.

---

## Propiedad `box-sizing`

La propiedad `box-sizing` determina cómo se calculan las dimensiones de una caja.

### `content-box`

Es el valor predeterminado.

Las propiedades `width` y `height` se aplican únicamente al **área de contenido**.

Si se agregan `padding` y `border`, estos se suman al tamaño especificado.

```css
.content-box-example {
    box-sizing: content-box;
    width: 200px;
    height: 100px;
    padding: 20px;
    border: 10px solid black;
    margin: 15px;
}
```

Por lo tanto, el tamaño total de la caja será mayor que los valores definidos en `width` y `height`.

### `border-box`

Con `border-box`, las propiedades `width` y `height` incluyen el **contenido, padding y border**.

El navegador ajusta automáticamente el tamaño del área de contenido para mantener las dimensiones totales especificadas.

```css
.border-box-example {
    box-sizing: border-box;
    width: 200px;
    height: 100px;
    padding: 20px;
    border: 10px solid black;
    margin: 15px;
}
```

Esto facilita la creación de diseños con tamaños más precisos y predecibles.

---

# Área de relleno — Padding

El **padding** es el espacio interno que separa el contenido del borde de la caja.

Se puede establecer individualmente mediante:

- `padding-top`
    
- `padding-right`
    
- `padding-bottom`
    
- `padding-left`
    

También se puede utilizar la propiedad resumida `padding`.

```css
div {
    padding: 20px;
}
```

---

# Área de borde — Border

El **border** rodea el área de padding y permite establecer:

- Grosor.
    
- Color.
    
- Estilo.
    

El grosor se define mediante `border-width`.

Puede establecerse para cada lado individualmente:

```css
div {
    border-top-width: 10px;
    border-right-width: 5px;
    border-bottom-width: 10px;
    border-left-width: 5px;
}
```

También puede establecerse para los cuatro bordes:

```css
div {
    border-width: 10px;
}
```

Si se indican cuatro valores, se aplican en el siguiente orden:

**superior → derecho → inferior → izquierdo**

---

# Área de margen — Margin

El **margin** es el espacio exterior que separa un elemento de sus elementos vecinos.

Se puede establecer individualmente mediante:

- `margin-top`
    
- `margin-right`
    
- `margin-bottom`
    
- `margin-left`
    

También se puede utilizar la propiedad resumida `margin`.

---

# Propiedad `display`

La propiedad `display` permite definir cómo se comporta y se muestra un elemento HTML.

Entre sus posibilidades se encuentran:

- Convertir un elemento de bloque en uno de línea.
    
- Convertir un elemento de línea en uno de bloque.
    
- Combinar características de ambos.
    
- Ocultar un elemento.
    

### `block`

Convierte el elemento en un **elemento de bloque**.

### `inline`

Convierte el elemento en un **elemento de línea**.

### `inline-block`

Combina características de ambos:

- Mantiene el comportamiento de un elemento `inline`.
    
- Permite establecer `width` y `height`.
    
- Respeta los márgenes verticales.
    

### `none`

Hace que el elemento **no se muestre**.

---

## Comparación entre `block`, `inline` e `inline-block`

|Propiedad|`block`|`inline`|`inline-block`|
|---|:-:|:-:|:-:|
|`width`|Sí|No|Sí|
|`height`|Sí|No|Sí|
|`padding`|Sí|Solo costados|Sí|
|`margin`|Sí|Solo costados|Sí|