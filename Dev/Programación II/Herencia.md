---
tags:
  - Programación
  - ProgramaciónII
---
Es una relación de tipo **“es un” (is-a)**.  
Permite crear una clase nueva a partir de otra ya existente.

La clase hija **hereda** los miembros públicos y protegidos de la clase padre y puede utilizarlos como propios.

TypeScript permite **herencia simple** (una sola clase padre), al igual que Java.  
C++ permite **herencia múltiple**.

##### Ejemplo de jerarquía:
```
Person 
├─ Employee 
└─ ProviderEmployee
```

Para indicar herencia se usa la palabra reservada `extends`:

```ts
class Employee extends Person {}
class ProviderEmployee extends Person {}
```

##### La clase derivada puede:
- reutilizar comportamiento del padre.
- agregar nuevas funcionalidades.
- sobrescribir métodos heredados si lo necesita.


#### Conceptos Relacionados:
- [[Palabra super]]

##### Abstracción
- [[Clase Abstracta]]

##### Conversión de tipos
- [[Upcasting]]
- [[Downcasting]]