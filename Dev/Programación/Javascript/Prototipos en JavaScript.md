JavaScript utiliza **prototipos** como mecanismo fundamental para implementar la **herencia y reutilización de propiedades y métodos entre objetos**.

> **Un prototipo también es un objeto.** La diferencia está en el **rol que cumple**, no en que sea un tipo diferente de objeto.

---

## ¿Qué es un prototipo?

Un **prototipo** es un objeto que está asociado a otro objeto y que JavaScript utiliza como **referencia para buscar propiedades y métodos que no encuentra directamente en ese objeto**.

Cuando JavaScript busca una propiedad o método:
1. Primero busca en el objeto.
2. Si no lo encuentra, busca en su prototipo.
3. Continúa por los prototipos siguientes hasta encontrarlo o llegar al final de la cadena.
    
Esta estructura se denomina **prototype chain** o **cadena de prototipos**.

---

## Objeto vs. prototipo

|                        Objeto                         |                               Prototipo                               |
| :---------------------------------------------------: | :-------------------------------------------------------------------: |
| Es una entidad que puede tener propiedades y métodos. |            También es un objeto con propiedades y métodos.            |
|        Puede representar una entidad concreta.        |  Cumple el rol de proporcionar propiedades y métodos a otro objeto.   |
|               Puede tener un prototipo.               | Es un objeto que está siendo utilizado como prototipo de otro objeto. |

Por lo tanto:

> **Todo prototipo es un objeto, pero no todo objeto está actuando como prototipo de otro objeto.**

La diferencia está en el **rol que cumple el objeto dentro de la relación**.

---

## Ejemplo

```javascript
const persona = {
    saludar() {
        console.log("Hola");
    }
};

const juan = Object.create(persona);

juan.saludar();
```

En este ejemplo:

```text
juan
  ↓
persona
```

`persona` y `juan` son ambos objetos, pero `persona` es el **prototipo de `juan`**.

Cuando ejecutamos:

```javascript
juan.saludar();
```

JavaScript:

1. Busca `saludar` en `juan`.
2. No lo encuentra.
3. Lo busca en su prototipo, `persona`.
4. Lo encuentra y lo ejecuta.
    
---

## Prototype chain

Los prototipos pueden formar una cadena:

```text
juan
  ↓
persona
  ↓
Object.prototype
  ↓
null
```

Si una propiedad no existe en `juan`, JavaScript continúa buscando en cada nivel de la cadena.

---

## Herencia por prototipos

Los prototipos permiten **reutilizar propiedades y métodos sin copiarlos** en cada objeto.

```text
juan
  ↓
persona
  ↓
métodos reutilizables
```

Por eso se habla de **herencia por prototipos** o **herencia por delegación**: si un objeto no encuentra algo en sí mismo, JavaScript delega la búsqueda a su prototipo.

---

## `Object.create()`

`Object.create()` permite crear un objeto indicando qué objeto será su prototipo:

```javascript
const persona = {
    saludar() {
        console.log("Hola");
    }
};

const juan = Object.create(persona);
```

Podemos consultar el prototipo con:

```javascript
Object.getPrototypeOf(juan);
```

---

## Conceptos clave

- **Objeto:** entidad que puede contener propiedades y métodos.
- **Prototipo:** objeto que actúa como referencia para buscar propiedades y métodos de otro objeto.
- **Prototype chain:** cadena de objetos que JavaScript recorre durante esa búsqueda.
- **Herencia por prototipos:** reutilización de propiedades y métodos mediante esa cadena.
- **Delegación:** cuando la búsqueda pasa del objeto al prototipo.
    
### Idea fundamental

> **Un prototipo no es algo distinto de un objeto. Es un objeto que cumple el rol de servir como referencia para otro objeto dentro de la cadena de prototipos.**

---

