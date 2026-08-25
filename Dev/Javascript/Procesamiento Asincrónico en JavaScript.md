JavaScript es un lenguaje de programación de un solo hilo (**single-threaded**), lo que significa que solo puede ejecutar una instrucción a la vez.

Sin embargo, para no bloquear la ejecución del código durante operaciones que pueden llevar mucho tiempo, como solicitudes de red o lectura/escritura de archivos, JavaScript utiliza un **modelo de programación asincrónica**.

El procesamiento asincrónico permite que el código continúe ejecutándose mientras se completan estas operaciones potencialmente lentas en segundo plano.

Cuando estas operaciones finalizan, se ejecuta un **callback** o se resuelve una **promesa** para manejar el resultado.

---

# Promesas
Las **promesas** son objetos que representan el resultado eventual de una operación asincrónica.

Permiten ejecutar código potencialmente lento sin bloquear el hilo principal de ejecución.

Una promesa puede estar en uno de tres estados:
- **Pending:** estado inicial. La operación todavía no se ha completado.
- **Fulfilled:** la operación se completó con éxito y la promesa tiene un valor resultante.
- **Rejected:** la operación falló y la promesa tiene un motivo de error.

---

## Creación y uso de Promesas

```JavaScript
const miPromesa = new Promise((resolve, reject) => {
    // Operación asincrónica
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
        console.log('Promesa finalizada (con éxito o error)');
    });
```

---

# Encadenamiento de Promesas
Una de las principales ventajas de las promesas es que pueden ser **encadenadas**, facilitando el manejo de operaciones asincrónicas secuenciales.

```JavaScript
obtenerDatos(url)
    .then(datos => {
        return procesarDatos(datos);
    })
    .then(datosProcesados => {
        return mostrarResultados(datosProcesados);
    })
    .catch(error => {
        console.error('Error en alguna parte del proceso:', error);
    });
```

---

# El objeto `Promise` y sus métodos
El objeto `Promise` proporciona métodos estáticos útiles para trabajar con código asincrónico:

- **`Promise.all()`**: espera a que todas las promesas de un array se resuelvan.
- **`Promise.race()`**: se resuelve o rechaza tan pronto como se resuelva o rechace cualquiera de las promesas de un array.
- **`Promise.allSettled()`**: espera a que todas las promesas se completen, ya sea resueltas o rechazadas.
- **`Promise.any()`**: se resuelve tan pronto como se resuelva cualquiera de las promesas de un array.

Para más información: [**MDN - Promise**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

---

# Async / Await
**Async/Await** es una sintaxis introducida en **ES2017** que facilita el trabajo con promesas, haciendo que el código asincrónico se parezca, en su sintaxis, al código sincrónico.

## Funciones `async`
Una función `async` siempre devuelve una promesa.

Si la función retorna un valor, la promesa se resolverá con ese valor. Si la función lanza una excepción, la promesa se rechazará con ese error.

```JavaScript
async function miFuncionAsincronica() {
    return 'Hola Mundo';
}

miFuncionAsincronica().then(console.log);
```

El valor retornado se convierte automáticamente en una promesa equivalente a:

```JavaScript
Promise.resolve('Hola Mundo');
```
---

## Operador `await`
El operador `await` solo puede utilizarse dentro de funciones `async`.

Este operador pausa la ejecución de la función `async` hasta que la promesa se resuelva y luego retorna el valor resuelto.

```JavaScript
async function obtenerYProcesarDatos() {
    try {
        const datos = await fetch('https://api.ejemplo.com/datos');
        const datosJson = await datos.json();
  
        // Procesar datos
        const resultadoProcesado = procesarDatos(datosJson);
        return resultadoProcesado;
        
    } catch (error) {
        console.error('Error al obtener o procesar datos:', error);
        throw error;
    }
}
```

Este ejemplo puede compararse con el ejemplo de **Encadenamiento de Promesas**.

---

# Ventajas de Async/Await
- **Código más limpio y legible:** se parece más al código sincrónico tradicional.
- **Mejor manejo de errores:** permite utilizar `try/catch` para manejar errores sincrónicos y asincrónicos.
- **Depuración más sencilla:** el stack trace es más claro y útil que con cadenas de promesas.
- **Control de flujo simplificado:** facilita la implementación de lógica condicional y bucles con operaciones asincrónicas.

---

# Ejemplo práctico: Promesas vs Async/Await

## Promesas
```JavaScript
function makeRequestWithPromise() {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();

        xhr.addEventListener('readystatechange', function() {
            if (this.readyState === this.DONE) {
                if (this.status >= 200 && this.status < 300) {
                    resolve(this.responseText);
                } else {
                    reject(new Error(`Request failed with status ${this.status}`));
                }
            }
        });

        xhr.addEventListener('error', function() {
            reject(new Error('Network error occurred'));
        });
        
        xhr.open('GET', 'https://catfact.ninja/fact');
        xhr.send(null);
    });
}
```

## Async/Await

```JavaScript
async function displayCatFactAsync() {
    try {

        // Esperar a que la promesa se resuelva
        const responseText = await makeRequestWithPromise();

        // Esto solo se ejecuta cuando la promesa se resuelve correctamente
        console.log(responseText);
        document.getElementById("response").innerHTML = responseText;

        // Podemos procesar los datos de manera más legible
        const data = JSON.parse(responseText);

        console.log(`El dato curioso sobre gatos es: ${data.fact}`);

        // Si quisiéramos hacer una segunda petición basada en la primera
        // const secondResponse = await makeAnotherRequest(data.fact);
        // console.log(secondResponse);

        return data;
        
    } catch (error) {
        // Manejo de errores más similar a código sincrónico
        console.error('Error:', error.message);
        document.getElementById("response").innerHTML =
            `Error: ${error.message}`;
    }
}
  
displayCatFactAsync().then(result => {
    console.log('Todo el proceso completado', result);
});
```

También se puede llamar simplemente mediante:

```JavaScript
displayCatFactAsync();
```