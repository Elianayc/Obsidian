Angular incluye un sistema de **routing** para asociar URLs con componentes.

El flujo básico es:

```
URL
 ↓
ROUTER
 ↓
COMPONENTE
```

---

## `Routes`

Las rutas pueden definirse mediante un arreglo de tipo `Routes`.

```typescript
export const routes: Routes = [
  { path: 'one', component: ComponentOneComponent },
  { path: 'two', component: ComponentTwoComponent }
];
```

Cada objeto relaciona un `path` con un componente.

```
/one → ComponentOneComponent
/two → ComponentTwoComponent
```

---

## Redirección

```typescript
{
  path: '',
  pathMatch: 'full',
  redirectTo: '/one'
}
```

Indica que cuando la ruta está vacía se debe redirigir a `/one`.

---

## Wildcard

```typescript
{
  path: '**',
  redirectTo: '/one'
}
```

`**` representa cualquier ruta que no haya coincidido con las anteriores.

Puede utilizarse como ruta de respaldo.

---

# `router-outlet`

`router-outlet` indica dónde debe mostrar Angular el componente correspondiente a la ruta activa.

```html
<router-outlet></router-outlet>
```

Conceptualmente:

```
AppComponent
│
├── navegación
│
└── router-outlet
        ↓
   componente activo
```

---

# `routerLink`

Permite navegar directamente desde el HTML.

```html
<a routerLink="/one">Ir a One</a>
```

El HTML indica directamente cuál es la ruta destino.

```
routerLink
→ navegación desde HTML
```

---

# `Router`

`Router` permite controlar la navegación desde TypeScript.

Por ejemplo:

```typescript
constructor(private router: Router) {}
```

y posteriormente:

```typescript
irAOne() {
  this.router.navigate(['/one']);
}
```

El HTML puede llamar a esa función:

```html
<button (click)="irAOne()">Ir a One</button>
```

El flujo es:

```
CLICK
 ↓
irAOne()
 ↓
router.navigate()
 ↓
/one
```

---

## `routerLink` vs `router.navigate()`

### `routerLink`

```html
<a routerLink="/one">
```

Se utiliza cuando la navegación puede definirse directamente en HTML.

### `router.navigate()`

```typescript
this.router.navigate(['/one']);
```

Se utiliza cuando la navegación se realiza desde TypeScript.

Esto permite ejecutar lógica antes de navegar.

---

## Machete

```
routerLink = navegación desde HTML
router.navigate() = navegación desde TypeScript
```

---

# `ActivatedRoute`

`ActivatedRoute` permite acceder a información de la ruta actualmente activa.

Por ejemplo, una URL podría contener un identificador:

```
/equipos/10
```

Ese `10` puede ser un **parámetro de ruta**.

`ActivatedRoute` permite obtener información de esos parámetros desde el componente.

---

# Guards

Los **Guards** permiten controlar si determinada navegación está permitida.

Conceptualmente:

```
intento navegar
      ↓
    GUARD
   ↙     ↘
permite  bloquea
```

Su implementación concreta puede estudiarse cuando sea necesario utilizarla.

---
