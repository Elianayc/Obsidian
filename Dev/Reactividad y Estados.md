La **reactividad** es el mecanismo mediante el cual un framework mantiene la **UI sincronizada con el estado** automáticamente.

Sin reactividad, el desarrollador debe actualizar manualmente el DOM cada vez que cambia un dato.

Con reactividad:

**Estado cambia → el framework detecta el cambio → la UI se actualiza**

El desarrollador declara qué debe mostrarse y el framework se encarga de actualizar el DOM.

### Implementación según el framework

- **React y Vue:** utilizan un **Virtual DOM**.
  1. El estado cambia.
  2. Se genera una nueva representación del Virtual DOM.
  3. Se compara con la anterior (*diffing*).
  4. Se aplican al DOM real únicamente los cambios necesarios (*patching*).

- **Angular:** utiliza **Change Detection** en lugar de Virtual DOM. Detecta cambios en el estado y actualiza el DOM de forma eficiente. Desde Angular 17, los **Signals** permiten una detección más granular.

---

# Estado

El **estado** es la información que un componente o una aplicación necesita recordar en un momento determinado para mostrar correctamente la UI.

Por ejemplo, en un chat:

- Usuario que inició sesión.
- Conversación seleccionada.
- Mensajes.
- Estado de carga.
- Errores.

Cuando el estado cambia, la reactividad permite que la UI se actualice automáticamente.

---

## Estado local

El **estado local** es información que pertenece a un único componente.

Puede incluir:

- Datos de formularios.
- Estados de carga.
- Estados de error.
- Listas que se muestran.
- Estado de la interfaz, como menús abiertos o elementos seleccionados.

### Cómo se declara

|  Framework  |       Mecanismo        |
| :---------: | :--------------------: |
| **Angular** |   Variables de clase   |
|  **React**  |      `useState()`      |
|   **Vue**   | `ref()` / `reactive()` |

Si un dato solo es necesario para un componente, normalmente debe mantenerse como **estado local**.

---

## Estado local y Props

Cuando un componente hijo necesita información que pertenece al padre, el padre puede pasarle su estado mediante **props**.

**Estado del padre cambia → framework detecta el cambio → se actualiza la UI y los hijos que reciben ese estado.**

Esto permite compartir estado entre componentes relacionados sin duplicar la información.

---

# Estado global

El **estado global** contiene datos compartidos por múltiples componentes de una aplicación o de una parte de ella.

El principio es:

> **Un dato, un lugar, muchos consumidores.**

Por ejemplo, en un chat, la conversación activa puede ser utilizada tanto por el `Sidebar` como por el `MensajesPanel`.

### Cómo se implementa

|  Framework  |             Mecanismo              |
| :---------: | :--------------------------------: |
| **Angular** | Servicios con `providedIn: 'root'` |
|  **React**  |            Context API             |
|   **Vue**   |               Pinia                |

**Importante:** no todo el estado debe ser global. Solo se utiliza para datos que realmente necesitan compartir varios componentes. El resto debe mantenerse como estado local.

---

# Conceptos adicionales

Son conceptos que pueden aparecer en proyectos reales a medida que crecen:

- **Provide / Inject:** permite compartir datos entre componentes de una misma rama del árbol sin pasar props por todos los componentes intermedios.
- **Contenedor / Presentacional:** separa componentes que manejan lógica y servicios de aquellos que solamente muestran datos.
- **Memoización:** evita cálculos o renderizados innecesarios cuando los datos relevantes no cambiaron.
- **Code splitting:** divide el código JavaScript en archivos más pequeños para cargar solamente lo necesario.
- **Lazy loading:** permite cargar el código de una ruta o funcionalidad únicamente cuando se necesita.
- **Inmutabilidad:** consiste en no modificar directamente determinados estados, sino reemplazarlos por una nueva versión. Es especialmente importante en React.

Estos conceptos son complementarios y suelen aparecer a medida que los proyectos aumentan de tamaño.

---

