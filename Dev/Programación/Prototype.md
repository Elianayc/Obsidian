---
tags:
  - Programación
  - ProgramaciónII
---
También llamado: Prototipo, Clon, Clone

---

## Propósito

**Prototype** es un patrón creacional que te permite copiar objetos existentes sin depender de sus clases concretas.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/prototype/prototype.png"> </p>

---

## Problema

Imaginá que querés clonar un objeto tal cual. En teoría es simple: creás otro de la misma clase y copiás sus campos.

El problema es que:

- Algunos campos pueden ser privados y no accesibles desde afuera.
- Tenés que conocer la clase concreta para poder copiarlo, lo que genera acoplamiento.
- A veces solo conocés la interfaz, no la clase real (por ejemplo, parámetros polimórficos).

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/prototype/prototype-comic-1-es.png"> </p>

---

## Solución

El patrón Prototype delega la clonación al propio objeto.

- Se define una interfaz común con un método tipo `clone`.
- Cada objeto sabe cómo clonarse a sí mismo.
- El clon copia todos los campos del original (incluso privados si pertenece a la misma clase).

Un objeto clonable se llama **prototipo**.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/prototype/prototype-comic-2-es.png"> </p>

En vez de construir desde cero, clonás objetos ya configurados.

---

## Analogía real

En la vida real, un prototipo se usa para testear antes de producir en masa.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/prototype/prototype-comic-3-es.png"> </p>

Un ejemplo más cercano es la división celular: una célula se divide y genera copias idénticas. La original actúa como prototipo.

---

## Estructura

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/prototype/structure-indexed.png"> </p>

1. **Prototype**: interfaz con método `clone`.
2. **Concrete Prototype**: implementa la clonación y maneja casos complejos.
3. **Client**: usa `clone` sin depender de clases concretas.

---

### Registro de prototipos

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/prototype/structure-prototype-cache-indexed.png"> </p>

- Guarda prototipos reutilizables (tipo cache).
- Normalmente es un `map name → prototype`.

---

## Pseudocódigo

Ejemplo con figuras [clonables]() sin depender de sus clases.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/prototype/example.png"> </p>

**Clase Base: Prototipo Shape**
```ts
abstract class Shape {
  x: number;
  y: number;
  color: string;

  constructor(source?: Shape) {
    if (source) {
      this.x = source.x;
      this.y = source.y;
      this.color = source.color;
    }
  }

  // Método clave del patrón: clonar
  abstract clone(): Shape;
}
```

**Prototipo concreto: Rectangle**
```ts
class Rectangle extends Shape {
  width: number;
  height: number;

  constructor(source: Rectangle) {
    super(source);
    this.width = source.width;
    this.height = source.height;
  }

  clone(): Shape {
    return new Rectangle(this);
  }
}
```

**Prototipo concreto: Circle**
```ts
class Circle extends Shape {
  radius: number;

  constructor(source: Circle) {
    super(source);
    this.radius = source.radius;
  }

  clone(): Shape {
    return new Circle(this);
  }
}
```

**Cliente**
```ts
class Application {
  shapes: Shape[] = [];

  constructor() {
    const circle = new Circle(undefined as any);
    circle.x = 10;
    circle.y = 10;
    circle.radius = 20;

    this.shapes.push(circle);
    this.shapes.push(circle.clone());
  }

  businessLogic() {
    const copy: Shape[] = [];

    for (const s of this.shapes) {
      copy.push(s.clone());
    }
  }
}
```

---

## Aplicabilidad

Usalo cuando:
- No querés depender de clases concretas.
- Trabajás con objetos que vienen de librerías o terceros.
- Querés evitar subclases solo para distintos estados iniciales.
- Querés reutilizar configuraciones ya armadas.

---

## Cómo implementarlo

1. Definí interfaz `clone`.
2. Implementá constructor de copia.
3. Cada clase concreta sobreescribe `clone`.
4. Opcional: agregá un registro de prototipos.
5. Reemplazá `new` por `clone` o por el registro.

---

## Pros y contras

**Pros**
- Clonás sin depender de clases concretas.
- Evitás inicialización repetida.
- Simplifica creación de objetos complejos.
- Alternativa a la herencia para configuraciones.

**Contras**
- Clonar estructuras con referencias circulares puede complicarse.

---

## Relaciones con otros patrones

- Suele aparecer junto a Factory Method, Abstract Factory y Builder.

- Abstract Factory usa métodos de creación, Prototype clona objetos.

- Útil con Command para guardar historial.

- Funciona muy bien con Composite y Decorator para clonar estructuras completas.

- A veces reemplaza a Memento en casos simples.

- Puede implementarse como Singleton junto a otros patrones creacionales.