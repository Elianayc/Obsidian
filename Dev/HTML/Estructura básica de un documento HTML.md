Cuando creamos un documento HTML existen elementos que deben estar presentes para que el navegador pueda interpretarlo correctamente.

La estructura básica de un documento HTML está formada por:

- `DOCTYPE`
- `<html>`
- `<head>`
- `<body>`

---

## DOCTYPE
El primer elemento que debe aparecer en un documento HTML es:

```html
<!DOCTYPE html>
```

Su función es declarar el **tipo de documento**.

Permite indicar que el documento sigue una estructura determinada por un **DTD (Document Type Definition)**.

---

## DTD (Document Type Definition)

Un **DTD** define:
- La estructura de un documento.
- Los elementos permitidos.
- Los atributos disponibles.

Mediante esta definición se establece qué estructura tendrá el documento que estamos creando.

En este caso, se indica que el documento utiliza el estándar **HTML**.

---

# Etiqueta `<html>`

La etiqueta `<html>` define que el documento cumple con el estándar HTML.

Todo el contenido del sitio debe encontrarse dentro de:

```html
<html>
    
</html>
```

Esta etiqueta representa el elemento raíz del documento, es decir, contiene todos los demás elementos HTML.

---

# Etiqueta `<head>`

La etiqueta `<head>` representa la parte **privada** del documento.

Su contenido no se muestra directamente al usuario, sino que contiene información utilizada para la comunicación entre la página y el navegador.

Dentro de esta sección se incluyen etiquetas como:

- `<title>` → define el título de la página.
- Información de configuración del documento.
- Referencias a recursos externos.

**Ejemplo**:

```html
<head>
    <title>Hola Mundo en HTML!</title>
</head>
```

---

# Etiqueta `<body>`

La etiqueta `<body>` contiene todo el contenido visible de la página web.

Dentro de esta sección se escriben los elementos que serán mostrados al usuario:

- Textos.
- Imágenes.
- Enlaces.
- Formularios.
- Otros elementos HTML.

**Ejemplo**:

```html
<body>
    Hola Mundo en HTML!
</body>
```

---

# Estructura completa de un documento HTML

Ejemplo:

```html
<!DOCTYPE html>
<html>

<head>
    <title>Hola Mundo en HTML!</title>
</head>

<body>
    Aquí se escribe texto y/o se anidan otras etiquetas.
</body>

</html>
```

---

# Resumen

|Elemento|Función|
|---|---|
|`DOCTYPE`|Declara el tipo de documento HTML|
|`DTD`|Define la estructura y elementos permitidos del documento|
|`<html>`|Contiene todo el documento HTML|
|`<head>`|Contiene información de configuración y comunicación con el navegador|
|`<body>`|Contiene el contenido visible de la página|

---
#Programación  
#ProgramaciónIII