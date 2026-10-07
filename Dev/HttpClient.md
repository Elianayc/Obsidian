# HttpClient

`HttpClient` es la herramienta de Angular para realizar solicitudes HTTP a un backend o API.

Por ejemplo:

```typescript
constructor(private readonly http: HttpClient) {}
````

Angular inyecta `HttpClient` en el service para que pueda realizar peticiones.

---

## GET

```ts
this.http.get<Producto[]>('/api/productos');
```

`get()` realiza una petición HTTP `GET`.

Flujo:

```
Service Angular
↓
HttpClient
↓
GET
↓
Backend / API
↓
respuesta
```

`HttpClient` devuelve un `Observable`, por lo que la respuesta puede trabajarse con `pipe()` y `subscribe()`.

```
this.http
  .get<Producto[]>('/api/productos')
  .pipe(...)
  .subscribe(...);
```

## En el TP

El flujo será conceptualmente:

```
Component
↓
Service Angular
↓
HttpClient
↓
Backend NestJS
```

Ver también: [[RxJS y Observables en Angular]]

````

Y en tu nota de Observables, donde dice:

> Angular utiliza RxJS para trabajar con asincronismo, especialmente mediante su HttpClient.

podés cambiar `HttpClient` por:

```text
[[HttpClient]]
````

