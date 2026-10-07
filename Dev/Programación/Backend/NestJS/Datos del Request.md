NestJS también utiliza decoradores para obtener datos de una petición HTTP.

Ver [[Contratos del Request]]

---

### `@Body()`

Obtiene datos enviados en el **cuerpo de la petición**.

```ts
@Body()
```

Por ejemplo:

```ts
createMessage(@Body() request: CreateMessageRequest) {
}
```

---

### `@Param()`

Obtiene un parámetro incluido en la URL.

```ts
@Param('encounterId')
```

Ejemplo:

```ts
GET /encounters/123
```

En esa URL:

```ts
GET /encounters/123
                 ↑
           encounterId
```

En NestJS podría recibirse así:

```ts
@Get(':encounterId')
getEncounter(
  @Param('encounterId') encounterId: string
) {
}
```

---

