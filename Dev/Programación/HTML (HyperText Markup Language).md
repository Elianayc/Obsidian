
**HTML** es un lenguaje de marcado utilizado para definir la **estructura y organización del contenido de una página web**.

Fue creado bajo la especificación de la **W3C (World Wide Web Consortium)** y permite que los navegadores interpreten una estructura formada por identificadores llamados **etiquetas (tags)** para generar un documento web.

HTML no es un lenguaje de programación, sino un **lenguaje de marcado**, ya que utiliza etiquetas para describir cómo está organizado el contenido.

---

## Función principal
Define la **estructura y el contenido** de una página web.

HTML funciona como el **esqueleto** de una aplicación web, organizando los diferentes elementos que forman la interfaz.

**Permite crear**:
- Títulos.
- Párrafos.
- Imágenes.
- Enlaces.
- Formularios.
- Secciones de contenido.
- Componentes estructurales.

HTML proporciona la base sobre la cual se aplican los estilos y comportamientos de la aplicación.

---

## Concepto de hipertexto

El término **hipertexto** hace referencia a la capacidad de un documento HTML de relacionarse con otros contenidos mediante enlaces.

Aunque visualmente una página pueda parecer un documento simple, internamente está formada por instrucciones que permiten:

- Navegar dentro del mismo documento.
- Acceder a otros documentos web.
- Crear vínculos entre diferentes recursos.

---

## Elementos HTML
Un par de etiquetas HTML de apertura y cierre forman un **elemento HTML**.

Los elementos pueden contener:
- Texto.
- Otros elementos HTML.
- Atributos.

**Ejemplo**:
```html
<h1>Título principal</h1>
````

En este caso:
- `<h1>` es la etiqueta de apertura.
- `Título principal` es el contenido del elemento.
- `</h1>` es la etiqueta de cierre.

---

## Anidamiento y jerarquía
HTML permite colocar elementos dentro de otros elementos, formando una estructura jerárquica.

**Ejemplo**:
```html
<div>
    <p>Texto dentro de un párrafo</p>
</div>
```

En este caso, el elemento `<p>` se encuentra dentro del elemento `<div>`.

Esta organización permite construir la estructura del documento web y representar la relación entre sus diferentes partes.

---

## Atributos HTML
Los elementos HTML pueden incluir **atributos**, que agregan información adicional o modifican ciertas características del elemento.

**Ejemplo**:
```html
<a href="https://www.google.com">Ir a Google</a>
```

El atributo `href` indica la dirección a la que apunta el enlace.

Los atributos pueden definir:
- Identificación de elementos.
- Comportamiento.
- Relación con otros recursos.
- Características del elemento.

---

## HTML y la presentación visual
Aunque algunas etiquetas pueden influir en la apariencia del contenido, el objetivo principal de HTML es **estructurar la información**.

La presentación visual debe realizarse principalmente mediante **CSS**.

Una correcta estructura HTML permite que otras tecnologías puedan acceder y modificar diferentes partes del documento de manera organizada.

Ejemplo:
```html
<h1>Mi título</h1>
```

HTML indica que el texto representa un encabezado.

Luego CSS puede modificar:
- Color.
- Tamaño.
- Tipografía.
- Posición.

---

## Importancia del uso correcto de etiquetas
Utilizar las etiquetas adecuadas permite que el documento tenga una estructura semántica correcta.

Por ejemplo, un texto que visualmente parece un título pero que no está definido con una etiqueta de encabezado (`<h1>`, `<h2>`, etc.) no será reconocido correctamente como un encabezado por otras herramientas.

Esto afecta:
- Accesibilidad.
- Organización del documento.
- Mantenimiento del código.
- Interpretación por parte de navegadores y herramientas externas.

---

## Estructura básica de un documento HTML
Un documento HTML posee una estructura jerárquica donde se incluyen el contenido y las diferentes etiquetas que forman la página.

**Ejemplo**:
```
<!DOCTYPE html>
<html>

<head>
    <title>Título de la página</title>
</head>

<body>
    Aquí se escribe texto y se agregan otras etiquetas.
</body>

</html>
```

---

## Resumen

|Concepto|Función|
|---|---|
|**HTML**|Define la estructura y contenido de una página web|
|**Etiquetas**|Indican la función de cada elemento|
|**Elementos**|Son conjuntos formados por etiquetas y contenido|
|**Atributos**|Agregan información adicional a los elementos|
|**CSS**|Define la presentación visual|
|**JavaScript**|Agrega comportamiento e interacción|

---
#Programación 
#ProgramaciónIII 