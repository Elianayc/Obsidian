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

> Una función declarada con `async` siempre devuelve una Promise. El valor que retorna la función se convierte en el resultado de esa Promise.

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
