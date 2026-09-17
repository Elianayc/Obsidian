
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

> JavaScript tiene un hilo principal que ejecuta una cosa por vez. Cuando aparece una operación que puede tardar, el entorno (por ejemplo, el navegador) puede encargarse de esa operación mientras JavaScript sigue trabajando.

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

![[Pasted image 20260904120921.png|681]]


### Ejemplo explicado

```js
// Función que será utilizada como callback.
function avisarFin() {
    console.log("La operación terminó");
}

// Función que recibe una función (Callback) como parámetro.
function hacerAlgo(callback) {
    setTimeout(function() { // Simulamos una operación que tarda un segundo.
        callback(); // Ejecutamos la función recibida.
    }, 1000);
}

// Pasamos la función avisarFin como argumento.
hacerAlgo(avisarFin);
```

En este ejemplo:

1. Se define la función `avisarFin()`.
2. Se define `hacerAlgo()`, que recibe una función mediante el parámetro `callback`.
3. Se llama a `hacerAlgo(avisarFin)`.
4. La función `avisarFin` queda almacenada en el parámetro `callback`.
5. `setTimeout()` espera un segundo.
6. Cuando termina la espera, `callback()` ejecuta la función `avisarFin()`.
7. Se muestra `"La operación terminó"` en la consola.

> **Importante:** `callback` no es una palabra reservada de JavaScript. Es simplemente el nombre convencional que se utiliza para el parámetro que recibe la función que será ejecutada posteriormente.


### Forma de uso más común

En código JavaScript es muy habitual pasar directamente una **función anónima** como callback cuando esa función solamente se necesita en ese lugar:

```js
function hacerAlgo(callback) {
    setTimeout(function() {
        callback();
    }, 1000);
}

hacerAlgo(function() {  //Función anónima que hace lo mismo que avisarFin() .
    console.log("La operación terminó");
});
```

Esta versión hace lo mismo que la anterior. La diferencia es que la función que se ejecuta al finalizar **no tiene un nombre propio**, porque se utiliza únicamente como callback.


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
