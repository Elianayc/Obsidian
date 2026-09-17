La evolución vista en clase puede resumirse así:

```text
Callbacks
    ↓
Callback Hell
    ↓
Promises
    ↓
Async / Await
```

### Callbacks
Permiten ejecutar una función cuando termina una operación, pero pueden producir código muy anidado.

### Promises
Representan el resultado eventual de una operación asincrónica y permiten encadenar operaciones.

### Async / Await
Utiliza Promises por debajo y permite escribir el código asincrónico de una manera más lineal y legible.

---

# Herramientas para comunicarse con el backend

|      Herramienta      |                        Característica principal                        |
| :-------------------: | :--------------------------------------------------------------------: |
|       **fetch**       |              API nativa del navegador, sin dependencias.               |
|       **Axios**       | Librería externa con una API más cómoda y funcionalidades adicionales. |
| **RxJS / HttpClient** | Mecanismo utilizado por Angular para trabajar con Observables y HTTP.  |

---

# Ideas clave

- JavaScript es **single-threaded**.
- El asincronismo permite evitar que operaciones lentas bloqueen el hilo principal.
- El **Event Loop** coordina la ejecución del código asincrónico.
- Los **callbacks** fueron una de las primeras formas de manejar asincronismo.
- El **Callback Hell** aparece cuando los callbacks se anidan excesivamente.
- Las **Promises** representan el resultado eventual de una operación asincrónica.
- Una Promise puede estar `Pending`, `Fulfilled` o `Rejected`.
- `async/await` utiliza Promises por debajo.
- `await` pausa la función `async`, pero **no bloquea el hilo principal**.
- `fetch()` devuelve una Promise.
- `fetch` no rechaza automáticamente una Promise ante respuestas HTTP 4xx o 5xx.
- `response.ok` permite comprobar si la respuesta HTTP fue exitosa.
- `response.json()` también devuelve una Promise.
- Axios simplifica varias tareas habituales de las solicitudes HTTP.
- Angular utiliza **RxJS y Observables** mediante `HttpClient`.
- Un Observable puede emitir múltiples valores, aunque una solicitud HTTP típica de Angular emite una respuesta y luego completa.

---