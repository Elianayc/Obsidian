---
tags:
  - Programación
  - ProgramaciónII
---
Es una relación **fuerte** entre objetos.

Representa una relación de tipo **“está formado por”** (compuesto + componente).  
El objeto principal **depende completamente** del componente para existir.  
Si el objeto componente deja de existir, el objeto principal también deja de existir.

Se da cuando una clase tiene al menos un atributo cuyo tipo es otra clase (no primitivo), y ese componente es esencial para su existencia.

> [!example]
>
> Auto + Motor  
> El auto no puede existir sin su motor.
> 
> ```ts
> class Engine {
>   start(): void {
>     console.log("Motor encendido");
>   }
> }
> 
> class Car {
>   private engine: Engine;
> 
>   constructor() {
>     this.engine = new Engine();
>   }
> 
>   startCar(): void {
>     this.engine.start();
>     console.log("Auto en marcha");
>   }
> }
> ```
#Programación