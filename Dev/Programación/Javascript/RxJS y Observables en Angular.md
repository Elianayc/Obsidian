[[Angular]] utiliza **RxJS** para trabajar con asincronismo, especialmente mediante su `HttpClient`.
Un **Observable** representa un flujo de valores a lo largo del tiempo.

A diferencia de una Promise, que representa normalmente un único resultado eventual, un Observable **puede emitir múltiples valores**, puede cancelarse y permite transformar y combinar los valores mediante operadores de RxJS.

```text
Promise
   ↓
resultado
   ↓
termina
```

Un Observable puede emitir:

```text
Observable
   ↓
valor
   ↓
valor
   ↓
valor
   ↓
...
```

> Un Observable puede emitir múltiples valores, aunque un Observable utilizado para una solicitud HTTP normalmente emite una respuesta y luego completa.

---

## Promise vs Observable

Las **Promises** y los **Observables** permiten trabajar con operaciones asincrónicas, pero tienen diferencias importantes en la forma en que producen y manejan los resultados.

|     **Característica**     |                     **Promise**                     |                               **Observable**                                |
| :------------------------: | :-------------------------------------------------: | :-------------------------------------------------------------------------: |
|       **Resultado**        |           Resuelve **un único resultado**           |      Puede emitir **uno o múltiples resultados** a lo largo del tiempo      |
| **Inicio de la operación** |    La operación comienza al **crear la Promise**    |           Generalmente comienza al **suscribirse** (`subscribe`)            |
|      **Cancelación**       | No tiene un mecanismo de cancelación nativo general |        Puede cancelarse mediante la **suscripción** (`unsubscribe`)         |
|     **Transformación**     |         Se utilizan métodos como `.then()`          | Se utilizan **operadores de RxJS**, como `map`, `filter`, `switchMap`, etc. |
|  **Manejo del resultado**  |         `.then()`, `.catch()`, `.finally()`         |               `subscribe()` con `next`, `error` y `complete`                |
|  **Angular `HttpClient`**  |     No es el mecanismo que utiliza directamente     |                          Devuelve **Observables**                           |
| **Cantidad de emisiones**  |            Una sola resolución o rechazo            |              Puede emitir múltiples valores antes de finalizar              |

### Ejemplo con Promise

```js
const promesa = fetch('/api/productos');

promesa.then(response => response.json())
       .then(productos => console.log(productos));
```

La Promise representa **un resultado futuro**: cuando se obtiene la respuesta, la Promise se resuelve y termina.

### Ejemplo con Observable

```ts
this.http.get<Producto[]>('/api/productos')
  .subscribe({
    next: productos => console.log(productos),
    error: error => console.error(error),
    complete: () => console.log('Finalizó')
  });
```

El Observable representa una **secuencia de valores a lo largo del tiempo**. Puede emitir uno, varios o ningún valor y finalmente completar o producir un error.

> **Importante:** una petición HTTP realizada mediante `HttpClient` normalmente emite **una sola respuesta y luego completa**. La principal diferencia no es que _toda_ petición HTTP produzca múltiples valores, sino que el modelo `Observable` permite trabajar con múltiples emisiones.

---

## HttpClient de Angular

El `HttpClient` de Angular utiliza Observables para realizar solicitudes HTTP.

```TypeScript
this.http.get<Conversacion[]>('/api/conversaciones');
```

El resultado es un Observable.

Para consumirlo se puede utilizar `subscribe()`:

```TypeScript
this.http.get<Conversacion[]>('/api/conversaciones')
    .subscribe({
        next: (data) => {
            this.conversaciones = data;
        },

        error: (err) => {
            this.error = err.message;
        },

        complete: () => {
            this.cargando = false;
        }
    });
```

Los callbacks de `subscribe()` indican qué hacer en cada situación:

|  Callback  |     Se ejecuta cuando...      |
| :--------: | :---------------------------: |
|   `next`   | El Observable emite un valor. |
|  `error`   |       Ocurre un error.        |
| `complete` |    El Observable termina.     |

---

