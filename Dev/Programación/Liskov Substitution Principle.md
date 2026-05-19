---
tags:
  - Programación
  - ProgramaciónII
---
Una clase hija debe poder **reemplazar a su clase padre sin romper el programa**.

Si uso una clase base, debería poder usar cualquiera de sus hijas **sin tener que preocuparme** de que algo deje de funcionar.

> [!error]
> ```ts
> class Bird {  
> 	fly(): void {    
> 		console.log("Flying...");  
> 	}
> }
> 
> class Penguin extends Bird {  
> 	fly(): void {    
> 		throw new Error("Penguins can't fly 💀");  
> 	}
> }
> ```
> 
> ###### Problema:
> Un `Penguin` **no puede reemplazar** a `Bird`.  
> Si el programa espera un pájaro que vuele… explota en runtime.
> 
> La subclase rompe la promesa de la clase base.


> [!check]
> Separamos comportamientos correctamente:
> ```ts
> class Bird {}
> 
> class FlyingBird extends Bird {  
> 	fly(): void {    
> 		console.log("Flying...");  
> 	}
> }
> 
> class Sparrow extends FlyingBird {}
> class Penguin extends Bird {}
> ```
> 
> Ahora sí:
> - Si algo espera `FlyingBird` → puede volar
> - Si espera `Bird` → puede ser cualquiera
> 
> Ninguna subclase rompe el contrato.