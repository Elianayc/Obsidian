**React** es una **biblioteca de JavaScript** desarrollada originalmente por Facebook, actualmente Meta, para crear **interfaces de usuario**.

Se utiliza principalmente en el Frontend y permite construir interfaces mediante **componentes reutilizables**.

---

## Características principales

- Arquitectura basada en [[Componentes]].
- Los componentes suelen definirse como funciones que devuelven **JSX**.
- Utiliza **props** para pasar datos de un componente padre a un hijo.
- Permite manejar **estado** dentro de los componentes.
- Actualiza la interfaz cuando cambia el estado.
- Permite manejar eventos del usuario.
- Renderiza listas mediante `.map()`.
- Utiliza `key` para identificar elementos de una lista.
- Permite realizar renderizado condicional.
- Utiliza **hooks** para acceder a diferentes funcionalidades.
- Puede utilizarse para desarrollar aplicaciones **SPA**.
- Puede incorporar routing mediante **React Router**.

---

# Componentes

Un [[Componentes|componente]] React suele ser una **función que devuelve JSX**.

```
function Mensaje() {
  return (
    <div>
      <p>Hola</p>
    </div>
  );
}
```

Conceptualmente:

```
Componente
    ↓
devuelve JSX
    ↓
interfaz
```

Un componente puede recibir datos, mantener estado, responder a eventos y utilizar otros componentes.

Por ejemplo:

```
function Mensaje({ autor, contenido }) {
  return (
    <div className="mensaje">
      <span>{autor}</span>
      <p>{contenido}</p>
    </div>
  );
}
```

---

# JSX

**JSX** es una sintaxis utilizada por React que permite escribir una estructura similar a HTML dentro de JavaScript.

Por ejemplo:

```
const elemento = <h1>Hola</h1>;
```

También permite insertar expresiones de JavaScript mediante `{ }`:

```
const nombre = 'Ana';

return (
  <p>Hola {nombre}</p>
);
```

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

Por ejemplo:

```
<Mensaje
  autor="Ana"
  contenido="Hola"
/>
```

El hijo puede recibir esos datos:

```
function Mensaje({ autor, contenido }) {
  return (
    <div>
      <strong>{autor}</strong>
      <p>{contenido}</p>
    </div>
  );
}
```

Las props no deberían ser modificadas directamente por el componente hijo.

---

# Eventos

React permite responder a eventos del usuario.

Por ejemplo:

```
function guardar() {
  console.log('Guardado');
}

return (
  <button onClick={guardar}>
    Guardar
  </button>
);
```

El flujo es:

```
usuario hace clic
       ↓
    onClick
       ↓
    guardar()
```

Los nombres de eventos en JSX suelen escribirse utilizando **camelCase**.

Por ejemplo:

```
onClick
onChange
onSubmit
```

---

# Estado

El [[Reactividad y Estado|estado]] representa información que el componente necesita recordar.

En componentes funcionales puede manejarse mediante el hook `useState`.

```
const [contador, setContador] = useState(0);
```

En este ejemplo:

```
contador
→ valor actual

setContador
→ función utilizada para cambiarlo
```

Por ejemplo:

```
function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <button onClick={() => setContador(contador + 1)}>
      {contador}
    </button>
  );
}
```

El flujo es:

```
CLICK
  ↓
setContador(...)
  ↓
cambia el estado
  ↓
React actualiza la interfaz
```

---

# Reactividad

Cuando cambia el estado de un componente, React vuelve a evaluar el componente y actualiza la parte necesaria de la interfaz.

Conceptualmente:

```
ESTADO CAMBIA
      ↓
React detecta el cambio
      ↓
se vuelve a renderizar
      ↓
UI actualizada
```

React utiliza un **Virtual DOM** para comparar representaciones de la interfaz y aplicar al DOM real los cambios necesarios.

---

# Binding

React no utiliza la misma sintaxis específica de binding que Angular.

Los valores pueden incorporarse en JSX mediante `{ }`.

```
const nombre = 'Ana';

return (
  <p>{nombre}</p>
);
```

También pueden utilizarse expresiones para establecer propiedades:

```
<img src={usuario.avatar} />
```

---

# Formularios y estado

Es habitual que el estado mantenga el valor de un campo.

```
const [busqueda, setBusqueda] = useState('');
```

El valor puede vincularse al input:

```
<input
  value={busqueda}
  onChange={evento => setBusqueda(evento.target.value)}
/>
```

El flujo es:

```
ESTADO
  │
  │ value
  ▼
INPUT
  │
  │ onChange
  ▼
setBusqueda()
  │
  ▼
ESTADO
```

React no proporciona una sintaxis específica equivalente al two-way binding de Angular o Vue. La comunicación se expresa explícitamente mediante **estado + evento**.

---

# Renderizado condicional

React permite mostrar contenido dependiendo de una condición.

Por ejemplo:

```
{cargando && <div>Cargando...</div>}
```

También pueden utilizarse expresiones condicionales:

```
{cargando
  ? <div>Cargando...</div>
  : <div>Contenido cargado</div>
}
```

Ver [[Renderizado]].

---

# Renderizado de listas

Las listas suelen generarse utilizando `.map()`.

```
{mensajes.map(mensaje => (
  <Mensaje
    key={mensaje.id}
    autor={mensaje.autor}
    contenido={mensaje.contenido}
  />
))}
```

Conceptualmente:

```
mensajes
   ↓
 .map()
   ↓
Mensaje
Mensaje
Mensaje
```

---

## `key`

`key` permite identificar cada elemento de una lista.

```
key={mensaje.id}
```

Esto ayuda a React a determinar qué elementos fueron agregados, eliminados o modificados.

---

# Ciclo de vida y `useEffect`

En los componentes funcionales modernos, React puede utilizar el hook `useEffect` para ejecutar determinados efectos relacionados con el ciclo de vida del componente.

Por ejemplo:

```
useEffect(() => {
  cargarProductos();
}, []);
```

Puede utilizarse para ejecutar una operación cuando se monta el componente.

También puede reaccionar a cambios:

```
useEffect(() => {
  cargarProducto(productoId);
}, [productoId]);
```

En este caso se ejecuta cuando cambia `productoId`.

También puede devolver una función de limpieza:

```
useEffect(() => {
  const subscription = servicio.subscribe();

  return () => {
    subscription.unsubscribe();
  };
}, []);
```

La función retornada permite realizar limpieza cuando corresponde.

Ver [[Ciclo de Vida de Componentes]].

---

# Routing

React no incluye un sistema completo de routing dentro de su núcleo.

Puede utilizarse una biblioteca como **React Router**.

Conceptualmente:

```
URL
 ↓
React Router
 ↓
Componente
```

Algunos mecanismos habituales son:

```
<Routes>
→ contiene las rutas

<Route>
→ define una ruta

useNavigate()
→ permite navegar desde JavaScript

useParams()
→ permite obtener parámetros de la URL
```

Por ejemplo, pueden existir rutas como:

```
/login
/productos
/productos/:id
```

Ver [[Routing]].

---

# Servicios y lógica reutilizable

React no posee un sistema de servicios equivalente al de Angular.

La lógica puede separarse utilizando:

- Funciones.
    
- Módulos.
    
- Hooks personalizados.
    
- Context cuando es necesario compartir determinados datos.
    

Por ejemplo:

```
export function obtenerUsuarios() {
  // llamada al Backend
}
```

Un componente puede utilizar esa función sin contener directamente toda la lógica de obtención de datos.

Conceptualmente:

```
COMPONENTE
    ↓
FUNCIÓN / HOOK
    ↓
BACKEND / API
```

---

# Estado compartido

Cuando varios componentes necesitan acceder a la misma información puede utilizarse, entre otros mecanismos, **Context API**.

Conceptualmente:

```
Context
├── Header
├── Sidebar
└── Perfil
```

Esto permite compartir determinados datos sin pasarlos manualmente por todos los componentes intermedios.

---

# Esquema general

```
REACT
│
├── Componentes
│   └── funciones + JSX
│
├── Props
│   └── padre → hijo
│
├── Estado
│   └── useState
│
├── Eventos
│   ├── onClick
│   ├── onChange
│   └── onSubmit
│
├── Reactividad
│   └── estado cambia → UI se actualiza
│
├── Renderizado
│   ├── condicionales
│   └── .map() + key
│
├── Ciclo de vida / efectos
│   └── useEffect
│
├── Routing
│   └── React Router
│
└── Lógica compartida
    ├── funciones
    ├── hooks
    └── Context
```

---
