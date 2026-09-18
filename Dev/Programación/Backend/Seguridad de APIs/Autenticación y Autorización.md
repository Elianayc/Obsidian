La **autenticación** y la **autorización** son conceptos relacionados, pero tienen objetivos diferentes.
Ambos mecanismos agregan capas de seguridad a una API REST.

---

### Autenticación

La autenticación responde a la pregunta:

> **¿Quién sos?**

Su objetivo es **identificar al usuario o cliente** que intenta acceder a la API y comprobar que se trata de una identidad válida.
    
La autenticación ocurre **antes de la autorización**: primero se verifica quién es el usuario y luego qué permisos tiene.

#### Métodos de autenticación
Los principales métodos son:

- **[[Basic Authentication]]** → envía usuario y contraseña en cada solicitud, codificados en Base64.
- **[[Digest Authentication]]** → utiliza un mecanismo de desafío-respuesta para evitar enviar directamente la contraseña.
- **[[JWT]]** → utiliza un token firmado que el cliente envía en las solicitudes posteriores.
    
> **Importante:** Base64 es una **codificación**, no un mecanismo de cifrado. Por eso Basic Authentication debe utilizarse junto con **HTTPS**.

> **Importante:** el payload de un JWT **no está cifrado**. Está codificado y puede ser leído por quien tenga el token. La firma permite detectar si fue modificado.


---

### Autorización

La autorización responde a la pregunta:

> **¿Qué podés hacer?**

Su objetivo es comprobar qué **acciones y recursos puede utilizar un usuario que ya fue autenticado**.

Por ejemplo, un usuario puede tener permiso para leer y modificar productos, pero no para eliminarlos.

La autorización suele basarse en **roles o permisos**.

---

### Diferencia

|   **Concepto**    |   **Pregunta**    |           **Objetivo**            |
| :---------------: | :---------------: | :-------------------------------: |
| **Autenticación** |    ¿Quién sos?    | Identificar al usuario o cliente. |
| **Autorización**  | ¿Qué podés hacer? |      Verificar sus permisos.      |

---

