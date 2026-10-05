La forma en que se incorpora un archivo JavaScript mediante `<script>` determina **cuándo comienza su descarga y cuándo se ejecuta** en relación con el procesamiento del HTML.

Los atributos `async` y `defer` modifican este comportamiento.

Es importante diferenciar dos conceptos:

- **Carga:** momento en que el navegador descarga el archivo JavaScript.
- **Ejecución:** momento en que el navegador ejecuta el código JavaScript descargado.

---

## Script normal

Cuando se utiliza un `<script>` sin `async` ni `defer`, el navegador tiene este comportamiento:

1. Comienza a analizar el HTML.
2. Llega al `<script>`.
3. **Pausa el análisis del HTML.**
4. Descarga el archivo JavaScript.
5. Ejecuta el JavaScript.
6. Continúa analizando el HTML.

```html
<script src="./fnc.js"></script>
```

Por lo tanto:

- La descarga del script **bloquea el análisis del HTML**.
- La ejecución ocurre **inmediatamente después de la descarga**.
- El HTML que viene después del `<script>` todavía no fue procesado.

Esto puede afectar el rendimiento de la página, especialmente cuando el archivo JavaScript es grande o tarda en descargarse.

---

## Atributo `defer`

Con `defer`, el navegador puede descargar el archivo JavaScript **en paralelo con el análisis del HTML**.

```html
<script src="./fnc.js" defer></script>
```

El proceso es:

1. El navegador comienza a analizar el HTML.
2. Encuentra el `<script defer>`.
3. **Comienza a descargar el JavaScript sin detener el análisis del HTML.**
4. El HTML continúa procesándose.
5. Cuando termina el análisis del HTML, se ejecuta el JavaScript.
6. La ejecución ocurre antes de `DOMContentLoaded`.

Además, los scripts con `defer` mantienen **el orden en que aparecen en el documento**.

### Idea clave

> **`defer`: descargá el script mientras procesás el HTML, pero esperá para ejecutarlo hasta terminar de procesar el HTML.**

Esto resulta especialmente útil para scripts que necesitan trabajar con elementos del DOM.

---

## Atributo `async`

Con `async`, el navegador también descarga el JavaScript **en paralelo con el análisis del HTML**.

```html
<script src="./fnc.js" async></script>
```

La diferencia está en la ejecución:

1. El navegador continúa analizando el HTML mientras descarga el script.
2. Cuando termina la descarga, **interrumpe el análisis del HTML**.
3. Ejecuta inmediatamente el JavaScript.
4. Cuando termina la ejecución, continúa analizando el HTML.

Por lo tanto, un script `async` puede ejecutarse **antes de que todo el HTML haya sido procesado**.

### Idea clave

> **`async`: descargá el script mientras procesás el HTML y ejecutalo apenas esté listo.**

Por eso es apropiado para scripts **independientes**, que no necesitan esperar al DOM ni depender de otros scripts.

---

## Comparación: normal, `defer` y `async`

|                                    |                 **Normal**                  |               **`defer`**               |        **`async`**         |
| :--------------------------------: | :-----------------------------------------: | :-------------------------------------: | :------------------------: |
|            **Descarga**            |        Bloquea el análisis del HTML         |               En paralelo               |        En paralelo         |
|           **Ejecución**            |     Inmediatamente después de descargar     | Después de terminar el parsing del HTML | Apenas termina la descarga |
| **¿Puede interrumpir el parsing?** |            Sí, mientras descarga            |                   No                    |      Sí, al ejecutar       |
|      **Orden entre scripts**       |                 Se respeta                  |               Se respeta                |      No se garantiza       |
|    **DOM completo al ejecutar**    |       Depende de dónde esté el script       |      Sí, el HTML ya fue procesado       |     No necesariamente      |
|           **Uso típico**           | Casos donde se necesita ejecución inmediata |    JS principal que necesita el DOM     |   Scripts independientes   |

---

# Script al final de `<body>` vs. `defer`

Esta comparación es diferente de `async`.

En ambos casos podemos evitar que un script bloquee el procesamiento inicial del HTML, pero **la diferencia principal está en cuándo comienza la descarga**.

### Script al final de `<body>`

```html
<body>

    <!-- contenido HTML -->

    <script src="./fnc.js"></script>
</body>
```

El navegador primero procesa el HTML que aparece antes del `<script>`.

Cuando llega al script:

1. Detiene el análisis.
2. Descarga el JavaScript.
3. Lo ejecuta.
4. Continúa.

La ventaja es que los elementos HTML anteriores al script ya fueron procesados.

### `defer` en `<head>`

```html
<head>
    <script src="./fnc.js" defer></script>
</head>
```

En este caso, el navegador encuentra el script mucho antes, por lo que **puede comenzar a descargarlo mientras continúa procesando el HTML**.

Después, cuando termina de procesar el HTML, ejecuta el script.

### Diferencia fundamental

**Final de `<body>`:**

> Primero proceso gran parte del HTML → después empiezo a descargar el JS → lo ejecuto.

**`defer`:**

> Empiezo a descargar el JS antes → sigo procesando el HTML → cuando termino, ejecuto el JS.

Por eso `defer` permite **aprovechar mejor el tiempo de descarga**.

---

## ¿Por qué `defer` suele ser preferible?

Para un script principal que necesita acceder al DOM, `defer` permite:

- Descargar el JavaScript mientras se procesa el HTML.
- Evitar bloquear el parsing del HTML.
- Garantizar que el HTML ya fue procesado cuando se ejecuta.
- Mantener el orden entre scripts `defer`.

Por eso es habitual utilizar:

```html
<head>
    <script src="./app.js" defer></script>
</head>
```

en lugar de colocar el script al final de `<body>`.

---

> 
> ##### Resumen
> 
> **Carga ≠ ejecución.**
> 
> - **Normal:** descarga → ejecuta inmediatamente → continúa HTML.
> - **`defer`:** descarga en paralelo → termina HTML → ejecuta después.
> - **`async`:** descarga en paralelo → termina descarga de JS → ejecuta inmediatamente.
> - **Final de `<body>`:** el navegador llega al script después de procesar el HTML anterior → recién ahí lo descarga y ejecuta.
> 
> **Poner el script al final de `<body>` evita bloquear el procesamiento inicial del contenido**, mientras que `defer` además permite **comenzar la descarga antes**.

---

