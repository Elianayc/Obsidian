---
tags:
  - Programación
  - ProgramaciónII
---
### Constructor
Es el método que se ejecuta automáticamente al crear una instancia de una clase.

- La instrucción `new` reserva el espacio en memoria necesario para la instancia y ejecuta el constructor.
- Sigue las reglas de una función, con una excepción: **no tiene tipo de retorno**.
- Siempre se ejecuta, por lo que es ideal para realizar **inicializaciones obligatorias**.
- Si no se define, el lenguaje crea automáticamente un **constructor vacío por defecto**.

##### Ejemplo de constructor clásico
```ts
name: string;
lastname: string;
constructor(name: string, lastname: string) {	
	this.name = name;	
	this.lastname = lastname;
}
```

**Versión abreviada (TypeScript):**
```ts
constructor(public name: string, public lastname: string) {}
```

Si el constructor tiene parámetros, deben pasarse al crear el objeto:
```ts
const miVariable = new Person("Al", "Goritmo");
```

También puede existir un constructor sin parámetros:
```ts
miVariable: Person = new Person();
``````

#Programación