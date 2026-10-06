Hasta ahora manejábamos los datos del formulario **manualmente** desde el componente:

```
username = '';
password = '';
```

Y capturábamos los cambios mediante eventos:

```
<input
  [value]="username"
  (input)="onUsernameInput(usernameInput.value)"
/>
```

Con **Reactive Forms**, Angular puede encargarse de administrar el formulario, sus campos y sus validaciones.

---

### Importaciones

```
import { FormBuilder, FormGroup, Validators } from '@angular/forms';
```

- **`FormGroup`**: representa el formulario completo en TypeScript.
- **`FormBuilder`**: herramienta que facilita la creación del formulario.
- **`Validators`**: permite definir reglas de validación.

---

### Crear el formulario

Primero se declara:

```ts
loginForm: FormGroup;
```

Después se construye:

```ts
this.loginForm = this.formBuilder.group({
  username: ['', [Validators.required, Validators.minLength(3)]],
  password: ['', [Validators.required, Validators.minLength(1)]],
});
```

Mentalmente:

```
loginForm
│
├── username
│   ├── valor inicial: ''
│   ├── required → obligatorio
│   └── minLength(3) → mínimo 3 caracteres
│
└── password
    ├── valor inicial: ''
    ├── required → obligatorio
    └── minLength(1) → mínimo 1 carácter
```

La estructura general de cada campo es:

```
nombreDelCampo: [valorInicial, [validaciones]]
```

Por ejemplo:

```
username: ['', [Validators.required, Validators.minLength(3)]]
```

significa:

> El campo `username` comienza vacío, es obligatorio y debe tener como mínimo 3 caracteres.

---

