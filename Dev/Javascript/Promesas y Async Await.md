## Promesas

Las **Promises** son objetos que representan el resultado eventual de una operación asincrónica.

Permiten trabajar con operaciones potencialmente lentas sin bloquear el hilo principal.

Una Promise puede estar en uno de tres estados:

- **Pending:** la operación todavía no terminó.
- **Fulfilled:** la operación terminó correctamente y tiene un valor resultante.
- **Rejected:** la operación falló y tiene un motivo de error.
    
Una Promise que ya terminó, tanto si fue exitosa como si falló, se encuentra en estado **settled**.

```text
             ┌── Fulfilled
Pending ─────┤
             └── Rejected

Fulfilled / Rejected = Settled
```

---

## Creación y uso de Promises

Una Promise recibe dos funciones:

- `resolve()` → indica que la operación terminó correctamente.  
- `reject()` → indica que la operación falló.

```JavaScript
const miPromesa = new Promise((resolve, reject) => {
    const exito = true;

    if (exito) {
        resolve('Operación completada con éxito');
    } else {
        reject('Error en la operación');
    }
});

miPromesa
    .then((resultado) => {
        console.log(resultado);
    })
    .catch((error) => {
        console.error(error);
    })
    .finally(() => {
        console.log('Promesa finalizada');
    });
```

Los principales métodos para consumir una Promise son:

- **`.then()`** → maneja el resultado exitoso.
- **`.catch()`** → maneja errores.
- **`.finally()`** → se ejecuta al finalizar, independientemente del resultado.
    
---

## Encadenamiento de Promises

Las Promises pueden encadenarse para ejecutar operaciones asincrónicas de manera secuencial.

```JavaScript
login(usuario, password)
    .then(token => obtenerPerfil(token))
    .then(perfil => obtenerConversaciones(perfil.id))
    .then(conversaciones => obtenerMensajes(conversaciones[0].id))
    .catch(error => manejarError(error));
```

Cada `.then()` recibe el resultado de la operación anterior.

Esto permite evitar el anidamiento excesivo de callbacks.

---

## Métodos estáticos de `Promise`

El objeto `Promise` proporciona métodos útiles para trabajar con múltiples Promises:

- **`Promise.all()`**: espera a que todas las Promises se resuelvan. Si una falla, el resultado completo falla.
    
- **`Promise.race()`**: termina cuando la primera Promise se resuelve o rechaza.
    
- **`Promise.allSettled()`**: espera a que todas terminen, independientemente de si se resolvieron o rechazaron.
    
- **`Promise.any()`**: se resuelve cuando cualquiera de las Promises se resuelve correctamente.
    

Para más información: [**MDN - Promise**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

---

## Async / Await

**Async/Await** es una sintaxis introducida en **ES2017** que facilita el trabajo con Promises.

No reemplaza las Promises: **las utiliza por debajo**.

Permite escribir código asincrónico de forma más lineal y legible, haciendo que su sintaxis se parezca a la del código sincrónico.

---

### Funciones `async`

Una función declarada con `async` **siempre devuelve una Promise**.

```JavaScript
async function miFuncionAsincronica() {
    return 'Hola Mundo';
}

miFuncionAsincronica()
    .then(resultado => console.log(resultado));
```

El valor retornado se convierte automáticamente en una Promise equivalente a:

```JavaScript
Promise.resolve('Hola Mundo');
```

Si la función lanza una excepción, la Promise que devuelve queda rechazada.

---

### Operador `await`

`await` permite esperar el resultado de una Promise.

```JavaScript
async function obtenerYProcesarDatos() {
    try {
        const datos = await obtenerDatos();

        const resultado = procesarDatos(datos);

        return resultado;

    } catch (error) {
        console.error('Error:', error);
        throw error;
    }
}
```

`await` pausa la ejecución de **esa función `async`** hasta que la Promise se resuelve.

Esto **no bloquea el hilo principal**. Mientras la función espera, JavaScript puede continuar procesando otras tareas.

> `await` no detiene todo JavaScript. Suspende la ejecución de esa función hasta obtener el resultado.

---

## Promises vs Async / Await

La misma lógica puede escribirse de ambas formas.

### Con Promises

```JavaScript
function cargarChat() {
    return login(usuario, password)
        .then(token => obtenerPerfil(token))
        .then(perfil => obtenerConversaciones(perfil.id))
        .catch(error => manejarError(error));
}
```

### Con Async / Await

```JavaScript
async function cargarChat() {
    try {
        const token = await login(usuario, password);
        const perfil = await obtenerPerfil(token);
        const conversaciones = await obtenerConversaciones(perfil.id);

        return conversaciones;

    } catch (error) {
        manejarError(error);
    }
}
```

`async/await` suele resultar más fácil de leer y depurar.

Actualmente es una de las formas más utilizadas para escribir código asincrónico, aunque es necesario comprender las Promises porque `async/await` funciona sobre ellas.

---

## Ventajas de Async / Await

- **Código más limpio y legible:** permite escribir operaciones asincrónicas de forma lineal.
    
- **Mejor manejo de errores:** permite utilizar `try/catch`.
    
- **Depuración más sencilla:** el flujo del código es más fácil de seguir.
    
- **Control de flujo simplificado:** facilita trabajar con condiciones, bucles y operaciones asincrónicas secuenciales.
    

---
