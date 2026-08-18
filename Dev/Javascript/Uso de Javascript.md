El primer paso es conseguir que el documento HTML tenga noción de la existencia del código JavaScript. 

Esto puede lograrse mediante:
- La referencia a un **archivo externo** que contenga los comandos.
- Embebiendo el código entre las etiquetas `<script>`.

El segundo paso consiste en llamar a las funciones para conseguir el efecto deseado. En la mayoría de los casos, la invocación se realiza para atender eventos provocados por el usuario, como hacer clic sobre un botón o mover el mouse sobre una determinada zona.

También es posible ejecutar código JavaScript ante eventos desatendidos, como el inicio o la finalización de la carga de la página web.

---

## JavaScript dentro del HTML

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

Definir JavaScript directamente dentro del HTML no es recomendable desde el punto de vista de la **mantenibilidad**, ya que dentro de un mismo archivo se encuentran tanto la estructura como el comportamiento.

Esto dificulta la separación de responsabilidades, especialmente en aplicaciones que contienen mucho código.

Para solucionarlo, se puede desacoplar el código JavaScript del HTML en otro archivo e incluirlo mediante la etiqueta `<script>`.

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
Separar el código JavaScript en un archivo externo permite:
- Carga más rápida de la página.
- Mejorar la mantenibilidad y legibilidad.
- Aplicar separación de responsabilidades.
- Reutilizar el código JavaScript en otro documento HTML.

---

# Propiedades `async` y `defer`

Las propiedades `async` y `defer` son atributos del elemento `<script>` que modifican la forma en que el navegador carga y ejecuta los archivos JavaScript.

Ambos ayudan a mejorar el rendimiento de carga de la página, pero funcionan de manera diferente.

---

## Script normal

Cuando se carga un script sin estos atributos, el comportamiento predeterminado es:

1. El navegador detiene el análisis del HTML.
2. Descarga el script.
3. Ejecuta el script inmediatamente.
4. Continúa analizando el HTML.

Esto puede ralentizar significativamente la carga de la página porque bloquea el renderizado.

---

## Atributo `defer`

Cuando se carga un script con el atributo `defer`:

1. El navegador descarga el script en paralelo mientras continúa analizando el HTML.
2. Espera a que el análisis del HTML termine completamente.
3. Ejecuta los scripts en el orden en que aparecen en el documento.
4. Los scripts se ejecutan justo antes del evento `DOMContentLoaded`.

**Ejemplo:**

<script src="./fnc.js" defer></script>

En resumen, `defer` indica al navegador:

> Descarga este script mientras sigues trabajando, pero no lo ejecutes hasta que hayas terminado de analizar toda la página.

---

## Atributo `async`

Cuando se carga un script con el atributo `async`:

1. El navegador descarga el script en paralelo mientras continúa analizando el HTML.
2. Pausa el análisis del HTML cuando el script termina de descargarse.
3. Ejecuta el script inmediatamente.
4. Continúa analizando el HTML después de que el script termina.

**Ejemplo:**

<script src="./fnc.js" async></script>

En resumen, `async` indica al navegador:

> Descarga este script mientras sigues trabajando y ejecútalo tan pronto como esté listo, incluso si aún no terminaste de analizar el HTML.

---

# ¿Cuándo usar cada uno?

### Sin atributos

Cuando el script debe ejecutarse inmediatamente y es esencial para la funcionalidad inicial.

**Poco recomendado.**

### `defer`

Ideal para:

- Scripts que necesitan interactuar con todo el DOM.
- Scripts que mantienen el orden de ejecución.
- Scripts principales de la aplicación.

### `async`

Ideal para:

- Scripts independientes que no dependen del DOM ni de otros scripts.
- Scripts de análisis y publicidad.

---

# Script al final de `<body>` vs. `defer`

Existen similitudes y diferencias entre ambos métodos respecto de la performance de la página.

### Tiempo de descarga

Con `defer`, la descarga comienza antes, mientras que los scripts ubicados al final de `<body>` recién comienzan a descargarse cuando el navegador llega a ellos.

### Percepción de velocidad

Ambos métodos permiten que el contenido visual aparezca rápidamente, ya que no bloquean el renderizado inicial.

---

## ¿Cuál es mejor para la performance?

En general, `defer` proporciona mejor performance que los scripts ubicados al final de `<body>`, especialmente para:

- Sitios con scripts pesados o muchos scripts.
- Conexiones lentas donde ganar tiempo en la descarga es importante.
- Aplicaciones web complejas.

---

## Consideraciones adicionales

### Compatibilidad

`defer` tiene buen soporte en navegadores modernos. En caso de necesitar compatibilidad con navegadores muy antiguos, los scripts al final de `<body>` son más seguros.

### Momento de ejecución

Si se necesita que ciertos scripts se ejecuten lo antes posible después de que el HTML esté disponible, `defer` es mejor que colocarlos al final de `<body>`.

### Facilidad de mantenimiento

Tener todos los scripts en el `<head>` con `defer` puede facilitar el mantenimiento del código.

---

## Conclusión

Los scripts al final de `<body>` son una solución simple que funciona en todos los navegadores, mientras que `defer` ofrece una optimización adicional al permitir que las descargas comiencen antes.

Ambas técnicas mejoran la performance, pero `defer` es generalmente superior en términos de eficiencia de carga.