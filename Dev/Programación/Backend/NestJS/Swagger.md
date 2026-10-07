**Swagger** permite **visualizar, documentar y probar los endpoints** de una API.

Permite ver, por ejemplo:

```
GET /encounters

qué recibe
qué devuelve
qué códigos HTTP responde
```

Decoradores como:

```ts
@ApiTags(...)
@ApiOperation(...)
@ApiBody(...)
```

agregan información al contrato que Swagger muestra.

Por ejemplo:

```ts
@ApiOperation({
  summary: 'List all encounters'
})
```

describe qué hace ese endpoint.

Swagger permite comprobar visualmente:

```
endpoint
↓
método HTTP
↓
URL
↓
request
↓
response
↓
código HTTP
```

---
