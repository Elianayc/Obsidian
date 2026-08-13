Las tablas permiten organizar información en filas y columnas.

Una tabla está formada por un conjunto de celdas donde se pueden almacenar diferentes tipos de contenido.

HTML dispone de varias etiquetas para definir la estructura de una tabla.

---

## Elementos principales de una tabla

|Elemento|Tipo|Descripción|
|---|---|---|
|`<table>`|Bloque|Contiene todos los elementos que forman la tabla (filas y columnas)|
|`<tr>`|Bloque|Define una fila de la tabla|
|`<th>`|Bloque|Define una celda de encabezado de la tabla|
|`<td>`|Bloque|Define una celda de datos de la tabla|

---

## Ejemplo de tabla

```html
<table>
    <tr>
        <th>Producto</th>
        <th>Precio</th>
        <th>Cantidad</th>
    </tr>

    <tr>
        <td>Laptop</td>
        <td>$1200</td>
        <td>5</td>
    </tr>

    <tr>
        <td>Mouse</td>
        <td>$25</td>
        <td>20</td>
    </tr>
</table>
```

**Resultado**:

|Producto|Precio|Cantidad|
|---|---|---|
|Laptop|$1200|5|
|Mouse|$25|20|

---
