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
```javascript
<script src="./fnc.js" defer></script>
```

En resumen, `defer` indica al navegador:

> Descargá este script mientras seguís trabajando, pero no lo ejecutes hasta que hayas terminado de analizar toda la página.


- [[Script al final de body vs. defer]]

---

## Atributo `async`
Cuando se carga un script con el atributo `async`:

1. El navegador descarga el script en paralelo mientras continúa analizando el HTML.
2. Pausa el análisis del HTML cuando el script termina de descargarse.
3. Ejecuta el script inmediatamente.
4. Continúa analizando el HTML después de que el script termina.

**Ejemplo:**
```javascript
<script src="./fnc.js" async></script>
```

En resumen, `async` indica al navegador:

> Descargá este script mientras seguís trabajando y ejecutalo tan pronto como esté listo, incluso si aún no terminaste de analizar el HTML.

---

# ¿Cuándo usar cada uno?

### Sin atributos
Cuando el script debe ejecutarse inmediatamente y es esencial para la funcionalidad inicial.
**Poco recomendado.**

### `defer`

**Ideal para**:
- Scripts que necesitan interactuar con todo el DOM.
- Scripts que mantienen el orden de ejecución.
- Scripts principales de la aplicación.

### `async`

**Ideal para**:
- Scripts independientes que no dependen del DOM ni de otros scripts.
- Scripts de análisis y publicidad.

---

