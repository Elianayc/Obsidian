El polimorfismo es la capacidad que tienen los objetos de **responder de distintas formas ante el mismo llamado o mensaje**. 

Se basa en la idea de que una misma operación puede comportarse de manera diferente según el tipo de objeto que la ejecute.

El polimorfismo ocurre cuando se implementan comportamientos distintos para una misma firma de método.

---

### Formas de polimorfismo

##### Sobrescritura (override)  
Permite polimorfismo dentro de una **misma jerarquía de clases**. 
Una clase hija redefine un método de la clase padre para modificar su comportamiento.
```ts
class Animal {
  speak(): void {console.log("Sonido genérico");}
}

class Dog extends Animal {
  override speak(): void {console.log("Guau");}
}
```

##### Interfaces  
Permiten polimorfismo entre objetos que no necesariamente pertenecen a la misma jerarquía de clases, pero que comparten un mismo contrato de comportamiento definido por la **interfaz**.
```ts
interface IFlyable {
  fly(): void;
}

class Bird implements IFlyable {
  fly(): void {console.log("Volando");}
}

class Airplane implements IFlyable {
  fly(): void {console.log("Avión volando");}
}
```


##### Composición  
Permite variar el comportamiento de un objeto en tiempo de ejecución utilizando **otros objetos internos**, delegando responsabilidades.
```ts
class Engine {
  start(): void {console.log("Motor encendido");}
}

class Car {
  constructor(private engine: Engine) {}

  start(): void {
    this.engine.start();
  }
}
```
