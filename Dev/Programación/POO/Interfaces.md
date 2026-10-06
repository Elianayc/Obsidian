---
tags:
  - Programación
  - ProgramaciónII
---

Una interfaz define un **contrato** que indica qué debe cumplir una determinada estructura.

En TypeScript puede utilizarse principalmente para:

1. Definir el **comportamiento** que debe cumplir una clase.
2. Definir la **estructura o forma** que debe tener un objeto.

---

## Interfaces como contrato de comportamiento

Una interfaz puede definir métodos que una clase deberá implementar.

### Idea conceptual

- La **clase** define cómo es y cómo funciona un objeto.
- La **interfaz** establece un contrato que indica qué debe poder hacer.

### Ejemplo

```typescript
interface ITurnable {
  turnOn(): boolean;
  turnOff(): boolean;
}
```

Una clase puede comprometerse a cumplir ese contrato mediante `implements`:

```typescript
class Engine implements ITurnable {
  turnOn(): boolean {
    return true;
  }

  turnOff(): boolean {
    return false;
  }
}
```

Todos los miembros exigidos por la interfaz deben estar presentes en la clase.

Una clase puede implementar más de una interfaz.

---

## Interfaces para definir la estructura de un objeto

En TypeScript una interfaz también puede indicar **qué propiedades debe tener un objeto y de qué tipo debe ser cada una**.

```typescript
interface DemoConversation {
  id: string;
  title: string;
  text: string;
  archived: boolean;
}
```

Esto establece que un objeto de tipo `DemoConversation` debe respetar esta estructura:

```text
DemoConversation
├── id       → string
├── title    → string
├── text     → string
└── archived → boolean
```

Por ejemplo:

```typescript
const conversation: DemoConversation = {
  id: 'conv-1',
  title: 'Planning',
  text: 'Review class 8 goals before practice.',
  archived: false,
};
```

También puede utilizarse para indicar el tipo de los elementos de un array:

```typescript
conversations: DemoConversation[];
```

Se lee:

> `conversations` es un array cuyos elementos deben respetar la interfaz `DemoConversation`.

---

## Relación con polimorfismo

Las interfaces permiten tratar objetos según un **contrato común**, independientemente de su clase concreta.

Esto permite aplicar polimorfismo basado en interfaces.

---

## Conversión de tipos

También es posible indicar a TypeScript que trate un valor según una interfaz utilizando `as`.

```typescript
const obj = engine as ITurnable;
```