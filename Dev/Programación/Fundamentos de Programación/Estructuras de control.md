---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Las **estructuras de control** permiten controlar el flujo de ejecución de un programa.
Las condiciones son expresiones lógicas cuyo resultado es verdadero o falso.

---

## Operadores lógicos

Permiten relacionar condiciones:

- `&&` → Y
- `||` → O
- `!` → NO

Ver [[Invertir un Booleano]]

---

### Ejemplo

```typescript
return !!this.usernameControl?.touched &&
       !!this.usernameControl?.hasError('required');
```

- `?.` → [[Optional chaining]]
- `!!` → [[Doble Negación]]

---

## Combinación de estructuras

Las estructuras pueden combinarse y anidarse.

Ver:
- [[If]]
- [[If-else]]
- [[Switch]]

---
