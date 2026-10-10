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

# Temas Importantes

- [[HttpClient]]
- [[pipe()]]
- [[map()]]
- [[tap()]]
- [[finalize()]]

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

# Errores en Observables

`throwError()` crea un Observable que emite un error.

```ts
return throwError(
  () => new Error('Ocurrió un error')
);
```

Esto permite que el error viaje por el flujo del Observable y sea recibido por:

```ts
subscribe({
  error: (errorRecibido) => {
    console.error(errorRecibido);
  }
});
```

También puede producirse un error mediante `throw` dentro de un operador como `map()`.

Cuando ocurre un error:

```
Observable
↓
error
↓
se detiene el flujo normal
↓
subscribe.error
↓
finalize
```

`complete` no se ejecuta cuando el Observable termina con error.

---
