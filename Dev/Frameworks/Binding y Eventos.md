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

```html
<h2>{{ titulo }}</h2>
```

---

### Property binding

Permite asignar valores dinámicos a propiedades de elementos HTML o componentes.

```HTML
<img [src]="usuario.avatar">
```

La diferencia es:

```HTML
<img src="usuario.avatar">
```

→ `"usuario.avatar"` se interpreta como texto literal.

```HTML
<img [src]="usuario.avatar">
```

→ `usuario.avatar` se interpreta como un valor dinámico.

---

### Event binding

Permite responder a acciones del usuario, como hacer clic, presionar una tecla o modificar un campo.

```HTML
<button (click)="enviar()">Enviar</button>
```

El evento del DOM ejecuta una función del componente.

---

### Two-way binding

Permite sincronizar el estado y la interfaz en ambas direcciones:

**Estado → UI:** el estado actualiza el elemento.

**UI → Estado:** las acciones del usuario actualizan el estado.

En Angular se utiliza, por ejemplo:

```HTML
<input [(ngModel)]="busqueda">
```

Esto combina **property binding + event binding**.

En React se utiliza habitualmente un **controlled component**, donde el estado es la fuente de verdad:

```Javascript
<input
  value={busqueda}
  onChange={e => setBusqueda(e.target.value)}
/>
```

En Vue se utiliza:

```HTML
<input v-model="busqueda">
```

React no utiliza una sintaxis específica de two-way binding, sino que mantiene explícitamente el flujo de datos mediante estado y eventos.

---

