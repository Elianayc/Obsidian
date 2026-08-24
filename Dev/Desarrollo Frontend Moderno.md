## ¿Por qué existen los frameworks de frontend?

Con **HTML, CSS y JavaScript puro** se pueden construir interfaces, pero a medida que una aplicación crece aparecen problemas:

- Hay que actualizar manualmente el **DOM** cuando cambian los datos.
- Se mezclan **lógica, presentación y manipulación del DOM**.
- Reutilizar elementos implica copiar y pegar HTML.
- Es difícil mantener sincronizados los datos con lo que se muestra.

Los frameworks resuelven estos problemas proporcionando:

- **Estructura:** una forma clara de organizar el código.
- **Componentes:** unidades reutilizables que encapsulan HTML, lógica y estilo.
- **Reactividad:** la interfaz se actualiza automáticamente cuando cambian los datos.

---

# Componentes

Un **componente** es una pieza reutilizable e independiente de la interfaz que encapsula **estructura, lógica y, opcionalmente, estilo**.

Una aplicación puede organizarse como un **árbol de componentes**:

```
App
├── Header
│   ├── Logo
│   └── NavMenu
├── Sidebar
│   ├── ConversacionItem
│   └── ConversacionItem
└── Main
    ├── MensajeList
    └── CuadroDeTexto
```

### Características de un buen componente

- **Una responsabilidad:** hace una cosa y la hace bien.
- **Reutilizable:** funciona en distintos contextos y con distintos datos.
- **Encapsulado:** sus detalles internos no afectan a quien lo utiliza.
- **Predecible:** ante el mismo input produce el mismo output.

Un componente funciona de manera similar a una **función**: recibe parámetros (_props_), ejecuta lógica interna y devuelve una interfaz renderizada.

---

# Props: datos de padre a hijo

Las **props** permiten pasar datos de un componente padre a uno hijo.

El flujo es **unidireccional**, de arriba hacia abajo:

```
App
 ↓ props
ConversacionList
 ↓ props
ConversacionItem
```

Esto permite:

- Hacer el código más predecible.
- Rastrear fácilmente de dónde proviene cada dato.
- Evitar que los componentes hijos modifiquen directamente los datos del padre.

Si un hijo necesita comunicar algo al padre, utiliza **eventos**.

Esta filosofía es compartida por **Angular, React y Vue**.

---

# Componentes en Angular, React y Vue

|Framework|Forma de definir un componente|
|---|---|
|**Angular**|Clase con decorador `@Component`|
|**React**|Función que devuelve JSX|
|**Vue**|Single File Component (`.vue`)|

### Angular

```
@Component({
  selector: 'app-mensaje',
  template: `
    <div class="mensaje">
      <span>{{ autor }}</span>
      <p>{{ contenido }}</p>
    </div>
  `
})
export class MensajeComponent {
  @Input() autor: string = '';
  @Input() contenido: string = '';
}
```

### React

```
function Mensaje({
  autor,
  contenido
}: {
  autor: string;
  contenido: string
}) {
  return (
    <div className="mensaje">
      <span>{autor}</span>
      <p>{contenido}</p>
    </div>
  );
}
```

### Vue

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

# Renderizado de listas y condicionales

Son patrones presentes prácticamente en cualquier componente.

### Renderizado de listas

Permite mostrar un elemento por cada elemento de un array.

- **Angular:** `*ngFor` + `trackBy`
- **React:** `.map()` + `key`
- **Vue:** `v-for` + `:key`

### Renderizado condicional

Permite mostrar elementos únicamente cuando se cumple una condición.

- **Angular:** `*ngIf`
- **React:** `if` / operador ternario
- **Vue:** `v-if` / `v-else`

### `key` / `trackBy`

Permite al framework identificar qué elemento de una lista cambió y actualizar solamente ese nodo del DOM, evitando volver a renderizar toda la lista.

---

# ¿Cuándo crear un componente?

Conviene extraer un componente cuando:

- **Se repite:** el mismo bloque HTML aparece varias veces.
- **Es demasiado grande:** más de aproximadamente 150 líneas puede indicar varias responsabilidades.
- **Tiene lógica propia:** posee estado o comportamiento propio.
- **Es reutilizable:** puede utilizarse en distintos contextos con diferentes datos.

### Ejemplo

En lugar de un único `ChatComponent` que haga todo:

```
ChatComponent
├── lista de conversaciones
├── cada ítem
├── buscador
└── panel de mensajes
```

Se separan responsabilidades:

```
ChatComponent
├── ConversacionListComponent
│   └── ConversacionItemComponent
├── BuscadorComponent
└── MensajesPanelComponent
```

**Regla práctica:** si para describir lo que hace un componente necesitás decir que hace una cosa **“y”** otra, probablemente convenga dividirlo.

---

# Routing en una SPA

Una **Single Page Application (SPA)** permite navegar entre pantallas sin recargar toda la página.

El **router** cambia el componente mostrado según la URL sin realizar una nueva carga completa desde el servidor.

La URL sigue siendo importante porque permite:

- Compartir enlaces a pantallas específicas.
- Utilizar correctamente el botón **Atrás** del navegador.
- Recargar una pantalla manteniendo su ruta.

### Conceptos principales

|Concepto|Descripción|
|---|---|
|**Ruta**|Asociación entre una URL y un componente|
|**Router outlet**|Lugar donde se monta el componente activo|
|**Link / navigate**|Cambiar de ruta sin recargar la página|
|**Parámetros de ruta**|Valores dinámicos, por ejemplo `/conversaciones/:id`|
|**Guard**|Lógica que determina si se puede acceder a una ruta|

---

# Routing en Angular, React y Vue

|Concepto|Angular|React|Vue|
|---|---|---|---|
|**Definir rutas**|`Routes[]`|`<Routes>` JSX|Array de objetos|
|**Navegar**|`router.navigate()`|`useNavigate()`|`router.push()`|
|**Parámetro URL**|`ActivatedRoute`|`useParams()`|`useRoute()`|
|**Componente**|`@Component`|Función + JSX|`.vue` SFC|
|**Props**|`@Input()`|Parámetros de función|`defineProps()`|
|**Lista**|`*ngFor` + `trackBy`|`.map()` + `key`|`v-for` + `:key`|
|**Condicional**|`*ngIf`|`if` / ternario|`v-if` / `v-else`|