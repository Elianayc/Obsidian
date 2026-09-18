---
tags:
  - Programación
  - ProgramaciónII
---
Los módulos de alto nivel **no deben depender de implementaciones concretas**, sino de **abstracciones**.  
Y las implementaciones concretas dependen de esas abstracciones.

Dicho en criollo: la lógica importante no debería depender de “cosas concretas”, sino de **interfaces**.

> [!error]
> ```ts
> class Lampara {  
> 	encender() {  
> 		console.log("Luz encendida");  
> 	}  
> }  
>   
> class Interruptor {  
> 	private lampara = new Lampara(); // depende de una clase concreta  
> 	  
> 	operar() {  
> 		this.lampara.encender();  
> 	}  
> }
> ```
> 
> ###### Problema:
> La clase **Interruptor** depende directamente de una implementación concreta (`Lampara`).  
> Esto hace que el interruptor solo sirva para encender una lámpara.
> 
> Si mañana queremos encender un ventilador, una estufa u otro dispositivo, tendremos que **modificar la clase Interruptor**, lo que la vuelve rígida y poco reutilizable.
> 
> El módulo de alto nivel (Interruptor) no debería depender de clases concretas.

> [!check]
> Primero definimos una **abstracción** (una interfaz que representa cualquier dispositivo encendible):
> ```ts
> interface Encendible {  
> 	encender(): void;
> }
> ```
> 
> Ahora las clases concretas dependen de esa abstracción:
> ```ts
> class Lampara implements Encendible {  
> 	encender() {  
> 		console.log("Luz encendida");  
> 	}  
> }  
>   
> class Ventilador implements Encendible {  
> 	encender() {  
> 		console.log("Ventilador encendido");  
> 	}  
> }
> ```
> 
> Finalmente, el módulo principal depende de la **interfaz**, no de una clase concreta:
> ```ts
> class Interruptor {  
> 	constructor(private dispositivo: Encendible) {}  
> 	  
> 	operar() {  
> 		this.dispositivo.encender();  
> 	}  
> }
> ```
> 
> Uso:
> ```ts
> const interruptorLampara = new Interruptor(new Lampara());  
> interruptorLampara.operar();  
>   
> const interruptorVentilador = new Interruptor(new Ventilador());  
> interruptorVentilador.operar();
> ```
> 
> Ahora **Interruptor** es flexible y reutilizable.
> Puede trabajar con cualquier dispositivo que implemente `Encendible` sin necesidad de modificar la clase.
#Programación