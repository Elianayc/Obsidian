Un **framework** es una estructura de software que proporciona herramientas, componentes, reglas y convenciones para facilitar y organizar el desarrollo de aplicaciones.

Su objetivo es ofrecer una **base predefinida** sobre la cual construir una aplicación, evitando tener que resolver desde cero problemas comunes de estructura, organización y funcionamiento.

---

## ¿Por qué utilizar un framework?

A medida que una aplicación crece, desarrollar únicamente con las herramientas básicas del lenguaje puede generar problemas de organización, reutilización y mantenimiento.

Los frameworks proporcionan:

- **Estructura:** una forma organizada de distribuir el código.
- **Componentes:** elementos reutilizables que permiten dividir la aplicación.
- **Reactividad:** actualización de la interfaz cuando cambian los datos, en frameworks de frontend.
- **Convenciones:** reglas y formas recomendadas de trabajar.
- **Herramientas:** funcionalidades que simplifican tareas habituales.
- **Mantenibilidad:** facilitan que proyectos grandes puedan evolucionar de manera organizada.

---

## Frameworks de Frontend

Los frameworks de frontend permiten construir interfaces web mediante **componentes reutilizables**, manejar datos y actualizar la interfaz de forma reactiva.

Entre las tecnologías utilizadas para este propósito se encuentran:

- [**Angular**](Angular.md) → framework de frontend desarrollado por Google.
- [**React**](React.md) → biblioteca de JavaScript para construir interfaces mediante componentes.
- [**Vue**](Vue.md) → framework progresivo de JavaScript para construir interfaces.

> **Nota:** React suele estudiarse junto con Angular y Vue como tecnología de frontend, aunque técnicamente React es una **biblioteca (library)**, mientras que Angular y Vue se consideran frameworks.

---

# Componentes

Un **componente** es una pieza reutilizable e independiente de la interfaz que encapsula **estructura, lógica y, opcionalmente, estilo**.

Una aplicación puede dividirse en un **árbol de componentes**, donde componentes grandes contienen componentes más pequeños.

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
- **Reutilizable:** puede utilizarse en distintos contextos y con distintos datos.
- **Encapsulado:** sus detalles internos no afectan a quien lo utiliza.
- **Predecible:** ante el mismo input produce el mismo resultado.

Un componente puede entenderse de forma similar a una **función**: recibe datos de entrada, ejecuta lógica interna y produce un resultado visible en la interfaz.

---

# Props: comunicación de padre a hijo

Las **props** son el mecanismo utilizado para pasar datos desde un componente padre hacia un componente hijo.

El flujo de datos es **unidireccional**, de arriba hacia abajo:

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

Una **prop no debería modificarse desde el hijo**.

Si un hijo necesita comunicar información o una acción al padre, utiliza **eventos**.

Esta filosofía es compartida por Angular, React y Vue.

---

# Renderizado de listas

El **renderizado de listas** consiste en generar un componente o elemento de interfaz por cada elemento de un array.

Los tres frameworks proporcionan mecanismos para realizarlo:

|Framework|Mecanismo|
|---|---|
|**Angular**|`*ngFor` + `trackBy`|
|**React**|`.map()` + `key`|
|**Vue**|`v-for` + `:key`|

### `key` / `trackBy`

Permite al framework identificar qué elemento de una lista cambió y actualizar solamente ese nodo del DOM, en lugar de volver a renderizar toda la lista.

---

# Renderizado condicional

Permite mostrar determinados elementos de la interfaz únicamente cuando se cumple una condición.

|Framework|Mecanismo|
|---|---|
|**Angular**|`*ngIf`|
|**React**|`if` / operador ternario|
|**Vue**|`v-if` / `v-else`|

Por ejemplo, se puede mostrar:

- Un mensaje de **“Cargando...”** mientras se obtienen datos.
- Un mensaje de **“Sin resultados”** cuando una lista está vacía.
- Una sección determinada únicamente cuando el usuario está autenticado.

---

# ¿Cuándo crear un componente?

Conviene extraer una parte de la interfaz a un componente separado cuando:

- **Se repite:** el mismo bloque HTML aparece varias veces.
- **Es demasiado grande:** puede contener más de una responsabilidad.
- **Tiene lógica propia:** posee estado o comportamiento independiente.
- **Es reutilizable:** puede utilizarse en diferentes contextos con distintos datos.

### Ejemplo

Un componente de chat que hace todo:

```
ChatComponent
├── lista de conversaciones
├── cada ítem de conversación
├── buscador
└── panel de mensajes
```

Puede dividirse en componentes con responsabilidades específicas:

```
ChatComponent
├── ConversacionListComponent
│   └── ConversacionItemComponent
├── BuscadorComponent
└── MensajesPanelComponent
```

**Regla práctica:** si para describir lo que hace un componente necesitás utilizar la palabra **“y”**, probablemente tenga más de una responsabilidad y convenga dividirlo.

---

# Routing

El **routing** permite determinar qué componente debe mostrarse según la URL.

En una **Single Page Application (SPA)**, la navegación entre pantallas normalmente no requiere recargar toda la página. El router cambia el componente mostrado según la ruta.

### ¿Por qué la URL sigue siendo importante?

Permite:

- Compartir enlaces a pantallas específicas.
- Utilizar correctamente el botón **Atrás** del navegador.
- Mantener una ruta específica al recargar la página.

### Conceptos principales

|Concepto|Descripción|
|---|---|
|**Ruta**|Asociación entre una URL y un componente|
|**Router outlet**|Lugar donde se monta el componente activo|
|**Link / navigate**|Permite cambiar de ruta sin recargar la página|
|**Parámetros de ruta**|Valores dinámicos dentro de la URL, por ejemplo `/conversaciones/:id`|
|**Guard**|Lógica que determina si se permite acceder a una ruta|

---

# Routing en los principales frameworks

Cada framework proporciona su propia forma de definir y utilizar rutas:

|Concepto|Angular|React|Vue|
|---|---|---|---|
|**Definir rutas**|`Routes[]`|`<Routes>`|Array de objetos|
|**Navegar**|`router.navigate()`|`useNavigate()`|`router.push()`|
|**Leer parámetros**|`ActivatedRoute`|`useParams()`|`useRoute()`|

---
