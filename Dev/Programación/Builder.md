---
tags:
  - Programación
  - ProgramaciónII
---
También llamado: Constructor

---

##  Propósito

**Builder** es un patrón de diseño creacional que nos permite construir objetos complejos paso a paso. El patrón nos permite producir distintos tipos y representaciones de un objeto empleando el mismo código de construcción.

<p align="center">
  <img src="https://refactoring.guru/images/patterns/content/builder/builder-es.png">
</p>

---

##  Problema

Imaginá un objeto complejo que necesita una inicialización paso a paso, con muchos campos y objetos anidados. Normalmente esto termina escondido dentro de un constructor gigante con muchísimos parámetros, o peor, repartido por todo el código cliente.
<p align="center">  
<img src="https://refactoring.guru/images/patterns/diagrams/builder/problem1.png">  
</p>

Otra opción es crear una subclase por cada configuración posible del objeto, pero eso complica demasiado el sistema.

Por ejemplo, para un objeto `Casa`, una versión simple necesita paredes, piso, puerta, ventanas y techo. Pero si querés una casa más grande, con jardín, calefacción, plomería y electricidad, las combinaciones empiezan a explotar.

La solución más directa es extender la clase base `Casa` y crear muchas subclases para cubrir todas las combinaciones posibles. El problema es que cada nuevo parámetro (como el estilo del porche) hace crecer todavía más esa jerarquía.

Otra alternativa es meter todo en un constructor enorme dentro de la clase `Casa`, con todos los parámetros posibles. Esto evita las subclases, pero trae otro problema distinto.
<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/builder/problem2.png"> </p>

Un constructor con muchos parámetros tiene un problema: no todos los parámetros se usan siempre.

En la mayoría de los casos, muchos de esos parámetros quedan sin usar, lo que hace que las llamadas al constructor sean bastante feas y difíciles de leer.

Por ejemplo, solo una minoría de casas tiene piscina, así que todo lo relacionado con piscina termina siendo inútil en la mayoría de los casos.

---

##  Solución

El patrón Builder propone sacar el código de construcción del objeto de su propia clase y moverlo a objetos separados llamados **constructores**.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/builder/solution1.png"> </p>

La idea es construir objetos complejos paso a paso. Mientras se está construyendo, otros objetos no pueden acceder al producto.

La construcción se organiza como una serie de pasos (`construirParedes`, `construirPuerta`, etc.). Para crear un objeto se ejecutan esos pasos en el constructor, pero no es obligatorio usarlos todos: podés usar solo los que necesites para una configuración específica.

Algunos pasos pueden cambiar según el tipo de objeto que quieras construir. Por ejemplo, una cabaña puede tener paredes de madera, mientras que un castillo necesita paredes de piedra.

Por eso podés tener distintos constructores que implementan los mismos pasos, pero de forma diferente. Así, usando la misma secuencia de construcción, obtenés resultados distintos.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/builder/builder-comic-1-es.png"> </p>

Todos los constructores hacen lo mismo, pero con materiales o lógica distinta. Por ejemplo:

- madera y vidrio → casa normal
- piedra e hierro → castillo
- oro y diamantes → palacio

Esto funciona siempre que el código cliente pueda interactuar con todos los constructores mediante una interfaz común.

---

#### Clase directora

Podés ir un paso más allá y mover la secuencia de construcción a una clase separada llamada **directora**. Esta clase define el orden de los pasos, mientras que el constructor define cómo se ejecutan.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/builder/builder-comic-2-es.png"> </p>

La directora sabe qué pasos ejecutar para construir un objeto válido.

No es obligatorio tener una directora: también podés llamar los pasos directamente desde el cliente. Pero sirve mucho para reutilizar procesos de construcción ya armados.

Además, la directora oculta completamente los detalles de construcción al cliente. El cliente solo conecta un constructor con la directora, inicia la construcción y recibe el resultado final.

---

##  Estructura

![Estructura del patrón de diseño Builder](https://refactoring.guru/images/patterns/diagrams/builder/structure-indexed.png)

1. La interfaz **Constructora** declara pasos de construcción de producto que todos los tipos de objetos constructores tienen en común.
    
2. Los **Constructores Concretos** ofrecen distintas implementaciones de los pasos de construcción. Los constructores concretos pueden crear productos que no siguen la interfaz común.
    
3. Los **Productos** son los objetos resultantes. Los productos construidos por distintos objetos constructores no tienen que pertenecer a la misma jerarquía de clases o interfaz.
    
4. La clase **Directora** define el orden en el que se invocarán los pasos de construcción, por lo que puedes crear y reutilizar configuraciones específicas de los productos.
    
5. El **Cliente** debe asociar uno de los objetos constructores con la clase directora. Normalmente, se hace una sola vez mediante los parámetros del constructor de la clase directora, que utiliza el objeto constructor para el resto de la construcción. No obstante, existe una solución alternativa para cuando el cliente pasa el objeto constructor al método de producción de la clase directora. En este caso, puedes utilizar un constructor diferente cada vez que produzcas algo con la clase directora.
    

##  Pseudocódigo

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/builder/structure-indexed.png"> </p>

1. La **Constructora (Builder)** define los pasos de construcción que todos los constructores comparten.

2. Los **Constructores Concretos** implementan esos pasos de distintas formas. Pueden generar productos que no necesariamente siguen la misma interfaz entre sí.

3. Los **Productos** son el resultado final. No tienen que pertenecer a la misma jerarquía ni interfaz según el constructor que los creó.

4. La **Directora** define el orden en que se ejecutan los pasos de construcción, permitiendo reutilizar configuraciones ya armadas.

5. El **Cliente** conecta un constructor con la directora. Normalmente esto se hace una sola vez mediante el constructor de la directora, que usa ese builder para todo el proceso. También existe la opción de pasar el builder al método de construcción de la directora, permitiendo usar distintos constructores cada vez.


```ts
// El uso del patrón Builder sólo tiene sentido cuando tus
// productos son bastante complejos y requieren una
// configuración extensiva. Los dos siguientes productos están
// relacionados, aunque no tienen una interfaz común.
class Auto {
    // Un auto puede tener un GPS, una computadora de
    // navegación y cierto número de asientos. Los distintos
    // modelos de autos (deportivo, SUV, descapotable) pueden
    // tener distintas características instaladas o habilitadas.
}

class Manual {
    // Cada auto debe contar con un manual de usuario que se
    // corresponda con la configuración del auto y explique
    // todas sus características.
}

// La interfaz constructora especifica métodos para crear las
// distintas partes de los objetos del producto.
interface Constructor {
    reiniciar(): void;
    establecerAsientos(...args: any[]): void;
    establecerMotor(...args: any[]): void;
    establecerComputadoraViaje(...args: any[]): void;
    establecerGPS(...args: any[]): void;
}

// Las clases constructoras concretas siguen la interfaz
// constructora y proporcionan implementaciones específicas de
// los pasos de construcción.
class ConstructorAuto implements Constructor {
    private auto: Auto;

    constructor() {
        this.reiniciar();
    }

    // El método reiniciar despeja el objeto en construcción.
    reiniciar(): void {
        this.auto = new Auto();
    }

    establecerAsientos(...args: any[]): void {
        // Establece la cantidad de asientos del auto.
    }

    establecerMotor(...args: any[]): void {
        // Instala un motor específico.
    }

    establecerComputadoraViaje(...args: any[]): void {
        // Instala una computadora de navegación.
    }

    establecerGPS(...args: any[]): void {
        // Instala un GPS.
    }

    getProducto(): Auto {
        const producto = this.auto;
        this.reiniciar();
        return producto;
    }
}

// Builder también permite construir productos sin interfaz común.
class ConstructorManualAuto implements Constructor {
    private manual: Manual;

    constructor() {
        this.reiniciar();
    }

    reiniciar(): void {
        this.manual = new Manual();
    }

    establecerAsientos(...args: any[]): void {
        // Documenta las características del asiento del auto.
    }

    establecerMotor(...args: any[]): void {
        // Añade instrucciones del motor.
    }

    establecerComputadoraViaje(...args: any[]): void {
        // Añade instrucciones de la computadora de navegación.
    }

    establecerGPS(...args: any[]): void {
        // Añade instrucciones del GPS.
    }

    getProducto(): Manual {
        const producto = this.manual;
        this.reiniciar();
        return producto;
    }
}

// El director sólo es responsable de ejecutar los pasos de
// construcción en una secuencia particular.
class Director {
    constructAutoDeportivo(constructor: Constructor): void {
        constructor.reiniciar();
        constructor.establecerAsientos(2);
        constructor.establecerMotor({ tipo: "deportivo" });
        constructor.establecerComputadoraViaje(true);
        constructor.establecerGPS(true);
    }

    constructSUV(constructor: Constructor): void {
        // ...
    }
}

// El código cliente crea un objeto constructor, lo pasa al
// director y después inicia el proceso de construcción.
class Aplicacion {
    makeCar(): void {
        const director = new Director();

        const constructorAuto = new ConstructorAuto();
        director.constructAutoDeportivo(constructorAuto);
        const auto = constructorAuto.getProducto();

        const constructorManual = new ConstructorManualAuto();
        director.constructAutoDeportivo(constructorManual);
        const manual = constructorManual.getProducto();
    }
}
```

---

##  Aplicabilidad

 El patrón Builder sirve para evitar el “constructor telescópico”.

Cuando tenés un constructor con muchos parámetros opcionales (por ejemplo 10), llamarlo se vuelve incómodo. Para arreglarlo, se suelen hacer varias versiones del constructor más cortas con distintos parámetros, que terminan llamando al principal con valores por defecto.

```ts
class Pizza {    
Pizza(int tamaño) { ... }    
Pizza(int tamaño, boolean queso) { ... }    
Pizza(int tamaño, boolean queso, boolean pepperoni) { ... }    
// ...}
```

Esto sólo es posible en lenguajes con sobrecarga de métodos como Java o C#.

El problema es que igual terminás con código difícil de mantener. El Builder lo resuelve permitiendo construir objetos paso a paso, usando sólo los pasos necesarios, sin llenar el constructor de parámetros.

---

### Cuándo usar Builder
Se usa cuando querés crear distintas representaciones del mismo objeto (por ejemplo casas de madera o de piedra), pero compartiendo pasos de construcción similares que cambian sólo en detalles.

La interfaz constructora define todos los pasos posibles, los constructores concretos implementan esos pasos para cada variante, y el director define el orden en que se ejecutan.

---

### Casos típicos de uso
También se usa cuando querés construir estructuras complejas como árboles con el patrón Composite, o cualquier objeto complejo.

Permite construir paso a paso, incluso de forma recursiva si hace falta (útil para estructuras tipo árbol).

---

### Detalle importante
El Builder no expone el objeto mientras se está construyendo. O sea, el cliente no puede agarrar un producto a medio armar y usarlo antes de tiempo.

---

##  Cómo implementarlo

1. Primero tenés que identificar bien los pasos comunes de construcción para todas las variantes del producto. Si no están claros, no podés aplicar el patrón.

2. Esos pasos se declaran en la interfaz base del constructor.

3. Después creás una clase constructora concreta por cada variante del producto, implementando esos pasos.
    
    Importante: también tenés que agregar un método para obtener el resultado final de la construcción. Esto no va en la interfaz porque puede haber constructores que generan productos sin interfaz común, entonces no se sabe qué tipo devolver.  
    
    Si todos los productos comparten una misma jerarquía, ahí sí se puede poner en la interfaz base sin problema.

3. Opcionalmente, podés crear una clase directora, que define distintas formas de construir el producto usando el mismo constructor.

4. El cliente crea el constructor y el director. Le pasa el constructor al director (normalmente una sola vez, por el constructor del director), y el director lo usa para ejecutar la construcción. También existe la variante donde el constructor se pasa directamente al método del director.

5. El resultado final:
	    - Si todos los productos comparten la misma interfaz, se puede obtener directamente desde el director.
	    - Si no, el cliente lo tiene que sacar directamente del constructor.

---

##  Pros y contras

**Pros**
- Podés construir objetos paso a paso, aplazar etapas del proceso o incluso ejecutarlas de forma recursiva.
- Podés reutilizar el mismo proceso de construcción para crear distintas representaciones del mismo producto.
- **Principio de responsabilidad única:** separás la lógica de construcción del objeto de la lógica de negocio, lo que deja el código más ordenado y mantenible.---

**Contras**
- Aumenta la complejidad del sistema, porque el patrón introduce varias clases e interfaces nuevas.

---

##  Relaciones con otros patrones

- Muchos diseños arrancan con Factory Method (más simple y flexible con subclases) y después evolucionan hacia Abstract Factory, Prototype o Builder, que son más potentes pero también más complejos.

- Builder se enfoca en construir objetos complejos paso a paso. Abstract Factory se centra en crear familias de objetos relacionados. La diferencia clave es que Abstract Factory devuelve el producto de una, mientras que Builder te deja armarlo por pasos antes de obtenerlo.

- Builder se puede usar para construir estructuras tipo Composite porque permite definir pasos de construcción incluso de forma recursiva.

- Builder también se puede combinar con Bridge: la clase directora funciona como la abstracción, y los distintos builders como las implementaciones.

- Abstract Factory, Builder y Prototype pueden implementarse como Singletons.