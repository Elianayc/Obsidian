---
tags:
  - Programación
  - ProgramaciónII
---
Los métodos son **funciones definidas dentro de una clase** que representan el **comportamiento del objeto**.

Permiten que el objeto realice acciones, procese datos o interactúe con otros objetos.

---

### Características de los métodos:
- Pueden recibir **parámetros**
- Pueden devolver un **valor**
- Pueden acceder a los **atributos de la clase**
- Utilizan `this` para referirse a la instancia actual
- Definen el **comportamiento del objeto**

---

### Estructura básica
```ts
nombreMetodo(parametros): tipoRetorno {...}
```

---

### Ejemplo
```ts
class Person {  
	name: string;  sayHi(): void {    
		console.log("Hola, soy " + this.name);  
	}
}
```

---

### Tipos de métodos
- **Métodos de instancia** → pertenecen al objeto
- **Métodos estáticos** → pertenecen a la clase (no al objeto)

---

### Acceso a atributos
Los métodos pueden leer y modificar el estado del objeto:

```ts
setName(name: string): void {this.name = name;}
```

---

#### Conceptos relacionados:
- [[Sobreescritura]]
- [[Sobrecarga]]
#Programación