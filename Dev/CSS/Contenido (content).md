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

![[Pasted image 20260812200626.png]]

---
