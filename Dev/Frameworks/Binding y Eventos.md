El **binding** es el mecanismo que permite sincronizar los datos del componente con la interfaz y responder a las acciones del usuario.

---

### Tipos de binding

|         Tipo         |  Dirección   |                            Función                             |
| :------------------: | :----------: | :------------------------------------------------------------: |
|  **Interpolación**   | Estado → DOM |                  Mostrar valores como texto.                   |
| **Property binding** | Estado → DOM | Asignar valores dinámicos a propiedades del DOM o componentes. |
|  **Event binding**   | DOM → Estado |     Ejecutar código cuando ocurre una acción del usuario.      |
| **Two-way binding**  | Estado ↔ DOM |    Sincronizar bidireccionalmente el estado y la interfaz.     |

---

### Interpolación

Permite mostrar el valor de una variable dentro de la interfaz.

**Angular:**

```HTML
<h2>{{ titulo }}</h2>
```

```Javascript
titulo = 'Lista de productos';
```

**React:**

```HTML
const titulo = 'Lista de productos';

return (
  <h2>{titulo}</h2>
);
```

**Vue:**

```HTML
<h2>{{ titulo }}</h2>
```

```Javascript
const titulo = ref('Lista de productos');
```

---

### Property binding

Permite asignar valores dinámicos a propiedades de elementos HTML o componentes.

**Angular:**

```HTML
<img [src]="usuario.avatar">
```

```Typescript
usuario = {
  avatar: 'foto.jpg'
};
```

**React:**

```Javascript
const usuario = {
  avatar: 'foto.jpg'
};

return (
  <img src={usuario.avatar} />
);
```

**Vue:**

```HTML
<img :src="usuario.avatar">
```

```Javascript
const usuario = {
  avatar: 'foto.jpg'
};
```

La diferencia importante es que el valor se obtiene de una **variable** y no se interpreta como texto literal.

---

### Event binding

Permite responder a acciones del usuario, como hacer clic, presionar una tecla o modificar un campo.

**Angular:**

```HTML
<button (click)="enviar()">Enviar</button>
```

```Typecript
enviar() {
  console.log('Mensaje enviado');
}
```

**React:**

```Javascript
function enviar() {
  console.log('Mensaje enviado');
}

return (
  <button onClick={enviar}>Enviar</button>
);
```

**Vue:**

```HTML
<button @click="enviar">Enviar</button>
```

```Javascript
function enviar() {
  console.log('Mensaje enviado');
}
```

En los tres casos, el evento del usuario ejecuta una función del componente.

---

### Two-way binding

Permite sincronizar el estado y la interfaz en ambas direcciones:

**Estado → UI:** el estado actualiza el elemento.

**UI → Estado:** las acciones del usuario actualizan el estado.

#### Angular

```HTML
<input [(ngModel)]="busqueda">

<p>Buscando: {{ busqueda }}</p>
```

```Typescript
busqueda = '';
```

`[(ngModel)]` realiza la sincronización en ambas direcciones.

#### React

React no tiene una sintaxis específica de two-way binding. Se utiliza un **controlled component**, donde el estado es la fuente de verdad:

```Javascript
const [busqueda, setBusqueda] = useState('');

return (
  <>
    <input
      value={busqueda}
      onChange={e => setBusqueda(e.target.value)}
    />

    <p>Buscando: {busqueda}</p>
  </>
);
```

- `value={busqueda}` → **Estado → UI**
- `onChange={...}` → **UI → Estado**

#### Vue

```HTML
<input v-model="busqueda">

<p>Buscando: {{ busqueda }}</p>
```

```Javascript
const busqueda = ref('');
```

`v-model` combina ambas direcciones en una sola expresión.

---

**Idea clave:** Angular y Vue ofrecen una sintaxis específica para two-way binding (`[(ngModel)]` y `v-model`), mientras que React lo implementa explícitamente mediante **estado + eventos**.