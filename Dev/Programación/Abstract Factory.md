---
tags:
  - Programación
  - ProgramaciónII
---
También llamado: Fábrica abstracta

---

##  Propósito

**Abstract Factory** es un patrón de diseño creacional que nos permite producir familias de objetos relacionados sin especificar sus clases concretas.

<p align="center">
  <img src="https://refactoring.guru/images/patterns/content/abstract-factory/abstract-factory-es.png">
</p>

---

## Problema

Imaginá que estás haciendo un simulador de tienda de muebles. El sistema tiene clases que representan:

1. Una familia de productos relacionados: `Silla` + `Sofá` + `Mesilla`.
2. Variantes de esa familia: por ejemplo `Moderna`, `Victoriana` y `ArtDecó`.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/abstract-factory/problem-es.png"> </p>

Familias de productos y sus variantes.

La idea es poder crear objetos de mobiliario que combinen entre sí dentro de la misma familia. Porque si no, el cliente se enoja cuando recibe cosas que no combinan.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/abstract-factory/abstract-factory-comic-1-es.png"> </p>

Ejemplo: un sofá moderno no combina con sillas victorianas.

Además, el sistema no debería romperse cuando agregás nuevos productos o nuevas familias, porque los catálogos de muebles cambian todo el tiempo. Si cada cambio obliga a tocar el código base, se vuelve un problema de mantenimiento.

---

##  Solución

El patrón Abstract Factory propone primero definir **interfaces claras para cada tipo de producto**: `Silla`, `Sofá`, `Mesilla`, etc.

Después, todas las variantes deben implementar esas interfaces. Por ejemplo, todas las sillas (modernas, victorianas, art decó) implementan `Silla`, y lo mismo con los otros productos.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/abstract-factory/solution1.png"> </p>

Todas las variantes de un mismo producto pertenecen a una misma jerarquía.

El siguiente paso es crear la **Fábrica Abstracta**, que define métodos para crear cada producto de la familia, por ejemplo: `crearSilla`, `crearSofá`, `crearMesilla`.  
Estos métodos devuelven productos abstractos (las interfaces).

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/abstract-factory/solution2.png"> </p>

Cada fábrica concreta representa una variante específica de la familia.

Después se crean fábricas concretas para cada estilo. Por ejemplo, una `FábricaDeMueblesModernos` que devuelve `SillaModerna`, `SofáModerno` y `MesillaModerna`.

El código cliente trabaja únicamente con interfaces, tanto de productos como de fábricas. Esto permite cambiar la fábrica sin romper nada del sistema.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/abstract-factory/abstract-factory-comic-2-es.png"> </p>

Al cliente no le importa la implementación concreta de la fábrica.

Por ejemplo, si el cliente pide una silla, no sabe si es moderna o victoriana. Solo sabe que es una `Silla` y usa su interfaz (por ejemplo `sentarse`). Lo importante es que siempre combina con los otros productos de la misma fábrica.

Finalmente, las fábricas concretas se crean al inicio de la aplicación, según la configuración o el entorno del sistema.

---

##  Estructura

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/abstract-factory/structure-indexed.png"> </p>

1. **Productos Abstractos**  
    Definen interfaces para grupos de productos relacionados que forman una familia (por ejemplo: silla, sofá, mesilla).
2. **Productos Concretos**  
    Son las implementaciones reales de esos productos abstractos, organizadas por variantes.  
    Ejemplo: silla victoriana / silla moderna, sofá victoriano / sofá moderno, etc.
3. **Fábrica Abstracta**  
    Declara los métodos de creación para cada tipo de producto abstracto (crearSilla, crearSofá, crearMesilla, etc.).
4. **Fábricas Concretas**  
    Implementan la fábrica abstracta. Cada una corresponde a una variante específica (moderna, victoriana, etc.) y crea únicamente esos productos.
5. Aunque las fábricas concretas crean productos concretos, sus métodos devuelven **tipos abstractos**.  
    Esto hace que el código cliente no dependa de implementaciones específicas. El cliente trabaja con cualquier fábrica o producto siempre que use las interfaces.

---

## Pseudocódigo

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/abstract-factory/example.png"> </p>

**Ejemplo de UI multiplataforma.**

La idea es crear elementos de interfaz que funcionen en distintos sistemas operativos sin acoplar el código a clases concretas. Los mismos componentes deben comportarse igual, aunque cambie su apariencia según el sistema.

La fábrica abstracta define métodos para crear distintos elementos UI. Cada fábrica concreta representa un sistema operativo específico y genera los elementos adecuados para ese entorno.

Cuando la aplicación inicia, detecta el sistema operativo y elige la fábrica correspondiente. A partir de ahí, todo el sistema crea UI usando esa fábrica, evitando errores como mezclar estilos de distintos sistemas.

El código cliente solo conoce interfaces abstractas, no clases concretas. Esto permite cambiar o agregar nuevas fábricas o componentes UI sin modificar el código existente.

En la práctica, cuando agregás una nueva familia de UI, solo creás una nueva fábrica concreta y ajustás la inicialización de la app. El resto del código no se toca.

**Fábrica Abstracta**
```ts
// Declara la familia de productos que se pueden crear
interface GUIFactory {
  createButton(): Button;
  createCheckbox(): Checkbox;
}
```

**Fábricas Concretas**
```ts
// Fabrica para Windows
class WinFactory implements GUIFactory {
  createButton(): Button {
    return new WinButton();
  }

  createCheckbox(): Checkbox {
    return new WinCheckbox();
  }
}

// Fabrica para Mac
class MacFactory implements GUIFactory {
  createButton(): Button {
    return new MacButton();
  }

  createCheckbox(): Checkbox {
    return new MacCheckbox();
  }
}
```

**Productos Abstractos**
```ts
// Botón genérico
interface Button {
  paint(): void;
}

// Checkbox genérico
interface Checkbox {
  paint(): void;
}
```

**Productos Concretos**
```ts
// Botón Windows
class WinButton implements Button {
  paint(): void {
    console.log("Botón estilo Windows");
  }
}

// Botón Mac
class MacButton implements Button {
  paint(): void {
    console.log("Botón estilo Mac");
  }
}

// Checkbox Windows
class WinCheckbox implements Checkbox {
  paint(): void {
    console.log("Checkbox estilo Windows");
  }
}

// Checkbox Mac
class MacCheckbox implements Checkbox {
  paint(): void {
    console.log("Checkbox estilo Mac");
  }
}
```

**Cliente (Aplicación)**
```ts
class Application {
  private factory: GUIFactory;
  private button!: Button;

  constructor(factory: GUIFactory) {
    this.factory = factory;
  }

  createUI(): void {
    this.button = this.factory.createButton();
  }

  paint(): void {
    this.button.paint();
  }
}
```

**Configurador / Main**
```ts
class ApplicationConfigurator {
  static main(os: string) {
    let factory: GUIFactory;

    if (os === "Windows") {
      factory = new WinFactory();
    } else if (os === "Mac") {
      factory = new MacFactory();
    } else {
      throw new Error("Sistema operativo desconocido");
    }

    const app = new Application(factory);
    app.createUI();
    app.paint();
  }
}
```

**Uso**
```ts
ApplicationConfigurator.main("Windows");
// ApplicationConfigurator.main("Mac");
```

---
## Aplicabilidad

Usá Abstract Factory cuando tu código tenga que trabajar con varias familias de productos relacionados, pero no quieras que dependa de clases concretas, ya sea porque todavía no las conocés o porque querés dejarlo abierto a futuras extensiones.

El patrón te da una interfaz para crear objetos de cada familia. Mientras crees todo a través de esa interfaz, evitás mezclar variantes incompatibles de productos.

También tiene sentido usarlo cuando una clase tiene muchos métodos de fábrica que empiezan a mezclar responsabilidades. En diseño limpio, cada clase debería hacer una sola cosa. Si una clase crea demasiados tipos de objetos, conviene separar esa responsabilidad en una fábrica única o directamente aplicar Abstract Factory.

---

## Cómo implementarlo

1. Definí una matriz de tipos de productos y sus variantes.

2. Creá interfaces abstractas para cada tipo de producto y hacé que todas las clases concretas las implementen.

3. Definí la interfaz de la fábrica abstracta con métodos para crear cada producto.

4. Implementá fábricas concretas, una por cada variante de familia de productos.

5. En la inicialización de la app, creá la fábrica concreta según configuración o entorno y pasala a las clases que necesitan crear productos.

6. Reemplazá todas las llamadas directas a `new` por llamadas a los métodos de la fábrica.

---

## Pros y contras

**Pros**
- Tenés la seguridad de que los productos que salen de una fábrica son compatibles entre sí.
- Evitás el acoplamiento fuerte entre el código cliente y clases concretas.
- **Principio de responsabilidad única:** la creación de objetos se centraliza en un solo lugar, haciendo el sistema más mantenible.
- **Principio abierto/cerrado:** podés agregar nuevas variantes sin romper el código existente.

**Contras**
- Puede volverse más complejo porque agrega varias interfaces y clases nuevas.

---

## Relaciones con otros patrones

- Muchos diseños arrancan con **Factory Method** (más simple) y evolucionan hacia **Abstract Factory, Prototype o Builder**, que son más flexibles pero también más complejos.

- **Builder** se enfoca en construir objetos paso a paso, mientras que **Abstract Factory** crea familias completas de objetos relacionados de una sola vez. Abstract Factory devuelve el producto listo; Builder permite construirlo por etapas.

- Abstract Factory muchas veces se implementa usando varios Factory Methods, aunque también puede apoyarse en Prototype.

- Puede reemplazar a **Facade** cuando querés ocultar cómo se crean los objetos del subsistema.

- Se puede combinar con **Bridge** cuando ciertas abstracciones solo funcionan con implementaciones específicas; Abstract Factory ayuda a encapsular esas combinaciones.

- Abstract Factory, Builder y Prototype pueden implementarse usando **Singleton** si se necesita una única instancia global de cada fábrica.