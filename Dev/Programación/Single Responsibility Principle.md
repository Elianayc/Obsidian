---
tags:
  - Programación
  - ProgramaciónII
---
Una clase debe tener **una sola razón para cambiar**.  
Es decir, debe encargarse de **una única responsabilidad** dentro del sistema.

Si una clase mezcla varias tareas, cuando cambie cualquiera de ellas habrá que modificar esa clase → mala señal.

**Idea rápida:** una clase = un propósito.

#### Beneficios
- Código más simple y mantenible
- Menos dependencias
- Más fácil de testear

---

##### Ejemplo que No cumple con SRP
```ts
// Una sola clase hace TODO 
class Lamp {  
	turnOn() {
		console.log("Luz encendida");
	}  
	turnOff() {
		console.log("Luz apagada");
	}  
	saveStateToFile() {
		console.log("Guardando estado en archivo");
	}
}
```

###### Problema:  
La lámpara debería encargarse de **funcionar**, no de **guardar archivos**.  

###### Tiene dos motivos para cambiar:
1. Cambia cómo funciona la lámpara
2. Cambia cómo se guardan archivos

---

##### Versión que cumple con SRP
```ts
// Responsabilidad: comportamiento de la lámpara
class Lamp {
	turnOn() {
		console.log("Luz encendida");
	}  
	turnOff() {
		console.log("Luz apagada");
	}
}
	
// Responsabilidad: guardar datos
class FileStorage {
	save(text: string) {    
		console.log("Guardando:", text);  
	}
}
```

Ahora cada clase tiene **un solo motivo para cambiar**

Si cambia cómo guardar archivos → tocás `FileStorage`.  
Si cambia la lámpara → tocás `Lamp`.

---
