Un **componente Angular** representa una parte de la interfaz de la aplicación.

Normalmente está formado por:

```
COMPONENTE
├── TypeScript → lógica y datos
├── HTML       → estructura
└── CSS        → estilos
```

---

## `@Component`

Angular utiliza el decorador `@Component` para indicar que una clase representa un componente.

```typescript
@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent {
}
```

---

## `selector`

El `selector` es el nombre con el que el componente puede utilizarse dentro del HTML de otro componente.

```typescript
selector: 'app-login'
```

permite escribir:

```html
<app-login></app-login>
```

---

## Clase del componente

```typescript
export class LoginComponent {
}
```

La clase contiene los datos y funciones relacionados con esa interfaz.

Por ejemplo:

```typescript
export class LoginComponent {
  nombre = '';

  ingresar() {
    // lógica relacionada con la acción
  }
}
```

El HTML puede utilizar esos datos y funciones mediante binding.

---

## Árbol de componentes

Angular permite construir la interfaz combinando componentes.

```
AppComponent
├── HeaderComponent
├── LoginComponent
└── ChatComponent
```

Un componente puede actuar como **padre** de otros componentes.

Esto permite dividir una aplicación grande en partes más pequeñas con responsabilidades específicas.

Ver [[Comunicación entre Componentes en Angular]].

---
