---
tags:
  - Programación
  - ProgramaciónII
---
Se utiliza para hacer referencia a la **clase padre (superclase)** desde una clase hija.

Permite acceder a:
- el **constructor** de la clase padre
- métodos de la clase padre

```ts
constructor (apellido:s, nombre:s, edad:n, legajo:s){

	super(apellido, nombre, edad); // Llama al constructor de la clase padre (Persona)
	this._legajo = legajo; // Propiedad propia de la clase hija (Alumno)
	
}
```

La palabra `super` permite invocar miembros de la clase base desde la clase derivada.

```ts
super.sayHi(); //Ejecuta sayHi() de la clase padre.
```

> En TypeScript, las clases hijas **deben llamar obligatoriamente a `super()` en su constructor** antes de poder usar `this`.
