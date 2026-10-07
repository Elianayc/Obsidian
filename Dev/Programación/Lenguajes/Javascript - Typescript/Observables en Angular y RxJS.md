Angular utiliza **RxJS** para trabajar con asincronismo, especialmente mediante su `HttpClient`.

Un `Observable` representa un flujo de valores a lo largo del tiempo.

A diferencia de una `Promise`, que representa normalmente un único resultado eventual, un `Observable` puede emitir múltiples valores, puede cancelarse y permite transformar y combinar los valores mediante operadores de RxJS.

## Promise

```
Promise
↓
resultado
↓
termina
```

## Observable

Un Observable puede emitir:

```
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

Un Observable puede emitir múltiples valores, aunque un Observable utilizado para una solicitud HTTP normalmente emite **una respuesta y luego completa**.

---

## Promise vs Observable

|     Característica     |                       Promise                       |                          Observable                           |
| :--------------------: | :-------------------------------------------------: | :-----------------------------------------------------------: |
|       Resultado        |             Resuelve un único resultado             | Puede emitir uno o múltiples resultados a lo largo del tiempo |
| Inicio de la operación |      La operación comienza al crear la Promise      |    Generalmente comienza al suscribirse con `subscribe()`     |
|      Cancelación       | No tiene un mecanismo de cancelación nativo general |           Puede cancelarse mediante la suscripción            |
|     Transformación     |         Se utilizan métodos como `.then()`          |       Se utilizan operadores de RxJS mediante `.pipe()`       |
|  Manejo del resultado  |         `.then()`, `.catch()`, `.finally()`         |        `subscribe()` con `next`, `error` y `complete`         |
|  Angular `HttpClient`  |     No es el mecanismo que utiliza directamente     |                     Devuelve Observables                      |
| Cantidad de emisiones  |            Una sola resolución o rechazo            |       Puede emitir múltiples valores antes de finalizar       |

---

### Ejemplo con Promise

```ts
const promesa = fetch('/api/productos');

promesa
  .then(response => response.json())
  .then(productos => console.log(productos));
```

La Promise representa un resultado futuro: cuando se obtiene la respuesta, la Promise se resuelve y termina.

---

### Ejemplo con Observable

```ts
this.http.get<Producto[]>('/api/productos')
  .subscribe({
    next: productos => console.log(productos),
    error: error => console.error(error),
    complete: () => console.log('Finalizó')
  });
```

El Observable representa una secuencia de valores a lo largo del tiempo. Puede emitir uno, varios o ningún valor y finalmente completar o producir un error.

**Importante:** una petición HTTP realizada mediante `HttpClient` normalmente emite una sola respuesta y luego completa. La principal diferencia no es que toda petición HTTP produzca múltiples valores, sino que el modelo Observable permite trabajar con múltiples emisiones.

---

# HttpClient de Angular

El `HttpClient` de Angular utiliza Observables para realizar solicitudes HTTP.

```ts
this.http.get<Conversacion[]>('/api/conversaciones');
```

El resultado es:

```ts
Observable<Conversacion[]>
```

No devuelve directamente el array de conversaciones.

Para consumir el Observable se utiliza `subscribe()`:

```ts
this.http.get<Conversacion[]>('/api/conversaciones')
  .subscribe({
    next: (conversacionesRecibidas) => {
      this.conversaciones = conversacionesRecibidas;
    },

    error: (errorRecibido: unknown) => {
      console.error(errorRecibido);
    },

    complete: () => {
      console.log('El Observable terminó correctamente');
    }
  });
```

Los callbacks de `subscribe()` indican qué hacer en cada situación:

|Callback|Se ejecuta cuando...|
|---|---|
|`next`|El Observable emite un valor|
|`error`|El Observable termina debido a un error|
|`complete`|El Observable termina correctamente|

Los parámetros `conversacionesRecibidas` y `errorRecibido` se declaran en esas funciones y reciben lo que emite el Observable.

---

# pipe()

`pipe()` permite aplicar **operadores de RxJS** al Observable antes de consumirlo con `subscribe()`.

Ejemplo:

```ts
observable
  .pipe(
    operador1(),
    operador2()
  )
  .subscribe(...);
```

Algunos operadores de RxJS son `map`, `filter`, `switchMap` y `finalize`.

Conceptualmente:

```
Observable
↓
pipe()
aplica operadores al flujo
↓
subscribe()
consume/escucha el resultado
```

`pipe()` no siempre es necesario. Se usa cuando queremos aplicar operadores al Observable.

---

# finalize()

`finalize()` es un operador de RxJS, por eso se coloca dentro de `pipe()`.

```ts
this.http.get<Conversacion[]>('/api/conversaciones')
  .pipe(
    finalize(() => {
      this.cargando = false;
    })
  )
  .subscribe({
    next: (conversacionesRecibidas) => {
      this.conversaciones = conversacionesRecibidas;
    },

    error: (errorRecibido: unknown) => {
      console.error(errorRecibido);
    }
  });
```

`finalize()` se ejecuta cuando el Observable termina, tanto si terminó correctamente como si terminó por error.

Por eso es útil para estados como `cargando`.

```
cargando = true
↓
Observable
↓
├── next / complete
└── error
↓
finalize
↓
cargando = false
```

---

## complete vs finalize

`complete`:

```
se ejecuta cuando el Observable termina correctamente
```

`finalize`:

```
se ejecuta cuando el Observable termina,
haya terminado correctamente o con error
```

Caso exitoso:

```
next
↓
complete
↓
finalize
```

Caso con error:

```
error
↓
finalize
```

Por eso para apagar un `loading` suele ser más útil `finalize()` que `complete`.

---

## Estructura típica

```ts
this.servicio
  .obtenerDatos()
  .pipe(
    finalize(() => {
      this.cargando = false;
    })
  )
  .subscribe({
    next: (datosRecibidos) => {
      this.datos = datosRecibidos;
    },

    error: (errorRecibido: unknown) => {
      console.error(errorRecibido);
    }
  });
```

```
Service
↓
Observable
↓
pipe()
├── finalize()
↓
subscribe()
├── next
├── error
└── complete
```

### Machete

```
Observable = flujo de valores en el tiempo

pipe() = aplica operadores al Observable

subscribe() = escucha/consume el Observable

next = llegó un valor

error = ocurrió un error

complete = terminó correctamente

finalize = terminó, haya salido bien o mal
```

---
