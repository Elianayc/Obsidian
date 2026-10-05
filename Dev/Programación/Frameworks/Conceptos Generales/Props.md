Las **props** son datos que un componente padre proporciona a un componente hijo.

El flujo es:

```
PADRE
  │
  │ dato
  ▼
HIJO
```

Por eso se habla de un flujo **unidireccional de datos**.

---

## Ejemplo

```
App
 │
 │ usuario
 ▼
Header
```

`App` posee el dato `usuario` y se lo proporciona a `Header`.

El componente hijo puede utilizar ese dato para construir su interfaz.

---

## ¿Por qué utilizar props?

Permiten:

- Reutilizar componentes con diferentes datos.
- Mantener claro de dónde proviene cada dato.
- Separar las responsabilidades entre componentes.
- Mantener un flujo de información predecible.
   
El hijo no debería modificar directamente el dato recibido del padre.
Si necesita comunicar algo hacia el padre, normalmente utiliza un **evento**.

```
PADRE
  │
  │ props
  ▼
HIJO

PADRE
  ▲
  │ evento
  │
HIJO
```

La implementación concreta depende del framework.

Ver:

- [[Comunicación entre Componentes en Angular]]
- [[React]]
- [[Vue]]

---
