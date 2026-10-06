---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Las **estructuras de control** permiten controlar el flujo de ejecución de un programa.

Las condiciones utilizadas en estas estructuras son **expresiones booleanas**, es decir, expresiones que al evaluarse producen `true` o `false`.

## Estructuras condicionales

Permiten ejecutar diferentes instrucciones dependiendo de si se cumple o no una condición.

- [[If]]
- [[If-else]]
- [[Switch]]

---

## Expresiones booleanas

Una condición produce un valor booleano:

```typescript
edad >= 18
```

El resultado de esa expresión será `true` o `false`.

Por este motivo, una expresión booleana también puede devolverse directamente:

```typescript
return edad >= 18;
```

Esto equivale a:

```typescript
if (edad >= 18) {
  return true;
}

return false;
```

---

## Operadores lógicos

Permiten combinar o negar expresiones booleanas.

- `&&` → Y (AND)
- `||` → O (OR)
- `!` → NO (NOT)

Ejemplo:

```typescript
edad >= 18 && tieneEntrada
```

La expresión completa también devuelve `true` o `false`.

> El operador `!!` tiene un uso diferente: convierte un valor a booleano. Ver [[Doble negación]].

---

## Combinación de estructuras

Las estructuras de control pueden combinarse y anidarse.

Por ejemplo, un `if` puede contener otro `if`.

Ver [[If]] y [[If-else]].

---
