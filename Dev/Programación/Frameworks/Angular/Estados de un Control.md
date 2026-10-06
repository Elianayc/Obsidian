En Reactive Forms, Angular registra automáticamente el **estado de cada control del formulario**.

Estos estados permiten saber si el usuario interactuó con el campo, si modificó su contenido y si cumple las validaciones.

---

### Interacción con el campo

- `touched`: el usuario entró al campo y luego salió.
- `untouched`: el usuario todavía no salió del campo.

```typescript
this.usernameControl?.touched
```

---

### Modificación del valor

- `dirty`: el usuario modificó el valor del campo.
- `pristine`: el usuario todavía no modificó el valor.

```typescript
this.usernameControl?.dirty
```

---

### Validación

- `valid`: el campo cumple todas sus validaciones.
- `invalid`: el campo incumple al menos una validación.

```typescript
this.usernameControl?.invalid
```

---

### Errores específicos

Para comprobar **qué validación está fallando** se puede utilizar:

```typescript
this.usernameControl?.hasError('required')
```

Por ejemplo:

```typescript
this.usernameControl?.hasError('minlength')
```

---

### Ejemplo

```typescript
this.usernameControl?.touched &&
this.usernameControl?.hasError('required')
```

Significa:

> El usuario ya salió del campo **y** el campo tiene el error `required`.

Esto permite mostrar el mensaje de error en el momento adecuado.

---

### Machete

| Estado            | Significado                   |
| ----------------- | ----------------------------- |
| `touched`         | Entró al campo y salió        |
| `untouched`       | Todavía no salió del campo    |
| `dirty`           | Modificó el valor             |
| `pristine`        | No modificó el valor          |
| `valid`           | Cumple todas las validaciones |
| `invalid`         | Incumple alguna validación    |
| `hasError('...')` | Comprueba un error específico |

Los estados se presentan en pares opuestos:

```text
touched  ↔ untouched
dirty    ↔ pristine
valid    ↔ invalid
```

---
