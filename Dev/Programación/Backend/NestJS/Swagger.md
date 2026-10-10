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

## Swagger vs NestJS

Los decoradores de **NestJS** hacen funcionar la aplicación.

Por ejemplo:

```ts
@Controller()
@Get()
@Post()
@Patch()
@Body()
@Param()
```

Los decoradores de **Swagger** documentan ese comportamiento.

Por ejemplo:

```ts
@ApiTags()
@ApiOperation()
@ApiBody()
@ApiProperty()
```

Conceptualmente:

```text
NestJS
→ crea y maneja el endpoint

Swagger
→ documenta y muestra ese endpoint
```

Por ejemplo:

```ts
@Get(':conversationId')
```

crea el comportamiento HTTP del endpoint.

Mientras que:

```ts
@ApiOperation({
  summary: 'Get one conversation by id'
})
```

solamente lo documenta.

`@ApiProperty()` documenta una propiedad, pero **no crea esa propiedad**.

Swagger tampoco crea endpoints.

---