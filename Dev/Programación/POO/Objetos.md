---
tags:
  - Programación
  - ProgramaciónII
---
Un objeto es una estructura que **agrupa datos y comportamientos mediante propiedades y métodos**.

En Programación Orientada a Objetos, un objeto puede ser una **instancia concreta de una clase**. Sin embargo, en lenguajes como **JavaScript y TypeScript también pueden existir objetos creados directamente, sin una clase**.

---

### Características del objeto

#### Ambiente
Es el contexto donde existen y se relacionan los objetos.

#### Comportamiento
Conjunto de acciones que el objeto puede realizar o responder.

#### Exhibe
Es lo que el objeto puede mostrar o permitir que otros objetos le soliciten mediante mensajes.

---

### Comunicación entre objetos

Un objeto puede interactuar con otros objetos mediante sus propiedades y métodos.

```
Objeto A ---> interacción ---> Objeto B
```

---

### Creación de objetos

#### A partir de una clase

Se utiliza `new` para crear una instancia de una clase:

```
const miObjeto = new NombreClase();
```

```
Clase → new → Objeto
```

#### Sin una clase: objeto literal

En JavaScript y TypeScript también se puede crear un objeto directamente utilizando `{ }`:

```
const persona = {
  nombre: 'Eliana',
  edad: 38,
};
```

Esto se llama **objeto literal**.

Su estructura básica es:

```
{
  propiedad: valor,
  propiedad: valor,
}
```

Por ejemplo:

```
const usuario = {
  username: 'Eliana',
  passwordLength: 8,
};
```

---

### Acceso a miembros del objeto

Las propiedades y métodos de un objeto pueden accederse mediante el operador punto (`.`):

```
persona.nombre;
miObjeto.metodo();
```

---

### Para recordar

```
Objeto creado desde una clase:
new NombreClase()

Objeto creado directamente:
{ propiedad: valor }

Los dos son objetos.
```


---

