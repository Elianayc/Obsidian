---
tags:
  - Programación
  - ProgramaciónII
---
Es un método que **se declara sin implementación** (sin cuerpo).

Solo define la **firma del método**, pero no su comportamiento.
- Debe estar dentro de una **clase abstracta**.
- Las clases que heredan están obligadas a **sobrescribirlo (override)** y definir su implementación.
- Sirve para establecer un “contrato” que las subclases deben cumplir.
- 
##### Ejemplo:
```ts
abstract class Animal {  
	abstract hacerSonido(): void; // Método abstracto (sin implementación)  
	moverse(): void {console.log("El animal se mueve");}
}

class Perro extends Animal {  
	hacerSonido(): void {console.log("Guau!");} //Implementación de Perro.
}

class Gato extends Animal {  
	hacerSonido(): void {console.log("Miau!");} //Implementación de Gato.
}
```

##### Uso:
```ts
const perro = new Perro();
perro.hacerSonido(); // Guau!
perro.moverse();     // El animal se mueve

const gato = new Gato();
gato.hacerSonido(); // Miau!
```