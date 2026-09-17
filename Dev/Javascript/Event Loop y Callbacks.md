
## Event Loop

El **Event Loop** es el mecanismo que permite coordinar la ejecución del código asincrónico en JavaScript.

Cuando aparece una operación que puede tardar, como un `fetch()` o un `setTimeout()`, esta se delega al navegador o al entorno de ejecución mientras JavaScript continúa ejecutando otras instrucciones.

> - **`fetch`** → es una función de JavaScript para hacer una solicitud a un servidor, por ejemplo pedir datos a una API.
> - **`setTimeout`** → permite decirle a JavaScript: **“ejecutá esta función después de cierto tiempo”**.

Cuando la operación termina, el código pendiente queda disponible para ser ejecutado. 
El Event Loop se encarga de comprobar cuándo el hilo principal está disponible y permite ejecutar esas tareas.

![[Pasted image 20260904121735.png]]

> - **queue** → una lista de tareas esperando ser procesadas.
> - **thread** → significa **hilo**. Es una secuencia de ejecución.
> - **thread pool** → un conjunto de hilos que el entorno puede utilizar para realizar determinadas tareas en paralelo.

```text
JavaScript ejecuta código
        ↓
Aparece una operación que puede tardar
(fetch, setTimeout, etc.)
        ↓
La operación se delega al navegador / entorno
        ↓
JavaScript continúa ejecutando otras instrucciones
        ↓
La operación termina
        ↓
El resultado queda pendiente de ejecución
        ↓
El Event Loop detecta que el hilo principal está disponible
        ↓
JavaScript ejecuta el código correspondiente
```

> **Idea clave:** JavaScript tiene un hilo principal que ejecuta una cosa por vez. Cuando aparece una operación que puede tardar, el entorno (por ejemplo, el navegador) puede encargarse de esa operación mientras JavaScript sigue trabajando.

---

### Ejemplo:

```JavaScript
console.log('Inicio');

setTimeout(() => {
    console.log('Terminó el timeout');
}, 1000);

console.log('Fin');
```

El resultado será:

```text
Inicio
Fin
Terminó el timeout
```

Aunque el `setTimeout()` aparece antes de `console.log('Fin')`, JavaScript no se queda esperando un segundo.

1. Imprime **Inicio**.
2. Encuentra `setTimeout` y le dice al navegador:  
    **"Avisame cuando haya pasado 1 segundo."**
3. **No se queda esperando.**
4. Continúa y ejecuta `console.log('Fin')`.
5. Pasa 1 segundo y el navegador dice:  
    **"La función del timeout ya está lista."**
6. Esa función queda en la **cola de tareas**.
7. El Event Loop ve que el hilo principal está libre.
8. La función entra al Call Stack y se ejecuta.
9. Imprime **Terminó el timeout**.
---

## Callbacks

Un **callback** es una función que se pasa como argumento a otra función para que sea ejecutada posteriormente, generalmente cuando una operación asincrónica termina.

Es una de las primeras formas utilizadas para manejar asincronismo en JavaScript.

```JavaScript
function obtenerConversaciones(callback) {
    setTimeout(() => {
        callback(['conv1', 'conv2', 'conv3']);
    }, 1000);
}

obtenerConversaciones(function(conversaciones) {
    console.log(conversaciones);
});
```

En este ejemplo:

1. Se llama a `obtenerConversaciones()`.
2. Se le pasa una función como callback.
3. La operación tarda un segundo.
4. Cuando termina, se ejecuta el callback.
5. El callback recibe las conversaciones.

![[Pasted image 20260904120921.png|681]]

---

## Callback Hell

Cuando una operación asincrónica depende del resultado de otra, los callbacks pueden comenzar a anidarse:

```JavaScript
login(usuario, password, function(token) {
    obtenerPerfil(token, function(perfil) {
        obtenerConversaciones(perfil.id, function(conversaciones) {
            obtenerMensajes(conversaciones[0].id, function(mensajes) {
                // etc...
            });
        });
    });
});
```

Esto se conoce como **Callback Hell**.

La lógica puede ser correcta, pero el código se vuelve:

- Difícil de leer.
- Difícil de mantener.
- Difícil de modificar.
- Más complicado de manejar cuando aparecen errores en cada nivel.

Este problema llevó al desarrollo de una abstracción más conveniente: las [[Promesas y Async Await]].

---
