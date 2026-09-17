**Vue** es un **framework progresivo de JavaScript** utilizado principalmente para desarrollar **interfaces de usuario y aplicaciones web**.

Permite construir interfaces mediante **componentes reutilizables** y puede utilizarse tanto para incorporar interactividad en partes pequeñas de una página como para desarrollar aplicaciones completas.

---

## Características principales

- Arquitectura basada en **componentes**.
- Utiliza **HTML, CSS y JavaScript**.
- Permite crear componentes mediante **Single File Components (`.vue`)**.
- Permite recibir datos desde un componente padre mediante **`defineProps()`**.
- Permite renderizar **listas** mediante `v-for`.
- Utiliza `:key` para identificar los elementos de una lista.
- Permite realizar **renderizado condicional** mediante `v-if` y `v-else`.
- Facilita la creación de interfaces **interactivas y reactivas**.
- Puede utilizarse para desarrollar aplicaciones web de una sola página (**SPA**).
- Puede utilizar **Vue Router** para implementar la navegación entre vistas.

---

## Componentes

Los componentes Vue suelen utilizar **Single File Components (`.vue`)**, que permiten organizar en un mismo archivo la estructura, lógica y estilos de un componente.

```vue
<template>
  <div class="mensaje">
    <span>{{ autor }}</span>
    <p>{{ contenido }}</p>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  autor: string;
  contenido: string;
}>();
</script>
```

---

## Props

Las **props** permiten pasar datos desde un componente padre hacia un componente hijo.

```
Componente padre
      ↓
    props
      ↓
Componente hijo
```

En Vue pueden definirse mediante `defineProps()`.

---

## Renderizado de listas

Vue utiliza `v-for` para generar elementos a partir de una colección:

```html
<Mensaje
  v-for="msg in mensajes"
  :key="msg.id"
  :autor="msg.autor"
  :contenido="msg.contenido"
/>
```

El atributo **`:key`** permite identificar cada elemento y ayuda al framework a actualizar correctamente la lista.

---

## Renderizado condicional

Permite mostrar elementos dependiendo de una condición mediante `v-if` y `v-else`.

``` html
<div v-if="cargando">
  Cargando...
</div>
<div v-else>
  Contenido cargado
</div>
```

---

## Routing

Vue puede utilizar **Vue Router** para gestionar la navegación entre diferentes vistas de una aplicación SPA.

Permite trabajar con rutas como:

```
/login
/chat
/chat/:id
```

También permite navegar mediante `router.push()` y obtener parámetros de la URL mediante `useRoute()`.

---

## Ejemplo

Una aplicación de productos puede utilizar componentes Vue independientes para representar el **buscador, las tarjetas de productos y el carrito de compras**, combinándolos para construir la interfaz completa.

---
