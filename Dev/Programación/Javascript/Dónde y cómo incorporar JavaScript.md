El primer paso es conseguir que el documento HTML tenga conocimiento de la existencia del código JavaScript.

Esto puede lograrse principalmente de dos formas:

- **JavaScript inline:** el código se escribe directamente dentro del documento HTML, utilizando la etiqueta `<script>` o, en algunos casos, dentro de atributos de eventos.

- **JavaScript externo:** el código se escribe en un archivo `.js` separado y se incorpora al HTML mediante la etiqueta `<script>` y su atributo `src`.

---

## JavaScript inline

El **JavaScript inline** consiste en escribir el código JavaScript directamente dentro del documento HTML.

La etiqueta `<script>` permite definir código JavaScript dentro del documento.

**Ejemplo:**

```js
<html>
<head>
    <title>Prueba uso Js</title>
    <script>
        function sayHi() {
            alert("Hola Mundo!");
        }
    </script>
</head>

<body>
    <div>
        <button type="button" onclick="sayHi()">Saludar</button>
    </div>
</body>
</html>
```

En el ejemplo se utiliza la etiqueta `<script>` para definir código JavaScript directamente dentro del HTML.

Se define la función `sayHi()`, que será ejecutada cuando el usuario presione el botón **"Saludar"**.

La etiqueta `<script>` puede ubicarse tanto dentro de `<head>` como dentro de `<body>`.

> La ubicación del `<script>` y las diferentes formas de carga y ejecución (`defer`, `async`, etc.) se desarrollan en el apartado **Cómo se carga y ejecuta un archivo JavaScript**.

---

## JavaScript en un archivo externo

Otra posibilidad consiste en colocar el código JavaScript en un archivo separado con extensión `.js` e incluirlo en el HTML mediante la etiqueta `<script>` y el atributo `src`.

**HTML:**

```html
<html>
<head>
    <title>Prueba uso Js</title>

    <script src="./fnc.js"></script>
</head>

<body>
    <div>
        <button type="button" onclick="sayHi()">Saludar</button>
    </div>
</body>
</html>
```

**JavaScript (`fnc.js`):**

```js
function sayHi() {
    alert("Hola Mundo!");
}
```

Separar el código JavaScript del HTML permite mejorar la **mantenibilidad** y la **separación de responsabilidades**, ya que la estructura del documento y su comportamiento quedan en archivos diferentes.

### Ventajas

- Mejorar la **mantenibilidad y legibilidad**.
- Aplicar una mejor **separación de responsabilidades**.
- **Reutilizar** el mismo código JavaScript en diferentes documentos HTML.
- Facilitar la organización del código en aplicaciones grandes.

---
