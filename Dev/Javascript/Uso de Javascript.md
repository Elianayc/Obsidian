El primer paso es conseguir que el documento HTML tenga noción de la existencia del código [[JavaScript]]. 

Esto puede lograrse mediante:
- La referencia a un **archivo externo** que contenga los comandos.
- Embebiendo el código entre las [[etiquetas]] `<script>`.

El segundo paso consiste en llamar a las [[funciones]] para conseguir el efecto deseado. En la mayoría de los casos, la invocación se realiza para atender eventos provocados por el usuario, como hacer clic sobre un botón o mover el mouse sobre una determinada zona.

También es posible ejecutar código JavaScript ante eventos desatendidos, como el inicio o la finalización de la carga de la página web.

---

## [[JavaScript]] dentro del HTML

La etiqueta `<script>` permite definir código JavaScript directamente dentro del documento HTML.

**Ejemplo:**
```html
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

En el ejemplo se utiliza la etiqueta `<script>` para definir código JavaScript.

Se define la función `sayHi()`, que será ejecutada cuando el usuario presione el botón **"Saludar"**.

La etiqueta `<script>` también puede definirse dentro de `<body>`.

Es usual que las etiquetas `<script>` aparezcan al final de `<body>` por al menos dos razones:

1. **Necesidad de que los elementos HTML ya estén definidos.**
2. **Rendimiento:** si el código a cargar demanda más tiempo que la carga o renderizado de la página, la usabilidad puede verse afectada.

---

## JavaScript en un archivo externo

Definir [[JavaScript]] directamente dentro del HTML no es recomendable desde el punto de vista de la **mantenibilidad**, ya que dentro de un mismo archivo se encuentran tanto la estructura como el comportamiento.

Esto dificulta la separación de responsabilidades, especialmente en aplicaciones que contienen mucho código.

Para solucionarlo, se puede desacoplar el código [[JavaScript]] del HTML en otro archivo e incluirlo mediante la etiqueta `<script>`.

### HTML
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


### JavaScript
```javascript
function sayHi() {
    alert("Hola Mundo!");
}
```


### Ventajas
Separar el código [[JavaScript]] en un archivo externo permite:
- Carga más rápida de la página.
- Mejorar la mantenibilidad y legibilidad.
- Aplicar separación de responsabilidades.
- Reutilizar el código [[JavaScript]] en otro documento HTML.

---

