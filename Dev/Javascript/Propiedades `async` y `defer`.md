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

> Descarga este script mientras sigues trabajando, pero no lo ejecutes hasta que hayas terminado de analizar toda la página.

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

> Descarga este script mientras sigues trabajando y ejecútalo tan pronto como esté listo, incluso si aún no terminaste de analizar el HTML.

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

---
