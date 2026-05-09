---
tags:
  - Programación
  - ProgramaciónII
---
Un objeto es una **instancia concreta de una clase**.  
Representa una entidad del mundo real dentro del programa y posee un comportamiento definido por su clase.

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
Objeto A envía un **mensaje** a Objeto B, y el objeto receptor debe ser capaz de interpretarlo y responder.

```
Objeto A ---> Mensaje ---> Objeto B
```

---

### Creación de un objeto
Un objeto se crea a partir de una clase utilizando la palabra reservada `new`.

```ts
miVariable: NombreClase = new NombreClase();
```

Esto reserva memoria e inicializa la instancia mediante el constructor.

---

### Acceso a miembros del objeto
Los atributos y métodos del objeto se acceden mediante el operador punto (`.`), llamado accesor.
```ts
miVariable.metodo();miVariable.atributo;
```


