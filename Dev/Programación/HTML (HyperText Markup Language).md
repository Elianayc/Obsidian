
**HTML** es un lenguaje de marcado utilizado para definir la **estructura y organización del contenido de una página web**.

Fue creado bajo la especificación de la **W3C (World Wide Web Consortium)** y permite que los navegadores interpreten una estructura formada por identificadores llamados **etiquetas (tags)** para generar un documento web.

HTML no es un lenguaje de programación, sino un **lenguaje de marcado**, ya que utiliza etiquetas para describir cómo está organizado el contenido.

---

## Función principal

Define la **estructura y organización del contenido** de un documento web.

HTML es un lenguaje de marcado que permite que los navegadores interpreten una estructura formada por identificadores llamados **etiquetas**, generando como resultado un documento web.

HTML funciona como la base estructural de una página, organizando sus diferentes elementos.

---

## Concepto de hipertexto

El concepto de **hipertexto** hace referencia a las características que permiten relacionar un documento con otros contenidos.

Aunque una página web pueda verse como un documento simple para el usuario, internamente está formada por instrucciones que permiten agregar funcionalidades como:

- Navegación dentro del mismo documento.
- Enlaces hacia otros documentos web.
- Vinculación entre diferentes recursos.

---

## Etiquetas HTML

Las etiquetas HTML son identificadores que permiten definir la estructura del documento.

Se escriben utilizando **corchetes angulares**:
`<etiqueta>`

Generalmente deben utilizarse en pares:
`<etiqueta>Contenido</etiqueta>`

Este mecanismo permite:
- Delimitar cadenas de texto.
- Contener otros elementos.
- Crear estructuras anidadas.
- Formar jerarquías dentro del documento.

---

## Elementos HTML
Cada par de etiquetas se conoce como un **elemento HTML**.

Los elementos pueden contener:
- Texto.
- Otros elementos HTML.
- Atributos.

**Ejemplo**:
```html
<h1>Título principal</h1>
```

En este caso:
- `<h1>` indica que el contenido es un encabezado.
- `Título principal` es el contenido del elemento.
- `</h1>` indica el cierre del elemento.

---

## Anidamiento y jerarquía

HTML permite colocar elementos dentro de otros elementos, formando una estructura jerárquica.

**Ejemplo**:
```html
<div>
    <p>Texto dentro de un párrafo</p>
</div>
```

En este caso, el elemento `<p>` está contenido dentro del elemento `<div>`.

Esta posibilidad permite crear subestructuras dentro del documento web.

---

## Atributos HTML
Los elementos HTML suelen presentar **atributos**, que agregan características adicionales al elemento.

Los atributos son interpretados por el navegador y pueden afectar aspectos como:
- Posición.
- Tamaño.
- Visibilidad.
- Comportamiento del elemento.

El modo en que un atributo modifica un elemento depende del tipo de etiqueta utilizada.

---

## HTML y la presentación visual
Aunque existen etiquetas que pueden modificar ciertos aspectos visuales, el objetivo principal de HTML es **estructurar los datos**.

El uso correcto de las etiquetas permite que otras tecnologías, como CSS, puedan disponer de las distintas partes del documento HTML sin generar efectos indeseados.

Por ejemplo, es posible indicarle a HTML que una cadena de texto representa un encabezado mediante la etiqueta correspondiente.

Esto no solo modifica su apariencia, sino que también le da un significado dentro de la estructura del documento.

Si un texto solamente tiene apariencia de encabezado pero no fue definido como tal mediante una etiqueta, otras herramientas no podrán identificarlo correctamente.

---

## Estructura básica de un documento HTML
Un documento HTML básico presenta una estructura jerárquica donde pueden escribirse textos y anidarse otras etiquetas.

**Ejemplo**:
```html
<!DOCTYPE html>
<html>

<head>
    <title>Título de la página</title>
</head>

<body>
    Aquí se escribe texto y/o se anidan otras etiquetas.
</body>

</html>
```

---

## Resumen

|Concepto|Función|
|---|---|
|**HTML**|Define la estructura de un documento web|
|**Etiquetas**|Identifican y organizan los elementos del documento|
|**Elementos**|Formados por etiquetas y contenido|
|**Atributos**|Agregan características adicionales a los elementos|
|**Anidamiento**|Permite crear estructuras jerárquicas|

---

#Programación  
#ProgramaciónIII