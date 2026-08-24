**Angular** es un **framework de desarrollo web** basado en **[[TypeScript]]**, desarrollado por Google.

Se utiliza principalmente para crear aplicaciones **Frontend completas, estructuradas y escalables**, especialmente aplicaciones de una sola página (**SPA**).

---

## Características principales

- Arquitectura basada en **componentes**.
- Utiliza **TypeScript**.
- Los componentes encapsulan **estructura, lógica y estilo** de una parte de la interfaz.
- Utiliza **`@Component`** para definir componentes.
- Permite recibir datos desde un componente padre mediante **`@Input()`**.
- Permite **renderizar listas** mediante herramientas como `*ngFor`.
- Permite **renderizado condicional** mediante `*ngIf`.
- Incluye un sistema de **routing** para navegar entre diferentes vistas sin recargar la página.
- Permite manejar **formularios**.
- Permite realizar **solicitudes HTTP** para comunicarse con APIs del Backend.
- Facilita la creación de aplicaciones **SPA (Single Page Application)**.
- Proporciona una estructura definida para organizar aplicaciones grandes.

---

## Componentes

Un componente Angular es una unidad reutilizable de la interfaz que encapsula **estructura, lógica y opcionalmente estilos**.

Se define mediante el decorador `@Component`.

```typescript
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

---

## Comunicación entre componentes

Los datos pueden pasar de un componente **padre a un hijo** mediante `@Input()`.

El flujo es **unidireccional**:

```typescript
Componente padre
      ↓
   @Input()
      ↓
Componente hijo
```

El componente hijo no debería modificar directamente los datos recibidos. Para comunicar información hacia el padre se utilizan **eventos**.

---

## Renderizado

Angular permite generar contenido dinámicamente.

- **Listas:** `*ngFor`
- **Condicionales:** `*ngIf`

Por ejemplo:

```typescript
<div *ngIf="cargando">
  Cargando...
</div>
```

Para listas:

```typescript
<app-mensaje
  *ngFor="let msg of mensajes"
  [autor]="msg.autor"
  [contenido]="msg.contenido">
</app-mensaje>
```

---

## Routing

Angular incluye un sistema de **routing** que permite asociar URLs con componentes y navegar entre vistas sin recargar toda la página.

Ejemplo:

```typescript
const routes: Routes = [
  { path: 'login', component: LoginComponent },
  { path: 'chat', component: ChatComponent },
  { path: 'chat/:id', component: ConversacionComponent }
];
```

Los parámetros de ruta permiten utilizar valores dinámicos, por ejemplo:

```typescript
/chat/42
```

donde `42` podría ser el identificador de una conversación.

---

## Ejemplo

Una aplicación empresarial puede utilizar Angular para crear las distintas **pantallas, componentes, formularios y navegación**, además de comunicarse con las **APIs del Backend** mediante solicitudes HTTP.

---
