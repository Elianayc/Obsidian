# `!!`

El operador `!!` permite convertir un valor a un booleano (`true` o `false`).

Un solo `!` niega un valor:

```typescript
!true  // false
!false // true
```

Al utilizar dos:

```typescript
!!valor
```

el primero lo niega y el segundo lo vuelve a negar. El resultado final representa el valor como un booleano.

Ejemplos:

```typescript
!!true       // true
!!false      // false
!!'Hola'     // true
!!''         // false
!!undefined  // false
!!null       // false
```

### Ejemplo de la práctica

```typescript
!!this.usernameControl?.touched
```

`this.usernameControl?.touched` podría devolver `true`, `false` o `undefined`.

El `!!` garantiza que el resultado sea solamente:

```text
true o false
```

### Machete

```text
!valor  → niega
!!valor → convierte a booleano
```

---
