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


`provideHttpClient()` habilita `HttpClient` para que Angular pueda inyectarlo y utilizarlo en la aplicación.

Conceptualmente:

```text
provideHttpClient()
↓
Angular puede proporcionar HttpClient
↓
un Service puede recibirlo por inyección
↓
puede realizar solicitudes HTTP
```

---
