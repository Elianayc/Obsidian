# `?.`

El operador `?.` permite acceder a una propiedad o método **solo si el objeto existe**.

Se puede leer como:

> **"Si esto existe, seguí."**

## Sintaxis

```typescript
objeto?.propiedad
```

## Ejemplo

```typescript
this.usernameControl?.touched
```

Significa:

> Si `usernameControl` existe, consultá su propiedad `touched`.

Esto es útil cuando una variable podría ser `null` o `undefined`.

Sin optional chaining:

```typescript
this.usernameControl.touched
```

Si `usernameControl` no existe, podría producirse un error al intentar acceder a `touched`.

Con optional chaining:

```typescript
this.usernameControl?.touched
```

Si `usernameControl` no existe, no intenta acceder a `touched` y evita ese error.

## Machete

```text
?. → "si esto existe, seguí"
```

---

