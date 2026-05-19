---
tags:
  - Programación
  - ProgramaciónII
---
Una clase debe estar **abierta para extender** pero **cerrada para modificar**.  

O sea: cuando agregás comportamiento nuevo, **no rompés ni tocás lo que ya funciona**. Solo agregás cosas nuevas.

---

> [!error]
> 
> ```ts
> // Cada vez que agrego una forma nueva… tengo que editar la clase
> class AreaCalculator {  
> 	calculate(shape: any): number {    
> 		if (shape.type === "circle") {      
> 		return Math.PI * shape.radius * shape.radius;    
> 		}    
> 		
> 		if (shape.type === "square") {      
> 		return shape.side * shape.side;    
> 		}    
> 	return 0;  
> 	}
> }
> ```
> 
> ###### Problema:  
> Si mañana aparece **Triangle**, tengo que volver a abrir la clase y meter otro `if`.  
> Y así para siempre. Es frágil y crece horrible.


> [!check]
> Primero definimos una “forma” general:
> ```ts
> interface Shape {  
> 	area(): number;
> }
> ```
> 
> Ahora cada figura se calcula sola:
> ```ts
> class Circle implements Shape {  
> 	constructor(private radius: number) {}  
> 	
> 	area(): number {    
> 		return Math.PI * this.radius * this.radius;  
> 	}
> }
> 
> class Square implements Shape {  
> 	constructor(private side: number) {}  
> 	
> 	area(): number {    
> 		return this.side * this.side;  
> 	}
> }
> ```
> 
> Y el calculador ya **no necesita cambiar nunca**
> ```ts
> class AreaCalculator {  
> 	calculate(shape: Shape): number {    
> 		return shape.area();  
> 	}
> }
> ```
> 
> Si mañana aparece **Triangle** solo agregás una clase nueva:
> ```ts
> class Triangle implements Shape {  
> 	constructor(private base: number, private height: number) {}  
> 	
> 	area(): number {    
> 		return (this.base * this.height) / 2;  
> 	}
> }
> ```
> 


