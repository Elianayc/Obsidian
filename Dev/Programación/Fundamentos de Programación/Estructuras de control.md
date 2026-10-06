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

---

## Simplificación de condiciones

Cuando varios [[If]] anidados solamente evalúan condiciones que deben cumplirse al mismo tiempo:

```typescript
if (condicion1) {
  if (condicion2) {
    return true;
  }
}

return false;
```

pueden combinarse mediante `&&`:

```typescript
if (condicion1 && condicion2) {
  return true;
}

return false;
```

Como la expresión lógica ya produce un valor booleano, puede retornarse directamente:

```typescript
return condicion1 && condicion2;
```

Por lo tanto:

```text
if anidados
      ↓
combinar condiciones con && 
      ↓
retornar directamente la expresión
```

---

### Ejemplo

```typescript
return !!this.usernameControl?.touched &&
       !!this.usernameControl?.hasError('required');
```

- `?.` → [[Optional chaining]]
- `!!` → [[Doble negación]]

---

## Combinación de estructuras

Las estructuras pueden combinarse y anidarse.

Ver:
- [[If]]
- [[If-else]]
- [[Switch]]

---
