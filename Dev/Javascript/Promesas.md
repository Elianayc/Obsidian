Las **Promises** son objetos que representan el resultado eventual de una operación asincrónica. Permiten trabajar con operaciones potencialmente lentas sin bloquear el hilo principal.

> “Ahora no tengo el resultado, pero te prometo que cuando termine la operación te voy a entregar un resultado o te voy a informar que hubo un error.”

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

Con callbacks, las operaciones pueden quedar **anidadas unas dentro de otras**. Es como una mamushka: cada operación queda **adentro de la anterior**.

```
PASO 1
  └── PASO 2
       └── PASO 3
            └── PASO 4
```

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



Con Promises, las operaciones se pueden escribir **una después de otra**, evitando ese anidamiento. Son **pasos independientes encadenados**. 
El resultado de uno pasa al siguiente, pero no necesitás meter físicamente una función dentro de otra.

```
PASO 1
  ↓
PASO 2
  ↓
PASO 3
  ↓
PASO 4
```

```javascript
login(usuario, password)
    .then(token => obtenerPerfil(token))
    .then(perfil => obtenerConversaciones(perfil.id))
    .then(conversaciones => obtenerMensajes(conversaciones[0].id))
    .catch(error => manejarError(error));
```

Por eso el código es más fácil de **leer, modificar y mantener**. Esa es justamente la idea del **encadenamiento de Promises**.

> **Importante:** `.then()` está pensado para manejar el **resultado exitoso de la Promise anterior**. El error puede manejarse mediante `.catch()`, que puede capturar un error producido durante cualquiera de las operaciones de la cadena.
> 
> Se pueden encadenar tantos `.then()` como sean necesarios para realizar los distintos pasos de una operación.

---

## Métodos estáticos de `Promise`

El objeto `Promise` proporciona métodos útiles para coordinar múltiples Promises:

|         Método         |             ¿Cuándo termina?              |            ¿Qué pasa si alguna falla?            |
| :--------------------: | :---------------------------------------: | :----------------------------------------------: |
|    `Promise.any()`     |     Cuando **la primera tiene éxito**     | Ignora los rechazos hasta encontrar un éxito<br> |
|    `Promise.all()`     |       Cuando **todas tienen éxito**       |                  **Falla todo**                  |
|    `Promise.race()`    | Cuando **la primera termina**, bien o mal |        Depende de cómo termine la primera        |
| `Promise.allSettled()` |  Cuando **todas terminaron**, bien o mal  |          **No falla por los rechazos**           |


    
Para más información: [**MDN - Promise**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

---

