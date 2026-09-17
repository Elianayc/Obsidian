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
- [[Promesas y Async Await]]
- [[Llamadas HTTP Fetch y Axios]]
- [[RxJS y Observables en Angular]]

---

