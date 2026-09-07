La **autenticación** y la **autorización** son conceptos relacionados, pero tienen objetivos diferentes.

Ambos mecanismos agregan capas de seguridad a una API REST.

---

### Autenticación

La autenticación responde a la pregunta:

> **¿Quién eres?**

Su objetivo es **identificar al usuario o cliente** que intenta acceder a la API y comprobar que se trata de una identidad válida.

Los métodos de autenticación tratados en la clase son:

- [[Basic Authentication]]
- [[Digest Authentication]]
- [[JWT]]

---

### Autorización

La autorización responde a la pregunta:

> **¿Qué puedes hacer?**

Su objetivo es comprobar qué **acciones y recursos puede utilizar un usuario que ya fue autenticado**.

Por ejemplo, un usuario puede tener permiso para leer y modificar productos, pero no para eliminarlos.

---

### Diferencia

|     Concepto      |      Pregunta      |             Objetivo             |
| :---------------: | :----------------: | :------------------------------: |
| **Autenticación** |    ¿Quién eres?    | Identificar al usuario o cliente |
| **Autorización**  | ¿Qué puedes hacer? |      Verificar sus permisos      |

La **autenticación** identifica al usuario, mientras que la **autorización** determina qué puede hacer dentro del sistema.

---
