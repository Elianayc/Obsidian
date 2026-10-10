Una clase de request define el **contrato de los datos que puede o debe recibir un endpoint**.

Ejemplo:

```ts
export class CreateDemoMessageRequest {
  content!: string;
  name!: string;
}
```

En este caso se esperan ambos datos.

```ts
export class UpdateDemoMessageRequest {
  content?: string;
  name?: string;
}
```

En este caso los datos son opcionales.

```
! → la propiedad se espera definida
? → la propiedad es opcional
```

El contrato del request **no define el método HTTP**.

El Controller decide dónde utilizarlo:

```ts
@Post()
createMessage(@Body() request: CreateDemoMessageRequest) {
}
```

```ts
@Patch(':messageId')
updateMessage(@Body() request: UpdateDemoMessageRequest) {
}
```

---

## Request, Model y Response

`Request`, `Model` y `Response` no necesariamente tienen la misma estructura.

```text
REQUEST
↓
datos que entran al Backend

MODEL
↓
representación de los datos con los que trabaja la aplicación

RESPONSE
↓
datos que el Backend devuelve
```

Por ejemplo, para modificar el título de una conversación el Request podría ser:

```json
{
  "title": "Nuevo título"
}
```

El Backend puede trabajar internamente con una conversación completa:

```text
conversationId
title
status
updatedAt
```

y devolver como Response:

```json
{
  "conversationId": "conv-5",
  "title": "Nuevo título",
  "status": "ACTIVE",
  "updatedAt": "2026-10-10T12:00:00.000Z"
}
```

Por lo tanto:

```text
Request
→ define cómo entran los datos

Model
→ representa los datos con los que trabaja la aplicación

Response
→ define cómo salen los datos
```

---
