**Vue** es un **framework progresivo de JavaScript** utilizado principalmente para desarrollar interfaces de usuario y aplicaciones web.

Permite construir interfaces mediante **componentes reutilizables** y puede utilizarse tanto para agregar interactividad a una parte de una página como para desarrollar aplicaciones completas.

---

## Características principales

- Arquitectura basada en [[Componentes]].
- Utiliza HTML, CSS y JavaScript.
- Permite crear **Single File Components (**`**.vue**`**)**.
- Utiliza props para comunicar datos desde un padre hacia un hijo.
- Proporciona un sistema reactivo.
- Permite manejar estado.
- Permite manejar eventos.
- Utiliza directivas como `v-if`, `v-for` y `v-model`.
- Puede utilizar **Vue Router** para navegación.
- Puede utilizar **Pinia** para manejar estado compartido.
- Puede utilizarse para desarrollar aplicaciones SPA.
    
---

# Componentes

Vue permite crear componentes mediante archivos `.vue` denominados **Single File Components**.

Un archivo puede contener:

```
COMPONENTE .vue
├── <template> → interfaz
├── <script>   → lógica
└── <style>    → estilos
```

Por ejemplo:

```
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

# `template`

La sección `<template>` define la estructura que se mostrará en la interfaz.

```
<template>
  <h1>{{ titulo }}</h1>
</template>
```

Puede utilizar datos definidos en la lógica del componente.

---

# Props

Las [[Props|props]] permiten pasar datos desde un componente padre hacia un componente hijo.

```
PADRE
  │
  │ props
  ▼
HIJO
```

En Vue pueden definirse mediante `defineProps()`.

```
defineProps<{
  nombre: string;
}>();
```

El padre puede proporcionar el valor:

```
<UsuarioCard :nombre="nombreUsuario" />
```

El hijo recibe el dato y puede utilizarlo en su interfaz.

---

# Eventos entre componentes

Un componente hijo también puede emitir eventos hacia su padre.

Conceptualmente:

```
PADRE
  │
  │ props
  ▼
HIJO

PADRE
  ▲
  │ evento
  │
HIJO
```

Vue permite definir eventos mediante mecanismos como `defineEmits()`.

Por ejemplo:

```
const emit = defineEmits(['seleccionar']);
```

El hijo puede emitir:

```
emit('seleccionar', producto);
```

El padre puede escuchar ese evento.

La idea es equivalente al patrón general:

```
padre → hijo
datos

hijo → padre
eventos
```

---

# Reactividad

Vue posee un sistema de **reactividad** que permite actualizar la interfaz cuando cambian los datos.

Conceptualmente:

```
DATO CAMBIA
    ↓
Vue detecta el cambio
    ↓
UI se actualiza
```

En Composition API pueden utilizarse mecanismos como `ref()`.

```
const contador = ref(0);
```

El dato puede utilizarse en el template:

```
<p>{{ contador }}</p>
```

Cuando cambia `contador`, Vue actualiza la interfaz.

---

# Estado

Un componente puede mantener su propio estado.

Por ejemplo:

```
const busqueda = ref('');
const cargando = ref(false);
```

Estos valores representan información que el componente necesita recordar.

Ver [[Reactividad y Estado]].

---

# Binding

Vue permite relacionar datos del componente con la interfaz.

---

## Interpolación

```
<p>{{ nombre }}</p>
```

Permite mostrar un valor.

---

## Property binding

Vue utiliza `v-bind`.

Por ejemplo:

```
<img v-bind:src="usuario.avatar">
```

También puede utilizarse su forma abreviada:

```
<img :src="usuario.avatar">
```

El `:` es una abreviación de `v-bind:`.

---

# Eventos

Vue utiliza `v-on` para escuchar eventos.

Por ejemplo:

```
<button v-on:click="guardar">
  Guardar
</button>
```

También puede utilizarse la forma abreviada:

```
<button @click="guardar">
  Guardar
</button>
```

El flujo es:

```
CLICK
 ↓
@click
 ↓
guardar()
```

---

# Two-way binding

Vue proporciona `v-model` para sincronizar un valor entre el estado y un elemento de la interfaz.

```
<input v-model="busqueda">
```

Conceptualmente:

```
ESTADO
  ↕
v-model
  ↕
INPUT
```

Si cambia el estado, cambia el input.

Si el usuario modifica el input, cambia el estado.

---

# Directivas

Vue utiliza **directivas** para agregar comportamientos especiales al HTML.

Algunas de las principales son:

```
v-if
v-else
v-for
v-bind
v-on
v-model
```

---

# Renderizado condicional

`v-if` permite mostrar contenido cuando se cumple una condición.

```
<div v-if="cargando">
  Cargando...
</div>
```

También puede utilizarse `v-else`:

```
<div v-if="cargando">
  Cargando...
</div>

<div v-else>
  Contenido cargado
</div>
```

Ver [[Renderizado]].

---

# Renderizado de listas

Vue utiliza `v-for` para generar elementos a partir de una colección.

```
<Mensaje
  v-for="mensaje in mensajes"
  :key="mensaje.id"
  :autor="mensaje.autor"
  :contenido="mensaje.contenido"
/>
```

Conceptualmente:

```
mensajes
   ↓
 v-for
   ↓
Mensaje
Mensaje
Mensaje
```

---

## `:key`

`:key` permite identificar cada elemento de la lista.

```
:key="mensaje.id"
```

Ayuda a Vue a determinar qué elementos cambiaron, fueron agregados o eliminados.

---

# Ciclo de vida

Vue proporciona hooks para ejecutar código en diferentes momentos del ciclo de vida.

Por ejemplo:

```
onMounted(() => {
  cargarProductos();
});
```

`onMounted()` permite ejecutar código después de montar el componente.

Para realizar limpieza puede utilizarse:

```
onUnmounted(() => {
  subscription.unsubscribe();
});
```

Conceptualmente:

```
MONTAJE
→ onMounted()

DESMONTAJE
→ onUnmounted()
```

También existen mecanismos como `watch()` para reaccionar a cambios en determinados datos.

Por ejemplo:

```
watch(
  () => props.productoId,
  nuevoId => {
    cargarProducto(nuevoId);
  }
);
```

Ver [[Ciclo de Vida de Componentes]].

---

# Routing

Vue puede utilizar **Vue Router** para manejar la navegación entre vistas.

Conceptualmente:

```
URL
 ↓
Vue Router
 ↓
Componente
```

Puede trabajar con rutas como:

```
/login
/productos
/productos/:id
```

Entre sus mecanismos se encuentran:

```
router.push()
→ navegar

useRoute()
→ obtener información de la ruta actual
```

Por ejemplo:

```
router.push('/productos');
```

permite navegar hacia `/productos`.

Ver [[Routing]].

---

# Servicios y lógica reutilizable

Vue no utiliza un sistema de servicios igual al de Angular.

La lógica reutilizable puede separarse mediante:

- Funciones.
- Módulos.
- **Composables**.
    
Conceptualmente:

```
COMPONENTE
    ↓
FUNCIÓN / COMPOSABLE
    ↓
BACKEND / API
```

Esto permite evitar que toda la lógica quede dentro del componente.

---

# Estado compartido

Para aplicaciones que necesitan compartir estado entre varios componentes puede utilizarse **Pinia**.

Conceptualmente:

```
ESTADO COMPARTIDO
      │
 ┌────┼─────┐
 ▼    ▼     ▼
Header Menu Perfil
```

De esta forma varios componentes pueden utilizar los mismos datos.

---

# Esquema general

```
VUE
│
├── Componentes
│   └── archivos .vue
│
├── Props
│   └── defineProps()
│
├── Eventos
│   └── defineEmits()
│
├── Reactividad
│   └── ref()
│
├── Binding
│   ├── {{ }}
│   ├── v-bind / :
│   ├── v-on / @
│   └── v-model
│
├── Directivas
│   ├── v-if
│   ├── v-else
│   └── v-for
│
├── Renderizado
│   ├── v-if
│   └── v-for + :key
│
├── Ciclo de vida
│   ├── onMounted
│   └── onUnmounted
│
├── Routing
│   └── Vue Router
│
└── Lógica / estado compartido
    ├── composables
    └── Pinia
```

---

