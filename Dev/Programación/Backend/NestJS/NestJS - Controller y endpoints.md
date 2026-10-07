En NestJS, un **Controller** recibe solicitudes HTTP y define los endpoints que expone el backend.

```
Frontend
↓ request HTTP
Controller NestJS
↓
endpoint
↓
response
↓
Frontend
```

---

## Endpoint

Un **endpoint** es una operación de una API identificada por:

```ts
método HTTP + URL
```

Ejemplo:

```ts
GET /current/encounters
```

- `GET` → método HTTP.
- `/current/encounters` → URL del endpoint.

---

## Controller

```ts
@Controller('encounters')
export class EncountersController {
}
```

`@Controller()` define la ruta base de los endpoints del Controller.

---

## Métodos HTTP

```ts
@Get()
@Post()
@Patch()
@Put()
@Delete()
```

Indican qué método HTTP atiende cada operación.

```ts
@Get()    → consultar
@Post()   → crear/enviar
@Patch()  → modificar parcialmente
@Put()    → reemplazar
@Delete() → eliminar
```

Ejemplo:

```ts
@Get()
getEncounters() {
}
```

representa:

```ts
GET /encounters
```

---

## Datos del request

```ts
@Body()
```

Obtiene datos enviados en el cuerpo de la petición.

```ts
@Param('encounterId')
```

Obtiene un parámetro incluido en la URL.

Ejemplo:

```ts
GET /encounters/123
                 ↑
           encounterId
```

---

## Swagger

Swagger permite **visualizar, documentar y probar los endpoints** de una API.

Permite ver, por ejemplo:

```ts
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

agregan información al contrato mostrado por Swagger.

---

## Machete

```ts
Controller = recibe requests HTTP y expone endpoints

endpoint = método HTTP + URL

@Get() = endpoint de lectura

@Body() = datos del body

@Param() = dato incluido en la URL

Swagger = documenta y permite probar la API
```

---
