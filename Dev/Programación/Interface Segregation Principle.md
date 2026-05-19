---
tags:
  - Programación
  - ProgramaciónII
---
Los clientes **no deberían verse obligados a implementar métodos que no usan**.  
En vez de una interfaz gigante, conviene tener **interfaces pequeñas y específicas**.

---

> [!error]
> ```ts
> interface Worker {  
> 	work(): void;  
> 	eat(): void;
> }
> 
> class Human implements Worker {  
> 	work(): void {    
> 		console.log("Trabajando");  
> 	}  
> 	eat(): void {    
> 		console.log("Comiendo");  
> 	}
> }
> 
> class Robot implements Worker {  
> 	work(): void {    
> 		console.log("Trabajando");  
> 	}  
> 	eat(): void {    
> 		// Un robot no come...    throw new Error("Robots don't eat");  
> 	}
> }
> ```
> 
> ###### Problema:
> El robot está obligado a implementar `eat()` aunque no tiene sentido.  
> La interfaz es demasiado grande.


> [!check]
> 
> Separamos responsabilidades en interfaces chicas:
> 
> ```ts
> interface Workable {  
> 	work(): void;
> }
> 
> interface Eatable {  
> 	eat(): void;
> }
> ```
> 
> Ahora cada clase implementa solo lo que necesita:
> ```ts
> class Human implements Workable, Eatable {  
> 	work(): void {    
> 		console.log("Trabajando");  
> 	}  
> 	eat(): void {    
> 		console.log("Comiendo");  
> 	}
> }
> 
> class Robot implements Workable {  
> 	work(): void {    
> 		console.log("Trabajando");  
> 	}
> }
> ```
> 
> Ahora ninguna clase implementa cosas inútiles.
> 
