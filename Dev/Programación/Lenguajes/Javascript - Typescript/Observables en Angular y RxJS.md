Angular utiliza **RxJS** para trabajar con asincronismo, especialmente mediante su `HttpClient`.

Un `Observable` representa un flujo de valores a lo largo del tiempo.

A diferencia de una `Promise`, que representa normalmente un único resultado eventual, un `Observable` puede emitir múltiples valores, puede cancelarse y permite transformar los valores mediante operadores de RxJS.

---

## Promise

```text
Promise
↓
resultado
↓
termina
```

---

## Observable

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

|Característica|Promise|Observable|
|---|---|---|
|Resultado|Un único resultado|Uno o múltiples valores|
|Inicio|Comienza al crear la Promise|Generalmente comienza al hacer `subscribe()`|
|Cancelación|No tiene cancelación nativa general|Puede cancelarse|
|Transformación|`.then()`|operadores RxJS mediante `.pipe()`|
|Manejo del resultado|`.then()`, `.catch()`, `.finally()`|`next`, `error`, `complete`|
|Angular `HttpClient`|No lo utiliza directamente|Devuelve Observables|

### Ejemplo con Promise

```ts
const promesa = fetch('/api/productos');

promesa
  .then(response => response.json())
  .then(productos => console.log(productos));
```

### Ejemplo con Observable

```ts
this.http.get<Producto[]>('/api/productos')
  .subscribe({
    next: (productos) => console.log(productos),
    error: (error) => console.error(error),
    complete: () => console.log('Finalizó')
  });
```

---

# HttpClient

`HttpClient` es el servicio de Angular que permite realizar solicitudes HTTP a un backend o API.

Puede hacer peticiones como:

```
GET    → obtener datos
POST   → crear/enviar datos
PUT    → modificar datos
DELETE → eliminar datos
```

Se puede inyectar en un service:

```ts
constructor(private readonly http: HttpClient) {}
```

Luego se puede hacer una petición:

```ts
this.http.get<Conversacion[]>('/api/conversaciones');
```

Esto significa:

```ts
this.http
= HttpClient

get()
= petición HTTP GET

<Conversacion[]>
= tipo de dato que esperamos recibir

'/api/conversaciones'
= URL que consultamos
```

`HttpClient` devuelve un Observable:

```ts
Observable<Conversacion[]>
```

No devuelve directamente el array de conversaciones.

Para consumirlo se utiliza `subscribe()`:

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
      console.log('Finalizó correctamente');
    }
  });
```

---

# subscribe()

`subscribe()` permite escuchar qué ocurre con el Observable.

```
subscribe()
├── next
├── error
└── complete
```

|Callback|Se ejecuta cuando...|
|---|---|
|`next`|El Observable emite un valor|
|`error`|Ocurre un error|
|`complete`|El Observable termina correctamente|

Ejemplo:

```ts
next: (conversacionesRecibidas) => {
  this.conversaciones = conversacionesRecibidas;
}
```

`conversacionesRecibidas` es un parámetro que recibe el valor emitido por el Observable.

```
Observable emite conversaciones
↓
conversacionesRecibidas
↓
this.conversaciones = conversacionesRecibidas
```

---

# pipe()

`pipe()` permite aplicar **operadores de RxJS** al Observable antes de consumirlo con `subscribe()`.

```ts
observable
  .pipe(
    operador1(),
    operador2()
  )
  .subscribe(...);
```

Conceptualmente:

```
Observable
↓
pipe()
aplica operadores
↓
subscribe()
consume el resultado
```

`pipe()` no siempre es necesario.

Algunos operadores son:

```ts
map()
tap()
filter()
switchMap()
finalize()
```

---

# map()

`map()` transforma el valor que emite un Observable.

```ts
map((datoRecibido) => datoTransformado)
```

Flujo:

```
dato original
↓
map()
↓
dato transformado
```

Ejemplo:

```ts
map((response) => response.data)
```

Entra:

```
response
├── success
├── message
└── data
```

Sale:

```ts
data
```

Machete:

```ts
map() = transforma el dato
```

---

# tap()

`tap()` permite hacer algo con el valor que pasa por el Observable **sin transformarlo**.

```ts
tap((conversacionesRecibidas) => {
  this.conversaciones = conversacionesRecibidas;
})
```

Machete:

```ts
map() → transforma el dato

tap() → hace algo con el dato,
        pero el dato sigue igual
```

---

# finalize()

`finalize()` es un operador de RxJS, por eso va dentro de `pipe()`.

```ts
.pipe(
  finalize(() => {
    this.cargando = false;
  })
)
```

Se ejecuta cuando el Observable termina, tanto si salió bien como si ocurrió un error.

Por eso es útil para estados de carga.

```
cargando = true
↓
Observable
↓
├── éxito
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
haya salido bien o mal
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

---

# Estructura típica

```ts
this.servicio
  .obtenerDatos()
  .pipe(
    map((respuesta) => respuesta.data),

    tap((datosRecibidos) => {
      this.datos = datosRecibidos;
    }),

    finalize(() => {
      this.cargando = false;
    })
  )
  .subscribe({
    error: (errorRecibido: unknown) => {
      console.error(errorRecibido);
    }
  });
```

Flujo:

```
Service
↓
HttpClient
↓
Observable
↓
pipe()
├── map()      → transforma
├── tap()      → hace algo sin transformar
└── finalize() → al terminar
↓
subscribe()
├── next
├── error
└── complete
```

---

## Para Angular y el TP

```
Component
↓
Service Angular
↓
HttpClient
↓
Backend
↓
respuesta
↓
Observable
↓
pipe()
↓
subscribe()
```

---

## Machete

```
HttpClient = hace solicitudes HTTP

http.get() = hace una petición GET

Observable = representa valores que pueden llegar después

pipe() = aplica operadores al Observable

map() = transforma el dato

tap() = hace algo con el dato sin transformarlo

subscribe() = escucha/consume el Observable

next = llegó un valor

error = ocurrió un error

complete = terminó correctamente

finalize = terminó, haya salido bien o mal
```

---
