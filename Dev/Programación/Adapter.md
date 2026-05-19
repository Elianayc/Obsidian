---
tags:
  - Programación
  - ProgramaciónII
---
También llamado: Adaptador, Envoltorio, Wrapper

---
## Propósito

Adapter es un patrón estructural que permite que objetos con **interfaces incompatibles puedan trabajar juntos**.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/adapter/adapter-es.png?id=5b877b3bdab93ef57848e3d6426064f1"> </p>

---

## Problema

Imaginá que estás creando una app que monitorea el mercado de valores. La app descarga datos de distintas fuentes en **XML** y los muestra con gráficos.

En un momento querés integrar una biblioteca externa de análisis… pero esa biblioteca **solo acepta JSON**.

Antes de la integración:

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/adapter/problem-es.png"> </p>

No podés usar la biblioteca “tal cual” porque el formato es incompatible.

Cambiar la biblioteca para que acepte XML no es buena idea:

- Podés romper código existente.
- Puede que ni siquiera tengas acceso al código fuente.

---

## Solución

Creás un **Adaptador**: un objeto que convierte una interfaz en otra compatible.

El adaptador:

- Envuelve el objeto incompatible.
- Traduce los datos internamente.
- El cliente no sabe que existe.

Ejemplo: envolver un sistema que usa **metros/km** con otro que usa **millas/pies**.

Después de la integración:

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/adapter/solution-es.png"> </p>

El cliente usa la interfaz esperada y el adaptador hace la conversión detrás de escena.

---

##  Analogía en el mundo real

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/adapter/adapter-comic-1-es.png?id=8e18327b405f5590443a97a5a6ae6877"> </p>

Una maleta antes y después de un viaje al extranjero.

Cuando viajas de Europa a Estados Unidos por primera vez, puede ser que te lleves una sorpresa cuanto intentes cargar tu computadora portátil. Los tipos de enchufe son diferentes en cada país, por lo que un enchufe español no sirve en Estados Unidos. El problema puede solucionarse utilizando un adaptador que incluya el enchufe americano y el europeo.

---

## Estructura

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/adapter/structure-object-adapter-indexed.png"> </p>

La clase **Cliente** contiene la lógica de negocio existente.

La **Interfaz con el Cliente** define el protocolo que otras clases deben seguir para colaborar con el cliente.

El **Servicio** es una clase útil (generalmente de terceros o heredada) que el cliente no puede usar directamente porque su interfaz es incompatible.

La **Clase Adaptadora** trabaja con ambas: implementa la interfaz del cliente y envuelve al servicio, traduciendo las llamadas del cliente a un formato que el servicio pueda entender.

El cliente no queda acoplado a una adaptadora concreta mientras use la interfaz objetivo. Esto permite agregar nuevos adaptadores sin romper el código existente, incluso si cambia o se reemplaza la interfaz del servicio.

---

## Clase adaptadora

Esta implementación utiliza la herencia, porque la clase adaptadora hereda interfaces de ambos objetos al mismo tiempo. Ten en cuenta que esta opción sólo puede implementarse en lenguajes de programación que soporten la herencia múltiple, como C++.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/adapter/structure-class-adapter-indexed.png?id=250b5c485a7dfba7c16b89a9201538fb"> </p>

1. La **Clase adaptadora** no necesita envolver objetos porque hereda comportamientos tanto de la clase cliente como de la clase de servicio. La adaptación tiene lugar dentro de los métodos sobrescritos. La clase adaptadora resultante puede utilizarse en lugar de una clase cliente existente.

---

## Ejemplo en TypeScript

Este ejemplo del patrón **Adapter** se basa en el clásico conflicto entre piezas cuadradas y agujeros redondos.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/adapter/example.png?id=9d2b6857ce256f2c669383ce4df3d0aa"> </p>
  
Adaptando piezas cuadradas a agujeros redondos.

> [!EXAMPLE]
> 
> **Tenemos dos clases con interfaces compatibles: RoundHole (HoyoRedondo) y RoundPeg (PiezaRedonda).**
> ```ts
> class RoundHole {
>   constructor(private radius: number) {}
> 
>   // Devuelve el radio del agujero
>   public getRadius(): number {
>     return this.radius;
>   }
> 
>   // Verifica si una pieza redonda encaja en el agujero
>   public fits(peg: RoundPeg): boolean {
>     return this.getRadius() >= peg.getRadius();
>   }
> }
> 
> class RoundPeg {
>   constructor(private radius: number) {}
> 
>   // Devuelve el radio de la pieza redonda
>   public getRadius(): number {
>     return this.radius;
>   }
> }
> ```
> 
> **Clase incompatible: SquarePeg (PiezaCuadrada)**
> ```ts
> class SquarePeg {
>   constructor(private width: number) {}
> 
>   // Devuelve la anchura de la pieza cuadrada
>   public getWidth(): number {
>     return this.width;
>   }
> }
> ```
> 
> **Adaptador: permite encajar piezas cuadradas en hoyos redondos.**
> ```ts
> //Extiende RoundPeg para que el cliente lo trate como pieza redonda
> class SquarePegAdapter extends RoundPeg {
>   private peg: SquarePeg;
> 
>   constructor(peg: SquarePeg) {
>     // Llamamos al constructor padre con un valor temporal
>     // porque el radio real lo calculamos dinámicamente.
>     super(0);
>     this.peg = peg;
>   }
> 
>   // Convierte la anchura del cuadrado en un radio equivalente
>   // Fórmula: radio = (ancho * √2) / 2
>   public getRadius(): number {
>     return (this.peg.getWidth() * Math.sqrt(2)) / 2;
>   }
> }
> ```
> 
> **Cliente**
> ```ts
> const hole = new RoundHole(5);
> const roundPeg = new RoundPeg(5);
> 
> console.log("¿Encaja la pieza redonda?", hole.fits(roundPeg)); // true
> 
> const smallSquarePeg = new SquarePeg(5);
> const largeSquarePeg = new SquarePeg(10);
> 
> // Usamos adaptadores
> const smallSquareAdapter = new SquarePegAdapter(smallSquarePeg);
> const largeSquareAdapter = new SquarePegAdapter(largeSquarePeg);
> 
> console.log("¿Encaja el cuadrado chico?", hole.fits(smallSquareAdapter)); // true
> console.log("¿Encaja el cuadrado grande?", hole.fits(largeSquareAdapter)); // false
> ```
> 

---

## Cuándo usar Adapter

Usalo cuando:
- Querés usar una clase existente pero su interfaz no coincide con la que necesitás.
- Querés reutilizar clases sin modificar su código.
- Necesitás integrar librerías externas o legacy.

---

## Pros y contras

**Pros**
- Permite reutilizar código existente sin modificarlo.
- Cumple el principio abierto/cerrado.
- Aísla la conversión de datos en una sola clase.

**Contras**
- Aumenta la complejidad agregando nuevas clases.
- Puede sumar una capa extra de abstracción innecesaria si no hacía falta.

---

## Relación con otros patrones

- Suele confundirse con **Facade**, pero:
    - Facade simplifica una interfaz compleja.
    - Adapter **convierte** una interfaz en otra.
- Puede combinarse con **Decorator** o **Proxy** si necesitás agregar comportamiento además de adaptar.