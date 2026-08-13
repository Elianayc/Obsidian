Todos los elementos HTML son interpretados como **cajas rectangulares**. Comprender el modelo de caja es fundamental para crear diseños complejos y controlar la alineación y distribución de los elementos.

Los elementos de tipo **línea (inline)** ocupan el ancho necesario según su contenido, mientras que los elementos de tipo **bloque (block)** ocupan, por defecto, el 100% del ancho disponible de su elemento contenedor.

![[Pasted image 20260812195734.png]]

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
1. **[[Contenido (content)]]**
2. **[[Relleno (padding)]]**
3. **[[Borde (border)]]**
4. **[[Margen (margin)]]**
   
![[Pasted image 20260812195808.png]]

---

# Propiedad `display`

La propiedad `display` permite definir cómo se comporta y se muestra un elemento HTML.

Entre sus posibilidades se encuentran:

- ### `block`
	Convierte el elemento en un **elemento de bloque**.

- ### `inline`
	Convierte el elemento en un **elemento de línea**.

- ### `inline-block`
	Combina características de ambos:
	- Mantiene el comportamiento de un elemento `inline`.
	- Permite establecer `width` y `height`.
	- Respeta los márgenes verticales.

- ### `none`
	Hace que el elemento **no se muestre**.

![[Pasted image 20260812200706.png]]

---


## Comparación entre `block`, `inline` e `inline-block`

|Propiedad|`block`|`inline`|`inline-block`|
|---|:-:|:-:|:-:|
|`width`|Sí|No|Sí|
|`height`|Sí|No|Sí|
|`padding`|Sí|Solo costados|Sí|
|`margin`|Sí|Solo costados|Sí|

---
