**HTML5** es la quinta versión del lenguaje HTML.

Con su aparición se incorporaron nuevos elementos y etiquetas que no solo funcionan como contenedores, sino que también permiten definir el tipo de contenido que representan.

El objetivo principal de HTML5 es mejorar la estructura de los documentos web, agregar significado al contenido y brindar soporte nativo para nuevas funcionalidades.

---

# Elementos semánticos HTML5
HTML5 incorpora etiquetas semánticas que permiten describir mejor la estructura de una página web.

A diferencia de los elementos contenedores tradicionales como `<div>`, estas etiquetas indican qué tipo de contenido contienen.

![[Pasted image 20260807160335.png]]

---

## `<section>`

Define una sección dentro de un documento.

Se utiliza para agrupar contenido relacionado dentro de una página.

**Ejemplo**:
```html
<section>
    <h2>Título de sección</h2>
    <p>Contenido relacionado.</p>
</section>
```

---

## `<nav>`

Define un bloque que contiene enlaces de navegación.

Se utiliza generalmente para menús o enlaces principales del sitio.

**Ejemplo**:
```html5
<nav>
    <a href="inicio.html">Inicio</a>
    <a href="contacto.html">Contacto</a>
</nav>
```

---

## `<article>`

Define contenido autónomo que puede existir independientemente del resto de la página.

**Ejemplos**:
- Noticias.
- Publicaciones.
- Entradas de blog.

---

## `<aside>`

Define contenido relacionado de forma secundaria con el contenido principal.

**Ejemplos**:
- Información adicional.
- Publicidad.
- Enlaces relacionados.

---

## `<main>`

Define el contenido principal o más importante del documento.

**Características**:
- Solo debe existir un elemento `<main>` por documento.
- Contiene la información central de la página.

---

## `<header>`

Define la cabecera de una página o sección.

Puede contener elementos como:
- Títulos.
- Logotipos.
- Menús.
- Información introductoria.

---

## `<footer>`

Define el pie de una página o sección.

Puede contener:
- Información del autor.
- Datos de contacto.
- Derechos de autor.
- Enlaces adicionales.

---

# Multimedia en HTML5

HTML5 incorpora soporte nativo para contenido multimedia mediante nuevos elementos.

Antes de HTML5 era común depender de plugins externos para reproducir audio y video.

---

## `<audio>`

Permite insertar archivos de audio dentro de una página web.

**Ejemplo**:
```html
<audio src="audio.mp3" controls>
    Tu navegador no implementa el elemento audio.
</audio>
```

El atributo `controls` agrega controles para que el usuario pueda:

- Reproducir.
- Pausar.
- Controlar el volumen.

---

## `<video>`

Permite insertar videos dentro de un documento HTML.

**Ejemplo**:
```html
<video src="video.mp4" controls>
    Tu navegador no implementa el elemento video.
</video>
```

También permite agregar mensajes alternativos para navegadores que no soporten este elemento.

---

# Mejoras en formularios HTML5
HTML5 incorpora nuevas funcionalidades para los formularios.

## Nuevos valores de atributos

**Ejemplo**:
```
<input type="email">
```

Permite indicar que el campo espera una dirección de correo electrónico.

También incorpora mejoras como:
- Validaciones automáticas.
- Nuevos tipos de controles.
- Nuevos atributos para facilitar el ingreso de datos.

---

## Enctype text/plain

HTML5 incorpora el valor:
```html
text/plain
```

para el atributo `enctype`.

Este atributo define cómo se codifican los datos enviados mediante un formulario.

Otros valores posibles son:
- `application/x-www-form-urlencoded`
- `multipart/form-data`
- `text/plain`

---
