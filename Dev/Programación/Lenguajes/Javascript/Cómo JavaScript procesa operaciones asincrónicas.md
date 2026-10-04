JavaScript es un lenguaje de programación de un solo hilo (**single-threaded**), lo que significa que tiene un único hilo principal de ejecución y puede ejecutar una instrucción a la vez.

Esto funciona bien para la mayoría de las operaciones, pero puede generar problemas cuando una tarea tarda mucho tiempo, por ejemplo:

- Realizar una solicitud HTTP.
- Esperar una respuesta de un servidor.
- Consultar una base de datos.
- Leer o escribir un archivo.
- Esperar un temporizador.
    

Si JavaScript tuviera que esperar bloqueado hasta que estas operaciones terminaran, la interfaz quedaría congelada y el usuario no podría interactuar con la aplicación.

Para evitarlo, JavaScript utiliza un **modelo de programación asincrónica**, que permite continuar ejecutando otras instrucciones mientras se completan operaciones potencialmente lentas.

Cuando estas operaciones terminan, JavaScript ejecuta el código correspondiente para manejar su resultado.

---

- [[Event Loop y Callbacks]]
- [[Promesas]]
- [[Async - Await]]
- [[Llamadas HTTP - Fetch y Axios]]
- [[RxJS y Observables en Angular]]
- [[Evolución del Asincronismo]]

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

