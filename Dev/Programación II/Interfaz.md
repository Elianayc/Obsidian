Una interfaz define el **comportamiento que deben cumplir las clases** que la implementan, estableciendo un **contrato común** entre distintas implementaciones.

Describe únicamente las **firmas de los métodos**, sin incluir su implementación.

Permite modelar objetos que pueden o no pertenecer a la misma jerarquía de clases, pero que comparten comportamientos.

---

### Idea conceptual
- La clase define la **fisionomía** de un objeto (cómo es)
- La interfaz define su **comportamiento** (qué puede hacer)

---

### Ejemplos conceptuales
- Encendible
- Apagable

---

### Ejemplo en TypeScript
```ts
interface ITurnable {  
	turnOn(): boolean;  
	turnOff(): boolean;
}
```

---

### Implementación
Las clases que implementan una interfaz deben utilizar la palabra clave `implements`, seguida del nombre de la interfaz.

Si se implementan varias interfaces, se separan con comas.

Todos los métodos definidos en la interfaz deben ser **implementados obligatoriamente**.

```ts
class Engine implements ITurnable {  
	turnOn(): boolean {return true;}  
	turnOff(): boolean {return false;}
}
```

---

### Relación con polimorfismo
Las interfaces permiten tratar objetos no solo por su clase, sino por su **comportamiento común**.
Esto habilita el uso de **polimorfismo basado en interfaces**.

---

### Conversión de tipos
También es posible tratar un objeto según una interfaz utilizando `as`.

```ts
const obj = engine as ITurnable;
```