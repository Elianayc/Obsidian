Los botones permiten ejecutar acciones dentro de un formulario.

Existen tres tipos principales:

|Tipo|Función|
|---|---|
|`submit`|Envía los datos al documento indicado en `action`|
|`reset`|Limpia todos los campos ingresados|
|`button`|No realiza una acción por sí mismo, suele utilizarse con JavaScript|

**Ejemplos**:

```html
<button type="submit">
Enviar
</button>
```

```html
<button type="reset">
Borrar
</button>
```

```html
<button type="button">
Acción
</button>
```

Los botones deben encontrarse dentro del formulario al que afectan.

---

# Controles de selección

Los controles de selección permiten que el usuario elija opciones definidas previamente por el programador.

El valor enviado corresponde al atributo:
```html
value
```

Existen tres grupos principales:
- Botones de radio.
- Casillas de chequeo.
- Menú desplegable.

---

## Botones de radio

Permiten seleccionar solamente una opción entre varias disponibles.

**Ejemplo**:
```html
<input type="radio" value="rojo">
Rojo

<input type="radio" value="azul">
Azul
```

---

## Casillas de chequeo (Checkbox)

Permiten seleccionar una, varias o ninguna opción.

**Ejemplo**:
```html
<input type="checkbox" value="acepta">
Acepta términos y condiciones
```

---

## Menú desplegable

Permite seleccionar una opción de una lista.

Se crea utilizando:
```html
<select>
```

y las opciones mediante:
```html
<option>
```

**Ejemplo**:
```html
<select>
    <option>Large</option>
    <option>Medium</option>
    <option>Small</option>
</select>
```

Por defecto permite seleccionar una sola opción.

---
