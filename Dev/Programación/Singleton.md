---
tags:
  - Programación
  - ProgramaciónII
---
También llamado: Instancia única

---

## Propósito

**Singleton** es un patrón creacional que asegura que una clase tenga una única instancia y además da un punto de acceso global a esa instancia.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/singleton/singleton.png"> </p>

---

## Problema

El patrón Singleton resuelve dos cosas a la vez, tocando un poco el **Principio de Responsabilidad Única**:

### 1. Garantizar una única instancia

La idea es que una clase solo tenga un objeto vivo en toda la app.

Ejemplo típico: acceso a recursos compartidos como base de datos o archivos.

Si intentás crear otro objeto, en vez de uno nuevo te devuelve el mismo ya creado.

Esto no se puede hacer con un constructor normal, porque `new` siempre genera una instancia nueva por diseño.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/singleton/singleton-comic-1-es.png"> </p>

### 2. Punto de acceso global

Antes se usaban variables globales para esto, pero son peligrosas porque cualquier parte del código puede pisarlas.

Singleton hace algo parecido pero controlado:

- Permite acceso global
- Pero evita que se reemplace la instancia

El problema es que esta lógica termina mezclando responsabilidades dentro de una misma clase.

Hoy en día se usa tanto que mucha gente llama “singleton” a cualquier cosa que tenga una sola instancia, aunque no cumpla todo el patrón.

---

## Solución

Todas las implementaciones de Singleton siguen lo mismo:

1. Constructor privado para evitar `new`.
2. Método estático que crea o devuelve la instancia.

- La primera vez crea el objeto.
- Después devuelve el mismo cacheado.

---

## Analogía real

Un gobierno:

- Solo existe uno por país.
- Es un punto de acceso global.
- Cambian las personas, pero la instancia “Gobierno” es única.

---

## Estructura

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/singleton/structure-es-indexed.png"> </p>

- Singleton tiene un método estático tipo `getInstance`.
- El constructor es privado.
- Solo se accede a la instancia a través del método estático.

---

## Pseudocódigo

**Ejemplo clásico: conexión a base de datos.**
```ts
class Database {
  // Instancia única (estática)
  private static instance: Database;

  // Constructor privado: evita new desde afuera
  private constructor() {
    // Inicialización (conexión DB, etc.)
  }

  // Punto de acceso global
  public static getInstance(): Database {
    if (!Database.instance) {
      Database.instance = new Database();
    }
    return Database.instance;
  }

  // Lógica de negocio
  public query(sql: string): void {
    // Ejecuta query a la base de datos
  }
}

// Cliente
class Application {
  main() {
    const foo = Database.getInstance();
    foo.query("SELECT ...");

    const bar = Database.getInstance();
    bar.query("SELECT ...");

    // foo y bar son el mismo objeto
  }
}
```

---

## Aplicabilidad

Usalo cuando:
- Necesitás una sola instancia global (ej: base de datos, logger).
- Querés controlar acceso a un recurso compartido.
- Querés reemplazar variables globales por algo más seguro.

También podés limitarlo a más de una instancia si querés, cambiando `getInstance`.

---

## Cómo implementarlo

1. Campo estático para la instancia.
2. Método estático público para acceder.
3. Inicialización perezosa (lazy).
4. Constructor privado.
5. Reemplazar `new` por `getInstance`.

---

## Pros y contras

**Pros**
- Garantiza una única instancia.
- Punto de acceso global controlado.
- Se crea solo cuando se necesita.

**Contras**
- Viola parcialmente el principio de responsabilidad única.
- Puede esconder mal diseño (acoplamientos fuertes).
- Complica testing (mocking difícil).
- Problemas en entornos multihilo si no se maneja bien.

---

## Relaciones con otros patrones

- Una **Facade** puede ser Singleton naturalmente.

- Se parece a **Flyweight**, pero:
    - Singleton = una sola instancia.
    - Flyweight = varias instancias compartiendo estado.
    - Singleton puede ser mutable, Flyweight no.

- También puede implementarse con Abstract Factory, Builder y Prototype.