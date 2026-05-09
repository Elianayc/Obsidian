---
tags:
  - Programación
  - ProgramaciónII
---
Los miembros (métodos o atributos) estáticos son aquellos que pertenecen a la clase y no a una instancia.

Se utilizan sin necesidad de instanciar la clase.

Todo miembro que requiere la existencia de un objeto para ser accedido se denomina **miembro de instancia**, mientras que aquel que no lo requiere se denomina **miembro de clase**.

La palabra reservada **static** se utiliza para definir miembros de clase, lo que permite invocarlos directamente desde la clase.

---

## Comportamiento
Los miembros estáticos **no pertenecen a los objetos**, sino a la clase.

No se “**clonan**” en cada instancia, porque no forman parte del objeto.

Existe una única copia compartida por todas las instancias.


#### Acceso entre miembros
Un miembro de instancia puede acceder a miembros estáticos.

Un miembro estático **no puede acceder directamente a miembros de instancia**, porque no existe un objeto asociado.


#### Relación entre miembros estáticos
Los miembros estáticos pueden interactuar entre sí libremente, ya que pertenecen al mismo contexto de clase.

---

## Atributos estáticos
Los atributos estáticos pertenecen a la clase y no a las instancias. Se comparten entre todos los objetos y se acceden directamente desde la clase.

Frecuentemente los atributos estáticos se usan para definir valores constantes o compartidos a nivel de clase.


## ⚠ Diferencia importante

##### `const`
- La referencia no puede cambiar.
- Solo se usa en variables, no en miembros de clase como en tu idea general.

##### `readonly`
- El valor no puede modificarse una vez asignado.
- Se usa en propiedades de clase.

##### `static`
- Pertenece a la clase, no al objeto.


**En TypeScript es común usar:**
```ts
class Config {    
	static readonly MAX_USERS = 100;
}
```