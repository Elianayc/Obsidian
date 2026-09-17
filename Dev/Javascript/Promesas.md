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

## Creación de una Promise

Una Promise recibe dos funciones:
- **`resolve()`** → indica que la operación terminó correctamente.
- **`reject()`** → indica que la operación falló.
   
```javascript
const miPromesa = new Promise(function(resolve, reject) {
    const exito = true;

    if (exito) {
        resolve("Operación completada con éxito");
    } else {
        reject("Error en la operación");
    }

});
```

En este ejemplo:

1. `new Promise()` crea una nueva Promise.
2. `resolve` y `reject` son las dos funciones que recibe.
3. Si `exito` es `true`, se ejecuta `resolve()`.
4. Si `exito` es `false`, se ejecuta `reject()`.
    
---
## Uso de la Promise

Los principales métodos para usar una Promise son:

- **`.then()`** → recibe un **callback** para manejar el resultado exitoso.
- **`.catch()`** → recibe un **callback** para manejar el error.
- **`.finally()`** → recibe un **callback** que se ejecuta al finalizar, independientemente del resultado.
    
```javascript
miPromesa
    .then(function(resultado) {
        console.log(resultado);
    })
    .catch(function(error) {
        console.error(error);
    })
    .finally(function() {
        console.log("Promesa finalizada");
    });
```

En este caso:

- `.then()` recibe un callback que recibe el resultado enviado por `resolve()`.
- `.catch()` recibe un callback que recibe el error enviado por `reject()`.
- `.finally()` recibe un callback que se ejecuta siempre, tanto si la Promise tuvo éxito como si falló.

> **Nota:** también es posible escribir estos callbacks utilizando la sintaxis de **funciones flecha (`=>`)**, pero primero conviene entender la forma tradicional con `function`.

---

## Encadenamiento de Promises

Las **Promises pueden encadenarse** para ejecutar operaciones asincrónicas de manera secuencial.
Cada operación devuelve una Promise, y el siguiente `.then()` recibe el resultado de la operación anterior.

```javascript
login(usuario, password)
    .then(token => obtenerPerfil(token))
    .then(perfil => obtenerConversaciones(perfil.id))
    .then(conversaciones => obtenerMensajes(conversaciones[0].id))
    .catch(error => manejarError(error));
```

El flujo sería:

```text
login()
   ↓ devuelve token
then → obtenerPerfil(token)
   ↓ devuelve perfil
then → obtenerConversaciones(perfil.id)
   ↓ devuelve conversaciones
then → obtenerMensajes(...)
   ↓
catch → manejar error
```

Cada `.then()` recibe un **callback** para manejar el resultado exitoso de la Promise anterior.

Además, ese callback puede devolver otra Promise. De esta manera, el siguiente `.then()` recibe el resultado de esa nueva operación y puede continuar el proceso.

---

## ¿Por qué usar Promises en lugar de callbacks?

Con callbacks, las operaciones pueden quedar **anidadas unas dentro de otras**:

```javascript
login(usuario, password, function(token) {
    obtenerPerfil(token, function(perfil) {
        obtenerConversaciones(perfil.id, function(conversaciones) {
            obtenerMensajes(conversaciones[0].id, function(mensajes) {
                // Continuar...
            });
        });
    });
});
```

Con Promises, las operaciones se pueden escribir **una después de otra**, evitando ese anidamiento:

```javascript
login(usuario, password)
    .then(token => obtenerPerfil(token))
    .then(perfil => obtenerConversaciones(perfil.id))
    .then(conversaciones => obtenerMensajes(conversaciones[0].id))
    .catch(error => manejarError(error));
```

Por eso, el código suele resultar más fácil de leer y mantener.

> **Importante:** `.then()` está pensado para manejar el **resultado exitoso de la Promise anterior**. El error puede manejarse mediante `.catch()`, que puede capturar un error producido durante cualquiera de las operaciones de la cadena.

Se pueden encadenar tantos `.then()` como sean necesarios para realizar los distintos pasos de una operación.


## Encadenamiento de Promises

Las **Promises pueden encadenarse** para ejecutar operaciones asincrónicas de manera secuencial.

Cada operación devuelve una Promise, y el siguiente `.then()` puede utilizar el resultado de la operación anterior.

```javascript
login(usuario, password)
    .then(function(token) {
        return obtenerPerfil(token);
    })
    .then(function(perfil) {
        return obtenerConversaciones(perfil.id);
    })
    .then(function(conversaciones) {
        return obtenerMensajes(conversaciones[0].id);
    })
    .catch(function(error) {
        manejarError(error);
    });
```

El flujo sería:

```text
login()
   ↓ devuelve token
then → obtenerPerfil(token)
   ↓ devuelve perfil
then → obtenerConversaciones(perfil.id)
   ↓ devuelve conversaciones
then → obtenerMensajes(conversaciones[0].id)
   ↓
catch → manejar cualquier error
```

Cada `.then()` **recibe un callback para manejar el resultado exitoso de la Promise anterior**.

Además, ese callback puede **devolver otra Promise**, permitiendo continuar el encadenamiento.

### ¿Por qué es mejor que anidar callbacks?

Con callbacks, las operaciones se pueden ir metiendo unas dentro de otras:

```javascript
login(usuario, password, function(token) {

    obtenerPerfil(token, function(perfil) {

        obtenerConversaciones(perfil.id, function(conversaciones) {

            obtenerMensajes(conversaciones[0].id, function(mensajes) {

                // Continuar...

            });
        });
    });
});
```

Con Promises, las operaciones se escriben **una después de otra**, sin anidar tantas funciones:

```javascript
login(usuario, password)
    .then(function(token) {
        return obtenerPerfil(token);
    })
    .then(function(perfil) {
        return obtenerConversaciones(perfil.id);
    })
    .then(function(conversaciones) {
        return obtenerMensajes(conversaciones[0].id);
    });
```

Por eso el código resulta más fácil de leer y mantener.

> **Importante:** `.then()` está pensado para manejar el **éxito de la Promise anterior**. Los errores pueden manejarse mediante `.catch()`, que puede capturar un error producido en cualquiera de las operaciones de la cadena.

Se pueden encadenar tantos `.then()` como sean necesarios para completar los pasos de una operación.

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
