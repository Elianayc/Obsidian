El **renderizado de listas** consiste en generar un componente o elemento de interfaz por cada elemento de un array.

Los tres frameworks proporcionan mecanismos para realizarlo:

|  Framework  |      Mecanismo       |
| :---------: | :------------------: |
| **Angular** | `*ngFor` + `trackBy` |
|  **React**  |   `.map()` + `key`   |
|   **Vue**   |   `v-for` + `:key`   |

### `key` / `trackBy`

Permite al framework identificar qué elemento de una lista cambió y actualizar solamente ese nodo del DOM, en lugar de volver a renderizar toda la lista.

---

# Renderizado condicional

Permite mostrar determinados elementos de la interfaz únicamente cuando se cumple una condición.

|  Framework  |        Mecanismo         |
| :---------: | :----------------------: |
| **Angular** |         `*ngIf`          |
|  **React**  | `if` / operador ternario |
|   **Vue**   |    `v-if` / `v-else`     |

Por ejemplo, se puede mostrar:

- Un mensaje de **“Cargando...”** mientras se obtienen datos.
    
- Un mensaje de **“Sin resultados”** cuando una lista está vacía.
    
- Una sección determinada únicamente cuando el usuario está autenticado.

---
