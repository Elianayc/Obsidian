## ¿Qué es el DOM?
El **DOM (Document Object Model)** es una de las piezas fundamentales para trabajar con JavaScript en el desarrollo web frontend.

El DOM es una **representación estructurada del documento HTML como un árbol de objetos** que puede ser manipulado utilizando JavaScript.

En esencia, es una interfaz de programación que permite a JavaScript acceder y modificar:

- El contenido.
- La estructura.
- El estilo de una página web.

Cuando el navegador carga una página web, crea un modelo de la página en memoria. Este modelo es el **DOM** y representa todos los elementos de la página como objetos que pueden ser:

- Leídos.
- Modificados.
- Añadidos.
- Eliminados.



<div style="text-align: center;">

<iframe width="560" height="315" src="https://www.youtube.com/embed/4ILE0y58J00" frameborder="0" allowfullscreen></iframe>

</div>


|                                           |                                           |
| ----------------------------------------- | ----------------------------------------- |
| ![[Pasted image 20260818151212.png\|350]] | ![[Pasted image 20260818151233.png\|363]] |

![[Pasted image 20260818151418.png|739]]

![[Pasted image 20260818151717.png]]

---

## Utilización del DOM con JavaScript

### 1. Selección de elementos
Para manipular elementos HTML, primero es necesario seleccionarlos.

Para ello se pueden utilizar funciones del objeto DOM como `getElementById`, `getElementsByClassName`, entre otras.

**Seleccionar por ID:**
```JavaScript
const titulo = document.getElementById('titulo');
```

**Seleccionar por clase:**
```JavaScript
const parrafos = document.getElementsByClassName('parrafo');
```

**Seleccionar por etiqueta:**
```JavaScript
const botones = document.getElementsByTagName('button');
```

---
### Selectores modernos

También se pueden utilizar selectores modernos, comunmente más usados:

```JavaScript
const miElemento = document.querySelector('#miId');
```

`querySelector()` devuelve el **primer elemento** que coincida con el selector.


```JavaScript
const todosLosParrafos = document.querySelectorAll('p');
```

`querySelectorAll()` devuelve **todos los elementos** que coincidan con el selector.

---

## 2. Modificación de elementos
Una vez seleccionado el elemento, podemos modificarlo.

### Cambiar el contenido
```JavaScript
titulo.textContent = 'Nuevo título';
titulo.innerHTML = 'Título con <span>formato</span>';
```

### Cambiar estilos
```JavaScript
titulo.style.color = 'blue';
titulo.style.fontSize = '24px';
```

### Manipular clases
```JavaScript
titulo.classList.add('destacado');
titulo.classList.remove('oculto');
titulo.classList.toggle('activo');
```

---

## 3. Creación y eliminación de elementos
El manejo del DOM también permite modificar la estructura del HTML agregando o eliminando elementos.

### Crear un elemento
```JavaScript
const nuevoParrafo = document.createElement('p');
nuevoParrafo.textContent = 'Este es un párrafo creado con JavaScript';
```

### Añadir el elemento al DOM
```JavaScript
document.body.appendChild(nuevoParrafo);
```

### Eliminar un elemento
```JavaScript
const elementoAEliminar = document.querySelector('.innecesario');
elementoAEliminar.parentNode.removeChild(elementoAEliminar);
```

En navegadores modernos también se puede utilizar:

```JavaScript
elementoAEliminar.remove();
```

---

Para más información ver: **[DOM documentation](https://developer.mozilla.org/en-US/docs/Web/API/Document)**

---
