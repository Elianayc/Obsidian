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
