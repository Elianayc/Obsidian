Existen diferentes formas de incorporar CSS a un documento HTML.

---

## Linkear archivos externos
Utilizando la etiqueta `<link>` dentro del `<head>` del documento HTML, podemos cargar un archivo CSS que contenga las reglas para formatear nuestro documento.

La etiqueta `<link>` utiliza:
- El atributo `rel` para indicar el tipo de archivo que se está cargando. En este caso, `stylesheet`.
- El atributo `href` para indicar la ruta del archivo CSS.

**Ejemplo**:
```html
<head>
    <link rel="stylesheet" href="estilos.css">
</head>
```

---

## Definir el CSS dentro del HTML
Utilizando la etiqueta `<style>` podemos definir las reglas CSS directamente dentro del documento HTML.

```html
<head>
    <style>
        h2 {
            color: blue;
        }
    </style>
</head>
```

---

## Estilo en línea
Todas las etiquetas HTML tienen el atributo `style`.

Entre las comillas del atributo se pueden definir reglas CSS para formatear **únicamente ese elemento**.

**Ejemplo**:
```html
<h1>Un encabezado sin formato</h1>

<h2 style="color: blue;">H2 con formato CSS</h2>

<p>Párrafo sin formatear</p>

<p style="color: red;">Párrafo formateado</p>
```


---
